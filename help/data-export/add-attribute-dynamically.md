---
title: Dynamisches Hinzufügen von Produktattributen
description: Erfahren Sie, wie Sie dem Datenexport-Feed während des Datensynchronisierungsprozesses dynamisch benutzerdefinierte Produktattribute hinzufügen.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
exl-id: d5ed7497-4be1-440a-a567-81b64fdc54fc
TQID: https://experienceleague.adobe.com/SZWtLSvxb-w-968f4wqWrPTBn1c9IEuthvhIv86Pvss
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 267
ht-degree: 0%

---

# Dynamisches Hinzufügen von Produktattributen

Sie können Produktattribute erweitern, ohne sie in [!DNL Adobe Commerce] zu registrieren, indem Sie ein Plug-in erstellen, um die Attribute während des Datensynchronisierungsprozesses hinzuzufügen.

>[!NOTE]
>
>Die beste Möglichkeit, Produktattribute zu erweitern, besteht darin[&#x200B; sie zu  [!DNL Adobe Commerce]](extensibility-and-customizations.md#add-product-attributes-to-adobe-commerce) where you can configure and manage them from the Commerce Admin. Only add them dynamically if you need them solely for Commerce storefront services and do not want to register them in [!DNL Adobe Commerce]. You also have the option to manage custom attributes using [[!DNL API Mesh] mit [!DNL Catalog Service]](../catalog-service/mesh.md) hinzuzufügen, um das [!DNL Catalog Service] [!DNL GraphQL] Schema zu erweitern.

## Produktattribute hinzufügen

Erstellen Sie ein Plug-in, das der `Magento\CatalogDataExporter\Model\Provider\Product\Attributes`-Klasse einen `customer_attribute` hinzufügt.

1. Aktualisieren Sie die [Konfigurationsdatei für die Abhängigkeitseinspeisung](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`), um das Plug-in zu definieren.

   ```xml
   <type name="Magento\CatalogDataExporter\Model\Provider\Product\Attributes">
     <plugin name="product_customer_attributes" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttribute"/>
   </type>
   ```

1. Erstellen Sie das Plug-in.

   ```php
    <?php
    declare(strict_types=1);
   
    namespace Vendor\CatalogDataExporter\Model\Plugin;
   
    use Magento\CatalogDataExporter\Model\Provider\Product\Attributes;
   
    class AddAttribute {
   
         /**
          * @param Attributes $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
          public function afterGet(Attributes $subject, array $result, $arguments): array
          {
              $additionalAttributes = [];
              $attributeCode = 'customer_attribute';
              foreach ($result as $product) {
                  if (!isset($product['productId']) || !isset($product['storeViewCode'])) {
                      continue;
                  }
                  // HINT: if needed, do filtration by "storeViewCode" and or "productId"
   
                  $productId = $product['productId'];
                  $storeViewCode = $product['storeViewCode'];
   
                  $newKey = \implode('-', [$product['storeViewCode'], $product['productId'], $attributeCode]);
                  if (isset($additionalAttributes[$newKey])) {
                      continue;
                  }
                  $additionalAttributes[$newKey] = [
                      'productId' => $productId,
                      'storeViewCode' => $storeViewCode,
                      'attributes' => [
                          'attributeCode' => $attributeCode,
                          // provide single or multiple values for the attribute
                          'value' => [
                              rand(1, 42)
                          ]
                      ]
                  ];
   
              }
   
              return array_merge($result, $additionalAttributes);
          }
    }
   ```

   Nachdem Sie das Plug-in hinzugefügt haben, werden die Änderungen bei der nächsten geplanten Synchronisierung mit verbundenen Storefront-Services synchronisiert. Um die Aktualisierungen sofort zu senden, verwenden Sie den folgenden CLI-Befehl, um den Synchronisierungsprozess manuell zu starten.

   ```shell
   bin/magento saas:resync --feed=products
   ```

## Deklarieren benutzerdefinierter Produktattribut-Metadaten

Wenn Sie ein benutzerdefiniertes Produktattribut dynamisch erstellen und es für die Anzeige, Suche oder Filterung in Storefront-Services verwenden möchten, fügen Sie die Metadaten des Produktattributs hinzu, um das Verhalten der Storefront zu konfigurieren.

1. Aktualisieren Sie die [Konfigurationsdatei für Abhängigkeitseinfügungen](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`), um das Plug-in für die Metadaten des Produktattributs zu definieren.

   ```xml
   <type name="Magento\CatalogDataExporter\Model\Provider\ProductMetadata">
     <plugin name="product_customer_attributes_metadata" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttributeMetadata"/>
   </type>
   ```

1. Erstellen Sie das Plug-in für die folgende Provider-`Magento\CatalogDataExporter\Model\Provider\ProductMetadata`.

   Überprüfen Sie `ProductAttributeMetadata` in `vendor/magento/module-catalog-data-exporter/etc/et_schema.xml` auf Pflichtfelder.

   ```php
    <?php
    declare(strict_types=1);
   
    namespace Vendor\CatalogDataExporter\Model\Plugin;
   
    use Magento\CatalogDataExporter\Model\Provider\ProductMetadata;
   
    class AddAttributeMetadata {
   
         /**
          * @param ProductMetadata $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
         public function afterGet(ProductMetadata $subject, array $result, $arguments): array
         {
              $result[] = [
                'id' => '123',
                // provide storeCode, websiteCode and storeViewCode applicable for your AC instance
                'storeCode' => 'default',
                'websiteCode' => 'base',
                'storeViewCode' => 'default',
                // specify the customer attribute code - should be the same as used in the products attributes plugin
                'attributeCode' => 'customer_attribute',
                // only product attributes are supported
                'attributeType' => 'catalog_product',
                // specify the data type
                'dataType' => 'int',
                'multi' => false,
                'label' => 'Customer Attribute',
                'frontendInput' => 'select',
                'required' => false,
                'unique' => false,
                'global' => true,
                'visible' => true,
                'searchable' => true,
                'filterable' => true,
                // This value must be set to true to export it to the storefront services
                'visibleInCompareList' => true,
                'visibleInListing' => true,
                'sortable' => true,
                'visibleInSearch' => true,
                'filterableInSearch' => true,
                'searchWeight' => 1.0,
                'usedForRules' => true,
                'boolean' => false,
                'systemAttribute' => false,
                'numeric' => false,
                // specify the list of attribute options
                'attributeOptions' => [
                    'option1',
                    'option2',
                    'option3'
                ]
             ];
   
              return $result;
         }
      }
   ```

   Nachdem Sie das Plug-in hinzugefügt haben, werden die Änderungen bei der nächsten geplanten Synchronisierung mit verbundenen Storefront-Services synchronisiert. Um die Aktualisierungen sofort zu senden, verwenden Sie den folgenden CLI-Befehl, um den Synchronisierungsprozess manuell zu starten.

   ```shell
   bin/magento saas:resync --feed=productAttributes
   ```

>[!MORELIKETHIS]
>
> * [Erweitern und Anpassen von SaaS-Datenexport-Feeds](extensibility-and-customizations.md)
> * [Synchronisieren Sie Feeds mithilfe der Commerce-CLI](data-export-cli-commands.md)
> * [Funktionsweise der Synchronisierung](sync-overview.md) - Erfahren Sie mehr über Synchronisierungsmodi und geplante oder manuelle Neusynchronisierung.
> * [Überprüfen Sie die Protokolle und führen Sie eine Fehlerbehebung durch](troubleshooting/logging.md)
