---
title: Positionen für [!DNL Payment Services]
description: Erfahren Sie mehr über Zeileneinträge für  [!DNL Payment Services]  und wie Sie Zeileneinträge im Händler-Dashboard anzeigen können.
feature: Payments, Paas, Saas
role: User
exl-id: f690ff94-f83d-4525-9d52-1dea25a71060
source-git-commit: 6727102c54e0ac81df289ecd66ec61156662b8b9
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Zeileneinträge für [!DNL Payment Services]

Die Positionen für [!DNL Payment Services] sind die in einer Bestellung enthaltenen Artikel. Diese Zeileneinträge enthalten u. a. folgende Informationen:

* Produktdetails
* Menge
* Preis (einschließlich Steuern, Rabatte und andere relevante Informationen)

Diese Informationen sind für den Kundendienst, die Auftragsverwaltung und die ordnungsgemäße Rechnungsstellung nützlich.

## Konfigurieren von Zeileneinträgen

Zeileneinträge sind standardmäßig für [!DNL Payment Services] aktiviert. So konfigurieren Sie:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.

1. Navigieren Sie zu **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]** aus.

1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.

1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_&#x200B;den Abschnitt&#x200B;_[!UICONTROL Line Items]_ .

1. Wählen Sie **[!UICONTROL Line Items Enabled]** &quot;`Yes`&quot; aus, um Zeileneinträge zu aktivieren (Standard), oder &quot;`No`&quot;, um sie zu deaktivieren.

1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.

>[!IMPORTANT]
>
> Wenn Sie Erweiterungen von Drittanbietern haben, die Ihren Bestellungen benutzerdefinierte Gebühren hinzufügen (z. B. Bearbeitungsgebühren), müssen Sie möglicherweise Zeileneinträge deaktivieren. [!DNL Payment Services] berechnet Positionsartikel auf der Basis von standardmäßigen Commerce-Auftragskomponenten (Artikel, Steuer, Versand und Rabatte). Gebühren von Drittanbietern, die von [!DNL Payment Services] nicht erkannt werden, können zu einer Diskrepanz zwischen der Gesamtsumme des Einzelpostens und der Bestellsumme führen, was den Abschluss des Checkouts verhindern kann.

## Zeileneinträge anzeigen

So zeigen Sie Zeileneinträge an:

1. Navigieren Sie zu Ihrem [PayPal-Händler-Dashboard](https://www.paypal.com/merchant/){target=_blank}.

1. Klicken Sie **Aktivität** > **Alle Transaktionen**.

1. Wählen Sie die gewünschte Reihenfolge aus und zeigen Sie die zugehörigen Zeileneinträge an:

   > Beispiel für Zeileneinträge in der Dashboard-Ansicht „Einkäufer“

   ![Zeileneintragsansicht](assets/paypal-shopper-dashboard-line-items-view.png){width="500" zoomable="yes"}

## Attribute für Zeileneinträge

Zeileneinträge werden generiert, wenn die Bestellung über Adobe Commerce aufgegeben wird und Informationen mit den folgenden Attributen an PayPal gesendet werden:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `name` | Zeichenfolge! | Der Elementname. Wenn ein Artikel aufgrund mehrerer Mengen oder eines Problems der Steuerrundung mehr als eine Position hat, bleibt die Artikelbezeichnung für alle Positionen gleich, aber der angezeigte Preis kann aufgrund der Rundung leicht variieren. |
| `unit_amount` | Objekt! | Der Artikelpreis oder -satz pro Einheit. Umfasst die folgenden Attribute: `currency_code` und `value`. |
| `tax` | Objekt | Die Artikelsteuer für jede Einheit. Umfasst die folgenden Attribute: `currency_code` und `value`. |
| `quantity` | Zeichenfolge! | Die Artikelmenge. Wird eine ganze Zahl sein. |
| `description` | Zeichenfolge | Die detaillierte Artikelbeschreibung. |
| `sku` | Zeichenfolge | Die Lagerungseinheit (oder SKU) für den Artikel. |
| `url` | Zeichenfolge | Die `URL` des gekauften Artikels. Für den Käufer sichtbar und in Käufererlebnissen verwendet. |
| `upc` | Objekt | Der universelle Produkt-Code (oder UPC) des Artikels. |
| `category` | Zeichenfolge | Der Typ der Elementkategorie. |

### Attribute `unit_amount`

Das `unit_amount`-Objekt enthält die folgenden Attribute:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `currency_code` | Zeichenfolge! | Der [dreistellige ISO-4217-](https://developer.paypal.com/api/rest/reference/currency-codes/), der die Währung angibt. |
| `value` | Zeichenfolge! | Gibt den Wert des Elements an. Die `currency_code` bestimmt die erforderliche Anzahl von Dezimalstellen, falls vorhanden. |

### Attribute `tax`

Das `tax`-Objekt enthält die folgenden Attribute:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `currency_code` | Zeichenfolge! | Der [dreistellige ISO-4217-](https://developer.paypal.com/api/rest/reference/currency-codes/), der die Währung angibt. |
| `value` | Zeichenfolge! | Gibt den Wert des Elements an. Hängt von jedem `currency_code` für die erforderliche Anzahl von Dezimalstellen ab. |

### Attribute `upc`

Das `upc`-Objekt enthält die folgenden Attribute:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `type` | Zeichenfolge! | Der UPC-Typ. |
| `code` | Zeichenfolge! | Der UPC-Produktcode des Artikels. |

+++Beispiel für Zeileneinträge

```json
{
    "name": "Crown Summit Backpack - 1",
    "unit_amount": {
        "currency_code": "USD",
        "value": "38.50"
    },
    "tax": {
        "currency_code": "USD"
        "value": "3.13"
    },
    "quantity": "1",
    "description": "The Crown Summit Backpack is equally at home in a gym locker, study cube or a pup tent, so be sure yours is packed with books,",
    "sku": "24-MB03",
    "url": "https://magento.test/crown-summit-backpack.html",
    "upc": {
        "type": "UPC-A",
        "code": "000003"
    },
    "category": "PHYSICAL_GOODS"
},
{
    "name": "Crown Summit Backpack - 2",
    "unit_amount": {
        "currency_code": "USD",
        "value": "38.50"
    },
    "tax": {
        "currency_code": "USD",
        "value": "3.14"
    },
    "quantity": "1",
    "description": "The Crown Summit Backpack is equally at home in a gym locker, study cube or a pup tent, so be sure yours is packed with books,",
    "sku": "24-MB03",
    "url": "https://magento.test/crown-summit-backpack.html",
    "upc": {
        "type": "UPC-A",
        "code": "000003"
    },
    "category": "PHYSICAL_GOODS"
}
```

+++

Weitere Informationen [&#x200B; diesen Feldern und deren Einschränkungen finden Sie in der &#x200B;](https://developer.paypal.com/docs/api/orders/v2/#definition-line_item){target=_blank} für PayPal-Entwickler zu Zeileneinträgen .

## Zeileneinträge verwalten

Adobe Commerce [berechnet die Steuer auf der Grundlage des Gesamtbetrags für jede Zeile](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/taxes/taxes#warning-messages){target=_blank} was zu Rundungsproblemen führen kann, wenn mehrere Mengen desselben Artikels bestellt werden oder wenn im Katalog steuerinklusive Preise angezeigt werden. In solchen Fällen kann die Gesamtmenge in zwei Zeilen aufgeteilt werden, aber die Menge entspricht der Gesamtzahl der bestellten Artikel.

> Beispiel für Zeileneinträge mit Rundungsproblemen in der Ansicht „Händler-Dashboard“

![Zeileneintragsansicht](assets/line-items-example.png){width="600" zoomable="yes"}

+++Wie Adobe Commerce ein Rundungsproblem in Zeileneinträgen berechnet

Zeileneinträge für [!DNL Payment Services] gleichen dieses Rundungsproblem aus, sodass der `unit_amount`- oder `unit_tax` dem Gesamtbetrag für den Auftrag entspricht. Ein Artikel kann zur Lösung dieses Rundungsproblems in zwei Zeilen aufgeteilt werden:

* Wenn die Rundungsausgabe auf der `unit_amount` erscheint, sollte der Händler eine Differenz zum Preis dieser zusätzlichen Position sehen.
* Wenn das Rundungsproblem auf der `unit_tax` auftritt, wird kein Unterschied bei den einzelnen Zeileneinträgen angezeigt, da die `tax` nicht im Raster, sondern nur als Summe am unteren Rand angezeigt wird.

+++
