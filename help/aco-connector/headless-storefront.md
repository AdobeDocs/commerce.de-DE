---
title: '[!DNL Adobe Commerce Optimizer Connector] Headless-Storefront-Integration'
description: Erfahren Sie, wie Sie Headless-Storefronts mit der  [!DNL Adobe Commerce Optimizer Connector] GraphQL-API, Preisbuch-IDs und der Bundle-Add-to-Cart-Kodierung integrieren.
feature: Storefront, Integration, GraphQL
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T16:27:30.102Z'
TQID: 'https://experienceleague.adobe.com/Orif1rROglTQ-3ZkRj5LMF90Y-AdpfTnOgPmJXQjYgc'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: c32adafa-ed01-4b31-997e-2413013911b0
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: d378ca77-2da1-4f39-ad92-1917fe974a38
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 6d4493db5e0714577a8800007cc6d2c552578fa4
workflow-type: tm+mt
source-wordcount: 237
ht-degree: 0%

---

# Headless-Storefront-Integration

Das `CommerceAdapter` Modul erweitert [!DNL Adobe Commerce], um die Lücke zwischen einer Headless-Storefront und [!DNL Adobe Commerce Optimizer] zu schließen. Sie bietet eine GraphQL-Abfrage zur Auflösung des Preisbuchkontexts des Kunden und erzwingt die von der [!DNL Adobe Commerce Optimizer] GraphQL-API erwartete Produktcodierung.

Allgemeine Anweisungen zum Einrichten von Storefronts finden Sie unter [Konfigurieren von Merchandising- und Storefronts](./overview.md#merchandising-storefronts) in der [!DNL Adobe Commerce Optimizer Connector].

## GraphQL: Abfrage `commerceOptimizer` {#graphql-commerceoptimizer-query}

Headless-Storefronts rufen die `commerceOptimizer` GraphQL-Abfrage auf, um die `priceBookId` für die aktuelle Kundensitzung abzurufen. Übergeben Sie diesen Wert beim Abrufen der Preise ](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/using-the-api){target="_blank"} die [[!DNL Adobe Commerce Optimizer] GraphQL-API.

```graphql
{
  commerceOptimizer {
    priceBookId
  }
}
```

Beispielantwort:

```json
{
  "data": {
    "commerceOptimizer": {
      "priceBookId": "base::a94a8fe5ccb19ba61c4c0873d391e987982fbbd3"
    }
  }
}
```

Wie `priceBookId` behoben wird:

| Sitzungsstatus | `priceBookId` |
|-----------------------|---------------------------------------------------------------------|
| Gast (nicht angemeldet) | `websiteCode::sha1(0)`, wobei `0` die ID der Gastkundengruppe ist |
| Angemeldeter Kunde | `websiteCode::sha1(customerGroupId)` |

Der Header der `Store`-Anfrage bestimmt den Umfang der Website und damit die `websiteCode`. Die `sha1(customerGroupId)` entspricht der Preisbuch-ID-Formel, die bei der Datensynchronisation verwendet wird. Siehe [Preisbücher](reference/field-mapping.md#price-books).

## Bundle-Produkte: Format „In den Warenkorb legen“ {#bundle-products-add-to-cart-format}

Erlauben Sie Käufern, aus einer Headless-Storefront Bundle-Produkte zum Warenkorb hinzuzufügen, wobei nur die `SKU` und `qty` für jede ausgewählte Bundle-Option verfügbar sind.

Jeder ausgewählte oder eingegebene Optionswert muss im folgenden Format base64-kodiert sein:

```text
base64("bundle_item/" + JSON.stringify({"sku": "<child_sku>", "qty": "<qty>"}))
```

Dieselbe untergeordnete SKU wird in allen Optionen möglicherweise nur einmal angezeigt.

Beispiel ([!DNL JavaScript])

```javascript
const encodedOption = btoa(
  'bundle_item/' + JSON.stringify({ sku: 'child-product-sku', qty: '1' })
);
```
