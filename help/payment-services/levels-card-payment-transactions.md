---
title: Verarbeitung der Ebenen 2 und 3
description: Kartenzahlungsverarbeitungs-Ebenen innerhalb  [!DNL Payment Services]  Transaktionen.
role: Admin
feature: Payments, Paas, Saas
exl-id: db8993fe-dd6f-48b5-9e7b-69a0f2e08552
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Verarbeitung der Ebenen 2 und 3

[!DNL Payment Services] bietet erweiterte Kartenverarbeitungsfunktionen, mit denen Händler ihre Zahlungsvorgänge optimieren und Interbankenentgelte senken können. Es stehen drei Ebenen der Kartenverarbeitung zur Verfügung, die jeweils unterschiedliche Anforderungen an Transaktionsdaten aufweisen.

>[!CAUTION]
>
> [Fastlane](payments-options.md#fastlane-button) Bestellungen enthalten keine Daten der Stufe 2/Stufe 3, Zeileneinträge und Aufschlüsselung des Betrags.

## Datenanforderungen pro Verarbeitungsebene

![Transaktionsbericht](assets/level-processing-details.png){width="500" zoomable="yes"}

[!DNL Payment Services] sammelt diese Daten und liefert detaillierte Berichte über Ihre Zahlungsvorgänge.

## Verfügbare Verarbeitungsstufen nach Kartennetzwerk

![Kartendetails](assets/cards-details-level-processing.png){width="500" zoomable="yes"}

Weitere Informationen finden [&#x200B; in der &#x200B;](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank}-Dokumentation für PayPal-Entwickler unter „Zahlungsabwicklung“.

### Stufe 1

Stufe 1 ist die häufigste, erfordert weniger Informationen und verursacht daher im Allgemeinen höhere Interbankenentgelte als Transaktionen, die mit Daten der Stufe 2 oder 3 verarbeitet werden, die in der Regel mit Unternehmens- und Kaufkreditkarten zusammenhängen.

### Ebene 2 und 3

[!DNL Payment Services] Händler auf Interchange Plus (IC++) können sich für die Verarbeitung auf Stufe 2/Stufe 3 qualifizieren, wenn sie zusätzliche Transaktionsdetails an Kartennetze übermitteln und bestimmte Qualifikationskriterien erfüllen. Diese Werte sind besonders für Händler von Vorteil, die große Mengen an Einkaufs- oder Firmenkarten abwickeln, da sie zu erheblichen Kosteneinsparungen führen können. Die Bereitstellung detaillierter Daten der Ebenen 2 oder 3 kann:

* Niedrigere Verarbeitungsgebühren und Optimierung der Gesamtkosten
* Betrug verhindern, Prozessorisiken senken
* Verbesserung der Transaktionssicherheit

Siehe [Was ist IC++?Weitere Informationen finden Sie in der Entwicklerdokumentation zu PayPal &#x200B;](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank}.

## Kartenzahlungstransaktionen der Stufen 2 und 3 in [!DNL Payment Services]

Um sich für die Verarbeitung auf Stufe 2 oder Stufe 3 zu qualifizieren, müssen die Händler die vorherigen Informationen übermitteln, obwohl es die Kartennetzwerke sind, die letztendlich bestimmen, für welche Stufe eine Transaktion bei der Verarbeitung qualifiziert ist.

Weitere Informationen finden Sie in der [&#x200B; zu &#x200B;](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} in der Entwicklerdokumentation zu PayPal.

Die Verarbeitung der Ebenen 2 und 3 ist für [!DNL Payment Services] Händler auf Store-Ebene standardmäßig deaktiviert.

Level 2 und Level 3 Verarbeitung sind verfügbar, wenn Sie bereits IC++ Preise verwenden. Um diese Funktion zu aktivieren, können Sie dies über die [Befehlszeilenschnittstelle (CLI) &#x200B;](configure-cli.md).

>[!IMPORTANT]
>
>Bei Fragen wenden Sie sich bitte an Ihren [!DNL Payment Services] Account Manager.
