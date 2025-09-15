---
title: Benutzerdefinierte Ereignisse erstellen
description: Erfahren Sie, wie Sie benutzerdefinierte Ereignisse erstellen, um Ihre Adobe Commerce-Daten mit anderen Adobe DX-Produkten zu verbinden.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: db782c0a-8f13-4076-9b17-4c5bf98e9d01
source-git-commit: 4e8cf0ad3f8f94d4f59bc8d78a44f4b3e86cbc3e
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Benutzerdefinierte Ereignisse erstellen

Sie können die [Eventing-Plattform](events.md) erweitern, indem Sie Ihre eigenen Storefront-Ereignisse erstellen, um branchenspezifische Daten zu erfassen. Wenn Sie ein benutzerdefiniertes Ereignis erstellen und konfigurieren, wird es an den [Adobe Commerce Events Collector gesendet](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-collector).

## Verarbeiten benutzerdefinierter Ereignisse

Benutzerdefinierte Ereignisse werden nur für die Adobe Experience Platform unterstützt. Benutzerdefinierte Daten werden nicht an Adobe Commerce-Dashboards und Metrik-Tracker weitergeleitet.

Für jedes `custom`-Ereignis gibt der Collector Folgendes aus:

- Fügt `identityMap` mit `ECID` als primäre Identität hinzu
- Enthält `email` in `identityMap` als sekundäre Identität _wenn_ `personalEmail.address` im Ereignis festgelegt ist
- Schließt das vollständige Ereignis in ein `xdm` ein, bevor es an Edge weitergeleitet wird

Beispiel:

Benutzerspezifisches Ereignis, das über Adobe Commerce Events SDK veröffentlicht wurde:

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

In Experience Platform Edge:

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> Die Verwendung benutzerdefinierter Ereignisse kann sich auf die standardmäßigen Adobe Analytics-Berichte auswirken.

## Überschreibungen von Ereignissen behandeln (benutzerdefinierte Attribute)

Für jedes Ereignis, das mit einem `customContext` festgelegt wird, überschreibt oder erweitert der Collector Felder in der Ereignis-Payload von den Feldern im `custom context`. Der Anwendungsfall für Überschreibungen besteht darin, dass ein Entwickler Kontexte, die von anderen Teilen der Seite in bereits unterstützten Ereignissen festgelegt wurden, wiederverwenden und erweitern möchte.

Ereignisüberschreibungen sind nur bei der Weiterleitung an Experience Platform anwendbar. Sie werden nicht auf Analytics-Ereignisse in Adobe Commerce und Sensei angewendet. Der Adobe Commerce Events Collector [README](https://github.com/adobe/commerce-events/blob/e34bcfc0deca8d5ac1f9310fc1ee4c1becf4ffbb/packages/storefront-events-collector/README.md) bietet zusätzliche Informationen.

>[!NOTE]
>
>Wenn Sie die `productListItems` mit benutzerdefinierten Attributen in Experience Platform-Ereignis-Payloads erweitern, stimmen Sie Produkte mithilfe der SKU ab. Diese Anforderung gilt nicht für `product-page-view`.

### Nutzung

```javascript
const mse = window.magentoStorefrontEvents;

mse.publish.productPageView(customCtx);
```

### Beispiel 1

Dieses Beispiel fügt beim Veröffentlichen des Ereignisses benutzerdefinierten Kontext hinzu.

```javascript
magentoStorefrontEvents.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

### Beispiel 2

In diesem Beispiel wird vor der Veröffentlichung des Ereignisses benutzerdefinierter Kontext hinzugefügt.

```javascript
const mse = window.magentoStorefrontEvents;

mse.context.setCustom({
  productListItems: [
    {
      productCategories: [
        {
          categoryID: "cat_15",
          categoryName: "summer pants",
          categoryPath: "pants/mens/summer",
        },
      ],
    },
  ],
});

mse.publish.productPageView();
```

### Beispiel 3

Dieses Beispiel legt den benutzerdefinierten Kontext im Herausgeber fest und überschreibt den benutzerdefinierten Kontext, der zuvor in der Adobe-Client-Datenschicht festgelegt wurde.

In diesem Beispiel weist das `pageView`-Ereignis **Feld „Benutzerdefinierter**&quot; im `web.webPageDetails.name` auf.

```javascript
const mse = window.magentoStorefrontEvents;

mse.context.setCustom({
  web: {
    webPageDetails: {
      name: 'Custom Page Name 1'
    },
  },
});

mse.publish.pageView({
  web: {
    webPageDetails: {
      name: 'Custom Page Name 2'
    },
  },
});
```

### Beispiel 4

Dieses Beispiel fügt benutzerdefinierten Kontext zu `productListItems` Ereignissen mit mehreren Produkten hinzu.

```javascript
const mse = window.magentoStorefrontEvents;

mse.context.setCustom({
  productListItems: [
    {
      SKU: "24-WB01", //Match SKU to override correct product in event payload
      productCategory: "Hand Bag", //Custom attribute added to event payload
      name: "Strive Handbag (CustomName)" //Override existing attribute with custom value in event payload
    },
    {
      SKU: "24-MB04",
      productCategory: "Backpack Bag",
      name: "Strive Backpack (CustomName)"
    },
  ],
});

mse.publish.shoppingCartView();
```

Luma-basierte Stores:

Luma-basierte Stores implementieren nativ Publishing-Ereignisse, sodass Sie benutzerdefinierte Daten durch Erweitern von `customContext` festlegen können.

Beispiel:

```javascript
mse.context.setCustom({
  web: {
    webPageDetails: {
      name: 'Custom Page Name'
    },
  },
});
```

>[!NOTE]
>
> Das Überschreiben von Ereignissen mit benutzerdefinierten Attributen kann sich auf standardmäßige Adobe Analytics-Berichte auswirken.
