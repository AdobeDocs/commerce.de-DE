---
title: Erfassen von Commerce-Daten mithilfe von Adobe Experience Platform Tags
description: Erfahren Sie, wie Sie Commerce-Daten mithilfe von Adobe Experience Platform-Tags erfassen.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '2563'
ht-degree: 0%

---

# Erfassen von Commerce-Daten mithilfe von Adobe Experience Platform Tags

Sie können die [!DNL Data Connection]-Erweiterung zwar verwenden, um Storefront-Ereignisse zu veröffentlichen und zu abonnieren, einige Händler verwenden jedoch möglicherweise bereits eine Datenerfassungslösung, z. B. die [Adobe Experience Platform-Tags](https://experienceleague.adobe.com/docs/platform-learn/data-collection/tags/create-a-property.html?lang=de). Für diese Händler bietet Adobe Commerce in der [!DNL Data Connection]-Erweiterung eine Veröffentlichungsoption, die die Adobe Commerce Event SDK verwendet.

Datenfluss ![[!DNL Data Connection] Erweiterung](assets/tags-data-flow.png)
Datenfluss der _[!DNL Data Connection]mit Tags_

In diesem Abschnitt erfahren Sie, wie Sie die von der [!DNL Data Connection] bereitgestellten Storefront-Ereigniswerte der bereits verwendeten Adobe Experience Platform Tags-Lösung zuordnen.

## Erfassen von Ereignisdaten aus Adobe Commerce

So erfassen Sie Commerce-Ereignisdaten:

- Installieren Sie [Adobe Commerce Events SDK](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-sdk). Informationen zu PHP-Storefronts finden Sie unter [install](install.md)-Thema. Informationen zu PWA Studio-Storefronts finden Sie im [PWA Studio-Handbuch](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/).

  >[!NOTE]
  >
  > **&#x200B;**&#x200B;nicht[konfigurieren](connect-data.md) die Organisations-ID und die Datenstrom-ID.

## Zuordnen von Commerce-Storefront-Daten zu Adobe Experience Platform

Um Daten einer Commerce-Storefront Adobe Experience Platform zuzuordnen, konfigurieren und installieren Sie Folgendes in Adobe Experience Platform Tags:

1. [Richten Sie eine Tag-Eigenschaft &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=de) der Datenerfassung in Adobe Experience Platform ein.

1. Wählen **unter** die Option **Erweiterungen** aus und installieren und konfigurieren Sie die folgenden Erweiterungen:

   - [Adobe Client-Datenschicht](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=de)

   - [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html?lang=de)

1. [Tag veröffentlichen](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=de) in Ihrer Entwicklungsumgebung.

1. Gehen Sie wie **folgt vor** um Datenelemente und Regeln für bestimmte Ereignisse zu konfigurieren.

### Ereignis-Mapping

Da sich die Datenerfassung mithilfe von Tags von der Verwendung der Adobe Commerce Event SDK unterscheidet, ist es wichtig, die in beiden Frameworks verwendeten entsprechenden Begriffe zu verstehen.

| Adobe Experience Platform Tags-Begriff | Adobe Commerce Event SDK Begriff |
|---|---|
| _Datenelemente_ | Kontext |
| _Regeln_ | Ereignis |
|  | _Regelbedingungen_ - Ereignis-Listener (von ACDL)<br><br>_Regelaktionen_ - Ereignis-Handler (an Adobe Experience Platform senden) |

Wenn Sie die Datenelemente und Regeln in Adobe Experience Platform Tags mit Adobe Commerce-spezifischen Ereignisdaten aktualisieren, werden Sie einige allgemeine Schritte ausführen.

Fügen wir beispielsweise das Adobe Commerce-`signOut`-Ereignis zu Adobe Experience Platform-Tags hinzu. Die folgenden Schritte beschreiben mit Ausnahme der von Ihnen festgelegten spezifischen Werte, wie [Datenelemente](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html?lang=de#data-element) und [Regeln](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html?lang=de#create-a-rule) hinzugefügt werden. Diese gelten für alle Adobe Commerce-Ereignisse, die Sie Tags hinzufügen.

1. Erstellen Sie ein Datenelement:

   ![Neues Datenelement erstellen](assets/create-new-data-elements.png)
   _Neues Datenelement erstellen_

1. Legen Sie **Name** auf `sign out` fest.

1. Legen **Erweiterung** auf `Adobe Experience Platform Web SDK` fest.

1. Setzen **Datenelementtyp** auf `XDM object`.

1. Wählen Sie die **Sandbox** und **Schema** aus, die Sie aktualisieren möchten.

1. Legen **unter** > **abmelden** den **Wert** in **Besucher-Abmeldung** auf `1` fest.

   ![Abmeldewert aktualisieren](assets/signout-value.png)
   _Abmeldewert aktualisieren_

1. Wählen Sie **Speichern** aus.

1. Erstellen Sie eine Regel:

   ![Neue Regel erstellen](assets/create-new-rule.png)
   _Neue Regel erstellen_

1. Wählen **Hinzufügen** unter **EREIGNISSE** aus.

1. Legen **Erweiterung** auf `Adobe Client Data Layer` fest.

1. Legen Sie **Ereignistyp** auf `Data Pushed` fest.

1. Wählen Sie **Spezifisches Ereignis** aus und setzen Sie den **Ereignis/Schlüssel für die Registrierung** auf `sign-out`.

1. Wählen **Änderungen beibehalten**, um die neue Regel zu speichern.

1. Fügen Sie eine Aktion hinzu.

1. Legen **Erweiterung** auf `Adobe Experience Platform Web SDK` fest.

1. Legen Sie **Aktionstyp** auf `Send Event` fest.

1. Legen Sie **instance** auf `Alloy` fest.

1. Legen Sie **type** auf `userAccount.logout` fest.

1. Legen Sie **XDM-Daten** auf `%sign out%` fest.

1. Klicken Sie **Speichern**.

   Sie haben ein Datenelement in Ihrem Schema für das `signOut` von Adobe Commerce erstellt. Außerdem haben Sie eine Regel mit einer bestimmten Aktion erstellt, die auftreten soll, wenn dieses Ereignis in der Adobe Commerce-Storefront ausgelöst wird.

Wiederholen Sie die obigen Schritte in Tags für jedes der unten beschriebenen Adobe Commerce-Ereignisse.

## Verfügbare Ereignisse

Ordnen Sie die Adobe Commerce-Ereignisse jedem der folgenden Ereignisse Ihrem XDM zu, indem Sie die oben genannten Schritte ausführen.

- [`signOut`](#signout)
- [`signIn`](#signin)
- [`createAccount`](#createaccount)
- [`editAccount`](#editaccount)
- [`pageView`](#pageview)
- [`productView`](#productview)
- [`searchRequestSent`](#searchrequestsent)
- [`searchResponseReceived`](#searchresponsereceived)
- [`addToCart`](#addtocart)
- [`openCart`](#opencart)
- [`viewCart`](#viewcart)
- [`removeFromCart`](#removefromcart)
- [`initiativeCheckout`](#initiatecheckout)
- [`placeOrder`](#placeorder)

### Abmelden

Wird ausgelöst, wenn ein Käufer versucht, sich abzumelden.

#### Datenelemente

Erstellen Sie das folgende Datenelement:

1. Abmelden:

   - **Name**: `Sign out`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `userAccount` > `logout`
   - **Besucher-Abmeldung**: **Wert** = `1`

#### Regeln 

- **Name**: `Sign out`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `sign-out`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `userAccount.logout`
- **XDM-Daten**: `%sign-out%`

### Anmelden

Wird ausgelöst, wenn ein Käufer versucht, sich anzumelden.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Konto-E-Mail:

   - **Name**: `account email`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.emailAddress`

1. Kontotyp:

   - **Name**: `account type`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountType`

1. Konto-ID:

   - **Name**: `account id`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path***: `accountContext.accountId`

1. Anmelden:

   - **Name**: `sign in`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `person` > `accountID`
   - **Konto-ID**: **Wert** = `%account id%`
   - **Feldergruppe**: `person` > `accountType`
   - **Kontotyp**: **value** = `%account type%`
   - **Feldergruppe**: `person` > `personalEmailID`
   - **Persönliche E-Mail**: **Wert** = `%account email%`
   - **Feldergruppe**: `personalEmail` > `address`
   - **Adresse**: **Wert** = `%account email%`
   - **Feldergruppe**: `userAccount` > `login`
   - **Besucheranmeldung**: **Wert** = `1`

#### Regeln 

- **Name**: `sign in`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `sign-in`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `userAccount.login`
- **XDM-Daten**: `%sign in%`

### createAccount

Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu erstellen.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Konto-E-Mail:

   - **Name**: `account email`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.emailAddress`

1. Kontotyp:

   - **Name**: `account type`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountType`

1. Konto-ID:

   - **Name**: `account id`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountId`

1. Konto erstellen:

   - **Name**: `Create account`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `person` > `accountID`
   - **Konto-ID**: **Wert** = `%account id%`
   - **Feldergruppe**: `person` > `accountType`
   - **Kontotyp**: **value** = `%account type%`
   - **Feldergruppe**: `person` > `personalEmailID`
   - **Persönliche E-Mail**: **Wert** = `%account email%`
   - **Feldergruppe**: `personalEmail` > `address`
   - **Adresse**: **Wert** = `%account email%`
   - **Feldergruppe**: `userAccount` > `createProfile`
   - **Kontoprofil erstellen**: **Wert** = `1`

#### Regeln 

- **Name**: `Create account`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `create-account`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `userAccount.createProfile`
- **XDM-Daten**: `%create account%`

### Konto bearbeiten

Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu bearbeiten.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Konto-E-Mail:

   - **Name**: `account email`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.emailAddress`

1. Kontotyp:

   - **Name**: `account type`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountType`

1. Konto-ID:

   - **Name**: `account id`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountId`

1. Konto bearbeiten:

   - **Name**: `Edit account`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `person` > `accountID`
   - **Konto-ID**: **Wert** = `%account id%`
   - **Feldergruppe**: `person` > `accountType`
   - **Kontotyp**: **value** = `%account type%`
   - **Feldergruppe**: `person` > `personalEmailID`
   - **Persönliche E-Mail**: **Wert** = `%account email%`
   - **Feldergruppe**: `personalEmail` > `address`
   - **Adresse**: **Wert** = `%account email%`
   - **Feldergruppe**: `userAccount` > `updateProfile`
   - **Kontoprofil erstellen**: **Wert** = `1`

#### Regeln

- **Name**: `Edit account`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `edit-account`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `userAccount.updateProfile`
- **XDM-Daten**: `%edit account%`

### pageView

Wird ausgelöst, wenn eine beliebige Seite geladen wird.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Seitenname:

   - **Name**: `page name`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `pageContext.pageName`

#### Regeln 

- **Name**: `page view`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `page-view`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `web.webPageDetails.pageViews`
- **XDM-Daten**: `%page view%`

### productView

Wird ausgelöst, wenn eine Produktseite geladen wird.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Produktname:

   - **Name**: `product name`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.name`

1. Produkt-SKU:

   - **Name**: `product sku`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.sku`

1. Produktbild-URL:

   - **Name**: `product image`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.mainImageUrl`

1. Währung des Produkts:

   - **Name**: `product currency`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.currencyCode`

1. Währungscode:

   - **Name**: `currency code`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('product currency') || _satellite.getVar('storefront').storeViewCurrencyCode
   ```

1. Sonderpreis:

   - **Name**: `special price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.specialPrice`

1. Regulärer Preis:

   - **Name**: `regular price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.regularPrice`

1. Produktpreis:

   - **Name**: `product price`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price')
   ```

1. Produktansicht:

   - **Name**: `product view`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Wählen **Einzelne Elemente angeben** und klicken Sie auf die Schaltfläche **Element hinzufügen**. Da es sich bei dieser Ansicht um eine PDP handelt, können Sie sie mit einem einzelnen Element füllen.
   - **Feldergruppe**: `productListItems` > `name`
   - **name**: **value** = `%product name%`
   - **Feldergruppe**: `productListItems` > `SKU`
   - **SKU**: **value** = `%product sku%`
   - **Feldergruppe**: `productListItems` > `priceTotal`
   - **Gesamtpreis**: **Wert** = `%product price%`
   - **Feldergruppe**: `productListItems` > `currencyCode`
   - **Währungscode**: **Wert** = `%currency code%`
   - **Feldergruppe**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **value** = `%product image%`
   - **Feldergruppe**: `commerce` > `productViews` > `value`
   - **value**: **value** = `1`

#### Regeln 

- **Name**: `product view`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `product-page-view`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productViews`
- **XDM-Daten**: `%product view%`

### searchRequestSent

Ausgelöst durch Ereignisse im Pop-up „Suche während der Eingabe“ und durch Ereignisse auf Suchergebnisseiten.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Eingabe suchen

   - **Name**: `search input`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `searchInputContext.units[0]`

1. Eingabephrase suchen

   - **Name**: `search input phrase`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('search input').phrase;
   ```

1. Eingabesortierung suchen

   - **Name**: `search input sort`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const sortFromInput = searchInput ? searchInput.sort : [];
   const sort = sortFromInput.map((searchSort) => {
       return {
           attribute: searchSort.attribute,
           order: searchSort.direction,
       };
   });
   return sort;
   ```

1. Eingabefilter suchen

   - **Name**: `search input filters`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const filtersFromInput = searchInput ? searchInput.filter : [];
   const filters = filtersFromInput.map(
       (searchFilter) => {
           let value = [];
           let isRange = false;
           if (searchFilter.eq) {
               value.push(searchFilter.eq);
           } else if (searchFilter.in) {
               value = searchFilter.in;
           } else if (searchFilter.range) {
               isRange = true;
               value.push(String(searchFilter.range.from));
               value.push(String(searchFilter.range.to));
           }
           return {
               attribute: searchFilter.attribute,
               value,
               isRange,
           };
       }
   );
   
   return filters;
   ```

1. Suchanfrage:

   - **Name**: `search request`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `siteSearch` > `phrase`
   - **value**: Noch nicht verfügbar
   - **Feldergruppe**: `siteSearch` > `sort`. Wählen Sie **Gesamtes Objekt bereitstellen** aus.
   - **Feldergruppe**: `siteSearch` > `filter`. Wählen Sie **Gesamtes Objekt bereitstellen** aus.
   - **Feldergruppe**: `searchRequest` > `id`
   - **Eindeutige Kennung**: **Wert** = `%search request ID%`
   - **Feldergruppe**: `searchRequest` > `value`
   - **value**: **value** = `1`

#### Regeln 

- **Name**: `search request sent`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `search-request-sent`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `searchRequest`
- **XDM-Daten**: `%search request%`

### searchResponseReceived

Wird ausgelöst, wenn die Live-Suche Ergebnisse für das Pop-up „Suche während der Eingabe“ oder die Suchergebnisseite zurückgibt.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Suchergebnisse:

   - **Name**: `search results`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `searchResultsContext.units[0]`

1. Anzahl der Produkte im Suchergebnis:

   - **Name**: `search result number of products`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('search result').products.length;
   ```

1. Produkte für Suchergebnisse:

   - **Name**: `search result products`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const productsFromResult = searchResult.products ? searchResult.products : [];
   const products = productsFromResult.map(
       (product) => {
           return { SKU: product.sku, name: product.name };
       }
   );
   return products;
   ```

1. Vorschläge für Suchergebnisse:

   - **Name**: `search result products`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const suggestionsFromResult = searchResult.suggestions ? searchResult.suggestions : [];
   const suggestions = suggestionsFromResult.map((suggestion) => suggestion.suggestion);
   return suggestions;
   ```

1. Produktbild-URL:

   - **Name**: `product image`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.mainImageUrl`

1. Suchantwort:

   - **Name**: `search response`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `siteSearch` > `suggestions`. Wählen Sie **Gesamtes Objekt bereitstellen** aus.
   - **Datenelement**: `%search result suggestions%`
   - **Feldergruppe**: `siteSearch` > `numberOfResults`
   - **value**: `%search result number of products%`
   - **Feldergruppe**: `productListItems`. Wählen Sie **Gesamtes Objekt bereitstellen** aus.
   - **Feldergruppe**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **value** = `%product image%`
   - **Datenelement**: `%search result products%`
   - **Feldergruppe**: `searchResponse` > `id`
   - **Eindeutige Kennung**: **Wert** = `%search response ID%`
   - **Feldergruppe**: `searchResponse` > `value`
   - **value**: **value** = `1`

#### Regeln 

- **Name**: `search response received`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `search-response-received`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `searchResponse`
- **XDM-Daten**: `%search response%`

### addToCart

Wird ausgelöst, wenn ein Produkt zum Warenkorb hinzugefügt wird oder jedes Mal, wenn die Menge eines Produkts im Warenkorb erhöht wird.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Produktname:

   - **Name**: `product name`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.name`

1. Produkt-SKU:

   - **Name**: `product sku`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.sku`

1. Währungscode:

   - **Name**: `currency code`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.currencyCode`

1. Sonderpreis für das Produkt:

   - **Name**: `product special price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.specialPrice`

1. Produktbild-URL:

   - **Name**: `product image`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.mainImageUrl`

1. Regulärer Produktpreis:

   - **Name**: `product regular price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.regularPrice`

1. Produkt  Preis:

   - **Name**: `product price`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. Warenkorb:

   - **Name**: `cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Zum Warenkorb hinzufügen:

   - **Name**: `add to cart`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Wählen **Einzelne Elemente angeben** und klicken Sie auf die Schaltfläche **Element hinzufügen**. Da es sich bei dieser Ansicht um eine PDP handelt, können Sie sie mit einem einzelnen Element füllen.
   - **Feldergruppe**: `productListItems` > `name`
   - **name**: **value** = `%product name%`
   - **Feldergruppe**: `productListItems` > `SKU`
   - **SKU**: **value** = `%product sku%`
   - **Feldergruppe**: `productListItems` > `priceTotal`
   - **Gesamtpreis**: **Wert** = `%product price%`
   - **Feldergruppe**: `productListItems` > `currencyCode`
   - **Feldergruppe**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **value** = `%product image%`
   - **Währungscode**: **Wert** = `%currency code%`
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `commerce` > `productListAdds` > `value`
   - **value**: **value** = `1`

#### Regeln 

- **Name**: `add to cart`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `add-to-cart`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productListAdds`
- **XDM-Daten**: `%add to cart%`

### openCart

Wird ausgelöst, wenn ein neuer Warenkorb erstellt wird, was passiert, wenn ein Produkt zu einem leeren Warenkorb hinzugefügt wird.

#### Datenelemente

Erstellen Sie das folgende Datenelement:

1. Warenkorb öffnen:

   - **Name**: `open cart`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `commerce` > `productListOpens` > `value`
   - **value**: **value** = `1`
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `productListItems`. `productListItems` können mehrere Elemente vorab berechnet werden. Wählen Sie **productListItems** > **Gesamtes Array bereitstellen** aus.

#### Regeln 

- **Name**: `open cart`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `open-cart`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productListOpens`
- **XDM-Daten**: `%open cart%`

### Warenkorb anzeigen

Wird ausgelöst, wenn eine beliebige Warenkorbseite geladen wird.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Storefront:

   - **Name**: `storefront`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `storefrontInstanceContext`

1. Produktbild-URL:

   - **Name**: `product image`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.mainImageUrl`

   1. Warenkorb:

   - **Name**: `cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Elemente der Produktliste:

   - **Name**: `product list items:`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Warenkorb anzeigen:

   - **Name**: `view cart`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. `productListItems` kann es mehrere Elemente geben, die vorberechnet werden. Wählen Sie **productListItems** > **Gesamtes Array füllen** aus.
   - **Datenelement**: `%product list items%`
   - **Feldergruppe**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **value** = `%product image%`
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `commerce` > `productListViews` > `value`
   - **value**: **value** = `1`

#### Regeln

- **Name**: `view cart`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `shopping-cart-view`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productListViews`
- **XDM-Daten**: `%view cart%`

### removeFromCart

Wird ausgelöst, wenn ein Produkt aus einem Warenkorb entfernt wird oder jedes Mal, wenn die Menge eines Produkts im Warenkorb verringert wird.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Produktname:

   - **Name**: `product name`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.name`

1. Produkt-SKU:

   - **Name**: `product sku`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.sku`

1. Währungscode:

   - **Name**: `currency code`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.currencyCode`

1. Sonderpreis für das Produkt:

   - **Name**: `product special price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.specialPrice`

1. Regulärer Produktpreis:

   - **Name**: `product regular price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.regularPrice`

1. Produkt  Preis:

   - **Name**: `product price`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. Warenkorb:

   - **Name**: `cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Aus dem Warenkorb entfernen:

   - **Name**: `remove from cart`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Wählen **Einzelne Elemente angeben** und klicken Sie auf die Schaltfläche **Element hinzufügen**. Da es sich bei dieser Ansicht um eine PDP handelt, können Sie sie mit einem einzelnen Element füllen.
   - **Feldergruppe**: `productListItems` > `name`
   - **name**: **value** = `%product name%`
   - **Feldergruppe**: `productListItems` > `SKU`
   - **SKU**: **value** = `%product sku%`
   - **Feldergruppe**: `productListItems` > `priceTotal`
   - **Gesamtpreis**: **Wert** = `%product price%`
   - **Feldergruppe**: `productListItems` > `currencyCode`
   - **Währungscode**: **Wert** = `%currency code%`
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `commerce` > `productListRemovals` > `value`
   - **value**: **value** = `1`

#### Regeln 

- **Name**: `remove from cart`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `remove-from-cart`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productListRemovals`
- **XDM-Daten**: `%remove from cart%`

### initiateCheckout

Wird ausgelöst, wenn der Käufer auf eine Checkout-Schaltfläche klickt.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Storefront:

   - **Name**: `storefront`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `storefrontInstanceContext`

1. Produktbild-URL:

   - **Name**: `product image`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.mainImageUrl`

1. Warenkorb:

   - **Name**: `cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Elemente der Produktliste:

   - **Name**: `product list items`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Checkout starten:

   - **Name**: `initiate checkout`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. `productListItems` kann es mehrere Elemente geben, die vorberechnet werden. Wählen Sie **productListItems** > **Gesamtes Array füllen** aus.
   - **Datenelement**: `%product list items%`
   - **Feldergruppe**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **value** = `%product image%`
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `commerce` > `checkouts` > `value`
   - **value**: **value** = `1`

#### Regeln 

- **Name**: `initiate checkout`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `initiate-checkout`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.checkouts`
- **XDM-Daten**: `%initiate checkout%`

### placeOrder

Wird ausgelöst, wenn der Käufer eine Bestellung aufgibt.

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Konto-E-Mail:

   - **Name**: `account email`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.emailAddress`

1. Storefront:

   - **Name**: `storefront`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `storefrontInstanceContext`

1. Produktbild-URL:

   - **Name**: `product image`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.mainImageUrl`

1. Warenkorb:

   - **Name**: `cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Bestellung:

   - **Name**: `order`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `orderContext`

1. Commerce-Bestellung:

   - **Name**: `commerce order`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const order = _satellite.getVar('order');
   const storefront = _satellite.getVar('storefront');
   
   if (order.payments && order.payments.length) {
       payments = order.payments.map(payment => {
           return {
               paymentAmount: payment.total,
               paymentType: payment.paymentMethodCode,
               transactionID: order.orderId.toString(),
           };
       });
   } else {
       payments = [
           {
               paymentAmount: order.grandTotal,
               paymentType: order.paymentMethodCode,
               transactionID: order.orderId.toString(),
           },
       ];
   }
   
   return {
       purchaseID: order.orderId.toString(),
       currencyCode: storefront.storeViewCurrencyCode,
       payments,
   };
   ```

1. Bestellversand:

   - **Name**: `order shipping`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const order = _satellite.getVar('order');
   return {
       shippingMethod: order.shipping.shippingMethod,
       shippingAmount: order.shipping.shippingAmount || 0,
   }
   ```

1. Promotion-ID:

   - **Name**: `promotion id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('order').appliedCouponCode
   ```

1. Elemente der Produktliste:

   - **Name**: `product list items`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Bestellung aufgeben

   - **Name**: `place order`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. `productListItems` kann es mehrere Elemente geben, die vorberechnet werden. Wählen Sie **productListItems** > **Gesamtes Array füllen** aus.
   - **Datenelement**: `%product list items%`
   - **Feldergruppe**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **value** = `%product image%`
   - **Feldergruppe**: `commerce` > `order`
   - **Eindeutige Kennung**: **Wert** = `%commerce order%`
   - **Feldergruppe**: `commerce` > `shipping`
   - **Eindeutige Kennung**: **Wert** = `%order shipping%`
   - **Feldergruppe**: `commerce` > `promotionID`
   - **Promotion-ID**: **value** = `%promotion id%`
   - **Feldergruppe**: `commerce` > `purchases` > `value`
   - **value**: **value** = `1`
   - **Persönliche E-Mail**: **Wert** = `%account email%`
   - **Feldergruppe**: `personalEmail` > `address`
   - **Adresse**: **Wert** = `%account email%`

#### Regeln 

- **Name**: `place order`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Spezifisches Ereignis**: `place-order`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.order`
- **XDM-Daten**: `%place order%`

## Festlegen der Identität in Storefront-Ereignissen

Storefront-Ereignisse enthalten Profilinformationen, die auf den Feldern `personalEmail` (für Kontoereignisse) und `identityMap` (für alle anderen Storefront-Ereignisse) basieren. Die [!DNL Data Connection]-Erweiterung verknüpft und generiert Profile, die auf diesen beiden Feldern basieren. Für jedes Feld sind jedoch verschiedene Schritte zum Erstellen von Profilen erforderlich:

>[!NOTE]
>
>Wenn Sie eine frühere Einrichtung haben, die sich auf verschiedene Felder stützt, können Sie diese weiterhin verwenden.

- `personalEmail` - Gilt nur für Kontoereignisse. Führen Sie die oben beschriebenen Schritte, Regeln und [&#x200B; aus](#createaccount)
- `identityMap` - Gilt für alle anderen Storefront-Ereignisse. Siehe folgendes Beispiel.

### Beispiel

Die folgenden Schritte zeigen, wie Sie ein `pageView`-Ereignis mit `identityMap` in [!DNL Data Connection] Erweiterung konfigurieren:

1. Konfigurieren des Datenelements mit benutzerdefiniertem Code für ECID:

   ![Konfigurieren des Datenelements mit benutzerdefiniertem Code](assets/set-custom-code-ecid.png)
   _Konfigurieren des Datenelements mit benutzerdefiniertem Code_

1. Wählen Sie [!UICONTROL Open Editor] aus und fügen Sie den folgenden benutzerdefinierten Code hinzu:

   ```javascript
   return alloy("getIdentity").then((result) => {
       var identityMap = {
           ECID: [
           {
               id: ecid,
               primary: true
           }
           ],
           email: [
           {
               id: email,
               primary: false
           }
           ]
       };
     _satelite.setVar("identityMap", identityMap);
   });
   ```

1. Aktualisieren Sie das XDM-Schema mit `identityMap` als ECID:

   ![identityMap als ECID festlegen](assets/identity-map-data-element.png)
   _identityMap als ECID festlegen_

1. Definieren Sie Regelaktionen, die ECID abrufen:

   ![ECID abrufen](assets/rule-retrieve-ecid.png)
   _ECID abrufen_

## Festlegen der Identität in Back-Office-Ereignissen

Im Gegensatz zu Storefront-Ereignissen, die ECID verwenden, um Profilinformationen zu identifizieren und zu verknüpfen, sind Backoffice-Ereignisdaten SaaS-basiert und daher ist keine ECID verfügbar. Bei Back-Office-Ereignissen müssen Sie E-Mails verwenden, um Käufer eindeutig zu identifizieren. In diesem Abschnitt erfahren Sie, wie Sie Backoffice-Ereignisdaten per E-Mail mit einer ECID verknüpfen.

1. Erstellen Sie ein Identitätszuordnungselement.

   ![Identitätszuordnung für Backoffice](assets/custom-code-backoffice.png)
   _Back-Office-Identitätszuordnung erstellen_

1. Wählen Sie [!UICONTROL Open Editor] aus und fügen Sie den folgenden benutzerdefinierten Code hinzu:

```javascript
const IdentityMap = {
  "ECID": [
    {
      id:  _satellite.getVar('ECID'),
      primary: true,
    },
  ],
};
 
if (_satellite.getVar('account email')) {
    IdentityMap.email = [
        {
            id: _satellite.getVar('account email'),
            primary: false,
        },
    ];
}
return IdentityMap;
```

1. Fügen Sie jedes `identityMap` Feld dieses neue Element hinzu.

   ![Aktualisieren jeder identityMap](assets/add-element-back-office.png)
   _Aktualisieren jeder identityMap_

## Einverständnis wird festgelegt

Wenn Sie die [!DNL Data Connection]-Erweiterung in Adobe Commerce installieren, ist das Einverständnis zur Datenerfassung standardmäßig aktiviert. Das Opt-out wird über das [`mg_dnt`-Cookie verwaltet](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=de). Sie können die hier beschriebenen Schritte ausführen, wenn Sie `mg_dnt` zur Einverständnisverwaltung verwenden. Die [Dokumentation zu Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=de) bietet mehrere zusätzliche Optionen zum Verwalten des Einverständnisses.

1. Erstellen Sie ein **Core Custom Code**-Datenelement (`%do not track cookie%`) für das `mg_dnt` Cookie:

   ![Erstellen verfolgt kein Datenelement](assets/element-dnt-cookie.png)
   _Erstellen verfolgt kein Datenelement_

1. Erstellen Sie ein **Core Custom Code**-Datenelement (`%consent%`), das `out` zurückgibt, wenn das Cookie gesetzt ist, und andernfalls `in`:

   ![Einverständnisdatenelement erstellen](assets/element-consent-dnt-cookie.png)
   _Einverständnisdatenelement erstellen_

1. Konfigurieren der Adobe Experience Platform Web SDK-Erweiterung mit `%consent%` Datenelement:

   ![Aktualisieren von SDK mit Einverständnis](assets/config-sdk-consent.png)
   _Aktualisieren von SDK mit Einverständnis_

## Warnungen

- Wenn Sie zum Deaktivieren der Experience Platform-Erfassung keine Schritte ausführen, werden Ereignisse doppelt gezählt
- Das Nicht-Einrichten von Zuordnungen/Ereignissen wie in diesem Thema beschrieben kann Auswirkungen auf Adobe Analytics Boards haben
- Sie können Target nicht über die [!DNL Data Connection]-Erweiterung einrichten, wenn die Datenerfassung deaktiviert ist
