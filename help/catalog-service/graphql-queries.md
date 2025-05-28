---
title: '[!DNL Retrieve catalog data with GraphQL]'
description: Verwenden Sie GraphQL-Abfragen, um die Katalogdaten abzurufen und Commerce-Erlebnisse zu unterstützen.
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
source-git-commit: 935f34a8b4317686e67e33b50df3301d746fbd25
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Abrufen von Katalogdaten mit GraphQL {#graphql-queries}

Verwenden Sie GraphQL-Abfragen, um Produkt-, Preis- und andere Daten aus dem SaaS-Datenbereich des Adobe Commerce-Katalogs abzurufen und sie zu verwenden, um Commerce-Erlebnisse schneller zu rendern als die nativen Adobe Commerce GraphQL-Abfragen.

Der Katalog-Service stellt die folgenden Abfragen bereit:

| Abfrage | Beschreibung | Nutzung |
|-------|-------------|-------|
| `categories` | Gibt Kategoriedaten zurück. Wenn das Unterbaum-Eingabeobjekt angegeben ist, gibt die Abfrage Details zu Unterkategorien zurück. | Nützlich zum Rendern der Navigation in der Storefront und der Kategorieseiten. [Siehe Beispiel.](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) |
| `products` | Gibt Details zu den als Eingabe angegebenen SKUs zurück. | Wird hauptsächlich zum Rendern von Inhalten auf Produktdetailseiten und Produktvergleichsseiten verwendet. [Siehe Beispiel.](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) |
| `productSearch` | Gibt eine Liste mit Produkten zurück, die den Suchkriterien entsprechen. | Nützlich für die Darstellung von Suchergebnissen und Produktlistenseiten basierend auf der Sucheingabe. [Siehe Beispiel.](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) |
| `refineProduct` | Engt die Ergebnisse einer Produktabfrage ein, die für ein komplexes Produkt ausgeführt wird, um bestimmte Informationen über eine Produktvariante zurückzugeben. | Nützlich für die Darstellung aktualisierter Produktdetailseiten, wenn der Käufer eine Produktoption auswählt. [Siehe Beispiel.](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) |
| `variants` | Gibt Details zu allen Varianten eines Produkts zurück. | Nützlich für die Anzeige von Variantenbildern auf Produktdetailseiten oder Listenseiten, ohne mehrere API-Anfragen zu senden. [Siehe Beispiel.](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-variants/) |


Weitere Informationen zur Verwendung [ Abfragen finden Sie ](https://developer.adobe.com/commerce/services/graphql/catalog-service/) Handbuch zur Catalog Service-API .

