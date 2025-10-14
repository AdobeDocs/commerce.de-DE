---
title: Berichterstellung
description: Verwenden Sie die Auswertung „Transaktionen“, um Einblicke in die Autorisierungsraten und Trends von Transaktionen zu erhalten.
role: User
level: Intermediate
exl-id: dd1d80f9-5983-4181-91aa-971522eb56fa
source-git-commit: 4482c1f93a424c73497b88c707d0ab93a694c957
workflow-type: tm+mt
source-wordcount: '1270'
ht-degree: 0%

---

# Berichterstellung

[!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bietet Ihnen ein umfassendes Reporting, damit Sie einen klaren Überblick über die Transaktionen, Bestellungen und Zahlungen Ihres Stores erhalten.

![Transaktionsbericht](assets/transactions-report.png){width="700" zoomable="yes"}

Der Transaktionsbericht bietet Einblicke in die Autorisierungsraten von Transaktionen und negative Transaktionstrends, sodass Sie den Status Ihres Stores effektiv überwachen und Transaktionsprobleme vorab identifizieren und beheben können.

Sehen Sie sich einzelne Transaktionen für Bestellungen an, die in der Storefront aufgegeben werden, sowie deren Zahlungsmethoden, Ergebnis, Zahlungsantwortcodes und mehr.

Die im Transaktionsbericht enthaltenen Informationen sind nur für die Verwendung durch Händler vorgesehen. Geben Sie diese Informationen nicht an Kunden oder andere potenzielle Betrüger weiter. Transaktionsinformationen können verwendet werden, um Sicherheitsprüfungen zu umgehen oder Bestellungen aufzugeben, die zu Rückbelastungen führen.

Sie können den Transaktionsbericht im CSV-Dateiformat herunterladen, um ihn in bestehender Buchhaltungs- oder Auftragsverwaltungssoftware zu verwenden.

>[!NOTE]
>
>Sie können keine Finanzberichte anzeigen, wenn Sie den [Live-Modus aktiviert und aktiviert](production.md#enable-live-payments) für [!DNL Payment Services] nicht aktiviert haben.

## Ansicht der Transaktionsberichte

Die Berichtsansicht „Transaktionen“ ist in der Ansicht „Transaktionen“ von Payment Services verfügbar. Es enthält alle verfügbaren Informationen über Transaktionen für Ihren Shop/Ihre Geschäfte.

Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**, um die detaillierte Ansicht des tabellarischen Transaktionsberichts anzuzeigen.

![Transaktionsbericht - Ansicht](assets/transactions-report-view.png){width="800" zoomable="yes"}

Sie können diese Ansicht gemäß den Abschnitten in diesem Thema so konfigurieren, dass die Daten, die angezeigt werden sollen, am besten präsentiert werden.

In diesem Bericht werden verknüpfte Commerce-Auftrags- und PayPal-Transaktions-IDs, Transaktionsbeträge, Zahlungsmethoden pro Transaktion und mehr angezeigt.

Nicht alle Zahlungsmethoden bieten die gleiche Granularität von Informationen. Kreditkartentransaktionen geben beispielsweise die Antwort-, AVS- und CCV-Codes sowie die letzten vier Ziffern der Karte im Transaktionsbericht an. Bei den PayPal-Zahlungstasten ist dies nicht der Fall.

Sie können [Transaktionen](#download-transactions) im CSV-Dateiformat herunterladen, um sie in bestehender Buchhaltungs- oder Auftragsverwaltungssoftware zu verwenden.

>[!WARNING]
>
> Der Transaktionsbericht enthält keine Erfassung, die außerhalb von [!DNL Payment Services] vorgenommen wurde.

### Datenquelle auswählen

In der Berichtsansicht Transaktionen können Sie die Datenquelle - **[!UICONTROL Live]** oder **[!UICONTROL Sandbox]** - auswählen, für die Sie Berichtsergebnisse anzeigen möchten.

![Datenquellenauswahl](assets/datasource.png){width="300" zoomable="yes"}

Wenn _[!UICONTROL Live]_&#x200B;die ausgewählte Datenquelle ist, können Sie Berichtsinformationen für Ihre Stores anzeigen, die [!DNL Payment Services] im Produktionsmodus verwenden. Wenn&#x200B;_[!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Sie Berichtsinformationen für Ihren Sandbox-Modus anzeigen.

Die Auswahl von Datenquellen funktioniert wie folgt:

* Wenn Sie keine Stores haben, die [!DNL Payment Services] im Produktionsmodus verwenden, ist die Datenquellenauswahl standardmäßig auf _[!UICONTROL Sandbox]_&#x200B;eingestellt.
* Wenn Sie über Stores (einen oder mehrere) verfügen, die [!DNL Payment Services] im Produktionsmodus verwenden, ist die Datenquellenauswahl standardmäßig auf _[!UICONTROL Live]_&#x200B;eingestellt.
* Berichtsexporte berücksichtigen immer die Auswahl der Datenquelle.

So wählen Sie die Datenquelle für Ihren [!UICONTROL Transactions] aus:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf **[!UICONTROL Data source]** und wählen Sie **[!UICONTROL Live]** oder **[!UICONTROL Sandbox]** aus.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

### Anpassen des Zeitrahmens für Daten

In der Berichtsansicht Transaktionen können Sie den Zeitrahmen der Transaktionen, die Sie anzeigen möchten, anpassen, indem Sie bestimmte Daten auswählen. Standardmäßig werden 30 Tage Transaktionen im Raster angezeigt.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf den Filter Kalender-Auswahl **[!UICONTROL Transaction dates]**.
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigt die Transaktionen für die angegebenen Daten im Raster an.

### Berichtinformationen filtern

In der Berichtsansicht Transaktionen können Sie die anzuzeigenden Statusergebnisse filtern, indem Sie Filterkriterien auswählen.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf die **[!UICONTROL Filter]**.
1. Schalten Sie die _[!UICONTROL Transaction Result]_&#x200B;ein, um die Berichtsergebnisse nur für ausgewählte Auftragstransaktionen anzuzeigen.
1. Schalten Sie die _[!UICONTROL Payment Method]_&#x200B;ein, um Berichtsergebnisse für die Art der Zahlung anzuzeigen, die für die Transaktion verwendet wird.
1. Schalten Sie die _[!UICONTROL Payment Detail]_&#x200B;ein, um zusätzliche Informationen zur verwendeten Zahlungsart anzuzeigen, sofern verfügbar.
1. Geben Sie einen _Mindestauftragsbetrag_ oder _Höchstauftragsbetrag_ ein, um die Berichtsergebnisse innerhalb dieses Auftragsbetragsbereichs anzuzeigen.
1. Geben Sie eine _[!UICONTROL Order ID]_&#x200B;ein, um nach einer bestimmten Transaktion zu suchen.
1. Stellen Sie die _[!UICONTROL Card Last Four]_&#x200B;vor, um nach einer bestimmten Kredit- oder Debitkarte zu suchen.
1. Geben Sie eine _[!UICONTROL Customer ID]_&#x200B;ein, um alle Transaktionen eines bestimmten Kunden anzuzeigen.
1. Geben Sie die _[!UICONTROL Customer Email]_&#x200B;ein, um Transaktionen für diese E-Mail zu filtern.
1. Klicken Sie auf **[!UICONTROL Hide filters]** , um den Filter auszublenden.

### Spalten ein- und ausblenden

Der Transaktionsbericht zeigt standardmäßig alle verfügbaren Informationsspalten an. Sie können jedoch anpassen, welche Spalten in Ihrem Bericht angezeigt werden.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf das **[!UICONTROL Column settings]**-Symbol ![Spalteneinstellungssymbol](assets/column-settings.png){width="20" zoomable="yes"}.
1. Um anzupassen, welche Spalten im Bericht angezeigt werden, aktivieren oder deaktivieren Sie die Spalten in der Liste.

   Der Transaktionsbericht zeigt sofort alle Änderungen an, die Sie im Menü Spalteneinstellungen vorgenommen haben. Die Spaltenvoreinstellungen werden gespeichert und bleiben wirksam, wenn Sie die Berichtsansicht verlassen.

### Berichtsdaten aktualisieren

Die Berichtsansicht Transaktionen zeigt einen _[!UICONTROL Last updated]_&#x200B;Zeitstempel an, der das letzte Mal anzeigt, dass die Berichtsinformationen aktualisiert wurden. Standardmäßig werden die Daten des Transaktionsberichts alle drei Stunden automatisch aktualisiert.

Sie können auch manuell eine Aktualisierung der Berichtsdaten erzwingen, um die aktuellsten Berichtsinformationen anzuzeigen.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf das _Aktualisieren_-Symbol (![Aktualisierungssymbol](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Die Daten des Transaktionsberichts werden aktualisiert, eine *[!UICONTROL Update complete]* wird angezeigt und die neuesten Informationen sind im Raster vorhanden.

### Transaktionen herunterladen

Sie können eine CSV-Datei herunterladen, in der alle Transaktionen im Raster der Transaktionsansicht sichtbar sind, unabhängig davon, ob Sie die standardmäßige 30-Tage-Transaktionsansicht oder einen benutzerdefinierten Zeitrahmen anzeigen.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. Wenn Sie Transaktionen für einen anderen Zeitraum als die letzten 30 Tage anzeigen möchten, [&#x200B; Sie den Zeitrahmen des Datumsbereichs für Ihre Status &#x200B;](#customize-dates-timeframe).
1. Klicken Sie auf _Symbol_ Herunterladen![Herunterladen](assets/icon-download.png){width="20" zoomable="yes"} .

Ihre Transaktionen werden im CSV-Format heruntergeladen.

### Spaltenbeschreibungen

Transaktionsberichte enthalten die folgenden Informationen.

| Spalte | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Commerce-Auftrags-ID (enthält nur Werte für erfolgreiche Transaktionen und ist leer für zurückgewiesene Transaktionen)<br> <br>Um zugehörige [Bestellinformationen) anzuzeigen](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/orders){target="_blank"} klicken Sie auf die ID. |
| [!UICONTROL PayPal Transaction ID] | Transaktions-ID vom Zahlungsdienstleister; enthält nur Werte für erfolgreiche Transaktionen und einen Bindestrich für abgelehnte Transaktionen. Sie können auf diese ID klicken, um auf die Seite mit den PayPal-Transaktionsdetails zuzugreifen. |
| [!UICONTROL Customer ID] | Commerce-Kunden-ID einer Bestellung<br> <br>Weitere Informationen finden Sie [&#x200B; Thema &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/customers/customer-accounts/account-create){target="_blank"}Kundeninformationen) . |
| [!UICONTROL Transaction Date] | Zeitstempel des Transaktionsdatums |
| [!UICONTROL Payment Method] | Art der Zahlung, die für die Transaktion verwendet wird, mit Informationen über Marke und Kartentyp. Siehe [Kartenarten](https://developer.paypal.com/docs/api/orders/v2/#definition-card_type) für weitere Informationen; verfügbar für Payment Services-Versionen 1.6.0 und höher |
| [!UICONTROL Payment Detail] | Enthält zusätzliche Informationen zur Art der Zahlung, die für die Transaktion verwendet wird, sofern verfügbar. |
| [!UICONTROL Card Last Four] | Letzte vier Stellen der für die Transaktion verwendeten Kredit- oder Debitkarten |
| [!UICONTROL Result] | Das Ergebnis der Transaktion - *[!UICONTROL OK]* (erfolgreiche Transaktion), *[!UICONTROL Rejected by Payment Provider]* (von PayPal abgelehnt), *[!UICONTROL Rejected by Bank]* (von der Bank, die die Karte ausgegeben hat, abgelehnt) |
| [!UICONTROL Response Code] | Fehlercode, der den Ablehnungsgrund des Zahlungsdienstleisters oder der Bank angibt; siehe Liste möglicher Antwort-Codes und Beschreibungen für [`Rejected by Bank` Status &#x200B;](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) den [`Rejected by Payment Provider` Status](https://developer.paypal.com/api/rest/reference/orders/v2/errors/). |
| [!UICONTROL AVS Code] | Adressverifizierungs-Service-Code; die Antwortinformationen des Prozessors für Zahlungsanfragen. Weitere Informationen [&#x200B; Sie unter „Liste möglicher Codes und &#x200B;](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response)&quot;. |
| [!UICONTROL CVV Code] | Kartenprüfwert-Code für Kredit- und Debitkarten; siehe [Liste möglicher Codes und Beschreibungen](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) für weitere Informationen. |
| [!UICONTROL Amount] | Bestellbetrag der Transaktion |
| [!UICONTROL Currency] | Für Bestellung in Transaktion verwendete Währung |
| [!UICONTROL Type] | [Zahlungsaktion](../payment-services/production.md#set-payment-services-as-payment-method) für Transaktion - `Authorize` oder `Authorize and Capture` |

### Fehlerantwort-Codes

Die _Antwort-Code_ Spalte zeigt einen bestimmten Fehler- oder Erfolgs-Code im Zusammenhang mit der Transaktion an. Zu den häufigen Fehlercodes, die angezeigt werden, gehören:

* `PAYMENT_DENIED`—Die Transaktion wurde von PayPal abgelehnt, da sie als Betrug verdächtigt wurde.
* `INTERNAL_SERVER_ERROR` - Transaktion wurde von PayPal abgelehnt und führte zu einem PayPal-Server-Fehler. Die Transaktion kann wiederholt werden.
* `INSTRUMENT_DECLINED` - Der Kunde wurde von PayPal für die ausgewählte Zahlungsmethode abgelehnt. Die Transaktion kann mit einer anderen Zahlungsmethode wiederholt werden.
* `9500`—Die Transaktion wurde von der zugehörigen Bank abgelehnt, da sie als Betrug verdächtigt wurde.
* `5120` - Die Transaktion wurde von der zugehörigen Bank abgelehnt, da der Kunde nicht über ausreichende Mittel für die Zahlung verfügte.
* `5650` - Die Transaktion wurde von der zugehörigen Bank abgelehnt, da die Bank eine starke Kundenauthentifizierung benötigt ([3DS](security.md#3ds)).

Detaillierte Fehler-Antwort-Codes für fehlgeschlagene Transaktionen sind für Transaktionen verfügbar, die neuer als der 1. Juni 2023 sind. Daten eines Teilberichts werden für Transaktionen angezeigt, die vor dem 1. Juni 2023 stattgefunden haben.
