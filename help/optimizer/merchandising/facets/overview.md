---
title: Facettenübersicht
description: Erfahren Sie mehr über Facetten in  [!DNL Adobe Commerce Optimizer]  und wie sie die Suchergebnisse verbessern.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 3020386cd051b4453ed6b90d2c694a5bb31dfb24
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Facetten

Facetten ist eine Methode zur Hochleistungsfilterung, bei der mehrere Dimensionen von Attributwerten als Suchkriterien verwendet werden.

![Gefilterte Suchergebnisse](../../assets/storefront-search-results-run.png)

Innerhalb einer Facette können Käufer mehrere Optionen auswählen, z. B. „Einfach“ und „eng“ unter „Stil“ und die Suchergebnisse werden aktualisiert, um nur diese Stile anzuzeigen. Wenn ein Käufer über Facetten hinweg Optionen auswählt, z. B. „Standard“ unter „Stil“ und „Indoor“ unter „Klima“, werden die Suchergebnisse aktualisiert, um diesen ausgewählten Stil und dieses ausgewählte Klima anzuzeigen.

Jede definierte Facette kann als URL-Parameter verwendet werden. Die Ergebnisse werden anhand der Parameterwerte `http://yourstore.com?brand=acme&color=red` gefiltert.

## Facettenaggregation

Die Facettenaggregation wird wie folgt durchgeführt: Wenn die Storefront drei Facetten hat (Kategorien, Farbe und Preis) und die Käufer alle drei filtern (Farbe = Blau, Preis ist von $10.00-50.00, Kategorien = `promotions`).

- `categories` Aggregation - Aggregiert `categories` und wendet dann die `color`- und `price` an, jedoch nicht den `categories`.
- `color` Aggregation - Aggregiert `color` und wendet dann die `price`- und `categories` an, jedoch nicht den `color`.
- `price` Aggregation - Aggregiert `price` und wendet dann die `color`- und `categories` an, jedoch nicht den `price`.

## Standard-Attributwerte

Die folgenden [Produktattribute](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/api-reference/#operation/createProductMetadata) werden von [!DNL Adobe Commerce Optimizer] verwendet und sind standardmäßig aktiviert.

| Eigenschaft | Beschreibung | Attribut |
|---|---|---|
| sortierbar | Wird zum Sortieren in der Produktliste verwendet | `price` |
| durchsuchbar | In Suche verwenden | `price` <br />`sku`<br />`name` |

## Standardmäßige Nicht-Systemattribut-Eigenschaften

In der folgenden Tabelle werden die standardmäßigen durchsuchbaren und filterbaren Eigenschaften von Nicht-Systemattributen angezeigt. Wenn Sie die *In der Suche verwenden* auf `Yes` setzen, kann das Attribut in [!DNL Adobe Commerce Optimizer] durchsucht werden.

| Attributcode | durchsuchbar |
|--- |--- |
| Aktivität | Ja |
| attributes_brand | Ja |
| Marke | Ja |
| Klima | Ja |
| Kragen | Ja |
| Farbe | Ja |
| Kosten | Ja |
| eco_collection |
| Geschlecht | Ja |
| Hersteller | Ja |
| Material | Ja |
| Zweck | Ja |
| strap_bags | Ja |
| style_general | Ja |

## Standardattribut-Eigenschaften

Die folgende Tabelle zeigt die standardmäßigen durchsuchbaren und filterbaren Eigenschaften von Systemattributen.

| Attributcode | durchsuchbar |
|--- |--- |
| allow_open_amount | Ja |
| Beschreibung | Ja |
| name | Ja |
| Preis | Ja |
| short_description | Ja |
| SKU | Ja |
| Status | Ja |
| TAX_CLASS_ID | Ja |
| url_key | Ja |
| Gewichtung | Ja |
