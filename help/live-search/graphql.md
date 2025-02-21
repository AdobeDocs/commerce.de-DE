---
title: GraphQL
description: Mit dem  [!DNL Live Search] GraphQL-Arbeitsbereich können Sie Abfragen mit Ihren Live-Daten erstellen.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '39'
ht-degree: 0%

---

# GraphQL

Der Arbeitsbereich *GraphQL* ermöglicht es Admins, GraphQL-Abfragen mit ihren eigenen Daten zu erstellen und zu testen.

Dieser Arbeitsbereich unterstützt die [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) und [`attributeMetadata`](https://developer.adobe.com/commerce/services/graphql/live-search/attribute-metadata/) Abfragen.

![GraphQL Workspace](assets/graphql.png)

```graphql
query productSearch {
  productSearch(phrase: "a306") {
    total_count
    items {
      product {
        sku
		name
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

