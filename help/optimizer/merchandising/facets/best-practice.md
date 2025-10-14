---
title: Best Practices für Facetten
description: Erfahren Sie mehr über die Best Practices für die Implementierung von Facetten in Ihrem Store.
role: Admin, Developer
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 3131cc27a25d1bf958071b973f1d4bf1a68be152
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Best Practices für Facetten

Die Filter- und Facettenfunktionalität ist eine wichtige Komponente Ihrer [!DNL Adobe Commerce Optimizer]-Site, die das Käufererlebnis verbessert, indem sie es Käufern ermöglicht, die Suchergebnisse einzugrenzen und Produkte effizienter zu finden. Diese Funktion hilft Käufern, große Kataloge von Artikeln zu sortieren, indem sie bestimmte Kriterien anwendet, was den Einkaufsprozess schneller, einfacher und befriedigender macht. Durch die Implementierung effektiver, käuferfreundlicher Filter und Facetten können Sie Kunden dabei unterstützen, schnell und effizient genau das zu finden, was sie benötigen, was letztendlich die Zufriedenheit und die Konversionsraten steigert.

## Tipps zum Optimieren von Facetten

- Bestimmen Sie die relevantesten und nützlichsten Attribute für Ihre Produkte, wie Titel, Kategorie, Marke, Preisspanne, Farbe und Größe und legen Sie sie als [dynamische Facetten“ &#x200B;](type.md). 
- Legen Sie Produktattribute fest und sortieren Sie sie, die in Ihrem gesamten Katalog konsistent und für Ihre Produkte äußerst relevant sind, um die Relevanz und Filtermöglichkeiten für Ihre Kunden zu verbessern.
- Stellen Sie sicher, dass Facettenbeschriftungen leicht verständlich sind und auf der gesamten Site konsistent benannt werden. Verwenden Sie beispielsweise „Preisspanne“ anstelle von „Kosten“.
- Vermeiden Sie es, Käufer zu überfordern, indem Sie die Anzahl der Facetten auf die wichtigsten beschränken. Zu viele Optionen können zu Entscheidungsermüdung führen. Standardmäßig ist [!DNL Adobe Commerce Optimizer] auf maximal 100 Attribute beschränkt, die als Facetten konfiguriert sind, und auf 30 Buckets, die innerhalb jeder Facette zurückgegeben werden. Weitere Informationen zu [Facettenbegrenzungen](../../boundaries-limits.md#catalog-views-and-policies). 
- Kunden ermöglichen, mehrere Filterkriterien gleichzeitig auszuwählen, um die Ergebnisse zu verfeinern. Beispielsweise können Käuferinnen und Käufer sowohl die Farben „Rot“ als auch „Blau“ auswählen.
- Die Anzahl der verfügbaren Produkte neben jeder Facette anzeigen, um Kundinnen und Kunden einen Eindruck von den Suchergebnissen zu vermitteln, die sie erwarten können.
- Implementieren Sie ausblendbare Facettenabschnitte, um die Oberfläche sauber und verwaltbar zu halten, insbesondere auf mobilen Geräten.
- Kunden ermöglichen, einzelne Facetten oder alle ausgewählten Filter zurückzusetzen, um eine neue Suche zu starten.
- Wenn Sie mit einer großen Anzahl von Attributen zu kämpfen haben, sollten Sie Attribute zu einem einzigen „Meta-Attribut“ kombinieren. Beispielsweise haben Schuhe in der Regel numerische Größen, während Hemden in der Regel die Größe „S/M/L/XL“ haben. Diese beiden Größentypen können zu einem durchsuchbaren Attribut kombiniert werden.
