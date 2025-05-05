---
title: Ereignisse [!DNL Live Search]
description: Erfahren Sie, wie Ereignisse Daten für  [!DNL Live Search] erfassen.
feature: Services, Eventing
exl-id: a9f4f254-d8ff-46f1-8deb-a75b90d70d52
source-git-commit: 94d2a9911ab10d164d75779d1f310e5bdf2aea74
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Ereignisse [!DNL Live Search]

[!DNL Live Search] nutzt Ereignisse, um Suchalgorithmen wie „Am häufigsten angezeigt“ und „Angezeigt dies, Angezeigt das“ zu unterstützen. Während das [Commerce-Beispiel-Luma](https://experienceleague.adobe.com/de/docs/commerce-admin/content-design/design/themes/themes#the-default-theme)-Design das Eventing vorkonfiguriert bekommt, müssen Headless- und andere benutzerdefinierte Implementierungen das Eventing für ihre eigenen Anforderungen implementieren.

In dieser Tabelle werden die von [!DNL Live Search] verwendeten Ereignisse [Rangfolgestrategien](rules-add.md#intelligent-ranking).

| Rangfolgestrategie | -Events | Seite |
| --- | --- | --- |
| Am häufigsten angezeigt | `page-view`<br>`product-view` | Produktdetailseite |
| Am häufigsten gekauft | `page-view`<br>`place-order` | Warenkorb/Checkout |
| Am häufigsten zum Warenkorb hinzugefügt | `page-view`<br>`add-to-cart` | Produktdetailseite<br>Produktlistenseite<br>Warenkorb<br>Wunschliste |
| hat dieses angezeigt, hat Folgendes angezeigt | `page-view`<br>`product-view` | Produktdetailseite |

>[!NOTE]
>
>Die Datenerhebung zum Zwecke der [!DNL Live Search] umfasst keine personenbezogenen Daten (PII). Alle Benutzerkennungen wie Cookie-IDs und IP-Adressen werden streng anonymisiert. [Weitere Informationen](https://www.adobe.com/privacy/experience-cloud.html).

## Erforderliche Dashboard-Ereignisse

Einige Ereignisse sind erforderlich, um das Dashboard [Live-Suche“ ](performance.md)

| Dashboard-Bereich | -Events | Feld verbinden |
| ------------------- | ------------- | ---------- |
| Eindeutige Suchvorgänge | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Null Suchergebnisse | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Rate der Nullergebnisse | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Beliebte Suchvorgänge | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Durchschnitt Klick-Position | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | `searchRequestId` |
| Clickthrough-Rate | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | `searchRequestId`, `sku`, `parentSku` |
| Konversionsrate | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | `searchRequestId`, `sku`, `parentSku` |

### Erforderliche Kontext

Für alle Ereignisse sind die `Page` und `Storefront` Kontexte erforderlich. Dies sollte auf Seitenebene/Storefront-Anwendungsebene geschehen, anstatt beim Generieren einzelner Ereignisse (z.B. in einer PHP-Storefront ist der PHP-Anwendungs-Container dafür verantwortlich, diese zur Laufzeit festzulegen).

## Nutzung

Im Folgenden finden Sie eine Beispielimplementierung des `search-request-sent` Ereignisses:

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## Einschränkungen

- Anzeigenblocker und Datenschutzeinstellungen können verhindern, dass Ereignisse erfasst werden, und können dazu führen, dass die Interaktion und der Umsatz [Metriken](performance.md) nicht erfasst werden. Darüber hinaus werden einige Ereignisse möglicherweise nicht gesendet, weil der Käufer die Seite oder das Netzwerk verlassen hat.
- Headless-Implementierungen müssen Eventing implementieren, um intelligentes Merchandising zu unterstützen.

>[!NOTE]
>
>Wenn [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=de) aktiviert ist, erfasst Adobe Commerce keine Verhaltensdaten, bis der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Einschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
