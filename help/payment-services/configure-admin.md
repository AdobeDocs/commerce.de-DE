---
title: Konfiguration für alte Zahlungsdienste
description: Nach der Installation können Sie  [!DNL Payment Services]  Admin in der Store-Konfiguration konfigurieren.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 51b3f5fffda1402d25bb57402eae82afc8515a14
workflow-type: tm+mt
source-wordcount: '1758'
ht-degree: 0%

---

# Alte [!DNL Payment Services]

Sie können [!DNL Payment Services] mit hilfreichen Konfigurationsoptionen im Admin an Ihre Anforderungen anpassen.

Wenn Sie [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] im Admin-Bereich konfigurieren, gelten diese Konfigurationen nur für die Umgebung, die im Feld _[!UICONTROL Method]_&#x200B;von&#x200B;_[!UICONTROL General Configuration]_ festgelegt ist. Alle Änderungen, die Sie in den Konfigurationsfeldern vornehmen, sind unabhängig davon, ob Sie die _[!UICONTROL Method]_&#x200B;wechseln. Wenn Sie die Methode wechseln, werden Ihre Auswahlen nicht zurückgesetzt.

## Allgemeine Konfiguration

Sie können [!DNL Payment Services] für Ihren Store und Ihre _[!UICONTROL Merchant Location]_&#x200B;aktivieren und im Abschnitt&#x200B;_[!UICONTROL General Configuration]_ entweder Sandbox-Tests oder Live-Zahlungen aktivieren.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Legen Sie das Feld _[!UICONTROL Merchant Country]_&#x200B;im&#x200B;_[!UICONTROL Merchant Location]_ fest. Wenn kein _[!UICONTROL Merchant Country]_&#x200B;angegeben ist, wird der&#x200B;_[!UICONTROL Default Country]_ aus der allgemeinen Konfiguration verwendet.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_, um auf den Abschnitt&#x200B;_[!UICONTROL [!DNL Payment Services]]_ zuzugreifen.
1. Erweitern Sie im Abschnitt _[!UICONTROL [!DNL Payment Services]]_&#x200B;den Abschnitt&#x200B;_[!UICONTROL General Configuration]_ .
1. Wählen **für &quot;**&quot; die Option `Yes` aus, um [!DNL Payment Services] für Ihren Store zu aktivieren.
1. Legen Sie für **Methode** den Wert auf `Sandbox` fest, wenn Sie noch [!DNL Payment Services] für Ihren Store testen, oder auf `Production`, wenn Sie bereit sind, Live-Zahlungen zu aktivieren.
1. Ihre **[!UICONTROL Payment Services Sandbox ID]**- und **[!UICONTROL Payment Services Production ID]** werden automatisch ausgefüllt, sobald Sie den [Commerce Services-Connector ](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/user-guides/integration-services/saas){target=_blank} und das [!DNL Payment Services]-Dashboard zum ersten Mal aufrufen. Führen Sie diese Schritte aus, um das Onboarding für Ihre Sandbox- und/oder Produktionsumgebung abzuschließen. Diese Werte verknüpfen Ihre SaaS-ID mit [!DNL Payment Services].

   >[!WARNING]
   >
   > Wenn Sie Ihre Datenspeicher-ID im Commerce Services-Connector ändern müssen, müssen Sie Ihre [!DNL Payment Services]-ID zurücksetzen. Klicken Sie **Zahlungsdienste-ID zurücksetzen**, um Ihre Sandbox- oder Produktions-IDs zurückzusetzen. Wenn Sie Ihre [!DNL Payment Services] IDs zurücksetzen, müssen Sie sich erneut anmelden.

1. Ihre **[!UICONTROL PayPal Merchant ID]**- und **[!UICONTROL PayPal Merchant Status]** werden automatisch von PayPal bereitgestellt, sobald Sie das [!DNL Payment Services]-Dashboard zum ersten Mal aufrufen.
1. Fügen Sie für **Soft-Deskriptor** (benutzerdefinierte Werte, die auf Bankauszügen von Kundentransaktionen angezeigt werden, um Geschäfte/Marken/Kataloge voneinander abzugrenzen) Ihren benutzerdefinierten Text (bis zu 22 Zeichen) in das Textfeld ein und ersetzen Sie `Soft descriptor` oder den vorhandenen Wert.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

![Ansicht der vorgestellten Adobe-Lösung](assets/config-view-all.png){width="700" zoomable="yes"}

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
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_&#x200B;den Abschnitt&#x200B;_[!UICONTROL Credit Card Fields]_ .
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
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=de) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Shop-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kasse. `Numeric Only` |
| [!UICONTROL Show on checkout page] | Website | Aktivieren oder Deaktivieren von Kreditkartenfeldern auf der Kasse. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | Shop-Ansicht | Aktivieren oder Deaktivieren [Kreditkarten-Vaulting](vaulting.md). Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Möglichkeit für [Händler, Bestellungen für Kunden in der ](vaulting.md) mithilfe einer Tresorzahlmethode abzuschließen. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3D Secure authentication] | Website | Aktivieren oder deaktivieren Sie [3DS Secure Authentication](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

Mit der [!UICONTROL Apple Pay] Zahlungsoption kann der Händler seinen Kunden Apple Pay anbieten. Diese können die Touch ID auf ihren Geräten verwenden, um Käufe über den Safari-Browser zu tätigen. Händler können bis zu 99 Domains pro Händlerkonto hinzufügen.

Weitere Informationen finden [ unter ](payments-options.md#apple-pay-button).

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_&#x200B;den Abschnitt&#x200B;_[!UICONTROL Apple Pay]_ .
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
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=de) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
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
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_&#x200B;den Abschnitt&#x200B;_[!UICONTROL Google Pay]_ .
1. (Optional) Ändern Sie den Namen der Zahlungsmethode, die während der Kasse angezeigt wird, indem Sie den neuen Namen in das Feld **[!UICONTROL Title]** eingeben.
1. [Legen Sie die Zahlungsaktion fest](production.md#set-payment-services-as-payment-method) indem Sie **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]** auswählen.
1. Geben Sie an, wo die [!DNL Google Pay] Option in Adobe Commerce aktiviert sein soll, indem Sie `Yes` der folgenden Optionen nach Bedarf auswählen:
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. Um **[!UICONTROL 3D Secure authentication]** zu aktivieren (standardmäßig `Off`), wählen Sie `Always` oder `When required`.
1. Um den Debugging-Modus zu aktivieren, wählen Sie `Yes` für die **[!UICONTROL Debug Mode]** aus (`No` deaktiviert ihn).
1. Konfigurieren Sie das Erscheinungsbild der _[!UICONTROL Google Pay]_-Schaltfläche, indem Sie die **[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**&#x200B;und **[!UICONTROL Button Style]**&#x200B;nach Bedarf auswählen.
1. Zum Festlegen der Höhe wird der Standardwert für die in **[!UICONTROL Button Style]** definierte Höhe verwendet.
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Shop-Ansicht | Gibt die Textbeschriftung an, die für diese Zahlungsoption während des Checkouts in der Zahlungsmethodenansicht angezeigt wird. Optionen: `[!UICONTROL text field]` |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=de) für die angegebene Zahlungsmethode. Optionen: `[!UICONTROL Authorize]` / `[!UICONTROL Authorize and Capture]` |
| [!UICONTROL Show on checkout page] | Website | Aktivieren oder Deaktivieren von [!DNL Google Pay] auf der Kaufbestätigungsseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | Shop-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kasse. `Numeric Only` |
| [!UICONTROL Show buttons on product detail page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL Google Pay] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Google Pay] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL Google Pay] auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL 3D Secure authentication] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [3D Secure Authentication](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Button Color] | Shop-Ansicht | Farbe der Schaltfläche &quot;[!DNL Google Pay]&quot; definieren. Optionen: `[!UICONTROL Default]` / `[!UICONTROL Black]` / `[!UICONTROL White]` |
| [!UICONTROL Button Type] | Shop-Ansicht | Typ der [!DNL Google Pay]-Schaltfläche definieren. Optionen: `[!UICONTROL buy]` / `[!UICONTROL checkout]` / `[!UICONTROL order]` / `[!UICONTROL pay]` / `[!UICONTROL plain]` |

Weitere Informationen finden Sie in der Dokumentation zu den Objektoptionen für die Google Pay[&#128279;](https://developers.google.com/pay/api/web/reference/request-objects)API-Anfrage .

## [!DNL PayPal Payment Buttons]

Die [!DNL PayPal payment buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden.

Weitere Informationen finden [ unter ](payments-options.md#paypal-smart-buttons).

Konfigurieren von [!DNL PayPal payment buttons]

Sie können die Zahlungsoptionen der PayPal-Zahlungs-Buttons im Admin-Bereich aktivieren und konfigurieren:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_&#x200B;den Abschnitt&#x200B;_[!UICONTROL PayPal payment buttons]_ .
1. Um den Namen der Zahlungsmethode zu ändern, wie er während des Checkouts angezeigt wird, bearbeiten Sie das _[!UICONTROL Title]_.
1. Um [Zahlungsaktion festzulegen](production.md#set-payment-services-as-payment-method) wählen Sie **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]**.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie einen `Numeric Only` Wert in das Feld **[!UICONTROL Sort order]** ein.
1. Um „Später bezahlen[ zu aktivieren/deaktivieren](payments-options.md#pay-later-button) wählen Sie `Yes`/`No` für **[!UICONTROL Display Pay Later Message]** aus.
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
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/de/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | Website | Aktivieren oder deaktivieren Sie die Pay-Later-Nachricht im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Kaufvorgangs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL PayPal payment buttons] auf der Kaufbestätigungsseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL PayPal payment buttons] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] in auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo, in der die Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Kreditkarten- und Debitkartenoptionen, wenn die Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Option „PayPal Später bezahlen“, wenn die Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_&#x200B;Optionen der Zahlungs-Schaltflächen konfigurieren:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL [!DNL Payment Services]]_&#x200B;den Abschnitt&#x200B;_[!UICONTROL PayPal Smart Button Styling]_ .
1. Um das Layout festzulegen, wählen Sie `Vertical` oder `Horizontal` für **[!UICONTROL Layout]**
1. Um die Farbe festzulegen, wählen Sie aus den verfügbaren Farben in **[!UICONTROL Color]**.
1. Um die Form festzulegen, wählen Sie `Rectangular` oder `Pill` für die **[!UICONTROL Shape]** aus.
1. Um die Standardhöhe zu verwenden, wählen Sie `Yes` oder `No` für die **[!UICONTROL Use Default Height]** aus.
1. Um die benutzerdefinierte Höhe festzulegen, fügen Sie die gewünschte Pixelhöhe für **[!UICONTROL Height]** hinzu.
1. Um den Slogan festzulegen, wählen Sie `Yes` oder `No` für **[!UICONTROL Tagline]**.
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können auch die Gestaltung der Zahlungs-Schaltfläche [in Einstellungen](settings.md#button-style) über die Zahlungsdienste-Startseite konfigurieren.

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

Wenn Sie die Konfiguration ändern, [leeren Sie den Cache manuell](/help/payment-services/settings.md#flush-the-cache) sodass Ihr Store die neuesten Konfigurationseinstellungen anzeigt.
