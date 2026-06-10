---
title: '[!DNL Adobe Commerce Optimizer Connector] Versionshinweise'
description: Erfahren Sie  [!DNL Adobe Commerce Optimizer Connector]  Versionshinweise, einschließlich neuer Funktionen, Fehlerbehebungen und bekannter Probleme bei der Katalogsynchronisierung und beim Export.
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/6NeLAfThvIWIyV4Y6OWtL8V9mC7lPy7UH-Zli8E-WEk'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: f08fa0de-a550-4acd-b570-f81cf1d03aafid: e7dae43f-215c-4cdf-90d3-c5a461a6e669
subfeature_v2: id: dad884f1-e840-49a1-970e-2f965bdbc410id: a40ebd6b-b542-4432-a730-1803ef74518d
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 6d4493db5e0714577a8800007cc6d2c552578fa4
workflow-type: tm+mt
source-wordcount: 267
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

![Behebung](../assets/fix.svg) **Verbesserte [!DNL Adobe Commerce Optimizer Connector]-Konfigurationsanweisungen** - Die Seite [!DNL Adobe Commerce Optimizer]-Konfiguration im Commerce Admin wurde aktualisiert, um einen Link zum _[!DNL Adobe Commerce Optimizer Connector]-Integrationshandbuch zu erstellen_.
<!--COMOPT-1922-->

![Fehlerbehebung](../assets/fix.svg) Verbesserung **[!DNL Adobe Commerce Optimizer Connector]Metadaten** - Die [!DNL Adobe Commerce Optimizer Connector] enthält jetzt ihre installierte Version in der Metadaten-Kopfzeile. Diese Verbesserung ermöglicht es Teams, während der Fehlerbehebung oder bei Support-Interaktionen schnell zu ermitteln, welche Connector-Version verwendet wird.<!--MDEE-1323-->

### Version 1.0.12

_2. April 2026_

![Neu](../assets/new.svg) **Es wurde Unterstützung für den Kategorien-Feed in `saas:resync` Befehl hinzugefügt**-Sie können jetzt Ihre neuesten Kategoriedaten einfach mit dem `saas:resync` CLI-Befehl aktualisieren und anzeigen:

```terminal
bin/magento saas:resync --feed=categories
```

### Version 1.0.11

_10. März 2026_

![Es wurde ](../assets/fix.svg) Kompatibilitätsproblem behoben, durch das der Zugriff auf die Seite &quot;[!DNL Commerce Services Connector]-Konfiguration“ über die Menüs &quot;Commerce Admin **[!UICONTROL System]**&quot; und &quot;**[!UICONTROL Configuration]**&quot; blockiert wurde, wenn die [!DNL Adobe Commerce Optimizer Connector] auf einer [!DNL Adobe Commerce]-Instanz installiert ist.  Jetzt können Sie auf die Seite [!DNL Commerce Services Connector]-Konfiguration zugreifen, wenn beide Erweiterungen installiert sind. <!--MDEE-1322-->


### Version 1.0.10

_9. März 2026_

![Fehlerbehebung](../assets/fix.svg) Wenn Sie auf die **[!UICONTROL Data Feed Sync Status]** zugreifen, bevor Sie die Connector-Konfiguration abgeschlossen haben, werden Sie jetzt automatisch zur Connector-Konfigurationsseite weitergeleitet. Dieser geführte Fluss stellt sicher, dass die Connector-Einrichtung abgeschlossen ist, und hilft, Fehler zu vermeiden, die durch fehlende Konfigurationseinstellungen verursacht werden, die zu fehlgeschlagenen oder unvollständigen Statuselementen führen könnten.<!--MDEE-1296-->

### Version 1.0.9

_1. März 2026_

Version mit allgemeiner Verfügbarkeit der [!DNL Adobe Commerce Optimizer Connector].

>[!NOTE]
>
>Wenn Sie am Beta-Programm für das [!DNL Adobe Commerce Optimizer Connector] teilgenommen haben und eine frühere Version der Erweiterung installiert haben, aktualisieren Sie auf die Version für allgemeine Verfügbarkeit , um die neuesten Aktualisierungen zu erhalten.
