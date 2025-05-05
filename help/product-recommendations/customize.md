---
title: Customize
description: Erfahren Sie, wie Sie Ihre Produktempfehlungen anpassen können.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Customize

Wenn Sie das Modul Produktempfehlungen installieren, erstellt Adobe Commerce das `ProductRecommendationsLayout`. Dieses Verzeichnis enthält Vorlagendateien, die Sie anpassen können, um zu ändern, wie die Empfehlungen auf Ihrer Storefront angezeigt werden. Insbesondere können Sie die folgende Vorlage ändern oder überschreiben:

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Weitere Informationen zum Ändern von Vorlagendateien finden Sie unter [Vorlagenanpassung](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) im Frontend-Entwicklerhandbuch.

Wenn Sie die `recommendations.html` ändern, müssen Sie die folgenden Tags in der Datei beibehalten, um sicherzustellen, dass Adobe Commerce Empfehlungsmetriken aus Ihrer Storefront erfassen kann:

| Tag | Verwenden Sie |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Sammelt Ansichtsereignisse. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Sammelt Klickereignisse. <br/>**Hinweis:** Wenn Sie Anker-Tags hinzufügen, müssen Sie diese Attribute einschließen. |

Zusätzlich zur `recommendations.html`-Datei enthält das `ProductRecommendationsLayout`-Verzeichnis die folgenden Unterverzeichnisse:

| Verzeichnis | Zweck |
|---|---|
| `layout` | Enthält `*.xml` Dateien für jeden Seitentyp |
| `templates` | Enthält Dateien, die die Skripte zum Abrufen und Rendern aufrufen |
| `web/js` | Enthält die JavaScript-Dateien, die Empfehlungen für Ihren Store abrufen und rendern |
| `web/template` | Enthält die Vorlage für das `magento/product-recommendations` |

## Positionierung der Empfehlungseinheit

Wenn Sie [Empfehlung erstellen](create.md) geben Sie den [Speicherort](placement.md) an, an dem sie auf der Seite angezeigt wird. Eine Empfehlungseinheit kann entweder oben oder unten im Hauptinhalts-Container platziert werden. Sie können diese Platzierung jedoch anpassen. Wenn Sie einen Inhaltstyp „Page Builder-Empfehlung“ erstellen, verwenden Sie die Page Builder-Tools, um die Empfehlungseinheit auf der Seite zu positionieren. Bearbeiten Sie für alle anderen Seitentypen die `*.xml`, die beim Erstellen der Empfehlung generiert werden.

1. Wechseln Sie in das `layout` Verzeichnis :

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   In der folgenden Tabelle sind die in diesem Verzeichnis vorhandenen XML-Dateien aufgeführt:

   | Dateiname | Seite |
   |---|---|
   | `catalog_category_view.xml` | Kategorie |
   | `catalog_product_view.xml` | Produktdetails |
   | `checkout_cart_index.xml` | Warenkorb |
   | `checkout_onepage_success.xml` | Checkout |
   | `cms_index_index.xml` | Startseite |

   >[!NOTE]
   >
   >Die Dateinamen im `layout` können unterschiedlich sein, wenn Ihr Store Erweiterungen von Drittanbietern verwendet.

1. Ändern Sie die `catalog_product_view.xml` so, dass die Empfehlungseinheit nach dem Produktbild auf der Produktdetailseite angezeigt wird. Sehen Sie sich vor dem Anpassen dieser XML-Datei die Datei an und lernen Sie die Abschnitte kennen, die Sie ändern müssen:

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Im obigen Ausschnitt zeigt der `main.content` Referenzblock an, dass die Empfehlungseinheit relativ zu diesem Element platziert wird. Ihr `block`-Element enthält das `after="-"`-Attribut, das angibt, dass die Empfehlungseinheit auf der Seite nach dem Hauptinhaltsblock angezeigt wird.

1. Ändern wir diese Datei, indem wir einen anderen Inhaltsbaustein angeben.

   Ändern Sie die `name` des Referenzblocks von `main.content` in `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Durch diese Änderung wird Ihre Empfehlungseinheit nach dem Produktbild auf der Produktdetailseite angezeigt. Wenn die Empfehlungseinheit vor dem `product.info.media` angezeigt werden soll, ändern Sie das `after="-"` Attribut in `before="-"`. Das `pagePlacement` Argument ist ein internes Argument, das nicht geändert werden sollte.

Weitere Informationen [ Blocktypen auf der Seite finden ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) unter „Layout - Übersicht .

## Benutzerdefinierte Produktattribute

Entwickler benötigen häufig Zugriff auf benutzerdefinierte Produktattributwerte in Recommendations-Einheiten auf Storefronts, damit sie auf der Grundlage dieser Attribute visuelle Abwandlungen zu Produkten hinzufügen können.

Wenn Ihr Geschäft beispielsweise Bio-Produkte verkauft, können Sie ein benutzerdefiniertes Attribut auf diesen Produkten haben, das sie als `Organic = Yes` kennzeichnet. Möglicherweise benötigen Sie Zugriff auf diesen Attributwert in der Storefront, damit Sie diesen Produkten eine besondere visuelle Behandlung bieten können, wenn sie in Recommendations angezeigt werden. Ebenso können Sie durch den Zugriff auf diese benutzerdefinierten Produktattributwerte Produkte kennzeichnen oder die benutzerdefinierte Logik in der Präsentationsebene Ihrer Site steuern.

![Abzeichen hinzufügen](assets/unit-custom.png)

Um sicherzustellen, dass beim Rendern der Empfehlungseinheit auf der Seite ein benutzerdefiniertes Produktattribut verfügbar ist, legen Sie die `Used in Product Listing` Eigenschaft auf der Seite &quot;[&quot; ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html?lang=de) Admin auf `Yes` fest.

Wenn diese Eigenschaft festgelegt ist, enthält die JSON-Payload ein `attributes`-Objekt, das ein Array von Attributcodes und -werten enthält. Sie können dann einen benutzerdefinierten Storefront-Stil anwenden, der auf diesen Attributwerten basiert, z. B. das Hinzufügen spezieller visueller Behandlungen oder Abzeichen wie zuvor erwähnt.

>[!NOTE]
>
>Es kann bis zu einer Stunde dauern, bis Produktattributänderungen in der JSON-Payload angezeigt werden.
