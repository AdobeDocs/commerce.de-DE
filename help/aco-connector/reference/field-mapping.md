---
title: Feldzuordnung für  [!DNL Adobe Commerce Optimizer Connector] -Feeds
description: Erfahren Sie mehr über  [!DNL Adobe Commerce Optimizer Connector]  Zuordnung von  [!DNL Adobe Commerce] -Katalogdaten zu Aufnahme [!DNL Adobe Commerce Optimizer] API-Formaten für alle Feeds.
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T15:49:03.934Z'
TQID: 'https://experienceleague.adobe.com/SOWOnguudhqzX-r66nGUqc-WKet5qq6GRV11ADx0Me4'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
  - id: c32adafa-ed01-4b31-997e-2413013911b0
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: b23e006f-0a29-4f1d-8fd0-77aa56f3d12b
source-git-commit: 1f901b4a72c10dc4e710742b98c03e88cbc8739f
workflow-type: tm+mt
source-wordcount: 465
ht-degree: 0%

---


# Feldzuordnung für Connector-Feeds

Auf dieser Seite wird dokumentiert, wie die [!DNL Adobe Commerce Optimizer Connector] [!DNL Adobe Commerce] Katalogfelder in das für die [!DNL Commerce Optimizer]-[!DNL Catalog Data Ingestion API] erforderliche Format umwandelt. Unter [Connector-Referenz](connector-reference.md#supported-feeds) finden Sie die Liste der unterstützten Feeds und ihrer API-Endpunkte.

## PRODUCT

| [!DNL Adobe Commerce] | API-Feld [!DNL Commerce Optimizer] | Notizen |
| ----------------------------------------------- | -------------- | ------- |
| `sku` | `sku` | |
| `storeViewCode` | `source/locale` | |
| `name` | `name` | |
| `urlKey` | `slug` | |
| `productId` | `externalIds[0].id` | `origin` auf `"AdobeCommerce"` festgelegt |
| `status` | `status` | Hochgestellt; für zusammengesetzte Produkte ohne zugewiesene untergeordnete Elemente auf `DISABLED` gesetzt |
| `description` | `description` | |
| `shortDescription` | `shortDescription` | |
| `visibility` | `visibleIn` | Kommagetrennte Werte, aufgeteilt und zugeordnet: `Catalog`→`CATALOG`, `Search`→`SEARCH`; nicht zugeordnete Werte gelöscht |
| `metaTitle` | `metaTags/title` | |
| `metaDescription` | `metaTags/description` | |
| `metaKeyword` | `metaTags/keywords` | Durch Zeilenumbruch getrennte Zeichenfolge in Array aufgeteilt |
| `inStock`, `lowStock`, `weight`, `weightUnit` | `attributes[].code = "aco_ac_attributes"` | JSON-kodierte `{inStock, lowStock, weight, weightType}`; immer als erster Attributeintrag vorhanden |
| `attributes[]` | `attributes[]` | Jeder Eintrag, der `{code, values[], variantReferenceId}` zugeordnet ist; `inStock`, `lowStock`, `weight`, `weightType` sind ausgeschlossen (sie gehen in `aco_ac_attributes`) |
| `images[]` | `images[]` | `url`, `label`; Standardrollen zugeordnet: `image`→`BASE`, `small_image`→`SMALL`, `thumbnail`→`THUMBNAIL`, `swatch_image`→`SWATCH`; Nicht-Standardrollen gehen an `customRoles[]` |
| `categoryData[].categoryPath` | `routes[].path` | |
| `categoryData[].productPosition` | `routes[].position` | |
| `links[].type` + `links[].sku` | `links[]` | `type` in Großbuchstaben; Einträge ohne `sku` werden gelöscht |
| `parents[].productType` + `parents[].sku` | `links[]` | Zugeordneter Typ: `configurable`→`VARIANT_OF`, `bundle`/`bundle_fixed`→`IN_BUNDLE` |
| `configurable options` | `configurations[]` | `id`→`attributeCode`, `label`; Optionstyp `SWATCH`, wenn `swatchType` festgelegt ist, andernfalls `CONFIGURABLE`; Standardvariante von `isDefault`; Werte umfassen `variantReferenceId`, `label`, `colorHex`, `imageUrl` |
| `bundle options` | `bundles[]` | `label`→`group`; `required`; `renderType` `checkbox`/`multi`→`multiSelect: true`; Standard-SKUs von `isDefault`; Elemente umfassen `sku`, `qty`, `userDefinedQty` (`qtyMutability`) |

## Metadaten der Produktattribute

| [!DNL Adobe Commerce] | API-Feld [!DNL Commerce Optimizer] | Notizen |
| --------------- | -------------- | ------- |
| `attributeCode` | `code` | |
| `storeViewCode` | `source/locale` | |
| `label` | `label` | |
| `dataType` + `frontendInput` | `dataType` | Siehe Konversionstabelle unten |
| `visible` | `visibleIn: "PRODUCT_DETAIL"` | Beim `true` zum Array hinzugefügt |
| `visibleInSearch` | `visibleIn: "SEARCH_RESULTS"` | Beim `true` zum Array hinzugefügt |
| `visibleInListing` | `visibleIn: "PRODUCT_LISTING"` | Beim `true` zum Array hinzugefügt |
| `visibleInCompareList` | `visibleIn: "PRODUCT_COMPARE"` | Beim `true` zum Array hinzugefügt |
| `filterable` | `filterable` | |
| `sortable` | `sortable` | |
| `searchable` | `searchable` | |
| `searchWeight` | `searchWeight` | |
| `searchTypes` | `searchTypes` | |

**Datentypkonvertierung:**

| [!DNL Adobe Commerce] `dataType` | [!DNL Adobe Commerce] `frontendInput` | [!DNL Commerce Optimizer] API-`dataType` |
| -------------------- | -------------------------- | ------------------- |
| `int` | `boolean` | `BOOLEAN` |
| `int` | `text` oder `select` | `TEXT` |
| `int` | Beliebige andere | `INTEGER` |
| `decimal` | - | `DECIMAL` |
| `text`, `varchar`, `static`, `datetime` | - | `TEXT` |
| `OBJECT` | - | `OBJECT` |
| Beliebige andere | - | `TEXT` |

## Preisbücher

Im Gegensatz zu den anderen Connector-Feeds wird der `priceBooks`-Feed nicht von einem [!DNL SaaS Data Export] Indexer in [!DNL Adobe Commerce] erfasst. Der Connector generiert diesen Feed aus der Website- und Kundengruppenkonfiguration im Admin-Bereich.

Pro Website wird ein **Grundpreisbuch** erstellt, plus ein **Kinderpreisbuch** pro Website-Kunden-Gruppenpaar.

**Preisbuch-ID-Formel:**

- **Basis** (reguläre Preise): `priceBookId = websiteCode`
- **Child** (Kundengruppe oder freigegebener Katalog): `priceBookId = websiteCode::sha1(customerGroupId)`, wobei `sha1(customerGroupId)` der SHA-1-Hex-Auszug der Ganzzahl-ID der Kundengruppe ist

Der Preis-Feed verwendet dieselbe Formel, wenn er festlegt, zu welchem Preisbuch ein Preiseintrag gehört. Informationen dazu, wie Storefronts die `priceBookId` für eine Kundensitzung auflösen, finden Sie unter [Headless-Storefront-Integration](../headless-storefront.md#graphql-commerceoptimizer-query).

| Erzeugtes Feld | API-Feld [!DNL Commerce Optimizer] | Notizen |
| ---------------- | -------------- | ------- |
| `websiteCode`, `customerGroupId` | `priceBookId` | |
| Website-Name | `name` | Basispreisbuch: Website-Name. Untergeordnet: `"Group Name (Website Name)"` |
| `websiteCode` | `parentId` | Nur bei untergeordneten Preisbüchern vorhanden; verweist auf das Grundpreisbuch |
| Website-Basiswährung | `currency` | Nur bei Grundpreisbüchern vorhanden; von Kindern übernommen |

## Preise

| [!DNL Adobe Commerce] | API-Feld [!DNL Commerce Optimizer] | Notizen |
| --------------- | -------------- | ------------------------------------------------------------------------------- |
| `sku` | `sku` | |
| `websiteCode`, `customerGroupId` | `priceBookId` | |
| `regular` | `regular` | |
| `discounts[]` | `discounts[]` | Beispiel für Rabatte: Sonderpreis, Katalogregel-Preis, Preis für freigegebenen Katalog |
| `tierPrices[]` | `tierPrices[]` | |

## Kategorien

Elemente mit einem leeren `urlPath` (logische Stammkategorien) werden übersprungen und nie gesendet.

| [!DNL Adobe Commerce] | API-Feld [!DNL Commerce Optimizer] | Notizen |
| --------------- | -------------- | ------- |
| `storeViewCode` | `source/locale` | |
| `name` | `name` | |
| `urlPath` | `slug` | |
| `description` | `description` | |
| `metaTitle` | `metaTags/title` | |
| `metaDescription` | `metaTags/description` | |
| `metaKeywords` | `metaTags/keywords` | Durch Zeilenumbruch getrennte Zeichenfolge in Array aufgeteilt |
| `image` | `images[].url` | Array mit einzelnen Elementen; `roles: ["BASE"]` |
| `isActive` + `includeInMenu` | `families` | `["top_menu"]` wenn beide `true`, `[]` andernfalls |

>[!MORELIKETHIS]
>
> - [Aufnahme von Produkt- und Preisdaten mit der Datenaufnahme-API](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/){target="_blank"} — Erfahren Sie mehr über das Katalogdatenmodell für Metadaten, Produkte, Kategorien, Preislisten und Preise
> - [Catalog data Ingestion REST API Reference](https://developer.adobe.com/commerce/services/reference/rest/){target="_blank"} — Prüfen Sie Anfrage- und Antwortschemata für jeden Feed-Endpunkt
> - [Funktionsweise von  [!DNL Commerce Optimizer Connector]  mit  [!DNL Adobe Commerce]](../overview.md#how-the-connector-works-with-adobe-commerce) - Erfahren Sie, wie Store-Ansichten, Websites und Kundengruppen Katalogquellen und Preisbüchern zugeordnet sind
> - [Preisbücher in [!DNL Commerce Optimizer]](/help/optimizer/setup/pricebooks.md) - Vom Connector-Export erstellte Preisbücher verwalten
> - [Headless-Storefront-Integration](../headless-storefront.md#graphql-commerceoptimizer-query) - `priceBookId` für Kundensitzungen auflösen
