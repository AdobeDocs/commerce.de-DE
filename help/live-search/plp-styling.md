---
title: Widget „Produktlistenseite“
description: Aktivieren und Formatieren des  [!DNL Live Search Product Listing Page Widget]
exl-id: 50ba8046-869a-4071-b3a3-a6392544c07b
source-git-commit: c0a6f038d2528a67da6f1bb4f5e5bb140afc7dfc
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Widget „Produktlistenseite“

Das [!DNL Live Search Product Listing Page Widget] (PLP) verwendet die Commerce Services-Plattform, um eine leistungsstarke, durchsuchbare und facettenfähige Produktlistenseite bereitzustellen. In diesem Thema wird beschrieben, wie Sie das PLP-Widget aktivieren und gestalten.

## Aktivieren des PLP-Widgets

Wenn der [!DNL Live Search]-Service installiert ist, wird die Standardsuchfunktion automatisch in [!DNL Live Search] konvertiert.

Das [!DNL Live Search] PLP-Widget ist bei Neuinstallationen standardmäßig aktiviert.

Wenn Sie ein Upgrade von [!DNL Live Search] durchführen und das PLP-Widget bereits deaktiviert wurde, wird es so bleiben.

>[!NOTE]
>
>Wenn Sie vom veralteten Suchadapter migrieren, finden Sie im [Migrationshandbuch](migrate-to-plp.md) detaillierte Anleitungen zu Szenarien, Voraussetzungen und schrittweise Anweisungen.

Aktivieren des PLP-Widgets:

1. Wechseln Sie in Ihrem Adobe Commerce-Administrator zu Stores → Einstellungen → Konfiguration.
1. Klicken Sie in der linken Navigation auf **[!UICONTROL Live Search]** > **[!UICONTROL Storefront Features]**.
1. Klicken Sie auf den Abschnitt [!UICONTROL Storefront Features] .
1. [!UICONTROL Enable Product Listing Widget] = Ja
1. Konfiguration speichern
1. Leeren Sie den Cache, wenn Sie dazu aufgefordert werden (navigieren Sie zu System > Tools > Cache-Verwaltung > [!UICONTROL Flush Magento Cache]).

>[!IMPORTANT]
>
>Wenn die [!DNL Live Search Product Listing Page Widget] aktiviert ist, kann die Sortierreihenfolge auf einer Produktlistenseite nicht geändert werden.

## Widget-Funktionen

Das PLP-Widget bietet die folgenden vordefinierten Funktionen:

- Schaltflächen zum Warenkorb hinzufügen - Nur für einfache Produkte verfügbar.
- Mehrere Bilder pro Produkt - Das Bild kann sich ändern, wenn für ein konfigurierbares Produkt eine andere Farbe ausgewählt wird.
- Unterstützung für Farbfelder - Beachten Sie, dass das Farbattribut `color` geschrieben werden muss, damit der Code ordnungsgemäß validiert werden kann.

### Anpassen des Widgets

Zusätzlich zu den vordefinierten Funktionen des PLP-Widgets können Sie das Widget weiter anpassen, um die folgenden Funktionen einzuschließen:

- Filtern nach Attributen
- Unterstützung mehrerer Sprachen
- Preisregler

Informationen zum Anpassen des PLP-Widgets für die oben genannten Funktionen finden Sie in der `storefront-product-listing-page` Readme-Datei im folgenden [Repository](https://github.com/adobe/storefront-product-listing-page/). Die Readme-Datei in diesem Repository enthält ein Beispiel für die Anpassung des PLP-Widgets und die Bereitstellung dieser Anpassungen auf Ihrer Site.

>[!WARNING]
>
>Wenn Sie das PLP-Widget mithilfe des im Repository verfügbaren Codes anpassen, sind Sie für die Wartung und alle erforderlichen Aktualisierungen verantwortlich. Alle neuen PLP-Widget-Funktionen, die Adobe veröffentlicht, sind möglicherweise nicht mit Ihrer benutzerdefinierten Implementierung kompatibel.

## Beispiel für einen Stil

Sie können das Erscheinungsbild des PLP-Widgets mit (CSS) an Ihre [&#x200B; anpassen](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Elemente mit benutzerdefinierten Klassen in einem Adobe Commerce-Design werden nicht vererbt. Diese Elemente müssen durch ihre spezifische Klasse angesprochen werden, damit sie mit den benutzerdefinierten Klassen übereinstimmen. Primäre Aktionsklassen funktionieren nicht auf einer Widget-Schaltfläche. Generische zielgerichtete Elemente innerhalb des CSS werden übernommen. `button` gilt für Widget-Schaltflächen.

Die hervorgehobenen DIVs enthalten die `ds-sdk-product-item__product-name` der Zielklasse.

![Paginierung](assets/plp-css-example.png)

Passen Sie den Produktnamen an, indem Sie eine Regel hinzufügen, um sie in Großbuchstaben zu ändern.

```css
.ds-sdk-product-item__product-name {
 text-transform: uppercase;
}
```

![Paginierung](assets/plp-css-example-after.png)

## CSS-Klassen

### Produktliste

- `.ds-sdk-product-list`: Äußeres div
- `.ds-sdk-product-list__grid`: Innerer div

![Paginierung](assets/plp-css-product-list.png)

#### Seitenumbruch für Produktliste

- `.ds-plp-pagination`

![Paginierung](assets/plp-css-pagination.png)

- `.ds-plp-pagination_item`

![Paginierungselement](assets/plp-css-pagination-item.png)

- `.ds-plp-pagination_item--current`

![Paginierung des aktuellen Elements](assets/plp-css-pagination-item-current.png)

### Widgets

- `.ds-widgets`: Äußeres div
- `.ds-widgets__actions`: Innerer div auf der linken Seite
- `.ds-widgets__results`: Rechter innerer Div

![Widget-Ergebnisse](assets/plp-css-widgets.png)

### Dropdown sortieren

- `.ds-sdk-sort-dropdown`

![Dropdown sortieren](assets/plp-css-dropdown.png)

- `.ds-sdk-sort-dropdown__button`

![Dropdown-Schaltfläche](assets/plp-css-dropdown-button.png)

- `.ds-sdk-sort-dropdown__items`

![Dropdown-Elemente](assets/plp-css-dropdown-items.png)

- `.ds-sdk-sort-dropdown__items--item`

![Dropdown-Element](assets/plp-css-dropdown-item.png)

- `.ds-sdk-sort-dropdown__items--item-selected`

![Dropdown-Element ausgewählt](assets/plp-css-dropdown-selected.png)

- `.ds-sdk-sort-dropdown__items--item-active`

![Dropdown-Auswahl aktiv](assets/plp-css-dropdown-active.png)

### Facetten

- `.ds-plp-facets`
- `.ds-plp-facets__header`
- `.ds-plp-facets__header_title`
- `.ds-plp-facets__header__clear-all`

![Facetten-Header-Titel](assets/plp-css-facets-title-clear.png){width="350"}

- `.ds-plp-facets__pills`
- `.ds-sdk-pill`

![Facettenpille](assets/plp-css-facets-pill.png){width="350"}

- `.ds-sdk-pill__label`
- `.ds-sdk-pill__cta`

![Facettenbezeichnung](assets/plp-css-pill-label-cta.png){width="350"}

- `.ds-plp-facets__list`

![Facettenliste](assets/plp-css-facets-list.png){width="350"}

- `.ds-sdk-input`
- `.ds-sdk-input__label`
- `.ds-sdk-product-item__product-swatch-group`
- `ds-sdk-product-item__product-swatch-item`
- `.ds-sdk-input_fieldset_show-more`

![Eingabe](assets/plp-css-sdk-input.png)

- `.ds-sdk-labelled-input`

![Beschriftte Eingabe](assets/plp-css-labelled-input.png)

- `.ds-sdk-labelled-input__input`
- `.ds-sdk-labelled-input__label`

![Beschriftung eingeben](assets/plp-css-labelled-input-label.png)

### Produktartikel

- `.ds-sdk-product-item`
- `.ds-sdk-product-item__image`
- `.ds-sdk-product-item__product-name`
- `.ds-sdk-product-item__product-options`
- `.ds-sdk-product-price`
   - `.ds-sdk-product-price--no-discount`
   - `.ds-sdk-product-price--grouped`
   - `.ds-sdk-product-price--bundle`
   - `.ds-sdk-product-price--discount`

![Produkt](assets/plp-css-product.png)

### Wird geladen

- `.ds-sdk-loading`
- `.ds-sdk-loading__spinner`
- `.ds-sdk-loading__spinner-label`

![Ladeanzeige](assets/plp-css-loading.png)

## Deaktivieren des PLP-Widgets

Deaktivieren des PLP-Widgets:

1. Gehen Sie zu **Stores** > Einstellungen > **Konfiguration** > **[!DNL Live Search]** > **Storefront-Funktionen** und setzen Sie **Produktlisten-Widgets aktivieren** auf „Nein“.
1. Wählen **Konfiguration speichern** um die Einstellung zu speichern.
