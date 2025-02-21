---
title: App-Setup
description: Richten Sie die  [!DNL Store Assist] -App ein, um End-to-End-Workflows für die Store-Erfüllung und Prozesse für Online-Käufe zu verwalten, die in Store-Bestellungen erfasst werden.
level: Intermediate
role: Admin
feature: Shipping/Delivery, Configuration, Tools and External Services
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---

# App-Setup

Store Assist ist eine Fulfillment-as-a-Service (FaaS)-Plattform-App, die von Walmart Commerce Technologies unterstützt wird. Die App bietet Funktionen zur Erfüllung von In-Store-Aufträgen zur Verarbeitung von [!DNL buy online, pick up in store] (BOPIS)-Aufträgen. Mit Store Assist können Filialmitarbeiter sehen, welche Artikel von Kunden bestellt wurden, die richtigen Artikel schneller auswählen und erfüllte Aufträge für die In-Store- oder Cortside-Abholung an Kunden einrichten.

Die Store Assist-App erhält alle Bestell- und Kundeninformationen - von den Bestelldetails bis zu den Abholzeiten - und stellt die Daten über Mobilgeräte online für Store-Mitarbeiter zur Verfügung. Die App enthält [!UICONTROL Pick]-, [!UICONTROL Stage]-, [!UICONTROL Handoff]- und [!UICONTROL Orders]-Module, die Store-Mitarbeiter bei Erfüllungsaktivitäten unterstützen, z. B.:

- Liefertermine und -zeiten der Bestellungen zuweisen.
- Erhalten Sie Benachrichtigungen von Kunden, wenn sie zur Bestellabholung eintreffen.
- Staging-Aufträge für Übergabe an Kunden.
- Verfolgen Sie den Bestellstatus für alle Bestellungen in den ihnen zugewiesenen Filialen.

>[!NOTE]
>
>Weitere Informationen zur Store-Assist-App finden Sie im Thema [Store-Assist-Workflows](store-assist-modules.md) .

## Konfigurieren der Store Assist-App

Für die Store Assist-App sind zwei Konfigurationstypen erforderlich:

- Adobe Commerce Admin-Systemeinstellungen zum [Verwalten von Benutzerkonten, Benutzerrollen, ](user-setup.md) und [die Auto- und Modellauswahl für Kunden während des Eincheckvorgangs verfügbar machen](check-in-experience-setup.md).

- Frontend-Konfigurationseinstellungen zum Anpassen der Benutzeroberfläche der Store-Assist-App und anderer Einstellungen, einschließlich:

   - **Brand the Store Assist app** - Passen Sie die Benutzeroberfläche der App mit Ihrem Firmenlogo und Ihren Farben an.

   - **Standardanweisungen aktualisieren** - Passen Sie die Anweisungen in den Modulen „Store Assist Pick“, „Staging“, „Handoff“ und „Order“ an, um Store Associates durch jeden Schritt des Erfüllungs-Workflows für Ihr Unternehmen zu führen.

   - **Lokalisierung** - Wählen Sie die für die App verfügbare Sprache aus. Wählen Sie Ihr Datums- und Uhrzeitformat sowie Ihre standardmäßigen Maßeinheiten und Standardwährung aus.

   - **Inaktivitätsdauer** - Geben Sie an, wie lange die Mobile App inaktiv sein muss, bevor sie sich abmeldet.

   - **Stornierung aus dem Store** - Geben Sie an, ob Bestellungen aus dem Store storniert werden können und welche Rollen über Stornierungsberechtigungen verfügen

   - **Auftragsbereinigungsfenster** - Geben Sie an, wie lange nach der [Geschätzten Abholungslaufzeit](enable-general.md#delivery-method-title-configuration) eine abgerufene Bestellung noch im Staging verbleibt, bevor sie wieder aufgefüllt wird, z. B. drei Tage. Der Standardwert ist sieben Tage. Wenn diese Konfiguration aktiviert ist, wird die Bestellung bei Ablauf dieser Zeit automatisch storniert. Die Artikel werden wieder vorrätig gehalten, und der Händler erhält eine Absage-E-Mail.

   - Anpassen aller In-App-Anweisungen (Kommissionieren, Staging, Übergabe).

   - **Entnahmebenachrichtigungen** - Geben Sie an, ob eine Push-Benachrichtigung gesendet werden soll, um den Entnahmeprozess zu starten, nachdem ein Kunde eine Bestellung aufgegeben hat.

   - **Eincheckbenachrichtigungen** - Geben Sie an, ob eine Push-Benachrichtigung während des Eincheckvorgangs für die Bestellabholung gesendet werden soll, nachdem der Eincheckvorgang einen bestimmten Zeitraum überschritten hat. Oder deaktivieren Sie die Benachrichtigung.

   - **Übergabeverfahren** - Aktivieren Sie optionale Prozesse, wenn Store Associate dem Kunden eine Bestellung zustellt. Sie benötigen beispielsweise eine Kundenunterschrift oder fordern den Associate auf, die Kunden-ID zu überprüfen.

   - **Artikelablehnung bei Übergabe aktivieren** - Ermöglicht es Kunden, Bestellartikel während der Übergabe der Bestellung zurückzugeben oder zu stornieren.

  Arbeiten Sie mit dem Client Services-Team von Walmart Commerce Technologies zusammen, um die Frontend-Konfiguration für die Store Assist-App abzuschließen.

## App-Download und -Installation

Nachdem die Store Assist-App eingerichtet und konfiguriert wurde, können Store Associates die Store Assist-App von ihren Mobilgeräten herunterladen, installieren und sich dort anmelden.

- Stellen Sie sicher, dass das Mobilgerät die [Hardware- und Softwareanforderungen](solution-requirements.md#store-assist-app-requirements) für die Store Fulfillment-Lösung erfüllt.

- Laden Sie die Store Assist-App vom [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} oder vom [Google Play Store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"} herunter.

- Store Associates benötigen für die Anmeldung die folgenden Informationen:

   - **[!UICONTROL Company name]**, die mit dem Store Assist-Konto verknüpft sind

   - **Anmeldedaten für Assist-Konto speichern** - Benutzername und Kennwort für das Konto.

  Ein Adobe Commerce-Administrator kann [!DNL Store Assist app] Benutzerkonten für alle Filialstandorte erstellen und verwalten, für die [In-Store](merchant-store-configuration.md#pickup-location-configuration)Abholung aktiviert in den Einstellungen für Admin Stores sind.
