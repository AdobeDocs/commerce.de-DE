---
title: Verbinden eines anderen PayPal-Kontos für eine Website
description: Vollständiges Onboarding von PayPal im Admin-Bereich für Websites, um ein anderes PayPal-Händlerkonto mit einer einzelnen Website zu verbinden.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Paas, Saas
TQID: 'https://experienceleague.adobe.com/U1zGAU6vYKjk2tc2KXnvyqnYdbA2HKTCNZSKhHdS0Vw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%
---
# Verbinden eines anderen PayPal-Kontos für eine Website

Für Commerce-Instanzen mit **mehreren Websites** benötigen Sie möglicherweise **verschiedene PayPal-Händlerkonten**. [!DNL Payment Services] aktiviert **Website-** PayPal-Onboarding nach **global** Onboarding.

>[!NOTE]
>
> Diese Funktion unterstützt nur die Verbindung neuer Konten.

## Voraussetzungen für das Onboarding über eine Website

Onboarding auf Website-Ebene ist nur verfügbar, wenn Ihr Store diese Anforderungen erfüllt:

- [Commerce Services-Connector](https://experienceleague.adobe.com/de/docs/commerce/user-guides/integration-services/saas) Einrichtung ist abgeschlossen.
- Ein PayPal-Konto ist im globalen Umfang (Standardkonfiguration) verbunden.

Sie können dies bestätigen, indem Sie überprüfen, ob die folgenden Felder im Standardbereich ausgefüllt sind:

- [!UICONTROL Payment Services Sandbox ID]
- [!UICONTROL Payment Services Production ID]
- [!UICONTROL PayPal Merchant ID]

Wenn diese Felder leer sind, müssen Sie zunächst [globales Onboarding &#x200B;](configure-admin.md). Die Schaltfläche **[!UICONTROL Connect different account]** ist deaktiviert, bis Sie die Voraussetzungen erfüllt haben.

## Starten der Verbindung auf Website-Ebene

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Sales]**&#x200B;und wählen Sie **[!UICONTROL Payment Methods]**.
1. Wechseln Sie in der Bereichsauswahl in der oberen linken Ecke von **[!UICONTROL Default Config]** zu der **[!UICONTROL Website]**, die Sie integrieren möchten.
1. Klicken Sie auf **[!UICONTROL Connect different account]**.

   Wenn die Schaltfläche deaktiviert ist, erfüllt Ihr Store die oben genannten [Voraussetzungen](#prerequisites-global-scope) nicht.

## Abschließen des Onboarding-Modals

Ein Popup-Fenster wird geöffnet.

1. Wählen Sie Ihre **[!UICONTROL Country]** aus dem Dropdown-Menü aus.
1. Wählen Sie Ihren Onboarding-Typ aus: **[!UICONTROL Basic]** oder **[!UICONTROL Advanced]**.
1. Klicken Sie auf **[!UICONTROL Next]**.

>[!NOTE]
>
> Wenn Sie in Ungarn, Spanien oder Österreich Onboarding durchführen, müssen Sie zunächst den Link Allgemeine Geschäftsbedingungen öffnen und anzeigen, bevor Sie auf die Schaltfläche **[!UICONTROL I Accept]** klicken können. Die Schaltfläche ist deaktiviert, bis Sie die Nutzungsbedingungen öffnen.

## Bei PayPal anmelden

Nachdem Sie zum PayPal-Login weitergeleitet wurden, melden Sie sich an und führen Sie die Onboarding-Schritte innerhalb von PayPal aus.

>[!IMPORTANT]
>
> Wenn Sie auf **[!UICONTROL Confirm and Continue]** klicken, endet die Sitzung für den globalen Bereich und die Verbindung auf Website-Ebene beginnt. Wenn Sie versehentlich auf **[!UICONTROL Connect different account]** geklickt haben, können Sie den Vorgang abbrechen, indem Sie **[!UICONTROL Cancel]** auswählen oder auf das **X**-Symbol klicken, bevor Sie den Vorgang bestätigen.

## Beenden und zum Administrator zurückkehren

1. Schließen Sie nach Abschluss der PayPal-Schritte das PayPal-Fenster.
1. Klicken Sie auf **[!UICONTROL Finish]** oder auf **X** in der oberen rechten Ecke, um das Onboarding-Popup zu schließen.
1. Die Commerce-Konfigurationsseite wird automatisch aktualisiert.

## Bestätigen des Ergebnisses

Nachdem die Seite aktualisiert wurde, überprüfen Sie die Konfigurationsseite des Website-Bereichs auf:

- Eine aktualisierte **[!UICONTROL PayPal Merchant ID]** für diese Website.
- Eine Statusbeschriftung, die das Ergebnis des Onboarding anzeigt:

| Status | Bedeutung |
| --- | --- |
| `ACTIVE` | Onboarding erfolgreich abgeschlossen |
| `PENDING` | Onboarding wird noch verarbeitet |
| `ERROR` | Onboarding wurde nicht erfolgreich abgeschlossen |

Wenn ein `ERROR` angezeigt wird, wird eine Fehlermeldung angezeigt, in der das Problem erläutert wird. Sie können den Onboarding-Prozess erneut ausführen, indem Sie erneut auf **[!UICONTROL Connect different account]** klicken.
