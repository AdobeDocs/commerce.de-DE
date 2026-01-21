---
title: '[!DNL Payment Services]'
description: Nach der Installation können Sie  [!DNL Payment Services]  Admin in der Store-Konfiguration konfigurieren.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: efeca11f450906ec6fd4151e9de36f4ad7a999ab
workflow-type: tm+mt
source-wordcount: '2712'
ht-degree: 0%

---

# [!DNL Payment Services]

Sie können [!DNL Payment Services] mit hilfreichen Konfigurationsoptionen im Admin an Ihre Anforderungen anpassen.

Wenn Sie [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] im Admin-Bereich konfigurieren, gelten diese Konfigurationen nur für die Umgebung, die im Feld _[!UICONTROL Method]_von_[!UICONTROL General Configuration]_ festgelegt ist. Alle Änderungen, die Sie in den Konfigurationsfeldern vornehmen, sind unabhängig davon, ob Sie die _[!UICONTROL Method]_wechseln. Wenn Sie die Methode wechseln, werden Ihre Auswahlen nicht zurückgesetzt.

## Allgemeine Konfiguration

Sie können [!DNL Payment Services] für Ihren Store und Ihre _[!UICONTROL Merchant Location]_aktivieren und im Abschnitt_[!UICONTROL General Configuration]_ entweder Sandbox-Tests oder Live-Zahlungen aktivieren.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Legen Sie das Feld _[!UICONTROL Merchant Country]_im_[!UICONTROL Merchant Location]_ fest. Wenn kein _[!UICONTROL Merchant Country]_angegeben ist, wird der_[!UICONTROL Default Country]_ aus der allgemeinen Konfiguration verwendet.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_, um auf den Abschnitt_[!UICONTROL [!DNL Payment Services]]_ zuzugreifen.
1. Erweitern Sie im Abschnitt _[!UICONTROL [!DNL Payment Services]]_den Abschnitt_[!UICONTROL General Configuration]_ .
1. Wählen **für &quot;**&quot; die Option `Yes` aus, um [!DNL Payment Services] für Ihren Store zu aktivieren.
1. Legen Sie für **Methode** den Wert auf `Sandbox` fest, wenn Sie noch [!DNL Payment Services] für Ihren Store testen, oder auf `Production`, wenn Sie bereit sind, Live-Zahlungen zu aktivieren.
1. Ihre **[!UICONTROL Payment Services Sandbox ID]**- und **[!UICONTROL Payment Services Production ID]** werden automatisch ausgefüllt, sobald Sie den [Commerce Services-Connector ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas){target=_blank} und das [!DNL Payment Services]-Dashboard zum ersten Mal aufrufen. Führen Sie diese Schritte aus, um das Onboarding für Ihre Sandbox- und/oder Produktionsumgebung abzuschließen. Diese Werte verknüpfen Ihre SaaS-ID mit [!DNL Payment Services].

   >[!WARNING]
   >
   > Wenn Sie Ihre Datenspeicher-ID im Commerce Services-Connector ändern müssen, müssen Sie Ihre [!DNL Payment Services]-ID zurücksetzen. Klicken Sie **Zahlungsdienste-ID zurücksetzen**, um Ihre Sandbox-ID zurückzusetzen. Wenn Sie Ihre [!DNL Payment Services] Sandbox-ID zurücksetzen, müssen Sie sich erneut anmelden.

1. Ihre **[!UICONTROL PayPal Merchant ID]**- und **[!UICONTROL PayPal Merchant Status]** werden automatisch von PayPal bereitgestellt, sobald Sie das [!DNL Payment Services]-Dashboard zum ersten Mal aufrufen.
1. Fügen Sie für **Soft-Deskriptor** (benutzerdefinierte Werte, die auf Bankauszügen von Kundentransaktionen angezeigt werden, um Geschäfte/Marken/Kataloge voneinander abzugrenzen) Ihren benutzerdefinierten Text (bis zu 22 Zeichen) in das Textfeld ein und ersetzen Sie `Soft descriptor` oder den vorhandenen Wert.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | Website | Aktivieren oder Deaktivieren von [!DNL Payment Services] für Ihre Website. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | Shop-Ansicht | Legen Sie die Methode oder Umgebung für Ihren Store fest. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Payment Services Sandbox ID] | Shop-Ansicht | Ihre Sandbox-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. |
| [!UICONTROL Payment Services Production ID] | Shop-Ansicht | Ihre Produktions-Händler-ID, die beim Onboarding in der Produktion (live) automatisch generiert wird. |
| [!UICONTROL PayPal Merchant ID] | Shop-Ansicht | Ihre eindeutige PayPal-Händlerkonto-ID, die beim Erstellen Ihres PayPal-Kontos generiert wird. |
| [!UICONTROL PayPal Merchant Status] | Shop-Ansicht | Status Ihrer PayPal-Händler-ID. |
| [!UICONTROL Soft Descriptor] | Website- oder Store-Ansicht | Fügen Sie Ihren Websites und Store-Ansichten einen Soft-Deskriptor hinzu, um Kundentransaktionen Informationen hinzuzufügen, die Marken, Stores oder Produktlinien abgrenzen. |

## [!UICONTROL Credit Card Fields]

Die [!UICONTROL Credit Card Fields] Zahlungsoptionen bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkartenzahlungsmethoden.

Weitere Informationen finden [ unter ](payments-options.md#paypal-smart-buttons).

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL Credit Card Fields]_ .
1. Geben Sie **[!UICONTROL Title]** Text ein (falls erforderlich), um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern.
1. Um [Zahlungsaktion festzulegen](production.md#set-payment-services-as-payment-method) wählen Sie **[!UICONTROL Authorize]** oder **Autorisieren und erfassen**.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie einen `Numeric Only` Wert in das Feld **[!UICONTROL Sort order]** ein.
1. Wählen Sie **[!UICONTROL Show on checkout page]** die Option `Yes` aus, um Kreditkartenfelder auf der Kaufbestätigungsseite zu aktivieren.
1. Wählen Sie **[!UICONTROL Vault Enabled]** die Option `Yes` aus, um das Vaulting von Kreditkarten für den Checkout zu aktivieren.
1. Wählen Sie **[!UICONTROL Vault Enabled in Admin]** die Option `Yes` aus, damit der Händler mithilfe seiner Tresorkreditkarte Bestellungen für Kunden erstellen kann.
1. Um **[!UICONTROL 3D Secure authentication]** zu aktivieren (standardmäßig `Off`), wählen Sie `Always` oder `When required`.
1. Wählen Sie **[!UICONTROL Debug Mode]** `Yes` aus, um den Debugging-Modus zu aktivieren, oder `No`, um ihn zu deaktivieren.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Shop-Ansicht | Fügen Sie den Text hinzu, der während des Checkouts als Titel für diese Zahlungsoption in der Ansicht „Zahlungsmethode“ angezeigt werden soll. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Shop-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kasse. `Numeric Only` |
| [!UICONTROL Show on checkout page] | Website | Aktivieren oder Deaktivieren von Kreditkartenfeldern auf der Kasse. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | Shop-Ansicht | Aktivieren oder Deaktivieren [Kreditkarten-Vaulting](vaulting.md). Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Möglichkeit für [Händler, Bestellungen für Kunden in der ](vaulting.md) mithilfe einer Tresorzahlmethode abzuschließen. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3D Secure authentication] | Website | Aktivieren oder deaktivieren Sie [3DS Secure Authentication](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Fastlane]

[[!DNL Fastlane by PayPal]](https://www.paypal.com/us/cshelp/article/what-is-fastlane-by-paypal-help1096) ist eine schnelle und einfache Möglichkeit, sicher online zu bezahlen. Während eines **Gast-Checkouts** können Sie Ihre Karte und Versanddetails sicher speichern, um in Zukunft noch schnellere Käufe zu ermöglichen.

Weitere Informationen finden [ unter ](payments-options.md#fastlane-button)Zahlungsoptionen“.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL Fastlane]_ .
1. Um sie zu aktivieren, wählen Sie `Yes` für die **[!UICONTROL Enable Fastlane]** aus (`No` deaktiviert sie).

   >[!NOTE]
   >
   > Wenn [!UICONTROL Fastlane] aktiviert ist, ist die Option &quot;[!UICONTROL Credit Card Fields] Zahlung“ deaktiviert.

1. Geben Sie **[!UICONTROL Title]** Text ein (falls erforderlich), um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern. Der Standardtitel lautet `Credit Card (via Fastlane)`
1. Um [Zahlungsaktion festzulegen](production.md#set-payment-services-as-payment-method) wählen Sie **[!UICONTROL Authorize]** oder **Autorisieren und erfassen**.
1. Um **[!UICONTROL 3D Secure Authentication for Fastlane]** (standardmäßig `Off`) zu aktivieren, wählen Sie `When required`, um die EU-Vorschriften einzuhalten, oder `Always` Sie eine zusätzliche Betrugsschutzschicht hinzufügen.

   >[!NOTE]
   >
   > Wenn der Kartenaussteller eine sichere 3D-Authentifizierung erfordert, kann dieser Schritt unabhängig von der [!UICONTROL Payment Services]-Konfiguration nicht umgangen werden.

1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie einen `Numeric Only` Wert in das Feld **[!UICONTROL Sort order]** ein.
1. Geben Sie an, ob das [!UICONTROL Fastlane]-Branding während des Auscheckens in Adobe Commerce aktiviert sein soll, indem Sie das Feld **[!UICONTROL Enable messaging]** auf `Yes` setzen.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Enable Fastlane] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL Fastlane] auf der Kaufbestätigungsseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Title] | Shop-Ansicht | Fügen Sie den Text hinzu, der während des Checkouts als Titel für diese Zahlungsoption in der Ansicht „Zahlungsmethode“ angezeigt werden soll. Der Standardwert ist `Credit Card (via Fastlane)`. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL 3D Secure authentication] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [3D Secure Authentication für Fastlane](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Sort order] | Shop-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kasse. `Numeric Only` |
| [!UICONTROL Enable messaging] | Shop-Ansicht | Geben Sie an, ob das [!UICONTROL Fastlane]-Branding beim Auschecken in Adobe Commerce aktiviert sein soll. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

### Optional. Erweiterte Stileinstellungen

Mit diesen optionalen Einstellungen können Sie anpassen, wie [!UICONTROL Fastlane] auf Ihrer Website angezeigt werden.

>[!TIP]
>
>Stile, die nicht den Richtlinien für Barrierefreiheit entsprechen, werden auf die Standardeinstellungen zurückgesetzt.

1. Navigieren Sie im Abschnitt _[!UICONTROL Payment Services]_zum Abschnitt_[!UICONTROL Fastlane]_ .
1. Erweitern Sie den Abschnitt _[!UICONTROL Advanced Style Settings (optional)]_.
1. Ändern Sie die Einstellungen nach Bedarf.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.

Weitere Informationen [ Anpassung finden Sie ](https://developer.paypal.com/limited-release/accelerated-checkout-bt/) den PayPal-Entwicklerdokumenten .

#### Root-Einstellungen

Mit diesen optionalen Einstellungen wird die gesamte [!UICONTROL Fastlane]-Auscheckkomponente geändert.

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Background Color] | Shop-Ansicht | Definiert die Hintergrundfarbe der Komponente. Nur `RGB` Werte |
| [!UICONTROL Border Color] | Shop-Ansicht | Definiert die Rahmenfarbe der Komponente. Nur `RGB` Werte |
| [!UICONTROL Font Family] | Shop-Ansicht | Legt die Schriftart der Komponente fest. Es werden nur die im Design verfügbaren Schriftarten angezeigt |
| [!UICONTROL Font Size Base] | Shop-Ansicht | Definiert die Schriftgröße. Nur `px` Werte (Pixel) |
| [!UICONTROL Padding] | Shop-Ansicht | Legt den Abstand in der Komponente fest. Nur `px` Werte (Pixel) |
| [!UICONTROL Primary Color] | Shop-Ansicht | Definiert die Hauptfarbe der Komponente. Nur `RGB` Werte |
| [!UICONTROL Text Color] | Shop-Ansicht | Definiert die Hauptfarbe des Textes in der Komponente. Nur `RGB` Werte |

#### Eingabeeinstellungen

Diese optionalen Einstellungen gelten für die Kundeneingabefelder Ihrer [!UICONTROL Fastlane].

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Background Color] | Shop-Ansicht | Definiert die Hintergrundfarbe der Komponente. Nur `RGB` Werte |
| [!UICONTROL Border Color] | Shop-Ansicht | Definiert die Rahmenfarbe der Komponente. Nur `RGB` Werte |
| [!UICONTROL Border Radius] | Shop-Ansicht | Definiert den Radius des Rahmens. Nur `px` Werte (Pixel) |
| [!UICONTROL Border Width] | Shop-Ansicht | Definiert die Breite des Rahmens. Nur `px` Werte (Pixel) |
| [!UICONTROL Focus Border Color] | Shop-Ansicht | Definiert die Rahmenfarbe des Fokus der Komponente. Nur `RGB` Werte |
| [!UICONTROL Text Color Base] | Shop-Ansicht | Definiert die Hauptfarbe des Textes in der Komponente. Nur `RGB` Werte |

## [!UICONTROL Apple Pay]

Mit [!DNL Apple Pay] können Händler in Safari ein sicheres, schnelles und nahtloses Checkout-Erlebnis bieten - mit Unterstützung für bis zu 99 Domains pro Händlerkonto. Mit der Schaltfläche &quot;[!DNL Apple Pay]&quot; werden automatisch Zahlungs-, Kontakt- und Versandinformationen vom iOS- oder macOS-Gerät des Kunden ausgefüllt, was schnelle, einmalige Käufe ermöglicht, die die Konversionsraten steigern können.

Weitere Informationen finden [ unter ](payments-options.md#apple-pay-button).

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL Apple Pay]_ .
1. Geben Sie **[!UICONTROL Title]** Text ein (falls erforderlich), um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern.
1. Um [Zahlungsaktion festzulegen](production.md#set-payment-services-as-payment-method) wählen Sie **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]**.
1. Geben Sie an, wo die [!DNL Apple Pay] Option in Adobe Commerce aktiviert sein soll, indem Sie `Yes` der folgenden Optionen nach Bedarf auswählen:
   * **[!UICONTROL Show Apple Pay on checkout page]**
   * **[!UICONTROL Show Apple Pay on product detail page]**
   * **[!UICONTROL Show Apple Pay in mini cart preview]**
   * **[!UICONTROL Show Apple Pay on cart page]**
1. Um den Debugging-Modus zu aktivieren, wählen Sie `Yes` für die **[!UICONTROL Debug Mode]** aus (`No` deaktiviert ihn).
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Shop-Ansicht | Fügen Sie den Text hinzu, der während des Checkouts als Titel für diese Zahlungsoption in der Ansicht „Zahlungsmethode“ angezeigt werden soll. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | Website | Aktivieren oder Deaktivieren von [!DNL Apple Pay] auf der Kaufbestätigungsseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | Shop-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kasse. `Numeric Only` |
| [!UICONTROL Show buttons on product detail page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL Apple Pay] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Apple Pay] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Apple Pay] in auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Google Pay]

Mit der [!UICONTROL Google Pay] Zahlungsoption kann der Händler Google Pay an seine Kunden anbieten, die die Google Wallet auf ihren Geräten verwenden können, um Käufe zu tätigen.

Weitere Informationen finden [ unter ](payments-options.md#google-pay-button).

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL Google Pay]_ .
1. (Optional) Ändern Sie den Namen der Zahlungsmethode, die während der Kasse angezeigt wird, indem Sie den neuen Namen in das Feld **[!UICONTROL Title]** eingeben.
1. [Legen Sie die Zahlungsaktion fest](production.md#set-payment-services-as-payment-method) indem Sie **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]** auswählen.
1. Geben Sie an, wo die [!DNL Google Pay] Option in Adobe Commerce aktiviert sein soll, indem Sie `Yes` der folgenden Optionen nach Bedarf auswählen:
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. Um **[!UICONTROL 3D Secure authentication]** zu aktivieren (standardmäßig `Off`), wählen Sie `Always` oder `When required`.
1. Um den Debugging-Modus zu aktivieren, wählen Sie `Yes` für die **[!UICONTROL Debug Mode]** aus (`No` deaktiviert ihn).
1. Konfigurieren Sie das Erscheinungsbild der _[!UICONTROL Google Pay]_-Schaltfläche, indem Sie die **[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**und **[!UICONTROL Button Style]**nach Bedarf auswählen.
1. Zum Festlegen der Höhe wird der Standardwert für die in **[!UICONTROL Button Style]** definierte Höhe verwendet.
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Shop-Ansicht | Gibt die Textbeschriftung an, die für diese Zahlungsoption während des Checkouts in der Zahlungsmethodenansicht angezeigt wird. Optionen: `[!UICONTROL text field]` |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: `[!UICONTROL Authorize]` / `[!UICONTROL Authorize and Capture]` |
| [!UICONTROL Show on checkout page] | Website | Aktivieren oder Deaktivieren von [!DNL Google Pay] auf der Kaufbestätigungsseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | Shop-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kasse. `Numeric Only` |
| [!UICONTROL Show buttons on product detail page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL Google Pay] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Google Pay] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL Google Pay] auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL 3D Secure authentication] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [3D Secure Authentication](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Button Color] | Shop-Ansicht | Farbe der Schaltfläche &quot;[!DNL Google Pay]&quot; definieren. Optionen: `[!UICONTROL Default]` / `[!UICONTROL Black]` / `[!UICONTROL White]` |
| [!UICONTROL Button Type] | Shop-Ansicht | Typ der [!DNL Google Pay]-Schaltfläche definieren. Optionen: `[!UICONTROL buy]` / `[!UICONTROL checkout]` / `[!UICONTROL order]` / `[!UICONTROL pay]` / `[!UICONTROL plain]` |

Weitere Informationen finden Sie in der Dokumentation zu den Objektoptionen für die Google Pay[API-Anfrage .](https://developers.google.com/pay/api/web/reference/request-objects)

## [!DNL PayPal Payment Buttons]

Die [!DNL PayPal payment buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden.

Weitere Informationen finden [ unter ](payments-options.md#paypal-smart-buttons).

Konfigurieren von [!DNL PayPal payment buttons]

Sie können die Zahlungsoptionen der PayPal-Zahlungs-Buttons im Admin-Bereich aktivieren und konfigurieren:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL PayPal payment buttons]_ .
1. Um den Namen der Zahlungsmethode zu ändern, wie er während des Checkouts angezeigt wird, bearbeiten Sie das _[!UICONTROL Title]_.
1. Um [Zahlungsaktion festzulegen](production.md#set-payment-services-as-payment-method) wählen Sie **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]**.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie einen `Numeric Only` Wert in das Feld **[!UICONTROL Sort order]** ein.
1. Um „Später bezahlen[ zu aktivieren/deaktivieren](payments-options.md#pay-later-button) wählen Sie `Yes`/`No` für **[!UICONTROL Display Pay Later Message]** aus.

   * Wenn Sie die Option [Später bezahlen](payments-options.md#pay-later-button) aktivieren, wird eine modale **[!UICONTROL Configure Messaging]**-Schaltfläche angezeigt, über die Sie die Stile für die **[!UICONTROL PayPal Pay Later messaging]** festlegen können.

1. Geben Sie an, wo die PayPal-Zahlungsschaltflächen in Adobe Commerce aktiviert sein sollen, indem Sie `Yes` in den folgenden Optionen nach Bedarf auswählen:
   * **[!UICONTROL Show buttons on checkout page]**
   * **[!UICONTROL Show buttons on product detail page]**
   * **[!UICONTROL Show buttons in mini cart preview]**
   * **[!UICONTROL Show buttons on cart page]**
1. Um Venmo als Zahlungsoption zu aktivieren, wählen Sie `Yes` für **[!UICONTROL Venmo Enabled]** aus.
1. Um Kredit- und Debitkarten als Zahlungsoption zu aktivieren (PayPal Smart Button), wählen Sie `Yes` für **[!UICONTROL Credit and Debit Card Enabled]**.
1. Um die Zahlungsoption [PayPal Pay Later](payments-options.md#pay-later-button) zu aktivieren, wählen Sie `Yes`/`No` für **[!UICONTROL PayPal Pay Later Enabled]** aus.
1. Um den Debugging-Modus zu aktivieren, wählen Sie `Yes` für die **[!UICONTROL Debug Mode]** aus (`No` deaktiviert ihn).
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Shop-Ansicht | Fügen Sie den Text hinzu, der während des Checkouts als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode angezeigt werden soll. Optionen: Textfeld |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | Website | Aktivieren oder deaktivieren Sie die PayPal-Nachricht Pay Later im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Kaufvorgangs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Configure Messaging] | Shop-Ansicht | Ändern Sie die PayPal-Messaging-Stile Später bezahlen . Optionen: `[!UICONTROL Product page]` / `[!UICONTROL Cart]` |
| [!UICONTROL Show buttons on checkout page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL PayPal payment buttons] auf der Kaufbestätigungsseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL PayPal payment buttons] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] in auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo, in der die Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Kreditkarten- und Debitkartenoptionen, wenn die Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Option „PayPal Später bezahlen“, wenn die Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_Optionen der Zahlungs-Schaltflächen konfigurieren:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL [!DNL Payment Services]]_den Abschnitt_[!UICONTROL PayPal Smart Button Styling]_ .
1. Um das Layout festzulegen, wählen Sie `Vertical` oder `Horizontal` für **[!UICONTROL Layout]**
1. Um die Farbe festzulegen, wählen Sie aus den verfügbaren Farben in **[!UICONTROL Color]**.
1. Um die Form festzulegen, wählen Sie `Rectangular` oder `Pill` für die **[!UICONTROL Shape]** aus.
1. Um die Standardhöhe zu verwenden, wählen Sie `Yes` oder `No` für die **[!UICONTROL Use Default Height]** aus.
1. Um die benutzerdefinierte Höhe festzulegen, fügen Sie die gewünschte Pixelhöhe für **[!UICONTROL Height]** hinzu.
1. Um den Slogan festzulegen, wählen Sie `Yes` oder `No` für **[!UICONTROL Tagline]**.
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|--- |--- |--- |
| [!UICONTROL Layout] | Shop-Ansicht | Definieren Sie den Stil des Layouts für PayPal-Zahlungsschaltflächen. Optionen: `[!UICONTROL Vertical]` / `[!UICONTROL Horizontal]` |
| [!UICONTROL Color] | Shop-Ansicht | Farbe der PayPal-Zahlungs-Buttons definieren. Optionen: [!UICONTROL Blue] / `[!UICONTROL Gold]` / `[!UICONTROL Silver]` / `[!UICONTROL White]` / `[!UICONTROL Black]` |
| [!UICONTROL Shape] | Shop-Ansicht | Definieren Sie die Form der PayPal-Zahlungsschaltflächen. Optionen: `[!UICONTROL Rectangular]` / `[!UICONTROL Pill]` |
| [!UICONTROL Use Default Height] | Shop-Ansicht | Definiert, ob die PayPal-Zahlungs-Schaltflächen eine Standardhöhe verwenden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Height] | Shop-Ansicht | Definieren Sie die Höhe der PayPal-Zahlungs-Schaltflächen. Standardwert: keiner |
| [!UICONTROL Label] | Shop-Ansicht | Definieren Sie den Titel, der in den PayPal-Zahlungs-Schaltflächen angezeigt wird. Optionen: `[!UICONTROL PayPal]` / `[!UICONTROL Checkout]` / `[!UICONTROL Buynow]` / `[!UICONTROL Pay]` / `[!UICONTROL Installment]` |
| [!UICONTROL Tagline] | Shop-Ansicht | Aktiviert das Slogan. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Leeren des Cache

Wenn Sie die Konfiguration in _Einstellungen_ ändern, z. B. durch Umschalten der Schaltflächen &quot;Apple Pay“, „Venmo“ oder „PayPal PayLater“, leeren Sie den Cache manuell, damit Ihr Store die neuesten Konfigurationen anzeigt.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Wenn ein Cache-Typ in der Cache-Management-Tabelle einen `INVALIDATED` hat, zeigt Ihr Store möglicherweise nicht die neueste Konfiguration für dieses Element an. Leeren Sie den Cache, um Ihren Store zu aktualisieren und die neueste Konfiguration anzuzeigen.

Um sicherzustellen, dass Ihr Store die richtige Konfiguration anzeigt, [ Sie regelmäßig den Cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management).

## Rollen konfigurieren

Um sicherzustellen, dass Admin-Benutzerinnen und -Benutzer Bestellungen in der Commerce Admin erstellen und verwalten können, aktivieren Sie [!DNL Payment Services] Ressourcen für Benutzerrollen.

Unter [Benutzerrollen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html) erfahren Sie, wie Sie Rollen verwalten.

Beim Zuweisen von Ressourcen zur Rolle müssen Sie Folgendes auswählen:

* **Mit[!DNL Payment Services]** bezahlen - Diese Ressource stellt sicher, dass beim Erstellen einer Bestellung in der Admin-Benutzeroberfläche [!DNL Payment Services] Kreditkarten als Zahlungsmethode verfügbar sind. Wenn Sie die übergeordnete Ressource **Aktionen** auswählen, wird diese Ressource ebenfalls ausgewählt.

* **[!DNL Payment Services]** - Diese Ressource umfasst die Ressourcen **Dashboard** und **SaaS Services Proxy** die ebenfalls ausgewählt werden müssen. Sie stellen sicher, dass [!DNL Payment Services] im Menü _Verkauf_ angezeigt wird.

  ![Zahlungsdienstressourcen](assets/roles-payments.png){width="400" zoomable="yes"}


## Kartengewölbe

Sie können Funktionen aktivieren, mit denen Ihre Kunden ihre Kreditkarteninformationen in ihrem Konto für zukünftige Käufe tresoren - oder „speichern“ - können.

Sie können in der Admin-Instanz auch das Vaulting von Karten verwenden, um nachfolgende Bestellungen für Bestandskunden abzuschließen.

Aktivieren oder deaktivieren Sie das Vaulting von Karten in [Einstellungen für Kreditkartenfelder](#credit-card-fields).

Weitere Informationen [ Sie unter ](vaulting.md)Kreditkartenabwicklung).

## 3DS

3DS schützt Kunden und Händler vor betrügerischen Aktivitäten in ihren Geschäften und ermöglicht die Einhaltung von EU-Standards.

Aktivieren oder deaktivieren Sie 3DS in den [Kreditkartenfeldeinstellungen](#credit-card-fields).

Weitere Informationen finden Sie unter [3DS ](security.md#3ds) Sicherheit).

## Mehrere PayPal-Konten verwenden

In [!UICONTROL Payment Services] können Sie mehrere PayPal-Konten innerhalb von **einem**-Händlerkonto auf Website-Ebene verwenden. Wenn Sie beispielsweise Ihr(e) Geschäft(e) in mehreren Ländern betreiben (die unterschiedliche [Währungen](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency) verwenden) oder Adobe Commerce für einige Teile Ihres Unternehmens, aber nicht _alle_ verwenden möchten, können Sie Ihr Händlerkonto so einrichten, dass mehrere PayPal-Konten verwendet werden.

Weitere [ zur Hierarchie von Websites, Stores und Store](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)Ansichten finden Sie unter „Site, Store und View Scope“.

Siehe [Befehlszeilenkonfiguration](configure-cli.md#configure-scope-via-cli) für weitere Informationen zur Konfiguration von Bereichen für mehrere PayPal-Konten über die CLI.

Ihr Vertriebsmitarbeiter kann einen neuen [Umfang](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) für Ihr Händlerkonto erstellen und die zusätzliche Site mit PayPal integrieren, sodass jede der PayPal-Schaltflächen, die Sie konfigurieren, auf Ihrer Site angezeigt wird. Vertrieb kontaktieren
Ansprechpartner für Unterstützung bei der Verwendung mehrerer PayPal-Konten für Ihre Websites.
