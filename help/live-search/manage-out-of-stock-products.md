---
title: Verwalten von nicht vorrätigen Produkten in [!DNL Live Search]
description: Erfahren Sie, wie Sie nicht vorrätige Produkte in  [!DNL Live Search]  für Adobe Commerce verwalten. Konfigurieren Sie die Inventaranzeige, den Lagerfilter und die GraphQL-API-Filterung.
feature: Services, Search
role: Admin, Developer
level: Intermediate
source-git-commit: bc8f35434c9f01f1a920745fe42617df2003ca60
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Verwalten von nicht vorrätigen Produkten

Sie können steuern, wie nicht vorrätige Produkte in [!DNL Live Search] Such- und Kategorieergebnissen angezeigt werden, indem Sie die Inventarkonfiguration, Abfragezeitfilter und optionale Backend-Feature-Flags verwenden. Diese Optionen haben wichtige Einschränkungen, die in diesem Thema erläutert werden.

## Stock-Statusfilter

Das Adobe Commerce Stock-Attribut `quantity_and_stock_status` wird nicht als Facette unterstützt und wird nicht im Dialogfeld &quot;**[!UICONTROL Add Facet]**&quot; angezeigt. [!DNL Live Search] stellt jedoch ein `inStock` bereit, das Sie zum Zeitpunkt der Abfrage als Filter verwenden können.

## Nicht vorrätige Produkte ausblenden

Verwenden Sie einen der folgenden Ansätze, um nicht vorrätige Produkte auszublenden.

### Commerce-Konfiguration

&#x200B;1. Navigieren Sie *Admin* zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Catalog]**>**[!UICONTROL Inventory]**.

&#x200B;1. Setzen Sie **[!UICONTROL Display Out of Stock Products]** auf **[!UICONTROL No]**.

1. Klicken Sie auf **[!UICONTROL Save Config]**.

Wenn **[!UICONTROL Display Out of Stock Products]** auf `No` gesetzt ist, fügt [!DNL Live Search] über das PLP-Widget `inStock = 'no` zu den Storefront-Abfragen hinzu, damit nicht vorrätige Produkte nicht zurückgegeben werden.

### API-Filter

Wenn Sie die [!DNL Live Search]-API direkt aufrufen (GraphQL oder REST), filtern Sie nicht vorrätige Produkte explizit, z. B.:

```graphql
query productSearchInStockOnly {
  productSearch(
    phrase: ""
    filter: [
      { attribute: "inStock", eq: "true" }
    ]
  ) {
    total_count
    items {
      productView {
        sku
        name
        inStock
      }
    }
  }
}
```

Verwenden Sie diesen Ansatz, wenn Sie die Anfrage nicht über das [Live Search PLP Widget) &#x200B;](plp-styling.md).

### Nicht vorrätige Ergebnisse nach Lagerbestand anzeigen

Um nicht vorrätige Produkte im Ergebnissatz, aber bei der Sortierung nach Relevanz immer nach vorrätigen Produkten zu behalten, kann Adobe eine interne Feature Flag für Ihre Umgebung aktivieren.

- Dieses Feature Flag wird nicht in der Admin-Benutzeroberfläche von [!DNL Live Search] angezeigt.
- Um diese anzufordern, [kontaktieren Sie den Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide){target="_blank"}Support und verweisen Sie auf die Funktion, um nicht vorrätige Produkte an das Ende der Suchergebnisse zu verschieben.

>[!NOTE]
>
>Nachdem das Flag aktiviert wurde, werden alle verbleibenden nicht vorrätigen Produkte im Ergebnissatz beim Sortieren nach „Relevanz *nach unten*. Andere Sortierreihenfolgen (z. B. *Preis* oder *Produktname*) sind davon nicht betroffen.

### Merchandising-Regeln und -Lager suchen

Regeln für Such-Merchandising sind abfragebasiert und zielen auf einzelne Produkte ab, nicht auf ganze Gruppen nach Lagerstatus oder Facettenwert:

- Regelbedingungen hängen nur vom Suchbegriff des Käufers ab (`Query is`, `Query contains`, `Query starts with`, `Query ends with`).
- Regelereignisse (Verstärken, Begraben, Anheften, Ausblenden) gelten für eine SKU pro Ereignis.

Aufgrund dieser Einschränkungen:

- Sie können keine Regel erstellen, die alle nicht vorrätigen Produkte allein auf Grundlage des Lagerstatus vergräbt oder ausblendet.
- Sie können bestimmte SKUs, die Sie als Ereignisse in einer Regel hinzufügen, manuell ausblenden oder begraben (mit einer Beschränkung von 50 Regeln und 25 Ereignissen pro Regel).

Um nicht vorrätige Produkte im gesamten Katalog auszublenden oder zu priorisieren, verwenden Sie die in diesem Thema beschriebene Inventarkonfiguration und den `inStock`-Filter (und das optionale Feature Flag) anstelle der Merchandising-Suchregeln.

>[!MORELIKETHIS]
>
> - [Merchandising-Regeln suchen](rules.md)
> - [Globale Inventory management-Optionen konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/configuration)
