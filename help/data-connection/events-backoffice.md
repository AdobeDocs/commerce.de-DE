---
title: Back-Office-Ereignisse
description: Erfahren Sie, welche Daten jedes Back-Office-Ereignis erfasst.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '3606'
ht-degree: 0%

---

# [!DNL Data Connection] Back-Office-Ereignisse

Im Folgenden sind die Commerce-Backoffice-Ereignisse aufgeführt, die bei der Installation der [!DNL Data Connection]-Erweiterung verfügbar sind. Die von diesen Ereignissen erfassten Daten werden an die Adobe Experience Platform gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) erstellen, um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt werden.

Zusätzlich zu den Daten, die die folgenden Ereignisse erfassen, erhalten Sie auch [andere Daten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) bereitgestellt von der Adobe Experience Platform Web SDK.

Back-Office-Ereignisse enthalten Server-seitige Daten. Diese Daten umfassen [Bestellstatus](#order-status) Informationen wie z. B. ob eine Bestellung aufgegeben, storniert, zurückerstattet, versendet oder abgeschlossen wurde. Server-seitige Daten enthalten auch [Kundenprofilereignisse](#customer-profile-events) Informationen, beispielsweise ob ein Konto erstellt, aktualisiert oder gelöscht wurde.

>[!NOTE]
>
>Alle Backoffice-Ereignisse enthalten das Feld [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , das die E-Mail-Adresse des Käufers, sofern verfügbar, und die ECID enthält.

## Bestellstatus

Die Daten zum Bestellstatus zeigen eine 360-Grad-Ansicht der Bestellung des Einkäufers. Diese Ansicht hilft Händlern, den gesamten Bestellstatus bei der Entwicklung von Marketing-Kampagnen zielgerichteter festzulegen oder zu analysieren. So können Sie beispielsweise Trends in bestimmten Produktkategorien erkennen, die zu unterschiedlichen Jahreszeiten eine gute Leistung erbringen. Zum Beispiel Winterkleidung, die sich in kälteren Monaten besser verkauft, oder bestimmte Produktfarben, an denen sich Käufer über die Jahre interessiert haben. Darüber hinaus können Sie mithilfe von Auftragsstatusdaten den Kundenwert über die gesamte Lebensdauer berechnen, indem Sie die Konversionsneigung eines Käufers auf der Grundlage früherer Bestellungen verstehen.

### orderPlaced

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Bestellung aufgibt. | `commerce.backofficeOrderPlaced` |

#### Von orderPlaced erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diese Zahlungsbuchung. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Gezählt, benutzerdefinierte Werte zulässig. |
| `commerce.order.payments.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.taxAmount` | Der vom Käufer als Teil der Abschlusszahlung gezahlte Steuerbetrag. |
| `commerce.order.discountAmount` | Gibt den Rabattbetrag an, der auf die gesamte Bestellung angewendet wurde. |
| `commerce.order.createdDate` | Die Uhrzeit und das Datum, an dem eine neue Bestellung im Commerce-System erstellt wird. Beispiel: `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | Der ISO 4217-Währungscode, der für die Bestellsummen verwendet wird. |
| `commerce.shipping` | Lieferdetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardlieferung, Expresslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `commerce.shipping.currencyCode` | Der ISO 4217-Währungscode, der für die Versandsumme verwendet wird. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `commerce.billing.address` | Rechnungsadresse. |
| `commerce.billing.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `commerce.billing.address.street2` | Zusätzliches Feld für Straßeninformationen. |
| `commerce.billing.address.city` | Der Name der Stadt. |
| `commerce.billing.address.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `commerce.billing.address.postalCode` | Die Postleitzahl des Standorts. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern enthält diese nur einen Teil der Postleitzahl. |
| `commerce.billing.address.country` | Der Name des von der Regierung verwalteten Gebiets. Anders als `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in einer beliebigen Sprache enthalten kann. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `productListItems` | Ein Array von Produkten in der Bestellung. |
| `productListItems.id` | Die Positionskennung für diesen Produkteintrag. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |

### orderInvoiced

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Händler eine Rechnung einreicht, um die Zahlung anzufordern. | `commerce.backofficeOrderInvoiced` |

#### Von orderInvoiced erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.priceTotal` | Der Gesamtpreis dieser Bestellung, nachdem alle Rabatte und Steuern angewendet wurden. |
| `commerce.order.currencyCode` | Der ISO 4217-Währungscode, der für die Bestellsummen verwendet wird. |
| `commerce.order.purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Gezählt, benutzerdefinierte Werte zulässig. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.shipping` | Lieferdetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardlieferung, Expresslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `productListItems` | Ein Array von Produkten in der Bestellung. |
| `productListItems.id` | Die Positionskennung für diesen Produkteintrag. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |

### orderItemsShipped

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird beim Versand einer Bestellung ausgelöst. | `commerce.backofficeOrderItemsShipped` |

#### Von orderItemsShipped erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diese Zahlungsbuchung. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Gezählt, benutzerdefinierte Werte zulässig. |
| `commerce.order.payments.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.priceTotal` | Der Gesamtpreis dieser Bestellung, nachdem alle Rabatte und Steuern angewendet wurden. |
| `commerce.order.purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. |
| `commerce.order.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.lastUpdatedDate` | Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz im Commerce-System zuletzt aktualisiert wurde. |
| `commerce.shipping` | Lieferdetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardlieferung, Expresslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `commerce.shipping.address` | Die physische Lieferadresse. |
| `commerce.shipping.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `commerce.shipping.address.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `commerce.shipping.address.city` | Der Name der Stadt. |
| `commerce.shipping.address.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `commerce.shipping.address.postalCode` | Die Postleitzahl des Standorts. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern enthält diese nur einen Teil der Postleitzahl. |
| `commerce.shipping.address.country` | Der Name des von der Regierung verwalteten Gebiets. Anders als `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in einer beliebigen Sprache enthalten kann. |
| `commerce.shipping.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.shipping.trackingNumber` | Die vom Versandunternehmen für eine Bestellartikellieferung angegebene Tracking-Nummer. |
| `commerce.shipping.trackingURL` | Die URL zum Nachverfolgen des Versandstatus eines Bestellartikels. |
| `commerce.shipping.shipDate` | Das Datum, an dem ein oder mehrere Artikel aus einer Bestellung versendet werden. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `commerce.billing.address` | Rechnungsadresse. |
| `commerce.billing.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `commerce.billing.address.street2` | Zusätzliches Feld für Straßeninformationen. |
| `commerce.billing.address.city` | Der Name der Stadt. |
| `commerce.billing.address.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `commerce.billing.address.postalCode` | Die Postleitzahl des Standorts. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern enthält diese nur einen Teil der Postleitzahl. |
| `commerce.billing.address.country` | Der Name des von der Regierung verwalteten Gebiets. Anders als `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in einer beliebigen Sprache enthalten kann. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `productListItems` | Ein Array von Produkten in der Bestellung. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |

### orderCancelled

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Bestellung storniert. | `commerce.backofficeOrderCancelled` |

#### Von orderCancelled erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. |
| `commerce.order.cancelDate` | Datum und Uhrzeit, zu der ein Käufer eine Bestellung storniert. |
| `commerce.order.lastUpdatedDate` | Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz im Commerce-System zuletzt aktualisiert wurde. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |

### orderLineItemRefund

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Rückerstattung für einen zurückgegebenen Artikel erhält. | `commerce.backofficeCreditMemoIssued` |

#### Von orderLineItemRefund erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.lastUpdatedDate` | Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz im Commerce-System zuletzt aktualisiert wurde. |
| `commerce.order.purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. |
| `commerce.refunds` | Die Liste der Erstattungen für diese Bestellung. |
| `commerce.refunds.transactionID` | Eindeutige Kennung für diese Erstattung. |
| `commerce.refunds.refundAmount` | Der Wert der Erstattung. |
| `commerce.refunds.refundPaymentType` | Die Zahlungsmethode für diese Bestellung. Gezählt, benutzerdefinierte Werte zulässig. |
| `commerce.refunds.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `productListItems` | Ein Array von Produkten in der Bestellung. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |

### orderItemsReturnInitiated

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer die Rückgabe eines Artikels anfordert. | `commerce.backofficeOrderItemsReturnInitiated` |

#### Von orderItemsReturnInitiated erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.returns` | Die RMA (Return Merchandise Authorization)-Informationen für diese Bestellung. |
| `commerce.order.returns.returnID` | Die eindeutige Kennung für diese Rücksendung (Warenrückgabe). |
| `commerce.order.returns.returnStatus` | Der Status der RMA (Return Merchandise Authorization), z. B. Ausstehend, Geschlossen usw. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `productListItems` | Ein Array von Produkten in der Bestellung. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |
| `productListItems.returnItem` | Die RMA-Informationen (Warenrücksendeautorisierung) für diesen Artikel. |
| `productListItems.returnItem.returnStatus` | Der Status des zurückgegebenen Elements, z. B. Ausstehend, Genehmigt usw. |
| `productListItems.returnItem.returnReason` | Der Grund, warum für diesen Artikel eine Rücksendung angefordert wird. |
| `productListItems.returnItem.returnItemCondition` | Die Bedingung des Elements, für das die Rückgabe angefordert wird. |
| `productListItems.returnItem.returnResolution` | Die angeforderte Auflösung des zurückgegebenen Elements, z. B. Rückerstattung, Umtausch usw. |
| `productListItems.returnItem.returnQuantityRequested` | Die Nummer dieses Artikels, den der Einkäufer zurückgeben wollte. |
| `productListItems.returnItem.returnQuantityAuthorized` | Die Nummer dieses Elements, das zur Rückgabe autorisiert ist. |
| `productListItems.returnItem.eturnQuantityReceived` | Die Anzahl der zurückgegebenen empfangenen Elemente. |
| `productListItems.returnItem.returnQuantityApproved` | Die Nummer dieses Artikels mit Rücksendung vollständig abgeschlossen und genehmigt. |

### orderItemReturnCompleted

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Artikel, den ein Käufer zurückgeben möchte, abgeschlossen ist. | `commerce.backofficeOrderItemsReturnCompleted` |

#### Von orderItemReturnCompleted erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.returns` | Die RMA (Return Merchandise Authorization)-Informationen für diese Bestellung. |
| `commerce.order.returns.returnID` | Die eindeutige Kennung für diese Rücksendung (Warenrückgabe). |
| `commerce.order.returns.returnStatus` | Der Status der RMA (Return Merchandise Authorization), z. B. Ausstehend, Geschlossen usw. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `productListItems` | Ein Array von Produkten in der Bestellung. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |
| `productListItems.returnItem` | Die RMA-Informationen (Warenrücksendeautorisierung) für diesen Artikel. |
| `productListItems.returnItem.returnStatus` | Der Status des zurückgegebenen Elements, z. B. Ausstehend, Genehmigt usw. |
| `productListItems.returnItem.returnReason` | Der Grund, warum für diesen Artikel eine Rücksendung angefordert wird. |
| `productListItems.returnItem.returnItemCondition` | Die Bedingung des Elements, für das die Rückgabe angefordert wird. |
| `productListItems.returnItem.returnResolution` | Die angeforderte Auflösung des zurückgegebenen Elements, z. B. Rückerstattung, Umtausch usw. |
| `productListItems.returnItem.returnQuantityRequested` | Die Nummer dieses Artikels, den der Einkäufer zurückgeben wollte. |
| `productListItems.returnItem.returnQuantityAuthorized` | Die Nummer dieses Elements, das zur Rückgabe autorisiert ist. |
| `productListItems.returnItem.eturnQuantityReceived` | Die Anzahl der zurückgegebenen empfangenen Elemente. |
| `productListItems.returnItem.returnQuantityApproved` | Die Nummer dieses Artikels mit Rücksendung vollständig abgeschlossen und genehmigt. |

### orderShipmentCompleted

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Lieferung abgeschlossen ist. | `commerce.backofficeOrderShipmentCompleted` |

#### Von orderShipmentCompleted erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diese Zahlungsbuchung. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Gezählt, benutzerdefinierte Werte zulässig. |
| `commerce.order.payments.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.taxAmount` | Der vom Käufer als Teil der Abschlusszahlung gezahlte Steuerbetrag. |
| `commerce.order.createdDate` | Die Uhrzeit und das Datum, an dem eine neue Bestellung im Commerce-System erstellt wird. Beispiel: `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Lieferdetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardlieferung, Expresslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `commerce.shipping.shipDate` | Das Datum, an dem ein oder mehrere Artikel aus einer Bestellung versendet werden. |
| `commerce.shipping.address` | Die physische Lieferadresse. |
| `commerce.shipping.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `commerce.shipping.address.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `commerce.shipping.address.city` | Der Name der Stadt. |
| `commerce.shipping.address.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `commerce.shipping.address.postalCode` | Die Postleitzahl des Standorts. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern enthält diese nur einen Teil der Postleitzahl. |
| `commerce.shipping.address.country` | Der Name des von der Regierung verwalteten Gebiets. Anders als `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in einer beliebigen Sprache enthalten kann. |
| `commerce.billing.address` | Rechnungsadresse. |
| `commerce.billing.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `commerce.billing.address.street2` | Zusätzliches Feld für Straßeninformationen. |
| `commerce.billing.address.city` | Der Name der Stadt. |
| `commerce.billing.address.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `commerce.billing.address.postalCode` | Die Postleitzahl des Standorts. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern enthält diese nur einen Teil der Postleitzahl. |
| `commerce.billing.address.country` | Der Name des von der Regierung verwalteten Gebiets. Anders als `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in einer beliebigen Sprache enthalten kann. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `productListItems` | Ein Array von Produkten in der Bestellung. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder von Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeilenartikel. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendete Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Für ein konfigurierbares Produkt verwendetes Feld. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |

## Kundenprofil-Ereignisse

Von der Server-Seite erfasste Profilereignisse enthalten Kontoinformationen wie `accountCreated`, `accountUpdated` und `accountDeleted`. Diese Daten werden verwendet, um wichtige Kundendetails auszufüllen, die erforderlich sind, um Segmente besser zu definieren oder Marketing-Kampagnen auszuführen, z. B. Sende-Anmelde-Rabattangebote, Kontoänderungsbestätigungen usw. Es werden ähnliche Profilereignisse aus der [Storefront](events.md#customer-profile-events) erfasst.

>[!NOTE]
>
>Jedes Kundenprofilereignis enthält auch das Feld [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , das die vom System generierte Commerce-Kunden-ID als primäre Kennung für das Profil und eine E-Mail-ID enthält, die als sekundäre Kennung verwendet wird.

### accountCreated

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu erstellen. | `userAccount.backofficeCreateProfile` |

#### Von accountCreated erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

### accountUpdated

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu bearbeiten. | `userAccount.backofficeUpdateProfile` |

#### Von accountUpdated erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |

### accountDeleted

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu löschen. | `userAccount.backofficeDeleteProfile` |

#### Von accountDeleted erfasste Daten

Die folgende Tabelle beschreibt die für dieses Ereignis erfassten Daten.

| Feld | Beschreibung |
|---|---|
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungskennung. Eine 32-stellige alphanumerische ID, die durch Bindestriche getrennt ist. |
| `commerce.commerceScope.storeCode` | Der eindeutige Speicher-Code. Pro Website können viele Geschäfte vorhanden sein. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Code der Store-Ansicht. Sie können mehrere Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. In einer Umgebung können sich viele Websites befinden. |
