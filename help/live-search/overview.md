---
title: Was ist [!DNL Live Search]?
description: '[!DNL Live Search] von Adobe Commerce bietet ein schnelles, relevantes und intuitives Sucherlebnis.'
recommendations: noCatalog
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 0%

---

# Was ist [!DNL Live Search]?

[!DNL Live Search] ist eine Funktion, die die standardmäßigen Suchfunktionen in Adobe Commerce ersetzt. Die [!DNL Live Search] Funktion wird mit Composer installiert und verbindet Ihren [!DNL Commerce] mit dem [Commerce Services Connector](../landing/saas.md). Wenn es konfiguriert ist, wird das standardmäßige Suchtextfeld durch das [!DNL Live Search] Textfeld ersetzt. [!DNL Live Search] installiert auch das Widget Produktlistenseite (PLP) , das beim Durchsuchen von Suchergebnissen robuste Filterfunktionen bietet.

Mit [!DNL Live Search] können Sie:

- Erstellen Sie aussagekräftige Sucherlebnisse, die Käufern und Käufern helfen, mit möglichst wenig Aufwand das zu finden, was sie möchten.
- Nutzen Sie die KI-gestützte dynamische Facettierung und die Neureihung von Suchergebnissen als Reaktion auf das Verhalten von Kundinnen und Kunden während der Sitzung.
- Verwenden Sie einen einfachen SaaS-basierten Service, der einfache Updates bietet und in Ihrer Lizenz enthalten ist, um die Gesamtbetriebskosten zu senken.
- Technische Neuerungen durch die Aktivierung der GraphQL-API, Headless-Flexibilität, API-Sandbox-Umgebungen und ultraschnelle SaaS.

>[!IMPORTANT]
>
>Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Überprüfen Sie vor der Implementierung die Informationen [Grenzen und ](boundaries-limits.md)), um sicherzustellen, dass [!DNL Live Search] zu Ihren Geschäftsanforderungen passt.

## Architektur

Der Adobe Commerce-Teil der Architektur umfasst das Hosten der Suche *Admin*, das Synchronisieren von Katalogdaten und das Ausführen des Abfrage-Service. Nach der Installation und Konfiguration von [!DNL Live Search] beginnt Adobe Commerce mit der Freigabe von Such- und Katalogdaten für SaaS-Services. Jetzt können Admin-Benutzer Such-(Facetten[&#128279;](facets.md), [Synonyme](synonyms.md) und Merchandising[Regeln einrichten, anpassen und ](category-merch.md).

![Live Search-Datenfluss](assets/ls-cs-data-flow.png)

## kurzer Überblick

Mit dem Fokus auf Geschwindigkeit, Relevanz und Benutzerfreundlichkeit ist [!DNL Live Search] ein Wendepunkt für Käufer und Händler gleichermaßen. Sehen Sie sich das folgende Video an und machen Sie dann einen kurzen Überblick über [!DNL Live Search] in der Storefront.

>[!VIDEO](https://video.tv.adobe.com/v/3452578?learn=on&captions=ger)

Ein ausführlicheres Video zur Verwendung und Konfiguration der Live-Suche finden Sie unter [Vollständige Demonstration zu [!DNL Live Search]](https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration).

### Während der Eingabe suchen

[!DNL Live Search] antwortet mit vorgeschlagenen Produkten und einer Miniaturansicht der wichtigsten Suchergebnisse in einem [Pop-up](storefront-popover.md) wenn Käufer Abfragen in das Feld [Suche](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/catalog/search/search) eingeben. Die [ „Produktdetails](https://experienceleague.adobe.com/de/docs/commerce-admin/start/storefront/storefront) wird angezeigt, wenn Käufer auf ein empfohlenes oder vorgestelltes Produkt klicken. Ein _Alle anzeigen_ in der Fußzeile des Popups zeigt die Suchergebnisseite an.

[!DNL Live Search] gibt Suchergebnisse für eine Abfrage mit zwei oder mehr Zeichen zurück. Bei einer Teilübereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in der Abfrage kann nicht konfiguriert werden. Das Popover enthält die `name`, `sku` und `category_ids`.

![Beispiel-Storefront - Suche während der Eingabe](assets/storefront-search-as-you-type.png)

### Alle Suchergebnisse anzeigen

Um alle Produkte aufzulisten, die von der Abfrage „Suche während der Eingabe“ zurückgegeben werden, klicken Sie _der Fußzeile des Popups auf_ Alle anzeigen“.

![Beispiel-Storefront - Preisfacetten](assets/storefront-view-all-search-results.png)

### Gefilterte Suche mit Facetten

Die gefilterte Suche verwendet mehrere Dimensionen von Attributwerten [Facetten](facets.md) als Suchkriterien. Die Auswahl der Filter wird vom Händler definiert und ändert sich entsprechend den zurückgegebenen Produkten. Die am häufigsten verwendeten Facetten werden an den Anfang der Liste angeheftet.

Verwenden Sie Facetten als URL-Parameter`http://yourwebsite.com?color=red` und filtern Sie Ergebnisse der Live-Suche basierend auf diesen Attributwerten.

### Synonyme

[Synonyme](synonyms.md) Erweitern Sie die Reichweite und schärfen Sie den Fokus von Abfragen, indem Sie Wörter einschließen, die Käuferinnen und Käufer möglicherweise verwenden, die sich von denen im Katalog unterscheiden. Sie können das Synonym-Wörterbuch optimieren, um Käufern auf dem Laufenden zu halten und auf dem Weg zum Kauf zu bleiben.

### Merchandising-Regeln

Merchandising [Regeln](rules.md) gestalten das Einkaufserlebnis mit If-Then-Anweisungen, die Logik und Ereignisse zur Suche hinzufügen. Sie können Produkte für eine Promotion, eine Saison oder einen anderen Zeitraum einfach erhöhen oder vergraben.

### Unterstützung für Suchbegriffe

[!DNL Live Search] unterstützt Commerce [Suchbegriff-Umleitungen](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/catalog/search/search-terms). Beispielsweise können Benutzer nach einem Begriff wie „Versandkosten“ suchen und direkt zur Seite „Versandkosten“ geleitet werden.

## Live Search-Komponenten

- [!DNL Live Search] [Popover-](storefront-popover.md)) ist das Feld, das unter dem Suchfeld geöffnet wird, das die Suchergebnisse enthält.
- [Produktlistenseite-Widget](plp-styling.md) (PLP) bietet eine durchsuchbare Produktlistenseite mit Facetten und Unterstützung für Synonyme. Das Widget wird in Live Search 4.0.0+ installiert und aktiviert und ersetzt den Suchadapter.
- (**Veraltet**) Der Suchadapter war der Vorläufer des PLP-Widgets und wurde mit Live Search &lt; 4.0.0 installiert. Wenn Sie eine Version der Live Search vor 4.0.0 verwenden, empfiehlt Commerce ein Upgrade, um die Vorteile der PLP-Widget-Funktionen und zukünftige Verbesserungen zu erhalten. Ab nun wird der Suchadapter nur noch aktualisiert, um Sicherheitsprobleme zu beheben.

## [!DNL Live Search] Workspace

Der [!DNL Live Search] [Arbeitsbereich](workspace.md) ist der Bereich im Admin-Bereich, in dem Sie [!DNL Live Search] Funktionen wie Synonyme, Facetten und Kategorie-Merchandising konfigurieren.

## -Events

[!DNL Live Search] verwendet [Ereignisse](events.md) zum Berechnen von [Intelligent Merchandising](category-merch.md) und [Performance](performance.md)-Dashboards. Eventing wird mit Standardimplementierungen bereitgestellt. Eventing für Headless-Storefronts sollte manuell aktiviert werden.

## Richtlinie zur Aufbewahrung von Katalogdaten

Wenn Sie an 90 aufeinander folgenden Tagen keine Suchanfrage für die Katalogdaten in Ihrer Testumgebung senden, werden die Katalogdaten in den Ruhezustand versetzt und es werden keine Daten für eine Suchanfrage zurückgegeben. Katalogdaten in Ihrer Produktionsumgebung sind von dieser Richtlinie nicht betroffen.

Um die Katalogdaten in Ihrer Testumgebung erneut zu aktivieren, [ Sie „eine Support-Anfrage ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#experience-league-start-page)&quot; mit dem Titel &quot;[!DNL Live Search] erneut aktivieren“ und fügen Sie die Umgebungs-IDs hinzu. Die Katalogdaten in Ihrer Testumgebung sollten innerhalb weniger Stunden wiederhergestellt werden.
