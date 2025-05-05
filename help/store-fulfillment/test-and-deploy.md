---
title: Testen und Bereitstellen der Store-Erfüllung
description: Testplan zur Überprüfung der Store-Erfüllungsfunktion. Die Tests umfassen die Inventarsynchronisierungs-API, den End-to-End-Erfüllungs-Workflow für stornierte Bestellungen, die Benutzerverwaltung der Store-Fulfillment-App und das Eincheckerlebnis des Kunden.
role: User, Admin
level: Intermediate
feature: Shipping/Delivery, User Account, Roles/Permissions
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 0%

---

# Testen und Bereitstellen von Store Fulfillment für Adobe Commerce

Nachdem Sie den Onboarding-Prozess in Ihrer Entwicklungsumgebung abgeschlossen haben, können Sie den Prozess starten, um die Store Fulfillment-Lösung zu testen und in Ihrer Produktionsumgebung bereitzustellen.

**Voraussetzungen**

Stellen Sie vor dem Testen oder Synchronisieren von Informationen, Speichern oder Bestellungen sicher, dass Sie die folgenden Aufgaben ausgeführt haben:

- Die [Allgemeine Konfiguration“ ](enable-general.md) Store-Fulfillment-Services wurde abgeschlossen.

- [Hinzufügen und Validieren der Kontoanmeldeinformationen und Verbindungsdetails für Ihre Sandbox- und Produktionsumgebung](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- Vergewissern Sie sich, dass die [Adobe Commerce Integration](connect-set-up-service.md#configure-store-fulfillment-account-credentials) für die Store Fulfillment-Lösung verfügbar und autorisiert ist.

## Vorbereiten der Tests

Die Verbindungskonfiguration muss abgeschlossen sein, bevor Sie Testaufträge erstellen oder Integrationstests durchführen können. Vor dem Testen müssen Sie auch überprüfen, ob Ihre Speicherdaten synchronisiert sind.

1. Synchronisieren Sie die Quellen für die Store-Erfüllung.

   - Gehe zu **[!UICONTROL Stores > Sources]**.

   - Wählen Sie **[!UICONTROL Synchronize Store Fulfillment Sources]** aus.

1. Überprüfen Sie im Store-Raster, ob Stores als `Synced` gekennzeichnet wurden, bevor Sie Testaufträge erstellen.

## Beispieltestplan

Einzelhändler überprüfen die grundlegenden Funktionen der Store Fulfillment-Lösung während der Konfigurations- und Testphasen einer Bereitstellung. Dieser Beispieltestplan bietet einen Ausgangspunkt für Tests. Fügen Sie je nach Ihren Anforderungen weitere Szenarien hinzu.

>[!NOTE]
>
>Testen Sie nach Abschluss des anfänglichen Onboardings für die Store Fulfillment-Lösung oder nach Aktualisierung einer vorhandenen Installation die Anwendung immer in einer Nicht-Produktionsumgebung, bevor Sie sie in der Produktion bereitstellen.

Dieser Musterprüfplan deckt die folgenden Funktionsbereiche ab:

| Funktionsbereich | Funktion | Rolle |
|-------------------------------------|------------------------------------------|----------------------------------|
| Inventar- und Auftragssynchronisierung | Inventar-API-Synchronisierung | Adobe Commerce Admin |
| End-to-End | Workflows für Auftragsstornierungen | Kunde, Admin, Store Associate |
| Administrator | Fulfillment-App-Berechtigungen speichern | Administrator |
| Adobe Commerce Frontend | Produktarten | Kunde, Administrator |
| Frontend-</br>-Formular | Eincheckerlebnis | Kunde, Administrator |
| Store-Assist-App | Bestellung</br>Auswahl</br>Phase</br>und Übergabe | Geschäftspartner |

### Inventar-API-Synchronisierung

In diesem Abschnitt des Testplans wird die Synchronisierung von Bestand und Bestellung behandelt, um sicherzustellen, dass Aktualisierungen der Abholquellen und Lager zwischen Adobe Commerce und der Store Fulfillment-Lösung korrekt synchronisiert werden.

**Funktionsbereich**: Inventar- und Auftragssynchronisierung</br>
**Rolle:** Admin</br>
**Testtyp:** positiv

<table>
<thead>
<tr>
<th>Funktion</th>
<th>Testszenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Lagerquelle für Abholung hinzufügen</strong></td>
<td>Speichern Sie eine neue Lagerquelle für die Abholung.</td>
<td>Die Echtzeit-Synchronisierung sendet die Quelldetails innerhalb von 5 Minuten an den Walmart GIF-Service.</td>
</tr>
<tr>
<td><strong>Vorhandene Lagerquelle der Abholung aktualisieren</strong></td>
<td>Aktualisierungen an einer vorhandenen Lagerabholquelle speichern.</td>
<td>Der Echtzeit-Synchronisierungsvorgang sendet die Details innerhalb von 5 Minuten an die Walmart GIF</td>
</tr>
<tr>
<td><strong>Lagerquelle </br><code>Is Synced</code> Lagerabholung</strong></td>
<td>Aktualisierungen an einer vorhandenen Lagerabholquelle speichern.</td>
<td>Nach einem erfolgreichen Vorgang wird die Spalte <code>Is Synced</code> der Seite Source verwalten von <code>No</code> auf <code>Yes</code> aktualisiert.</td>
</tr>
<tr>
<td><strong>Geänderter Lagerreservierungsprozess</strong></td>
<td>Neue Bestellung für ein Produkt erstellen und übermitteln.</td>
<td>Die verkaufsfähige Menge für das Produkt nimmt entsprechend ab.</td>
</tr>
<tr>
<td><strong>Neue Auftrags-Push-, API-Synchronisierung - Kundenbestellung</strong></td>
<td>Der Kunde reicht einen Abholauftrag für ein Geschäft ein.</td>
<td><ul><li>In der Ansicht „Admin-Auftrag“ sieht ein <strong>Adobe Commerce-Administrator</strong>, dass der Status der Auftragssynchronisierung auf aktualisiert wurde <code>Sent</code></li><li>Das Protokoll mit den Bestelldetails enthält die Meldung <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Neue Push-Bestellung, API-Synchronisation - Administrator reicht Bestellung ein</strong></td>
<td>Ein Adobe Commerce <strong>Administrator</strong> reicht einen Abholauftrag ein.</td>
<td><ul><li>In der Ansicht „Admin-Auftrag“ wird der Status der Auftragssynchronisierung auf <code>Sent</code> aktualisiert.</li><li>Das Protokoll mit den Bestelldetails enthält die Meldung <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Neue Auftrags-Push-Benachrichtigung, Ausnahmewarteschlange<strong></td>
<td>Identifizieren Sie mehrere virtuelle und herunterladbare Produkte in Adobe Commerce Admin, die über Adobe Commerce ausgeführt werden können, ohne dass eine Interaktion mit Fulfillment Service (FAAs) erforderlich ist.</td>
<td>Diese Produkte werden im Export entsprechend entfernt oder gekennzeichnet, um einen nachgelagerten Konflikt mit den FAAs zu vermeiden.</td>
</tr>
</tbody>
</table>

### Workflows für Auftragsstornierungen

Dieser Abschnitt des Testplans enthält Szenarien, in denen der End-to-End-Workflow für Bestellungen getestet wird, die über Adobe Commerce storniert wurden.

**Funktionsbereich:** Adobe Commerce Admin</br>
**Rolle:** End-to-End (Admin, Store Associate, Kunde)</br>
**Testergebnistyp:** für alle Szenarien positiv

<table style="table-layout:fixed">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td><strong>Vollständige Stornierung der Bestellung</strong></td>
<td><ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie den Empfang der Rechnungs-E-Mail auf die Erstellung der Rechnung (sofern autorisiert und erfasst).</li>
<li>Erstellen Sie eine Gutschrift mit allen bestellten Produkten aus der Ansicht Rechnung .</li>
</ol>
</td>
<td>
<ul>
<li>Auftragsverlauf aktualisiert mit <code>We refunded $X online. Transaction ID: transactionID</code> und <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>Bestellstatus ist <code>Closed</code>. (Wir haben jetzt PAYMENT REVIEW festgelegt.)</li>
<li>Gutschrift in Adobe Commerce erstellt. (Warten Sie, bis Cron funktioniert.)</li>
<li>Wenn alle Artikel ausgewählt wurden, zeigt die <code>DISPLAY COMMENT HISTORY</code> „Bereit für Abholung“ <code>Order is ready for pickup</code> an (<code>CUSTOMER NOTIFIED</code> Markierung ist <code>true</code>.)</li>
<li>Wenn nicht alle Elemente ausgewählt sind, werden Abbruchs-E-Mail und KOMMENTARVERLAUF ANZEIGEN angezeigt <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> Markierung ist <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>Teilstornierung der Bestellung<strong></td>
<td>
<ol>
<li>Bestellung mit mindestens zwei Produkten aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (sofern autorisiert und erfasst) und ob die Rechnung per E-Mail empfangen wurde.</li>
<li>Zwei Stunden auf die Transaktionsabrechnung warten.</li>
<li>Erstellen Sie eine Gutschrift, wenn nur ein Teil der bestellten Produkte in der Ansicht „Rechnung“ angezeigt wird.</li>
</td>
<td>
<ul>
<li>Update des Bestellverlaufs: <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>Update des Bestellverlaufs: <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>Erhalt der E-Mail zur Bestellrückerstattung: <code>$x amount was refunded</code></li>
<li>Bestellstatus ist <code>Processing</code>.</li>
<li>Gutschrift in Adobe Commerce erstellt (warten, bis Cron funktioniert).</li>
<li>Wenn einige Artikel nicht ausgewählt wurden, bestätigen Sie, dass die [!UICONTROL Ready for Pickup]-E-Mail mit dem Abschnitt „Keine Auswahl“ oder „Rückerstattung“ angezeigt wird. <code>DISPLAY COMMENT HISTORY</code> zeigt <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> Markierung ist <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>Bereit für Abholung</br></br>vollständige Stornierung</br>(alle Produkte werden mit 0 Menge abgeholt)</strong></td>
<td>
<ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (sofern autorisiert und erfasst) und ob die Rechnung per E-Mail empfangen wurde.</li>
<li>Gehen Sie zur Postman und führen Sie die Anfrage Bereit für Abholung aus, wobei alle Produkte als mit <code>0 qty</code> <code>picked</code> festgelegt sind.</li>
</ol>
</td>
<td>
<ul>
<li>Aktualisierter Bestellverlauf: <code>We refunded $X offline</code></li>
<li>Der Bestellstatus ist <code>CLOSED</code>.
<li>Die Gutschrift wird erstellt. (Warten Sie, bis Cron funktioniert.)</li>
<li>E-Mail zur Rückerstattung erhalten: <code>$x amount was refunded</code></li>
<li>E-Mail zu Bestellabbruch gesendet.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Bereit zur Abholung - Teilabbruch</strong></br></br><strong>(Einige Produkte werden abgeholt, andere werden mit <code>0 qty</code> abgeholt)</strong>
</td>
<td>
<ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (sofern autorisiert und erfasst) und ob die Rechnung per E-Mail empfangen wurde.</li>
<li>Wechseln Sie zur Postman und führen Sie die Anfrage Bereit für Abholung aus, wobei ein Teil der Produkte mit einer Menge von 0 ausgewählt wurde und der Rest von ihnen ausgewählt wurde.</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> mit [!UICONTROL Ready for Pickup Items] und [!UICONTROL Canceled Items]. </li>
<li>Der Bestellstatus ist ABHOLBEREIT. </li>
<li>Auftragsverlauf aktualisiert: <code>We refunded $X offline.</code>
<li>Auftragsverlauf aktualisiert: <code>Order notified as partly canceled at: Date and hour</code>
<li>E-Mail zur Rückerstattung erhalten: <code>$x amount was refunded</code>
<li>Die Gutschrift wird erstellt. (Warten Sie, bis Cron funktioniert.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Bereit zur Abholung - Teilweise Stornierung</br></br>Einige Produkte werden ausgewählt, und einige werden mit <code>0 qty</code> ausgewählt)</strong>
</td>
<td><ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (sofern autorisiert und erfasst) und ob die Rechnung per E-Mail empfangen wurde.</li>
<li>Wechseln Sie zur Postman und führen Sie die Anfrage Bereit für Abholung aus, wobei ein Teil der Produkte mit einer Menge von 0 ausgewählt wurde und der Rest von ihnen ausgewählt wurde.</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> mit [!UICONTROL Ready for Pickup Items] und [!UICONTROL Canceled Items]. </li>
<li>Der Bestellstatus ist ABHOLBEREIT. </li>
<li>Auftragsverlauf aktualisiert: <code>We refunded $X offline.</code>
<li>Auftragsverlauf aktualisiert: <code>Order notified as partly canceled at: Date and hour</code>
<li>E-Mail zur Rückerstattung erhalten: <code>$x amount was refunded</code>
<li>Die Gutschrift wird erstellt. (Warten Sie, bis Cron funktioniert.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Dispensiert (während der Dispensierung) </br></br>Vollständiger Abbruch (alle Produkte werden als abgelehnt festgelegt)</strong>
</td>
<td>
<ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (sofern autorisiert und erfasst) und ob die Rechnung per E-Mail empfangen wurde.</li>
<li>Gehen Sie zur Postman und führen Sie die Anfrage Bereit für Abholung aus, wobei alle Produkte als ausgewählt festgelegt sind.</li>
<li>Öffnen Sie Ihr Postfach und suchen Sie die E-Mail Bereit für Abholung . Klicken Sie anschließend auf **[!UICONTROL Confirm Arrival]**.</li>
<li>Einchecken.</li>
<li>Wechseln Sie zu Postman und führen Sie die Dispensed-Anfrage aus, wobei alle Produkte als abgelehnt festgelegt sind.</li>
</ol>
<td><ul>
<li>Aktualisierter Bestellverlauf: <code>We refunded $X offline.</code></li>
<li>E-Mail zur Rückerstattung erhalten: <code>$x amount was refunded</code></li>
<li>Status auf <code>CLOSED</code> gesetzt.</li>
<li>Gutschrift erstellt. (Warten Sie, bis Cron funktioniert.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Dispensed (during dispens)</br></br>Partial Cancellation</br>(Some products are disppensed; some are Rejected.)</strong>
</td>
<td>
<ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (sofern autorisiert und erfasst) und ob die Rechnung per E-Mail empfangen wurde.</li>
<li>Gehen Sie zu Postman und führen Sie die Anfrage Bereit für Abholung aus, wobei alle Produkte als ausgewählt festgelegt sind.</li>
<li>Öffne deinen Briefkasten! Suchen Sie die E-Mail Bereit für Abholung und wählen Sie <code>Confirm Arrival</code> aus.</li>
<li>Einchecken.</li>
<li>Wechseln Sie zur Postman und führen Sie die Anfrage „Dispensed“ aus, wobei einige Produkte als „Dispensed“ und einige als „Rejected“ (Abgelehnt) festgelegt wurden</li>
</ol>
</td>
<td>
<li>Aktualisierter Bestellverlauf: <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>E-Mail zur Rückerstattung erhalten: <code>$x amount was refunded</code>
<li>Bestellstatus auf <code>Ready for pickup Dispensed</code> gesetzt
<li>Gutschrift erstellt. (Warten Sie, bis Cron funktioniert.)</li>
</td>
</tr>
<tr>
<td> <strong>Neue RMA nach Rückkehr (voll)</strong>
</td>
<td>
<ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Wenn die Option „Autorisieren und erfassen“ konfiguriert ist, überprüfen Sie, ob die Rechnung erstellt wurde und der Kunde die Rechnung per E-Mail erhalten hat.</li>
<li>Wählen Sie alle Produkte mit Postman aus.</li>
<li>Einchecken.</li>
<li>Geben Sie etwas aus.</li>
<li>Wechseln Sie zur Bestellung und wählen Sie<strong>[!UICONTROL Create returns]=
<li>Erstellen Sie die RMA.</li>
</ol>
</td>
<td>
<ul>
<li>Die RMA wurde erstellt und wird in der Bestellansicht unter der Registerkarte <strong>[!UICONTROL Returns]</b> angezeigt.</li>
<li>Kunde hat RMA-Bestätigungs-E-Mail erhalten.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Neue RMA nach Rückkehr — Teilweise</strong>
</td>
<td>
<ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (sofern autorisiert und erfasst) und ob die Rechnung per E-Mail empfangen wurde.</li>
<li>Wählen Sie alle Produkte mit Postman aus.</li>
<li>Einchecken.</li>
<li>Geben Sie etwas aus.</li>
<li>Wechseln Sie zur Bestellung und wählen Sie  <strong>[!UICONTROL Create returns]</strong></li>
<li>Erstellen Sie die RMA mit einem Teil der bestellten Produkte.</li>
</ol>
<td>
<ul>
<li>RMA erstellt und in der Bestellansicht unter der Registerkarte <strong>[!UICONTROL Returns]</strong> angezeigt.</li>
<li>Kunde hat die RMA-Bestätigungs-E-Mail erhalten.</li>
<li>Nach der Erstellung der RMA müssen Sie die RMA-Autorisierung einholen: Wechseln Sie vom Administrator zu <strong>[!UICONTROL Sales > Returns]</strong>. Wählen Sie die erstellte RMA aus und autorisieren Sie sie.</li>
<li>Überprüfen Sie, ob der Kunde die E-Mail zur Bestätigung der RMA-Autorisierung erhalten hat.</li>
<li>Prüfen Sie, ob die Rückerstattung zum Transaktions- und Bestellverlauf hinzugefügt wurde.</li>
</ul>
</td>
</tr>
</table>


### Fulfillment-App-Berechtigungen speichern

Dieser Abschnitt des Testplans behandelt die Kontoverwaltung für Benutzer der Store Fulfillment-App.

- Bestätigen Sie, dass sich ein Store Associate mit einem neuen, vom Adobe Commerce-Administrator erstellten Benutzerkonto authentifizieren kann.
- Bestätigen Sie, dass Aktualisierungen an vorhandenen Konten erfolgreich angewendet wurden.

**Funktionsbereich:** Adobe Commerce Admin</br>
**Rolle:** Admin, Store Associate</br>
**Testtyp:** positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td><strong>Benutzerkontenverwaltung - Konto erstellen</strong></br></br>
</td>
<td>
<ol>
<li><strong>Admin</strong> — Beim Adobe Commerce Admin anmelden</li>
<li>Gehen Sie zu <strong>[!UICONTROL System] &gt; Store Fulfillment App-Berechtigungen &gt; Alle Store Fulfillment App-Benutzer</strong></li>
<li><strong>Neuen Benutzer hinzufügen.</strong></li>
</ol>
<td>
<ul>
<li>Konto erfolgreich erstellt.</li>
<li>Ein neues Benutzerkonto wird im [!UICONTROL Store Fulfillment Users]-Dashboard angezeigt.</li>
<li><strong>Store Associate</strong> melden Sie sich mit einem neuen Benutzerkonto bei der Store Assist-App an.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Benutzerkontenverwaltung - Vorhandenes Benutzerkonto aktualisieren</strong>
</td>
<td>
<ol>
<li>Melden Sie sich beim Adobe Commerce Admin mit einem Administratorkonto an.</li>
<li>Gehen Sie zu <strong>[!UICONTROL System] &gt; Store Fulfillment App-Berechtigungen &gt; Alle Store Fulfillment App-Benutzer</strong>.</li>
<li>Öffnen Sie in der Liste Benutzerkonto ein vorhandenes aktives Benutzerkonto, indem Sie <strong>[!UICONTROL Edit]</strong> auswählen.
<li>Deaktivieren Sie das Konto, indem Sie <strong>[!UICONTROL Is Active]</strong> auf <strong>Nein</strong> ändern.</li>
</ol>
</td>
<td>
<ul>
<li>Im <strong>[!UICONTROL Store Fulfillment App Users]</strong>-Dashboard wurde der Status für das aktualisierte Konto in <strong>[!UICONTROL Inactive]</strong> geändert.</li>
<li>Store Associate kann sich nicht mit den inaktiven Kontoanmeldeinformationen bei der Store Assist-App anmelden.</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce-Produkttypen

Die Testszenarien für Adobe Commerce-Produkttypen überprüfen, ob Kunden die richtigen Produkt-, Lager- und Liefermethodeninformationen für verschiedene Produkttypen sehen:

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] in der Adobe Commerce-Storefront.

**Funktionsbereich:** Adobe Commerce Frontend</br>
**role:** Store Assist App User (Store Associate)</br>
**Testtyp:** positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Kommentare</th>
</tr>
<tr>
<td><strong>Konfigurierbare Produkte</strong>
</td>
<td>
<ul>
<li>Stellen Sie sicher, dass der Benutzer nur die konfigurierbaren Optionen sehen kann, welche Quelle aktiviert ist, das Lager zugewiesen ist und dass einige Artikel auf Lager sind - überprüfen Sie die untergeordneten Produkte.</li>
<li>Stellen Sie sicher, dass bei der Auswahl eines anderen Stores nicht verfügbare Optionen durchgestrichen angezeigt werden.</li>
<li>Vergewissern Sie sich, dass konfigurierbare Optionen deaktiviert werden, wenn der Benutzer einen anderen Store auswählt.</li>
<li>Vergewissern Sie sich, dass ein nicht vorrätiges Produkt angezeigt wird, wenn sich ein konfigurierbares Produkt bereits im Warenkorb befindet und Benutzende einen anderen Shop auswählen.</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>Gruppierte Produkte</strong>
</td>
<td>
<ul>
<li>Überprüfen Sie, ob die Versandmethoden und [!UICONTROL Add to cart] Schaltfläche für den Kunden deaktiviert sind, wenn alle untergeordneten Produkte
<code>qty</code> auf <code>0</code> gesetzt.</li>
<li>Überprüfen Sie, ob die Versandmethoden für den Kunden aktiviert sind, wenn für mindestens ein untergeordnetes Produkt Folgendes festgelegt <code>qty</code> <code>0.</code></li>
<li>Stellen Sie sicher, dass [!UICONTROL Store Pickup Delivery] Methode nur für Produkte sichtbar und aktiv ist, für die sie aktiviert [!UICONTROL Available for Store Pickup]. (Untergeordnetes Produkt prüfen.)</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>Virtuelle Produkte</strong>
</td>
<td>
Stellen Sie sicher, dass virtuelle Produkte nicht die [!UICONTROL In-store Pickup] Versandmethode bieten.
<td></td>
</td>
</tr>
<tr>
<td><strong>Bundle-Produkte</strong>
</td>
<td>
<ul>
<li>Vergewissern Sie sich, dass die Versandoption Store-Abholung für den Kunden nicht verfügbar ist, wenn mindestens ein untergeordnetes Produkt deaktiviert [!UICONTROL Available for Store Pickup].</li>
<li>Vergewissern Sie sich, dass dem Kunden die Option Heimversand nicht zur Verfügung steht, wenn mindestens ein untergeordnetes Produkt deaktiviert [!UICONTROL Available for Home Delivery].</li>
<li>Überprüfen Sie, ob mindestens eines der untergeordneten Produkte in einem Paket nicht vorrätig ist, denn das Paket (übergeordnetes Produkt) wird ebenfalls angezeigt
Wie [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## Eincheckerlebnis

In diesem Abschnitt des Testplans wird das Eincheckerlebnis für Abholaufträge im Geschäft für die folgenden Funktionen behandelt:

- Alternative Abholkontakte - Überprüfen Sie den Workflow zum Hinzufügen einer [!UICONTROL Alternate Pickup Contact] und zum Auswählen einer [!UICONTROL Preferred Contact] in Abholaufträgen.

- Eincheckformular - Überprüfen Sie den Workflow zum Senden einer Eincheckanfrage für Abholaufträge im Store.

**Funktionsbereiche:** Warenkorb-Checkout, Check-In-Formular für Abholaufträge im Geschäft</br>
**Rolle:**, Kunde, Store-Mitarbeiter</br>
**Testtyp:** positiv

### Ersatzabnehmerkontakt


**Funktionsbereich:** Warenkorb Checkout</br>
**Rolle:** Kunde</br>
**Testtyp:** positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td><strong>Wechselkontakt für Abholung</br>
Einchecken<strong>
</td>
<td>
Ein Kunde reicht eine Bestellung mit der Option „In-Store-Abholung“ ein.</td>
<td>Während des Checkout-Prozesses sieht der Kunde die [!UICONTROL Alternate Pickup Contact] der Option im Versandschritt.
</td>
</tr>
<tr>
<td><strong>Bevorzugter Kontakt für alternative Abholung, Einchecken</strong>
<td>
Ein Kunde reicht eine Bestellung mit der Option „In-Store-Abholung“ ein. Während des Checkouts fügt der Kunde eine [!UICONTROL Alternate Pickup Contact] hinzu.</td>
<td>Während des Checkout-Prozesses sieht der Kunde die [!UICONTROL Preferred Contact] Option im Versandschritt.</td>
</td>
</tr>
<tr>
<td><strong>Alternative Kontaktdaten für Abholung, Einchecken</strong>
</td>
<td>
Ein Kunde reicht eine Bestellung mit der Option „In-Store-Abholung“ ein. Während des Checkouts wählt der Kunde im Versandschritt [!UICONTROL Alternate Pickup Contact] aus.
</td>
<td>Der Kunde sieht Eingabeoptionen zum Eingeben von Kontaktdetails: [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone] und [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>Alternative Abholung, E-Mail einchecken</strong>
</td>
<td>Ein Kunde reicht eine Bestellung mit der Option „In-Store-Abholung“ ein. Während des Checkouts wählt der Kunde im Versandschritt [!UICONTROL Alternate Pickup Contact] aus, fügt die Kontaktdaten hinzu und reicht die Bestellung ein.</td>
<td>Sowohl der Kunde als auch der alternative Kontakt erhalten eine Check-In-E-Mail für die Bestellung.</td>
</tr>
<td><strong>Alternative Abholung, Bestelldetails</strong></td>
<td>Ein Kunde reicht eine Bestellung mit der Option „In-Store-Abholung“ ein. Während des Checkouts wählt der Kunde im Versandschritt [!UICONTROL Alternate Pickup Contact] aus, fügt die Kontaktdaten hinzu und reicht die Bestellung ein.</td>
<td>Der Administrator sieht die zusätzlichen Kontaktinformationen für die gespeicherte Bestellung.</td>
</tr>
<tr>
<td><strong>Alternative Abholkontakte, Ansicht „Zugeordnete Bestellung speichern“</strong>
</td>
<td>Ein Kunde reicht eine Bestellung mit der Option „In-Store-Abholung“ ein. Während des Checkouts wählt der Kunde im Versandschritt [!UICONTROL Alternate Pickup Contact] aus, fügt die Kontaktdaten hinzu und reicht die Bestellung ein.</td>
<td>Der Store Associate kann die zusätzlichen Kontaktinformationen zur Bestellung in FAAs/CHAs einsehen.</td>
</td>
</tr>
</tbody>
</table>

### Eincheckformular


**Funktionsbereich:** Formular</br>
**Rolle:** Kunde</br>
**Testtyp:** positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td><strong>Aktion einchecken - Anfrage senden</strong>
</td>
<td>Auf dem Check-in-Formular füllt ein Kunde alle erforderlichen Felder aus und sendet die Anfrage.</td>
<td>Der Kunde erhält eine Erfolgsantwort.</td>
</tr>
<tr>
<td><strong>Aktion einchecken - Anfragedetails anzeigen</strong></td>
<td>Ein Kunde sendet erfolgreich eine Anfrage zum Einchecken.</td>
<td>Der Bestellstatus wird im FAS-System aktualisiert, und der Store Associate kann die Details der Eincheckanfrage in den FAS sehen.
</td>
</tr>
<tr>
<td><strong>Aktion einchecken - Anfrage nur einmal senden</strong></td>
<td>Nach dem Einreichen einer Check-in-Anfrage für eine Bestellung wählt ein Kunde den Link zum Einchecken ein zweites Mal aus.</td>
<td>Im Eincheckformular sieht der Kunde keine Option zum Bearbeiten oder erneuten Senden des Formulars.</td>
</tr>
<tr>
<td><strong>Einchecken in Aktion - Ankunft bestätigen</strong></td>
<td>Eine Abholbestellung im Laden wird in den FAA als abholbereit markiert. Der Kunde erhält eine E-Mail zur Abholbereitschaft und wählt [!UICONTROL Confirm Arrival] aus.</td>
<td>Der Kunde sieht das Eincheckformular für die Bestellung.</td>
</tr>
</tbody>
</table>

## Store-Assist-App

In diesem Abschnitt des Testplans werden Szenarien für das Testen von Auftrags-, Auswahl- und Übergabe-Workflows in der Store Assist-App behandelt.

**Funktionsbereich:** Store Assist App</br>
**Rolle:** Store Associate</br>
**Testtyp:** positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td>
<strong>Einzel-Kommissionierung - Happy Path, Curbside Pickup</strong></td>
<td>Wählen Sie Artikel mit einer oder mehreren Mengen. Keine Nullpunkte und Bordsteinabnahme (mit Staging).
</td>
<td>
</td>
</tr>
<tr>
<td><strong>Kommissionierung mit mehreren Bestellungen - Happy Path, Curbside Pickup</strong></td>
<td>Einzel- und Mehrmengen-Artikel. Keine Nullpunkte und Bordsteinabnahme (mit Staging)</td>
<td></td>
</tr>
<tr>
<td><strong>Einzelne Kommissionierung - Happy Path-Abholung im Geschäft</strong></td>
<td>Einzel- und Mehrmengen-Artikel. Keine Nullsummen, und Abholung im Geschäft (mit Staging)</td>
<td>
</td>
</tr>
<tr>
<td><strong>Kommissionierung mit mehreren Bestellungen - Happy Path, Abholung im Geschäft</strong></td>
<td>Wählen Sie Artikel mit einer oder mehreren Mengen. Keine Nullpunkte und Bordsteinabnahme (mit Staging).</td>
<td></td>
</tr>
<tr>
<td><strong>Einzelne Kommissionierung - kein glücklicher Weg, Abholung im Geschäft</strong></td>
<td>Einzel- und Mehrmengen-Artikel mit Teil- und Nilpick- und Ladenaufnahme (mit Staging)</td>
</td>
<td></td>
</tr>
<td><strong>Kommissionierung mit mehreren Bestellungen - keine glückliche Pfadauswahl am Bordrand</strong></td>
<td>Einzel- und Mehrmengen-Artikel mit Teil- und Nilpick- und Ladenaufnahme (mit Staging)</td>
<td></td>
</tr>
<td><strong>Einzelne Kommissionierung - kein glücklicher Weg, Randabholung</strong></td>
<td>Einzel- und Mehrmengenartikel mit Teil- und Nilpick und Bordsteinabnahme (mit Staging)</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>Bestellung aufgegeben - vor Kommissionierung storniert</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Bestellung aufgegeben - vor Übergabe storniert</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Bestellung aufgegeben - Suche im Bestellmodul</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Bestellung aufgegeben - Suche und manuelles Einchecken für Übergabe</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Bestellung aufgegeben - alle Artikel, die nicht ausgewählt oder nicht verfügbar sind und von der Auswahl markiert wurden</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Bestellung mit Paketartikeln aufgegeben - Kommissionierung und Übergabe</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Bestellung aufgegeben - Übergabe mit Ablehnung</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Bestellung aufgegeben - Übergabe mit Ablehnung aller Artikel</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## Bereitstellen

Nachdem Sie sich vergewissert haben, dass die Lösung gemäß Ihren Spezifikationen konfiguriert und getestet wurde, können Sie sie vom Staging bis zur Produktion bereitstellen.

Bereitstellung und Tests hängen von Ihrer Infrastruktur und Ihren Möglichkeiten ab.

>[!TIP]
>
>Bereitstellungsrichtlinien, Checklisten und Best Practices für Adobe Commerce bei Cloud-Infrastrukturprojekten finden Sie unter [Bereitstellen Ihres Stores](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) in der Adobe Commerce Developer-Dokumentation.
