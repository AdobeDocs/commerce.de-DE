---
title: Benutzerdefinierte Ereignisse erstellen
description: Erfahren Sie, wie Sie benutzerdefinierte Ereignisse erstellen, um Ihre Adobe Commerce-Daten mit anderen Adobe DX-Produkten zu verbinden.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '260'
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

Attributüberschreibungen für Standardereignisse werden nur für die Experience Platform unterstützt. Benutzerdefinierte Daten werden nicht an Commerce-Dashboards und Metrik-Tracker weitergeleitet.

Für jedes Ereignis mit `customContext` überschreibt der Collector Felder, die in den relevanten Kontexten festgelegt sind, mit Feldern in `customContext`. Der Anwendungsfall für Überschreibungen besteht darin, dass ein Entwickler Kontexte, die von anderen Teilen der Seite in bereits unterstützten Ereignissen festgelegt wurden, wiederverwenden und erweitern möchte.

>[!NOTE]
>
>Beim Überschreiben benutzerdefinierter Ereignisse sollte die Ereignisweiterleitung an Experience Platform für diesen Ereignistyp deaktiviert werden, um eine doppelte Zählung zu vermeiden.

Beispiele:

Produktansicht mit Überschreibungen, die über Adobe Commerce Events SDK veröffentlicht wurden:

```javascript
mse.publish.productPageView({
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

In Experience Platform Edge:

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> Das Überschreiben von Ereignissen mit benutzerdefinierten Attributen kann sich auf standardmäßige Adobe Analytics-Berichte auswirken.
