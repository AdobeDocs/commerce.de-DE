---
title: '[!DNL Adobe Commerce Optimizer Connector] Versionshinweise'
description: Die neuesten Versionsinformationen für  [!DNL Adobe Commerce Optimizer Connector]  für Adobe Commerce.
feature: Services, Catalog Service, Release Notes
source-git-commit: e0f7b9b860f8dce18b357d479cbc021f32970c18
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Versionshinweise zum Adobe Commerce Optimizer-Connector

In diesen Versionshinweisen werden alle Versionen für die [!DNL Adobe Commerce Optimizer Connector] beschrieben. Sie enthalten:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

## Versionen 2026

### Version 1.0.13

_6. Mai 2026_

![Beheben](../assets/fix.svg) **Verbesserte Connector-Konfigurationsanweisungen**-Die Seite &quot;Commerce Optimizer-Konfiguration“ in Commerce Admin wurde aktualisiert, um eine Verknüpfung mit dem _Adobe Commerce Connector-Handbuch herzustellen_. <!--COMOPT-1922-->
![Fehlerbehebung](../assets/fix.svg) Verbesserung der **-Connector**-Der ACO-Connector fügt jetzt seine installierte Version in die Metadaten-Kopfzeile ein. Diese Verbesserung ermöglicht es Teams, während der Fehlerbehebung oder bei Support-Interaktionen schnell zu ermitteln, welche Connector-Version verwendet wird.<!--MDEE-1323-->

### Version 1.0.12

_2. April 2026_

![Neu](../assets/new.svg) **Es wurde Unterstützung für den Feed Kategorien in `saas:resync` Befehl &#x200B;** hinzugefügt. Mit dem `saas:resync` CLI-Befehl können Sie jetzt Ihre neuesten Kategoriedaten einfach aktualisieren und anzeigen:

```terminal
bin/magento saas:resync --feed=categories
```

_10. März 2026_

![Es wurde &#x200B;](../assets/fix.svg) Kompatibilitätsproblem behoben, durch das der Zugriff auf die Seite &quot;Commerce Services Connector-Konfiguration“ über das Commerce Admin-System und die Konfigurationsmenüs blockiert wurde, wenn der Adobe Commerce Optimizer Connector auf einer Commerce-Instanz installiert ist.  Jetzt können Sie auf die Commerce Services Connector-Konfigurationsseite zugreifen, wenn beide Erweiterungen installiert sind. <!--MDEE-1322-->


### Version 1.0.10

_9. März 2026_

![Fehlerbehebung](../assets/fix.svg) Wenn Sie auf die Seite „Status der Daten-Feed-Synchronisierung“ zugreifen, bevor Sie die Connector-Konfiguration abgeschlossen haben, werden Sie jetzt automatisch zur Seite „Connector-Konfiguration“ weitergeleitet. Dieser geführte Fluss stellt sicher, dass die Connector-Einrichtung abgeschlossen ist, und hilft, Fehler zu vermeiden, die durch fehlende Konfigurationseinstellungen verursacht werden, die zu fehlgeschlagenen oder unvollständigen Statuselementen führen könnten.<!--MDEE-1296-->

### Version 1.0.9

_1. März 2026_

Version mit allgemeiner Verfügbarkeit von Adobe Commerce Optimizer Connector.

>[!NOTE]
>
>Wenn Sie am Beta-Programm für den Adobe Commerce Optimizer-Connector teilgenommen haben und eine frühere Version der Erweiterung installiert haben, aktualisieren Sie auf die Version für allgemeine Verfügbarkeit , um die neuesten Aktualisierungen zu erhalten.

