---
title: SaaS-Preisindizierung
description: Verwenden der SaaS-Preisindizierung zur Leistungsverbesserung
autotag-review: '2026-06-17T15:08:59.000Z'
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: d1bf3879-3e86-4665-a55c-494963c87f90
TQID: https://experienceleague.adobe.com/dfZjgp5wR6H4c7WkNNhjLYUgKNTPIqPWxKiShlTU1yA
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
last-update: 2026-07-29
source-git-commit: 7ce47d7abf7519a7e3ecd436faabf4089005cd63
workflow-type: tm+mt
source-wordcount: 491
ht-degree: 0%

---

# SaaS-Preisindizierung

Die SaaS-Preisindizierung optimiert die Site-Performance, indem ressourcenintensive Aufgaben wie Indizierung und Preisberechnung von der Commerce-Anwendung auf die Cloud-Infrastruktur von Adobe verlagert werden. Dieser Ansatz ermöglicht es Händlern, Ressourcen schnell zu skalieren, um die Indexierungszeiten zu beschleunigen und Preisaktualisierungen schneller für die Storefront und verbundene Commerce-Services bereitzustellen.

Das folgende Diagramm zeigt den Indizierungsdatenfluss zu SaaS-Services, wenn Commerce den im Commerce-Programm enthaltenen [Preisindizierungs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)-Prozess verwendet:

![Standarddatenfluss](assets/old_way.png)

Wenn die SaaS-Preisindizierung aktiviert ist, ändert sich der Datenfluss. Die Preisindizierung erfolgt mithilfe des [Commerce SaaS-](../data-export/sync-overview.md).

![SaaS-Preisindizierungs-Datenfluss](assets/new_way.png)

Alle Händler können von der SaaS-Preisindizierung profitieren, aber Händler, die Projekte mit folgenden Merkmalen haben, können die größten Gewinne erzielen:

* **Konstante Preisänderungen** - Händler, die wiederholte Preisänderungen benötigen, um strategische Ziele wie häufige Werbeaktionen, saisonale Rabatte oder Bestandsmarkdowns zu erreichen.
* **Mehrere Websites und/oder Kundengruppen** - Händler mit freigegebenen Produktkatalogen über mehrere Websites (Domains/Marken) und/oder Kundengruppen hinweg.
* **Viele einzigartige Preise über Websites oder Kundengruppen hinweg** - Händler mit umfangreichen gemeinsamen Produktkatalogen, die einzigartige Preise über Websites oder Kundengruppen hinweg enthalten. Beispiele sind B2B-Händler mit vorab ausgehandelten Preisen oder Marken mit unterschiedlichen Preisstrategien.

## SaaS-Preisindizierung verwenden

Die SaaS-Preisindizierung wird bei der Installation von Adobe Commerce Services automatisch aktiviert. Es unterstützt die Preisberechnung für alle integrierten Adobe Commerce-Produktarten.

### Anforderungen

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+. Weitere Informationen finden Sie [Systemanforderungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements){target="_blank"}.

### Voraussetzungen

* Einer der folgenden Commerce-Services muss mit der neuesten Version der Commerce-Erweiterung installiert sein:

  * [Katalog-Service](../catalog-service/overview.md)
  * [Live Search](../live-search/overview.md)
  * [Produkt Recommendations](../product-recommendations/guide-overview.md)

>[!NOTE]
>
>Bei Bedarf kann der standardmäßige Preisindexer in der Commerce-Anwendung über den [Catalog Adapter“ deaktiviert ](catalog-adapter.md).

## Preise mit SaaS-Preisindizierung synchronisieren

Nachdem Sie die SaaS-Preisindizierung für Adobe Commerce aktiviert haben, aktualisieren Sie die Preise in der Storefront und in Commerce Services, indem Sie die neuen -Feeds synchronisieren:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## Fortschritt der Synchronisierung überwachen

{{$include /help/_includes/data-export/verify-commerce-service-data-sync.md}}

Verwenden Sie die [Commerce CLI](../data-export/data-export-cli-commands.md) um Feeds bei Bedarf manuell neu zu synchronisieren. Informationen zu Resynchronisierungsoptionen und zusätzlichen Schritten zur Fehlerbehebung finden Sie unter [Synchronisierung verwalten](../data-export/data-sync-manage.md) im _SaaS-Datenexporthandbuch_.

>[!NOTE]
>
>Um die Seite Status der Daten-Feed-Synchronisierung zu aktivieren, wenn sie nicht in der Commerce Admin für Commerce in Cloud- oder lokalen Bereitstellungen verfügbar ist, folgen Sie den [Installationsanweisungen für Erweiterungen](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status#install-the-extension).

## Preise für benutzerdefinierte Produktarten

Preisberechnungen werden für benutzerdefinierte Produktarten wie Basis-, Spezial-, Gruppen- und Katalogregelpreise unterstützt.

Wenn Sie über einen benutzerdefinierten Produkttyp verfügen, der eine bestimmte Formel zur Berechnung des Endpreises verwendet, können Sie das Verhalten des Produktpreis-Feeds erweitern.

1. Erstellen Sie ein Plug-in in der `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice`.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
       <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
           <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
       </type>
   </config>
   ```

1. Erstellen Sie eine Methode mit der benutzerdefinierten Formel:

   ```php
   class UpdatePriceFromFeed
   {
       /**
       * @param ProductPrice $subject
       * @param array $result
       * @param array $values
       *
       * @return array
       */
       public function afterGet(ProductPrice $subject, array $result, array $values) : array
       {
           // Override the output $result with your data for the corresponding products (see original method for details)
           return $result;
       }
   }
   ```
