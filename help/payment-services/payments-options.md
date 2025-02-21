---
title: Zahlungsoptionen
description: Legen Sie die Zahlungsoptionen fest, um die für Ihre Store-Kunden verfügbaren Methoden anzupassen.
feature: Payments, Checkout, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---

# Zahlungsoptionen

Mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] [!DNL Payment Services] stehen Ihnen mehrere Zahlungsoptionen zur Verfügung.

Sie können diese Zahlungsoptionen in &quot;[&quot; oder ](payments-home.md)[ Store-Konfiguration](configure-admin.md) konfigurieren (empfohlen für ältere Zahlungsoptionen oder eine Multi-Store-Einrichtung).

Es gibt verschiedene Verhaltensweisen für jede Zahlungsmethode, je nachdem, wo Sie sich im Checkout-Prozess befinden:

* Produktseite - Die Produktseite für ein Element
* Mini-Warenkorb - Erhältlich beim Klicken auf das Warenkorb-Symbol, wenn ein Produkt zum Warenkorb hinzugefügt wurde
* Warenkorb - Verfügbar beim Klicken auf _Warenkorb anzeigen und bearbeiten_ aus dem Miniwarenkorb
* Checkout-Ansicht - Verfügbar beim Klicken auf _Zum Checkout_ aus dem Mini-Warenkorb oder Warenkorb

>[!IMPORTANT]
>
>[!DNL Payment Services] Onboarding muss abgeschlossen sein, bevor Zahlungen verarbeitet werden können.

## Erlebnis „Standard“ im Vergleich zu „Erweiterte Zahlungen“

[!DNL Payment Services] bietet **Erweitert** (vollständig unterstützt) und **Standard** (Express-Checkout) Zahlungsoptionen und Onboarding-Flüsse, je nach dem Land, in dem Sie tätig sind.

* **Erweitert** - Alle verfügbaren [Zahlungsoptionen](../payment-services/payments-options.md) sind für aktuelle ([ Länder) ](../payment-services/overview.md#availability). Um Live-Zahlungen während des Onboardings zu aktivieren, wählen Sie die Option [Erweitertes Onboarding](../payment-services/production.md#advanced-onboarding) aus.
* **Standard** - Eine Untergruppe von Zahlungsoptionen (Express Checkout) - PayPal-Kredit- und Debitkarten - ist für andere verfügbare unterstützte Länder verfügbar. [Kreditkartenfelder](#credit-card-fields) und [Apple Pay](#apple-pay-button) sind für diese Onboarding-Option nicht verfügbar. Wählen Sie während des Onboardings die Option [Standard-Onboarding](../payment-services/production.md#standard-onboarding) aus, um Live-Zahlungen zu aktivieren.

Informationen [ Abschluss des Erweiterten Onboardings und des standardmäßigen Onboarding finden Sie  [!DNL Payment Services]  „Aktivieren für ](../payment-services/production.md#complete-merchant-onboarding)&quot;.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkartenzahlungsmethoden. Wenn ein Käufer mit Kreditkartenfeldern auscheckt, gibt er seinen Namen, seine Rechnungsadresse und Kreditkarteninformationen ein, um seine Bestellung aufzugeben. Ihre Kundeninformationen werden während der Kaufsitzung sicher verwendet, um sie nahtlos durch den Checkout-Ablauf zu führen.

![Kreditkartenfelder beim Checkout](assets/credit-card-fields.png){width="500" zoomable="yes"}

Aktivieren Sie [Kreditkartenabdeckung](#vaulting) für Ihre Geschäfte, damit Käufer ihre Kreditkarteninformationen für einen schnellen späteren Checkout abspeichern können.

Sie können [!UICONTROL Credit Card Fields] in der Store-Konfiguration oder auf der [!DNL Payment Services]-Startseite konfigurieren. Weitere Informationen finden [ unter ](settings.md#credit-card-fields).

Sie können auch das Layout, die Breite, Höhe und den äußeren Stil der Kreditkartenfelder ändern. Weitere Informationen finden [ in der ](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) zu PayPal .

## [!DNL Apple Pay]

Kunden können [[!DNL Apple Pay]](https://www.apple.com/apple-pay/) verwenden, das auf einem iOS- oder macOS-Gerät gespeicherte Anmeldeinformationen für die Zahlung mit Kredit- und Debitkarte verwendet, um Käufe zu tätigen.

[!DNL Apple Pay] ist nur im Safari-Browser verfügbar. Händler können bis zu 99 Domains pro Händlerkonto hinzufügen.

![Apple-Pay-Schaltfläche im Mini-Warenkorb](assets/applepay-button.png){width="500" zoomable="yes"}

Die Schaltfläche &quot;[!DNL Apple Pay]&quot; ist auf der Produktseite sowie in den Ansichten „Mini-Warenkorb“, „Warenkorb“ und „Checkout“ sichtbar.

Um [!DNL Apple Pay] für Ihre Stores zu verwenden[ füllen Sie den Abschnitt Selbstregistrierung mit [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_nur Ihre Live-_ registrieren) aus und [ Sie ihn für Ihre Stores in  [!DNL Payment Services]](settings.md#payment-buttons).

>[!NOTE]
>
> Siehe [erweiterter Checkout](https://www.paypal.com/us/cshelp/article/what-is-paypal-advanced-checkout-and-how-do-i-get-started-help953){target=_blank} in der Entwicklerdokumentation zu PayPal, um zu erfahren, wie Sie Käufern ermöglichen, auf Ihrer Site mit Apple Pay zu bezahlen.

Sie können [!UICONTROL Apple Pay] in der Store-Konfiguration oder auf der Zahlungsdienste-Startseite konfigurieren. Weitere Informationen finden [ unter ](settings.md#apple-pay).

## [!DNL Google Pay]

Kunden können [[!DNL Google Pay]](https://pay.google.com/about/) verwenden, indem sie Zahlungsdetails zu ihrem Google-Konto hinzufügen, wo sie sicher für einen nahtlosen Checkout-Erlebnis gespeichert werden.

[!DNL Google Pay] ist nur in bestimmten Ländern oder Regionen und auf bestimmten Geräten verfügbar. Weitere Informationen finden [[!DNL Google Pay]  unter ](https://developer.paypal.com/docs/checkout/apm/google-pay/#link-googlepayintegration)Dokumentation).

![Google-Pay-Schaltfläche an der Kasse](assets/google-pay-button.png){width="500" zoomable="yes"}

Die Schaltfläche &quot;[!DNL Google Pay]&quot; ist auf der Produktseite sowie in den Ansichten „Mini-Warenkorb“, „Warenkorb“ und „Checkout“ sichtbar.

Sie können [!UICONTROL Google Pay] in der Store-Konfiguration oder auf der Zahlungsdienste-Startseite konfigurieren. Weitere Informationen finden [ unter ](configure-admin.md).

>[!NOTE]
>
> Die [!DNL Google Pay]-API kann nur auf Websites in einem sicheren Kontext verwendet werden. Weitere Informationen finden [ in ](https://developers.google.com/pay/api/web/support/troubleshooting) Dokumentation zur Fehlerbehebung .

## [!DNL PayPal Payment Buttons]

[!DNL PayPal payment buttons], die PayPal verwenden, um einen Kauf abzuschließen, speichert die Lieferadresse, Rechnungsadressen und Zahlungsdetails Ihres Käufers für die spätere Verwendung. Käufer können jede Zahlungsmethode verwenden, die zuvor von PayPal gespeichert oder angeboten wurde.

![PayPal-Taste](assets/paypal-button.png){width="350" zoomable="yes"}

Sie können [!UICONTROL PayPal payment buttons] in der Store-Konfiguration oder auf der [!DNL Payment Services]-Startseite konfigurieren. Weitere Informationen finden [ unter ](settings.md#payment-buttons).

Erfahren Sie mehr über die Verfügbarkeit von Zahlungsmethoden nach Land in der [ zu Zahlungsmethoden ](https://developer.paypal.com/docs/checkout/payment-methods/).

### [!DNL PayPal]

Kunden können mit der PayPal-Schaltfläche bequem und sicher auschecken.

Die Schaltfläche &quot;[!DNL PayPal]&quot; ist auf der Produktseite sowie in den Ansichten „Mini-Warenkorb“, „Warenkorb“ und „Checkout“ sichtbar.

### [!DNL Venmo]

Kunden können mit der Schaltfläche [Venmo](https://venmo.com/) auschecken.

Die Schaltfläche &quot;[!DNL Venmo]&quot; ist auf der Produktseite sowie in den Ansichten „Mini-Warenkorb“, „Warenkorb“ und „Checkout“ sichtbar.

### PayPal Debit- oder Kreditkarten-Button

Kunden können mit der PayPal Debit- oder Kreditkartenschaltfläche auschecken.

Die Schaltfläche PayPal Debit oder Kreditkarte ist auf der Checkout-Seite sichtbar.

Diese Option kann verwendet werden, um Ihren Kunden eine Debit- oder Kreditkartenzahlungsoption mit einer PayPal-gehosteten Schaltfläche als Alternative zu einer Kreditkartenintegration anzuzeigen.

### [!DNL Pay Later]

Bieten Sie Ihren Kunden kurzfristige, zinslose Zahlungen und andere Finanzierungsoptionen, damit sie jetzt kaufen und später mit der [!DNL Pay Later] bezahlen können.

Die Schaltfläche &quot;[!DNL Pay Later]&quot; ist auf der Produktseite sowie in den Ansichten „Mini-Warenkorb“, „Warenkorb“ und „Checkout“ sichtbar.

Informationen zu den Pay Later-Angeboten finden Sie in [ Dokumentation zu PayPal-Angeboten ](https://developer.paypal.com/docs/checkout/pay-later/us/). Wählen Sie **Dropdown-Menü „Land** oder Region“ eine gewünschte Region aus.

Erfahren Sie, wie Sie [!DNL Pay Later]-Messaging deaktivieren oder aktivieren, indem Sie die Konfiguration [Einstellungen](settings.md#payment-buttons) aktualisieren.

## Nur PayPal-Zahlungs-Buttons verwenden

Um Ihren Shop schnell in den Produktionsmodus zu versetzen, können Sie _nur_ PayPal-Zahlungsschaltflächen (Venmo, PayPal usw.) konfigurieren.- anstatt auch die PayPal Kreditkartenzahlungsoption zu verwenden.

Auf diese Weise können Sie:

* Bieten Sie verschiedene Zahlungsoptionen für Ihre Kunden, einschließlich Venmo und PayPal-Zahlungsschaltflächen, mit der Option, PayPal-gehostete Kartenfelder zu deaktivieren und einen vorhandenen Kreditkartenanbieter zu verwenden.
* Nutzen Sie Ihren bestehenden Kreditkartenanbieter für Kreditkartenzahlungen und nutzen Sie gleichzeitig die anderen Zahlungsoptionen von PayPal.
* Verwenden Sie die Zahlungs-Buttons von PayPal in Regionen, in denen PayPal keine Kreditkarten als Zahlungsoption unterstützt.

So **Zahlungen mit _nur_ PayPal-Zahlungs-Schaltflächen (_nicht_ PayPal-Kreditkartenzahlungsoption) erfasst**:

1. Stellen Sie sicher, dass sich Ihr Store [im Produktionsmodus) ](settings.md#enable-payment-services).
1. [Konfigurieren Sie die gewünschten PayPal-Zahlungs-Schaltflächen](settings.md#payment-buttons) in den Einstellungen.
1. Deaktivieren __ die Option **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** im Abschnitt _[!UICONTROL Payment buttons]_.

So **Sie Zahlungen mit Ihrem vorhandenen Kreditkartenanbieter _und_ PayPal-Zahlungs-Schaltflächen**:

1. Stellen Sie sicher, dass sich Ihr Store [im Produktionsmodus) ](settings.md#enable-payment-services).
1. [Konfigurieren Sie die gewünschten PayPal-Zahlungsschaltflächen](settings.md#payment-buttons).
1. Deaktivieren __ die Option **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** im Abschnitt _[!UICONTROL Payment buttons]_.
1. Deaktivieren __ die Option **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** im Abschnitt _[!UICONTROL Credit card fields]_und verwenden Sie Ihr [vorhandenes Kreditkartenkonto](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## Neuberechnung der Bestellung

Wenn ein Kunde den Checkout-Fluss über den Mini-Warenkorb, den Warenkorb oder die Produktseite aufruft, wird er zu einer Seite zur Bestellüberprüfung weitergeleitet, auf der er die ausgewählte Lieferadresse in einem PayPal-Popup-Fenster sehen kann. Nachdem der Kunde die Versandart ausgewählt hat, wird der Bestellbetrag entsprechend neu berechnet und der Kunde kann die Versandkosten und -steuern sehen.

Wenn ein Kunde den Checkout-Fluss über die Checkout-Seite betritt, ist das System bereits über die Lieferadresse und den endgültigen berechneten Betrag informiert und die Gesamtsummen werden entsprechend dargestellt.

Steuerferien, Versandkosten und Umsatzsteuer können von Standort zu Standort stark variieren. Nachdem [!DNL Payment Services] die Lieferadresse und den Preis erhalten hat, berechnet es schnell alle anfallenden Kosten neu und zeigt sie in den letzten Phasen des Checkouts angemessen an.

## Tresor mit Kreditkarte

Käufer können ihre Kreditkarteninformationen für zukünftige Käufe auf der Website-Ebene (jedes Geschäft innerhalb des Kontos desselben Händlers) Vault-nutzen oder „speichern“.

Weitere Informationen [ Sie unter ](vaulting.md)Kreditkartenabwicklung).

## Sicherheit

Siehe [PCI-](security.md#pci-compliance)) für weitere Informationen.
