---
title: GraphQL
description: Mit dem [!DNL Live Search] GraphQL-Arbeitsbereich können Sie Abfragen mit Ihren Live-Daten erstellen.
exl-id: d32edf42-1fb0-40f9-89e5-798b39521b77
TQID: https://experienceleague.adobe.com/y-aM85yTrJA6JNXlJeacXEOkr8l-Bwij9gdVCgNGEqY
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
source-git-commit: 438d00c69044818382ffd22ffb68a4061c59ddbd
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%
---
# GraphQL

Der Arbeitsbereich *GraphQL* ermöglicht es Admins, GraphQL-Abfragen mit ihren eigenen Daten zu erstellen und zu testen.

Dieser Arbeitsbereich unterstützt die [`productSearch`](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) und [`attributeMetadata`](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/attribute-metadata/) Abfragen.

![GraphQL Workspace](assets/graphql.png)

```graphql
query productSearch {
  productSearch(phrase: "") {
    total_count
    items {
      productView {
        sku
      }
    }
    facets {
      title
    }
  }
}
```

Variablen:

```json
{
  "Magento-Environment-Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "Magento-Website-Code": "base",
  "Magento-Store-Code": "base",
  "Magento-Store-View-Code": "default",
  "X-Api-Key": "search_gql"
}
```
