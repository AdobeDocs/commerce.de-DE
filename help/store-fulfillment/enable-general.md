---
title: Allgemeine Konfiguration
description: Konfigurieren Sie allgemeine Einstellungen, um  [!DNL Store Fulfillment]  für Ihren Store zu aktivieren. Konfigurieren Sie globale Erweiterungseinstellungen, Systemeinstellungen für Protokollierung, Datensynchronisierung und Sicherheit. Bereitstellen von Schlüsseldaten für die Integration zwischen Adobe Commerce und Store Fulfillment-Services.
role: Admin
level: Intermediate
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '2405'
ht-degree: 0%

---

# Store-Service- und Verkaufskonfiguration

Aktivieren Sie [!DNL Store Fulfillment] Erweiterung über den [!DNL Commerce] Admin, indem Sie die Erweiterungseinstellungen, die Sicherheitseinstellungen für Benutzende der Store Assist-App und die Optionen für die Versandmethode konfigurieren.

>[!IMPORTANT]
>
>Die Konfiguration des Store Fulfillment-Services wird erst angewendet, nachdem Sie Ihre Adobe Commerce-Instanz mit der [!DNL Store Fulfillment] App verbunden haben. Siehe [Connect Store-Erfüllung](connect-set-up-service.md).

## Store Fulfillment-Diensteinstellungen verwalten

Einstellungen für Store-Fulfillment-Services über das Menü [!DNL Commerce Admin Store Configuration] verwalten.

- Aktivieren Sie die Erweiterung, konfigurieren Sie globale Einstellungen und geben Sie Sicherheitsoptionen für Benutzerverbindungen und Konten der Store Assist-App an, indem Sie **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]** auswählen.

  ![Konfiguration der Admin Store-Services für Store-Erfüllung](assets/store-services-admin-sf-config.png)

- Konfigurieren Sie die Versandmethoden, indem Sie **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]** auswählen.

  ![Admin Store-Verkaufskonfiguration für Store-Erfüllung](assets/store-sales-admin-sf-deliver-config.png)

## Grundlegende Einstellungen

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>Der Preis, den Sie dem Kunden für die Abholung im Geschäft in Rechnung stellen. Die Standardeinstellung ist null.</td>
<td>Website</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>Der Radius in Kilometern, der verwendet werden soll, wenn ein Käufer an der Storefront-Kasse nach einem Abholort sucht. Die Suchergebnisse geben nur Stores zurück, die sich innerhalb des angegebenen Suchradius befinden.</td>
<td>Website</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>Nachricht, die angezeigt wird, wenn ein Kunde die Abholung im Geschäft für einen Artikel auswählt, der nicht für die Abholung im Geschäft verfügbar ist. Sie können den Standardtext bei Bedarf anpassen.
</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>Die [!UICONTROL Search Radius] wird nur verwendet, wenn Sie den [Store-Speicherort und die Zuordnungseinrichtung](store-location-map-provider-setup.md) für Adobe Commerce konfiguriert haben.

## Store-Fulfillment-Lösung aktivieren

Aktivieren Sie die [!DNL Store Fulfillment] Lösung, um die Funktionen „In-Store“ und „Am Bordrand“-Pick-up zum Einkaufen und Checkout in Ihrer Adobe Commerce-Storefront hinzuzufügen.

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>Aktivieren oder Deaktivieren der Lösung. Wenn diese Option aktiviert ist, konfigurieren und verwenden Sie die Store-Fulfillment-Funktionen und stellen Sie die Verbindung zwischen Ihrem Adobe Commerce-Store und [!DNL Store Fulfillment]-Services her. Wenn diese Option deaktiviert ist, sind alle Store Fulfillment-Funktionen deaktiviert und es findet keine Kommunikation zwischen Adobe Commerce und Store Fulfillment-Services statt. Bestellinformationen können nicht verarbeitet oder empfangen werden.</td>
<td>Website</td>
<td>Ja</td>
</tr>
</tbody>
</table>

## Kontoanmeldeinformationen hinzufügen

<table>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>Wählen Sie entweder <i>[!UICONTROL Sandbox]</i> oder <i>[!UICONTROL Production]</i><br></br>Durch Auswahl von [!UICONTROL Sandbox] wird die Kommunikation mit Fulfillment-Services in einer Testumgebung ermöglicht.<br></br>Die Auswahl von [!UICONTROL Production] ermöglicht die Kommunikation mit Fulfillment-Services in einer Live-Umgebung.<br></br>Sie erhalten für jede Umgebung einen Satz von Anmeldeinformationen und können beide Sätze in derselben Installation verwalten. <br></br>Speichern Sie die Anmeldeinformationen, bevor Sie die Verbindung validieren.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>Die URL zum Walmart Store Fulfillment-API-Endpunkt. Der Wert muss die vollständig qualifizierte URL sein, die während des Onboarding-Prozesses angegeben wird. Store-Fulfillment-Kunden erhalten sowohl eine Sandbox- als auch eine Produktions-URL. Stellen Sie beim Hinzufügen der Werte sicher, dass Sie die vollständige URL kopieren und einfügen, einschließlich des Schrägstrichs "/".</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>Die URL zum Endpunkt für die Walmart Store-Fulfillment-Authentifizierung. Der Wert muss die vollständig qualifizierte URL sein, die während des Onboarding-Prozesses angegeben wird. Sie erhalten sowohl eine Sandbox als auch eine Produktions-URL. Stellen Sie beim Hinzufügen der Werte sicher, dass Sie die vollständige URL kopieren und einfügen, einschließlich des Schrägstrichs "/".</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Ihre eindeutige Händler-ID (Mandanten-ID), die während des Onboarding-Prozesses angegeben wurde. Diese ID wird verwendet, um Bestellungen weiterzuleiten und sicherzustellen, dass sie von Ihren Händlern empfangen werden.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>Die eindeutige Integrations-ID, die während des Onboarding-Prozesses bereitgestellt wird. Diese ID wird verwendet, um die gesamte Kommunikation zwischen Adobe Commerce und Store Fulfillment-Services zu authentifizieren</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>Der eindeutige Integrationsschlüssel, der während des Onboarding-Prozesses bereitgestellt wird. Dieser Schlüssel wird verwendet, um die gesamte Kommunikation zwischen Adobe Commerce und dem Store Fulfillment-Service zu authentifizieren.</td>
<td>Global</td>
<td>Ja</td>
</tr>
</table>

Nachdem Sie die [!UICONTROL Account Credentials] konfiguriert haben, wählen Sie <strong>[!UICONTROL Validate Credentials]</strong> aus, um zu überprüfen und zum ersten Mal eine Verbindung zum Store Fulfillment-Service herzustellen.

## Konfigurieren der Protokollierung

Protokolle für Store-Fulfillment-Services sind im `var/log/walmart-bopis.log` der Protokolldatei verfügbar.

Bitten Sie den Systemadministrator, Ihre Umgebungen so zu konfigurieren, dass die Ausnahmebehandlung zugelassen wird, damit API-bezogene Ausnahmen über die Firewall oder den Cache erfasst werden können.

Da die Anwendungsprotokolldatei schnell wachsen kann, aktivieren Sie die Protokollierung für die Anwendung nur für kurze Zeit bei Bedarf, z. B. bei der Fehlerbehebung bei Problemen mit der Speichererfüllung für eine [!DNL Commerce]. Diese Konfiguration verhindert durch große Protokolldateien verursachte Antwortzeitprobleme in Produktionsumgebungen.

>[!TIP]
>
>Bitten Sie bei lokalen Adobe Commerce-Installationen Ihren Systemadministrator, eine Protokollrotation für die `var/log/walmart-bopis.log` einzurichten, um die Größe zu minimieren. Informationen zu lokalen Adobe Commerce-Installationen finden Sie [Protokollrotation](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) im _Adobe Commerce-Installationshandbuch_. Informationen zu Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>Der Debug-Modus wird verwendet, um die protokollierte Aktivität innerhalb der Integration zu erhöhen. Wenn diese Option deaktiviert ist, werden keine Debuginformationen protokolliert. Wenn diese Option aktiviert ist, werden alle Debugging<br></br>Informationen protokolliert. Alle protokollierten Daten finden Sie in der Datei: <pre>var/log/walmart-bopis.log</pre>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

## Auftragssynchronisierung verwalten

Konfigurieren Sie die Einstellungen, um die Fehlerbehandlung für die Auftragssynchronisierung, Katalogattribute für die Barcode-Überprüfung während der Kommissionierung zu verwalten, und konfigurieren Sie Auftrags-Batch-Größen für die Warteschlange für die Store-Erfüllung.

Details zu Vorgängen der Auftragssynchronisierung werden im Dashboard „Warteschlangenverwaltung für die Store-Erfüllung“ im Admin-Bereich (
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>).

### Verwaltung von Synchronisierungsfehlern

<table>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>Gibt die Wiederholungsversuche für einen Datensatz-Synchronisierungsvorgang an, nachdem ein kritischer Fehler aufgetreten ist.<br></br>Kritische Fehler treten immer dann auf, wenn die Integration keine positive Antwort vom Fulfillment-Service erhält. Diese Probleme treten auf, wenn der Service ausgefallen ist oder ein Fehler in den gesendeten Bestelldaten auftritt.<br></br>Wenn der Schwellenwert für weitere Zustellversuche erreicht ist, bleibt das Element in einer Warteschlange, wird aber nicht erneut verarbeitet. Zeigen Sie alle Elemente mit Fehlern aus der <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> im Admin-Bereich an. Wenden Sie sich an Ihren Account Manager, um Probleme zu beheben, die durchgängig fehlschlagen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>Aktivieren Sie Fehlerbenachrichtigungen, um eine E-Mail zu erhalten, wenn die [!UICONTROL Retry Critical Error Threshold] für eine Bestellung erreicht wird. Die Benachrichtigung enthält alle verfügbaren Details zum Fehler.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>Eine kommagetrennte Liste der Empfänger-E-Mail-Adressen für Fehlerbenachrichtigungen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>Gibt die E-Mail-Vorlage an, die verwendet wird, um Empfänger über Fehler bei der Auftragssynchronisierung zu informieren. Eine Standardvorlage wird bereitgestellt. Es unterstützt keine Anpassung.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</table>

### Synchronisierung der Reihenfolge

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>Das Katalogattribut, das den scannbaren Code für die entsprechenden Elemente an Ihren Händlerstandorten speichert.<br></br>Wenn Sie nur einen Händler-Standort haben, verwenden Sie wahrscheinlich UPC-Codes, während Ihr E-Commerce-Kanal Produkte nach SKU identifiziert. Wählen Sie in diesem Szenario das Katalogattribut aus, das den UPC-Code enthält.<br></br>Diese Einstellung stellt sicher, dass Bestellungen, die an Ihre Storelistenelemente gesendet werden, die richtige Kennung aufweisen, damit Storeassoziierte während des Kommissioniervorgangs Elemente genau scannen können.<br></br>Wenn Sie sich nicht sicher sind, fragen Sie bei Ihren Erfüllungsbeauftragten in der Versand- und Kommissionierabteilung nach, welches Attribut gesendet werden soll. Wenn das Attribut derzeit nicht in der Datenbank enthalten ist, können Sie das Attribut zum Adobe Commerce-Produktattributsatz hinzufügen.</td>
<td>Website</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>Das Katalogattribut, das die Barcodequelle für entsprechende Elemente an Ihren Händlerstandorten speichert.<br></br>Diese Einstellung stellt sicher, dass Bestellungen, die an Ihre Storelistenelemente mit der richtigen Kennung gesendet werden, damit Storeassoziierte während des Kommissioniervorgangs Elemente genau scannen können. Die Optionen umfassen - SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Preis Embedded UPC.<br></br>Wenn Sie sich nicht sicher sind, wählen Sie die Option aus, die den in Ihrem [!UICONTROL Barcode Source] enthaltenen Werten am ähnlichsten ist. Store-Associates können Elemente weiterhin manuell aus ihrer Auswahlliste abgleichen.</td>
<td>Website</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>Die maximale Anzahl von Elementen, die gleichzeitig aus der Store-Erfüllungswarteschlange gesendet werden können.<br></br>BOPIS-Bestellungen werden in regelmäßigen Abständen stapelweise an den Fulfillment-Service gesendet. Mit dieser Einstellung können Sie die Größe des Stapels steuern.<br></br>Der Standardwert ist 100 Elemente. Je nach Auftragsvolumen und Kapazität können Sie den Maximalwert nach oben oder unten anpassen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

## Versandoptionen für Store Fulfillment aktivieren

Konfigurieren Sie die Versandoptionen für die Store-Erfüllung, die die Verfügbarkeit von Abholungs- und Zustelloptionen im Geschäft für Ihre Adobe Commerce-Stores bestimmen.

### In Lager versenden

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>Die Einstellung von Schiff zu Lager basiert auf Ihren vorhandenen Ship-to-Store-Funktionen. Wenn Sie Inventory management verwenden oder wenn Sie Bestellungen an Händlerstandorten ohne Lager über „Store-to-Store“-Bestandsübertragungen annehmen und ausführen können, setzen Sie diese Option auf „Ja“.<br></br>Wenn Sie die Ship-to-Store-Option nicht unterstützen können oder nicht anbieten möchten, setzen Sie auf „Nein“. Wenn diese Option deaktiviert ist, werden Artikel in Ihrem Katalog, die über keinen Bestand für ein Händlergeschäft verfügen, oder Artikel, die unter dem [!DNL Out of Stock Threshold] für diesen Speicherort liegen, nicht mit Abholoptionen im Geschäft angeboten.<br></br>Sie können den Wert dieser Einstellung für jeden Händler-Standort anpassen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

### Versand aus Lager

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>Aktiviert oder deaktiviert die Option „Hauslieferung“ in Ihren Händlern. Wenn diese Option aktiviert ist, werden die Standorte Ihrer Händlergeschäfte zusammen mit anderen zugewiesenen Quellen im Lager berücksichtigt, das mit Ihrer Website verbunden ist.<br></br>In standardmäßigen Inventory management-Services ist die Option [!DNL Ship from Store] inhärent und kann nicht deaktiviert werden. Mit der Store Fulfillment-Lösung können Sie sie aktivieren oder deaktivieren.<br></br>Sie können diese Einstellung je nach Standort und Produkt des Händlers anpassen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>


## Benutzerkonten und Berechtigungen für Store Fulfillment-App verwalten

Konfigurieren Sie die Einstellungen für das Benutzerkonto und die Kennwortsicherheit für die Store Fulfillment App sowie die Zwei-Faktor-Authentifizierung.

### App-Sicherheit

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>Der Zeitraum in Sekunden, in dem eine Store Associate-Benutzersitzung vor dem automatischen Abmelden aktiv bleibt. Gültige Werte liegen zwischen 60 und 31536000.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>Gibt die Anzahl fehlgeschlagener Anmeldeversuche an, die zulässig sind, bevor ein Store-Associate aus seinem Konto gesperrt wird.<br></br>Um die Kontosperrung zu deaktivieren, setzen Sie den Wert auf 0.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>Anzahl der Minuten, die ein Konto nach einem Anmeldefehler gesperrt werden soll.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>: Benutzer auffordern, ihr Kennwort nach der Kontoeinrichtung zu ändern.<br></br><em>[!UICONTROL No]</em>: empfiehlt, dass Benutzende das Kennwort nach der Kontoeinrichtung ändern.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>Die Anzahl der Tage, die ein Kennwort gültig bleibt, bevor eine erforderliche Kennwortänderung vorgenommen wird. Lassen Sie das Feld leer, um diese Option zu deaktivieren.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

## Versandmethoden

Store Fulfillment erweitert die nativen Adobe Commerce [!DNL In-Store Delivery]-Funktionen. Nach der Installation der Erweiterung können Sie Versandmethoden im Geschäft mithilfe der folgenden erweiterten Einstellungen konfigurieren, die dem Administrator hinzugefügt werden.

- **Abholung im Geschäft** - Angebotsoptionen für den Versand im Geschäft während des Checkout-Prozesses
Mit diesen Einstellungen werden die häufigsten Versandszenarien für BOPIS-Bestellungen konfiguriert.

- **[!UICONTROL Curbside pick up]**-Offer-Optionen für Kunden, um an einem Store-Standort zu parken und ihre Bestellung von einem Store-Mitarbeiter liefern zu lassen.

Konfigurieren Sie diese Einstellungen über den Administrator, indem Sie <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong> auswählen.

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von Bereitstellungsoptionen im Geschäft finden Sie unter [In-Store](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery) im _Adobe Commerce-Benutzerhandbuch_.


### Konfiguration der Versandmethoden

Mit der Versandmethode im Geschäft kann der Kunde eine Quelle auswählen, die während des Checkouts als Abholort verwendet werden soll.

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Umfang</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>Aktivieren oder deaktivieren Sie die Option Abholung im Geschäft, die während des Checkouts für Kunden verfügbar ist, die die Abholung im Geschäft wählen. Wenn die Abholung im Geschäft deaktiviert ist, wird die Option nicht angezeigt.<br></br>Diese globale Einstellung gilt für alle Filialen im Einzelhandel. Wenn diese Option aktiviert ist, können Sie sie selektiv im Einzelhandelsgeschäft deaktivieren.</td>
<td>Website</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>Aktivieren oder deaktivieren Sie die Option „Randabholung“ während des Checkout-Prozesses für Kunden, die sich für eine Shop-Abholung entscheiden.<br></br>Diese globale Einstellung gilt für alle Filialen im Einzelhandel. Wenn diese Option aktiviert ist, können Sie sie selektiv im Einzelhandelsgeschäft deaktivieren.</td>
<td>Website</td>
<td>Nein</td>
</tr>
</tbody>
</table>

### Titelkonfiguration der Versandmethode

<table>
<thead>
<tr>
<th><strong>Feld</strong></th>
<th><strong>Beschreibung</strong></th>
<th><strong>Umfang</strong></th>
<th><strong>Erforderlich</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Titel des Heimversands</strong></td>
<td>Gibt den Titel an, der für die Option Heimversand im Bereich Produkt, Warenkorb und Checkout angezeigt werden soll. Der Versand nach Hause bezieht sich auf die standardmäßigen Versandfunktionen von Adobe Commerce - von einem Lager, durch einen Spediteur oder direkt an die vom Kunden bereitgestellte Versandadresse. </br></br>Diese Kennzeichnung hat keinen Einfluss auf die Beschriftungen der Versandmethode für den ausgewählten Versanddienstleister.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Versandbeschreibung - Startseite</strong></td>
<td>Eine optionale Beschreibung, die angezeigt wird, wenn Kunden der Titel des Heimversands angezeigt wird. Meistens ist die Beschreibung eine statische Nachricht, um die Versandversprechen mitzuteilen. Einige Beispiele:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Abholtitel speichern</strong></td>
<td>Wenn einem Kunden Lieferoptionen präsentiert werden und eine Abholung im Geschäft verfügbar ist, wird dieser Titel angezeigt. </br></br>Sie können diese Beschriftung anpassen, die in den Bereichen Produkt, Warenkorb und Checkout angezeigt wird.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Beschreibung der Store-Abholung</strong></td>
<td>Wo auch immer der Titel der Store-Abholung angezeigt wird, können Sie optional eine Beschreibung einfügen. Diese statische Nachricht hilft, die Kundenkommunikation in Bezug auf die Store-Abholung zu verbessern. Einige Beispiele:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>In-Store-Abholtitel</strong></td>
<td>Wenn die Abholung im Geschäft aktiviert ist, wird dieser Titel den Kunden als Versandoption „Abholung im Geschäft“ angezeigt. Sie können die Beschriftung anpassen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<tr>
<td><strong>Curbside Pickup Title</strong></td>
<td>Wenn die Option „Randabholung“ aktiviert ist, wird sie den Kunden als Versandart „Store-Abholung“ angezeigt. Sie können die Beschriftung hier anpassen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Anweisungen zur Abholung im Geschäft</strong></td>
<td>Wenn eine Bestellung in Ihren Einzelhandelsgeschäften zur Abholung bereit ist, wird der Kunde per E-Mail benachrichtigt. Wenn der Kunde während des Checkouts [!DNL In-Store Pickup] ausgewählt hat, können Sie hier die Abholanweisungen anpassen. </br></br>Diese Anweisungen sind global festgelegt und gelten für alle Einzelhandelsgeschäfte. Sie können die Anweisungen auch auf der Ebene des Einzelhandelsgeschäfts anpassen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Anleitung für die Bordabholung</strong></td>
<td>Gibt benutzerdefinierte Anweisungen zur Auftragsabholung an, die in Kunden-E-Mail-Benachrichtigungen für Abholaufträge am Bordstein enthalten sein sollen. </br></br>Diese Anweisungen sind global festgelegt und gelten für alle Einzelhandelsgeschäfte. Sie können die Anweisungen auch auf der Ebene des Einzelhandelsgeschäfts anpassen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Geschätzte Abholzeit</strong></td>
<td>Die Anzahl der Minuten, die erforderlich sind, bevor eine Bestellung empfangen, erfüllt und abholbereit ist. Diese Informationen werden dem Kunden angezeigt, wenn er einen Einzelhandelsspeicherort für die Versandoption „Store-Abholung“ auswählt. Diese Einstellung gilt für alle Filialen im Einzelhandel. Sie können die Vorlaufzeit auch auf der Ebene des Einzelhandelsgeschäfts anpassen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Titel der geschätzten Abholzeit</strong></td>
<td>Zeigt die geschätzte Zeit an, bis eine Bestellung für die Kundenabholung verfügbar ist. Diese Informationen werden Kundinnen und Kunden angezeigt, wenn sie einen Einzelhandelsspeicherort für die Versandoption "[!DNL In-Store Pickup]" auswählen. </br></br>Wenn Sie diese Beschriftung anpassen, können Sie den Code-<code>%1</code> verwenden, um Ihre <strong>Geschätzte Abholzeit“ </strong>. Beispiel: </br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Diese Einstellung gilt für alle Filialen im Einzelhandel. Sie können die Vorlaufzeit auch auf der Ebene des Einzelhandelsgeschäfts anpassen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
<tr>
<td><strong>Haftungsausschluss für Abholzeit</strong></td>
<td>Der Inhalt, der auf der Produktseite in der QuickInfo angezeigt wird und Speicherstunden, Feiertage, unerwartete Schließungen usw. auflistet</td>
<td>Shop-Ansicht
</td>
<td>Nein
</td>
</tr>
</tbody></table>

### Konfiguration der Stock-Verfügbarkeitstitel

<table>
<thead>
<tr>
<th><strong>Feld</strong></th>
<th><strong>Beschreibung</strong></th>
<th><strong>Umfang</strong></th>
<th><strong>Erforderlich</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>vorrätig</strong></td>
<td>Wenn ein Kunde den Einzelhandelslagerplatz verwendet, wird für jeden Lagerplatz die Lagerverfügbarkeit für die aktuellen Artikel angezeigt. </br></br>Sie können die <em>[!UICONTROL in-stock]</em> hier anpassen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>nicht vorrätig</strong></td>
<td>Wenn ein Kunde den Einzelhandelslagerplatz verwendet, wird für jeden Lagerplatz die Lagerverfügbarkeit für alle aktuellen Artikel angezeigt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>teilweise vorrätig</strong></td>
<td>Wenn ein Kunde den Einzelhandelslagerplatz verwendet, wird für jeden Lagerplatz die Lagerverfügbarkeit für alle aktuellen Artikel angezeigt. </br></br>Sie können die <em>[!UICONTROL partially in-stock]</em> hier anpassen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

