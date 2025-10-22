---
title: '[!DNL Catalog Service and API Mesh]'
description: '[!DNL API Mesh] für Adobe Commerce bietet eine Möglichkeit, mehrere Datenquellen über einen gemeinsamen GraphQL-Endpunkt zu integrieren.'
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
exl-id: 903f4f96-6dba-4c45-8106-76d9845544ec
source-git-commit: 5dd290a4e10bdbd1f6c96b67ab6c9ba1598705dc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

[API Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht Entwicklern die Integration von privaten oder Drittanbieter-APIs und anderen Benutzeroberflächen mit Adobe-Produkten unter Verwendung von Adobe I/O Runtime.

![Katalog-Architekturdiagramm](assets/catalog-service-architecture-mesh.png)

Um API Mesh mit dem Katalog-Service zu verwenden, müssen Sie API Mesh mit Ihrer Instanz verbinden und dann die API Mesh-Quelle [CommerceCatalogServiceGraph](https://github.com/adobe/api-mesh-sources/blob/main/connectors/) hinzufügen, die die Konfiguration für die Verbindung mit dem Katalog-Service bereitstellt.

## Verbinden und Konfigurieren von API-Mesh.

1. Verbinden Sie API Mesh mit Ihrer Adobe Commerce-Instanz, indem Sie die Anweisungen [Erstellen eines &#x200B;](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/)) im _API Mesh-Entwicklerhandbuch_ befolgen.

   Wenn Sie API Mesh zum ersten Mal verwenden, schließen Sie den [Erste Schritte-Prozess](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic/) ab, bevor Sie das Netz erstellen.

1. Erstellen Sie eine JSON-Datei, z. B. `variables.json`, die den Catalog Service-API-Schlüssel für Ihr Projekt enthält, indem Sie das folgende Format verwenden.

   ```json
   {
       "CATALOG_SERVICE_API_KEY":"your_api_key"
   }
   ```

1. Fügen Sie die `CommerceCatalogServiceGraph` mithilfe der [Adobe I/O Extensible CLI](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic/#install-the-aio-cli) zu Ihrem Netz hinzu.

   ```bash
   aio api-mesh source install "CommerceCatalogServiceGraph" -f variables.json
   ```

   Die Option `-f variables.json` liefert den Schlüsselwert der Catalog Service-API, der zum Aktualisieren der Konfiguration erforderlich ist.

Nach Ausführung dieses Befehls sollte der Katalog-Service über das API-Mesh ausgeführt werden. Verwenden Sie den Befehl `aio api-mesh get` , um die Konfiguration Ihres aktualisierten Netzes anzuzeigen.

## API-Mesh-Beispiele

Mit der API Mesh können Benutzer externe Datenquellen nutzen, um Ihre Adobe Commerce-Instanz zu verbessern. Sie können damit auch vorhandene Commerce-Daten konfigurieren, um neue Funktionen zu aktivieren.

### Stufenpreise aktivieren

In diesem Beispiel wird die API Mesh verwendet, um Preisstufen in Adobe Commerce zu aktivieren.
Ersetzen Sie die Werte `name`, `endpoint` und `x-api-key`.

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

Fragen Sie nach der Konfiguration das Netz nach gestaffelten Preisen ab:

```graphql
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```

### Entitäts-ID abrufen

Dieses Mesh fügt die `entityId` an die ProductView-Schnittstelle an. Ersetzen Sie die Werte `name`, `endpoint` und `x-api-key`.

```json
{
    "meshConfig": {
      "sources": [
        {
          "name": "<Commerce Instance Name>",
          "handler": {
            "graphql": {
              "endpoint": "<Adobe Commerce GraphQL endpoint>"
            }
          },
          "transforms": [
              {
                  "prefix": {
                      "includeRootOperations": true,
                        "value": "Core_"
                  }
              }
          ]
        },
        {
          "name": "CommerceCatalogServiceGraph",
          "handler": {
            "graphql": {
              "endpoint": "https://catalog-service.adobe.io/graphql",
              "operationHeaders": {
                "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
                "Magento-Website-Code": "{context.headers['magento-website-code']}",
                "Magento-Store-Code": "{context.headers['magento-store-code']}",
                "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>",
                "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
              },
              "schemaHeaders": {
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>"
              }
            }
          }
        }
      ],
      "additionalTypeDefs": "extend interface ProductView {\n  entityId: String\n}\n extend type SimpleProductView {\n  entityId: String\n}\n extend type ComplexProductView {\n  entityId: String\n}\n",
      "additionalResolvers": [
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n    items {\n  sku\n uid\n  }\n    }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          },
          {
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n items {\n  sku\n uid\n }}",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          }
      ]
    }
  }
```

`entityId` können jetzt abgefragt werden:

```graphql
query {
  products(skus: ["MH07"]){
    sku
    name
    id
    entityId
  }
}
```
