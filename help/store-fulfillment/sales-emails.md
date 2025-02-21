---
title: Verkaufs-E-Mail-Vorlagen
description: Konfigurieren Sie die Transaktions-E-Mail-Vorlagen für die Kommunikation mit Kunden und Store-Administratoren während des Erfüllungsprozesses für Store-Abholaufträge.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Communications, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 1%

---


# Verkaufs-E-Mail-Vorlagen

Store Fulfillment bietet einen erweiterten Satz von Transaktions-E-Mail-Vorlagen zur Unterstützung von Auftrags- und Erfüllungs-Workflows. Sie bieten konsistente, automatisierte Kommunikation und Messaging über verschiedene Kanäle hinweg. So werden Kunden- und Store-Administratoren über Änderungen des Bestellstatus, Anweisungen für Abholaufträge in Geschäften und mehr informiert.

E-Mail-Vorlagen für die Store-Erfüllung sind mit standardmäßigen Messaging- und Einstellungen konfiguriert. Händler-Administratoren in Adobe Commerce können Konfigurationen verwalten und ändern sowie E-Mail-Vorlagen auswählen, um mit Kunden in verschiedenen Szenarien zu kommunizieren. Admins können auch Vorlagen konfigurieren und anpassen.

Konfigurieren Sie die E-Mail-Vorlagen für den Verkauf über den Administrator: **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## E-Mails - Allgemeine Einstellungen

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
<td><strong>asynchrones Senden</strong></td>
<td>Bestimmt, ob Verkaufs-E-Mails asynchron gesendet werden. Optionen: <br/>**`Disable`** - (Standard) Verkaufs-E-Mails werden gesendet, wenn sie durch ein Ereignis ausgelöst werden. Verwenden Sie die Standardeinstellung, um die schnellste Kommunikation und Antwortzeit für die Store-Abholung zu erzielen. <br/>**`Enable`** - Durch Aktivierung dieser Option werden Prozesse, die E-Mail-Benachrichtigungen zur Checkout- und Bestellverarbeitung verarbeiten, in den Hintergrund verschoben, damit sie in vorgegebenen, regelmäßigen Abständen gesendet werden.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

## Bestellung bereit für Abholung im Geschäft

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, wenn der Verkaufsassistenten die Auswahl seiner Bestellung abgeschlossen hat. Auf „Nein“ setzen, um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert sie nicht, dass eine Bestellung vom Store-Associate ausgewählt wird.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung bereit für Abholung E-Mail Absender</strong></td>
<td>Die Absenderidentität, die beim Senden der E-Mail-Benachrichtigung verwendet wurde.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Abholbereite E-Mail-Vorlage</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um registrierte Kunden zu benachrichtigen. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>E-Mail-Vorlage „Bestellung bereit für Abholung“ für Gast</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>E-Mail-Vorlage „Bestellung bereit für Abholung“ für alternativen Abholkontakt</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um zusätzliche Kontakte zu benachrichtigen, die in der Bestellung genannt werden. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung bereit für Abholung per E-Mail senden an</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung bereit für Abholung per E-Mail senden</strong></td>
<td>Die zu verwendende E-Mail-Kopiermethode (Carbon Copy).</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>


## Bestellung wurde im Shop entgegengenommen

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, wenn er bestätigen muss, dass er seine Bestellung im Geschäft abgeholt hat. Auf „Nein“ setzen, um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert sie nicht, dass eine Bestellung vom Kunden abgeholt wird.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung wurde vom E-Mail-Absender entgegengenommen</strong></td>
<td>Die Absenderidentität, die beim Senden der E-Mail-Benachrichtigung verwendet wurde.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung wurde in E-Mail-Vorlage aufgenommen</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um registrierte Kunden zu benachrichtigen. Für die Integration wird eine Standardvorlage bereitgestellt</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Bestellung wurde für Gast per E-Mail-Vorlage abgeholt</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Senden wurde per E-Mail aufgenommen an Kopie</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Der Versand wurde per E-Mail durchgeführt</strong></td>
<td>Die zu verwendende E-Mail-Kopiermethode (Carbon Copy).</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

## Bestellung verzögert

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, um ihn über eine Verzögerung bei der Bearbeitung oder Auswahl seiner Bestellung im Merchant Store zu informieren. Auf „Nein“ setzen, um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert die Funktion nicht, dass eine Bestellung verzögert wird.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>E-Mail-Absender mit verzögerter Bestellung
</strong></td>
<td>Die Absenderidentität, die beim Senden der E-Mail-Benachrichtigung verwendet wurde.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Vorlage für verzögerte E-Mail-Bestellung</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um registrierte Kunden zu benachrichtigen. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>E-Mail-Vorlage für verzögerte Bestellung für Gast</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Auftrag mit verzögerter E-Mail-Kopie senden an</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Methode für verzögerte Kopie des Versandauftrags</strong></td>
<td>Die zu verwendende E-Mail-Kopiermethode (Carbon Copy).</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>



## Bestellung storniert

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, um ihn darüber zu informieren, dass seine Bestellung im Merchant Store storniert wurde. Auf <code>No</code> setzen, um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert ihre Funktion nicht, dass eine Bestellung storniert wird.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>E-Mail-Absender storniert bestellen
</strong></td>
<td>Die Absenderidentität, die beim Senden der E-Mail-Benachrichtigung verwendet wurde.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Vorlage für stornierte E-Mails bestellen</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um registrierte Kunden zu benachrichtigen. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Bestellung für Gast storniert</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Abgebrochene E-Mail zum Bestellversand an</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Kopiermethode für abgebrochenen Versand</strong></td>
<td>Die zu verwendende E-Mail-Kopiermethode (Carbon Copy).</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>


## Bestellung teilweise storniert

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, um ihn darüber zu informieren, dass ein Teil seiner Bestellung im Merchant Store storniert wurde. Auf <code>No</code> setzen, um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert sie nicht, dass eine Bestellung teilweise storniert wird.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>E-Mail-Absender teilweise storniert bestellen
</strong></td>
<td>Die Absenderidentität, die beim Senden der E-Mail-Benachrichtigung verwendet wurde.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>E-Mail-Vorlage für teilweise stornierte Bestellungen</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um registrierte Kunden zu benachrichtigen. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Teilweise stornierte E-Mail-Vorlage für alternativen Abholkontakt bestellen</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um zusätzliche Kontakte zu benachrichtigen, die in der Bestellung genannt werden. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung für Gast teilweise storniert</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung teilweise storniert per E-Mail an kopieren</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Teilweise abgebrochene Kopiermethode des Versandauftrags</strong></td>
<td>Die zu verwendende E-Mail-Kopiermethode (Carbon Copy).</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

## An Lager versenden

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
<td><strong>Bestellung hat Versand an Produkt-E-Mail-Absender</strong></td>
<td>E-Mail, die als aggregierter Bericht zu allen offenen Bestellungen, die erst in einem Händlergeschäft aufgenommen werden können, wenn das Inventar verfügbar ist, an bestimmte Händlermitarbeiter gesendet wird. </br></br> Händler können diese Auswertung verwenden, um Lagerübertragungen oder -auffüllungen von einem Lager zum anderen zu initiieren und zu verwalten. </br></br>Diese Benachrichtigung gilt nur, wenn die [!DNL Ship-to-Store] Funktionen aktiviert sind.
</br></br>Diese Kennzeichnung hat keine Auswirkungen auf den ausgewählten Versanddienstleister oder dessen verfügbare Versandmethodenkennzeichnungen.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Versand an Store-E-Mail-Empfänger</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>E-Mail-Vorlage</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, mit der Empfänger benachrichtigt werden. Für die Integration wird eine Standardvorlage bereitgestellt.</td>
<td>Shop-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

>[!NOTE]
>
>Wenn Sie Nachbestellungen zulassen, müssen Sie eine Administrator-E-Mail-Adresse angeben, um Benachrichtigungen über diese Bestellungen zu erhalten. Fügen Sie die Adresse den folgenden Konfigurationseinstellungen hinzu: **[!UICONTROL Send Order Delayed Email Copy To]** in der Vorlage [Auftragsverzögerung](#order-delayed) und [!UICONTROL Ship To Store Email Recipients] in der Vorlage [Ship to Store](#ship-to-store).



