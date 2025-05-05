---
title: Bericht zum Status der Bestellzahlung
description: Verwenden Sie den Bericht zum Zahlungsstatus von Bestellungen, um den Zahlungsstatus Ihrer Bestellungen einsehen und mögliche Probleme identifizieren zu können.
role: User
level: Intermediate
feature: Payments, Checkout, Orders
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '2045'
ht-degree: 0%

---

# Bericht zum Status der Bestellzahlung

[!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bietet Ihnen ein umfassendes Reporting, damit Sie einen klaren Überblick über die [Transaktionen](transactions.md) Bestellungen und Zahlungen Ihres Geschäfts erhalten.

Es gibt zwei verfügbare Berichtsansichten zum Zahlungsstatus von Bestellungen, mit denen Sie den Zahlungsstatus Ihrer Bestellungen schnell anzeigen können:

* **[Visualisierungsansicht für den Zahlungsstatus der Bestellung](#order-payment-status-data-visualization-view)** - Das Diagramm ist auf der Zahlungsdienste-Startseite verfügbar und stellt die aggregierten Zahlungsstatus pro Tag in der Berichtsansicht für den Zahlungsstatus der Bestellung dar
* **[Ansicht des Status der Bestellzahlung](#order-payment-status-report-view)** - Bericht verfügbar im Status der Bestellzahlung, der detaillierte Zahlungs-, Rechnungs-, Versand-, Rückerstattungs- und Streitfallstatus für alle Transaktionen anzeigt

Mithilfe der Statusansichten für die Bestellzahlung können Sie leicht erkennen, wo sich eine bestimmte Bestellung innerhalb des Order-to-Cash-Prozessflusses befindet. Diese Berichte ermöglichen es Ihnen, Bestellungen anhand ihres Zahlungsstatus und Zahlungsdatums schnell anzuzeigen und potenzielle Probleme zu identifizieren.

Sie können [Bestellzahlungsstatus herunterladen](#download-order-payment-statuses) in einem CSV-Dateiformat zur Verwendung in vorhandener Buchhaltungs- oder Auftragsverwaltungssoftware.

>[!NOTE]
>
>Sie können keine Finanzberichte anzeigen, wenn Sie den [Live-Modus aktiviert und aktiviert](production.md#enable-live-payments) für [!DNL Payment Services] nicht aktiviert haben.

## Visualisierungsansicht für Zahlungsstatus der Bestellung

Die Datenvisualisierungsansicht für den Status der Bestellzahlung ist auf der Zahlungsdienste-Startseite verfügbar. Es handelt sich um eine visuelle Darstellung der aggregierten Zahlungsstatus pro Tag aus der detaillierten tabellarischen [Bericht zum Status der Bestellzahlung](#order-payment-status-report-view).

Navigieren Sie in _Admin_-Seitenleiste zu **Verkauf** > **Zahlungsdienste** > _Bestellungen_, um die Datenvisualisierung anzuzeigen [Diagramm der Zahlungsstatus](#statuses-information).

![Visualisierung der Auszahlungsdaten in der Admin-](assets/orderpayment-dataviz.png){width="800" zoomable="yes"}

Klicken Sie auf **[!UICONTROL View Report]** , um zur detaillierten Tabelle [Berichtsansicht Bestellzahlungsstatus“ ](#order-payment-status-report-view).

### Anpassen des Zeitrahmens für Status

Standardmäßig werden 30 Tage Zahlungsstatus angezeigt.

In der Visualisierungsansicht für den Zahlungsstatus der Bestellung können Sie den Zeitrahmen für die Zahlungsstatus, die Sie anzeigen möchten, anpassen, indem Sie einen Datumsbereich auswählen:

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Die Datenvisualisierungsansicht für den Status der Bestellzahlung ist im Abschnitt _Bestellungen_ sichtbar.
1. Klicken Sie auf den Filter **[!UICONTROL Range]**.
1. Wählen Sie den entsprechenden Datumsbereich aus - 30 Tage, 15 Tage oder 7 Tage.
1. Statusinformationen für die angegebenen Daten anzeigen.

### Statusinformationen

Die Zahlungsstatus für einen ausgewählten Datumsbereich werden links neben der Datenvisualisierungsansicht für den Zahlungsstatus der Bestellung angezeigt. Die Datumsangaben für den ausgewählten Datumsbereich werden unten in der Ansicht angezeigt. Wenn zu einem bestimmten Datum keine Bestellungen vorhanden waren, wird dieses Datum nicht angezeigt.

Die Datenvisualisierungsansicht für den Status der Bestellzahlung enthält die folgenden Informationen.

| Daten | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Orders] | Betragsbereich für Bestellungen im angegebenen Zeitrahmen; Daten auf der Y-Achse (links) |
| Datumsbereich | Datumsbereich für den angegebenen Zeitrahmen; Daten auf der X-Achse (unten) |
| Zugelassen | Bestellung genehmigt |
| Erfassung angefordert | Erfassung für Bestellung angefordert |
| Erfassung bestätigt | Auftragserfassung abgeschlossen |
| Teilweise Erfassung | Teilweise erfasste Bestellung |
| Erfassung fehlgeschlagen | Auftragserfassung fehlgeschlagen |
| annulliert | Bestellung storniert |

## Berichtsansicht zum Status der Bestellzahlung

Die Berichtsansicht zum Status der Bestellzahlung ist in der Startansicht von Payment Services verfügbar. Es enthält detaillierte Status - Zahlung, Fakturierung, Versand, Rückerstattung, Streitigkeiten und mehr - für alle Transaktionen.

Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**, um die detaillierte Berichtsansicht zum Status der tabellarischen Bestellung anzuzeigen.

![Zahlungsstatusbuchungen in der Admin bestellen](assets/orders-report-data.png){width="800" zoomable="yes"}

Sie können diese Ansicht gemäß den Abschnitten in diesem Thema so konfigurieren, dass die Daten, die angezeigt werden sollen, am besten präsentiert werden.

Sie können [Auszahlungstransaktionen](#download-order-payment-statuses) im CSV-Dateiformat herunterladen, um sie in bestehender Buchhaltungs- oder Auftragsverwaltungssoftware zu verwenden.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden standardmäßig in absteigender Reihenfolge (`DESC`) mithilfe der `TRANS DATE` sortiert. Das `TRANS DATE` ist das Datum und die Uhrzeit, zu der die Transaktion initiiert wurde.

### Aktualisierungen des Zahlungsstatus

Bestimmte Zahlungsmethoden erfordern einen bestimmten Zeitraum, um die Zahlung zu erfassen. [!DNL Payment Services] erkennt jetzt den Status „Ausstehend“ einer Zahlungsoperation in einer Bestellung durch:

* Synchrone Erkennung `pending capture` Transaktionen
* Asynchrone Überwachung `pending capture` Transaktionen

>[!NOTE]
>
>Die Erkennung der ausstehenden Status von Zahlungsvorgängen in einer Bestellung verhindert, dass Bestellungen versehentlich versendet werden, wenn die Zahlung noch nicht eingegangen ist. Dies kann bei E-Check- und PayPal-Transaktionen auftreten.

#### Synchrone Erkennung ausstehender Erfassungstransaktionen

Erkennen Sie erfasste Transaktionen automatisch in einem `Pending` Status und verhindern Sie, dass Bestellungen einen `Processing` Status erhalten, wenn eine solche Transaktion erkannt wird.

Beim Kunden-Checkout oder wenn ein Administrator eine Rechnung für eine zuvor autorisierte Zahlung erstellt, erkennt [!DNL Payment Services] automatisch erfasste Transaktionen in einem `Pending` Status und wechselt die entsprechenden Bestellungen in `Payment Review` Status.

#### Asynchrone Überwachung ausstehender Erfassungstransaktionen

Erkennen, wann eine ausstehende Erfassungstransaktion in einen `Completed` eingeht, damit Händler die Verarbeitung der betroffenen Bestellung fortsetzen können.

Um sicherzustellen, dass dieser Prozess erwartungsgemäß funktioniert, müssen Händler einen neuen Cron-Auftrag konfigurieren. Sobald der Auftrag so konfiguriert ist, dass er automatisch ausgeführt wird, werden keine weiteren Eingriffe vom Händler erwartet.

Siehe [Konfigurieren von Cron-Aufträgen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html?lang=de). Nach der Konfiguration wird der neue Auftrag alle 30 Minuten ausgeführt, um Aktualisierungen für Bestellungen abzurufen, die sich im Status `Payment Review` befinden.

Händler können den aktualisierten Zahlungsstatus über die Berichtsansicht „Bestellzahlungsstatus“ überprüfen.

### Im Bericht verwendete Daten

[!DNL Payment Services] verwendet Bestelldaten und kombiniert sie mit aggregierten Zahlungsdaten aus anderen Quellen (einschließlich PayPal), um aussagekräftige und hochnützliche Berichte zu erstellen.

Bestelldaten werden exportiert und im Zahlungsdienst gespeichert. Wenn Sie [Bestellstatus ändern oder hinzufügen](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/order-status#custom-order-status) oder [eine Store-Ansicht ](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/store-views#edit-a-store-view), [Store](https://experienceleague.adobe.com/de/docs/commerce-admin/start/setup/store-details#store-information) oder den Website-Namen bearbeiten, werden diese Daten mit Zahlungsdaten kombiniert und der Bericht „Status der Bestellzahlung“ wird mit den kombinierten Informationen ausgefüllt.

Dieser Prozess umfasst zwei Schritte:

1. Der Index wird entweder `ON SAVE` (jedes Mal, wenn Bestellinformationen oder Speicherinformationen geändert werden) oder `BY SCHEDULE` (nach einem vorkonfigurierten Cron-Zeitplan) geändert, je nachdem, wie er in [Indexverwaltung](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/index-management) im Admin konfiguriert ist.

   Standardmäßig erfolgt die Datenindizierung `ON SAVE`, d. h. wenn sich etwas in der Bestellung, im Bestellstatus, in der Store-Ansicht, im Store oder auf der Website ändert, erfolgt die Neuindizierung sofort.

1. Die indizierten Daten werden an den Zahlungsdienst gesendet, der dann in den Bericht zum Status der Bestellzahlung eingefügt wird.

Die einzigen Daten, die zu Berichtszwecken exportiert und sortiert werden, sind Daten, die vom Bericht „Zahlungsstatus für Bestellungen“ verwendet werden.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden standardmäßig in absteigender Reihenfolge (`DESC`) mithilfe der `ORDER DATE` sortiert. Das `ORDER DATE` ist der Datums-/Zeitstempel, an dem die Bestellung erstellt wurde.

#### Konfigurieren des Datenexports

Obwohl die Neuindizierung standardmäßig im `ON SAVE` erfolgt, wird empfohlen, die Indizierung im `BY SCHEDULE`-Modus durchzuführen. Der `BY SCHEDULE`-Index wird nach einem Cron-Zeitplan von einer Minute ausgeführt, und alle geänderten Daten werden innerhalb von zwei Minuten nach einer Datenänderung in Ihrem Bestellstatusbericht angezeigt. Diese geplante Neuindizierung hilft Ihnen, die Belastung Ihres Geschäfts zu reduzieren, insbesondere wenn Sie eine große Menge an eingehenden Bestellungen haben, da sie nach einem Zeitplan erfolgt (nicht bei jeder Bestellung).

Sie können den Indexmodus - `ON SAVE` oder `BY SCHEDULE` - [ Admin ](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).

Informationen zum Konfigurieren des Datenexports finden Sie unter [Befehlszeilenkonfiguration](configure-cli.md#configure-data-export).

### Datenquelle auswählen

In der Berichtsansicht zum Status der Bestellzahlung können Sie die Datenquelle - **[!UICONTROL Live]** _ oder **[!UICONTROL Sandbox]** - auswählen, für die Sie Berichtsergebnisse anzeigen möchten.

![Datenquellenauswahl](assets/datasource.png){width="300" zoomable="yes"}

Wenn _[!UICONTROL Live]_&#x200B;die ausgewählte Datenquelle ist, können Sie Berichtsinformationen für Ihre Stores anzeigen, die [!DNL Payment Services] im Produktionsmodus verwenden. Wenn&#x200B;_[!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Berichtsinformationen für den Sandbox-Modus angezeigt werden.

Die Auswahl von Datenquellen funktioniert wie folgt:

* Wenn Sie keine Stores haben, die [!DNL Payment Services] im Live-Modus verwenden, ist die Datenquellenauswahl standardmäßig auf _[!UICONTROL Sandbox]_&#x200B;eingestellt.
* Wenn Sie über Stores (einen oder mehrere) verfügen, die [!DNL Payment Services] im Live-Modus verwenden, ist die Datenquellenauswahl standardmäßig auf _[!UICONTROL Live]_&#x200B;eingestellt.
* Berichtsexporte berücksichtigen immer die Auswahl der Datenquelle.

So wählen Sie die Datenquelle für Ihren [!UICONTROL Order Payment Status] aus:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Orders]** > **[!UICONTROL View Report]**.
1. Klicken Sie auf den Filter _[!UICONTROL Data source]_&#x200B;und wählen Sie **[!UICONTROL Live]**&#x200B;oder **[!UICONTROL Sandbox]**&#x200B;aus.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

### Zeitrahmen für Bestelldaten anpassen

In der Berichtsansicht zum Status von Bestellungen können Sie den Zeitrahmen der Statusergebnisse anpassen, die Sie anzeigen möchten, indem Sie bestimmte Daten auswählen. Standardmäßig werden 30 Tage Zahlungsstatus im Raster angezeigt.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf den Filter Kalender-Auswahl _[!UICONTROL Order dates]_.
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigen Sie die Status der Bestellzahlungen für Ihre angegebenen Daten im Raster an.

### Berichtinformationen filtern

In der Berichtsansicht zum Status der Bestellzahlung können Sie die anzuzeigenden Statusergebnisse filtern, indem Sie Filterkriterien auswählen.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf die **[!UICONTROL Filter]**.
1. Schalten Sie die _Zahlungsstatus_ ein, um Berichtsergebnisse nur für ausgewählte Zahlungsstatus anzuzeigen.
1. Berichtsergebnisse innerhalb eines Bestellbetragsbereichs durch Eingabe eines _[!UICONTROL Min Order Amount]_&#x200B;oder _[!UICONTROL Max Order Amount_] anzeigen.
1. Klicken Sie auf **[!UICONTROL Hide filters]** , um den Filter auszublenden.

### Spalten ein- und ausblenden

Die Auswertung „Zahlungsstatus der Bestellung“ zeigt standardmäßig alle verfügbaren Spalten mit Informationen an. Sie können jedoch anpassen, welche Spalten in Ihrem Bericht angezeigt werden.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf das _Spalteneinstellungen_-Symbol (![Spalteneinstellungssymbol](assets/column-settings.png){width="20" zoomable="yes"}).
1. Um anzupassen, welche Spalten im Bericht angezeigt werden, aktivieren oder deaktivieren Sie die Spalten in der Liste.

   Der Bericht zum Status der Bestellzahlung zeigt sofort alle Änderungen an, die Sie im Menü Spalteneinstellungen vorgenommen haben. Die Spaltenvoreinstellungen werden gespeichert und bleiben wirksam, wenn Sie die Berichtsansicht verlassen.

### Anzeigen von Status

Die Berichtsansicht „Bestellzahlungsstatus“ zeigt umfassende Zahlungsstatusinformationen für jede Bestellung an.

Standardmäßig werden 30 Tage Zahlungsstatus im Raster angezeigt.

Scrollen Sie nach links und rechts, um [Informationen zum Bestellzahlungsstatus](#column-descriptions) einschließlich Bestelldatum, autorisiertem Datum, Rechnungsdatum, Versand, Zahlungsstatus und mehr anzuzeigen.

Die Anzahl der Zeilen, die bei einer Suche zurückgegeben oder standardmäßig in den Status von 30 Tagen für die Bestellzahlung angezeigt werden, wird über dem Ansichtsraster für den Status der Bestellzahlung zusammen mit dem Auswahlfilter für den Bestelldatums-Kalender angezeigt.

#### Lohnstatus

Die Spalte Zahlungsstatus zeigt den aktuellen Status für jede Zahlung an. Eine `Capture failed` zeigt einen roten Warnstatus und eine `Voided` einen grauen Warnstatus an.

#### Erstattungsstatus

Die Spalte Erstattungsstatus zeigt den aktuellen Status für jede Erstattung an. Eine `Capture failed` zeigt einen roten Warnstatus und eine `Voided` einen grauen Warnstatus an.

### Berichtsdaten aktualisieren

Die Berichtsansicht zum Status der Bestellzahlung zeigt einen _[!UICONTROL Last updated]_&#x200B;Zeitstempel an, der das letzte Mal anzeigt, dass die Berichtsinformationen aktualisiert wurden. Standardmäßig werden die Berichtsdaten zum Status der Bestellzahlung alle drei Stunden automatisch aktualisiert.

Sie können auch manuell eine Aktualisierung der Berichtsdaten zum Status der Bestellzahlung erzwingen, um die aktuellsten Berichtsinformationen anzuzeigen.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf das _Aktualisieren_-Symbol (![Aktualisierungssymbol](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Die Berichtsdaten zum Status der Bestellzahlung werden aktualisiert, eine *[!UICONTROL Update complete]* wird angezeigt und die neuesten Informationen sind im Raster vorhanden.

### Streitigkeiten anzeigen

Sie können alle Streitigkeiten über die Bestellungen in Ihrem Geschäft anzeigen und zum PayPal-Lösungszentrum navigieren, um entsprechende Maßnahmen zu ergreifen, und zwar über den Bericht zum Status der Bestellzahlung.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Navigieren Sie zum **[!UICONTROL Disputes column]**.
1. Zeigen Sie alle Streitigkeiten für eine bestimmte Bestellung an und lesen Sie [Streitstatus](#order-payment-status-information).
1. Überprüfen Sie die Details der Streitigkeit vom [PayPal-Lösungszentrum](https://www.paypal.com/us/cshelp/article/what-is-the-resolution-center-help246), indem Sie auf den Link für die Streitfall-ID klicken, der mit _PP-D-_ beginnt.
1. bei Bedarf geeignete Maßnahmen in Bezug auf die Streitigkeit zu ergreifen.

   Um Streitigkeiten nach Status zu sortieren, klicken Sie auf die [!UICONTROL Disputes] Spaltenüberschrift.

### Zahlungsstatus für Bestellung herunterladen

Sie können eine CSV-Datei herunterladen, deren Status im Ansichtsraster „Zahlungsstatus“ der Bestellung angezeigt werden, unabhängig davon, ob Sie die standardmäßigen Statuswerte von 30 Tagen oder einen benutzerdefinierten Zeitrahmen anzeigen.

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Wenn Sie Status für einen anderen Zeitraum als die letzten 30 Tage anzeigen möchten, [passen Sie den Zeitrahmen des Datumsbereichs für Ihre Status an](#customize-dates-timeframe).
1. Klicken Sie auf _Symbol_ Herunterladen![ (](assets/icon-download.png){width="20" zoomable="yes"}).

Der Status der Bestellzahlung wird im CSV-Format heruntergeladen.

### Spaltenbeschreibungen

Die Berichte zum Status der Bestellzahlung enthalten die folgenden Informationen.

| Spalte | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Commerce-Auftrags-ID<br> <br>Um zugehörige [Bestellinformationen) anzuzeigen](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/orders){target="_blank"} klicken Sie auf die ID. |
| [!UICONTROL Order Date] | Zeitstempel des Bestelldatums |
| [!UICONTROL Authorized Date] | Datum/Zeitstempel der Zahlungsermächtigung |
| [!UICONTROL Order Status] | Aktuelle Commerce [Bestellstatus](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/order-status){target="_blank"} |
| [!UICONTROL Invoiced] | Rechnungsstatus der Bestellung - *[!UICONTROL No]*, *[!UICONTROL Partial]* oder *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Versandstatus der Bestellung - *[!UICONTROL No]*, *[!UICONTROL Partial]* oder *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Gesamtbetrag der Bestellung |
| [!UICONTROL Cur] | Währungstyp des Auftrags |
| [!UICONTROL Pay Status] | Status der Zahlung für einen bestimmten Auftrag |
| [!UICONTROL Paid Amt] | Für eine Bestellung gezahlter Betrag |
| [!UICONTROL Cur] | Währungstyp des für eine Bestellung gezahlten Betrags |
| [!UICONTROL Refund Status] | Status einer Rückerstattung bei einer Bestellung (z. B. Informationen aus Rücksendungen, RMAs und Gutschriften)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]* oder *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Summe des zurückerstatteten Betrags für eine Bestellung |
| [!UICONTROL Cur] | Währungstyp des für eine Bestellung zurückgezahlten Betrags |
| [!UICONTROL Disputes] | Status aller Streitigkeiten über eine Bestellung (Informationen aus Streitigkeiten und Rückbelastungen) - *[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]* oder *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | In der Commerce-Transaktion für eine Bestellung verwendete Zahlungsmethode |
| [!UICONTROL Website] | Website, von der aus die Bestellung aufgegeben wurde |
| [!UICONTROL Store] | Store, aus dem die Bestellung aufgegeben wurde |
| [!UICONTROL Store View] | Store-Ansicht, von der aus die Bestellung aufgegeben wurde |
