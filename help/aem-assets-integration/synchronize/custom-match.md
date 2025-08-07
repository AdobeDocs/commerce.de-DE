---
title: Benutzerdefinierter automatischer Abgleich
description: Erfahren Sie, wie die benutzerdefinierte automatische Zuordnung besonders für Händler mit komplexer Abgleichlogik oder für Händler nützlich ist, die auf einem Drittanbietersystem basieren, das keine Metadaten in AEM Assets einfügen kann.
feature: CMS, Media, Integration
exl-id: e7d5fec0-7ec3-45d1-8be3-1beede86c87d
source-git-commit: ff6affa5bcc4111e14054f3f6b3ce970619ca295
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 1%

---

# Benutzerdefinierter automatischer Abgleich

Wenn die standardmäßige automatische Abgleichstrategie (**OOTB Automatic Matching**) nicht an Ihren spezifischen Geschäftsanforderungen ausgerichtet ist, wählen Sie die Option Benutzerdefinierte Abgleichung aus. Diese Option unterstützt die Verwendung von [Adobe Developer App Builder](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) zum Entwickeln einer benutzerdefinierten Matcher-Anwendung, die komplexe Matching-Logik verarbeitet, oder von Assets, die von einem Drittanbietersystem stammen, das keine Metadaten in AEM Assets einfügen kann.

## Konfigurieren von benutzerdefiniertem automatischem Abgleich

1. Navigieren Sie vom Commerce-Administrator aus zu **[!UICONTROL Store]** > Konfiguration > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

1. Wählen Sie **[!UICONTROL Custom Matcher]** als Übereinstimmungsregel aus.

1. Wenn Sie diese Zuordnungsregel auswählen, zeigt Admin zusätzliche Felder zum Konfigurieren der **Endpunkte** und der erforderlichen **Authentifizierungsparameter** für die benutzerdefinierte Zuordnungslogik an.

## Benutzerdefinierte Matcher-API-Endpunkte

Wenn Sie eine benutzerdefinierte Matcher-Anwendung mit [App Builder](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder){target=_blank} erstellen, muss die Anwendung die folgenden Endpunkte bereitstellen:

* Endpunkt **App Builder-Asset zur Produkt** URL
* Endpunkt **App Builder-Produkt zu Asset** URL

### Endpunkt von App Builder Asset-zu-Produkt-URL

Dieser Endpunkt ruft die Liste der mit einem bestimmten Asset verknüpften SKUs ab:

#### Beispielverwendung

```bash
const { Core } = require('@adobe/aio-sdk')

async function main(params) {

    // Build your own matching logic here to return the products that map to the assetId
    // var productMatches = [];
    // params.assetId
    // params.eventData.assetMetadata['commerce:isCommerce']
    // params.eventData.assetMetadata['commerce:skus'][i]
    // params.eventData.assetMetadata['commerce:roles']
    // params.eventData.assetMetadata['commerce:positions'][i]
    // ...
    // End of your matching logic

    return {
        statusCode: 500,
        body: {
            asset_id: params.assetId,
            product_matches: [
                {
                    product_sku: "<YOUR-SKU-HERE>",
                    asset_roles: ["thumbnail", "image", "swatch_image", "small_image"],
                    asset_position: 1
                }
            ]
        }
    };
}

exports.main = main;
```

**Anfrage**

```bash
POST https://your-app-builder-url/api/v1/web/app-builder-external-rule/asset-to-product
```

| Parameter | Datentyp | Beschreibung |
| --- | --- | --- |
| `assetId` | Zeichenfolge | Stellt die aktualisierte Asset-ID dar |
| `eventData` | Zeichenfolge | Gibt die mit dem `assetId` verknüpfte Daten-Payload aus. |

**Antwort**

```bash
{
  "asset_id": "{ASSET_ID}",
  "product_matches": [
    {
      "product_sku": "{PRODUCT_SKU_1}",
      "asset_roles": ["thumbnail","image"]
    },
    {
      "product_sku": "{PRODUCT_SKU_2}",
      "asset_roles": ["thumbnail"]
    }
  ]
}
```

### Endpunkt von App Builder-Produkt-zu-Asset-URL

Dieser Endpunkt ruft die Liste der Assets ab, die mit einer bestimmten SKU verknüpft sind:

#### Beispielverwendung

```bash
const { Core } = require('@adobe/aio-sdk')

async function main(params) {
    // return asset matches for a product
    // Build your own matching logic here to return the assets that map to the productSku
    // var assetMatches = [];
    // params.productSku
    // ...
    // End of your matching logic

    return {
        statusCode: 500,
        body: {
            product_sku: params.productSku,
            asset_matches: [
                {
                    asset_id: "<YOUR-ASSET-ID-HERE>", // urn:aaid:aem:1aa1d5i2-17h8-40a7-a228-e3ur588deee1
                    asset_roles: ["thumbnail", "image", "swatch_image", "small_image"],
                    asset_format: "image", // can be "image" or "video"
                    asset_position: 1
                }
            ]
        }
    };
}

exports.main = main;
```

**Anfrage**

```bash
GET https://your-app-builder-url/api/v1/web/app-builder-external-rule/product-to-asset
```

| Parameter | Datentyp | Beschreibung |
| --- | --- | --- |
| `productSKU` | Zeichenfolge | Stellt die aktualisierte Produkt-SKU dar. |
| `asset_matches` | Zeichenfolge | Gibt alle mit einem bestimmten `productSku` verknüpften Assets aus |

Der `asset_matches`-Parameter enthält die folgenden Attribute:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `asset_id` | Zeichenfolge | Stellt die aktualisierte Asset-ID dar. |
| `asset_roles` | Zeichenfolge | Gibt alle verfügbaren Asset-Rollen zurück. Verwendet unterstützte [Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/digital-assets/product-image#image-roles)Asset-Rollen wie `thumbnail`, `image`, `small_image` und `swatch_image`. |
| `asset_format` | Zeichenfolge | Stellt die verfügbaren Formate für das Asset bereit. Mögliche Werte sind `image` und `video`. |
| `asset_position` | Zeichenfolge | Zeigt die Position des Assets an. |

**Antwort**

```bash
{
  "product_sku": "{PRODUCT_SKU}",
  "asset_matches": [
    {
      "asset_id": "{ASSET_ID_1}",
      "asset_roles": ["thumbnail","image"]
    },
    {
      "asset_id": "{ASSET_ID_2}",
      "asset_roles": ["thumbnail"]
    }
  ]
}
```
