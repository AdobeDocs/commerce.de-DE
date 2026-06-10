---
title: Synchronisieren von Daten mit dem SaaS-Datenexport
description: Erfahren Sie, wie  [!DNL SaaS Data Export]  Daten zwischen Adobe Commerce-Instanzen und verbundenen SaaS-Services erfasst und synchronisiert.
role: Admin, Developer
exl-id: 2ca7c92a-fb52-4055-ae16-11e99b38d161
TQID: https://experienceleague.adobe.com/wM71qxvduDr77EW6Y8mSNfBXlqkloC-PGOOBOl-mZQM
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
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
source-git-commit: 2a09ef51939649a12b72c45cbb8b0dc0d0a4c8ad
workflow-type: tm+mt
source-wordcount: 1104
ht-degree: 0%

---

# Synchronisieren von Daten mit dem SaaS-Datenexport

Wenn Sie einen Commerce-Service installieren, für den ein Datenexport erforderlich ist, z. B. Catalog Service, Live Search oder Product Recommendations, wird eine Sammlung von SaaS-Datenexportmodulen installiert, um den Datenerfassungs- und Synchronisierungsprozess zu verwalten.

Der SaaS-Datenexport verschiebt Produktdaten laufend von einer Adobe Commerce-Instanz auf die Commerce Services-Plattform, um die Daten auf dem neuesten Stand zu halten. Beispielsweise benötigen Sie für Produktempfehlungen aktuelle Kataloginformationen, um Empfehlungen mit korrekten Namen, Preisen und Verfügbarkeit genau zurückzugeben. Einzelheiten zur Überwachung des Synchronisierungsprozesses finden Sie unter [Synchronisierungsprozess anzeigen und verwalten](#view-and-manage-the-synchronization-process).


Das folgende Diagramm zeigt den SaaS-Datenexportfluss.

![SaaS-Datenexporterfassung und -synchronisierungsfluss für Adobe Commerce](assets/data-export-flow.png){width="900" zoomable="yes"}

Zu den Hauptkomponenten des SaaS-Datenexportflusses gehören:

- SaaS-Datenexportmodule, die die Daten für Feeds aus Adobe Commerce erfassen, Feed-Elemente zusammenstellen, auf Aktualisierungen warten und den Feed-Status beibehalten.
- SaaS exportieren Module, die Daten exportieren, Routing konfigurieren und die Feeds an verbundene Services veröffentlichen.
- Der Adobe Commerce-Service verwaltet den Datenaufnahmeprozess, um eingehende Feeds zu validieren und Aktualisierungen für verbundene Services beizubehalten.

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

### Teilweise synchronisieren

Bei teilweiser Synchronisierung sendet der SaaS-Datenexport automatisch Aktualisierungen aus der Commerce-Anwendung, z. B. Änderungen des Produktnamens oder Preisaktualisierungen, an verbundene Commerce-Services.

Der Datenexportprozess verwendet die folgenden Cron-Aufträge, um den Vorgang der partiellen Synchronisierung zu automatisieren.

- Cron-Gruppenaufträge „indizieren“:
   - Der `indexer_reindex_all_invalid` indiziert alle ungültigen Feeds neu. Dies ist ein standardmäßiger Adobe Commerce-Cron-Auftrag.
   - Der `saas_data_exporter` ist für alte Export-Feeds.
   - Der `sales_data_exporter` ist spezifisch für den Verkaufsdaten-Export-Feed.

Diese Aufträge werden jede Minute ausgeführt.

Dieselben partiellen Synchronisierungs-Cron-Aufträge werden für [!DNL Adobe Commerce Optimizer Connector]-Feeds ausgeführt. Informationen zur Connector-spezifischen Übermittlung und Fehlerbehandlung finden Sie unter [Connector-Sync-Pipeline](../aco-connector/connector-sync-pipeline.md).

Damit die partielle Synchronisierung funktioniert, benötigt die Commerce-Anwendung die folgende Konfiguration:

- [Die Aufgabenplanung wird über Cron-Aufträge aktiviert](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)

- Alle SaaS-Datenexportindizierer sind im `Update by Schedule`-Modus konfiguriert.

  In der SaaS-Datenexportversion 103.1.0 und höher ist der `Update by Schedule` standardmäßig aktiviert. Sie können die Indexkonfiguration auf dem Server mithilfe des Commerce-CLI-Befehls `bin/magento indexer:show-mode | grep -i feed`

### Synchronisierung fehlgeschlagener Elemente wiederholen

Die Synchronisierung fehlgeschlagener Elemente wiederholen verwendet einen separaten Prozess zum erneuten Senden von Elementen, die aufgrund von Fehlern während des Synchronisierungsprozesses nicht synchronisiert werden konnten, z. B. ein Anwendungsfehler, eine Netzwerkunterbrechung oder ein SaaS-Service-Fehler. Die Implementierung für diese Synchronisierung basiert ebenfalls auf Cron-Aufträgen.

- `resync_failed_feeds_data_exporter` Cron-Gruppenaufträge:
   - Der `<feed name>_feed_resend_failed_feeds_items` sendet Elemente, die nicht synchronisiert werden konnten, erneut, z. B. `products_feed_resend_failed_items`.

### Synchronisierungsprozess anzeigen und verwalten

Die meisten Synchronisierungsaktivitäten werden automatisch auf Grundlage der Anwendungskonfiguration verarbeitet. Der SaaS-Datenexport bietet jedoch auch Tools zur Überwachung und Verwaltung des Prozesses.

- [!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."} **[Daten-Management-Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard)** - Admin-Benutzer können Daten anzeigen und verfolgen, die mit Commerce Services synchronisiert und für Storefront-Services verfügbar sind. Dieses Dashboard zeigt das mit Commerce Services synchronisierte Produkt an.

  {{aco-data-sync-verification}}

- [!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt für Adobe Commerce-Projekte, die in Adobe Commerce Optimizer integriert sind (von Adobe verwaltete SaaS-Infrastruktur)."} **[Seite Synchronisierungsstatus für Daten-Feeds](https://experienceleague.adobe.com/en/docs/commerce/optimizer/setup/data-sync)** - Überprüfen Sie für Commerce-Projekte, die [!DNL Adobe Commerce Optimizer] verwenden, die Verfügbarkeit von Katalogdaten für Ihre Storefront auf der Seite Synchronisierungsstatus für Daten-Feeds in Adobe Commerce Optimizer. Dieses Dashboard zeigt den Synchronisierungsstatus der Datenexport-Feeds an.

>[!NOTE]
>
>Das Daten-Management-Dashboard ist nur verfügbar, wenn Sie die Live Search, Produktempfehlungen oder den Katalog-Service installiert haben. Das Dashboard für den Synchronisierungsstatus von Daten-Feeds ist verfügbar, wenn diese Services oder der [Adobe Commerce Optimizer Connector](../aco-connector/overview.md) installiert sind. Informationen zum Verhalten der Optimizer-Connector-Pipeline, einschließlich Umfangskontrolle und Übermittlungsfehlern, finden Sie unter [Connector-Synchronisierungs-Pipeline](../aco-connector/connector-sync-pipeline.md).

### Konfiguration der Commerce-Anwendung überprüfen

Die Synchronisierung von teilweise synchronisierten und fehlgeschlagenen Elementen mit „Erneut versuchen“ funktioniert nur, wenn die Commerce-Instanz korrekt konfiguriert wurde. Normalerweise wird die Konfiguration abgeschlossen, wenn der Commerce-Service eingerichtet wird. Wenn der Datenexport nicht ordnungsgemäß funktioniert, überprüfen Sie die folgende Konfiguration.

- [Bestätigen Sie, dass Cron-Aufträge ausgeführt werden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).

- Stellen Sie sicher, dass die Indexer vom [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) oder mithilfe des Commerce CLI-`bin/magento indexer:info` ausgeführt werden.

- Stellen Sie sicher, dass die Indexer für die folgenden Feeds auf `Update by Schedule` eingestellt sind: Katalogattribute, Produkt, Produktüberschreibungen und Produktvariante. Sie können die Indexer unter [Indexverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) im Admin oder über die CLI (`bin/magento indexer:show-mode | grep -i feed`) überprüfen.

### Ereignis-Manager-Benachrichtigungen für die Datenübertragungsprotokollierung

In Version 103.3.4 und höher sendet der SaaS-Datenexport das `data_sent_outside`, wenn Daten von der Commerce-Instanz an Adobe Commerce-Services gesendet werden.

```php
$this->eventManager->dispatch(
   "data_sent_outside",
   [
       "timestamp" => time(),
       "type" => $metadata->getFeedName(),
       "data" => $data
   ]
);
```

>[!NOTE]
>
>Informationen zu Ereignissen und zum Abonnieren finden Sie unter [Ereignisse und Beobachter](https://developer.adobe.com/commerce/php/development/components/events-and-observers) in der Adobe Commerce Developer-Dokumentation.
