---
title: Erweitern und Anpassen von SaaS-Datenexport-Feed-Daten
description: Erfahren Sie, wie Sie die Feed [!DNL SaaS Data Export] Daten erweitern und anpassen.
role: Admin, Developer
exl-id: 694bd281-12c5-415c-a251-b4251e2edea7
source-git-commit: ac6c690f87e3df2ac4997d80453028829be8e657
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Erweitern und Anpassen von SaaS-Datenexport-Feed-Daten

Die [!DNL Commerce Data Export] bietet eine Möglichkeit, Daten aus der [!DNL Commerce]-Anwendung in Commerce-Services wie Live Search, Catalog Service und Product Recommendations zu exportieren. Bei Bedarf können Sie die Feed-Daten erweitern und anpassen, um zusätzliche Attributdaten einzuschließen, oder die erfassten Daten ändern.

Nachdem Sie Attributdaten hinzugefügt haben, können Sie über das Feld [Attribute](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#productviewattribute-type) im GraphQL-Schema für den Storefront-Service darauf zugreifen.

>[!NOTE]
>
>Das Hinzufügen oder Ändern von Feed-Daten kann sich auf die Leistung und Verarbeitungslogik im Commerce-Backend auswirken. Testen Sie benutzerdefinierten Code vor der Zusammenführung mit der Produktion. Verwenden Sie API Mesh, um das GraphQL-Schema des Katalog-Services zu erweitern, anstatt dem Backend Daten hinzuzufügen. Konfigurationsdetails finden Sie unter [Katalog-Service und API-Mesh](../catalog-service/mesh.md).

## Erweitern von Systemattributdaten im Produkt-Feed

Der Produkt-Feed enthält standardmäßige Systemattribute, die für die Produktverarbeitung erforderlich sind oder von Verbrauchern häufig verwendet werden. Sie können zusätzliche Systemattribute in den Produkt-Feed aufnehmen, indem Sie sie zum Feed hinzufügen.

Um diese Aufgabe abzuschließen, aktualisieren Sie das Modul `magento/catalog-data-exporter` , um die zusätzlichen Systemattribute zur Konfigurationsdatei [Dependency Injection“ hinzuzufügen ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/)`di.xml`).

Fügen Sie die Attribute der `Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery` Produktattributabfrage hinzu.

**Beispiel**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```

## Hinzufügen von Produktattributen zu Adobe Commerce

Entwicklerinnen und Entwickler können Produktattribute hinzufügen, auf die über das Feld [Produktattribute](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#output-fields) zugegriffen werden kann, indem sie eine der folgenden Methoden verwenden:

- Fügen Sie das -Attribut zu Adobe Commerce hinzu, um es in die `products`-Feed-Daten aufzunehmen, die an Commerce-Storefront-Services exportiert wurden.
- Dynamisches Hinzufügen des Attributs während des Feed-Synchronisierungsprozesses mithilfe eines Plug-ins.

### Hinzufügen des Attributs zu Adobe Commerce

Sie können ein Produktattribut aus Commerce Admin hinzufügen oder programmgesteuert ein benutzerdefiniertes PHP-Modul verwenden, um das Attribut zu definieren und Adobe Commerce zu aktualisieren. Das Hinzufügen des Attributs über die Commerce Admin ist die einfachste Methode, da Sie das Attribut und alle erforderlichen Metadaten gleichzeitig hinzufügen können. Das neue Attribut und seine Metadateneigenschaften werden bei der nächsten geplanten Synchronisierung automatisch in die SaaS-Services exportiert.

#### Erstellen des Produktattributs über den Administrator

1. Erstellen Sie das Attribut über die Commerce-Admin auf der Seite „Produktattribut-Konfiguration“ ([!UICONTROL Stores] > *[!UICONTROL Attributes]* > [!UICONTROL Product]).

1. Fügen Sie das -Attribut einem nach Bedarf festgelegten Attributsatz hinzu.

Siehe [Erstellen von Produktattributen](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create) im *Adobe Commerce-Administratorhandbuch*.

#### Programmgesteuertes Erstellen des Produktattributs

Fügen Sie ein Produktattribut programmgesteuert hinzu, indem Sie einen Daten-Patch erstellen, der die `DataPatchInterface` implementiert, und instanziieren Sie eine Kopie der `EavSetup Factory`-Klasse im Konstruktor, um die Attributoptionen zu konfigurieren.

Wenn Sie die Attributoptionen definieren, sind alle Attributparameter außer `type`, `label` und `input` optional. Definieren Sie die folgenden zusätzlichen Parameter und alle anderen, die sich von den Standardeinstellungen unterscheiden.

- **`user_defined`=`1`** - Exportiert das Attribut während der Datensynchronisation in die Storefront-Services
- **`used_in_product_listing`=`1`** - Gewährleisten Sie den Zugriff auf das Attribut in der Datenbankabfrage der Produktliste.

Informationen zum Erstellen von Daten-Patches finden Sie [Daten- und Schema-Patches entwickeln](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) im *PHP-Entwicklerhandbuch*.

### Dynamisches Hinzufügen des Produktattributs

Weitere Informationen zum dynamischen Erstellen von Produktattributen ohne Einführung neuer EAV-Attribute finden Sie unter [Attribut dynamisch hinzufügen](add-attribute-dynamically.md).
