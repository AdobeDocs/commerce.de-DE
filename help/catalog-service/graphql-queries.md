---
title: '[!DNL Retrieve catalog data with GraphQL]'
description: Verwenden Sie GraphQL-Abfragen, um die Katalogdaten abzurufen und Commerce-Erlebnisse zu unterstützen.
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
exl-id: 49bbdb3b-bbe9-4777-8ea7-3bd25ae53889
TQID: https://experienceleague.adobe.com/ahutwotbB6Dxg7Tc3WMFd7S-WBMALvOYIUTmB5JKmyM
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 268
ht-degree: 0%

---

# Abrufen von Katalogdaten mit GraphQL {#graphql-queries}

Verwenden Sie GraphQL-Abfragen, um Produkt-, Preis- und andere Daten aus dem SaaS-Datenbereich des Adobe Commerce-Katalogs abzurufen und sie zu verwenden, um Commerce-Erlebnisse schneller zu rendern als die nativen Adobe Commerce GraphQL-Abfragen.

{{aco-merchandising-services}}

Der Katalog-Service stellt die folgenden Abfragen bereit:

| Abfrage | Beschreibung | Nutzung |
|-------|-------------|-------|
| `categories` | Gibt Kategoriedaten zurück. Wenn das Unterbaum-Eingabeobjekt angegeben ist, gibt die Abfrage Details zu Unterkategorien zurück. | Nützlich zum Rendern der Navigation in der Storefront und der Kategorieseiten. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) |
| `products` | Gibt Details zu den als Eingabe angegebenen SKUs zurück. | Wird hauptsächlich zum Rendern von Inhalten auf Produktdetailseiten und Produktvergleichsseiten verwendet. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) |
| `productSearch` | Gibt eine Liste mit Produkten zurück, die den Suchkriterien entsprechen. | Nützlich für die Darstellung von Suchergebnissen und Produktlistenseiten basierend auf der Sucheingabe. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) |
| `refineProduct` | Engt die Ergebnisse einer Produktabfrage ein, die für ein komplexes Produkt ausgeführt wird, um bestimmte Informationen über eine Produktvariante zurückzugeben. | Nützlich für die Darstellung aktualisierter Produktdetailseiten, wenn der Käufer eine Produktoption auswählt. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/) |
| `variants` | Gibt Details zu allen Varianten eines Produkts zurück. | Nützlich für die Anzeige von Variantenbildern auf Produktdetailseiten oder Listenseiten, ohne mehrere API-Anfragen zu senden. [Siehe Beispiel.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/product-variants/) |

Weitere [ zur Verwendung dieser Abfragen finden ](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/) unter „Storefront Services GraphQL&quot;.
