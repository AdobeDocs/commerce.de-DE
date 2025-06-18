---
title: Einstellungen für Zahlungsdienste
description: Nach der Installation können Sie Folgendes  [!DNL Payment Services]  der Startseite konfigurieren.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
feature: Payments, Checkout, Configuration, Paas, Saas
source-git-commit: 9e7eb509aa19f3382d36221ac0c7dcf2130e8d8d
workflow-type: tm+mt
source-wordcount: '2420'
ht-degree: 0%

---

# Einstellungen

Sie können [!DNL Payment Services] mit hilfreichen Einstellungen auf der [!DNL Payment Services]-Startseite an Ihre Anforderungen anpassen.

Um [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] zu konfigurieren, klicken Sie auf **[!UICONTROL Settings]**. Diese Konfigurationsoptionen gelten nur für die Umgebung, die im Feld _[!UICONTROL Payment mode]_&#x200B;der Konfigurationsoptionen[_ Allgemein _festgelegt ](#configure-general-settings).

Informationen zur Multi-Store- oder Legacy-Konfiguration finden Sie [Konfigurieren von in der Admin-](configure-admin.md)).

## Konfigurieren allgemeiner Einstellungen

Die [!UICONTROL General] bieten die Möglichkeit, Zahlungsdienste als Zahlungsmethode zu aktivieren oder zu deaktivieren und Kundentransaktionen Informationen hinzuzufügen, um eine Website- oder Store-Ansicht mit benutzerdefinierten Informationen zu markieren oder voranzustellen.

### Zahlungsdienste aktivieren

Sie können [!DNL Payment Services] für Ihre Website aktivieren und entweder Sandbox-Tests oder Live-Zahlungen aktivieren.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

1. Klicken Sie auf **[!UICONTROL Settings]**. Weitere Informationen finden [ unter „Einführung  [!DNL Payment Services] Startseite](payments-home.md) .

   ![React-Einstellungsansicht](assets/react-settings-view.png){width="500" zoomable="yes"}

   Der Abschnitt _[!UICONTROL General]_&#x200B;enthält Einstellungen, mit denen [!DNL Payment Services] als Zahlungsmethode aktiviert wird.

1. Um [!DNL Payment Services] als Zahlungsmethode für Ihren Store zu aktivieren, schalten Sie im Abschnitt _[!UICONTROL General]_&#x200B;den **[!UICONTROL Enable Payment Services as payment method]**&#x200B;auf `Yes` um.

1. Wenn Sie noch [!DNL Payment Services] für Ihren Store testen, setzen Sie **Zahlungsmodus** auf `Sandbox`. Wenn Sie bereit sind, Live-Zahlungen zu aktivieren, setzen Sie sie auf `Production`.

1. Ihre **[!UICONTROL Payment Services Sandbox ID]**- und **[!UICONTROL Payment Services Production ID]** werden automatisch ausgefüllt, sobald Sie den [Commerce Services-Connector ](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/user-guides/integration-services/saas){target=_blank} und das [!DNL Payment Services]-Dashboard zum ersten Mal aufrufen. Führen Sie diese Schritte aus, um das Onboarding für Ihre Sandbox- und/oder Produktionsumgebung abzuschließen. Diese Werte verknüpfen Ihre SaaS-ID mit [!DNL Payment Services].

   >[!WARNING]
   >
   > Wenn Sie Ihre [!DNL Payment Services] IDs zurücksetzen, müssen Sie sich erneut anmelden.

1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, diese Ansicht zu verlassen, ohne Ihre Änderungen zu speichern, wird ein modales Fenster angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, weiter zu bearbeiten oder zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können jetzt mit der Änderung der Standardeinstellungen für [Zahlungsoptionen](#configure-payment-options) Funktionen und die Storefront-Anzeige fortfahren.

### Soft-Deskriptor hinzufügen

Sie können [!UICONTROL Soft Descriptor] zu Ihrer/Ihren Website(s) oder Konfiguration einzelner Store-Ansichten hinzufügen. Weiche Deskriptoren werden auf den Kontoauszügen für Kundentransaktionen angezeigt. Wenn Sie beispielsweise über mehrere Stores/Marken/Kataloge verfügen, können Sie diese einfach voneinander abgrenzen, indem Sie dem [!UICONTROL Soft Descriptor] benutzerdefinierten Text hinzufügen.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Settings]**. Weitere Informationen finden [ unter „Einführung  [!DNL Payment Services] Startseite](payments-home.md) .
1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Website- oder Store-Ansicht aus, für die Sie einen Soft-Deskriptor erstellen möchten. Belassen Sie diese Einstellung für die Ersteinrichtung als **[!UICONTROL Default]**, um den Standardwert festzulegen.
1. Fügen Sie im Textfeld benutzerdefinierten Text (bis zu 22 Zeichen) ein, der `Soft descriptor` ersetzt.
1. Klicken Sie auf **[!UICONTROL Save]**.
1. So erstellen Sie einen anderen Soft-Deskriptor als den konfigurierten Standard für eine Website- oder Store-Ansicht:
   1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Website- oder Store-Ansicht aus, für die Sie einen Soft-Deskriptor erstellen möchten.
   1. Schalten Sie _aus_ **[!UICONTROL Use website]** (oder **[!UICONTROL Use default]**, je nach ausgewähltem Umfang).
   1. Fügen Sie den benutzerdefinierten Text in das Textfeld ein.
   1. Klicken Sie auf **[!UICONTROL Save]**.
1. So aktivieren Sie für eine Website- oder Store-Ansicht den standardmäßigen Soft-Deskriptor _oder_ den für die übergeordnete Website verwendeten Soft-Deskriptor:
   1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Website- oder Store-Ansicht aus, für die Sie einen vorhandenen Soft-Deskriptor aktivieren möchten.
   1. Ein _Ein_ **[!UICONTROL Use website]** (oder **[!UICONTROL Use default]**, je nach ausgewähltem Umfang).
   1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, diese Ansicht zu verlassen, ohne Ihre Änderungen zu speichern, wird ein modales Fenster angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, weiter zu bearbeiten oder zu speichern.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | Website | Aktivieren oder Deaktivieren von [!DNL Payment Services] für Ihre Website. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Payment mode] | Shop-Ansicht | Legen Sie die Methode oder Umgebung für Ihren Store fest. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Payment Services Sandbox ID] | Shop-Ansicht | Ihre Sandbox-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. |
| [!UICONTROL Payment Services Production ID] | Shop-Ansicht | Ihre Produktions-Händler-ID, die beim Onboarding in der Produktion (live) automatisch generiert wird. |
| [!UICONTROL Soft Descriptor] | Website- oder Store-Ansicht | Fügen Sie Ihren Websites und Store-Ansichten einen Soft-Deskriptor hinzu, um Kundentransaktionen Informationen hinzuzufügen, die Marken, Stores oder Produktlinien abgrenzen. Der Umschalter [!UICONTROL Use website] wendet alle Soft-Deskriptoren an, die auf der Website-Ebene hinzugefügt werden. Der Umschalter [!UICONTROL Use default] wendet alle Soft-Deskriptoren an, die als Standard hinzugefügt werden. |

## Zahlungsoptionen konfigurieren

Nachdem Sie [!UICONTROL Payment Services] für Ihre Website aktiviert haben, können Sie die Standardeinstellungen für Zahlungsfunktionen und die Storefront-Anzeige ändern.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Settings]**. Weitere Informationen finden [ unter „Einführung  [!DNL Payment Services] Startseite](payments-home.md) .
1. Konfigurieren Sie Zahlungsoptionen für [Kreditkarten](#credit-card-fields), [Zahlungsschaltflächen](#payment-buttons) und [Schaltflächenstil](#button-style) gemäß den folgenden Abschnitten.

### Kreditkartenfelder

Die _[!UICONTROL Credit Card Fields]_&#x200B;Einstellungen bieten eine einfache und sichere Checkout-Option für Kreditkarten- oder Debitkarten-Zahlungsmethoden.

Weitere Informationen finden [ unter ](payments-options.md#credit-card-fields).

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Store-Ansicht aus, für die Sie eine Zahlungsmethode aktivieren möchten.
1. Bearbeiten Sie im Abschnitt **[!UICONTROL Credit card fields]** den Wert im Feld **[!UICONTROL Checkout title]** , um den Namen der Zahlungsmethode zu ändern, die während des Checkouts angezeigt wird.
1. Um [ Zahlungsaktion festzulegen, ](production.md#set-payment-services-as-payment-method) Sie **[!UICONTROL Payment action]** auf `Authorize` oder `Authorize and Capture`.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie einen `Numeric Only` Wert in das Feld **[!UICONTROL Sort order]** ein.
1. Um die sichere [3DS-Authentifizierung zu aktivieren](security.md#3ds) (standardmäßig `Off`), schalten Sie den **[!UICONTROL 3DS Secure authentication]** auf `Always` oder `When required` um.
1. Um Kreditkartenfelder auf der Kaufbestätigungsseite zu aktivieren oder zu deaktivieren, schalten Sie die **[!UICONTROL Show on checkout page]** ein.
1. Zum Aktivieren oder Deaktivieren [Kartengewölbe](#card-vaulting) schalten Sie die **[!UICONTROL Vault enabled]** ein.
1. Um [Tresorzahlungsmethoden in der Admin](#card-vaulting) zu aktivieren oder zu deaktivieren (damit Händler Bestellungen für Kunden in der Admin mit ihrer Tresorzahlungsmethode ausführen können), schalten Sie die **[!UICONTROL Show vaulted methods in Admin]**-Auswahl um.
1. Um den Debugging-Modus zu aktivieren oder zu deaktivieren, schalten Sie die **[!UICONTROL Debug Mode]** um.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, diese Ansicht zu verlassen, ohne Ihre Änderungen zu speichern, wird ein modales Fenster angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, weiter zu bearbeiten oder zu speichern.

1. [Leeren Sie den Cache](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Shop-Ansicht | Fügen Sie den Text hinzu, der während des Checkouts als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode angezeigt werden soll. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/de/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Shop-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kasse. `Numeric Only` |
| [!UICONTROL 3DS Secure authentication] | Website | Aktivieren oder deaktivieren Sie [3DS Secure Authentication](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | Website | Aktivieren oder deaktivieren Sie Kreditkartenfelder, die auf der Kasse angezeigt werden sollen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Vault enabled] | Shop-Ansicht | Aktivieren oder Deaktivieren [Kreditkarten-Vaulting](vaulting.md). Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show vaulted payment methods in Admin] | Shop-Ansicht | Möglichkeit für Händler aktivieren oder deaktivieren, Bestellungen für Kunden in der Admin [mit einer Tresorzahlmethode) ](vaulting.md). Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Apple Pay

Mit der Zahlungsoption &quot;[!UICONTROL Apple Pay]-Button“ können Sie eine [!UICONTROL Apple Pay] Zahlungsschaltfläche an der Kasse Ihres Shops im Safari-Browser bereitstellen (für bis zu 99 Domains pro Händlerkonto).

Sie können Apple Pay nur verwenden, wenn Sie die [Apple Pay-Selbstregistrierung über PayPal](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) abschließen und dann [Apple Pay konfigurieren](settings.md/#payment-buttons) für Ihre Stores durchführen.

Weitere Informationen finden [ unter ](payments-options.md#apple-pay-button).

Sie können die [!UICONTROL Apple Pay]-Zahlungsoption aktivieren und konfigurieren:

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Store-Ansicht aus, für die Sie eine Zahlungsmethode aktivieren möchten.
1. Bearbeiten Sie im Abschnitt **[!UICONTROL Apple Pay]** den Wert im Feld _[!UICONTROL Checkout title]_, um den Namen der Zahlungsmethode zu ändern, die während des Checkouts angezeigt wird.
1. Um [ Zahlungsaktion festzulegen, ](production.md#set-payment-services-as-payment-method) Sie **[!UICONTROL Payment action]** auf `Authorize` oder `Authorize and Capture`.
1. Um Apple Pay auf der Kaufbestätigungsseite zu aktivieren oder zu deaktivieren, schalten Sie die **[!UICONTROL Show Apple Pay on checkout page]**-Auswahl um.
1. Um Apple Pay auf der Produktdetailseite zu aktivieren oder zu deaktivieren, schalten Sie die **[!UICONTROL Show Apple Pay on product detail page]**-Auswahl um.
1. Um Apple Pay für die Vorschau des Mini-Warenkorbs zu aktivieren oder zu deaktivieren, schalten Sie die **[!UICONTROL Show Apple Pay on the mini cart preview]** um.
1. Um Apple Pay auf der Warenkorbseite zu aktivieren oder zu deaktivieren, schalten Sie die **[!UICONTROL Show Apple Pay on cart page]**-Auswahl um.
1. Um den Debugging-Modus zu aktivieren oder zu deaktivieren, schalten Sie die **[!UICONTROL Debug Mode]** um.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, diese Ansicht zu verlassen, ohne Ihre Änderungen zu speichern, wird ein modales Fenster angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, weiter zu bearbeiten oder zu speichern.

1. [Leeren Sie den Cache](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Checkout title] | Shop-Ansicht | Fügen Sie den Text hinzu, der während des Checkouts als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode angezeigt werden soll. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/de/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | Website | Aktivieren oder deaktivieren Sie die Schaltfläche Apple Pay , die auf der Kasse angezeigt wird. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on checkout page] | Website | Aktivieren oder deaktivieren Sie die Schaltfläche Bezahlen in Apple, die auf der Produktdetailseite angezeigt werden soll. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on mini cart preview] | Website | Aktivieren oder deaktivieren Sie die Schaltfläche Apple Pay , um sie in der Vorschau des Mini-Warenkorbs anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on cart page] | Website | Aktivieren oder deaktivieren Sie die Schaltfläche Bezahlen in Apple, um sie auf der Warenkorbseite anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Zahlungs-Schaltflächen

Die [!DNL PayPal payment buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden. Weitere Informationen finden [ unter ](payments-options.md#paypal-smart-buttons).

Sie können die Zahlungsoptionen für PayPal-Zahlungsschaltflächen aktivieren und konfigurieren:

1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Store-Ansicht aus, für die Sie eine Zahlungsmethode aktivieren möchten.
1. Um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern, bearbeiten Sie den Wert im Feld **[!UICONTROL Checkout Title]** .
1. Um [ Zahlungsaktion festzulegen, ](production.md#set-payment-services-as-payment-method) Sie **[!UICONTROL Payment action]** auf `Authorize` oder `Authorize and Capture`.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie einen `Numeric Only` Wert in das Feld **[!UICONTROL Sort order]** ein.
1. Verwenden Sie die Umschalter-Selektoren, um [!DNL PayPal smart button] Anzeigefunktionen zu aktivieren oder zu deaktivieren:

   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**
   - **[!UICONTROL Show PayPal Credit and Debit Card button]**

     >[!NOTE]
     >
     > Um Apple Pay zu verwenden[ müssen Sie über ein Apple Sandbox-Testerkonto verfügen](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) (mit gefälschten Kreditkarten- und Rechnungsinformationen), um es zu testen. Wenn Sie bereit sind, Apple Pay im Sandbox- _oder_ Produktionsmodus zu verwenden, schließen Sie nach Abschluss von [Tests und ](test-validate.md#test-in-sandbox-environment) die [Selbstregistrierung mit [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (nur Abschnitt _Registrieren Sie Ihre Live-Domain_) ab und [konfigurieren Sie sie für Ihre Stores in [!DNL Payment Services]](settings.md#payment-buttons).

     Wenn Sie die Sichtbarkeit der Zahlungs-Buttons oder der PayPal Pay Later-Nachricht ein-/ausschalten, wird unten auf der Einstellungsseite eine visuelle Vorschau dieser Konfiguration angezeigt.

1. Um den Debugging-Modus zu aktivieren, schalten Sie die **[!UICONTROL Debug Mode]** um.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, diese Ansicht zu verlassen, ohne Ihre Änderungen zu speichern, wird ein modales Fenster angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, weiter zu bearbeiten oder zu speichern.

1. [Leeren Sie den Cache](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Shop-Ansicht | Fügen Sie den Text hinzu, der während des Checkouts als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode angezeigt werden soll. Optionen: Textfeld |
| [!UICONTROL Payment Action] | Website | Die [Zahlungsaktion](https://experienceleague.adobe.com/de/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Shop-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kasse. `Numeric Only` |
| [!UICONTROL Show PayPal buttons on checkout page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL PayPal payment buttons] auf der Kaufbestätigungsseite. Optionen: [!UICONTROL &#x200B; Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL PayPal payment buttons] auf der Produktdetailseite. Optionen: [!UICONTROL &#x200B; Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | Shop-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] in der Vorschau des Mini-Warenkorbs. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal buttons on cart page] | Shop-Ansicht | Aktivieren oder Deaktivieren von [!DNL PayPal payment buttons] auf der Warenkorbseite. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later button] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Option „Später bezahlen“, wenn die Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later Message] | Website | Aktivieren oder deaktivieren Sie die Pay-Later-Nachricht im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Kaufvorgangs. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Venmo button] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo, in der die Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Apple Pay button] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Option Apple Pay Payment , in der die Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Credit and Debit card button] | Shop-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption „Kredit- und Debitkarte“, wenn die Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | Website | Aktivieren oder Deaktivieren des Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_&#x200B;Optionen der Zahlungs-Schaltflächen konfigurieren:

1. Um die **[!UICONTROL Layout]** zu ändern, wählen Sie `Vertical` oder `Horizontal` aus.

   >[!NOTE]
   >
   > Wenn der Schaltflächenstil als `Horizontal` konfiguriert ist und Ihr Store so konfiguriert ist, dass mehrere Zahlungsschaltflächen angezeigt werden, werden möglicherweise nur zwei Schaltflächen auf der Produktseite, der Checkout-Seite und dem Mini-Warenkorb angezeigt und eine Schaltfläche wird im Warenkorb angezeigt.

1. Um den Slogan in einem horizontalen Layout zu aktivieren, schalten Sie die **[!UICONTROL Show tagline]** um.
1. Um die **[!UICONTROL Color]** zu ändern, wählen Sie die gewünschte Farboption aus.
1. Um die **[!UICONTROL Shape]** zu ändern, wählen Sie `Pill` oder `Rectangle` aus.
1. Um die Höhenauswahl der Schaltfläche zu aktivieren, schalten Sie die **[!UICONTROL Responsive button height]** um.
1. Um die **[!UICONTROL Label]** zu ändern, wählen Sie die gewünschte Beschriftungsoption aus.

   Wenn Sie die Konfigurationsoptionen für Layout, Farbe, Form, Höhe und Beschriftung ändern, wird unten auf der Seite „Einstellungen“ eine visuelle Vorschau dieser Konfiguration angezeigt. In der Abbildung unten ist die **[!UICONTROL Shape]** auf _Rectangle_ und die **[!UICONTROL Label]** auf _PayPal (empfohlen)_.

   ![[!DNL PayPal payment buttons] Optionen](assets/payment-buttons.png){width="400" zoomable="yes"}

1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, diese Ansicht zu verlassen, ohne Ihre Änderungen zu speichern, wird ein modales Fenster angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, weiter zu bearbeiten oder zu speichern.

1. [Leeren Sie den Cache](#flush-the-cache).

Sie können die Gestaltung der Zahlungs-Schaltfläche [in der Legacy-Konfiguration in der Admin-](configure-admin.md#configure-paypal-smart-buttons) oder hier in [!DNL Payment Services Home] konfigurieren. Weitere Informationen [ Formatieren von PayPal-Zahlungstasten finden Sie ](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) „PayPal&#39;s Buttons Style Guide“.

#### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|--- |--- |--- |
| [!UICONTROL Layout] | Shop-Ansicht | Definieren Sie den Stil des Layouts für Zahlungsschaltflächen. Optionen: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Shop-Ansicht | Aktiviert/deaktiviert die Tag-Zeile. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Color] | Shop-Ansicht | Farbe der Zahlungs-Schaltflächen definieren. Optionen: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Shop-Ansicht | Form der Zahlungs-Schaltflächen definieren. Optionen: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Shop-Ansicht | Definiert, ob für Zahlungsschaltflächen eine Standardhöhe verwendet wird. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Height] | Shop-Ansicht | Höhe der Zahlungs-Schaltflächen definieren. Standardwert: keiner |
| [!UICONTROL Label] | Shop-Ansicht | Definieren Sie den Titel, der in den Zahlungs-Schaltflächen angezeigt wird. Optionen: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## Rollen konfigurieren

Um sicherzustellen, dass Admin-Benutzerinnen und -Benutzer Bestellungen in der Commerce Admin erstellen und verwalten können, aktivieren Sie [!DNL Payment Services] Ressourcen für Benutzerrollen.

Unter [Benutzerrollen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html?lang=de) erfahren Sie, wie Sie Rollen verwalten.

Beim Zuweisen von Ressourcen zur Rolle müssen Sie Folgendes auswählen:

- **Mit[!DNL Payment Services]** bezahlen - Diese Ressource stellt sicher, dass beim Erstellen einer Bestellung in der Admin-Benutzeroberfläche [!DNL Payment Services] Kreditkarten als Zahlungsmethode verfügbar sind. Wenn Sie die übergeordnete Ressource **Aktionen** auswählen, wird diese Ressource ebenfalls ausgewählt.
- **[!DNL Payment Services]** - Diese Ressource umfasst die Ressourcen **Dashboard** und **SaaS Services Proxy** die ebenfalls ausgewählt werden müssen. Sie stellen sicher, dass [!DNL Payment Services] im Menü _Verkauf_ angezeigt wird.

  ![Zahlungsdienstressourcen](assets/roles-payments.png){width="400" zoomable="yes"}

## Leeren des Cache

Wenn Sie die Konfiguration in _Einstellungen_ ändern, z. B. durch Umschalten der Schaltflächen &quot;Apple Pay“, „Venmo“ oder „PayPal PayLater“, leeren Sie den Cache manuell, damit Ihr Store die neuesten Konfigurationen anzeigt.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Wenn ein Cache-Typ in der Cache-Management-Tabelle einen `INVALIDATED` hat, zeigt Ihr Store möglicherweise nicht die neueste Konfiguration für dieses Element an. Leeren Sie den Cache, um Ihren Store zu aktualisieren und die neueste Konfiguration anzuzeigen.

Um sicherzustellen, dass Ihr Store die richtige Konfiguration anzeigt, [ Sie regelmäßig den Cache](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/cache-management).

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

In [!UICONTROL Payment Services] können Sie mehrere PayPal-Konten innerhalb von **einem**-Händlerkonto auf Website-Ebene verwenden. Wenn Sie beispielsweise Ihr(e) Geschäft(e) in mehreren Ländern betreiben (die unterschiedliche [Währungen](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/currency/currency) verwenden) oder Adobe Commerce für einige Teile Ihres Unternehmens, aber nicht _alle_ verwenden möchten, können Sie Ihr Händlerkonto so einrichten, dass mehrere PayPal-Konten verwendet werden.

Weitere [ zur Hierarchie von Websites, Stores und Store](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=de)Ansichten finden Sie unter „Site, Store und View Scope“.

Siehe [Befehlszeilenkonfiguration](configure-cli.md#configure-scope-via-cli) für weitere Informationen zur Konfiguration von Bereichen für mehrere PayPal-Konten über die CLI.

Ihr Vertriebsmitarbeiter kann einen neuen [Umfang](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=de#scope-settings) für Ihr Händlerkonto erstellen und die zusätzliche Site mit PayPal integrieren, sodass jede der PayPal-Schaltflächen, die Sie konfigurieren, auf Ihrer Site angezeigt wird. Wenden Sie sich an Ihren Kundenbetreuer, wenn Sie mehrere PayPal-Konten für Ihre Websites verwenden möchten.
