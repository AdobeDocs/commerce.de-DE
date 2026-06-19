---
title: '[!DNL Manage the Data Export extension]'
description: Erfahren Sie, wie Sie  [!DNL Data Export]  Erweiterung aktualisieren und nicht erforderliche Datenexportdienste entfernen oder deaktivieren.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
exl-id: 94702995-d272-47b9-9560-198eee3250a6
TQID: https://experienceleague.adobe.com/ghrA-YFR7hurQgEnjS8PdxR7Zcx-ayLTuyBfhbCC-KI
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: de2e2e68-c5d7-4efe-be7b-27528698f06b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: d3cdead0-685a-4489-9250-4bb709942f66
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 312
ht-degree: 0%

---

# Verwalten der SaaS-Datenexporterweiterung

Die [[!DNL data export] Erweiterung](https://github.com/magento/commerce-data-export) für SaaS-Services ist eine Sammlung von Modulen, die die Datenerfassung und Synchronisierung zwischen Adobe Commerce und verbundenen Commerce-Services ermöglichen.

Spezifische Module sind in den Metapaketen für Adobe Commerce Services-Erweiterungen enthalten, z. B.
as [Live Search](/help/live-search/overview.md), [Product Recommendations](/help/product-recommendations/overview.md), [Catalog Service](/help/catalog-service/overview.md) und [[!DNL Adobe Commerce Optimizer Connector]](/help/aco-connector/overview.md). Wenn Sie diese Services verwenden, ist keine separate Installation erforderlich, um die Datenexporterweiterung zu aktivieren.

## Entfernen oder Deaktivieren von Commerce-Datenexportfunktionen

Wenn Sie keines der installierten Commerce-Datenexportmodule benötigen, deaktivieren Sie es mit dem `magento:module:disable` CLI-Befehl.

Beispielsweise gibt es eine [Kategorien-API](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) die die Kategorienberechtigungs-Feed-Daten intern verwendet. Wenn Sie diese API nicht verwenden, können Sie den Datenexport für den Berechtigungsfeed der Kategorien deaktivieren.

```shell
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### Aktualisieren eines Moduls auf eine bestimmte Version

Sie können jedes der installierten Commerce-Datenexportmodule mithilfe von Composer aktualisieren. Lesen Sie die [Versionshinweise](release-notes.md), um festzustellen, ob eine benötigte Fehlerbehebung verfügbar ist, und aktualisieren Sie dann auf diese spezifische Version und alle erforderlichen Abhängigkeiten.

>[!NOTE]
>
>Wenn Sie auf die neueste Version von [Live Search](/help/live-search/overview.md), [Catalog Service](/help/catalog-service/overview.md), [Product Recommendations](/help/product-recommendations/overview.md) oder [[!DNL Adobe Commerce Optimizer Connector]](/help/aco-connector/overview.md) aktualisieren, erhalten Sie auch die neueste Version der Datenexporterweiterung. Das Metapaket für den Datenexport ist eine Abhängigkeit von den Composer-Paketen für diese Services.

1. Melden Sie sich beim Commerce-Anwendungsserver an.

1. Aktualisieren Sie das Modul über die Befehlszeile mit Composer:

   ```bash
   composer require magento/module-data-exporter:103.0.4 --with-all-dependencies
   ```

Wenn die Commerce-Instanz in der Cloud-Infrastruktur bereitgestellt wird, aktualisieren Sie die Erweiterung in Ihrem Cloud-Projektverzeichnis. Siehe [Upgrade einer Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) im Handbuch zu _Adobe Commerce in Cloud-Infrastrukturen_.

>[!MORELIKETHIS]
>
> - [Versionshinweise](release-notes.md)
> - [SaaS-Datenexportmodule](reference/data-export-modules.md)
> - [Handbuch - Übersicht](overview.md)
