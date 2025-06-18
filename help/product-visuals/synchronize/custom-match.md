---
title: Benutzerdefinierter automatischer Abgleich
description: Erfahren Sie, wie der benutzerdefinierte automatische Abgleich besonders für Händler mit komplexer Abgleichlogik oder für Händler nützlich ist, die auf einem Drittanbietersystem basieren, das keine Metadaten zu visuellen Produkten in AEM Assets einfügen kann.
feature: CMS, Media, Integration
source-git-commit: 3ecc429003490235211a812af064d1b10d053e38
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# Benutzerdefinierter automatischer Abgleich

Wenn die standardmäßige automatische Abgleichstrategie (**OOTB Automatic Matching**) nicht an Ihren spezifischen Geschäftsanforderungen ausgerichtet ist, wählen Sie die Option Benutzerdefinierte Abgleichung aus. Diese Option unterstützt die Verwendung von [Adobe Developer App Builder](https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) zum Entwickeln einer benutzerdefinierten Matcher-Anwendung, die komplexe Matching-Logiken verarbeitet, oder von Assets aus einem Drittanbietersystem, das keine Produktvisualmetadaten in AEM Assets einfügen kann.

## Konfigurieren von benutzerdefiniertem automatischem Abgleich

1. Navigieren Sie vom Commerce-Administrator aus zu **[!UICONTROL Store]** > Konfiguration > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

1. Wählen Sie **[!UICONTROL Custom Matcher]** als Übereinstimmungsregel aus.

1. Wenn Sie diese Zuordnungsregel auswählen, zeigt Admin zusätzliche Felder zum Konfigurieren der **Endpunkte** und der erforderlichen **Authentifizierungsparameter** für die benutzerdefinierte Zuordnungslogik an.

## Benutzerdefinierte Matcher-API-Endpunkte

Wenn Sie eine benutzerdefinierte Matcher-Anwendung mit [App Builder](https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder){target=_blank} erstellen, muss die Anwendung die folgenden Endpunkte bereitstellen:

* Endpunkt **App Builder-Asset zur Produkt** URL
* Endpunkt **App Builder-Produkt zu Asset** URL

### Endpunkt von App Builder Asset-zu-Produkt-URL

Dieser Endpunkt ruft die Liste der mit einem bestimmten Asset verknüpften SKUs ab:

#### Beispielverwendung

```bash
const { Core } = require('@adobe/aio-sdk')
 
async function main (params) {
    // return the products that map to the assetId
    return {
        statusCode: 200,
        body: {
          asset_id: "urn:aaid:aem:1aa1d4a0-18b8-40a7-a228-e0ab588deee1",
          product_matches: [
            {
              product_sku: "SKU1",
              asset_roles: ["thumbnail"],
              asset_position: [1]
            }
          ]
        }
   }
}
 
exports.main = main
```

**Anfrage**

```bash
GET https://your-app-builder-url/api/v1/web/app-builder-external-rule/asset-to-product
```

| Parameter | Datentyp | Beschreibung |
| --- | --- | --- |
| `assetId` | Zeichenfolge | Stellt die aktualisierte Asset-ID dar |

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
 
async function main (params) {
    // return asset matches for a product
    return {
        statusCode: 200,
        body: {
          product_sku: params.productSku, //SKU-1
          asset_matches: [
            {
              asset_id: "urn:aaid:aem:1aa1d4a0-18b8-40a7-a228-e0ab588deee1",
              asset_roles: ["thumbnail","image"]
            }
          ]
        }
      }
}
 
exports.main = main
```

**Anfrage**

```bash
GET https://your-app-builder-url/api/v1/web/app-builder-external-rule/product-to-asset
```

| Parameter | Datentyp | Beschreibung |
| --- | --- | --- |
| `productSKU` | Zeichenfolge | Stellt die aktualisierte Produkt-SKU dar |

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

>[!TIP]
>
> Verwenden Sie im `asset_roles` unterstützte [Commerce-Asset](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/products/digital-assets/product-image#image-roles)Rollen wie `thumbnail`, `image`, `small_image` und `swatch_image`.
