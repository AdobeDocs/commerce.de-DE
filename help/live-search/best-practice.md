---
title: Best Practices für [!DNL Live Search]
description: Erfahren Sie mehr über die Best Practices für die Implementierung von  [!DNL Live Search]  in Ihrem Store.
role: Admin, Developer
exl-id: f7700339-fb13-42fe-a249-17cd4ba36e1b
source-git-commit: 4ba9734946f551784cd429ffa7cb23358f0f9710
workflow-type: tm+mt
source-wordcount: '2429'
ht-degree: 0%

---

# Best Practices

Dieser Artikel hilft Merchandisern, ihre Site-Suchfunktion zu verbessern, um ein nahtloses und effizientes Kundenerlebnis zu gewährleisten, das die Konversionsraten maximiert. Wenn Sie die beschriebenen Strategien befolgen, erfahren Sie, wie Sie erweiterte Suchfunktionen implementieren und Ihr Suchwerkzeug kontinuierlich verfeinern, um eine optimale Leistung mit Adobe Commerce [!DNL Live Search] zu erzielen.

Die Relevanz und Effektivität von Suchergebnissen hängt von mehreren Schlüsselfaktoren ab:

- Durch gut strukturierte Produktdaten wird sichergestellt, dass Suchalgorithmen Produkte effektiv Abfragen zuordnen können. Niedrige Produktdaten führen zu schlechten relevanten Suchergebnissen. So wirken Sie sich direkt auf den Erfolg Ihrer Merchandising-Strategie aus:
   - Richten Sie die richtigen Attribute als durchsuchbar mit der entsprechenden Gewichtung ein.
   - Stellen Sie sicher, dass Daten innerhalb dieser Attribute relevant sind.
- Ein gut gestaltetes Sucherlebnis schafft Vertrauen bei den Kunden und gibt ihnen die Zuversicht, das zu finden, was sie brauchen.
- Suchregeln sind wichtig, da sie die Sichtbarkeit bestimmter Produkte basierend auf Popularität, Neuankömmlingen, Werbekriterien oder einer anderen Merchandising-Strategie erhöhen können, um Ihre Geschäftsanforderungen zu erfüllen.
- Die Facettennavigation ermöglicht es Kunden, ihre Suche zu verfeinern und schnell relevante Ergebnisse zu erhalten.

Um [!DNL Live Search] zu verwalten, gehen Sie **Marketing** > *SEO &amp; Search* > **[!DNL Live Search]** im Adobe [!DNL Commerce] Admin. 

## Optimieren der Suchfunktion

In diesem Abschnitt erfahren Sie, wie Sie Ihre Suchfunktion optimieren können, indem Sie Funktionen wie die automatische Vervollständigung verwenden, um Echtzeit-Vorschläge wie Käufertyp, Synonyme und Schreibweisen bereitzustellen, um sicherzustellen, dass Käuferinnen und Käufer Produkte finden, auch wenn sie verschiedene Wörter verwenden, Facetten, mit denen Käuferinnen und Käufer die Suchergebnisse eingrenzen können, und Suchumleitungen, um Käuferinnen und Käufer automatisch von einer Suchabfrage zu einer bestimmten Seite umzuleiten.

### AutoVervollständigen

Die automatische Vervollständigung, auch als automatische Textvervollständigung oder automatische Vervollständigung bezeichnet, ist eine interaktive Suchfunktion, die Käufern bei der Eingabe ihrer Suchbegriffe dynamisch Vorschläge anzeigt. Dies hilft Käufern, Produkte schnell und einfach zu finden, indem es Echtzeitvorschläge basierend auf ihrer Eingabe anbietet.

Das Widget [!DNL Live Search] [[!DNL popover]](storefront-popover.md) ermöglicht Optionen für die automatische Vervollständigung von Suchvorschlägen, um beliebte Produkte vorzuschlagen. Mit jedem vom Käufer eingegebenen Zeichen wird das Pop-up mit vorgeschlagenen Produkten und Miniaturbildern der wichtigsten Suchergebnisse aktualisiert.

[!DNL Live Search] beginnt mit der Rückgabe von Ergebnissen, wenn der Benutzer zwei Zeichen eingegeben hat. Bei einer Teilübereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in einer Abfrage vom Typ „Suche während der Eingabe“ ist nicht konfigurierbar.

Weitere Informationen über das [Popover](storefront-popover.md)-Widget.

### Synonyme und Schreibfehler

Die Live Search verwaltet Rechtschreibfehler standardmäßig. Sie können Synonyme einrichten, um Wörter einzuschließen, die Käufer möglicherweise verwenden, die sich von den in Ihrem Katalog angegebenen Wörtern unterscheiden. Sie wollen keinen Verkauf verlieren, weil jemand ein „Sofa“ sucht, während Ihr Produkt als „Couch“ aufgeführt ist. Sie können eine breite Palette von Suchbegriffen erfassen, indem Sie alle möglichen Wörter eingeben, die Kunden verwenden könnten, um Ihre Produkte zu finden. Sie können [Synonyme auf eine oder zwei Arten festlegen](synonyms-add.md#step-2-define-the-synonym-by-type) um die Ergebnisse zu verbessern.

#### Tipps zur Optimierung von Synonymen

- Ordnen Sie nun alle Markenbezeichnungen und Abkürzungen ihren vollständigen Namen zu, z. B. „HP“ für „Hewlett-Packard“ und die gebräuchlichen Produktspitznamen, z. B. &quot;iPhone&quot; für &quot;Apple iPhone&quot;.
- Geben Sie branchenspezifischen Jargon und Begriffe an, die Käufer möglicherweise austauschbar verwenden, z. B. „Sneaker“ und „Laufschuhe“.
- Aktualisieren Sie die Synonym-Liste regelmäßig auf der Grundlage neuer Suchtrends, Produktzusätze und des Käuferverhaltens.
- Testen Sie die Effektivität von Synonym-Zuordnungen durch die Analyse von Suchergebnissen und Kunden-Feedback. Verfeinern Sie Zuordnungen, um die Genauigkeit und Relevanz zu verbessern.

Weitere Informationen zu Synonymen:

- [Arten von Synonymen](synonyms-type.md)
- [Erstellen von Synonymen](synonyms-add.md)
- [Verwalten von Synonymen](synonyms-manage.md)
- [Sprachunterstützung](settings.md#language)

### Facetten

Die Filter- und Facettenfunktionalität ist eine wichtige Komponente Ihrer [!DNL Commerce]-Site, die das Käufererlebnis verbessert, indem sie es Käufern ermöglicht, die Suchergebnisse einzugrenzen und Produkte effizienter zu finden. Diese Funktion hilft Käufern, große Kataloge von Artikeln zu sortieren, indem sie bestimmte Kriterien anwendet, was den Einkaufsprozess schneller, einfacher und befriedigender macht. Durch die Implementierung effektiver, käuferfreundlicher Filter und Facetten können Sie Kunden dabei unterstützen, schnell und effizient genau das zu finden, was sie benötigen, was letztendlich die Zufriedenheit und die Konversionsraten steigert.

Um ein Produktattribut als Facette einzurichten, müssen die folgenden [Eigenschaften“ festgelegt &#x200B;](facets-add.md#step-1-add-a-facet):

- **[!UICONTROL Use in Search]** -  `No`
- **[!UICONTROL Use in Layered Navigation]** -  `Filterable (with results)`
- **[!UICONTROL Use in Search Results Layered Navigation]** -  `Yes`

#### Tipps zum Optimieren von Facetten

- Bestimmen Sie die relevantesten und nützlichsten Attribute für Ihre Produkte, wie Titel, Kategorie, Marke, Preisspanne, Farbe und Größe und legen Sie sie als [dynamische Facetten“ &#x200B;](facets-type.md). 
- Legen Sie Produktattribute fest und sortieren Sie sie, die in Ihrem gesamten Katalog konsistent und für Ihre Produkte äußerst relevant sind, um die Relevanz und Filtermöglichkeiten für Ihre Kunden zu verbessern.
- Stellen Sie sicher, dass Facettenbeschriftungen leicht verständlich sind und auf der gesamten Site konsistent benannt werden. Verwenden Sie beispielsweise „Preisspanne“ anstelle von „Kosten“.
- Vermeiden Sie es, Käufer zu überfordern, indem Sie die Anzahl der Facetten auf die wichtigsten beschränken. Zu viele Optionen können zu Entscheidungsermüdung führen. Standardmäßig ist [!DNL Live Search] auf maximal 100 Attribute beschränkt, die als Facetten konfiguriert sind, und auf 30 Buckets, die innerhalb jeder Facette zurückgegeben werden. Weitere Informationen zu [Facettenbegrenzungen](boundaries-limits.md#facets). 
- Kunden ermöglichen, mehrere Filterkriterien gleichzeitig auszuwählen, um die Ergebnisse zu verfeinern. Beispielsweise können Käuferinnen und Käufer sowohl die Farben „Rot“ als auch „Blau“ auswählen.
- Die Anzahl der verfügbaren Produkte neben jeder Facette anzeigen, um Kundinnen und Kunden einen Eindruck von den Suchergebnissen zu vermitteln, die sie erwarten können.
- Implementieren Sie ausblendbare Facettenabschnitte, um die Oberfläche sauber und verwaltbar zu halten, insbesondere auf mobilen Geräten.
- Kunden ermöglichen, einzelne Facetten oder alle ausgewählten Filter zurückzusetzen, um eine neue Suche zu starten.

Weitere Informationen zu Facetten:

- [Facettentypen](facets-type.md)
- [Facetten hinzufügen](facets-add.md)
- [Facetten verwalten](facets-manage.md) (Bearbeiten, Facetten anheften, löschen, veröffentlichen)
- [Preisfacettierung](settings.md#price-faceting)

### Weiterleitungen suchen

Mit einer Suchumleitung können Sie Käufer automatisch von einer Suchanfrage zu einer bestimmten Seite umleiten. Suchumleitungen können das Kundenerlebnis verbessern und Kunden zu den relevantesten Inhalten leiten, z. B. einer Produktseite, einer Kategorie, einer Landingpage oder einem maßgeschneiderten Satz von Suchergebnissen. Suchumleitungen tragen dazu bei, das Einkaufserlebnis zu optimieren und sicherzustellen, dass Kunden schnell und effizient finden, wonach sie suchen.

Empfohlene Anwendungsfälle zum Einrichten von Suchumleitungen:

- **Beliebte Produkte oder Kategorien** - Leitet Käufer zu einer bestimmten Produktseite oder Kategorie weiter, wenn sie nach allgemeinen oder beliebten Begriffen suchen. Die Suche nach &quot;iPhone&quot; kann beispielsweise direkt zur Kategorieseite von iPhone oder zu einer bestimmten Modellseite umgeleitet werden.

- **Werbekampagnen** - Leiten Sie bei Werbe-Events oder -Verkäufen relevante Suchbegriffe auf Landingpages um, die spezielle Angebote oder vorgestellte Produkte hervorheben.

- **Markensuche** - Wenn Käufer nach einem Markennamen suchen, leiten Sie sie auf die entsprechende Seite der Marke weiter, auf der alle Produkte dieser Marke aufgeführt sind.

- **Einstellung eines Produkts** - Wenn ein Produkt eingestellt wird, können Sie die Suche nach diesem Produkt auf ähnliche Produkte oder die neue Version des Produkts umleiten.

Testen Sie immer die Umleitungen der Suche, um sicherzustellen, dass sie ordnungsgemäß funktionieren und zu den relevantesten Seiten führen. Überwachen Sie kontinuierlich ihre Leistung und nehmen Sie bei Bedarf Anpassungen vor.

Erfahren Sie, wie [Suchumleitungen verwalten](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms).

## Relevanz der Suchergebnisse verbessern

In diesem Abschnitt wird beschrieben, wie Sie die Relevanz der Suchergebnisse verbessern können, indem Sie effektive Suchregeln implementieren und Produktmetadaten verwenden, um sicherzustellen, dass genaue und detaillierte Attribute durchsuchbar sind.

### Bilder

Stellen Sie sicher, dass die untergeordneten Produkte der konfigurierbaren Produkte Bilder mit den richtigen Rollen enthalten. Übergeordnete oder untergeordnete Produkte können dazu führen, dass das Suchergebnis keine Bilder enthält.

>[!NOTE]
>
>Bilder in Suchergebnissen können je nach Suchbegriff unterschiedlich sein. Wenn der Suchbegriff bestimmt, dass ein untergeordnetes Produkt relevanter ist, werden anstelle von Bildern des übergeordneten Produkts Bilder vom untergeordneten Produkt verwendet.

### Suchregeln

Um Ihre Konversionsrate und Ihren Umsatz zu optimieren, müssen Sie effektive Suchregeln implementieren. Passen Sie Produkt-Rankings basierend auf Verkaufsdaten, Lagerbeständen und Werbeaktionen mit [Search Merchandising](rules.md) an.

Es ist von entscheidender Bedeutung, eine gut durchdachte Standard-Suchregel festzulegen. Ihre [Standardregel](rules.md#default-rule) bestimmt, wie Suchergebnisse zunächst sortiert und den Käufern angezeigt werden, wodurch ihr Gesamterlebnis verbessert und die Wahrscheinlichkeit eines Kaufs erhöht wird. Eine regelmäßige Überwachung und Anpassung dieser Regel stellt sicher, dass sie weiterhin den Bedürfnissen der Kunden und den Geschäftszielen effektiv entspricht.

#### Tipps zum Optimieren von Suchregeln

- Produkte mit hohen Verkaufsmengen oder kürzlichen Verkaufsaktivitäten heften oder ankurbeln.
- Priorisieren Sie Produkte mit hohen Bewertungen und positiven Bewertungen.
- Stellen Sie sicher, dass Artikel auf Lager höher eingestuft werden.
- Produkte mit höheren Gewinnspannen leicht priorisieren, ohne die Relevanz zu beeinträchtigen.
- Heben Sie Produkte hervor, die zum Verkauf stehen oder Teil von Sonderaktionen sind.
- Legen Sie Suchregeln während der Promotion oder des Verkaufszeitraums automatisch fest, indem Sie den Datumsbereich während des Promotion-Zeitraums verwenden.
- Passen Sie Suchergebnisse mithilfe von „Intelligent Ranking[&#x200B; wie &quot;](rules-add.md#intelligent-ranking) für Sie empfohlen“, „Am häufigsten angezeigt“ usw. an das individuelle Kundenverhalten an. Um das Kundenverhalten anzupassen, müssen Sie sicherstellen, dass das Eventing korrekt implementiert ist. Für Händler in Luma ist das Eventing vorkonfiguriert verfügbar. Bei Headless- oder benutzerdefinierten Implementierungen müssen Sie [Ereignis implementieren](https://developer.adobe.com/commerce/services/shared-services/storefront-events/) basierend auf Ihren spezifischen Anforderungen.

Weitere Informationen zu Suchregeln:

- [Merchandising-Arbeitsbereich](rules-workspace.md#set-the-scope)
- [Anforderungen](rules.md#requirements)
- [Standard-Suchregel](rules.md#default-rule)
- Verwalten von Suchregeln
   - [Erstellen](rules-add.md)
   - [Bearbeiten, Anzeigen, Löschen](rules-manage.md)
- Datenerfassung
   - [[!DNL Live Search] Ereignisse](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search)
   - [Adobe Commerce Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/)
   - [GitHub-Commerce-Ereignisse](https://github.com/adobe/commerce-events/tree/main/examples) 

### Verwenden von Produktmetadaten

Stellen Sie sicher, dass genaue und detaillierte Produktattribute [als durchsuchbar eingerichtet) &#x200B;](workspace.md#set-attributes-as-searchable). Beachten Sie, dass die Attribute „SKU“, „Name“ und „Kategorie“ standardmäßig durchsuchbar sind und nicht von der Suche ausgeschlossen werden können. Verwenden Sie für optimale Ergebnisse keine Leerzeichen in Ihren SKUs.

Um die Suchrelevanz zu erhöhen, weisen Sie jedem durchsuchbaren Attribut eine Gewichtung zu. Attribute mit einer höheren Gewichtung sollten in den Suchergebnissen höher angezeigt werden. Die Sortierung nach Relevanz wird von mehreren Kriterien beeinflusst, z. B. der Suchgewichtung. Dies bedeutet, dass manchmal Attribute mit niedrigerer Suchgewichtung immer noch mehr Relevanz haben können als Attribute mit höherer Suchgewichtung. Andere Kriterien können die Anzahl der Übereinstimmungen in einem bestimmten Attribut, die Position des gefundenen Suchbegriffs und die Gesamttextstruktur vor und nach einem Suchbegriff sein.

Stellen Sie sicher, dass jedes Produkt relevanten Inhalt in jedem durchsuchbaren Attribut hat. Es wird nicht empfohlen, ein Attribut als durchsuchbar festzulegen, wenn es große Mengen an Inhalten enthält, die die Relevanz der Suchergebnisse verringern können.

Weitere Informationen zu Produktattributen für die Suche:

- [Festlegen von Attributen als durchsuchbar](workspace.md#set-attributes-as-searchable)
- [Attributen Gewichtung zuweisen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results#weighted-search)

## Suchergebnisse überwachen

Um Suchergebnisse mit [!DNL Live Search] zu optimieren, überwachen Sie relevante Key Performance Indicators (KPIs) wie eindeutige Abfragen, durchschnittliche Klickposition, Clickthrough-Raten, Konversionsrate und Nullergebnisrate, um zu verstehen, wie Käufer mit Ihrer Suchfunktion interagieren. Diese Daten helfen Ihnen, Ihre Suchregeln regelmäßig zu aktualisieren und zu verfeinern.

Sie können diese KPIs im [!DNL Live Search]Arbeitsbereich Leistung[&#x200B; überwachen](performance.md) in dem die folgenden Metriken zu finden sind: 

- **Eindeutige Suchvorgänge** - Die Anzahl der einzelnen Suchabfragen, die auf Ihrer [!DNL Commerce]-Site durchgeführt wurden. Jede einzelne Suche wird nur einmal gezählt, auch wenn sie mehrere Male von ein und demselben oder verschiedenen Erstkäufern wiederholt wird. Diese Metrik hilft Ihnen, die Vielfalt der von Kundinnen und Kunden verwendeten Suchbegriffe zu verstehen, und bietet Einblicke in die Produkte oder Informationen, die Kundinnen und Kunden suchen. Das Tracking einzelner Suchvorgänge ermöglicht Folgendes:

   - Identifizieren Sie beliebte Suchtrends und häufig gesuchte Elemente.
   - Erkennung potenzieller Lücken in Ihrem Produktkatalog oder Inhalt.
   - Optimieren Sie Ihre Suchfunktion, indem Sie [Synonyme](synonyms.md) hinzufügen, Suchregeln erstellen oder aktualisieren.

- **Durchschnittliche Klickposition** - Gibt die durchschnittliche Position der Suchergebnisse an, auf die Käuferinnen und Käufer nach der Durchführung einer Suchabfrage auf Ihrer Site geklickt haben. Diese Metrik bietet Einblicke in die Relevanz und Effektivität Ihrer Suchergebnisse.

  Eine niedrigere durchschnittliche Klickposition (näher an 1) deutet darauf hin, dass Käufer relevante Ergebnisse schnell finden, was darauf hinweist, dass Ihre Suchstrategie effektiv ist. Dies hilft Ihnen, das Verhalten der Käufer zu verstehen und zu erkennen, wie weit sie bereit sind, zu scrollen, um das gewünschte Produkt zu finden. Wenn die durchschnittliche Klickposition hoch ist, kann dies darauf hindeuten, dass die relevantesten Ergebnisse nicht oben angezeigt werden, was eine Überprüfung und Optimierung Ihrer Suchstrategie erfordert.

- **Clickthrough-Rate (CTR)** - Misst den Prozentsatz der Käufer, die nach der Durchführung einer Suchanfrage auf ein Suchergebnis klicken. Ein hoher CTR-Wert bedeutet, dass die Suchergebnisse relevant und für Kunden attraktiv sind, da sie auf die Ergebnisse klicken, die sie finden. Die CTR-Überwachung kann dabei helfen, Bereiche zu identifizieren, in denen Verbesserungen erforderlich sind. Eine niedrige CTR kann darauf hindeuten, dass die Suchergebnisse nicht mit den Kundenabsichten übereinstimmen, was dazu führen kann, dass die Suchregeln verfeinert, die Produktdaten verbessert oder die Ergebnisdarstellung verbessert werden muss.

- **Konversionsrate** - Zeigt die Effektivität Ihrer Suchfunktion zur Steigerung des Umsatzes und zum Erreichen von Geschäftszielen an. Sie spiegelt die allgemeine Effektivität Ihrer Suchfunktion bei der Erfüllung der Kundenanforderungen und der Erleichterung eines reibungslosen Einkaufserlebnisses wider. Eine hohe Konversionsrate bedeutet, dass Ihre Suchergebnisse hochrelevant und überzeugend sind, sodass die Käufer ihre Käufe abschließen. Wenn die Konversionsrate niedrig ist, kann dies auf Probleme mit der Suchrelevanz, der Produktverfügbarkeit oder dem gesamten Käufer-Journey von der Suche bis zum Kauf hinweisen.

- **Keine Ergebnisse** - Misst den Prozentsatz der Suchanfragen auf Ihrer [!DNL Commerce]-Site, die keine Ergebnisse zurückgeben. Diese Metrik ist wichtig, um zu verstehen, wie oft die Suchvorgänge von Käufern erfolglos sind, und kann Einblicke in potenzielle Lücken in Ihrem Produktkatalog oder Ihrer Sucheinrichtung geben. Eine hohe Ergebnisrate von null kann Käuferinnen und Käufer frustrieren, was zu einem schlechten Einkaufserlebnis und potenziellen Kundenverlust führt. Es kann auf fehlende Produkte oder Kategorien in Ihrem Katalog hinweisen, nach denen Käufer suchen, die Inventar- und Produktlisten-Entscheidungen anleiten.

  Um die Nullergebnisrate zu reduzieren, haben Sie folgende Möglichkeiten:

   - Bieten Sie alternative oder verwandte Suchbegriffe an, z[&#x200B; B. &quot;](synonyms.md)&quot;, wenn keine exakten Übereinstimmungen gefunden werden.
   - Geben Sie Käufern verwandte oder alternative Vorschläge, wenn ihre Suche keine Ergebnisse liefert, indem Sie Umleitungen für die Suche festlegen.
   - Überprüfen Sie regelmäßig Nullergebnisabfragen, um Muster zu identifizieren und notwendige Anpassungen an Ihrem Produktkatalog und Ihren Sucheinstellungen vorzunehmen.

- **Beliebte Ergebnisse** - Kann Ihre Suchergebnisse erheblich verbessern, indem es sie an den Vorlieben und Verhaltensweisen der Käufer ausrichtet.

Sie können diese Metrikdaten verwenden, um Ihre Suchfunktion wie folgt zu optimieren:

- Implementieren Sie Regeln, um beliebte Produkte automatisch höher in den Suchergebnissen zu bewerten. Produkte, auf die häufig geklickt oder gekauft wird, können bevorzugt oben angezeigt werden. Kuratieren Sie Listen beliebter Produkte für bestimmte Suchabfragen manuell und stellen Sie sicher, dass diese Elemente gut sichtbar angezeigt werden.
- Markieren Sie Produkte, die derzeit im Trend liegen oder in letzter Zeit einen Anstieg der Popularität erlebt haben. Dies kann besonders bei saisonalen Veranstaltungen, Feiertagen oder Werbezeiten wirksam sein. Verwenden Sie dazu das intelligente Ranking, das beim Einrichten einer Suchregel Ihrem Anwendungsfall und Ihren Geschäftsanforderungen besser entspricht.
- Markieren Sie beliebte Filter oder Facetten. Wenn Käufer häufig nach bestimmten Marken oder Preisspannen filtern, heben Sie diese Optionen hervor, indem Sie diese Facetten anheften und entsprechend sortieren.
- Wenn eine Suche keine Ergebnisse liefert, verwenden Sie beliebte Ergebnisdaten, um alternative Produkte oder verwandte Kategorien mit hoher Käuferinteraktion vorzuschlagen.
- Analysieren Sie beliebte Suchbegriffe und Produktdaten, um wichtige Keywords zu identifizieren. Optimieren Sie die durchsuchbaren Attribute Ihres Produkts mit diesen Keywords, um die Suchrelevanz zu verbessern.
- Analysieren Sie Ihre Ergebnisdaten regelmäßig, um sich ändernde Trends, Kundenpräferenzen und -verhalten zu verstehen, die wichtigsten Suchbegriffe zu identifizieren und Probleme zu erkennen. Verwenden Sie diese Feedback-Schleife, um Ihre Suchregeln und Produktangebote kontinuierlich zu verfeinern und zu verbessern

Um korrekte Daten in Ihrem [!DNL Live Search]-Bericht zu erhalten, müssen Sie sicherstellen, dass das Eventing korrekt implementiert ist. Für Händler in Luma ist das Eventing vorkonfiguriert verfügbar. Bei Headless- oder benutzerdefinierten Implementierungen müssen Sie [Ereignis implementieren](https://developer.adobe.com/commerce/services/shared-services/storefront-events/) basierend auf Ihren spezifischen Anforderungen.
