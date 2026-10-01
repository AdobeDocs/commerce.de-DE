---
source-git-commit: a3ade1a31d3c2905b601f71bda118de89c43cf59
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 27%
---

# Konfliktende Erweiterungen entfernen

Wenn Sie eine der folgenden Erweiterungen installiert haben, deinstallieren Sie diese, bevor Sie die [!DNL Adobe Commerce Optimizer Connector for B2B] installieren:

* [!DNL Adobe Commerce Live Search] (`magento/live-search`)
* [!DNL Adobe Commerce Product Recommendations] (`magento/product-recommendations`)
* [!DNL Adobe Commerce Catalog Service] (`magento/catalog-service`, `magento/catalog-service-installer`)
* **[!UICONTROL Data Management Dashboard]** (`magento-catalog-sync-admin`)

Daten, die mit diesen Erweiterungen verknüpft sind, sind weiterhin in der Commerce-Datenbank verfügbar. Er wird jedoch nicht nach [!DNL Commerce Optimizer] exportiert, wenn der Connector aktiviert ist. Um die Adobe Commerce-Such- und Merchandising-Funktionen zu implementieren, die von diesen Erweiterungen nach der Aktivierung des Connectors bereitgestellt werden, konfigurieren Sie sie über die [[!DNL Commerce Optimizer] Admin-Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/commerce/optimizer/overview#quick-tour).

>[!IMPORTANT]
>
>Wenn diese Erweiterungen nicht entfernt werden, bevor der Connector aktiviert wird, treten Konfigurationsfehler, doppelte Daten in [!DNL Commerce Optimizer] und 401- oder 403-Authentifizierungsfehler auf.