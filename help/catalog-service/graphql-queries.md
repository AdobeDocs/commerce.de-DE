---
title: '[!DNL Retrieve catalog data with GraphQL]'
description: Verwenden Sie GraphQL-Abfragen, um die Katalogdaten abzurufen und Commerce-Erlebnisse zu unterstützen.
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
exl-id: 49bbdb3b-bbe9-4777-8ea7-3bd25ae53889
TQID: https://experienceleague.adobe.com/ahutwotbB6Dxg7Tc3WMFd7S-WBMALvOYIUTmB5JKmyM
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: d842311424e76b83a131ada7a2db6e3fb868acd8
workflow-type: tm+mt
source-wordcount: 269
ht-degree: 0%

---

# Abrufen von Katalogdaten mit GraphQL {#graphql-queries}

Verwenden Sie GraphQL-Abfragen, um Produkt-, Preis- und andere Katalogdaten aus dem [!DNL Catalog Service] abzurufen und [!DNL Adobe Commerce] Storefront-Erlebnisse schneller als native Produktabfragen zu rendern.

{{aco-merchandising-services}}

Die [!DNL Catalog Service] stellt die folgenden Abfragen bereit:

| Abfrage | Beschreibung | Nutzung | Beschränkungen |
| --- | --- | --- | --- |
| `categories` | Gibt Kategoriedaten zurück. Wenn das `subtree` Eingabeobjekt angegeben ist, gibt die Abfrage Details zu Unterkategorien zurück. | Nützlich für das Rendern der Navigation in der Storefront und für Kategorieseiten. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/){target="_blank"} | — |
| `products` | Gibt Details zu den als Eingabe angegebenen SKUs zurück. | Wird hauptsächlich zum Rendern von Inhalten auf Produktdetailseiten und Produktvergleichsseiten verwendet. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/){target="_blank"} | 100 SKUs pro Anfrage |
| `productSearch` | Gibt eine Liste mit Produkten zurück, die den Suchkriterien entsprechen. | Nützlich für die Darstellung von Suchergebnissen und Produktlistenseiten basierend auf der Sucheingabe. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/){target="_blank"} | 100 SKUs pro Anfrage |
| `refineProduct` | Engt die Ergebnisse der `products` Abfrage für ein komplexes Produkt ein, um spezifische Informationen zu einer Produktvariante zurückzugeben. | Nützlich zum Rendern aktualisierter Produktdetailseiten, wenn Käufer eine Produktoption auswählen. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/){target="_blank"} | 100 SKUs pro Anfrage |
| `variants` | Gibt Details zu allen Varianten eines Produkts zurück. | Nützlich für die Anzeige von Variantenbildern auf Produktdetailseiten oder Listenseiten, ohne mehrere API-Anfragen zu senden. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/product-variants/){target="_blank"} | 100 SKUs pro Anfrage |

{style="table-layout:auto"}

Weitere [&#x200B; zur Verwendung dieser Abfragen finden &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/){target="_blank"} unter „Storefront Services GraphQL&quot;.
