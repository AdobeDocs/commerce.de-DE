---
title: Benutzerdefinierter automatischer Abgleich
description: Erfahren Sie, wie die benutzerdefinierte automatische Zuordnung besonders für Händler mit komplexer Abgleichlogik oder für Händler nützlich ist, die auf einem Drittanbietersystem basieren, das keine Metadaten in AEM Assets einfügen kann.
feature: CMS, Media, Integration
exl-id: e7d5fec0-7ec3-45d1-8be3-1beede86c87d
source-git-commit: 6e8d266aeaec4d47b82b0779dfc3786ccaa7d83a
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Benutzerdefinierter automatischer Abgleich

Wenn die standardmäßige automatische Abgleichstrategie (**OOTB Automatic Matching**) nicht an Ihren spezifischen Geschäftsanforderungen ausgerichtet ist, wählen Sie die Option Benutzerdefinierte Abgleichung aus. Diese Option unterstützt die Verwendung von [Adobe Developer App Builder](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) zum Entwickeln einer benutzerdefinierten Matcher-Anwendung, die komplexe Matching-Logik verarbeitet, oder von Assets, die von einem Drittanbietersystem stammen, das keine Metadaten in AEM Assets einfügen kann.

## Konfigurieren von benutzerdefiniertem automatischem Abgleich

1. Navigieren Sie vom Commerce-Administrator aus zu **[!UICONTROL Store]** > Konfiguration > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

1. Wählen Sie **[!UICONTROL Custom Matcher]** als Übereinstimmungsregel aus.

1. Wenn Sie diese Zuordnungsregel auswählen, zeigt Admin zusätzliche Felder zum Konfigurieren der **Endpunkte** und der erforderlichen **Authentifizierungsparameter** für die benutzerdefinierte Zuordnungslogik an.

### workspace.json

Das Feld **[!UICONTROL Adobe I/O Workspace Configuration]** bietet eine optimierte Möglichkeit, Ihren benutzerdefinierten Matcher zu konfigurieren, indem Sie Ihre App Builder `workspace.json`-Konfigurationsdatei importieren.

Sie können die `workspace.json` Datei von der [Adobe Developer Console herunterladen](https://developer.adobe.com/console). Die Datei enthält alle Anmeldeinformationen und Konfigurationsdetails für Ihren App Builder Workspace.

+++Beispiel `workspace.json`

```json
{
  "project": {
    "id": "project_id",
    "name": "project_name",
    "title": "title_name",
    "org": {
      "id": "id",
      "name": "Organization_name",
      "ims_org_id": "ims_id"
    },
    "workspace": {
      "id": "workspace_id",
      "name": "workspace_name_id",
      "title": "workspace_title_id",
      "action_url": "https://action_url.net",
      "app_url": "https://app_url.net",
      "details": {
        "credentials": [
          {
            "id": "credential_id",
            "name": "credential_name_id",
            "integration_type": "oauth_server_to_server",
            "oauth_server_to_server": {
              "client_id": "client_id",
              "client_secrets": ["secret"],
              "technical_account_email": "xx@technical_account_email.com",
              "technical_account_id": "technical_account_id",
              "scopes": [
                "AdobeID",
                "openid",
                "read_organizations",
                "additional_info.projectedProductContext",
                "additional_info.roles",
                "adobeio_api",
                "read_client_secret",
                "manage_client_secrets"
              ]
            }
          }
        ],
        "services": [
          {
            "code": "AdobeIOManagementAPISDK",
            "name": "I/O Management API"
          }
        ],
        "runtime": {
          "namespaces": [
            {
              "name": "namespace_name",
              "auth": "example_auth"
            }
          ]
        },
        "events": {
          "registrations": []
        },
        "mesh": {}
      }
    }
  }
}
```

+++

1. Ziehen Sie Ihre `workspace.json` aus dem App Builder-Projekt in das Feld **[!UICONTROL Adobe I/O Workspace Configuration]** . Alternativ können Sie zum Durchsuchen klicken und die Datei auswählen.

![Workspace-Konfiguration](../assets/workspace-configuration.png){width="600" zoomable="yes"}

1. Das System führt automatisch folgende Schritte durch:

   * Validiert die JSON-Struktur
   * Extrahiert und füllt OAuth-Anmeldeinformationen
   * Ruft verfügbare Laufzeitaktionen für den Arbeitsbereich ab
   * Füllt Dropdown-Optionen für die Felder **[!UICONTROL Product to Asset URL]** und **[!UICONTROL Asset to Product URL]** aus

1. Wählen Sie für jeden Fluss die entsprechenden Laufzeitaktionen aus den Dropdown-Menüs aus.

1. Klicken Sie auf **[!UICONTROL Save Config]**.

## Benutzerdefinierte Matcher-API-Endpunkte

Wenn Sie eine benutzerdefinierte Matcher-Anwendung mit [App Builder](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder){target=_blank} erstellen, muss die Anwendung die folgenden Endpunkte bereitstellen:

* Endpunkt **App Builder-Asset zur Produkt** URL
* Endpunkt **App Builder-Produkt zu Asset** URL

### Endpunkt von App Builder Asset-zu-Produkt-URL

Dieser Endpunkt ruft die Liste der mit einem bestimmten Asset verknüpften SKUs ab:

#### Beispielverwendung

```javascript
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

    // Set skip to true if the mapping hasn't changed
    const skipSync = false;

    return {
        statusCode: 200,
        body: {
            asset_id: params.assetId,
            product_matches: [
                {
                    product_sku: "<YOUR-SKU-HERE>",
                    asset_roles: ["thumbnail", "image", "swatch_image", "small_image"],
                    asset_position: 1
                }
            ],
            skip: skipSync
        }
    };
}

exports.main = main;
```

**Anfrage**

```text
POST https://your-app-builder-url/api/v1/web/app-builder-external-rule/asset-to-product
```

| Parameter | Datentyp | Beschreibung |
| --- | --- | --- |
| `assetId` | Zeichenfolge | Stellt die aktualisierte Asset-ID dar. |
| `eventData` | Zeichenfolge | Gibt die Daten-Payload zurück, die mit der Asset-ID verknüpft ist. |

**Antwort**

```json
{
  "asset_id": "{ASSET_ID}",
  "product_matches": [
    {
      "product_sku": "{PRODUCT_SKU_1}",
      "asset_roles": ["thumbnail", "image"]
    },
    {
      "product_sku": "{PRODUCT_SKU_2}",
      "asset_roles": ["thumbnail"]
    }
  ],
  "skip": false
}
```

| Parameter | Datentyp | Beschreibung |
| --- | --- | --- |
| `asset_id` | Zeichenfolge | Die Asset-ID, die abgeglichen wird. |
| `product_matches` | Array | Liste der mit dem Asset verknüpften Produkte. |
| `skip` | Boolesch | (Optional) Bei der `true` überspringt die Regel-Engine die Synchronisierung für dieses Asset (keine Aktualisierung der Produktzuordnung). Wenn `false` oder ausgelassen, wird die normale Verarbeitung ausgeführt. Siehe [Synchronisierungsverarbeitung überspringen](#skip-sync-processing). |

### Endpunkt von App Builder-Produkt-zu-Asset-URL

Dieser Endpunkt ruft die Liste der Assets ab, die mit einer bestimmten SKU verknüpft sind:

#### Beispielverwendung

```javascript
const { Core } = require('@adobe/aio-sdk')

async function main(params) {
    // return asset matches for a product
    // Build your own matching logic here to return the assets that map to the productSku
    // var assetMatches = [];
    // params.productSku
    // ...
    // End of your matching logic

    // Set skip to true if the mapping hasn't changed
    const skipSync = false;

    return {
        statusCode: 200,
        body: {
            product_sku: params.productSku,
            asset_matches: [
                {
                    asset_id: "<YOUR-ASSET-ID-HERE>", // urn:aaid:aem:1aa1d5i2-17h8-40a7-a228-e3ur588deee1
                    asset_roles: ["thumbnail", "image", "swatch_image", "small_image"],
                    asset_format: "image", // can be "image" or "video"
                    asset_position: 1
                }
            ],
            skip: skipSync
        }
    };
}

exports.main = main;
```

**Anfrage**

```text
POST https://your-app-builder-url/api/v1/web/app-builder-external-rule/product-to-asset
```

| Parameter | Datentyp | Beschreibung |
| --- | --- | --- |
| `productSKU` | Zeichenfolge | Stellt die aktualisierte Produkt-SKU dar. |
| `eventData` | Zeichenfolge | Gibt die Daten-Payload zurück, die mit der Produkt-SKU verknüpft ist. |

**Antwort**

```json
{
  "product_sku": "{PRODUCT_SKU}",
  "asset_matches": [
    {
      "asset_id": "{ASSET_ID_1}",
      "asset_roles": ["thumbnail", "image"],
      "asset_position": 1,
      "asset_format": "image"
    },
    {
      "asset_id": "{ASSET_ID_2}",
      "asset_roles": ["thumbnail"],
      "asset_position": 2,
      "asset_format": "image"
    }
  ],
  "skip": false
}
```

| Parameter | Datentyp | Beschreibung |
| --- | --- | --- |
| `product_sku` | Zeichenfolge | Die abgeglichene Produkt-SKU. |
| `asset_matches` | Array | Liste der mit dem Produkt verknüpften Assets. |
| `skip` | Boolesch | (Optional) Bei der `true` überspringt die Regel-Engine die Synchronisierung für dieses Produkt (keine Aktualisierung der Asset-Zuordnung). Wenn `false` oder ausgelassen, wird die normale Verarbeitung ausgeführt. Siehe [Synchronisierungsverarbeitung überspringen](#skip-sync-processing). |

Der `asset_matches`-Parameter enthält die folgenden Attribute:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `asset_id` | Zeichenfolge | Die Asset-ID. |
| `asset_roles` | Array | Asset-Rollen. Verwendet unterstützte [Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/digital-assets/product-image#image-roles)Asset-Rollen wie `thumbnail`, `image`, `small_image` und `swatch_image`. |
| `asset_format` | Zeichenfolge | Das Asset-Format. Mögliche Werte sind `image` und `video`. |
| `asset_position` | Zahl | Die Position des Assets in der Produktgalerie. |

## Synchronisierungsverarbeitung überspringen

Mit dem `skip` Parameter kann der benutzerdefinierte Matcher die Synchronisierungsverarbeitung für bestimmte Assets oder Produkte umgehen.

Wenn Ihre App Builder-Anwendung in der Antwort `"skip": true` zurückgibt, sendet die Regel-Engine keine Aktualisierungs- oder Entfernungs-API-Anfragen für dieses Asset oder Produkt an Commerce. Diese Optimierung reduziert unnötige API-Aufrufe und verbessert die Leistung.
