---
title: Verhaltensereignisse
description: Erfahren Sie, welche Daten jedes Verhaltensereignis erfasst.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '4516'
ht-degree: 0%

---

# [!DNL Data Connection] Verhaltensereignisse

Im Folgenden sind die Commerce-Verhaltensereignisse aufgeführt, die bei der Installation der [!DNL Data Connection] verfügbar sind. Die von diesen Ereignissen erfassten Daten werden an die Adobe Experience Platform gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) erstellen, um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt werden.

Zusätzlich zu den Daten, die die folgenden Ereignisse erfassen, erhalten Sie auch [andere Daten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) bereitgestellt von der Adobe Experience Platform Web SDK.

Die Verhaltensereignisse erfassen anonymisierte Verhaltensdaten von Ihren Kundinnen und Kunden, während sie Ihre Website durchsuchen. Sie können die von diesen Ereignissen erfassten Daten verwenden, um Werbeaktionen und Kampagnen für eine bestimmte Gruppe von Käufern zu erstellen.

>[!NOTE]
>
>Alle Verhaltensereignisse umfassen das Feld [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , das die E-Mail-Adresse des Käufers (sofern verfügbar) und die ECID enthält.

## Storefront-Ereignisse

Storefront-Ereignisse erfassen Daten aus den Interaktionen von Käufern auf der Website und umfassen Ereignisse wie [`addToCart`](#addtocart), [`pageView`](#pageview), [`createAccount`](#createaccount), [`editAccount`](#editaccount), [`startCheckout`](#startcheckout), [`completeCheckout`](#completecheckout), [`signIn`](#signin), [`signOut`](#signout) usw. Storefront-Ereignisse gelten nur für einfache und konfigurierbare Produkte.

### addToCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Produkt zum Warenkorb hinzugefügt oder die Menge eines Produkts im Warenkorb erhöht wird. | `commerce.productListAdds` |

#### Von addToCart erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListAdds` | Gibt an, ob ein Produkt zum Warenkorb hinzugefügt wurde. Der Wert `1` gibt an, dass ein Produkt hinzugefügt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### openCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein neuer Warenkorb erstellt wird, d. h. wenn ein Produkt zu einem leeren Warenkorb hinzugefügt wird. | `commerce.productListOpens` |

#### Von OpenCart erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListOpens` | Gibt an, ob ein Warenkorb erstellt wurde. Der Wert `1` gibt an, dass ein Warenkorb erstellt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### removeFromCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird jedes Mal ausgelöst, wenn ein Produkt entfernt oder die Menge eines Produkts im Warenkorb verringert wird. | `commerce.productListRemovals` |

#### Von removeFromCart erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListRemovals` | Gibt an, ob ein Produkt aus dem Warenkorb entfernt wurde. Der Wert `1` gibt an, dass ein Produkt aus dem Warenkorb entfernt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### shoppingCartView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine beliebige Warenkorbseite geladen wird. | `commerce.productListViews` |

#### Von „shoppingCartView“ erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListViews` | Zeigt an, ob eine Produktliste angezeigt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `commerce.order` | Enthält Informationen zur ausstehenden Bestellung für ein oder mehrere Produkte. |
| `commerce.order.discountAmount` | Gibt den Rabattbetrag an, der auf die gesamte Bestellung angewendet wurde. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### pageView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine beliebige Seite geladen wird. | `web.webpagedetails.pageViews` |

#### Von pageView erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `web.webPageDetails.pageViews` | Gibt an, ob eine Seite geladen wurde. Eine `value` von `1` zeigt an, dass die Seite geladen wurde. |
| `web.webPageDetails.URL` | Die normative oder übliche URL der Webseite. Dies kann die tatsächliche URL sein, die verwendet wird, um die Seite zu erreichen, und die mithilfe von `Web Link` aufgezeichnet wird. |
| `web.webPageDetails.name` | Der normative Name der Webseite. Dieser Name ist nicht unbedingt der Seitentitel oder direkt mit dem Seiteninhalt verknüpft, sondern wird verwendet, um die Seiten einer Site zu Klassifizierungszwecken zu organisieren. |
| `web.webReferrer.URL` | Die URL der Web-Seite, die ein Käufer besucht hat, bevor er auf einen Link zu Ihrer Site geklickt hat. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

### productPageView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Produktseite geladen wird. | `commerce.productViews` |

#### Von productPageView erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productViews` | Gibt an, ob das Produkt angesehen wurde. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### startCheckout

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn der Käufer auf eine Checkout-Schaltfläche klickt. | `commerce.checkouts` |

#### Vom startCheckout erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.checkouts` | Gibt an, ob während des Checkout-Prozesses eine Aktion stattgefunden hat. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### completeCheckout

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn der Käufer eine Bestellung aufgibt. | `commerce.purchases` |

#### Von completeCheckout erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.purchases` | Zeigt an, ob eine Bestellung akzeptiert wurde. |
| `commerce.order` | Enthält Informationen zur aufgegebenen Bestellung für ein oder mehrere Produkte. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diese Zahlungsbuchung. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Die Optionen sind: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.taxAmount` | Der vom Käufer als Teil der Abschlusszahlung gezahlte Steuerbetrag. |
| `commerce.order.discountAmount` | Gibt den Rabattbetrag an, der auf die gesamte Bestellung angewendet wurde. |
| `commerce.order.createdDate` | Die Uhrzeit und das Datum, an dem eine neue Bestellung im Commerce-System erstellt wird. Beispiel: `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Lieferdetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardlieferung, Expresslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |  | `shipping` | Lieferdetails für ein oder mehrere Produkte. |
| `commerce.shipping.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

## Kundenprofil-Ereignisse

Profilereignisse, die von der Storefront erfasst werden, enthalten Kontoinformationen wie `signIn`, `signOut`, `createAccount` und `editAccount`. Diese Daten werden verwendet, um wichtige Kundendetails auszufüllen, die erforderlich sind, um Segmente besser zu definieren oder Marketing-Kampagnen auszuführen, z. B. Sende-Anmelde-Rabattangebote, Kontoänderungsbestätigungen usw. Es werden ähnliche Profilereignisse von der [Server-seitig](events-backoffice.md#customer-profile-events) erfasst.

### Anmelden

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, sich anzumelden. | `userAccount.login` |

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Dies bedeutet nicht, dass die Aktion erfolgreich war.

#### Von SignIn erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Ein einzelner Akteur, Kontakt oder Inhaber. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp, wie `Personal` oder `Company`, falls zutreffend. |
| `person.personalEmailID` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `personalEmail` | Erfasst Kontaktdetails - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `userAccount` | Gibt alle Treuedetails, Voreinstellungen, Anmeldeprozesse und andere Kontoeinstellungen an. |
| `userAccount.login` | Gibt an, ob ein Besucher versucht hat, sich anzumelden. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

### Abmelden

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, sich abzumelden. | `userAccount.logout` |

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Dies bedeutet nicht, dass die Aktion erfolgreich war.

#### Von der Abmeldung erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `userAccount` | Gibt alle Treuedetails, Voreinstellungen, Anmeldeprozesse und andere Kontoeinstellungen an. |
| `userAccount.logout` | Zeigt an, ob ein Besucher versucht hat, sich abzumelden. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

### createAccount

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu erstellen. | `userAccount.createProfile` |

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Dies bedeutet nicht, dass die Aktion erfolgreich war.

#### Von createAccount erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Ein einzelner Akteur, Kontakt oder Inhaber. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp, wie `Personal` oder `Company`, falls zutreffend. |
| `person.personalEmailID` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `personalEmail` | Erfasst Kontaktdetails - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `userAccount` | Gibt alle Treuedetails, Voreinstellungen, Anmeldeprozesse und andere Kontoeinstellungen an. |
| `userAccount.updateProfile` | Gibt an, ob ein Benutzer sein Kontoprofil aktualisiert hat. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

### Konto bearbeiten

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu bearbeiten. | `userAccount.updateProfile` |

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Dies bedeutet nicht, dass die Aktion erfolgreich war.

#### Von editAccount erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Ein einzelner Akteur, Kontakt oder Inhaber. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp, wie `Personal` oder `Company`, falls zutreffend. |
| `person.personalEmailID` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `personalEmail` | Erfasst Kontaktdetails - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `userAccount` | Gibt alle Treuedetails, Voreinstellungen, Anmeldeprozesse und andere Kontoeinstellungen an. |
| `userAccount.updateProfile` | Gibt an, ob ein Benutzer sein Kontoprofil aktualisiert hat. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

## Ereignisse suchen

Die Suchereignisse liefern Daten, die für die Absicht des Erstkäufers relevant sind. Ein Einblick in die Absichten eines Käufers hilft Händlern zu sehen, wie Käufer nach Artikeln suchen, was sie klicken und schließlich kaufen oder verlassen. Ein Beispiel für die Verwendung dieser Daten ist, wenn Sie bestehende Kunden ansprechen möchten, die nach Ihrem Top-Produkt suchen, das Produkt jedoch nie kaufen. Sie müssen die [[!DNL Live Search]](../live-search/install.md)-Erweiterung installieren, um auf diese Ereignisse zugreifen zu können.

Verwenden Sie die Felder `searchRequest.id` und `searchResponse.id`, die sowohl in den `searchRequestSent`- als auch in den `searchResponseReceived`-Ereignissen zu finden sind, um einen Querverweis zwischen einer Suchanfrage und der entsprechenden Suchantwort durchzuführen.

### searchRequestSent

| Beschreibung | XDM-Ereignisname |
|---|---|
| Ausgelöst durch die folgenden Ereignisse im Pop-up „search as you type“: <br><br>Drücken Sie die Eingabetaste, klicken Sie auf _Alle anzeigen_<br><br> Ausgelöst durch die folgenden Ereignisse auf den Suchergebnisseiten:<br><br>Wählen Sie einen Filter aus, ändern Sie die Sortierreihenfolge (_Sortieren nach_), ändern Sie die Sortierrichtung (aufsteigend oder absteigend), ändern Sie die Anzahl der Ergebnisse pro Seite (_Anzeigen # pro Seite_), navigieren Sie zur nächsten Seite, navigieren Sie zur vorherigen Seite, navigieren Sie zu einer anderen Seite | `searchRequest` |

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition mit installierter B2B-Erweiterung nicht unterstützt.

#### Von searchRequestSent erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `searchRequest` | Gibt an, ob eine Suchanfrage gesendet wurde. |
| `searchRequest.id` | Die eindeutige ID für diese bestimmte Suchanfrage. |
| `searchRequest.value` | Der quantifizierbare Wert der Anfrage. |
| `siteSearch` | Enthält Informationen zur Suche. |
| `siteSearch.filter` | Gibt an, ob Filter angewendet wurden, um die Suchergebnisse zu begrenzen. |
| `siteSearch.filter.attribute` (Filter) | Der Aspekt eines Elements, mit dem bestimmt wird, ob er in Suchergebnisse aufgenommen werden soll. |
| `siteSearch.filter.isRange` | Wenn „true“, geben die Werte die Endpunkte eines akzeptablen Wertebereichs an. |
| `siteSearch.filter.value` | Attributwert, der bestimmt, welche Elemente in den Suchergebnissen enthalten sind. |
| `siteSearch.sort` | Gibt an, wie die Suchergebnisse sortiert werden sollen. |
| `siteSearch.sort.attribute` (sortieren) | Ein Attribut zum Sortieren von Elementen in Suchergebnissen. |
| `siteSearch.sort.order` | Die Reihenfolge, in der Suchergebnisse zurückgegeben werden. |
| `siteSearch.query` | Die gesuchten Begriffe. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

### searchResponseReceived

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn die Live-Suche Ergebnisse für das Pop-up „Suche während der Eingabe“ oder die Suchergebnisseite zurückgibt. | `searchResponse` |

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition mit installierter B2B-Erweiterung nicht unterstützt.

#### Von searchResponseReceived erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `searchResponse` | Gibt an, ob eine Suchantwort empfangen wurde. |
| `searchResponse.id` | Die eindeutige ID für diese bestimmte Suchantwort. |
| `searchResponse.value` | Der quantifizierbare Wert der Antwort. |
| `siteSearch.numberOfResults` | Die Anzahl der zurückgegebenen Produkte. |
| `siteSearch.suggestions` | Ein Array von Zeichenfolgen, die die Namen von Produkten und Kategorien enthalten, die im Katalog vorhanden sind und der Suchanfrage ähnlich sind. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

## B2B-Ereignisse

![B2B für Adobe Commerce](../assets/b2b.svg) Für B2B-Händler müssen [ die `experience-platform-connector-b2b`-Erweiterung ](install.md#install-the-b2b-extension)installieren“, um auf diese Ereignisse zugreifen zu können.

Die B2B-Ereignisse enthalten [Anforderungsliste](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) Informationen, z. B. ob eine Anforderungsliste erstellt, hinzugefügt oder gelöscht wurde. Durch die Verfolgung von für Anforderungslisten spezifischen Ereignissen können Sie sehen, welche Produkte Ihre Kunden häufig kaufen, und auf dieser Grundlage Kampagnen erstellen.

### createRequirementList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Einkäufer eine Anforderungsliste erstellt. | `commerce.requisitionListOpens` |

#### Von createRequirementList erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requisitionListOpens` | Zeigt die Initialisierung einer neuen Anforderungsliste an. |
| `commerce.requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste. |
| `commerce.requisitionList.ID` | Eindeutige Kennung der Anforderungsliste. |
| `commerce.requisitionList.name` | Name der vom Kunden angegebenen Anforderungsliste. |
| `commerce.requisitionList.description` | Beschreibung der vom Kunden angegebenen Anforderungsliste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

### addToRequirementList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Einkäufer ein Produkt zu einer vorhandenen Anforderungsliste hinzufügt oder beim Erstellen einer Liste. | `commerce.requisitionListAdds` |

#### Von addToRequirementList erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requisitionListAdds` | Gibt an, ob ein oder mehrere Produkte zu einer Anforderungsliste hinzugefügt werden sollen. |
| `commerce.requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste. |
| `commerce.requisitionList.ID` | Eindeutige Kennung der Anforderungsliste. |
| `commerce.requisitionList.name` | Name der vom Kunden angegebenen Anforderungsliste. |
| `commerce.requisitionList.description` | Beschreibung der vom Kunden angegebenen Anforderungsliste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `productListItems` | Ein Array von Produkten, die der Anforderungsliste hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### removeFromRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Einkäufer ein Produkt aus einer Anforderungsliste entfernt. | `commerce.requisitionListRemovals` |

#### Von removeFromRequisitionList erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requsitionListRemovals` | Gibt an, ob ein oder mehrere Produkte aus einer Anforderungsliste entfernt werden sollen. |
| `commerce.requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste. |
| `commerce.requisitionList.ID` | Eindeutige Kennung der Anforderungsliste. |
| `commerce.requisitionList.name` | Name der vom Kunden angegebenen Anforderungsliste. |
| `commerce.requisitionList.description` | Beschreibung der vom Kunden angegebenen Anforderungsliste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `productListItems` | Ein Array von Produkten, die der Anforderungsliste hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### deleteRequirementList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Einkäufer eine Anforderungsliste löscht. | `commerce.requisitionListDeletes` |

#### Von deleteRequirementList erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requisitionListDeletes` | Gibt an, dass eine Anforderungsliste gelöscht wurde. |
| `commerce.requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste. |
| `commerce.requisitionList.ID` | Eindeutige Kennung der Anforderungsliste. |
| `commerce.requisitionList.name` | Name der vom Kunden angegebenen Anforderungsliste. |
| `commerce.requisitionList.description` | Beschreibung der vom Kunden angegebenen Anforderungsliste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
