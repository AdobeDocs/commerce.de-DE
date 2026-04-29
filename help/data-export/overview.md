---
title: '[!DNL SaaS Data Export Guide]'
description: Erfahren Sie mehr über die Verwendung  [!DNL data export]  Erweiterung für Adobe Commerce SaaS-Services, die Daten zwischen Adobe Commerce und verbundenen Commerce-Services synchronisiert.
role: Admin, Developer
exl-id: 8a0067ba-90a4-48a6-8276-208d09abe6fc
source-git-commit: 803e270c5b3119681a6e8c005728a00b3b7875f7
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Handbuch zu [!DNL SaaS Data Export]

[!DNL SaaS data export] synchronisiert Daten zwischen einer Adobe Commerce-Instanz und verbundenen Commerce Services. Wenn Sie Live Search, Produktempfehlungen oder den Katalog-Service zu einer Adobe Commerce-Installation hinzufügen, wird die [!DNL Data export] automatisch installiert.

>[!NOTE]
>
>Wenn Sie den Adobe Commerce Optimizer-Connector installieren, wird dieselbe Datenexporterweiterung verwendet, um Katalog- und Preis-Feeds mithilfe des Composable Catalog Data Model (CCDM) an Adobe Commerce Optimizer zu senden. Architektur- und Konfigurationsdetails finden Sie im ](../aco-connector/overview.md) zum Adobe Commerce Optimizer-Connector [.

SaaS-Datenexport erfasst und exportiert verschiedene Datentypen, so genannte _Feeds_, mit denen bestimmte Arten von Informationen aggregiert werden. Je nachdem, welche Commerce-Services installiert sind, umfassen die SaaS-Datenexport-Feeds Folgendes:

- **Katalogentitäts-Feeds** aggregieren Produktdaten. Zu den Daten gehören Produkte, Produktattribute, Produktpreise, Produktvarianten, Kategorien, Kategorieberechtigungen und Produktberechtigungen.
- Der **Bereiche-Feed** aggregiert Daten für Kundengruppen, Websites, Stores und Store-Ansichten.
- Der **Kundenauftrags-Feed** aggregiert Auftragsdaten einschließlich der zugehörigen Entitäten wie Rechnungen, Lieferungen, Gutschriften usw.
- Der **Inventar-Feed für mehrere Source** aggregiert Daten zu Lagerbestandsstatus-Elementen.

SaaS-Datenexport wird als PHP-Erweiterung bereitgestellt. Es unterstützt mehrere Methoden zum Initiieren und Verwalten des Datensynchronisierungsprozesses.

- **Manuelle Synchronisierung über Admin oder die Befehlszeile**

   - Das [Daten-Management-Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard) in Commerce Admin bietet eine grafische Ansicht des Synchronisierungsstatus, der die erfolgreich mit Commerce-Services synchronisierten Produktdaten anzeigt. Sie können das Dashboard verwenden, um eine vollständige Resynchronisation (_vollständige_) aller Feeds durchzuführen. Adobe empfiehlt jedoch nur dann eine vollständige Synchronisierung, wenn Sie Adobe Commerce zum ersten Mal mit einem Commerce-Service verbinden. Siehe [Synchronisierungsprozess](data-synchronization.md).

     {{aco-data-sync-verification}}

   - Die Seite [Status der Daten-Feed](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status)Synchronisierung) bietet Echtzeiteinblicke in den Zustand und die Leistung von Datenexport-Feeds, die Produkt- und Kategoriedaten von Commerce an externe Services wie Produktempfehlungen, Live-Suche und Katalog-Service oder Adobe Commerce Optimizer übertragen.

   - Das [Adobe Commerce-Befehlszeilen-Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) bietet Befehle zum Synchronisieren bestimmter Feeds und zusätzliche Optionen zum Anpassen der Feed-Verarbeitung.

- **Automatisierte Synchronisation mit Cron-Aufträgen**

   - [Partielle Datensynchronisation](data-synchronization.md#partial-sync) - Cron-Vorgangs-Trigger führt eine partielle Datensynchronisation durch, wenn ein Commerce-Administrator eine Entität aktualisiert. Der Datenexportvorgang sendet nur diese Aktualisierungen an verbundene Commerce-Services. Der Teilsynchronisierungsprozess basiert auf dem MView-Mechanismus und erfordert keine Aktionen vom Admin-Benutzer oder Systemintegrator.

   - [Automatische Wiederholung für Synchronisierungsfehler](data-synchronization.md#retry-failed-items-sync) - Cron-Auftrags-Trigger Automatischer Versuch des Synchronisierungsprozesses, wenn während des Datensynchronisierungsprozesses Fehler auftreten.

- **Exportplanung und -leistung**

   - Entwickler und Systemintegratoren können die Zeit schätzen, die für den SaaS-Datenexport zur Synchronisierung von Daten zwischen Adobe Commerce und Connected Services erforderlich ist. Diese Schätzung kann dazu beitragen, die Verarbeitung von Datenexporten zu planen, um eine Unterbrechung der Site zu verhindern. Siehe [Schätzen des Datenvolumens und der Übertragungszeit](estimate-data-volume-sync-time.md).

   - In Fällen, in denen die Synchronisierung schneller erfolgen muss, bietet der SaaS-Datenexport Anpassungsoptionen, um die Leistung der Exportverarbeitung zu verbessern. Siehe [Verbessern der Leistung beim Datenexport](customize-export-processing.md).

- **Nachverfolgen und Fehlerbehebung bei Datenexportaktivitäten** - Verwenden Sie Datenexport- und SaaS-Exportprotokolle, um den Synchronisierungsstatus zu überprüfen und Payloads während des Synchronisierungs- und Indizierungsprozesses zu speisen. Siehe [Protokollierung und Fehlerbehebung](troubleshooting-logging.md).
