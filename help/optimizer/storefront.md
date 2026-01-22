---
title: Einrichten der Storefront
description: Erfahren Sie, wie Sie Ihre Storefront  [!DNL Adobe Commerce Optimizer] .
role: Developer
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 2b4c9e98-a30c-4a33-b356-556de5bd721a
source-git-commit: 0cd9749574460374a8fe875f1eff54f2a4a8d614
workflow-type: tm+mt
source-wordcount: '1397'
ht-degree: 0%

---

# Einrichten der Storefront

Dieses Handbuch führt Sie durch die Einrichtung einer Storefront für Ihre [!DNL Adobe Commerce Optimizer] mithilfe von Adobe Edge Delivery Services. Ihre Storefront umfasst Textbaustein-Code, Beispielinhalte und Unterstützung für Produktdetailseiten und die Produkterkennung (Suche und Filterung).

**Geschätzte Dauer:** 30-45 Minuten

## Voraussetzungen

* **GitHub-Konto** das Repositorys erstellen kann und für die lokale Entwicklung konfiguriert ist (github.com)
* **[!DNL Adobe Commerce Optimizer]-Instanz** mit Beispieldaten und konfigurierten Katalogansichten und Richtlinien
   * Siehe [Hinzufügen von Beispieldaten](get-started.md#add-sample-data) für Einrichtungsanweisungen.

### Erforderliche Instanzdaten

Bevor Sie beginnen, erfassen Sie die folgenden Informationen aus Ihrer [!DNL Adobe Commerce Optimizer]:

* **Mandanten-ID** (auch als Instanz-ID bezeichnet)
   * Verfügbar auf der [Detailseite der Instanz](get-started.md#manage-instances)
* **GraphQL-Endpunkt** für Ihre Instanz
   * Verfügbar auf der [Detailseite der Instanz](get-started.md#manage-instances)
* **Katalogansicht-ID** für die globale Katalogansicht
   * Auf der Seite [Katalogdetails“ ](./setup/catalog-view.md#manage-catalog-view)
* **Source-Gebietsschema** für Ihre Katalogansicht
   * Die Standardeinstellung für Beispieldaten ist `en-US`

>[!NOTE]
>
>Kunden mit Testzugriff können den GraphQL-Endpunkt in der Begrüßungs-E-Mail finden, die bei der Erstellung Ihrer Instanz empfangen wurde. Testinstanzen enthalten vorkonfigurierte Beispieldaten, Katalogansichten und Richtlinien.

## Schritte einrichten

1. **[Storefront-Projekt erstellen](#create-your-storefront-project)**-Verwenden Sie das [Site Creator-Tool](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator), um ein neues Storefront-Projekt mit Textbaustein-Code, Beispielinhalten und einer Konfigurationsdatei zu erstellen.

1. **[Konfiguration der Storefront anpassen](#customize-the-storefront-configuration)**-Aktualisieren Sie die `config.json`-Datei in Ihrem Repository, um eine Verbindung zu Ihrer [!DNL Adobe Commerce Optimizer]-Instanz herzustellen.

1. **[Setup überprüfen](#verify-your-setup)** (10 Min.)
   * Vorschau der Storefront-Site
   * Testen von Produktdetailseiten und Suchfunktionen

## Erstellen Ihres Storefront-Projekts

Das Tool Site Creator erstellt ein vollständiges Storefront-Projekt mit den folgenden Komponenten:

* **Site**: Landingpage für Storefront mit Textbausteininhalten
* **Code**: Repository mit Textbaustein-Quelldateien
* **Inhalt**: Dokumentautorenumgebung mit Site-Inhaltsdateien
* **Commerce Config**: `config.json` Datei für die instanzspezifische Konfiguration

### Schritt 1: Generieren des Projekts

1. Öffnen Sie das Tool [Site Creator](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator)

   ![[!DNL Site Creator tool]](./assets/storefront-setup-site-creator.png){width="700" zoomable="yes"}

1. Wählen **Neue Site erstellen (Code und Inhalt)** aus.

1. Abschließen der Site-Konfiguration:

   * **GitHub-Organisation/**: Geben Sie Ihren GitHub-Benutzernamen oder -Organisationsnamen ein
   * **Site-**: Wählen Sie einen beschreibenden Namen für Ihre Storefront
   * **Commerce GraphQL-Endpunkt (optional)**: Geben Sie den GraphQL-Endpunkt für Ihre [!DNL Adobe Commerce Optimizer] ein

1. Klicken Sie **Site erstellen**, um das GitHub-Repository mit dem Textbausteincode für die Storefront zu erstellen.

   Wenn das Repository erstellt wird, werden Sie vom Site Creator aktualisiert und aufgefordert, die Code Sync -App zu installieren.

### Schritt 2: Installieren der Code Sync App

1. Klicken Sie auf **[!UICONTROL Install AEM Code Sync App]** , um das Installationsprogramm für die Code-Synchronisierung in einer neuen Registerkarte zu öffnen.

1. Konfigurieren Sie die Code-Synchronisierungs-App:
   * Wählen Sie Ihre GitHub-Organisation aus und klicken Sie dann auf **[!UICONTROL Configure]**.
   * Klicken Sie in der Code-Synchronisierungsschnittstelle auf **[!UICONTROL Only select repositories]**.
   * Klicken Sie auf das Menü **[!UICONTROL Select repositories]** und wählen Sie dann das von Ihnen erstellte Code-Repository für die Storefront aus.
   * Klicken Sie auf **[!UICONTROL Save]** , um Ihr Repository zu registrieren.

1. Kehren Sie zum Browser-Fenster zurück, in dem der Site-Ersteller geöffnet ist, und klicken Sie auf **Site erstellen**.

   Der Site Creator kopiert den Textbausteininhalt der Storefront in die Dokumentautorenumgebung. Dieser Vorgang dauert 1-2 Minuten.

### Schritt 3: Speichern Sie Ihre Projekt-Links

1. Überprüfen Sie im Abschnitt Site-Details die Links für Ihr Storefront-Projekt:

   ![[!DNL Storefront setup complete]](./assets/storefront-setup-complete.png){width="700" zoomable="yes"}

   Verwenden Sie diese Links, um Code, Inhalt und Konfiguration Ihrer Storefront zu verwalten.

1. Kopieren Sie diese Links und speichern Sie sie dann zur späteren Verwendung: Klicken Sie auf **[!UICONTROL Copy].

## Konfigurieren der Storefront

Aktualisieren Sie Ihre Storefront-Konfiguration, um eine Verbindung zu Ihrer [!DNL Adobe Commerce Optimizer]-Instanz herzustellen.

1. Öffnen Sie die `config.json`-Datei in Ihrem Textbaustein-Code-Repository.

   `https://github.com/<username or org>/<repo name>/config.json`

1. Suchen Sie den Abschnitt `cs` (Catalog Service) in der -Konfiguration.

1. Ersetzen Sie die Platzhalterwerte durch die Werte für Ihre Instanz. Siehe [Voraussetzungen](#prerequisites).

   ```json
   "cs": {
      "AC-View-ID": "{catalogViewId}",
      "AC-Source-Locale": "en-US",
      "AC-Price-Book-ID": "{priceBookId}"
   }
   ```

   >[!NOTE]
   >
   >Um die Preisbuch-ID zu finden, überprüfen Sie die [Konfigurationsdetails der Katalogansicht](./setup/catalog-view.md) in Adobe Commerce Optimizer, um die zugewiesenen Preisbücher anzuzeigen. Wenn keine Preisverzeichnisse zugewiesen sind, können Sie diese Kopfzeile aus der Konfigurationsdatei entfernen. Fügen Sie sie wieder hinzu, wenn der Katalogansicht ein Preisbuch zugewiesen wurde.

1. Speichern Sie die Konfigurationsdatei.

   Es kann einige Minuten dauern, bis die Konfigurationsänderungen übernommen werden. Wenn die Daten nicht sofort angezeigt werden, warten Sie 2-3 Minuten, bevor Sie die Fehlerbehebung vornehmen.

## Überprüfen des Setups

Testen Sie Ihre Storefront, um sicherzustellen, dass sie ordnungsgemäß mit Ihrer [!DNL Adobe Commerce Optimizer]-Instanz verbunden ist.

### Schritt 1: Startseite der Storefront anzeigen

1. Navigieren Sie zu Ihrer Live-Vorschau-URL:

   `https://main--{SITE}--{ORG}.aem.live`

   Ersetzen Sie `{ORG}` und `{SITE}` durch Ihre GitHub-Organisation und Ihren Site-Namen.

1. **Erfolgskriterien**: Sie sollten die Startseite der Storefront mit Textbausteininhalten sehen.

   ![[!DNL ACO storefront site with boilerplate]](./assets/aco-storefront-site-boilerplate.png){width="700" zoomable="yes"}

### Schritt 2: Produktdetailseiten testen

Sehen Sie sich die Standardproduktdetailseite an, um zu überprüfen, ob die Produktdaten korrekt geladen werden.

1. Navigieren Sie zu einer Beispielproduktseite:
   `https://main--{SITE}--{ORG}.aem.live/products/placeholder/{sku}`

   Verwenden Sie eine beliebige SKU aus Ihren Beispieldaten, z. B.:
   `https://main--{SITE}--{ORG}.aem.live/products/placeholder/aur-flu-tir-std-2017`

   Für die Standard-Storefront können Sie den `placeholder` in der Route verwenden, um das Produkt anzuzeigen. Wenn Sie mit der Anpassung Ihrer Storefront beginnen, können Sie den Code der Storefront anpassen, um den Pfad zur Produktdetailseite basierend auf den in Ihrem Katalog definierten Produktrouten festzulegen.

   >[!TIP]
   >
   >Zeigen Sie verfügbare SKUs auf der Seite [Datensynchronisierung](./setup/data-sync.md) in Ihrer [!DNL Adobe Commerce Optimizer] an.

1. **Erfolgskriterien**: Die Seite sollte Folgendes anzeigen:
   * Produktname, Beschreibung und Preise
   * Produktbilder
   * Funktion zum Hinzufügen zum Warenkorb
   * Aus der [!DNL Adobe Commerce Optimizer] abgerufene Daten

   ![[!DNL Default product detail page showing a product from the sample data]](./assets/storefront-boilerplate-product-page.png){width="700" zoomable="yes"}

### Schritt 3: Testen der Standardsuchfunktion

Testen Sie die standardmäßigen Produktfunktionen, einschließlich Suche und Filterung.

1. Klicken Sie auf der Startseite der Storefront auf das Lupensymbol in der Kopfzeile.

1. Geben Sie die `tires` Suchzeichenfolge ein und drücken Sie **Eingabetaste**.

1. **Erfolgskriterien**: Sie sollten Folgendes sehen:
   * Suchergebnisseite mit Reifenprodukten
   * Filteroptionen in der Seitenleiste
   * Produktlisten mit Bildern und Preisen

   ![[!DNL View search results page]](./assets/storefront-with-aco-search-results-page.png){width="675" zoomable="yes"}

1. Klicken Sie auf ein Reifenprodukt, um dessen Detailseite anzuzeigen.

   ![[!DNL View product details page]](./assets/storefront-with-aco-pdp-page.png){width="675" zoomable="yes"}

## Fehlerbehebung

Wenn während des Setups Probleme auftreten, verwenden Sie die Web-Seiten-Inspektor-Konsole, um nach Fehlern zu suchen. Löschen Sie außerdem Ihren Browser-Cache oder verwenden Sie einen anderen Browser.

Verwenden Sie die folgende Anleitung, um häufige Probleme zu überprüfen:

### Häufige Probleme

| Problem | Symptome | Lösung |
|-------|----------|----------|
| **Die Installation der Codesynchronisierung schlägt fehl** | Einrichtung der Codesynchronisierung kann nicht abgeschlossen werden | <ul><li>Stellen Sie sicher, dass Sie Administratorzugriff auf Ihre GitHub-Organisation haben.</li><li>Versuchen Sie, ein persönliches Repository anstelle einer Organisation zu verwenden.</li><li>Überprüfen Sie die GitHub-Berechtigungen und versuchen Sie es erneut.</li></ul> |
| **Site wird nicht geladen** | 404- oder Verbindungsfehler | <ul><li>URL-Format der Site überprüfen: `https://main--{SITE}--{ORG}.aem.live`</li><li>Überprüfen Sie, ob die Code Sync App ordnungsgemäß installiert ist.</li><li>Stellen Sie sicher, dass das Repository öffentlich ist oder ordnungsgemäß konfiguriert ist.</li></ul> |
| **Keine Produktdaten angezeigt** | Produktseiten enthalten Platzhalter oder Fehler | <ul><li>Überprüfen Sie Ihre Konfigurationswerte in `config.json`</li><li>Überprüfen Sie in der [!DNL Adobe Commerce Optimizer]-Instanz die Seite Datensynchronisierung , um sicherzustellen, dass Beispielprodukte geladen werden. Wenn keine Produkte verfügbar sind, laden Sie die Beispieldaten neu oder fügen Sie ein Produkt mithilfe der [Datenaufnahme-API“ ](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/using-the-api/#make-your-first-request). Warten Sie einige Minuten, bis die Konfigurationsänderungen weitergegeben werden.</li><li>Versuchen Sie, die Produktdetails mithilfe der Merchandising-Service-[Produktabfrage](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/use-cases/#return-product-details) abzurufen, indem Sie dieselben Kopfzeilen verwenden, die in der `config.json`-Datei konfiguriert sind. Wenn Sie die Daten abrufen können, ist dies wahrscheinlich ein Problem mit der Konfiguration der Katalogansicht oder ein Indexfehler.</li></ul> |
| **Suche gibt keine Ergebnisse zurück** | Leere Suchergebnisseite | <ul><li>Stellen Sie sicher, dass Sie die Produktsuchergebnisse mithilfe der Merchandising-Services [productSearch-Abfrage](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/use-cases/#product-search) mit denselben Kopfzeilen abrufen können, die in der `config.json`-Datei konfiguriert sind. Wenn Sie die Daten abrufen können, ist dies wahrscheinlich ein Problem mit der Konfiguration der Katalogansicht oder ein Indexfehler.</li><li>Vergewissern Sie sich, dass die Katalogansichts-ID in der `config.json` mit der Katalogansichts-ID in [!DNL Adobe Commerce Optimizer] übereinstimmt.</li><li>Überprüfen Sie in Adobe Commerce Optimizer die Konfiguration der Richtlinien, des Gebietsschemas und der Preisverzeichnisse, die Sie in der Konfiguration der Storefront-Kopfzeilen verwendet haben.</li><li>Stellen Sie sicher[ dass für die Suche die ](https://developer.adobe.com/commerce/services/reference/rest/#operation/createProductMetadata)Attribut-Metadateneinstellungen) korrekt eingestellt sind.</li></ul> |

### Validierungs-Checkliste

Bevor Sie mit den nächsten Schritten fortfahren, stellen Sie sicher, dass Ihre Storefront ordnungsgemäß funktioniert, indem Sie Folgendes überprüfen:

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) Konfigurationswerte stimmen mit Ihren Instanzeinstellungen überein<br>
![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) Die Startseite der Storefront wird fehlerfrei geladen<br>
![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) Auf mindestens einer Produktdetailseite werden vollständige Informationen angezeigt<br>
![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) Die Suchfunktion gibt relevante Ergebnisse zurück<br>
![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) Produktbilder werden korrekt geladen<br>
![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) Konfigurationswerte stimmen mit Ihren Instanzeinstellungen überein<br>

### Hilfe erhalten

Wenn die Probleme bestehen bleiben:

* Lesen Sie die Dokumentation zur [Adobe Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/)
* Lesen Sie das [Adobe Commerce Optimizer-Entwicklerhandbuch](https://developer.adobe.com/commerce/services/optimizer/)
* Besuchen Sie die [Adobe Commerce Support-Ressourcen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview)

## Nächste Schritte

Nachdem Sie Ihre Storefront eingerichtet und überprüft haben, können Sie:

1. **[Installieren Sie die ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/#install-and-configure-sidekick)** Sidekick-Browser, um Inhalte direkt auf Ihrer Website zu bearbeiten, in der Vorschau anzuzeigen und zu veröffentlichen.

2. **[Einrichten einer lokalen Entwicklungsumgebung](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/#set-up-local-environment)** - Erstellen einer lokalen Umgebung zum Anpassen des Codes und Inhalts Ihrer Storefront.

### Erfahren und erkunden

* **[Abschließen des End-to-End-Anwendungsfalls](./use-case/admin-use-case.md)** Erfahren Sie mehr über die Einrichtung von Storefronts und die Katalogverwaltung mithilfe von [!DNL Adobe Commerce Optimizer].

* **[Anpassung der Storefront erkunden](https://experienceleague.adobe.com/developer/commerce/storefront/setup/)**—Erfahren Sie mehr über erweiterte Setup- und Konfigurationsoptionen.

* **[Verwenden Sie Commerce-Dropdown-Menüs, um das Storefront-Erlebnis anzupassen](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/)**-Fügen Sie vorgefertigte Komponenten hinzu, um das Storefront-Erlebnis zu verbessern.

* **Migrieren zum Storefront-Konfigurations-**: Nachdem Sie Ihre erste Storefront erstellt haben, können Sie die Konfiguration so migrieren, dass der Konfigurations-Service verwendet wird, der erweiterte Anwendungsfälle wie die Konfiguration „Repoless“ und Überlagerungen unterstützt. Weitere Informationen finden Sie in der [Konfigurationsdienst](https://www.aem.live/docs/config-service-setup) Dokumentation in der Adobe Experience Manager.

>[!MORELIKETHIS]
>
> Weitere Informationen zum Aktualisieren von Website-Inhalten und [ Integration mit Commerce-Frontend-Komponenten und Backend-Daten finden Sie in der Dokumentation zur ](https://experienceleague.adobe.com/developer/commerce/storefront/)Adobe Commerce Storefront .
