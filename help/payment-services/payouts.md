---
title: Bericht zu Auszahlungen
description: Verwenden Sie die Auswertung „Auszahlungen“ für vollständige Transparenz bezüglich des Zahlungsbetrags, des verarbeiteten Volumens und der detaillierten Berichterstellung auf Transaktionsebene zur finanziellen Abstimmung.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
feature: Payments, Checkout, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '1303'
ht-degree: 0%

---

# Bericht zu Auszahlungen

[!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bietet Ihnen ein umfassendes Reporting, damit Sie einen klaren Überblick über die Transaktionen, Bestellungen und Zahlungen Ihres Stores erhalten.

Es gibt zwei verfügbare Auszahlungs-Berichtsansichten, mit denen Sie detaillierte Informationen zu allen Ihren Auszahlungen sehen können:

* **[Datenvisualisierungsansicht für Auszahlungen](#payouts-data-visualization-view)** - Auf der Zahlungsdienste-Startseite verfügbares Diagramm, das eine visuelle Darstellung der aggregierten Beträge pro Tag aus der Auszahlungsansicht darstellt
* **[Auszahlungsbericht-Ansicht](#payouts-report-view)** - Bericht verfügbar in Auszahlungen, der detaillierte Auszahlungsinformationen für alle Transaktionen anzeigt

Die Auszahlungsansichten zeigen umfassende Auszahlungsinformationen auf einen Blick, sodass Sie vollständige Transparenz hinsichtlich des Zahlungsbetrags, des verarbeiteten Volumens und eine detaillierte Berichterstellung auf Transaktionsebene für die finanzielle Abstimmung erhalten.

Sie können [Auszahlungstransaktionen](#download-transactions) im CSV-Dateiformat herunterladen, um sie in bestehender Buchhaltungs- oder Auftragsverwaltungssoftware zu verwenden.

>[!NOTE]
>
>Auszahlungsberichte zeigen nur Bestellungen an, die erfasst (Zahlungsaktion ist auf [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html?lang=de#set-payment-services-as-payment-method) eingestellt) - oder [ als `Invoiced`](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) markiert sind.

## Datenvisualisierungsansicht für Auszahlungen

Die Datenvisualisierungsansicht „Auszahlungen“ ist auf der Startseite der Zahlungs-Services verfügbar. Es ist eine visuelle Darstellung der aggregierten Beträge pro Tag aus der detaillierten tabellarischen [Auszahlungsbericht-Ansicht](#payouts-report-view).

Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** , um das Datenvisualisierungsdiagramm der Einnahmen im Vergleich zu den Ausgaben und der gleitenden Durchschnittswerte im Zeitverlauf anzuzeigen.

![Visualisierung der Auszahlungsdaten in der Admin-](assets/payouts-report.png){width="800" zoomable="yes"}

Klicken Sie auf **[!UICONTROL View Report]** , um zur detaillierten Tabelle [Berichtsansicht „Auszahlungen](#payouts-report-view) zu navigieren.

### Zeitrahmen der Transaktionen anpassen

Standardmäßig werden 30 Tage Transaktionen angezeigt.

In der Datenvisualisierungsansicht „Auszahlungen“ können Sie den Zeitrahmen für die Auszahlungstransaktionen anpassen, die Sie anzeigen möchten, indem Sie einen Datumsbereich auswählen:

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Die Datenvisualisierungsansicht „Auszahlungen“ ist im Abschnitt „Auszahlungen“ sichtbar.
1. Klicken Sie auf den Filter **[!UICONTROL Range]**.
1. Wählen Sie den entsprechenden Datumsbereich aus - 30 Tage, 15 Tage oder 7 Tage.
1. Zeigen Sie die Transaktionsinformationen für Ihre angegebenen Daten an.

### Transaktionsinformationen

Die Transaktionsbeträge für einen ausgewählten Datumsbereich werden links in der Datenvisualisierungsansicht „Auszahlungen“ angezeigt. Die Datumsangaben für den ausgewählten Datumsbereich werden unten in der Ansicht angezeigt. Wenn es an einem bestimmten Datum keine Auszahlungen gab, wird dieses Datum nicht angezeigt.

Die Datenvisualisierungsansicht „Auszahlungen“ enthält die folgenden Informationen.

| Daten | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | Betragsbereich für Transaktionen im angegebenen Zeitrahmen; Daten auf der Y-Achse (links) |
| Datumsbereich | Datumsbereich für den angegebenen Zeitrahmen; Daten auf der X-Achse (unten) |
| Kredit | Zahlungen für den angegebenen Zeitraum |
| Sollseite | Belastungen (Rückerstattungen) für den angegebenen Zeitraum |
| Gleitender Mittelwert | Darstellung der durchschnittlichen Auszahlung für jedes Datum im angegebenen Zeitrahmen |
| Netto für Bereich | Nettoauszahlungsbetrag für den angegebenen Zeitrahmen (Bereich) |

## Berichtsansicht „Auszahlungen“

Die Ansicht Auszahlungen ist in der Ansicht Auszahlungen von Zahlungs-Services verfügbar. Es enthält alle verfügbaren Informationen über Auszahlungen für Ihr Geschäft/Ihre Geschäfte.

Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**, um die detaillierte Berichtsansicht „Tabellenauszahlungen“ anzuzeigen.

![Auszahlungstransaktionen im Admin](assets/payouts-report-new.png){width="800" zoomable="yes"}

Sie können diese Ansicht gemäß den Abschnitten in diesem Thema so konfigurieren, dass die Daten, die angezeigt werden sollen, am besten präsentiert werden.

In diesem Bericht werden verknüpfte Commerce-Auftrags- und Transaktions-IDs, Transaktionsbeträge, Zahlungsmethoden pro Transaktion und mehr angezeigt.

Sie können [Auszahlungstransaktionen](#download-transactions) im CSV-Dateiformat herunterladen, um sie in bestehender Buchhaltungs- oder Auftragsverwaltungssoftware zu verwenden.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden standardmäßig in absteigender Reihenfolge (`DESC`) mithilfe der `TRANS DATE` sortiert. Das `TRANS DATE` ist das Datum und die Uhrzeit, zu der die Transaktion initiiert wurde.

### Datenquelle auswählen

In der Berichtsansicht „Zahlungen“ können Sie die Datenquelle (**[!UICONTROL Live]** oder **[!UICONTROL Sandbox]**) auswählen, für die Sie Berichtsergebnisse anzeigen möchten.

![Datenquellenauswahl](assets/datasource.png){width="300" zoomable="yes"}

Wenn _[!UICONTROL Live]_&#x200B;die ausgewählte Datenquelle ist, können Sie Berichtsinformationen für Stores im Produktionsmodus anzeigen. Wenn&#x200B;_[!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Sie Berichtsinformationsspeicher im Sandbox-Modus sehen.

Die Auswahl von Datenquellen funktioniert wie folgt:

* Wenn Sie keine Stores haben, die sich im Live-Modus befinden, ist die Datenquellenauswahl standardmäßig auf _[!UICONTROL Sandbox]_&#x200B;eingestellt.
* Wenn Sie Stores (einen oder mehrere) im Live-Modus haben, ist die Datenquellenauswahl standardmäßig auf _[!UICONTROL Live]_&#x200B;eingestellt.
* Berichtsexporte berücksichtigen immer die Auswahl der Datenquelle.

So wählen Sie die Datenquelle für die Auswertung „Zahlungsstatus der Bestellung“ aus:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf **[!UICONTROL Data source]** und wählen Sie **[!UICONTROL Live]** oder **[!UICONTROL Sandbox]** aus.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

### Buchungen anzeigen

Standardmäßig werden 30 Tage Transaktionen angezeigt.

Die Anzahl der Zeilen, die bei einer Suche zurückgegeben oder in den standardmäßigen 30 Tagen von Transaktionen angezeigt werden, wird über dem Ansichtsraster „Auszahlungen“ neben dem Kalenderauswahlfilter „Transaktionsdaten“ angezeigt.

Scrollen Sie nach links und rechts, um [Informationen für jede Auszahlungstransaktion](#column-descriptions) im täglichen Bericht anzuzeigen, einschließlich Transaktionsdatum, Referenz-ID, Rechnungsnummer und Details zur Zahlungsmethode.

#### Zeitrahmen der Transaktionen anpassen

In der Berichtsansicht „Auszahlungen“ können Sie den Zeitrahmen für die Auszahlungstransaktionen anpassen, die Sie anzeigen möchten, indem Sie bestimmte Daten eingeben oder einen Datumsbereich aus der Datumsauswahl auswählen:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf den Filter Kalender-Auswahl _[!UICONTROL Transaction dates]_.
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigen Sie die Status der Auszahlungen im Raster für Ihre angegebenen Daten an.

### Spalten ein- und ausblenden

Die Berichtsansicht „Auszahlungen“ zeigt standardmäßig die meisten verfügbaren Informationsspalten an. Sie können jedoch anpassen, welche Spalten im Bericht angezeigt werden.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf das _Spalteneinstellungen_-Symbol (![Spalteneinstellungssymbol](assets/column-settings.png){width="20" zoomable="yes"}).
1. Um anzupassen, welche Spalten im Bericht angezeigt werden, aktivieren oder deaktivieren Sie die Spalten in der Liste.

   Die Berichtsansicht „Auszahlungen“ zeigt sofort alle Änderungen an, die Sie im Menü Spalteneinstellungen vorgenommen haben. Die Spaltenvoreinstellungen werden gespeichert und bleiben wirksam, wenn Sie die Berichtsansicht verlassen.

### Transaktionen herunterladen

Sie können eine CSV-Datei herunterladen, die alle Transaktionen enthält, die im Raster der Auszahlungsansicht sichtbar sind.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. [Passen Sie den Zeitrahmen des Datumsbereichs für Ihre Transaktionen an](#customize-transactions-timeframe).
1. Klicken Sie auf _Symbol_ Herunterladen![ (](assets/icon-download.png){width="20" zoomable="yes"}).

Ihre Auszahlungstransaktionen werden im CSV-Format heruntergeladen.

### Spaltenbeschreibungen

Auszahlungsberichte enthalten die folgenden Informationen.

| Spalte | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Zahlungsdienstleister |
| [!UICONTROL Provider trans] | Transaktions-ID |
| [!UICONTROL Trans date] | Datum und Uhrzeit der Initiierung der Transaktion |
| [!UICONTROL Type] | Transaktionstyp: *[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL REFUND]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REVERSAL]* *[!UICONTROL WITHDRAWAL]*, <br> <br>Siehe [Transaktionstypen](#transaction-types) für weitere Informationen. |
| [!UICONTROL Status] | Aktueller Status der Transaktion - *[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Transaktionscode, der entweder „Guthaben“ (*CR*) oder „Soll“ (*DR*) angibt |
| [!UICONTROL Reference ID] | Ursprüngliche Transaktions-ID, mit der dieses Ereignis verknüpft ist |
| [!UICONTROL Invoice] | Rechnungskennung (eine pro Bestellung) der Transaktion |
| [!UICONTROL Commerce order] | Commerce-Auftrags-ID <br> <br>Um zugehörige [Bestellinformationen) anzuzeigen](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/orders) klicken Sie auf die ID. |
| [!UICONTROL Commerce trans] | Commerce Transaktions-ID |
| [!UICONTROL Pay method] | Kreditkartenart - *[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]* - und dazugehöriger Kartenanbieter (z. B *Visa* oder *MasterCard*) |
| [!UICONTROL TRANS AMT] | Transaktionsbetrag |
| [!UICONTROL CUR] | Währungseinheit für Transaktionsbetrag |
| [!UICONTROL PENDING] | Auszuzahlender Betrag |
| [!UICONTROL CUR] | Währungseinheit für den ausstehenden Betrag |
| [!UICONTROL SELLER AMT] | Betrag der an oder von einem <br> übertragenen Mittel <br>Beträge, die aus dem Verkäuferkonto ausgezahlt werden, haben das Präfix DASH (-). |
| [!UICONTROL CUR] | Währungseinheit für den Verkäuferbetrag |
| [!UICONTROL PARTNER FEE] | Mit der <br> verbundene Partnergebühren <br>Mittel, die aus dem Partnergebührenkonto ausgezahlt werden, weisen ein Bindestrich (-) als Präfix auf. |
| [!UICONTROL CUR] | Währungseinheit für die Partnergebühr |
| [!UICONTROL PROV FEES] | Mit der <br> verbundene Gebühren <br>Mittel, die aus dem Gebührenkonto des Anbieters ausgezahlt werden, weisen das Präfix DASH (-) auf. |
| [!UICONTROL CUR] | Währungseinheit für die Providergebühr |
| [!UICONTROL FEE %] | Prozentsatz des als Gebühr in Rechnung gestellten Transaktionsbetrags |
| [!UICONTROL FIXED FEE] | Fester Provisionsbetrag des Anbieters |
| [!UICONTROL CHBK FEE] | Dem <br> zugeordnete Rückbelastungsgebühr <br>Ein Bindestrich (-) zeigt an, dass die Rückbelastungsgebühr umgekehrt wurde. |
| [!UICONTROL CUR] | Währungseinheit für die Rückbelastungsgebühr |
| [!UICONTROL HOLD AMT] | Zurückgestellter oder aus der Zurückstellung freigegebener Betrag <br> <br>Ein Bindestrich (-) gibt an, dass zurückgestellte Mittel freigegeben werden. |
| [!UICONTROL CUR] | Währungseinheit für den Sperrbetrag |
| [!UICONTROL RECOUP AMT] | Aus dem <br> ausgezahlter Betrag <br>Mittel, die aus dem Rückzahlungskonto ausgezahlt werden, zeigen ein Bindestrichpräfix (-) an. |
| [!UICONTROL CUR] | Währungseinheit für den Rückzahlungsbetrag |

### Transaktionsarten

Diese Transaktionstypen können in den Auszahlungstransaktionen vermerkt werden.

| Bericht | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Geld zwischen einem Käufer und einem Verkäufer für eine Bestellung verschoben |
| [!UICONTROL AUTH] | Autorisierung und Autorisierung ungültiger Transaktionen |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | Rückbelastungsgebühren und Rückbelastungsgebühren-Rückbuchungen |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | Partnergebühren, Zahlungsgebühren und Gebührenumkehrtransaktionen |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | Rückzahlungen aus Bank- oder Verlustkonten |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
