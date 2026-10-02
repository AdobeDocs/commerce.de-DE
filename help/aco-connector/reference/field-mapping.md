---
title: Feldzuordnung für [!DNL Adobe Commerce Optimizer Connector]-Feeds
description: Erfahren Sie mehr über [!DNL Adobe Commerce Optimizer Connector] Feldzuordnung von [!DNL Adobe Commerce] Katalogdaten zu [!DNL Adobe Commerce Optimizer] Aufnahme-API-Formaten für alle Feeds.
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T15:49:03.934Z'
TQID: 'https://experienceleague.adobe.com/SOWOnguudhqzX-r66nGUqc-WKet5qq6GRV11ADx0Me4'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: b23e006f-0a29-4f1d-8fd0-77aa56f3d12b
    internal-label: Data modeling
source-git-commit: 1e34df4f07f9043675104fce55c58e0617463b33
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 2%
---

# Feldzuordnung für Connector-Feeds

Auf dieser Seite wird dokumentiert, wie die [!DNL Adobe Commerce Optimizer Connector] [!DNL Adobe Commerce] Katalogfelder in das für die [!DNL Commerce Optimizer]-[!DNL Catalog Data Ingestion API] erforderliche Format umwandelt. Unter [Connector-Referenz](connector-reference.md#supported-feeds) finden Sie die Liste der unterstützten Feeds und ihrer API-Endpunkte.

## PRODUCT

Der `products`-Feed sendet Daten an den Endpunkt [products](https://developer.adobe.com/commerce/services/reference/rest/#tag/Products){target="_blank"}.

| [!DNL Adobe Commerce] | API-Feld [!DNL Commerce Optimizer] | Zuordnungsdetails |
| ----------------------------------------------- | -------------- | ------- |
| `sku` | `sku` | |
| `storeViewCode` | `source/locale` | |
| `name` | `name` | |
| `urlKey` | `slug` | |
| `productId` | `externalIds[0].id` | Setzt `origin` auf `"AdobeCommerce"` |
| `status` | `status` | Wandelt den Status in Großbuchstaben um. Verwendet `DISABLED`, wenn der Status fehlt oder wenn ein konfigurierbares oder gebündeltes Produkt keine Optionswerte hat. |
| `description` | `description` | Verwendet eine leere Zeichenfolge, wenn die Beschreibung fehlt. |
| `shortDescription` | `shortDescription` | Verwendet eine leere Zeichenfolge, wenn die Kurzbeschreibung fehlt. |
| `visibility` | `visibleIn` | Teilt den kommagetrennten Wert und ordnet `Catalog` `CATALOG` und `Search` zu `SEARCH` zu. Löscht andere Werte. |
| `metaTitle` | `metaTags/title` | |
| `metaDescription` | `metaTags/description` | |
| `metaKeyword` | `metaTags/keywords` | Teilt Keywords mit Zeilenumbruch in ein Array auf und kürzt Leerzeichen. |
| `inStock`, `lowStock`, `weight`, `weightUnit` | `attributes[].code = "aco_ac_attributes"` | Fügt immer einen `aco_ac_attributes` Eintrag als erstes Attribut hinzu. Ihr JSON-Wert enthält `inStock` und `lowStock` als Zeichenfolgen. Sie enthält `weight` und `weightType`, wenn diese Werte verfügbar sind. |
| `attributes[]` | `attributes[]` | Ordnet jeden Eintrag seinem Attributcode, seinen Zeichenfolgenwerten und, sofern verfügbar, seiner übereinstimmenden Variantenreferenz-ID zu. Überspringt `inStock`, `lowStock`, `categories`, `weight` und `weightType`. Die inventarbezogenen Werte sind in `aco_ac_attributes` enthalten. Kategorien werden als Routen exportiert. |
| `images[]` | `images[]` | Überspringt Bilder ohne eine URL.<br>Exportiert `url`, `label` (leer, wenn fehlt) und `sortOrder` (Ganzzahl, Standardwert ist `0`).<br>Sortiert Bilder nach `sortOrder` in aufsteigender Reihenfolge.<br>Ordnet Standardrollen zu: `image` zu `BASE`, `small_image` zu `SMALL`, `thumbnail` zu `THUMBNAIL` und `swatch_image` zu `SWATCH`. Exportiert andere Rollen nach `customRoles[]`. |
| `categoryData[].categoryPath` | `routes[].path` | Einträge mit einem leeren Kategoriepfad werden übersprungen. |
| `categoryData[].productPosition` | `routes[].position` | Verwendet `0`, wenn die Produktposition fehlt. |
| `links[].type` + `links[].sku` | `links[]` | `type` in Großbuchstaben; Einträge ohne `sku` werden gelöscht |
| `parents[].productType` + `parents[].sku` | `links[]` | Ordnet `configurable` `VARIANT_OF` und `bundle` oder `bundle_fixed` `IN_BUNDLE` zu. Wandelt andere Produktarten in Großbuchstaben um. Überspringt Eltern ohne SKU. |
| `configurable options` | `configurations[]` | Exportiert Optionen mit einer ID und mindestens einem Wert.<br>Ordnet `id` `attributeCode` zu. Legt `type` auf `SWATCH` fest, wenn `swatchType` vorhanden ist, und auf andernfalls `CONFIGURABLE`.<br>Verwendet die ID des Standardwerts als `defaultVariantReferenceId`.<br>Ordnet jeden Wert `variantReferenceId`, `label`, `colorHex` und `imageUrl` zu. |
| `bundle options` | `bundles[]` | Exportiert Optionen, die mindestens ein Element enthalten.<br>Verwendet die Optionsbeschriftung als `group` oder `Bundle group`, wenn die Beschriftung leer ist. Kopiert `required` in die Ausgabe.<br>Setzt `multiSelect` auf `true` für `checkbox` und `multi` Render-Typen.<br>Listet Standard-SKUs in `defaultItemSkus` auf. Jedes Element enthält `sku`, `qty` (standardmäßig `0`) und `userDefinedQty` (ab `qtyMutability` standardmäßig `false`). |

## Metadaten der Produktattribute

Der `productAttributes`-Feed sendet Daten an den [Metadaten-Endpunkt](https://developer.adobe.com/commerce/services/reference/rest/#tag/Metadata){target="_blank"}.

| [!DNL Adobe Commerce] | API-Feld [!DNL Commerce Optimizer] | Zuordnungsdetails |
| --------------- | -------------- | ------- |
| `attributeCode` | `code` | |
| `storeViewCode` | `source/locale` | |
| `label` | `label` | |
| `dataType` + `frontendInput` | `dataType` | Siehe Konversionstabelle unten |
| `dataType` und `frontendInput` | `dataType` | Verwendet die unten stehenden Konversionsregeln. |
| `visible`, `visibleInSearch`, `visibleInListing`, `visibleInCompareList` | `visibleIn[]` | Wenn ein Flag `true` wird, fügt den entsprechenden Wert hinzu: <br>`visible` → `PRODUCT_DETAIL`<br>`visibleInSearch` → `SEARCH_RESULTS`<br>`visibleInListing` → `PRODUCT_LISTING`<br>`visibleInCompareList` → `PRODUCT_COMPARE` |
| `filterable` | `filterable` | |
| `sortable` | `sortable` | |
| `searchable` | `searchable` | |
| `searchWeight` | `searchWeight` | |
| `searchTypes` | `searchTypes` | |

### Datentypkonvertierung

Wenn `dataType` `int` wird, prüft der Connector `frontendInput`. Bei anderen Datentypen hat `frontendInput` keine Auswirkungen auf die Konvertierung.

| `dataType` | `frontendInput` | `dataType` |
| ---------------- | --------------------- | ----------------- |
| `int` | `boolean` | `BOOLEAN` |
| `int` | `text` oder `select` | `TEXT` |
| `int` | Alle anderen Werte, einschließlich eines fehlenden Werts | `INTEGER` |
| `decimal` | Nicht verwendet | `DECIMAL` |
| `text`, `varchar`, `static`, `datetime` | Nicht verwendet | `TEXT` |
| `OBJECT` | Nicht verwendet | `OBJECT` |
| Beliebiger anderer Wert | Nicht verwendet | `TEXT` |

>[!NOTE]
>
>Wenn ein Attribut den Datentyp `OBJECT` verwendet, versucht die [Products-API](https://developer.adobe.com/commerce/services/reference/graphql/#products){target="_blank"} seinen gespeicherten Wert als JSON zu analysieren. Wenn das Analysieren erfolgreich ist, gibt die API den Wert als verschachteltes -Objekt zurück. Verwenden Sie `OBJECT` für strukturierte Attributdaten, die nicht als einzelner Wert dargestellt werden können. Anweisungen finden Sie [Produktattribute dynamisch hinzufügen](../../data-export/add-attribute-dynamically.md).

## Preisbücher

Der `priceBooks`-Feed sendet Daten an den [Preisbuchendpunkt](https://developer.adobe.com/commerce/services/reference/rest/#tag/Price-Books){target="_blank"}.

Im Gegensatz zu den anderen Connector-Feeds wird der `priceBooks`-Feed nicht von einem [!DNL SaaS Data Export] Indexer in [!DNL Adobe Commerce] erfasst. Der Connector generiert diesen Feed aus der Website- und Kundengruppenkonfiguration im Admin-Bereich.

Für jede Website erstellt der Connector für jede Kundengruppe ein Basispreisbuch und ein untergeordnetes Preisbuch.

Verwenden Sie diese Formeln für `priceBookId`:

- Grundpreis Bücher für reguläre Preise: `priceBookId = websiteCode`.
- Untergeordnete Preislisten für Kundengruppen: `priceBookId = websiteCode::sha1(customerGroupId)`, wobei `sha1(customerGroupId)` der SHA-1-Hex-Auszug der Ganzzahl-ID der Kundengruppe ist.

Der Preis-Feed verwendet dieselbe Formel, um jeden Preiseintrag einem Preisbuch zuzuordnen. Informationen dazu, wie eine Storefront `priceBookId` für eine Kundensitzung auflöst, finden Sie unter [Headless-Storefront-Integration](../headless-storefront.md#graphql-commerceoptimizer-query).


| Source-Feld oder -Wert | API-Feld [!DNL Commerce Optimizer] | Zuordnungsdetails |
| ---------------- | -------------- | ------- |
| `websiteCode` | `parentId` | Fügt dieses Feld den untergeordneten Preisbüchern hinzu. Sein Wert gibt den Grundpreis an. |
| Website-Name | `name` | Verwendet den Namen der Website für Grundpreisbücher. Verwendet `Customer group name (Website name)` für Kinderpreisbücher. |
| `websiteCode` | `parentId` | Nur bei untergeordneten Preisbüchern vorhanden; verweist auf das Grundpreisbuch |
| Website-Basiswährung | `currency` | Enthält dieses Feld nur für Basispreise. Kinderpreisbücher lassen es aus. |

## Preise

Der `prices`-Feed sendet [!DNL Adobe Commerce] Daten an den [Endpunkt Preise](https://developer.adobe.com/commerce/services/reference/rest/#tag/Prices){target="_blank"}.

| Eingabefeld für den Feed | API-Feld [!DNL Commerce Optimizer] | Zuordnungsdetails |
| --------------- | -------------- | ------------------------------------------------------------------------------- |
| `sku` | `sku` | Übergibt die SKU unverändert an . |
| `websiteCode`, `customerGroupCode` | `priceBookId` | Kombiniert `websiteCode` mit dem SHA-1-Hash der Kundengruppen-ID in `customerGroupCode`. Wenn `customerGroupCode` `0` ist, verwendet `websiteCode` allein. |
| `regular` | `regular` | Gibt den regulären Preis unverändert weiter. |
| `discounts[]` | `discounts[]` | Wenn der Quellwert `null` ist, exportiert ein leeres Array.<br>Für Einträge mit `code` auf `special_price` und einem `percentage` setzt `percentage` auf `100 - percentage`, wenn der Wert zwischen `0` und `100` liegt. Legt fest, dass der Wert `0` oder außerhalb dieses Bereichs liegt.<br>Passt andere Einträge, einschließlich preisbasierter Sonderpreise, unverändert an. |
| `tierPrices[]` | `tierPrices[]` | Verwendet ein leeres Array, wenn der Quellwert fehlt oder `null`. |

## Kategorien

Der `categories`-Feed sendet [!DNL Adobe Commerce] Daten an den [Categories-Endpunkt](https://developer.adobe.com/commerce/services/reference/rest/#tag/Categories){target="_blank"}.

Elemente mit einem leeren `urlPath` (logische Stammkategorien) werden übersprungen und nie gesendet.

| [!DNL Adobe Commerce] | API-Feld [!DNL Commerce Optimizer] | Zuordnungsdetails |
| --------------- | -------------- | ------- |
| `storeViewCode` | `source/locale` | |
| `name` | `name` | |
| `urlPath` | `slug` | |
| `description` | `description` | |
| `position` | `position` | Exportiert die Kategorieposition, sofern vorhanden. Lässt das Feld aus, wenn es fehlt. |
| `metaTitle` | `metaTags/title` | |
| `metaDescription` | `metaTags/description` | |
| `metaKeywords` | `metaTags/keywords` | Durch Zeilenumbruch getrennte Zeichenfolge in Array aufgeteilt |
| `image` | `images[].url` | Array mit einzelnen Elementen; `roles: ["BASE"]` |
| `isActive` + `includeInMenu` | `families` | `["top_menu"]` wenn beide `true`, `[]` andernfalls |

| `metaKeywords` | `metaTags/keywords` | Teilt mit Zeilenumbruch getrennte Schlüsselwörter in ein Array auf und kürzt Leerzeichen. |
| `image` | `images[].url` | Wenn `image` vorhanden ist, exportiert ein Bild mit der Rolle `BASE`. Exportiert ein leeres Array, wenn das Bild leer ist oder fehlt. |
| `isActive` + `includeInMenu` | `families` | Fügt `top_menu` nur hinzu, wenn beide Werte `true` sind. Andernfalls exportiert ein leeres Array. |
| `attributes[]` | `attributes[]` | Exportiert Einträge mit einer nicht leeren `attributeCode` als `{code, values[]}`. Konvertiert Werte in Zeichenfolgen. `attributes` ausgelassen, wenn keine geeigneten Einträge vorhanden sind. |

>[!MORELIKETHIS]
>
> - [Aufnahme von Produkt- und Preisdaten mit der Datenaufnahme-API](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/){target="_blank"} — Erfahren Sie mehr über das Katalogdatenmodell für Metadaten, Produkte, Kategorien, Preislisten und Preise
> - [Catalog data Ingestion REST API Reference](https://developer.adobe.com/commerce/services/reference/rest/){target="_blank"} — Prüfen Sie Anfrage- und Antwortschemata für jeden Feed-Endpunkt
> - [Funktionsweise von  [!DNL Commerce Optimizer Connector]  mit  [!DNL Adobe Commerce]](../overview.md#how-the-connector-works-with-adobe-commerce) - Erfahren Sie, wie Store-Ansichten, Websites und Kundengruppen Katalogquellen und Preisbüchern zugeordnet sind
> - [Preisbücher in [!DNL Commerce Optimizer]](/help/optimizer/setup/pricebooks.md) - Vom Connector-Export erstellte Preisbücher verwalten
> - [Headless-Storefront-Integration](../headless-storefront.md#graphql-commerceoptimizer-query) - `priceBookId` für Kundensitzungen auflösen
