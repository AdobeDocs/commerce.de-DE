---
title: Einrichten der Live-Suche
description: Der  [!DNL Live Search]  wird zum Konfigurieren, Verwalten und Überwachen der Suchleistung verwendet.
exl-id: 07c32b26-3fa4-4fae-afba-8a10866857c3
source-git-commit: c6725fc524e9d239ccc0f16701e92ad5d2fc7729
workflow-type: tm+mt
source-wordcount: '2117'
ht-degree: 0%

---

# Einrichten der Live-Suche

Im Arbeitsbereich können Sie die Leistung von [!DNL Live Search] konfigurieren, verwalten und überwachen. Das Menü oben bietet Zugriff auf die Werkzeuge in jedem Funktionsbereich. Die verfügbaren Funktionen spiegeln die aktuelle Menüauswahl wider.

![Workspace](assets/workspace.png)

## Datenerfassung

Um sicherzustellen, dass jeder Funktionsbereich im Arbeitsbereich die richtigen Daten enthält, müssen Sie die Datenerfassung basierend auf der ausgewählten Storefront-Implementierung konfigurieren:

1. Luma - Die Datenerfassung ist vorkonfiguriert verfügbar.
1. Headless - Die Datenerfassung muss je nach Storefront-Implementierung manuell konfiguriert werden.

Wenn Sie eine Headless-Storefront verwenden, finden Sie in der folgenden Dokumentation weitere Informationen zu den erforderlichen Ereignissen, die Sie hinzufügen müssen:

- [Erforderliche Ereignisse](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search) für das Dashboard der Live-Suche.
- [Storefront Events Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/), der als Voraussetzung hinzugefügt werden muss.
- [Beispiele](https://github.com/adobe/commerce-events/tree/main/examples) der Ereignisstruktur.

### Healthcare-Kunden

Wenn Sie Kundschaft im Gesundheitswesen sind und die [Data Services HIPAA-Erweiterung](../data-connection/hipaa-readiness.md#installation) installiert haben, die Teil der [Data Connection](../data-connection/overview.md)-Erweiterung ist, werden von [!DNL Live Search] verwendete Storefront-Ereignisdaten nicht mehr erfasst. Dies liegt daran, dass Storefront-Ereignisdaten Client-seitig generiert werden. Um weiterhin Storefront-Ereignisdaten zu erfassen und zu senden, aktivieren Sie die Ereigniserfassung für [!DNL Live Search] erneut. Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/config/general/general#data-services)Allgemeine Konfiguration“.

## Festlegen des Umfangs

Anfangs ist [Umfang](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=de#scope-settings) aller [!DNL Live Search] auf `Default Store View` festgelegt. Wenn Ihre [!DNL Commerce] mehrere Store-Ansichten enthält, legen Sie **Umfang** auf die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=de) fest, für die Ihre Facetteneinstellungen gelten.

## Menüoptionen

| Option | Beschreibung |
|--- |--- |
| [Leistung](performance.md) | Das Dashboard ermöglicht insight die Suche nach Produkten. |
| [facettiert](facets.md) | Leistungsstarke Filterung, die mehrere Dimensionen von Attributwerten verwendet, um Suchkriterien zu verfeinern. |
| [Synonyme](synonyms.md) | Erweitern Sie die Reichweite der Suche, um Wörter einzuschließen, die Kunden möglicherweise verwenden, um Produkte zu finden, die sich von denen in Ihrem Katalog unterscheiden. |
| [Merchandising suchen](rules.md) | Gestalten Sie das Sucherlebnis mit logischen Regeln, die den Trigger geplanter Aktionen festlegen. Produkte optimieren, vergraben, anheften oder ausblenden, um Suchergebnisse zu kalibrieren und so Ihre Geschäftsziele zu unterstützen. |
| [Kategorie Merchandising](category-merch.md) | Wenden Sie Regeln und intelligentes Merchandising auf Kategorieebene an. |
| [GraphQL](graphql.md) | Entwickler, die beim Administrator Ihres Stores angemeldet sind, können Abfragen mit tatsächlichen Katalogdaten erstellen und testen. Weitere Informationen finden Sie unter [Übersicht über GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) in der [!DNL Live Search] Entwicklerdokumentation. |
| [Einstellungen](settings.md) | Ermitteln Sie, wie die Facettenwerte des Preises nach Preisbereich in der Storefront gruppiert werden, und legen Sie die Indizierungssprache fest. |

## Festlegen von Attributen als durchsuchbar

Um zielgerichtete Ergebnisse zu erzielen, überprüfen Sie den Satz [&#x200B; (durchsuchbaren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html?lang=de) (`searchable=true`) Produktattribute. Um Relevanz zu gewährleisten, sollten Attribute nur durchsuchbar sein, wenn sie Inhalte mit einer klaren und knappen Bedeutung enthalten. Vermeiden Sie die Verwendung von Attributen, die weniger präzisen, langen Text enthalten, z. B. `description`. Dies kann, obwohl standardmäßig die Suche aktiviert ist, die Genauigkeit der Suchergebnisse verringern. Wenn eine Person beispielsweise nach „kurzen Hosen“ sucht und es Hemden mit einer Beschreibung gibt, die den Begriff „kurze Ärmel“ enthält, werden die Hemden in die Suchergebnisse aufgenommen.

Führen Sie die folgenden Schritte aus, damit Attribute durchsuchbar sein können:

1. Gehen Sie in der Admin zu **Stores** > *Attribut* > **Produkt**.
1. Wählen Sie das Attribut aus, das durchsuchbar sein soll, z. B. `color`.
1. Wählen Sie **Storefront-Eigenschaften** aus und setzen **In der Suche verwenden** auf `yes`.

[!DNL Live Search] berücksichtigt auch die [Gewichtung](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html?lang=de#weighted-search) eines Produktattributs, wie in Adobe Commerce festgelegt. Attribute mit einer höheren Gewichtung werden in den Suchergebnissen höher angezeigt.

Die folgenden Attribute sind immer durchsuchbar:

- `sku`
- `name`
- `categories`

### Attributverhalten in komplexen Produkten

Bei komplexen Produkttypen (konfigurierbare, gebündelte und gruppierte Produkte) indiziert [!DNL Live Search] Attributwerte von übergeordneten und untergeordneten Produkten, sodass ein übergeordnetes Produkt mit mehreren Werten für dasselbe Attribut verknüpft werden kann. Dies ermöglicht eine variantenbasierte Filterung. Beispielsweise wird beim Filtern nach „blau“ ein konfigurierbares Hemd angezeigt, wenn eine Variante blau ist, auch wenn das übergeordnete Produkt keinen Farbsatz hat.

Dies funktioniert gut für Attribute wie Farbe und Größe, kann aber zu unerwarteten Ergebnissen für Attribute wie `new_arrival`, `product_ranking`, `promotion_label` oder benutzerdefinierte Preisattribute führen. Wenn beispielsweise ein konfigurierbares Produkt (SKU-001) `new_arrival = true` hat, aber seine untergeordnete Variante (SKU-001-01) `new_arrival = false` hat, wird die übergeordnete Produkt-SKU-001 mit beiden Werten (`true` und `false`) indiziert, sodass sie in den Suchergebnissen für jede Bedingung angezeigt wird.

### Mehrschichtige Suche und Erweiterung von Suchtypen

Die mehrschichtige Suche oder Suche innerhalb einer Suche ist ein leistungsstarkes, attributbasiertes Filtersystem, das die herkömmliche Suchfunktion um zusätzliche Suchparameter erweitert. Diese zusätzlichen Suchparameter ermöglichen eine präzisere und flexiblere Produktsuche.

>[!NOTE]
>
>Die mehrschichtige Suche ist in Live Search 4.6.0 verfügbar.

Mit der mehrschichtigen Suche können Sie:

- Ermöglichen Sie es Käufern, innerhalb der Suchergebnisse zu suchen.
- Verwenden Sie `startsWith` und `contains` Suchindizierung in der zweiten Ebene der mehrschichtigen Suche, um die Ergebnisse weiter zu verfeinern.

Die erweiterten Suchfunktionen werden über den `filter`-Parameter in der [`productSearch`-Abfrage mithilfe &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) Operatoren implementiert:

- **Mehrschichtige Suche** - Suche in einem anderen Suchkontext - Mit dieser Funktion können Sie bis zu zwei Suchebenen für Ihre Suchanfragen durchführen. Beispiel:

   - **Layer 1 Suche** - Suche nach „motor“ auf `product_attribute_1`.
   - **Layer 2-Suche** - Suche nach „Teilenummer 123“ auf `product_attribute_2`. In diesem Beispiel wird in den Ergebnissen nach „Motor“ nach „Teilenummer 123“ gesucht.

  Die mehrschichtige Suche ist sowohl für die `startsWith` als auch für die `contains` Suchindizierung in der zweiten Ebene der mehrschichtigen Suche verfügbar, wie unten beschrieben:

- **startsWith search indexation** - Suche mit `startsWith`. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach Produkten, bei denen der Attributwert mit einer angegebenen Zeichenfolge beginnt.
   - Konfigurieren der Suche „endet mit“, damit Käufer nach Produkten suchen können, bei denen der Attributwert mit einer bestimmten Zeichenfolge endet. Um eine Suche „endet mit“ zu aktivieren, muss das Produktattribut in umgekehrter Reihenfolge aufgenommen werden und der API-Aufruf sollte auch eine umgekehrte Zeichenfolge sein. Wenn Sie beispielsweise nach einem Produktnamen suchen möchten, der mit „pants“ endet, müssen Sie dies als „stnap“ senden.

- **enthält Suchindizierung** - Suchattribut mit enthält indizierung. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach einer Abfrage innerhalb einer größeren Zeichenfolge. Beispiel: Ein Käufer sucht in der Zeichenfolge „HAPE-123“ nach der Produktnummer „PE-123“.

      - Hinweis: Dieser Suchtyp unterscheidet sich von dem vorhandenen Suchbegriff[&#x200B; der eine &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#phrase) Suche durchführt. Wenn Ihr Produktattributwert beispielsweise „Outdoor Pants“ ist, gibt eine Suchphrase eine Antwort für „out pan“ zurück, aber keine Antwort für „or ants“. Eine Suche enthält jedoch eine Antwort für „oder Ameisen“.

Diese neuen Bedingungen verbessern den Filtermechanismus für Suchanfragen, um Suchergebnisse zu verfeinern. Diese neuen Bedingungen wirken sich nicht auf die Hauptsuchabfrage aus.

#### Implementierung

1. Legen Sie in der Admin [ein Produktattribut fest](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/product-attributes-add#step-5-describe-the-storefront-properties) um durchsuchbar zu sein.

   Siehe die Liste der durchsuchbaren [Attribute](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/attributes-input-types).

1. Geben Sie die Suchfunktion für dieses Attribut an, z. B **„Enthält** (Standard) oder **Beginnt mit**. Sie können maximal sechs Attribute angeben, die für &quot;**&quot; aktiviert** sollen, und sechs Attribute, die für „Beginnt **&quot;** werden sollen. Darüber hinaus ist für die **Enthält**-Indizierung die Zeichenfolgenlänge auf 50 Zeichen oder weniger begrenzt.

   ![Suchfunktion angeben](./assets/search-filters-admin.png)

1. In der [Entwicklerdokumentation](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-using-search-capability) finden Sie Beispiele dazu, wie Sie Ihre [!DNL Live Search]-API-Aufrufe mithilfe der neuen `contains` und `startsWith` Suchfunktionen aktualisieren können.

   Sie können diese neuen Bedingungen auf Ihrer Suchergebnisseite implementieren. Sie können beispielsweise einen neuen Abschnitt auf der Seite hinzufügen, in dem der Erstkäufer seine Suchergebnisse weiter verfeinern kann. Sie können Käufern die Auswahl bestimmter Produktattribute ermöglichen, z. B. „Hersteller“, „Teilenummer“ und „Beschreibung“. Von dort aus suchen sie mithilfe der `contains` oder `startsWith` Bedingungen innerhalb dieser Attribute.

### Verwendung der mehrschichtigen Suche anstelle von Facetten

Die mehrschichtige Suche und Facetten dienen verschiedenen Zwecken der Produktsuche. Die Auswahl zwischen ihnen hängt von Ihrem spezifischen Anwendungsfall ab:

**Verwenden Sie die mehrschichtige Suche, wenn:**

- Sie müssen anhand mehrerer Kriterien in den Suchergebnissen suchen.
- Arbeiten mit Teilenummern, SKUs oder technischen Spezifikationen, bei denen Benutzende nur teilweise Informationen kennen.
- Käufer müssen die Ergebnisse Schritt für Schritt anhand verschachtelter Kriterien eingrenzen.
- Sie möchten die Anzahl der API-Aufrufe reduzieren, indem Sie mehrere Suchkriterien in einer einzigen Abfrage kombinieren.
- Sie müssen geschäftsspezifische Suchmuster implementieren, die über die standardmäßige Facettennavigation hinausgehen.

**Verwenden von Facetten bei:**

- Bereitstellung typischer Filter für Kategorien, Preise, Marken und Attribute
- Intuitive Filteroptionen, die Benutzerinnen und Benutzer leicht verstehen und auswählen können
- Verfügbare Optionen basierend auf aktuellen Suchergebnissen anzeigen
- Anzeigen von Filterzählungen und -bereichen, die Benutzern das Verständnis der verfügbaren Optionen erleichtern
- Arbeiten mit allgemeinen Produktmerkmalen wie Farbe, Größe, Material usw.

**Best Practice:** Verwenden Sie die mehrschichtige Suche für komplexe, technische Suchen, bei denen Benutzende bestimmte Kriterien haben, und verwenden Sie Facetten für die standardmäßige E-Commerce-Filterung, bei der Benutzende Optionen visuell erkunden und eingrenzen möchten.

## Facetten und Synonyme

Facetten und Synonyme sind eine weitere Möglichkeit, das Sucherlebnis für Ihre Kunden zu verbessern.

[Facetten](facets.md) sind Produktattribute, die in definiert sind, [!DNL Live Search] filterbar zu sein. Sie können jedes filterbare Attribut als Facette in [!DNL Live Search] festlegen, aber es gibt [Beschränkungen](boundaries-limits.md) nach wie vielen Facetten Sie gleichzeitig suchen können.

>[!NOTE]
>
>Ein Produktattribut kann nur gefiltert werden, wenn die Konfiguration des Produktattributs die erforderlichen Eigenschaften aufweist: *In Suche verwenden = Ja*, *In Suchergebnissen verwenden: Mehrschichtige Navigation = Ja* und *In mehrschichtiger Navigation verwenden = Filterbar (mit Ergebnissen)*. Wenn diese Eigenschaften fehlen oder nicht korrekt festgelegt sind, ist das Attribut in der Facettenkonfiguration nicht sichtbar. Konfigurationsanweisungen finden Sie unter [Facette hinzufügen](facets-add.md#add-a-facet).

[Synonyme](synonyms.md) sind Begriffe, die Sie definieren können, um Benutzende zum richtigen Produkt zu führen. Benutzer, die nach Hosen suchen, geben möglicherweise „Hosen“ oder „Hosen“ ein. Sie können Synonyme so einstellen, dass diese Suchbegriffe die Benutzer zu den „Hosen“-Ergebnissen führen.

## Commerce-Konfigurationseinstellungen

Im folgenden Abschnitt werden die unterstützten und nicht unterstützten Commerce-Konfigurationseinstellungen für [!DNL Live Search] beschrieben.

### Unterstützte Konfigurationswerte

>[!IMPORTANT]
>
>Es wird dringend empfohlen, die Widgets zur Produktauflistung zu verwenden, die in Live Search 4.0.0 standardmäßig aktiviert sind. Die Widgets sollen die Adapterimplementierung in zukünftigen Versionen vollständig ersetzen. Weitere [&#x200B; finden Sie unter &#x200B;](install.md#enable-product-listing-widgets) für die Produktliste aktivieren .

| Commerce-Konfigurationseinstellung | Beschreibung | Unterstützt von Popover | Unterstützt durch Adapter |
|---|---|---|---|
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Alle Produkte pro Seite zulassen | Ist hierfür `Yes` festgelegt, wird die Option `ALL` in das Steuerelement „Pro Seite anzeigen“ einbezogen. | Ja. Max. 500 Produkte | Ja. Max. 500 Produkte |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Minimale Abfragelänge | Die bei einer Katalogsuche zulässige Mindestanzahl von Zeichen. | Ja | Ja |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Produkte pro Seite für zulässige Rasterwerte | Bestimmt die Anzahl der in der Rasteransicht angezeigten Produkte. | Ja | Ja |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Produkte pro Seite im Raster Standardwert | Bestimmt die Anzahl der Produkte, die standardmäßig in der Rasteransicht pro Seite angezeigt werden. | Ja. Max. 500 Produkte | Ja. Max. 500 Produkte |
| Stores > Konfiguration > Katalog > Inventar > Nicht vorrätige Produkte anzeigen | Zeigt nicht vorrätige Produkte an. | Ja | Ja |
| Stores > Konfiguration > Währung > Standardanzeigewährung | Die primäre Währung zur Anzeige von Preisen. | Ja | Ja |
| Filialen > Konfiguration > Allgemein > Währungseinstellungen > Währungsoptionen > Basiswährung | Die primäre Währung, die für alle Online-Zahlungsvorgänge verwendet wird. | Ja | Ja |

Die Preise auf der Widget-Produktlistenseite und im Pop-up werden mithilfe der konfigurierten Währungskurse in die standardmäßige Anzeigewährung umgerechnet.

### Nicht unterstützte Konfigurationswerte

| Commerce-Konfigurationseinstellung | Beschreibung | Notizen |
|---|---|---|
| Stores > Konfiguration > Katalog > Storefront > Listenmodus | Bestimmt das Format der Suchergebnisliste. | Wird korrekt dargestellt, bei einigen Seiteninteraktionen werden jedoch keine Ereignisse gesendet |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Maximale Abfragelänge | Die maximale Anzahl von Zeichen, die bei einer Katalogsuche zulässig ist. | Nicht implementiert; Search Services akzeptiert bis zu 255 Zeichen |
| Konfiguration > Verkauf > Steuer > Preisanzeigeeinstellungen > Produktpreise im Katalog anzeigen | Bestimmt, ob im Katalog veröffentlichte Produktpreise Steuern enthalten oder ausschließen oder zwei Versionen des Preises anzeigen, eine mit und die andere ohne Steuer |  |
| Stores > Konfiguration > Katalog > Storefront > Produktliste Sortieren nach | Bestimmt die Sortierreihenfolge der Suchergebnisliste. | Gilt nicht für das [!DNL Live Search] [Produktlistenseite-Widget](plp-styling.md) |

## Standard-Attributwerte

Die folgenden Produktattribute verfügen über [Storefront-Eigenschaften](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html?lang=de), die von [!DNL Live Search] verwendet und standardmäßig aktiviert werden.

| Eigenschaft | Storefront-Eigenschaft | Attribut |
|---|---|---|
| sortierbar | Wird zum Sortieren in der Produktliste verwendet | `price` |
| durchsuchbar | In Suche verwenden | `price` <br />`sku`<br />`name` |
| filterableInSearch | Verwendung in der mehrschichtigen Navigation - Filterbar (mit Ergebnissen) | `price`<br />`visibility`<br />`category_name` |

## Standardmäßige Nicht-Systemattribut-Eigenschaften

Die folgende Tabelle zeigt die standardmäßigen suchbaren und filterbaren Eigenschaften von Nicht-Systemattributen, einschließlich derjenigen, die für die Luma-Beispieldaten spezifisch sind. Wenn Sie die *In der Suche verwenden* auf `Yes` setzen, kann das Attribut sowohl in [!DNL Live Search] als auch in nativer Adobe Commerce durchsucht werden.

| Attributcode | durchsuchbar | Verwendung in der mehrschichtigen Navigation |
|--- |--- |--- |
| Aktivität | Ja | Filterbar (mit Ergebnissen) |
| attributes_brand | Ja | Nein |
| Marke | Ja | Nein |
| Klima | Ja | Filterbar (mit Ergebnissen) |
| Kragen | Ja | Filterbar (mit Ergebnissen) |
| Farbe | Ja | Filterbar (mit Ergebnissen) |
| Kosten | Ja | Nein |
| eco_collection | Ja | Filterbar (mit Ergebnissen) |
| Geschlecht | Ja | Filterbar (mit Ergebnissen) |
| Hersteller | Ja | Filterbar (mit Ergebnissen) |
| Material | Ja | Filterbar (mit Ergebnissen) |
| Zweck | Ja | Filterbar (mit Ergebnissen) |
| strap_bags | Ja | Filterbar (mit Ergebnissen) |
| style_general | Ja | Filterbar (mit Ergebnissen) |

## Standardattribut-Eigenschaften

Die folgende Tabelle zeigt die standardmäßigen durchsuchbaren und filterbaren Eigenschaften von Systemattributen.

| Attributcode | durchsuchbar | Verwendung in der mehrschichtigen Navigation |
|--- |--- |--- |
| allow_open_amount | Ja | Filterbar (mit Ergebnissen) |
| Beschreibung | Ja | Nein |
| name | Ja | Nein |
| Preis | Ja | Filterbar (mit Ergebnissen) |
| short_description | Ja | Nein |
| SKU | Ja | Nein |
| Status | Ja | Nein |
| TAX_CLASS_ID | Ja | Nein |
| url_key | Ja | Nein |
| Gewichtung | Ja | Nein |
