---
title: Facetten
description: '[!DNL Live Search] Facetten verwenden mehrere Dimensionen von Attributwerten als Suchkriterien.'
exl-id: d036265e-1868-461d-ab4c-7f469b1c6f5b
TQID: https://experienceleague.adobe.com/bTE-Ow8xEDfK-saxGxotnvkgHZI4QThno1dCqRbjvCc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 452
ht-degree: 0%

---

# Facetten

Facettierung ist eine Methode zur Hochleistungsfilterung, bei der mehrere Dimensionen von Attributwerten als Suchkriterien verwendet werden. Die Facettensuche ist ähnlich, aber erheblich „intelligenter“ als die standardmäßige [Layered Navigation](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html?lang=de). Die Liste der verfügbaren Filter wird durch die [filterbaren Attribute](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html?lang=de#filterable-attributes) der in den Suchergebnissen zurückgegebenen Produkte bestimmt.

[!DNL Live Search] verwendet die `productSearch`-Abfrage, die Facetten- und andere Daten zurückgibt, die spezifisch für [!DNL Live Search] sind. Code-Beispiele finden Sie [&#128279;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) der Entwicklerdokumentation unter `productSearch` Abfrage .

![Gefilterte Suchergebnisse](assets/storefront-search-results-run.png)

Innerhalb einer Facette können Käufer mehrere Optionen auswählen, z. B. „Einfach“ und „eng“ unter „Stil“ und die Suchergebnisse werden aktualisiert, um nur diese Stile anzuzeigen. Wenn ein Käufer über Facetten hinweg Optionen auswählt, z. B. „Standard“ unter „Stil“ und „Indoor“ unter „Klima“, werden die Suchergebnisse aktualisiert, um diesen ausgewählten Stil und dieses ausgewählte Klima anzuzeigen.

Jede definierte Facette kann als URL-Parameter verwendet werden. Die Ergebnisse werden anhand der Parameterwerte `http://yourstore.com?brand=acme&color=red` gefiltert.

## Anforderungen an Facetten

Die Anforderungen an Kategorie- und Produktattribute für die Facettierung ähneln den filterbaren Attributen, die für die mehrschichtige Navigation verwendet werden. Für jede Storefront-Eigenschaft eines Attributs muss der Wert „In Suchergebnissen in mehrschichtiger Navigation verwenden“ auf „Ja“ festgelegt sein. Sie können die Attributkonfiguration über das Menü [!DNL Stores] > [!DNL Attribute] in Admin überprüfen und aktualisieren.

>[!NOTE]
>
>Wenn Sie eine Produktkategorie als Facette definieren, zeigt die Facette die `url_path` der Kategorie und der Unterkategorie an.
>
>![Kategoriefacetten](assets/facet-category.png)

Weitere [&#x200B; zu den Facettenanforderungen in [!DNL Live Search] finden &#x200B;](./boundaries-limits.md#facets) unter „Grenzen und Beschränkungen“.

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
