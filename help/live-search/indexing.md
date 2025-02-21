---
title: Indizierung
description: Erfahren Sie [!DNL Live Search]  wie Produktattributeigenschaften indiziert.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Indizierung

Der [!DNL Live Search] Indizierungsprozess liest den Katalog nach Produktattributen durch und erstellt einen Index, damit Produkte schnell gesucht, gefiltert und angezeigt werden können.

Produkteigenschaften (Metadaten) bestimmen:

* Verwendung eines Attributs im Katalog
* Sein Aussehen und Verhalten im Laden
* Die Daten, die bei Datenübertragungsvorgängen enthalten sind

Der Umfang der Attributmetadaten ist `website/store/store view`.

Mit der [!DNL Live Search]-API kann ein Client nach jedem Produktattribut sortieren, bei dem die Eigenschaft [Storefront](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) im Adobe Commerce Admin auf `Yes` gesetzt `Use in Search`. Wenn diese Option aktiviert ist, können `Search Weight` für das Attribut festgelegt werden.

[!DNL Live Search] indiziert keine gelöschten Produkte oder Produkte, für die `Not Visible Individually` festgelegt ist.

>[!NOTE]
>
> Commerce-Kunden mit [!DNL Live Search] können mit dem SaaS-Preisindexer [ schnellere Preisänderungen und Synchronisierungszeiten auf ihren Websites ](../price-index/price-indexing.md).

## Indizierungs-Pipeline

Der Client ruft den Suchdienst von der Storefront auf, um (filterbare, sortierbare) Indexmetadaten abzurufen. Der Suchdienst kann nur durchsuchbare Produktattribute aufrufen, bei denen die Eigenschaft *Verwenden in der* Navigation) auf `Filterable (with results)` und *Verwenden für die Sortierung in der* auf `Yes` gesetzt ist.

Um eine dynamische Abfrage zu erstellen, muss der Suchdienst wissen, welche Attribute durchsuchbar sind und welche ([) ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results). [!DNL Live Search] berücksichtigt die Gewichtung der Adobe Commerce-Suche (1-10, wobei 10 die höchste Priorität hat). Die Liste der Daten, die mit dem Katalog-Service synchronisiert und freigegeben werden, finden Sie im Schema , das definiert ist in:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] Index-Client-Suchdiagramm](assets/indexing-pipeline.svg)

1. Händler auf [!DNL Live Search] prüfen.
1. Abrufen von Store-Ansichten mit Änderungen an Attributmetadaten.
1. Indizierungsattribute speichern.
1. Indizieren Sie den Suchindex neu.

### Vollständiger Index

Wenn [!DNL Live Search] während des Onboardings konfiguriert und synchronisiert wird, kann es bis zu 60 Minuten dauern, bis der anfängliche Index erstellt ist. Die Indizierung großer Kataloge kann länger dauern. Der Prozess beginnt, nachdem `cron` den Feed gesendet und die Ausführung abgeschlossen hat.

Die folgenden Ereignisse verursachen einen Trigger bei einem vollständigen Synchronisierungs- und Index-Build:

* Onboarding [Katalog-Datensynchronisation](install.md#synchronize-catalog-data)
* Änderungen an Attributmetadaten

Wenn Sie beispielsweise die `Use in Search`-Eigenschaft des `color` von `No` auf `Yes` ändern, werden die Attributmetadaten in `searchable=true` geändert, und die Trigger erhalten eine vollständige Synchronisierung und Neuindizierung. Der folgende Attributmetadaten-Trigger führt eine vollständige Synchronisierung und Neuindizierung durch, wenn er geändert wird:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Streaming-Produktaktualisierungen

Nachdem der anfängliche Index während des [Onboarding](install.md#synchronize-catalog-data) erstellt wurde, werden die folgenden inkrementellen Produktaktualisierungen kontinuierlich synchronisiert und neu indiziert:

* Dem Katalog hinzugefügte neue Produkte
* Änderungen an Produktattributwerten

Das Hinzufügen eines neuen Farbfeldwerts zum `color`-Attribut wird beispielsweise als Streaming-Produktaktualisierung gehandhabt.

Workflow zur Streaming-Aktualisierung:

1. Aktualisierte Produkte werden von der Adobe Commerce-Instanz mit dem Katalog-Service synchronisiert.
1. Der Indizierungs-Service sucht kontinuierlich nach Produktaktualisierungen über den Katalog-Service. Aktualisierte Produkte werden indiziert, sobald sie im Katalog-Service eintreffen.
1. Es kann bis zu 15 Minuten dauern, bis eine Produktaktualisierung in [!DNL Live Search] verfügbar ist.

#### Aktualisierungen, die sich auf die Sichtbarkeit des Produkts auswirken

Wenn Sie Aktualisierungen an [!DNL Live Search] Admin-Konfigurationseinstellungen, Adobe Commerce Admin-Konfigurationseinstellungen oder Aktualisierungen an Katalogdaten vornehmen, können Sie eine Verzögerung erwarten, bevor diese Änderungen in der Storefront angezeigt werden.

In der folgenden Tabelle werden die verschiedenen Änderungen und die ungefähre Wartezeit beschrieben, bevor sie in der Storefront angezeigt werden.

| Updates | Wartet, bis auf der Storefront sichtbar |
|---|---|
| [!DNL Live Search] Admin ändert sich in Facetten, Preiseinstellungen, Such- oder Kategorie-Merchandising-Regeln. | 15-20 Minuten. |
| [!DNL Live Search] Admin-Änderungen, die eine Neuindizierung erfordern: Spracheinstellungen oder Synonyme. | Bis zu 15 Minuten nach Abschluss der Neuindizierung. |
| Adobe Commerce Admin-Änderungen, die eine vollständige Neuindizierung erfordern: durchsuchbare, sortierbare oder filterbare Attributmetadaten | Bis zu 15 Minuten nach Abschluss der Neuindizierung. |
| Inkrementelle Änderungen an Katalogdaten, die keine Neuindizierung erfordern: Produktbestand, Preis, Name usw. | Bis zu 15 Minuten, nachdem der Elastic Search-Index mit den neuesten Daten aktualisiert wurde. |

## Client-Suche

Mit der [!DNL Live Search]-API kann ein Client nach einem beliebigen sortierbaren Produktattribut sortieren, indem er die Eigenschaft [Storefront](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes), *Wird zum Sortieren in Produktlisten verwendet* auf `Yes` setzt. Je nach Design wird durch diese Einstellung das -Attribut als Option in das Paginierungssteuerelement [Sortieren nach](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation) auf Katalogseiten aufgenommen. Bis zu 200 Produktattribute können nach [!DNL Live Search] indiziert werden, wobei [Storefront-Eigenschaften](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) durchsuchbar und filterbar sind.

Die Index-Metadaten werden in der Indizierungs-Pipeline gespeichert und stehen dem Suchdienst zur Verfügung.

![[!DNL Live Search] Index-Metadaten-API-Diagramm](assets/index-metadata-api.svg)

### Arbeitsablauf für sortierbare Attribute

1. Der Client ruft den Suchdienst auf.
1. Der Suchdienst ruft den Suchadministratordienst auf.
1. Der Suchdienst ruft die Indizierungs-Pipeline auf.

## Für alle Produkte indiziert

Die Reihenfolge der Felder in dieser Liste entspricht der typischen Reihenfolge der Spalten in den exportierten Produktdaten.

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

Das folgende Feld ist für alle konfigurierbaren Produkte indiziert:

* `childrenSkus`
