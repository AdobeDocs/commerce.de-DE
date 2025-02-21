---
title: Verarbeitung der Ebenen 2 und 3
description: Kartenzahlungsverarbeitungs-Ebenen innerhalb  [!DNL Payment Services]  Transaktionen.
role: Admin
feature: Payments
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Verarbeitung der Ebenen 2 und 3

Es gibt drei Stufen der Kartenverarbeitung, die über [!DNL Payment Services] verfügbar sind:

* Stufe 1 ist die häufigste, erfordert weniger Informationen und verursacht daher im Allgemeinen höhere Interbankenentgelte als Transaktionen, die mit Daten der Stufe 2 oder 3 verarbeitet werden, die in der Regel mit Unternehmens- und Kaufkreditkarten zusammenhängen.

* Bei Stufe 2 und Stufe 3 können [!DNL Payment Services] Kunden mit Interchange Plus (IC++)-Preisen, die eine Vielzahl von Kauf- oder Firmenkartentransaktionen akzeptieren, eine niedrigere Verarbeitungsrate erhalten, indem sie [!DNL Payment Services] ermöglichen, mehr Informationen über eine Transaktion zu senden. Wenn die Transaktion entsprechend den Anforderungen an das Kartennetz qualifiziert ist, kann der Händler eine niedrigere Verarbeitungsrate für eine bestimmte Transaktion erhalten.

>[!NOTE]
>
>Die Preise der Stufen 2 und 3 gelten nur für Visa- und MasterCard-Transaktionen. American Express bietet nur Preise der Stufe 2 an. Discover bietet weder Stufe 2 noch Stufe 3 Preise. Weitere Informationen finden [ in der ](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank}-Dokumentation für PayPal-Entwickler unter „Zahlungsabwicklung“.

Siehe [Was ist IC++?Weitere Informationen finden Sie in der Entwicklerdokumentation zu PayPal ](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank}.

Die Verarbeitungsdaten der Stufen 2 und 3 ermöglichen es Händlern, ihre IC++-Preise zu senken, wenn sie zusätzliche Details zum Kauf angeben, die das Prozessorrisiko reduzieren und positive Aspekte bieten:

* Große Kunden zahlen weniger, wenn sie diese Verarbeitungsdaten bereitstellen.

* Die Wahrscheinlichkeit, dass Kunden in betrügerische Situationen geraten, ist geringer, da die Bestellungen über mehr Informationen verfügen.

Kartennetzwerke wie Visa und Mastercard bestimmen jedoch letztlich, ob eine Transaktion für die Verarbeitung auf Stufe 2 oder Stufe 3 in Frage kommt:

* Daten der Stufe 2 enthalten zusätzliche Informationen, wie z. B. den Steuerbetrag für die Bestellung oder den Kundencode oder die Bestellnummer.

* Bei den Daten der Stufe 3 handelt es sich um detailliertere Informationen über den Verkauf, was dazu beiträgt, dass noch niedrigere Interbankensätze als bei Stufe 2 gelten. Daten der Stufe 3 enthalten Informationen wie eine Beschreibung des gekauften Artikels, die Menge der gekauften Einheiten, die Maßeinheit für die bestellten Artikel und andere spezifische Details.

[!DNL Payment Services] sammelt diese Daten und liefert detaillierte Berichte über Ihre Zahlungsvorgänge.

## Kartenzahlungstransaktionen der Stufen 2 und 3 in [!DNL Payment Services]

Um sich für die Verarbeitung auf Stufe 2 oder Stufe 3 zu qualifizieren, müssen die Händler die vorherigen Informationen übermitteln, obwohl es die Kartennetzwerke sind, die letztendlich bestimmen, für welche Stufe eine Transaktion bei der Verarbeitung qualifiziert ist.

Weitere Informationen finden Sie in der [ zu ](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} in der Entwicklerdokumentation zu PayPal.

Die Verarbeitung der Ebenen 2 und 3 ist für [!DNL Payment Services] Händler auf Store-Ebene standardmäßig deaktiviert.

Level 2 und Level 3 Verarbeitung sind verfügbar, wenn Sie bereits IC++ Preise verwenden. Um diese Funktion zu aktivieren, können Sie dies über die [Befehlszeilenschnittstelle (CLI) ](configure-cli.md).

>[!IMPORTANT]
>
>Bei Fragen wenden Sie sich bitte an Ihren [!DNL Payment Services] Account Manager.
