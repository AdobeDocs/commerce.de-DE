---
title: Facetten
description: '[!DNL Live Search] Facetten verwenden mehrere Dimensionen von Attributwerten als Suchkriterien.'
exl-id: d036265e-1868-461d-ab4c-7f469b1c6f5b
source-git-commit: 31223f4196187e4960c5bec0e90aa55cc4e0ac9a
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# Facetten

Facettierung ist eine Methode zur Hochleistungsfilterung, bei der mehrere Dimensionen von Attributwerten als Suchkriterien verwendet werden. Die Facettensuche ist ähnlich, aber erheblich „intelligenter“ als die standardmäßige [Layered Navigation](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html?lang=de). Die Liste der verfügbaren Filter wird durch die [filterbaren Attribute](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html?lang=de#filterable-attributes) der in den Suchergebnissen zurückgegebenen Produkte bestimmt.

[!DNL Live Search] verwendet die `productSearch`-Abfrage, die Facetten- und andere Daten zurückgibt, die spezifisch für [!DNL Live Search] sind. Code-Beispiele finden Sie [`productSearch` der Entwicklerdokumentation unter ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) Abfrage .

![Gefilterte Suchergebnisse](assets/storefront-search-results-run.png)

Innerhalb einer Facette können Käufer mehrere Optionen auswählen, z. B. „Einfach“ und „eng“ unter „Stil“ und die Suchergebnisse werden aktualisiert, um nur diese Stile anzuzeigen. Wenn ein Käufer über Facetten hinweg Optionen auswählt, z. B. „Standard“ unter „Stil“ und „Indoor“ unter „Klima“, werden die Suchergebnisse aktualisiert, um diesen ausgewählten Stil und dieses ausgewählte Klima anzuzeigen.

Jede definierte Facette kann als URL-Parameter verwendet werden. Die Ergebnisse werden anhand der Parameterwerte `http://yourstore.com?brand=acme&color=red` gefiltert.

## Anforderungen an Facetten

Die Anforderungen an Kategorie- und Produktattribute für die Facettierung ähneln den filterbaren Attributen, die für die mehrschichtige Navigation verwendet werden. Für jede Storefront-Eigenschaft eines Attributs muss der Wert „In Suchergebnissen in mehrschichtiger Navigation verwenden“ auf „Ja“ festgelegt sein. Sie können die Attributkonfiguration über das Menü [!DNL Stores] > [!DNL Attribute] in Admin überprüfen und aktualisieren.

>[!NOTE]
>
>Wenn Sie eine Produktkategorie als Facette definieren, zeigt die Facette die Kategorie und die Unterkategorie an.
>
>![Kategoriefacetten](assets/facet-category.png)

Weitere [ zu den Facettenanforderungen in ](./boundaries-limits.md#facets) finden [!DNL Live Search] unter „Grenzen und Beschränkungen“.

Wenn Sie mit einer großen Anzahl von Attributen zu kämpfen haben, sollten Sie Attribute zu einem einzigen „Meta-Attribut“ kombinieren. Beispielsweise haben Schuhe in der Regel numerische Größen, während Hemden in der Regel die Größe „S/M/L/XL“ haben. Diese beiden Größentypen können zu einem durchsuchbaren Attribut kombiniert werden.

| Einstellung | Beschreibung |
|--- |--- |
| [Einstellungen für Kategorieanzeige](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html?lang=de) | Anker - `Yes` |
| [Attributeigenschaften](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html?lang=de) | [Katalogeingabetyp](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html?lang=de) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (nur Widget), `Text swatch` (nur Widget) |
| Eigenschaften der Storefront-Attribute | Verwendung in Suchergebnissen - mehrschichtige Navigation - `Yes` |

## Facettenaggregation

Die Facettenaggregation wird wie folgt durchgeführt: Wenn die Storefront drei Facetten hat (Kategorien, Farbe und Preis) und die Käufer alle drei filtern (Farbe = Blau, Preis ist von $10.00-50.00, Kategorien = `promotions`).

* `categories` Aggregation - Aggregiert `categories` und wendet dann die `color`- und `price` an, jedoch nicht den `categories`.
* `color` Aggregation - Aggregiert `color` und wendet dann die `price`- und `categories` an, jedoch nicht den `color`.
* `price` Aggregation - Aggregiert `price` und wendet dann die `color`- und `categories` an, jedoch nicht den `price`.

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
