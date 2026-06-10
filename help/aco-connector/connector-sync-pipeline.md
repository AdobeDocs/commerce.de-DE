---
title: Katalog-Sync-Pipeline
description: Erfahren Sie, wie  [!DNL Adobe Commerce Optimizer Connector]  Pipeline „sync“ funktioniert, einschließlich Feed-Transformation, Cron-Zeitpläne, Umfangskontrolle und Fehlerbehandlung.
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T16:21:52.214Z'
TQID: 'https://experienceleague.adobe.com/EXUQzAd0I6Hnq4twzhaBZZnv0jLjeGBuTx-QgQz-5MA'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: addc3a3a-2b1c-4fdf-aea4-4b1eb2931ba6
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 6d4493db5e0714577a8800007cc6d2c552578fa4
workflow-type: tm+mt
source-wordcount: 625
ht-degree: 1%

---

# Connector-Synchronisierungs-Pipeline

Die auf [[!DNL SaaS Data Export]](https://experienceleague.adobe.com/de/docs/commerce/saas-data-export/overview) basierende **[!DNL Adobe Commerce Optimizer Connector]** ordnet die von [!DNL SaaS Data Export] Indexern erfassten Daten dem Format zu, das für die [!DNL Adobe Commerce Optimizer]-[!DNL Catalog Data Ingestion API] erforderlich ist, und verarbeitet Authentifizierung, Batch-Übermittlung und bereichsbasierte Synchronisierungssteuerung. In den folgenden Abschnitten wird beschrieben, wie diese Synchronisierung funktioniert.

Verwandter Kontext:

- Erfahren Sie mehr über den geschäftlichen Nutzen der Integration, die wichtigsten Funktionen und die Architektur im [[!DNL Commerce Optimizer Connector] Überblick](overview.md).

- Informationen zu Modulpaketnamen, Feed-API-Endpunkten und Konfigurationsschlüsselpfaden finden Sie in der [Connector-Referenz](reference/connector-reference.md)

## Funktionsweise der Synchronisierung

Das folgende Diagramm zeigt die Datensynchronisation von [!DNL Adobe Commerce] zu [!DNL Commerce Optimizer] über die [!DNL Adobe I/O Gateway].

Synchronisierungsdiagramm auf hoher Ebene für ![Commerce Optimizer Connector](assets/aco-connector-sync-high-level-diagram.png){width="800" zoomable="yes"}

Wenn sich Katalogdaten in [!DNL Adobe Commerce] ändern, durchläuft die Synchronisierung diese Phasen.

1. **Erkennung von Entitätsänderungen** - (alle 1 Minute) Ein Cron-Auftrag (`indexer_reindex_all_invalid`) erkennt, [!DNL Adobe Commerce] die Entität die [!DNL SaaS Data Export] ändert und Trigger, die Feed-Elemente zusammenstellt und deren Status verfolgt.
1. **Transformation** - Der [!DNL Commerce Optimizer Connector] nimmt die zusammengestellten Feeds auf, ordnet [!DNL Adobe Commerce] Entitäten und Bereiche den Formaten zu, die von der [!DNL Commerce Optimizer]-API benötigt werden, und bereitet die Payload für die Übertragung vor.
1. **Übertragung** - Die umgewandelten Daten werden über HTTP POST (`/v1/catalog/<feed name>`) über die [!DNL Adobe I/O Gateway] an [!DNL Commerce Optimizer] gesendet, wodurch die eingehenden Feeds validiert und beibehalten werden.
1. **Fehlerwiederholung** (alle 5 Minuten) - Ein separater Cron-Auftrag (`*_resend_failed_items`) erkennt alle fehlgeschlagenen Feed-Elemente und sendet sie erneut über dieselbe Pipeline.

### Geplante Cron-Aufträge

Zwei Cron-Gruppen automatisieren die Pipeline nach einem festen Zeitplan.

| Cron-Gruppe | Zweck | Zeitplan |
| ---------- | ------- | -------- |
| `indexer_reindex_all_invalid` | Lauscht auf Entitätsaktualisierungen, stellt Feed-Elemente zusammen, behält den Feed-Status bei | Alle 1 Minute |
| `*_resend_failed_items` | Prüft auf fehlgeschlagene Feed-Elemente und sendet sie erneut an [!DNL Commerce Optimizer] | Alle 5 Minuten |

Die **[!DNL SaaS Data Export]**-Erweiterung verarbeitet die Feed-Erfassung und die Statusverfolgung. Die Connector-Ebene ordnet Entitäten und Bereiche dem Format zu, das für die [!DNL Commerce Optimizer]-API erforderlich ist, und übermittelt sie über `POST /v1/catalog/<feed name>`.

#### Anforderungen

- [Commerce Cron muss ausgeführt werden](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues){target="_blank"}.
- Feed-Indexer müssen den **[!UICONTROL Update by Schedule]** verwenden. Siehe [Überprüfen der Konfiguration von Commerce-](../data-export/data-synchronization.md#verify-commerce-application-configuration){target="_blank"}.

## Bereichsbasierte Synchronisierungssteuerung

Das `CommerceOptimizerScopeMapper`-Modul liest die Exporteinstellungen pro Website und pro Store-Ansicht und erzwingt sie bei der Erfassung und Übermittlung von Feeds.

- **Aktivierte Bereiche** exportieren Daten im normalen Delta-Zeitplan.
- **Deaktivierte Bereiche** werden aus der Pipeline ausgeschlossen.
Zuvor synchronisierte Entitäten werden bei der nächsten Cron-Ausführung aus [!DNL Commerce Optimizer] entfernt.

Wenn Synchronisierungsprobleme nur eine Katalogquelle oder ein Preisbuch betreffen, siehe [Daten werden nicht synchronisiert](troubleshooting.md#data-not-syncing).

Einzelheiten zum Anpassen des Synchronisierungsbereichs finden Sie unter [Anpassen der Exportkonfiguration für Commerce-Bereiche](get-started.md#customize-the-commerce-scopes-export-configuration).

## Zeitplanung und Überwachung

| Szenario | Typisches Timing |
| -------- | -------------- |
| Routinemäßige Katalogaktualisierungen | 1-2 Delta-Sync-Zyklen (~1-2 Minuten für Indizierung plus Übermittlung) |
| Vorübergehende Fehler | Alle 5 Minuten erneut versucht |
| Vollständige Synchronisierung für große Kataloge | Minuten bis Stunden |

Überwachen Sie den Status der einzelnen Feeds über die Seite [[!UICONTROL Data Feed Sync Status]](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status) in Commerce Admin. Siehe [Überprüfen, ob die Datensynchronisation funktioniert](./get-started.md#verify-that-the-data-sync-is-working).

## Feed-Übermittlung und Fehlerbehandlung

Der `FeedSubmitter` verarbeitet [!DNL Catalog Data Ingestion API].

1. Trennt Aktualisierungselemente von Löschelementen (verschiedene API-Endpunkte).
1. Aufrufe zum unabhängigen Aktualisieren und Löschen von Endpunkten.
1. Führt die Statusergebnisse pro Element wieder in einer einzigen Antwort zusammen.

### Zusammenführen von HTTP-Status-Code

Wenn update- und delete-Aufrufe unterschiedliche Status-Codes zurückgeben, kombiniert `FeedSubmitter` die Ergebnisse wie folgt.

| Ergebnisse aktualisieren | Ergebnisse löschen | Endergebnis |
| --------------- | --------------- | ------------- |
| 200 | 200 oder keine | 200 Erfolg |
| 200 | 400 | 200 mit Löschfehlern |
| 400 | 400 | 400 zusammengeführte Fehler |
| Sonstige | Sonstige | WIEDERHOLBAR |

| Fehlertyp | Verhalten |
| ---------- | -------- |
| **400** | Elemente, die im Feld Antwort-`errors` aufgeführt sind, werden in der Admin-Liste angezeigt und müssen bearbeitet werden. Für andere Elemente im Batch wird ein erneuter Zustellversuch unternommen. |
| **5xx** | Wiederholung durch die Feed-spezifischen `*_feed_resend_failed_items` Cron-Aufträge in der `resync_failed_feeds_data_exporter`. |

>[!MORELIKETHIS]
>
> - [Connector-Übersicht](overview.md) - Erfahren Sie mehr über Geschäftskontext und die Zuordnung von Bereichen
> - [Connector-Referenz](reference/connector-reference.md) - Überprüfungsmodule, API-Endpunkte und Konfigurationsschlüssel
> - [Anpassen der Exportkonfiguration für Commerce-Bereiche](./get-started.md#customize-the-commerce-scopes-export-configuration) — Konfigurieren von Feeds pro Bereichsebene, Aktivieren und Deaktivieren des Verhaltens und von Admin-Schritten
> - [Fehlerbehebung](troubleshooting.md) — Diagnose von Synchronisierungsfehlern
