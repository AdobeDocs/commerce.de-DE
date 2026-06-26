---
title: '[!DNL SaaS Data Export Guide]'
description: Erfahren Sie mehr über die Verwendung  [!DNL data export]  Erweiterung für Adobe Commerce SaaS-Services, die Daten zwischen Adobe Commerce und verbundenen Commerce-Services synchronisiert.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
exl-id: 8a0067ba-90a4-48a6-8276-208d09abe6fc
TQID: https://experienceleague.adobe.com/OHE1GBUEd8hHFPwFlO9fJa3Y0wK2xZ0HOYnwUn0-DSk
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2:
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 402
ht-degree: 0%

---

# Handbuch zu [!DNL SaaS Data Export]

[!DNL SaaS data export] synchronisiert Daten zwischen einer Adobe Commerce-Instanz und verbundenen Commerce Services. Beim Hinzufügen von Live Search, Produktempfehlungen, dem Katalog-Service oder der [!DNL Adobe Commerce Optimizer Connector] zu einer Adobe Commerce-Installation wird die [!DNL Data Export] automatisch installiert.

>[!NOTE]
>
>Wenn Sie die [!DNL Adobe Commerce Optimizer Connector] installieren, erfasst dieselbe [!DNL Data Export]-Erweiterung Katalog- und Preis-Feeds von [!DNL Adobe Commerce]. Der Connector ordnet diese Feeds dann [!DNL Adobe Commerce Optimizer] zu und übermittelt sie mithilfe des Composable Catalog Data Model (CCDM). In der [[!DNL Adobe Commerce Optimizer Connector] Übersicht](../aco-connector/overview.md) finden Sie Informationen zum Setup und zur Architektur sowie [Connector-Sync](../aco-connector/connector-sync-pipeline.md)Pipeline) für das Synchronisierungsverhalten nach dem Export.

SaaS-Datenexport erfasst und exportiert verschiedene Datentypen, so genannte _Feeds_, mit denen bestimmte Arten von Informationen aggregiert werden. Je nachdem, welche Commerce-Services installiert sind, umfassen die SaaS-Datenexport-Feeds Folgendes:

- **Katalogentitäts-Feeds** aggregieren Produktdaten. Zu den Daten gehören Produkte, Produktattribute, Produktpreise, Produktvarianten, Kategorien, Kategorieberechtigungen und Produktberechtigungen.
- Der **Bereiche-Feed** aggregiert Daten für Kundengruppen, Websites, Stores und Store-Ansichten.
- Der **Kundenauftrags-Feed** aggregiert Auftragsdaten einschließlich der zugehörigen Entitäten wie Rechnungen, Lieferungen, Gutschriften usw.
- Der **Inventar-Feed für mehrere Source** aggregiert Daten zu Lagerbestandsstatus-Elementen.

SaaS-Datenexport wird als PHP-Erweiterung bereitgestellt, die sowohl automatische als auch manuelle Synchronisierung unterstützt:

- **Automatische Synchronisierung** - Nach der ersten vollständigen Synchronisierung, wenn Sie einen Commerce-Service verbinden, halten Cron-Aufträge verbundene Services mithilfe der teilweisen Synchronisierung und des automatischen Wiederholens fehlgeschlagener Elemente auf dem neuesten Stand, ohne dass eine Aktion vom Admin-Benutzer oder Systemintegrator erforderlich ist.

- **Manuelle Synchronisierung** Führen Sie eine vollständige Neusynchronisierung oder Neusynchronisierung ausgewählter Feeds über die Commerce Admin oder die [Commerce CLI aus](data-export-cli-commands.md).

- **Monitoring** - Verfolgen Sie Zustand, Status und Versand von Feeds über die [!UICONTROL Data Feed Sync Status] und das Daten-Management-Dashboard in Commerce Admin. Siehe [Synchronisierung verwalten](data-sync-manage.md) für Schritte zur Überprüfung und Neusynchronisierung.

Informationen zum Synchronisierungsverhalten, zu den Modi und zum Exportflussdiagramm finden Sie unter [Funktionsweise der Synchronisierung](sync-overview.md).

Der SaaS-Datenexport bietet außerdem Tools zur Planung und Fehlerbehebung beim Synchronisierungsprozess:

- **Planung und Leistung** - Schätzen Sie die Synchronisierungszeit, um die Verarbeitung zu planen und Site-Unterbrechungen zu vermeiden, und passen Sie die Exportverarbeitung an, um die Leistung zu verbessern. Siehe [Schätzen des Datenvolumens und der Übertragungszeit](estimate-data-volume-sync-time.md) und [Verbessern der Datenexportleistung](customize-export-processing.md).

- **Tracking und Fehlerbehebung**—Überprüfen Sie den Synchronisierungsstatus und die Feed-Payloads mithilfe von Datenexport- und SaaS-Exportprotokollen. Siehe [Protokolle überprüfen und Fehler beheben](troubleshooting/logging.md).

>[!MORELIKETHIS]
>
> - [SaaS-Datenexport-Feeds erweitern und anpassen](extensibility-and-customizations.md) — Hinzufügen oder Ändern von Feed-Daten.
> - [Fehlerbehebungsszenarien](troubleshooting/troubleshooting-scenarios.md) — Diagnostizieren Sie Konfigurationsfehler und unerwartete Synchronisierungsergebnisse.
> - [Versionshinweise](release-notes.md) - Erweiterungs-Updates und bekannte Probleme.
