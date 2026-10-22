---
title: Verbessern der Produkterkennung mit der Adobe Commerce Live Search
description: Erfahren Sie, wie Sie mit Search Performance Insights und semantischer Suche Kunden bei der Suche nach relevanten Produkten unterstützen können.
audience: Merchandisers, commerce administrators, and store owners
autotag-review: '2026-10-21T12:57:39.807Z'
TQID: 'https://experienceleague.adobe.com/vUbbKdcd7RFb3YUNNjlW4u7AgtiXJKeZeRs9uJwxYyY'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
topic_v2:
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
source-git-commit: f54c816fd23786ec519d5c890bc2664c3dcf8c6f
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 0%
---

# Verbessern der Produkterkennung mit der Adobe Commerce Live Search

<table style="table-layout:auto">
<tr style="border: 0;">
   <td valign="middle" style="vertical-align: middle;"><img alt="Porträt von Sandra Gonzalez Mangana" src="../../assets/guidance-and-insights/live-search-author-avatar-sgonzalezmangana.png" width="96"><br><strong>Sandra Gonzalez Mangana</strong><br><em>Senior Product Manager</em></td>
</tr>
</table>

*Helfen Sie Käufern, die benötigten Produkte mit Einblicken in die Suchleistung und semantischer Suche zu finden.*

Die richtigen Produkte in Ihrem Katalog zu haben, ist nur ein Teil des Einkaufserlebnisses. Außerdem müssen Käufer in der Lage sein, diese Produkte anhand der Wörter, Ausdrücke und Fragen zu finden, die sie natürlich verwenden.

Die Adobe Commerce-Live-Suche bietet Einblicke in die Suchleistung, die Ihnen dabei helfen, Erkennungsprobleme zu erkennen und das Erlebnis zu verfeinern. Verwenden Sie diese Einblicke, um herauszufinden, wo Käuferinnen und Käufer Schwierigkeiten haben, und nicht nur, ob die Suche Ergebnisse liefert.

## Suche nach Signalen in der Suchleistung

Überprüfen Sie im Arbeitsbereich Live Search-Performance die Metriken wie eindeutige Suchen, ergebnisfreie Suchen, beliebte Ergebnisse, Clickthrough-Rate, Konversionsrate und durchschnittliche Klickposition. Verwenden Sie sie, um Trends zu identifizieren und zu entscheiden, welche Abfragen oder Produkte beachtet werden müssen. [Leistung](https://experienceleague.adobe.com/de/docs/commerce/live-search/live-search-admin/performance)

![Arbeitsbereich „Performance der Live-Suche“ mit eindeutigen Suchvorgängen, durchschnittlicher Klickposition, Clickthrough-Rate, Konversionsrate und Nullergebnisrate mit Registerkarten für eindeutige Suchvorgänge, Nullergebnisse und beliebten Ergebnissen](../../assets/guidance-and-insights/live-search-performance-dashboard.png){width="800" zoomable="yes"}

*Der Arbeitsbereich Leistung der Live-Suche zeigt die zu überprüfenden Metriken. Die angezeigten Werte sind Beispieldaten.*

Betrachten wir diese Signale:

- **Null-Ergebnisse-Suchen:** Abfragen ohne Ergebnisse können auf Lücken in Ihrem Katalog, Ihren Produktinformationen oder Ihrer Sucheinrichtung verweisen. Ziel ist es, Suchvorgänge ohne Ergebnis unter 5 % zu halten. Eine Rate oberhalb dieser Schwelle ist ein Signal, das untersucht werden sollte.
- **Niedriger Clickthrough oder schwache Clickposition:** Kunden sehen möglicherweise Ergebnisse, die nicht ihren Anforderungen entsprechen, oder relevante Produkte sind möglicherweise nicht auffällig genug. Um die Interaktion sicherzustellen, streben Sie mindestens 50 % der Suchen an, sodass ein Produktklick erfolgt.
- **Niedrige Konversionsrate bei der Suche** Überprüfen Sie, ob die Suche Kunden dabei hilft, von einer Abfrage zu einem Kauf zu wechseln. Eine Konversionsrate von über 3 % wird angestrebt.

Behandeln Sie diese als Benchmark und Diagnosesignale, nicht als universelles „Pass-or-fail“. Die Leistung variiert je nach Branche, Katalogkomplexität, Kundenverhalten und Art der Messung der einzelnen Metriken. Etablieren Sie eine Grundlinie für Ihren Store und vergleichen Sie die Leistung im Zeitverlauf. Die Ergebnisse können je nach Katalog, Kunden und Art der Ergebnismessung variieren.

## Übereinstimmung mit dem Kundenwunsch, nicht nur exakte Wörter

Käufer beschreiben Produkte nicht immer unter Verwendung der Terminologie in Ihrem Katalog. Jemand, der beispielsweise nach „bequemen Schuhen für den ganzen Tag stehen“ sucht, könnte an Produkten interessiert sein, die als „gepolsterte Laufschuhe“ beschrieben werden.

Die semantische Suche verwendet Bedeutung und Kontext neben der Keyword-Zuordnung und hilft dabei, Abfragen in natürlicher Sprache mit relevanten Produkten zu verbinden, auch wenn die Abfrage nicht genau mit dem Katalogtext übereinstimmt. Live Search kombiniert Keyword- und semantische Übereinstimmung in einem Sucherlebnis. [Semantische Suche](https://experienceleague.adobe.com/de/docs/commerce/live-search/live-search-admin/semantic-search)

Die semantische Zuordnung kann bei der explorativen Suche hilfreich sein, die Relevanz hängt jedoch weiterhin von den in Ihrem Katalog verfügbaren Produkten und Informationen ab. Überprüfen Sie bei Suchen nach einem exakten Modell, einer Spezifikation oder einer Kompatibilitätsanforderung, ob die Ergebnisse präzise sind.

## Überprüfen der semantischen Suche für Ihre -Bereitstellung

Die Einrichtung hängt vom verwendeten Adobe Commerce-Produkt ab:

- **Adobe Commerce in der Cloud-Infrastruktur oder lokal:** Die semantische Live Search-Suche ist für Adobe Commerce 2.4.4 und höher verfügbar. Gehen Sie im Admin zu Marketing > SEO &amp; Search > Live Search, öffnen Sie Einstellungen, aktivieren Sie die semantische Suche und speichern Sie. Es unterstützt englische Kataloge. [Einstellungen - Semantische Suche](https://experienceleague.adobe.com/de/docs/commerce/live-search/live-search-admin/settings)
- **Adobe Commerce as a Cloud Service:** Das System aktiviert standardmäßig die semantische Suche. Es unterstützt englische Kataloge. [Semantische Suche](https://experienceleague.adobe.com/de/docs/commerce/live-search/live-search-admin/semantic-search)
- **Adobe Commerce Optimizer:** Das System aktiviert standardmäßig die semantische Suche. Sie können optional Steuerelemente wie semantische Verstärkung und Ähnlichkeitsschwellenwert anpassen. Die Einstellungen umfassen auch die Option für die Fuzzy-Suche. [Semantische Suche](https://experienceleague.adobe.com/de/docs/commerce/optimizer/setup/semantic-search) ・ [Einstellungen - Optionale Abstimmung](https://experienceleague.adobe.com/de/docs/commerce/optimizer/settings)

## Sucheinblicke in Aktion umwandeln

Verwenden Sie einen kontinuierlichen Überprüfungszyklus, um die Produkterkennung zu verbessern:

1. **Suchen von Abfragen zur Untersuchung.** Überprüfen Sie ergebnisfreie Suchen, beliebte Abfragen und Suchen mit geringer Interaktion.
2. **Überprüfen Sie, was der Käufer verlangt.** Stellen Sie fest, ob die Abfrage auf ein fehlendes Produkt, eine nicht übereinstimmende Formulierung oder unklare Produktdaten verweist.
3. **Produktinformationen verbessern.** Machen Sie Produktattribute und Beschreibungen genau und nützlich für die Begriffe, die Kundinnen und Kunden verwenden. Für die Live-Suche empfiehlt Adobe, die entsprechenden durchsuchbaren Attribute und Gewichtungen einzurichten und sicherzustellen, dass die Attributdaten relevant sind. [Best Practices für die Live-Suche](https://experienceleague.adobe.com/de/docs/commerce/live-search/best-practice)
4. **Sucherlebnis verfeinern.** Verwenden Sie gegebenenfalls Suchregeln, Synonyme und Facetten, um Käufern zu helfen, relevante Ergebnisse zu finden und einzugrenzen. [Best Practices für die Live-Suche](https://experienceleague.adobe.com/de/docs/commerce/live-search/best-practice)
5. **Ergebnisse überprüfen und wiederholen.** Überwachen Sie dieselben Abfragen und Leistungssignale, nachdem Sie Änderungen vorgenommen haben, und passen Sie sie dann entsprechend den Aktionen der Kunden an.

## Zählung aller Suchvorgänge vornehmen

Eine Suchanfrage ist ein Signal dafür, was ein Kunde möchte. Indem Sie Suchleistungseinblicke mit relevanten Produktinformationen und den richtigen Suchfunktionen kombinieren, können Sie es Käufern erleichtern, Produkte zu finden, die ihren Anforderungen entsprechen.

### Weitere Informationen

- [Was ist die Live-Suche?](../../../live-search/overview.md)
- [Best Practices für die Live-Suche](../../../live-search/best-practice.md)
- [Semantische Suche](../../../live-search/semantic-search.md) für Adobe Commerce auf Cloud-Infrastruktur
- [Semantische Suche](../../../optimizer/setup/semantic-search.md) für Adobe Commerce Optimizer
