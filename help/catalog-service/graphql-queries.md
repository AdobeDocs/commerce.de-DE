---
title: '[!DNL Retrieve catalog data with GraphQL]'
description: Verwenden Sie GraphQL-Abfragen, um die Katalogdaten abzurufen und Commerce-Erlebnisse zu unterstützen.
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
exl-id: 49bbdb3b-bbe9-4777-8ea7-3bd25ae53889
source-git-commit: a4c3a24deb77a9aadc7954b46d171b4d4edea6ba
workflow-type: tm+mt
source-wordcount: '214'
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

Weitere [&#x200B; zur Verwendung dieser Abfragen finden &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/) unter „Storefront Services GraphQL&quot;.
