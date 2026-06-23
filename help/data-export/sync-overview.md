---
title: Synchronisieren von Daten mit dem SaaS-Datenexport
description: Erfahren Sie, wie  [!DNL SaaS Data Export]  Daten zwischen Adobe Commerce-Instanzen und verbundenen Commerce-Services erfasst und synchronisiert.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
exl-id: 2ca7c92a-fb52-4055-ae16-11e99b38d161
TQID: https://experienceleague.adobe.com/wM71qxvduDr77EW6Y8mSNfBXlqkloC-PGOOBOl-mZQM
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: ef1a9efc579d8d21c145e6981235489a2e4ea203
workflow-type: tm+mt
source-wordcount: 907
ht-degree: 0%

---

# Synchronisieren von Daten mit dem SaaS-Datenexport

Wenn Sie einen [!DNL Adobe Commerce]-Service installieren, für den ein Datenexport erforderlich ist, z. B. Catalog Service, Live Search oder Product Recommendations, wird eine Sammlung von SaaS-Datenexportmodulen installiert, um den Datenerfassungs- und Synchronisierungsprozess zu verwalten.

Der SaaS-Datenexport verschiebt Produktdaten laufend von einer Adobe Commerce-Instanz auf die Commerce Services-Plattform, um die Daten auf dem neuesten Stand zu halten. Beispielsweise benötigen Sie für Produktempfehlungen aktuelle Kataloginformationen, um Empfehlungen mit korrekten Namen, Preisen und Verfügbarkeit genau zurückzugeben. Einzelheiten zur Überwachung des Synchronisierungsprozesses finden Sie unter [Synchronisierungsprozess anzeigen und verwalten](data-sync-manage.md).

Das folgende Diagramm zeigt den SaaS-Datenexportfluss.

![SaaS-Datenexporterfassung und -synchronisierungsfluss für Adobe Commerce](assets/data-export-flow.png){width="900" zoomable="yes"}

Wenn sich Katalogdaten in [!DNL Adobe Commerce] ändern, durchläuft die Synchronisierung diese Phasen.

1. **Erkennung von Entitätsänderungen** - Das Mview-System von Magento erkennt Zeilenänderungen in abonnierten Datenbanktabellen (z. B. `catalog_product_entity`) und schreibt Einträge in eine Änderungsprotokolltabelle.
1. **Feed-Indizierung** - Der Feed-Indexer liest das Änderungsprotokoll, lädt Entitätsdaten aus den Quelltabellen und stellt Feed-Elemente zusammen.
1. **Datenerfassung und -umwandlung** - Im Feed-Schema registrierte Anbieter [`et_schema.xml`](extensibility-and-customizations.md#feed-schema-overview) Erfassen von Felddaten.
1. **Hash-Deduplizierung** - Für jedes Feed-Element wird ein Inhalts-Hash berechnet. Elemente, deren Hash seit dem letzten Export nicht geändert wurde, werden übersprungen, sodass nur geänderte Daten übertragen werden.
1. **HTTP-Übermittlung** - Feed-Elemente werden als authentifizierte HTTP-POST-Batches an den Adobe SaaS-Feed-Aufnahme-Service gesendet.
1. **Status persistent** - Der API-Antwortstatus wird für jedes Element zurück in die [Feed-](reference/feed-table-reference.md)) geschrieben.
1. **Fehlgeschlagener Wiederholungsversuch** - Elemente, die nicht exportiert werden konnten, werden automatisch durch einen geplanten Cron-Auftrag erneut versucht.

>[!NOTE]
>
>Für [!DNL Adobe Commerce Optimizer Connector] Bereitstellungen übernimmt [!DNL SaaS Data Export] die Erkennung von Entitätsänderungen und die Feed-Assembly. Der Connector ordnet dann Feeds dem [!DNL Catalog Data Ingestion API]-Format zu und sendet sie an [!DNL Adobe Commerce Optimizer]. Siehe [Connector-Synchronisierungs](../aco-connector/connector-sync-pipeline.md)Pipeline für die Umfangskontrolle, Übermittlung und Fehlerbehandlung.

>[!NOTE]
>
>Um eine reibungslose Planung sicherzustellen und Unterbrechungen im Site-Betrieb zu vermeiden, empfiehlt Adobe, das Datenvolumen und die Synchronisierungszeit zu schätzen, bevor Sie eine Daten-Feed-Synchronisierung starten. Diese Schätzung ist wichtig bei der Planung von anfänglichen Synchronisationen oder umfangreichen Katalogaktualisierungen, z. B. Massenpreisänderungen. Weitere Informationen finden Sie unter [Schätzen des Datenvolumens und der Übertragungszeit für die Datensynchronisation](estimate-data-volume-sync-time.md)

## Synchronisationsmodi

Der SaaS-Datenexport verfügt über zwei Modi zur Verarbeitung von Entitäts-Feeds:

- **Modus für sofortigen Export** - In diesem Modus werden Daten in einer einzigen Iteration erfasst und sofort an den Commerce-Service gesendet. Dieser Modus beschleunigt die Bereitstellung von Entitätenaktualisierungen an den Commerce-Service und reduziert die Speichergröße der Feed-Tabellen.

- **Alter Exportmodus** - In diesem Modus werden Daten in einem einzigen Prozess erfasst. Dann sendet ein Cron-Auftrag die erfassten Daten an die verbundenen Commerce-Services. In Datenexportprotokolleinträgen sind Feeds, die den alten Modus verwenden, mit `(legacy)` gekennzeichnet.

## Synchronisierungstypen

Der SaaS-Datenexport unterstützt drei Synchronisierungstypen: Vollständige Synchronisierung, Teilsynchronisierung und Wiederholen fehlgeschlagener Elementsynchronisierung.

### Vollständige Synchronisierung

Nachdem Sie eine Adobe Commerce-Instanz mit dem Commerce-Service verbunden haben, führen Sie eine vollständige Synchronisierung durch, um Entitäts-Feed-Daten von Adobe Commerce an den verbundenen Service zu senden.

>[!NOTE]
>
>Die vollständige Synchronisierung erfolgt hauptsächlich in der Onboarding-Phase. Vermeiden Sie den regulären Gebrauch, um eine Überlastung der Datenbank zu vermeiden. Nach der ersten Synchronisierung werden laufende Änderungen automatisch durch partielle Synchronisierung synchronisiert.

>[!NOTE]
>
>Der Befehl `saas:resync` übermittelt nur neue Elemente, aktualisierte Elemente und Elemente, die zuvor nicht exportiert werden konnten. Elemente, deren Inhaltshash seit dem letzten Export nicht geändert wurde, werden übersprungen.

### Teilweise synchronisieren {#partial-sync}

Bei teilweiser Synchronisierung sendet der SaaS-Datenexport automatisch Aktualisierungen aus der Commerce-Anwendung, z. B. Änderungen des Produktnamens oder Preisaktualisierungen, an verbundene Commerce-Services.
Damit die partielle Synchronisierung funktioniert, benötigt die Commerce-Anwendung die folgende Konfiguration:

- [Die Aufgabenplanung wird über Cron-Aufträge aktiviert](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)
- Alle SaaS-Datenexportindizierer sind im `Update by Schedule`-Modus konfiguriert.

### Synchronisierung fehlgeschlagener Elemente wiederholen {#retry-failed-items-sync}

Die Synchronisierung fehlgeschlagener Elemente wiederholen verwendet einen separaten Prozess zum erneuten Senden von Elementen, die aufgrund von Fehlern während des Synchronisierungsprozesses nicht synchronisiert werden konnten, z. B. ein Anwendungsfehler, eine Netzwerkunterbrechung oder ein SaaS-Service-Fehler. Die `*_resend_failed_items` Cron-Aufträge in der `resync_failed_feeds_data_exporter` bearbeiten dies automatisch alle 5 Minuten.

## Geplante Cron-Aufträge

Die folgenden Cron-Gruppen automatisieren die Pipeline nach einem festen Zeitplan.

| Cron-Gruppe | Cron-Job | Zweck | Zeitplan |
|---|---|---|---|
| `index` | `indexer_update_all_views` | Verarbeitet MView-Änderungsprotokolle und Trigger für partielle Feed-Aktualisierungen | Alle 1 Minute |
| `index` | `indexer_reindex_all_invalid` | Führt eine vollständige Neusynchronisierung für Feed-Indizes durch, die als „Neuindizierung erforderlich“ markiert sind | Alle 1 Minute |
| `resync_failed_feeds_data_exporter` | `*_resend_failed_items` | Erkennt fehlgeschlagene Feed-Elemente und sendet sie erneut | Alle 5 Minuten |
| `commerce_data_export` | `saas_data_exporter` | Übermittelt Daten für Feeds des alten Modus (Bestellungen, Bereiche) | Alle 5 Minuten |
| `commerce_data_export` | `cleanup_deleted_feed_items` | Bereinigt synchronisierte gelöschte Feed-Elemente nach dem Aufbewahrungszeitraum (7 Tage) | Jeden Tag um 2:00 h |

## Feed-Übermittlung und HTTP-Fehlerbehandlung {#feed-submission-and-http-error-handling}

Feed-Elemente werden als authentifizierte gzip-komprimierte JSON-Batches über HTTP-POST gesendet. Die folgende Tabelle zeigt, wie HTTP-Antwort-Codes dem Exportstatus und dem Wiederholungsverhalten zugeordnet sind.

| Status-Code | Erneut versuchen? | Bedeutung |
|-------------|--------|---------------------------------------------------------------------------------------------------------------------|
| 200 | Nein | Erfolgreich akzeptiert |
| 400 | Nein | Fehlerhafte Daten oder Validierungsfehler - Erfordert manuelle Untersuchung. `var/log/saas-export-errors.log` Details finden Sie. |
| 429 | Ja | Ratenbegrenzungstreffer - Reduzieren der `thread_count` in [Exportverarbeitungseinstellungen](customize-export-processing.md) |
| 5xx | Ja | SaaS-seitiger Fehler - automatischer erneuter Versuch |
| 2 | Ja | Element ist für einen erneuten Versuch geplant |

Zusätzlich zu Fehlern auf HTTP-Ebene werden Fehler auf Anwendungsebene, wie lokale Verarbeitungsfehler oder Netzwerkstörungen, auch für automatische erneute Versuche durch die `*_resend_failed_items` Cron-Aufträge geplant.

Überwachen Sie den Status der einzelnen Feeds über die Seite [[!UICONTROL Data Feed Sync Status]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status) in Commerce Admin.

>[!MORELIKETHIS]
>
> - [Synchronisierung verwalten](data-sync-manage.md) — Synchronisierungsstatus überprüfen und Feeds manuell neu synchronisieren.
> - [Feed-Tabellenschema](reference/feed-table-reference.md) — Überprüfen Sie den Status und die Fehlerdetails auf Elementebene.
> - [Leistung beim Datenexport verbessern](customize-export-processing.md) - Stimmen Sie die Batch-Größe und die Thread-Anzahl ab.
