---
title: '[!DNL Payment Services] Versionshinweise'
description: Informationen zu allen Versionen finden  [!DNL Payment Services]  in den Versionshinweisen .
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: ed5473874891e4f58e27d15a7368d678657a0e34
workflow-type: tm+mt
source-wordcount: '4346'
ht-degree: 0%

---


# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Payment Services] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Funktionsänderungen und -korrekturen, die außerhalb der regulären Funktionsveröffentlichungsversion veröffentlicht wurden, finden Sie in den Abschnitten _Gehostete Service-Updates_.

Weitere Informationen zu kommenden Versionen, zum Produkt-Support und dazu, welche Adobe Commerce-Versionen die [!DNL Payment Services] unterstützen, finden Sie in den [&#x200B; zu Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) und [Produktverfügbarkeit](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Gehostete Service-Aktualisierungen

In diesen Versionshinweisen werden Funktionsänderungen und -korrekturen beschrieben, die außerhalb der regulären Funktionsversionen für den gehosteten Service stattfanden und veröffentlicht wurden.

+++Gehostete Service-Aktualisierungen

_25. April 2025_

![Neues Problem](../assets/new.svg)<!-- Issue PAY-6051 --> Jetzt zeigt [!DNL Payment Services] Dashboard sowohl die aktuelle Erweiterungsversion als auch die Dashboard-Version an.

_30. August 2024_

![Neues Problem](../assets/new.svg)<!-- Issue PAY-5658 --> Jetzt können Händler Transaktionen nach den Zahlungsdetails im [Transaktionsbericht“ filtern, &#x200B;](reporting.md#transactions-report-view) detailliertere und genauere Zahlungsmethodendaten zu erhalten.

_15. Juli 2024_

![Neues Problem](../assets/new.svg)<!-- Issue PAY-5571 --> Jetzt können Händler Transaktionen nach der Commerce-Kunden-E-Mail im [Transaktionsbericht](reporting.md#transactions-report-view) filtern. Geben Sie die Kunden-E-Mail ein, um Transaktionen für diese spezifische E-Mail zu filtern.

_9. Juli 2024_

![Neues Problem](../assets/new.svg)<!-- Issue PAY-5488 --> Jetzt können Händler die Commerce-Kunden-ID als Spalte im [Transaktionsbericht“ anzeigen, &#x200B;](reporting.md#transactions-report-view) Transaktionen zu identifizieren, die ein bestimmter Kunde platziert hat. Darüber hinaus können Händler den Transaktionsbericht nach dieser Commerce-Kunden-ID nach zugehörigen Bestellungen filtern.

_5. März 2024_

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-5252 --> Jetzt können Händler Daten aus den Dashboard-Rastern kopieren, indem sie den Inhalt einer einzelnen Zelle auswählen.

_10. Oktober 2023_

![Neue Ausgabe](../assets/fix.svg)<!-- Issue PAY-4888 --> Jetzt können Händler Kredit- und Debitkartentransaktionen nach den letzten vier Ziffern der Kartennummer im Bericht &quot;[&quot; &#x200B;](reporting.md#transactions-report-view).

_12. Juli 2023_

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4587 --> Ein Problem, das in der [!DNL Payment Services]-Version 2.1.0 eingeführt wurde und verhinderte, dass durch frühere Erweiterungsversionen erstellte Autorisierungs-Leerstellen gelöscht wurden, wurde jetzt behoben. Händler, die eine beliebige Version von [!DNL Payment Services] verwenden, können Autorisierungen widerrufen.

_9. Juni 2023_

![Neu](../assets/new.svg)<!-- Issue PAY-4288 --> Jetzt können Händler [nur __ PayPal-Zahlungs-Buttons konfigurieren](payments-options.md#use-only-paypal-payment-buttons) - und _nicht_ die PayPal-Kreditkartenzahlungsoption verwenden. Dadurch können Händler verschiedene Zahlungsoptionen bereitstellen, einschließlich Venmo und PayPal-Zahlungsschaltflächen, und einen vorhandenen Kreditkartenanbieter anstelle der PayPal-Kreditkartenzahlungsoption verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-4050 --> Es wurde eine [Datenvisualisierungsansicht](/help/payment-services/payouts.md#payouts-data-visualization-view) hinzugefügt, die auf der Zahlungsdienst-Startseite für den Bericht „Zahlungsstatus der Bestellung“ angezeigt wird.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4486--> Zuvor wurde die Schaltfläche PayPal PayLater für Händler in Großbritannien nicht an der Kasse angezeigt. Dieses Problem wurde behoben.

![Es wurde &#x200B;](../assets/fix.svg)<!-- Issue PAY-4485-->, dass Berichtsdatenvisualisierungsansichten jetzt auf [!DNL Payment Services] Startseite angezeigt werden, wenn[!DNL Payment Services] deaktiviert ist.

_25. Januar 2023_

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-4102 --> Neue Installationen von [!DNL Payment Services] können Commerce Services nicht konfigurieren, wodurch [!DNL Payment Services] nicht mehr funktionsfähig sind. Um dieses Problem zu beheben, aktualisieren Sie Ihre [!DNL Payment Services]-Erweiterung auf Version 1.5.3.

_12. September 2022_

![Neu](../assets/new.svg)<!-- Issue PAY-3705 --> Die `increment_id` ist jetzt für die Abstimmung von Auszahlungen in externen ERP-Systemen verfügbar. Sie wird an die `custom_id` __ und`invoice_id` übertragen, die sowohl im PayPal-Webhook als auch in den Details zur Händleraktivität für eine Auszahlung sichtbar sind.

_31. August 2022_

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3629 --> Wenn ein neuer Händler zum ersten Mal auf die [!DNL Payment Services]-Startseite zugreift, wird die Seite jetzt sofort geladen, um den Inhalt anzuzeigen, anstatt die Seite zu aktualisieren.

_9. August 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay ist jetzt als PayPal Smart Button erhältlich. Diese [Zahlungsoption](payments-options.md#apple-pay-button) ermöglicht es Kunden, die Touch ID-Funktion auf ihrem iOS- oder macOS-Gerät zu verwenden, um Apple Pay auszuwählen. Apple Pay verarbeitet die Zahlung mit den auf dem Gerät gespeicherten Zahlungsdaten für Kredit- und Debitkarten.

_28. Juni 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-1720 --> Streitigkeiten bei Lagerbestellungen sind jetzt im Bericht [Status der Bestellzahlung“ &#x200B;](/help/payment-services/order-payment-status.md#view-disputes). Sie können Streitigkeiten beilegen, indem Sie von [!DNL Payment Services] direkt zum PayPal-Lösungszentrum gehen.

![Neu](../assets/new.svg)<!-- Issue PAY-2854 --> Zu den Verbesserungen des Benutzererlebnisses auf [!DNL Payment Services] Startseite gehören die Möglichkeit, eine Konfiguration auf der aktuellen Vererbungsebene zu ändern, sowie Verbesserungen bei der Anzeige der Kopfzeile und der Navigation.

![Neu](../assets/new.svg)<!-- Issue PAY-2854 --> Sie können jetzt Warnungen sehen, wenn Sie vom Sandbox-Modus in den Produktionsmodus wechseln und versuchen, eine Ansicht mit nicht gespeicherten Aktualisierungen zu verlassen.

![Neu](../assets/new.svg)<!-- Issue PAY-2761 --> Sie können jetzt die Daten anpassen, die im Bericht [Zahlungsstatus bestellen](/help/payment-services/order-payment-status.md#show-and-hide-columns) und im Bericht [Auszahlungen](/help/payment-services/payouts.md#show-and-hide-columns) angezeigt werden, indem Sie Spalten mithilfe des Steuerelements Spalteneinstellungen ein- oder ausblenden.

+++

>[!NOTE]
>
> Es werden häufig Versionen veröffentlicht, um bei Bedarf neue Funktionen und Fehlerbehebungen bereitzustellen. Der Veröffentlichungszeitplan ist nicht festgelegt.

## v2.13.1

_18. Dezember 2025_

![Problem behoben](../assets/fix.svg)<!-- PAY-6355 --> Es wurde ein Problem behoben, bei dem Händler beim Checkout keine Versandmethode auswählen konnten.

![Problem behoben](../assets/fix.svg)<!-- PAY-6347 --> Verbesserte Ausfallsicherheit beim Checkout, indem unnötige API-Aufrufe entfernt wurden.

![Problem behoben](../assets/fix.svg)<!-- PAY-6368 --> Es wurde ein Ausweichmechanismus zum Laden der Zahlungs-SDK implementiert, wenn die primäre Domain nicht verfügbar ist, um sicherzustellen, dass Kreditkartenfelder während des Checkouts zugänglich bleiben.

## v2.13.0

_10. November 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-xxxx --> Jetzt unterstützt [!DNL Payment Services] das PayPal-Modal **One-Time Checkout (OTC)** mit integrierten Kontakt- und Versandinformationen.

![Neu](../assets/new.svg)<!-- PAY-xxxx --> Verbessertes mobiles Erlebnis durch **PayPal-App-Switch-Authentifizierung** zusammen mit verbesserter API-Integration für reibungslosere Journey. Diese Funktion steht nur Kunden mit Sitz in den USA [!DNL Payment Services] Verfügung.

![Neu](../assets/new.svg)<!-- PAY-xxxx --> Hinzugefügte **3D Secure (3DS)-Authentifizierung** Unterstützung für Fastlane zur Erfüllung **Strong Customer Authentication (SCA)** Anforderungen. Dadurch können Händler in Großbritannien und der EU [!DNL Payment Services] Transaktionen mit **3DS-Authentifizierung** verarbeiten, um Betrugsvorbeugung zu verbessern und die Einhaltung regionaler Vorschriften sicherzustellen.

![Neu](../assets/new.svg)<!-- PAY-xxxx --> Jetzt können [!DNL Payment Services] Händler für die Fastlane-Checkout-Komponente zwischen **hellen und dunklen** wählen, sodass die Checkout-Seiten ihrem Site-Design entsprechen. Wenn benutzerdefinierte Stile die Barrierefreiheitsstandards nicht erfüllen, wird das System automatisch auf die Standardeinstellungen zurückgesetzt.

![Behobenes Problem](../assets/fix.svg)<!-- PAY-xxxx --> Behobenes Ladeproblem beim **Admin-Checkout mit der 3DS-Herausforderung**.

![Problem behoben](../assets/fix.svg)<!-- PAY-xxxx --> Verbesserte **Validierung beim Speichern der Zahlungskonfiguration** über API.

## v2.12.2

_23. September 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Problem behoben](../assets/fix.svg)<!-- PAY-6275 --> Durch die Ablehnung [!DNL Fastlane] Transaktionen im Erfassungsmodus werden keine Bestellungen mehr in Commerce erstellt.

## v2.12.1

_18. September 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Es wurde &#x200B;](../assets/fix.svg)<!-- PAY-6164 --> Problem behoben. Jetzt verwendet [!DNL Payment Services] die Basiswährung für die verfügbaren Versandmethoden im **Server-Side Shipping Callback (SSSC)**.

![Problem behoben](../assets/fix.svg)<!-- PAY-6267 --> Der **Versand an**-Block wird auf der Kaufbestätigungsseite ausgeblendet, wenn **In-Store-Abholung (ISPU)** ausgewählt wird.

![Problem behoben](../assets/fix.svg)<!-- PAY-6271 --> Jetzt zeigt [!DNL Payment Services] gespeicherte Kreditkartendetails aus dem PayPal-PayFlow im Abschnitt **Kundenkonto** > **Gespeicherte Zahlungsmethoden** an.

## v2.12.0

_20. August 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-6022 --> [Fastlane](https://experienceleague.adobe.com/en/docs/commerce/payment-services/payments-checkout/payments-options) bietet einen schnelleren Kauf während des Gast-Checkouts.

![Neu](../assets/new.svg)<!-- PAY-6168 --> Es wurde die [`addProductsToNewCart`](https://developer.adobe.com/commerce/webapi/graphql/payment-services-extension/mutations/) Mutation zu [!DNL Payment Services] hinzugefügt, um reibungslosere Übergänge und eine bessere Wiederverwendung des Warenkorbs zu ermöglichen.

![Neu](../assets/new.svg)<!-- PAY-6169 --> Es wurde die [`setCartAsInactive`](https://developer.adobe.com/commerce/webapi/graphql/payment-services-extension/mutations/) Mutation zu [!DNL Payment Services] hinzugefügt, um das Lebenszyklus-Management von Angeboten zu verbessern.

![Neu](../assets/new.svg)<!-- PAY-6227 --> Beim Auschecken mit PayPal überspringt [!DNL Payment Services] das Popup zur Bestellbestätigung, um einen schnelleren Kaufvorgang zu ermöglichen.

![Neu](../assets/new.svg)<!-- PAY-6234 --> Es wurde eine neue Funktion für die Zahlungsoption [Später &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/payment-services/payments-checkout/payments-options). Jetzt bietet der BNPL-Messaging-Konfigurator mehr Flexibilität bei der Anzeige von Pay Later BNPL-Nachrichten auf Kunden-Checkout-Seiten.

![Es wurde &#x200B;](../assets/fix.svg)<!-- PAY-5505 --> Problem behoben. Jetzt wird [!DNL Payment Services] Angebot als inaktiv festgelegt, wenn ein Google Pay- oder PayPal-Popup auf der Produktseite geschlossen wird.

![Problem behoben](../assets/fix.svg)<!-- PAY-5754 --> [!DNL Payment Services] erlaubt es nicht mehr, Bestellungen aus leeren Anführungszeichen zu erstellen.

## v2.11.1

_14. März 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Problem behoben](../assets/fix.svg)<!-- PAY-5849 --> Es wurde ein Problem behoben, das [Zeilenelemente](line-items.md) während des Auscheckens betraf. Jetzt hat [!DNL Payment Services] die Zuverlässigkeit des Checkout-Prozesses für **Zeilenelemente“**. Wenn ein ähnliches Problem auftritt, wenden Sie sich an Ihren [!DNL Payment Services] Vertriebsmitarbeiter.

## v2.11.0

_13. März 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer


![Neu](../assets/new.svg)<!-- PAY-5938 --> Jetzt ermöglicht [!DNL Payment Services] Händlern die Verwaltung von Zahlungseinstellungen, um die Flexibilität in ihrem Unternehmen zu maximieren. Diese Version verbessert die Möglichkeit, [mehrere PayPal-Konten](configure-admin.md#use-multiple-paypal-accounts) für die Regionen und Marken anzuhängen, die ein Händler unterstützt. Unser Vertriebsteam kann einen Onboarding-Link bereitstellen, um Ihre Website einzurichten und Ansichtsumfänge zu speichern.

![Neu](../assets/new.svg)<!-- PAY-5968 --> Jetzt aktualisiert [!DNL Payment Services] die Admin-Konfiguration mit den Werten **PayPal-Händler-ID** und **PayPal-Händler-Status**. Diese Werte bieten Händlern eine bessere Übersicht über ihren PayPal-Kontostatus.

![Problem behoben](../assets/fix.svg)<!-- PAY-5816 --> Die Funktionalität der normalen Reihenfolge in [!DNL Payment Services] wurde wiederhergestellt, indem ein Problem behoben wurde, das bei allen Auftragsplatzierungen mit Version 2.9.0 zu Fehlern führte.

![Problem behoben](../assets/fix.svg)<!-- PAY-5825 --> Es wurde ein Problem behoben, bei dem der Mini-Warenkorb &quot;Apple Pay“ eine falsche geschätzte Gesamtsummen-URL für angemeldete Kunden verwendete. Jetzt stellt [!DNL Payment Services] genaue Gesamtberechnungen sicher.

![Problem behoben](../assets/fix.svg)<!-- PAY-5826 --> Die Zuverlässigkeit der Bestellverwaltung wurde verbessert, indem ein Problem behoben wurde, das beim Ändern des Angebotsstatus in &quot;`inactive`&quot; einen HTTP 500-Fehler verursachte.

![Problem behoben](../assets/fix.svg)<!-- PAY-5849 --> Es wurde ein Problem behoben, bei dem `LineItemProvider` Ausnahmen für Dezimalzahlen unter 1 gab. Jetzt bietet [!DNL Payment Services] eine bessere Unterstützung für Teilmengen.

![Problem behoben](../assets/fix.svg)<!-- PAY-5868 --> Es wurde ein Fehler bei der Gutscheinkarte beim Checkout behoben. [!DNL Payment Services] stellt nun während des Checkout-Prozesses genaue Werte sicher.

![Problem behoben](../assets/fix.svg)<!-- PAY-5911 --> Fehler bei der Sendungserstellung bei Bestellungen, die mit nicht [!DNL Payment Services] Online-Zahlungsmethoden aufgegeben wurden, wodurch die Zuverlässigkeit insgesamt verbessert wurde.

![Problem behoben](../assets/fix.svg)<!-- PAY-5954 --> [!DNL Payment Services] bietet jetzt ein reibungsloseres Checkout-Erlebnis, indem ein Problem behoben wird, bei dem Apple Pay keine Bestellung aufgab, wenn eine andere Kreditkarte in der Brieftasche ausgewählt wurde.

![Problem behoben](../assets/fix.svg)<!-- PAY-5971 --> [!DNL Payment Services] leitet Kunden nicht mehr zur Bestellüberprüfungsseite weiter, wenn Apple Pay fehlschlägt, wodurch unnötige Checkout-Unterbrechungen vermieden werden.

## v2.10.3

_24. Februar 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Problem behoben](../assets/fix.svg)<!-- PAY-xxxx --> Verbesserte Gesamtstabilität und Leistung.

![Problem behoben](../assets/fix.svg)<!-- PAY-xxxx --> Allgemeine Verbesserungen und Optimierungen. Es wurden kritische Fehler in Version 2.10.2 behoben.

## v2.10.2

_21. Februar 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Bekanntes Problem](../assets/bug.svg)<!-- PAY-xxxx --> Enthält kritische Fehler, die die Stabilität und Leistung beeinträchtigen können. Adobe empfiehlt, auf Version 2.10.3 zu aktualisieren, anstatt diese Version (v2.10.2) zu verwenden.

## v2.10.1

_5. Februar 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-5813 --> Es wurde Unterstützung für Adobe Commerce 2.4.8 und PHP 8.4 hinzugefügt.

## v2.10.0

_13. Dezember 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-5702 --> [!DNL Payment Services] unterstützt jetzt GraphQL-Endpunkte für Vaulting ohne Kauf, sodass Kunden ihre Zahlungsmethoden speichern können, ohne eine Transaktion abzuschließen.

![Neu](../assets/fix.svg)<!-- PAY-5789 --> [!DNL Payment Services] unterstützt jetzt die sichere [3D-Authentifizierung mit Google Pay](security.md#3ds), wodurch die Sicherheit für Händler und Kunden während des Zahlungsverkehrs verbessert wird.

![Korrigieren](../assets/fix.svg)<!-- PAY-5703 --> [!DNL Payment Services] bietet Kunden die Möglichkeit[&#x200B; Karten direkt in ihrem **Mein Konto“ zu speichern,**](vaulting.md#vaulting-without-purchase) Komfort zu verbessern und zukünftige Checkouts zu vereinfachen. `Vault without purchase functionality might not be 100% compatible with Adobe Commerce 2.4.4 due to a known issue with` [`GraphQL authorization mechanisms`](https://developer.adobe.com/commerce/webapi/graphql/usage/authorization-tokens/).

![Korrektur](../assets/fix.svg)<!-- PAY-5762 --> Es wurde ein Problem behoben, bei dem Couponcodes auf der Seite zur Bestellüberprüfung nicht angewendet wurden, wenn die Bestellung von der Produktdetailseite (PDP) aus initiiert wurde.

![Korrigieren](../assets/fix.svg)<!-- PAY-5792 --> [!DNL Payment Services] zeigt jetzt Beschreibungen und Rechnungsadressen für [Tresorkarten auf der Checkout-Seite an](vaulting.md) sodass Kunden ihre gespeicherten Zahlungsmethoden besser einsehen können.

![Korrigieren](../assets/fix.svg)<!-- PAY-5793 --> [!DNL Payment Services] ermöglicht es Händlern, die Rechnungsadresse für Tresorkarten direkt auf der Checkout-Seite zu speichern, um genaue und vollständige Zahlungsinformationen zu gewährleisten.

## v2.9.0

_7. November 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-5629 --> [!DNL Payment Services] unterstützt jetzt eine **upgegradete SDK-URL für Apple Pay**, wodurch die Integration für Händler, die Apple Pay verwenden, verbessert wird. Diese Funktion ist mit macOS 14 und höher kompatibel. Geräte, auf denen frühere Versionen von macOS ausgeführt werden, zeigen diese Funktion nicht an.

![Neu](../assets/new.svg)<!-- PAY-5630 --> Die Seiten **Checkout**, **Product**, **Cart** und **MiniCart** wurden aktualisiert, um die **upgegradete SDK-URL für Apple Pay** zu unterstützen und das Benutzererlebnis für Händler zu verbessern, die Apple Pay als Zahlungsoption anbieten.

![Neu](../assets/new.svg)<!-- PAY-5635 --> Verbesserte Versandschätzungen **basierend auf der Pay-** von Apple), sodass Kunden die genauen Versandkosten während des Checkouts anzeigen können.

![Behebung](../assets/fix.svg)<!-- PAY-5661 --> Es wurden verschiedene **[!DNL Payment Services]an der Kasse behoben** wodurch die Zuverlässigkeit des Zahlungsprozesses für Händler und Käufer verbessert wurde.

![Behebung](../assets/fix.svg)<!-- PAY-5692 --> Es wurde ein Problem behoben, bei dem der **Vor- und Nachname des Kunden** nicht zur Bestellung hinzugefügt wurde, wenn **intelligente Schaltflächen für den Express-Checkout)**.

![Behebung](../assets/fix.svg)<!-- PAY-5712 --> Es wurde ein Problem behoben, bei dem Händler **den Checkout nicht mit der Option Null Zwischensumme Checkout-Zahlung abschließen konnten** obwohl der Gesamtbetrag kostenlos war.

## v2.8.1

_13. September 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Beheben](../assets/fix.svg)<!-- PAY-5644 --> Es wurde ein Problem mit dem Cache von SDK-Parametern bei der Verwendung mehrerer Bereiche in [!DNL Payment Services] behoben. Die SDK-Konfiguration wird jetzt für jeden Bereich separat zwischengespeichert, anstatt unter einem einzigen Schlüssel. Dadurch wird sichergestellt, dass der Cache jedes Bereichs unabhängig invalidiert wird, was die Zuverlässigkeit bei der Verwaltung mehrerer Bereiche verbessert.

## v2.8.0

_13. September 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-5499 --> [!DNL Payment Services] unterstützt jetzt das Senden von Tracking-Nummer-Informationen an PayPal, wenn [Tracking-Nummer“ &#x200B;](track-shipment.md) Adobe Commerce eingegeben wird.

![Korrigieren](../assets/fix.svg)<!-- PAY-5626 --> [!DNL Payment Services] hat den Anfrageprozess an die Händlerregistrierung optimiert, wenn Kunden die Commerce-Checkout-Seite besuchen. Zuvor wurden für jede Zahlungsmethode separate Anfragen gestellt (gehostete Felder, Google Pay, Apple Pay und Smart Buttons). Diese Verbesserung reduziert die Anzahl der Aufrufe und verbessert die Leistung und Effizienz während des Checkout-Prozesses.

![Korrigieren](../assets/fix.svg)<!-- PAY-5645 --> [!DNL Payment Services] verhindert jetzt, dass das Popup PayPal/Google Pay geöffnet wird, wenn der Käufer den von Händlern erstellten benutzerdefinierten Bedingungen auf der Kaufbestätigungsseite nicht zugestimmt hat.

![Korrigieren](../assets/fix.svg)<!-- PAY-5648 -->  [!DNL Payment Services] hat ein Problem im Zusammenhang mit der Aufschlüsselung der Steuer nach Zeileneinträgen im PayPal-Portal behoben. Wenn die Versandkosten einer Bestellung mit Steuern verknüpft sind, wird die Steuer als Teil der Versandkosten eingeschlossen und auf diese Weise in den Positionsdetails sichtbar, die im PayPal-Portal angezeigt werden.

## v2.7.0

_2. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-4844 --> [!DNL Payment Services] unterstützt jetzt [Zeilendaten auf Auftragsebene](line-items.md). Mit dieser Funktion können Händler detaillierte Informationen zu den Artikeln in einer Bestellung anzeigen, z. B. Produktdetails, Menge und Preis (einschließlich Mehrwertsteuer, Rabatte und andere relevante Informationen).

![Neu](../assets/new.svg)<!-- PAY-5380 --> [!DNL Payment Services] verbessert die [Konfiguration im Admin](configure-admin.md#general-configuration)-Erlebnis für Händler, sodass der Onboarding-Prozess einfacher und intuitiver wird. Mit dieser Funktion können Händler ihre [!DNL Payment Services] IDs zurücksetzen.

![Neu](../assets/new.svg)<!-- PAY-5255 --> [!DNL Payment Services] enthält eine [Benachrichtigung bei Zahlungsausfall](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-payment-failed-emails). Diese Funktion bietet Händlern nahezu in Echtzeit Benachrichtigungen über Zahlungsfehler, sodass Bestellungen gespeichert werden können, indem Sie sich an den Erstkäufer wenden und möglicherweise die Problemlösung verbessern.

![Behebung](../assets/fix.svg)<!-- PAY-5469 --> Es wurde ein Problem behoben, bei dem das Popup **Google Pay von Safari blockiert**. Käufer können jetzt ihre Google Pay-Zahlungsvorgänge auf Safari abschließen.

![Beheben](../assets/fix.svg)<!-- PAY-5492 --> Es wurde ein Problem behoben, bei dem ein Händler benutzerdefinierte Geschäftsbedingungen zur Checkout-Seite hinzufügt. Während eines [Express-Checkouts](payments-options.md#standard-vs-advanced-payments-experience) kann ein Käufer jetzt diese Geschäftsbedingungen akzeptieren, um den Checkout ohne Probleme abzuschließen.

![Beheben](../assets/fix.svg)<!-- PAY-5532 --> Verbesserte ISPU-Funktionen (In-Store Pickup) mit **InstantPurchase**. **ISPU-Versandmethoden** werden nicht mehr angezeigt, wenn ein Käufer eine Bestellung mit **InstantPurchase** aufgibt.

![Behebung](../assets/fix.svg)<!-- PAY-5606 --> Es wurde ein Problem in der **Konfigurationsseite** Länderauswahl behoben, das auftrat, wenn das Land des Händlers auf &quot;**&quot;**.

## v2.6.0

_4. Juni 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-4877 --> Jetzt unterstützt [!DNL Payment Services] Preisfunktionen [L2/L3](/help/payment-services/levels-card-payment-transactions.md#level-2-and-level-3). Diese Funktion steht nur [!DNL Payment Services] Kunden mit aktiviertem IC++-Preis zur Verfügung. Wenn Sie L2/L3-Verarbeitungsdaten für [!DNL Payment Services] verwenden möchten, wenden Sie sich an Ihren [!DNL Payment Services] Account Manager.

![Fix](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] ermöglicht es Ihnen, Apple Pay direkt über die Erweiterung zu aktivieren, ohne die [Domain-Zuordnungsdatei“ herunterzuladen und zu &#x200B;](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).

## v2.5.0

_23. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Fix](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] unterstützt jetzt [Adobe Commerce-Richtlinien für den `--db-prefix` Parameter](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) für Adobe Commerce Version 2.4.7 und höher.

## v2.4.3

_16. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Behebung](../assets/fix.svg)<!-- Issue PAY-5106 --> Es wurde ein Problem behoben, durch das die Bestellsummen beim Checkout zwischen PayPal und Adobe Commerce falsch ausgefüllt wurden. Jetzt können Händler sicherstellen, dass die Bestellsummen bei der Bestellung korrekt sind.

## v2.4.2

_11. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- Issue xxx --> Unterstützung für Adobe Commerce 2.4.7 wurde hinzugefügt.

## v2.4.1

_4. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Behebung](../assets/fix.svg)<!-- PAY-5322 --> Es wurde ein PCI-Kompatibilitätsproblem mit neueren Adobe Commerce-Versionen behoben. Jetzt ist [!DNL Payment Services] als Zahlungsoption an die Checkout-Anforderungen in Adobe Commerce angepasst.

![Fix](../assets/fix.svg)<!-- PAY-5323 --> PayLater und Venmo werden in Adobe Commerce korrekt angezeigt. Fehlerkorrektur - Der Administrator kann jetzt die Umschalter „PayLater“ und „Venmo“ anzeigen.

## v2.4.0

_20. März 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-4868 --> Händler können [Google Pay während des gesamten Kauferlebnisses konfigurieren](/help/payment-services/payments-options.md) ähnlich wie andere Zahlungsschaltflächen in [!DNL Payment Services] über den Administrator.

![Neu](../assets/new.svg)<!-- PAY-4381 --> [Payment Services unterstützt Google Pay über GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) sodass Händler ein Headless-Commerce-Erlebnis mit der Google Pay-Zahlungsmethode haben.

![Neu](../assets/new.svg)<!-- PAY-4878 --> Jetzt ist die [!DNL Payment Services] grundlegende Checkout-Funktion für Adobe Commerce- und Magento Open Source-Händler gebündelt.[!DNL Payment Services] können jetzt Händler mit Unternehmen in 200 Regionen weltweit unterstützen.[!DNL Payment Services] einfache Checkout bietet die Optionen „Debit/Credit“, „PayPal“, „Venmo“ (falls verfügbar) und „PayLater“ (falls verfügbar) in einem Self-Service-Onboarding.

![Behebung](../assets/fix.svg)<!-- PAY-5291 --> Bei einigen Transaktionen kann sich der Erhalt einer Zahlungsbestätigung verzögern. In diesem Fall können Händler jetzt einen aktualisierten Zahlungsstatus für eine Bestellung erhalten. [Zahlungsdienste erkennen den Status „Ausstehend“ einer &#x200B;](/help/payment-services/order-payment-status.md#payment-status-updates) in einer Bestellung, indem sie ausstehende Transaktionen erkennen und diese Transaktionen proaktiv überwachen und aktualisieren, wenn der Status „Ausstehend“ erfasst wurde.

## v2.3.4

_1. März 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-5244 --> Behobene Kompatibilität beim asynchronen Auschecken.

![Beheben](../assets/fix.svg)<!-- PAY-5253 --> Es wurde ein Fehler behoben, bei dem ein Vault-Token, das nicht zu [!DNL Payment Services] gehört, nicht gelöscht werden konnte.

## v2.3.3

_14. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-5048 --> Unterstützung für PHP 8.3 hinzugefügt

![Beheben](../assets/fix.svg)<!-- PAY-5048 --> Es wurde ein Fehler mit dem `is_deleted`-Flag behoben. Jetzt schlagen Bestellungen nicht aufgrund des von der Erweiterung gesendeten `Rejected` fehl.

## v2.3.2

_26. Januar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Beheben](../assets/fix.svg)<!-- PAY-5183 --> Es wurden REST-/GraphQL-Leistungsprobleme behoben. Jetzt wird die Kreditkartenschaltfläche gerendert, wenn sie über die API abgerufen wird.

## v2.3.1

_7. Dezember 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-5047 --> Die Kredit-/Debitkartenmarke oder der Zahlungsart ist jetzt an folgenden Standorten verfügbar:

- Die Seite mit der Kundenbestellung in der Storefront
- Die E-Mail zur Bestellbestätigung, die an den Einkäufer gesendet wurde
- In der [&#x200B; „Auftragsdetails“ &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) Commerce Admin.

## v2.3.0

_1. Dezember 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-4381 --> [Payment Services unterstützt jetzt die Integration von GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). Dank GraphQL-Unterstützung für PayPal-Zahlungsschaltflächen, gehostete Felder und Apple Pay unterstützt [!DNL Payment Services] jetzt die Einrichtung von Headless-Commerce.

## v2.2.1

_27. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4870 --> Es wurde ein Problem behoben, durch das das neue Header-Attribut beim Senden der Erweiterungsversion mit der neuesten Version falsch in Storefront ausgefüllt wurde. Mit der `1.3.0` Version des Commerce Services-Connectors konnten Sie die `User-Agent header` nicht aus der [!DNL Payment Services]-Erweiterung erweitern.

## v2.2.0

_30. August 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- PAY-4638 --> Es wurde eine [Integration mit Signifyd](fraud-protection.md) hinzugefügt, die automatisierte Betrugsschutzdienste bietet.

![Neu](../assets/new.svg)<!-- PAY-3981 --> [Apple Pay wurde auf eine separate Zahlungsoption &#x200B;](payments-options.md#apple-pay-button), die außerhalb der PayPal-Zahlungsschaltflächen liegt, um die Sichtbarkeit der Zahlungsoption für Kunden zu erhöhen und es Händlern zu ermöglichen, die Platzierung und das Styling von Apple Pay zu steuern.

![Neu](../assets/new.svg)<!-- PAY-4002 --> Verbessertes Benutzererlebnis bei der Kasse von Kreditkartenfeldern, einschließlich Stilverbesserungen wie dem Hinzufügen von Zahlungssymbolen, um die kognitive Belastung der Käufer zu verringern und die Konversionen zu erhöhen.

![Neu](../assets/new.svg)<!-- PAY-4002 --> Eine Funktion wurde hinzugefügt, mit der Händler [die Reihenfolge ihrer Zahlungsoptionen sortieren](configure-admin.md#paypal-payment-buttons) um bestimmte Zahlungsoptionen zu priorisieren. Diese Funktion ermöglicht eine höhere Gesprächsrate beim Checkout.

![Neu](../assets/new.svg)<!-- PAY-4035 --> Händler können jetzt die Konsistenz ihrer Stores effizient überwachen und mithilfe des neuen [Transaktionsberichts](reporting.md#transactions-report-view), der auf der Admin-[!DNL Payment Services] verfügbar ist, Transaktionsprobleme identifizieren. Der Bericht enthält auch Daten zu den Autorisierungsraten und negativen Trends bei Transaktionen.

## v2.1.0

_9. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- Issue xxx --> Unterstützung für Adobe Commerce 2.4.7-beta1 wurde hinzugefügt.

![Neu](../assets/new.svg)<!-- Issue xxx --> Hinzugefügt [Verfügbarkeit in folgenden Ländern und assoziierten Währungen](introduction.md#availability): Australien, Frankreich, Großbritannien.

![Neu](../assets/new.svg)<!-- Issue PAY-4296 --> Hinzugefügte [erweiterte Ressourcen für Administratorrollen](configure-admin.md#configure-roles) um sicherzustellen, dass Admin-Benutzer Bestellungen für Kunden erstellen und verwalten und [!DNL Payment Services] Menü „Verkauf“ anzeigen können.

![Neu](../assets/new.svg)<!-- Issue PAY-4236 --> Hinzugefügt [automatische Stornierung für Bestellungen, bei denen beim Checkout Fehler auftreten](checkout.md#order-auto-voided-if-error).

![Neu](../assets/new.svg)<!-- Issue PAY-4183 --> Es wurde eine Funktion [Anzeige der Optionsschaltfläche für Kredit-/Debitkartenzahlungen](payments-options.md#paypal-debit-or-credit-card-button) auf der Kaufbestätigungsseite erstellt.

## v2.0.0

_10. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg)<!-- Issue PAY-4152 --> Es wurde Unterstützung für PHP 8.2 und Adobe Commerce 2.4.6 hinzugefügt. Nicht kompatibel mit PHP 7.x.

## v1.6.1

_10. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Behebung](../assets/fix.svg)<!-- Issue PAY-4226 --> Es wurde ein Problem behoben, das neue [!DNL Payment Services] daran hinderte, den Checkout in der Admin zu verwenden.[!DNL Payment Services] verwendete zuvor die Commerce-Kunden-ID, die für neue Kunden nicht vorhanden ist.

![Behebung](../assets/fix.svg)<!-- Issue PAY-4205 --> Es wurde ein Problem behoben, das dazu führte, dass der angegebene Status der Versandadresse beim Checkout mit der Option „PayPal[&#x200B; durch den Status in den Standardsteuereinstellungen ersetzt &#x200B;](payments-options.md#paypal-payment-buttons). Jetzt können Kunden ihre Bestellungen in einen anderen als den in den Steuereinstellungen des Händlers als Standard konfigurierten Status senden lassen.

![Behebung](../assets/fix.svg)<!-- Issue PAY-4202 --> Es wurde ein Problem behoben, das Kunden daran hinderte, mithilfe der Kartenabdeckung einen Kauf abzuschließen oder eine Vault-Zahlungsmethode für einen Store [mithilfe der `Authorize and Capture` Zahlungsaktion) &#x200B;](production.md#set-payment-services-as-payment-method). Zuvor trat der Fehler „Provider Vault ID nicht gefunden“ auf, wenn der Kunde versuchte, seine Vault-Kreditkarten zu verwenden oder zu ändern.

## v1.6.0

_17. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Neu](../assets/new.svg)<!-- Issue PAY-3540 --> Hinzugefügte [PCI 3DS-Compliance-Funktion für Händler, die in der Europäischen Union (EU) und Großbritannien Geschäfte tätigen](security.md#3ds). Diese zusätzliche Sicherheitsebene, die von den Käufern verlangt, sich bei ihrem Kreditkartenaussteller zu authentifizieren, trägt dazu bei, Online-Betrug zu verhindern und ist im Rahmen der EU-Compliance-Vorschriften erforderlich.

![Neu](../assets/new.svg)<!-- Issue PAY-3609 --> Es wurde die Möglichkeit hinzugefügt, [Vaulting von Karten in Admin zu aktivieren](vaulting.md#use-vaulting-in-the-admin). Auf diese Weise können Händler mithilfe ihrer Vault-Zahlungsmethoden eine Bestellung für Kunden in der Admin erstellen.

## v1.5.4

_29. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4110 --> Es wurde ein Problem behoben, das Käufer daran hinderte, eine Bestellung mithilfe von Zahlungsschaltflächen auf der Produktseite, im Mini-Warenkorb und im Warenkorb aufzugeben. Einkäufer können jetzt Bestellungen erfolgreich abschließen.

## v1.5.3

_25. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4102 --> Es wurde eine Korrektur für ein abwärtsinkompatibles bekanntes Problem veröffentlicht. Mit dieser Version wird die Version der Service-ID-Erweiterung auf die neueste stabile Version gesperrt, sodass neue [!DNL Payment Services]-Installationen Commerce Services konfigurieren können.

## v1.5.2

_22. Dezember 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3992 --> Die Fakturierung in [!DNL Payment Services] wurde verbessert, wenn eine Zahlungsmethode abgelehnt wurde.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services] zeigt jetzt korrekt die PayPal-Zahlungsschaltflächen für Händler an, die [&#x200B; benutzerdefinierte Vorlage &quot;](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank}-Checkout auslösen“ für die Checkout-Seite verwenden. Zuvor wurden im Minicart gelegentlich die Tasten angezeigt.

## v1.5.1

_23. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Neu](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] enthält jetzt die Versionsnummer in der Kopfzeile des Benutzeragenten, damit Anfragen nicht verwendete Endpunkte verfolgen, filtern oder verwerfen können.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] zeigt jetzt Bestelldaten korrekt an, wenn eine Bestellung über die Zahlungsschaltflächen von der Produktseite aus aufgegeben wird.

## v1.5.0

_18. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Neu](../assets/new.svg)<!-- Issue PAY-3880 --> Ein Käufer kann jetzt [&#x200B; Kreditkarteninformationen während des Checkouts Vault (speichern), &#x200B;](vaulting.md) sie bei einem späteren Kauf für dasselbe oder ein anderes Geschäft innerhalb desselben Händlerkontos zu verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-3950 --> Händler können jetzt die Funktion [Instant Purchase Commerce](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) für ihre Stores aktivieren, sodass Käufer ([Vault-Kreditkarteninformationen) &#x200B;](vaulting.md) können, um den Checkout zu beschleunigen.

## v1.4.1

_14. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Behebung](../assets/fix.svg)<!-- Issue PAY-3766 --> Wenn die Zahlungsmethode eines Kunden abgelehnt wird, ist die sichtbare Fehlermeldung beschreibender. Er empfiehlt dem Kunden, die Zahlungsinformationen erneut einzugeben und erneut zu versuchen, eine andere Zahlungsmethode auszuprobieren oder sich bezüglich der abgelehnten Transaktion an seine Bank zu wenden.

## v1.4.0

_30. September 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Neu](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] bietet jetzt die Möglichkeit, ein Händlerkonto einzurichten, um [mehrere PayPal-Geschäftskonten zu &#x200B;](configure-admin.md#use-multiple-paypal-accounts). Dadurch kann der Händler Ihre Geschäfte in mehreren Ländern mit unterschiedlichen Währungen betreiben oder Adobe Commerce für einen Teil Ihres Geschäfts verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-3231 --> Händler können [eine [!UICONTROL Soft Descriptor]](configure-admin.md) zu Websites oder einzelnen Store-Ansichten-Konfigurationen hinzufügen, die auf den Kontoauszügen für Kundentransaktionen angezeigt werden, um Marken, Stores oder Produktlinien abzugrenzen.

![Neu](../assets/new.svg)<!-- Issue PAY-3707 --> [Aktivieren oder Deaktivieren von Kreditkartenfeldern und PayPal-Zahlungs-Schaltflächen](configure-admin.md#paypal-payment-buttons) für den Checkout in[!DNL Payment Services] Einstellungen.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3546 --> Wenn ein Kunde auf **[!UICONTROL Edit cart]** klickt, wird die Seite zur Warenkorbseite weitergeleitet und zeigt die aktualisierten Artikel an, anstatt einen leeren Warenkorb anzuzeigen.

## v1.3.1

_6. September 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Es wurde &#x200B;](../assets/fix.svg)<!-- Issue PAY-3663 --> Problem behoben: Wenn im Geschäft eines Händlers eine Bestellung erfasst wird, die mit einer nicht-globalen Währung autorisiert wurde, wird der Erfassungsprozess abgeschlossen und es wird kein Fehler angezeigt.

## v1.3.0

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Neue](../assets/new.svg)<!-- Issue PAY-XX --> Allgemeine Verfügbarkeitsversion—[!DNL Payment Services] wird jetzt [unterstützt von [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.5](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay ist jetzt mit dem Safari-Browser v15.5 auf Mobilgeräten und Desktops kompatibel.

## v1.2.0

_29. Juni 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay ist mit dem Safari-Browser 15.5 auf Mobilgeräten und Desktop-Computern inkompatibel. Wenn Sie Safari Version 15.5 verwenden, können Sie den Checkout mit Apple Pay nicht abschließen.

![Es wurde &#x200B;](../assets/fix.svg)<!-- Issue PAY-3264 --> Problem behoben. Wenn ein angemeldeter Benutzer zuvor eine andere Rechnungs-/Versandadresse als die Standardadresse für sein Konto ausgewählt hatte, schlug der Checkout-Vorgang fehl. Jetzt wird die ausgewählte Rechnungs-/Lieferadresse gesendet (anstelle der standardmäßig gespeicherten Adresse) und der Checkout wurde erfolgreich abgeschlossen.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3314 --> Wenn Sie die PayPal-Zahlungsschaltflächen für den Checkout deaktivieren, werden keine Fehler angezeigt.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3330 --> Zahlungen schlagen beim Checkout nicht mehr fehl, wenn ein Gastbenutzer eine Telefonnummer mit Bindestrichen eingibt.

![Es wurde ein Problem &#x200B;](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 -->. Wenn Commerce Services-Anmeldeinformationen ungültig sind, werden Sie jetzt [!DNL Payment Services], indem auf der [!DNL Payment Services]-Startseite in Admin ein Fehler bezüglich der Anmeldeinformationen angezeigt wird.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] ist nicht kompatibel mit `commerce-data-export` Version 101.20 und höher, weshalb die Kompatibilität mit der [[!DNL Channel manager] Erweiterung](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html) gegeben ist.

## v1.1.0

_31. März 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Neue](../assets/new.svg)<!-- Issue PAY-2127 --> Allgemeine Verfügbarkeitsversion—[!DNL Payment Services] wird jetzt [unterstützt von [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.4](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

![Neu](../assets/new.svg)<!-- Issue PAY-2682 --> Die [!DNL Payment Services]-Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist jetzt für kanadische Händler verfügbar. Händler können die Zahlungskonfiguration entweder auf [Französisch](introduction.md?lang=fr#accepted-credit-cards-and-currencies) oder [Englisch](introduction.md#accepted-credit-cards-and-currencies) anzeigen.

![Neu](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] unterstützt [Canadian Dollar (CAD)](introduction.md#accepted-credit-cards-and-currencies) für Kreditkarten und PayPal-Transaktionen.

![Neu](../assets/new.svg)<!-- Issue PAY-2680 --> Händler können [Onboarding [!DNL Payment Services]](onboard.md)-Erweiterung in englischer oder französischer Sprache.

![Neu](../assets/new.svg)<!-- Issue PAY-2678 --> Händler können jetzt Finanzberichte anzeigen, sowohl die [Bestellzahlungsstatus](order-payment-status.md) als auch [Auszahlungen](payouts.md) in kanadischen Dollar (CAD).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] ist jetzt mit [PHP 8.1](https://www.php.net/releases/8.1/en.php) kompatibel.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3017 --> Der Sandbox-Modus-Warnhinweis wurde verbessert, sodass korrekte Warnhinweise mit mehreren Stores angezeigt werden.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2742 --> Sie können jetzt verfügbare Zahlungsmethoden wie Venmo auf der Store-Ansichtsebene aktivieren und deaktivieren. Zuvor konnten Sie nur Zahlungsmethoden pro Website konfigurieren.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2277 --> Sie können jetzt einzelne PayPal[Zahlungsschaltflächen selektiv aktivieren oder deaktivieren](configure-admin.md#payment-buttons).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2561 --> Zuvor entfernte Produkte werden nicht im Warenkorb auf der Seite _Bestellung überprüfen_ angezeigt.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2842 --> Testen von Kreditkartentransaktionen [kann mit PayPal fehlschlagen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) wenn Zahlungen in einer Sandbox-Umgebung verarbeitet werden.

## v1.0.0

_29. November 2021_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce, Version 2.4.0 und neuer

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Allgemeine Verfügbarkeit - [[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) wird jetzt von [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.3-p1 unterstützt.

![Neu](../assets/new.svg)<!-- Issue PAY-124 --> Die [!DNL Payment Services]-Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] kann entweder für Instanzen [[!DNL Adobe Commerce] in der Cloud-Infrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) oder [On-Premise](install.md#on-premises) installiert werden. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] unterstützt ein [Sandbox-Konto](sandbox.md) mit dem Händler die Erweiterung im Testmodus bewerten können.

![Neu](../assets/new.svg)<!-- Issue PAY-666 --> Händler können [Zahlungsdienste konfigurieren](configure-admin.md) Erweiterung mit grundlegenden Zahlungsverhalten, wie z. B. die Verwendung [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) Wechsels zwischen Sandbox- oder Produktionsumgebungen.

![Neu](../assets/new.svg)<!-- Issue PAY-780 --> Ihre Kunden können mit [!DNL Payment Services] oder über die [manuelle Bestellerstellung) &#x200B;](create-order.md).

![Neu](../assets/new.svg)<!-- Issue PAY-1856 --> Umfassende Berichte über [Bestellzahlungsstatus](order-payment-status.md) und [Auszahlungsberichte](payouts.md) sind für [!DNL Payment Services] verfügbar, um Ihnen einen klaren Überblick über die Bestellungen Ihres Stores und die damit verbundenen Zahlungen zu geben.

![Neu](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] unterstützt eine flexible Preisstaffelung, die auf dem gesamten Verarbeitungsvolumen basiert und an jeden Händler angepasst ist.

![Neu](../assets/new.svg)<!-- Issue PAY-1443 --> Sie können [&#x200B; Aussehen und Verhalten &#x200B;](payments-options.md) PayPal-Zahlungs-Buttons und Kreditkartenfelder für die [!DNL Payment Services]-Erweiterung einfach anpassen.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2473 --> Die Verwendung [falschen Composer-Schlüsseln](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) während der Installation der Erweiterung verhindert, dass der Benutzer sich [&#x200B; mit &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) richtigen `MAGEID` authentifiziert.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] Berichte [werden möglicherweise nicht sofort synchronisiert](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2475 --> Ihr [PayPal-Sandbox-](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) für [!DNL Payment Services] kann nicht überprüft werden, wenn Sie dieses Konto beim Onboarding erstellen.
