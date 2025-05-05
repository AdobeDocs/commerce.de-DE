---
title: SaaS-Preisindizierung
description: Verwenden der SaaS-Preisindizierung zur Leistungsverbesserung
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# SaaS-Preisindizierung

Die SaaS-Preisindizierung optimiert die Site-Performance, indem ressourcenintensive Aufgaben wie Indizierung und Preisberechnung von der Commerce-Anwendung auf die Cloud-Infrastruktur von Adobe verlagert werden. Dieser Ansatz ermöglicht es Händlern, Ressourcen schnell zu skalieren, um die Indexierungszeiten zu beschleunigen und Preisaktualisierungen schneller für die Storefront und verbundene Commerce-Services bereitzustellen.

Das folgende Diagramm zeigt den Indizierungsdatenfluss zu SaaS-Services, wenn Commerce den im Commerce-Programm enthaltenen [Preisindizierungs](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/manage-indexers)-Prozess verwendet:

![Standarddatenfluss](assets/old_way.png)

Wenn die SaaS-Preisindizierung aktiviert ist, ändert sich der Datenfluss. Die Preisindizierung erfolgt mithilfe des [Commerce SaaS-](../data-export/data-synchronization.md).

![SaaS-Preisindizierungs-Datenfluss](assets/new_way.png)

Alle Händler können von der SaaS-Preisindizierung profitieren, aber Händler, die Projekte mit folgenden Merkmalen haben, können die größten Gewinne erzielen:

* **Konstante Preisänderungen** Händler, die wiederholte Preisänderungen benötigen, um strategische Ziele wie häufige Werbeaktionen, saisonale Rabatte oder Bestandsmarkdowns zu erreichen.
* **Mehrere Websites und/oder Kundengruppen** Händler mit freigegebenen Produktkatalogen über mehrere Websites (Domains/Marken) und/oder Kundengruppen hinweg.
* **Viele einzigartige Preise über Websites oder Kundengruppen hinweg**-Händler mit umfangreichen gemeinsamen Produktkatalogen, die einzigartige Preise über Websites oder Kundengruppen hinweg enthalten. Beispiele sind B2B-Händler mit vorab ausgehandelten Preisen oder Marken mit unterschiedlichen Preisstrategien.

## SaaS-Preisindizierung verwenden

Die SaaS-Preisindizierung wird bei der Installation von Adobe Commerce Services automatisch aktiviert. Es unterstützt die Preisberechnung für alle integrierten Adobe Commerce-Produktarten.

### Anforderungen

* Adobe Commerce 2.4.4+

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

### Preise für benutzerdefinierte Produktarten

Preisberechnungen werden für benutzerdefinierte Produktarten wie Basispreis, Sonderpreis, Gruppenpreis, Katalogregelpreis usw. unterstützt.

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

