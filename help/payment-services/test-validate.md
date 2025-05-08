---
title: Testen und Validieren
description: Tests und Validierungen helfen sicherzustellen,  [!DNL Payment Services]  die Funktionen erwartungsgemäß funktionieren und die besten Zahlungsoptionen für Ihre Kunden bereitstellen
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Testen und Validieren

Bevor Sie Ihren Käufern [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] zur Verfügung stellen, empfiehlt es sich, diese in Ihrer Sandbox-Umgebung _und)_ Produktion zu testen. Tests und Validierung helfen sicherzustellen, dass [!DNL Payment Services] Funktionen erwartungsgemäß funktionieren und die besten Zahlungsoptionen für Ihr Geschäft und Ihre Kunden bieten.

## Testen in Sandbox-Umgebung

Das Testen von [!DNL Payment Services] in einer Sandbox-Umgebung ist ein wichtiger Validierungsschritt, auch wenn es sich um eine simulierte Umgebung handelt, die nur mit der PayPal-Sandbox und nicht mit echten Banken und Händlern verbunden ist.

1. Schließen Sie einen erfolgreichen Checkout aus Ihrem Geschäft ab, entweder mit [Kreditkartenfeldern](payments-options.md#credit-card-fields) oder einer der [PayPal-Zahlungsschaltflächen](payments-options.md#paypal-smart-buttons). Weitere Informationen [ Verwendung gefälschter Kreditkarten zum Testen finden ](#testing-credentials) unter „Testen von Anmeldeinformationen“.
1. Erfassen Sie (wenn Ihre Zahlungsaktion [auf `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method) eingestellt), [Rückerstattung](refunds.md) oder [Annullierung](voids.md) die gerade abgeschlossene Bestellung. Sie können auch einfach [Rechnung erstellen](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"} für eine Bestellung, wenn Ihre Zahlungsaktion auf `Authorize` statt auf `Authorize and Capture` gesetzt ist.
1. Zeigen Sie die Transaktion und andere Informationen innerhalb von 24-48 Stunden im [Auszahlungsbericht](payouts.md) an.
1. Weitere Informationen zur Bestellung finden Sie im [Bericht zum Status der ](order-payment-status.md).

### Testen von Anmeldeinformationen

Beim Testen und Validieren Ihrer Sandbox müssen Sie gefälschte Kreditkartennummern verwenden, damit Sie keine echten Gebühren für ein vorhandenes Kreditkartenkonto erstellen.

Verwenden Sie den Kreditkartengenerator von PayPal, um [zufällige Kreditkarteninformationen) zum Testen ](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) generieren.

So testen Sie Apple Pay im Sandbox-Modus:

* Erstellen Sie ein [Apple Sandbox-Tester](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account)Konto, einschließlich gefälschter Kreditkarten- und Rechnungsinformationen.
* [Registrieren von Sandbox-Domains](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>Die Sandbox-Zahlungsabwicklung von PayPal ist manchmal langsam, und der Service kann gelegentlich ausfallen. Diese Situation ist kein Hinweis auf die Geschwindigkeit und Effizienz der Verarbeitung von Live-Produktzahlungen.

## Test in Produktion

Es wird dringend empfohlen, [!DNL Payment Services] in der Produktion mit echten Kreditkarten und Banken zu testen, bevor Sie diese Funktion Käufern offenlegen. Obwohl das Testen von [!DNL Payment Services] in Sandbox wichtig ist, ist das Testen in der Produktion die sicherste Methode, um sicherzustellen, [!DNL Payment Services] wie erwartet funktioniert.

Sie haben zwei Möglichkeiten, [!DNL Payment Services] in der Produktion zu testen:

* Wählen Sie einen Zeitpunkt aus, zu dem keine Bestellungen von Käufern aufgegeben werden.
* Verwenden Sie einen Webstore, auf den Käufer vorübergehend nicht zugreifen können, der Ihnen jedoch zum Testen zur Verfügung steht.

Testen Sie Ihre Produktion mit echten Kreditkarten und PayPal-Konten und testen Sie den gesamten Lebenszyklus einer Zahlung, einschließlich Erfassung und Rückerstattung. Wenn Sie den gesamten Checkout- und Zahlungsfluss während des Tests abschließen, erhalten Sie ein klares Bild davon, wie Ihre [!DNL Payment Services]-Funktionalität funktionieren wird, wenn Live-Shopper sie verwenden.

Sie sollten auch überprüfen, ob die Informationen, die auf den Kontoauszügen für die Zahlungsmethoden angezeigt werden, die Sie in Produktionstests verwenden, korrekt und erwartet sind (einschließlich der Beschreibung Ihres Unternehmens).

Um Apple Pay im Produktionsmodus zu testen, müssen Sie [Ihre Produktionsdomänen registrieren](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
