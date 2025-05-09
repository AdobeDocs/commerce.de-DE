---
title: Einrichten der Storefront
description: Erfahren Sie, wie Sie Ihre Storefront  [!DNL Adobe Commerce Optimizer] .
role: Developer
exl-id: 2b4c9e98-a30c-4a33-b356-556de5bd721a
source-git-commit: f1aa8439d6322e5278ab787f5cd096e16b7813a2
workflow-type: tm+mt
source-wordcount: '2150'
ht-degree: 0%

---

# Einrichten der Storefront

>[!NOTE]
>
>In dieser Dokumentation wird ein Produkt beschrieben, das sich in der Entwicklung für den frühzeitigen Zugriff befindet und nicht alle für die allgemeine Verfügbarkeit vorgesehenen Funktionen enthält.

In diesem Tutorial erfahren Sie, wie Sie eine [Adobe Commerce-Storefront mit Edge Delivery Services](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de) einrichten und verwenden, um eine leistungsstarke, skalierbare und sichere Commerce-Storefront auf der Grundlage von Daten aus Ihrer [!DNL Adobe Commerce Optimizer]-Instanz zu erstellen.


## Voraussetzungen

* Stellen Sie sicher, dass Sie über ein GitHub-Konto (github.com) verfügen, das Repositorys erstellen kann und für die lokale Entwicklung konfiguriert ist.

* Erfahren Sie mehr über die Konzepte und den Workflow zur Entwicklung von Commerce-Storefronts mit Adobe Edge Delivery Services [ Sie in der Dokumentation ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started?lang=de) Adobe Commerce-Storefront .
* Einrichten der Entwicklungsumgebung


### Einrichten der Entwicklungsumgebung

Installieren Sie Node.js und die Sidekick-Browser-Erweiterung, die zum Entwickeln und Testen Ihrer [!DNL Adobe Commerce Optimizer]-Storefront auf Edge Delivery Services erforderlich sind.

#### Installieren von Node.js

Installieren Sie Node Version Manager (NVM) und die erforderliche Node.js-Version (22.13.1 LTS).

1. Installieren Sie Node Version Manager (NVM).

   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
   ```

1. Installieren Sie Node.js und NPM. Weitere Informationen finden Sie unter [Node.js](https://nodejs.org/en/).

   ```bash
   nvm install 22
   ```

   ```bash
   npm install -g npm
   ```

1. Überprüfen Sie die Installation.

   ```bash
   npm -v
   ```

>[!TIP]
>
>Dieser Einrichtungsprozess der Storefront dient zur Verwendung von [!DNL Adobe Commerce Optimizer] mit der Storefront des Adobe Commerce Edge Delivery-Services. Zusätzliche Ressourcen zum Erweitern und Anpassen Ihrer [!DNL Adobe Commerce Optimizer]-Lösung sind über [App Builder für Adobe Commerce](https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) und [API Mesh für Adobe Developer App Builder](https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/adobe-developer-app-builder/api-mesh/getting-started-api-mesh) verfügbar. Wenden Sie sich für Informationen zu Zugriff und Nutzung an Ihren Adobe-Kundenbetreuer.

#### Installieren von Sidekick

Installieren Sie die Sidekick-Browser-Erweiterung, um Inhalte zu bearbeiten, in der Vorschau anzuzeigen und in der Storefront zu veröffentlichen. Siehe [Sidekick-Installationsanweisungen](https://www.aem.live/docs/sidekick#installation).


## Erstellen einer Storefront

Die Storefront, die Sie für Ihr [!DNL Adobe Commerce Optimizer]-Projekt erstellen, verwendet eine angepasste Version des Textbausteins Adobe Commerce on Edge Delivery Services Storefront . Das Textbaustein ist ein Satz von Dateien und Ordnern, die einen Ausgangspunkt für die Entwicklung von Storefronts bieten. Dieser Einrichtungsprozess unterscheidet sich vom standardmäßigen Einrichtungsprozess für eine [Adobe Commerce in der Edge Delivery Services-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de).

>[!NOTE]
>
>In diesem Tutorial werden macOS, Chrome und Visual Studio Code als Entwicklungsumgebung verwendet. Der Bildschirm erfasst und Anweisungen spiegeln diese Einrichtung wider. Sie können ein anderes Betriebssystem, einen anderen Browser und einen anderen Code-Editor verwenden, aber die angezeigte Benutzeroberfläche und die von Ihnen durchgeführten Schritte variieren entsprechend.

### Workflow-Übersicht

Führen Sie diese Schritte aus, um eine Storefront zur Verwendung mit [!DNL Adobe Commerce Optimizer] einzurichten.

1. **[Erstellen eines Inhaltsordners](#step-1-create-a-content-folder)** Erstellen eines freigegebenen Inhaltsordners in Google Drive oder SharePoint. Dieser Ordner enthält Beispielinhalte und Assets für Ihre Storefront.

1. **[Erstellen eines Code-Repositorys](#step-2-create-a-code-repository)**-Erstellen Sie ein GitHub-Repository aus der Textvorlage Adobe Commerce + Edge Delivery Services . Schließen Sie alle Verzweigungen aus dem Quell-Repository ein.
1. **[Storefront-Textbaustein aktualisieren](#step-3-update-the-storefront-boilerplate)**-Aktualisieren Sie die benutzerdefinierte Textbausteinvorlage auf der `aco` Verzweigung, um Ihren Inhaltsordner mit der Storefront zu verbinden.
1. **[Laden Sie den aktualisierten Textbausteincode der Storefront hoch](#step-4-upload-the-updated-boilerplate-code)**-Überschreiben Sie den Code auf der `main` Verzweigung mit dem aktualisierten Code aus der `aco` Verzweigung.
1. **[Fügen Sie die CodeSync-App hinzu](#step-5-add-the-aem-code-sync-app)**-Verbinden Sie Ihr Repository mit dem Edge Delivery-Service. Verbinden Sie die Code-Synchronisierungs-App erst, wenn Sie die Anpassung des Quell-Codes abgeschlossen haben und bereit sind, den Code in die `main` zu übertragen.
1. **[Vorschau und Veröffentlichung Ihres Inhalts](#step-6-preview-and-publish-your-content)** - Verwenden Sie die Sidekick-Erweiterung, um eine Vorschau anzuzeigen und den Site-Inhalt aus dem Inhaltsordner in der Storefront zu veröffentlichen.
1. **[Vorschau Ihrer Site und Anzeigen von Beispieldaten](#step-7-preview-your-site)**-Stellen Sie eine Verbindung zu Ihrer Storefront-Site her, um den Beispielinhalt und die Daten aus der [!DNL Adobe Commerce Optimizer]-Demoinstanz anzuzeigen.
1. **[Entwickeln Sie die Storefront in Ihrer lokalen Umgebung](#step-8-develop-the-storefront-in-your-local-environment)**-Installieren Sie die erforderlichen Abhängigkeiten. Starten Sie den lokalen Entwicklungs-Server und aktualisieren Sie die Storefront-Konfiguration, um eine Verbindung zur [!DNL Adobe Commerce Optimizer]-Instanz herzustellen, die Adobe für Sie bereitgestellt hat.
1. **[Nächste Schritte](#next-steps)**-Erfahren Sie mehr über die Verwaltung und Anzeige von Inhalten und Daten in der Storefront.

### Schritt 1: Erstellen eines Inhaltsordners

Befolgen Sie die Anweisungen in der Dokumentation zur Adobe Commerce-Storefront, um einen freigegebenen Inhaltsordner in Google Drive oder SharePoint hinzuzufügen und den Beispielinhalt hinzuzufügen. Der Beispielinhalt umfasst Bilder, Text und andere Assets, aus denen Ihre Site besteht.

* [Erstellen und Freigeben eines Google-Laufwerks oder SharePoint-Ordners](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de#create-and-share-folder)
* [Laden Sie den Beispielinhalt](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de#add-sample-content) in Ihren Ordner.

### Schritt 2: Code-Repository erstellen

Erstellen Sie in GitHub mithilfe der Textbausteinvorlage Edge Delivery Services + Adobe Commerce ein Textbaustein-Repository für die Storefront.

1. Melden Sie sich bei Ihrem GitHub-Konto an.

1. Navigieren Sie zum [aem-boilerplate-commerce](https://github.com/hlxsites/aem-boilerplate-commerce) GitHub-Repository.

1. Wählen **Diese Vorlage verwenden** und wählen Sie dann **Neues Repository erstellen** aus dem Dropdown-Menü aus.

   ![[!DNL Create github repo from storefront boilerplate template]](./assets/storefront-create-github-repo.png){width="700" zoomable="yes"}

   Die Seite mit der Repository-Konfiguration wird angezeigt.

   ![[!DNL Configure github repo to pull all branches from boilerplate repo]](./assets/storefront-configure-github-repo.png){width="700" zoomable="yes"}

1. Füllen Sie das Konfigurationsformular mit den folgenden Details aus:

   * **Repository-Vorlage** - `hlxsites/aem-boilerplate-commerce` (Standard).
   * **Alle Verzweigungen einbeziehen** - Wählen Sie diese Option, um alle Verzweigungen einzubeziehen.
   * **Inhaber** - Ihr Unternehmen oder Konto (erforderlich).
   * **Repository-**: Ein eindeutiger Name für Ihr neues Repository (erforderlich).
   * **Beschreibung** - Eine kurze Beschreibung Ihres Repositorys (optional).
   * **Öffentlich oder Privat** - Adobe empfiehlt Öffentlich (Standard).

1. Wählen Sie **Repository erstellen** aus.

   Nach einigen Minuten wird Ihr neues Repository geöffnet.

   Ignorieren Sie alle Pull-Anforderungsbenachrichtigungen, die in der GitHub-Benutzeroberfläche angezeigt werden.

### Schritt 3: Schaufenster aktualisieren

Sie benötigen die folgenden Informationen, um den Textbausteincode der Storefront zu aktualisieren:

* **GitHub-Repository-URL aus Schritt 2**— `github.com/{ORG}/{SITE}`

   * `{ORG}` ist der Organisationsname oder Benutzername für das Repository.

   * `{SITE}` ist Ihr Repository-Name

* **Inhaltsordner-URL aus Schritt 1**— `https://drive.google.com/drive/folders/{YOUR_FOLDER_ID}`

  `{YOUR_FOLDER_ID}` ist die ID des Ordners, den Sie mit den Beispielinhaltsdaten erstellt haben.

#### Aktualisieren Sie den Textbausteincode, um eine Verbindung zu Ihrem Inhaltsordner herzustellen.

1. Klonen Sie das Repository auf Ihrem lokalen Computer.

   ```bash
   git clone https://github.com/{ORG}/{SITE}.git
   ```

   Wenn beim Klonen des Repositorys Fehler auftreten, finden Sie weitere Informationen unter [Fehlerbehebung beim Klonen](https://docs.github.com/en/repositories/creating-and-managing-repositories/troubleshooting-cloning-errors) in der GitHub-Dokumentation.

1. Öffnen Sie das Repository in Ihrem Terminal oder in Ihrer IDE.

1. Checken Sie die `aco` aus

   ```bash
   git checkout aco
   ```

1. Erstellen Sie die Konfigurationsdatei, indem Sie die `default-fstab.yaml` nach `fstab.yaml` kopieren.

   ```bash
   cp default-fstab.yaml fstab.yaml
   ```

1. Aktualisieren Sie den Bereitstellungspunkt in der StoreFront-Konfigurationsdatei so, dass er auf Ihre Inhalts-URL verweist.

   1. Öffnen Sie die [fstab.yaml](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de#vocabulary) Konfigurationsdatei.

      ```json
      mountpoints:
       /: {YOUR_MOUNTPOINT_URL}
      
      folders:
       /products/: /products/default
      ```

   1. Ersetzen Sie `{YOUR_MOUNTPOINT_URL}` durch die URL Ihres Inhaltsordners.

      Wenn Sie beispielsweise Google Drive verwenden, sollte der aktualisierte Code wie folgt aussehen.

      ```json
       mountpoints:
        /: https://drive.google.com/drive/folders/1HXPWdQT-EK09IxVQV5HBSHN4QCA1a56Y
      ```

   1. Speichern Sie die Datei.

#### Überprüfen der Datenverbindungskonfiguration

Die Datenverbindungskonfiguration stellt die Kommunikation zwischen der Storefront und der angegebenen [!DNL Adobe Commerce Optimizer]-Instanz her. Diese Verbindung ermöglicht es, Katalogdaten an die Storefront zu übertragen und verschiedene Storefront-Schnittstellen zu befüllen, einschließlich der Suchkomponenten-, Produktlisten- und Produktdetailseiten.

Für die Ersteinrichtung der Storefront stellen Sie eine Verbindung zur standardmäßigen [!DNL Adobe Commerce Optimizer]-Instanz mit Beispieldaten her.

```json
{
  "public": {
    "default": {
      "commerce-core-endpoint": "https://www.aemshop.net/graphql",
      "commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/Fwus6kdpvYCmeEdcCX7PZg/graphql",
      "headers": {
        "cs": {
          "ac-channel-id": "9ced53d7-35a6-40c5-830e-8288c00985ad",
          "ac-environment-id": "Fwus6kdpvYCmeEdcCX7PZg",
          "ac-price-book-id": "west_coast_inc",
          "ac-scope-locale": "en-US"
        }
      },
      "analytics": {
        "base-currency-code": "USD",
        "environment": "Production",
        "store-id": 1,
        "store-name": "ACO Demo",
        "store-url": "https://www.aemshop.net",
        "store-view-id": 1,
        "store-view-name": "Default Store View",
        "website-id": 1,
        "website-name": "Main Website"
      }
    }
  }
}
```

In dieser Datei geben die folgenden Schlüsselwerte die [!DNL Adobe Commerce Optimizer] an, mit der eine Verbindung hergestellt werden soll, und bestimmen die Daten, die an die Storefront übertragen werden:

* `commerce-endpoint` gibt die Instanz an, mit der eine Verbindung hergestellt werden soll. Sie ist so eingestellt, dass die [!DNL Adobe Commerce Optimizer] verwendet wird. Dieser Endpunkt wird zum Abrufen von Katalogdaten verwendet.
* `ac-environment-id` ist die Mandanten-ID für die [!DNL Adobe Commerce Optimizer].
* `headers` bestimmen die Daten, die von der Instanz zur Storefront fließen.
   * `ac-channel-id` ist auf `west_coast_inc` festgelegt
   * `ac-price-book-id` ist auf `west_coast_inc` festgelegt
   * `ac-scope-locale` ist auf `en-US` festgelegt
   * `ac-price-book-id` ist auf `west_coast_inc` festgelegt

Diese Werte legen die Kanal-ID, das Gebietsschema und die Preisbuch-ID fest, um Katalogdaten an einen bestimmten Vertriebskanal zu senden und diese Daten anhand der angegebenen Gebietsschema- und Preisbuchwerte zu filtern. Später aktualisieren Sie den Endpunkt, um eine Verbindung zur [!DNL Adobe Commerce Optimizer]-Instanz herzustellen, die Adobe für Sie bereitgestellt hat, und ersetzen die Header-Werte, um die Daten aus dieser Instanz abzurufen.

#### Konfigurieren der Sidekick-Erweiterung

Fügen Sie die Projektkonfiguration für die Sidekick-Erweiterung hinzu. Durch diese Konfiguration wird sichergestellt, dass Sidekick zum Verwalten von Inhalten für Ihr Storefront-Projekt verfügbar ist.

>[!NOTE]
>
>Vergewissern Sie sich, dass Sie die [Sidekick-Erweiterung](https://www.aem.live/docs/sidekick#installation) in Ihrem Browser installiert haben.

1. Öffnen Sie die `tools/sidekick/config.json`.

   +++Sidekick-Konfigurationsdatei

   ```json
   {
     "project": "Boilerplate",
     "plugins": [
       {
         "id": "cif",
         "title": "Commerce",
         "environments": [
           "edit"
         ],
         "url": "https://main--{SITE}--{ORG}.aem.live/tools/picker/dist/index.html",
         "isPalette": true,
         "paletteRect": "top: 54px; left: 5px; bottom: 5px; width: 300px; height: calc(100% - 59px); border-radius: var(--hlx-sk-button-border-radius); overflow: hidden; resize: horizontal;"
       },
       {
         "id": "personalisation",
         "title": "Personalisation",
         "environments": [
           "edit"
         ],
         "url": "https://main--{SITE}--{ORG}.aem.live/tools/segments/dist/index.html",
         "isPalette": true,
         "paletteRect": "top: 54px; left: 5px; bottom: 5px; width: 300px; height: calc(100% - 59px); border-radius: var(--hlx-sk-button-border-radius); overflow: hidden; resize: horizontal;"
       }
     ]
   }
   ```

   Weitere Informationen finden Sie in der Dokumentation [&#128279;](https://www.aem.live/docs/sidekick-library) Sidekick-Bibliothek .

   +++

1. Aktualisieren Sie die `url` mit den Werten für Ihr GitHub-Repository.

   * Ersetzen Sie die `{ORG}` Zeichenfolge durch die Organisation oder den Benutzernamen für Ihr Repository.

   * Ersetzen Sie die `{SITE}` Zeichenfolge durch den Repository-Namen

   +++Beispiel einer aktualisierten Konfigurationsdatei

   Wenn Ihr GitHub-Repository `aco-storefront` heißt und Ihre Organisation `early-adopter` ist, sollte die aktualisierte URL wie folgt aussehen:

   ```json
   {
     "project": "Boilerplate",
     "plugins": [
       {
         "id": "cif",
         "title": "Commerce",
         "environments": [
           "edit"
         ],
         "url": "https://main--aco-storefront--early-adopter.aem.live/tools/picker/dist/index.html",
         "isPalette": true,
         "paletteRect": "top: 54px; left: 5px; bottom: 5px; width: 300px; height: calc(100% - 59px); border-radius: var(--hlx-sk-button-border-radius); overflow: hidden; resize: horizontal;"
       },
       {
         "id": "personalisation",
         "title": "Personalisation",
         "environments": [
           "edit"
         ],
         "url": "https://main--aco-storefront--early-adopter.aem.live/tools/segments/dist/index.html",
         "isPalette": true,
         "paletteRect": "top: 54px; left: 5px; bottom: 5px; width: 300px; height: calc(100% - 59px); border-radius: var(--hlx-sk-button-border-radius); overflow: hidden; resize: horizontal;"
       }
     ]
   }
   ```

   +++

1. Speichern Sie die Datei.

### Schritt 4: Aktualisierten Textbausteincode hochladen

Um den benutzerdefinierten Textbausteincode für die Storefront zu verwenden, überschreiben Sie den Code in der `main` mit Ihren Aktualisierungen.

1. Übertragen und speichern Sie die aktualisierten Dateien über Ihren Editor oder Ihre IDE.

   ```bash
   git add .
   ```

1. Vergewissern Sie sich, dass Sie die beiden aktualisierten Dateien übergeben.

   ```bash
   git status
   On branch aco
   Your branch is up to date with 'origin/aco'.
   
   Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        new file:   fstab1.yaml
        modified:   tools/sidekick/config.json
   ```

1. Übergeben Sie die Änderungen an die `aco`.

   ```bash
   git commit -m "Update storefront boilerplate for Adobe Commerce Optimizer"
   ```

1. Überschreiben Sie das Textbaustein auf dem `main` Zweig mit den Änderungen auf dem `aco` Zweig.

   ```bash
   git push origin aco:main -f
   ```

### Schritt 5: AEM Code Sync App hinzufügen

Verbinden Sie Ihr Repository mit dem Edge Delivery-Service, indem Sie die GitHub-App zur AEM-Codesynchronisierung zu Ihrem Repository hinzufügen.

>[!IMPORTANT]
>
>Verbinden Sie die Code-Synchronisierungs-App erst, wenn Sie den aktualisierten Textbausteincode in die Hauptverzweigung Ihres GitHub-Repositorys hochgeladen haben.

1. Öffnen Sie die Konfigurationsseite der [AEM Code Sync App](https://github.com/apps/aem-code-sync).

1. Wählen Sie **Konfigurieren** und authentifizieren Sie sich dann bei dem **&#x200B;**&#x200B;oder **Konto**, das das von Ihnen erstellte Repository enthält.

1. Wählen Sie im Formular **Nur Repositorys auswählen** und wählen Sie das von Ihnen erstellte Repository aus.

1. Wählen Sie **Installieren** aus, um die AEM Code Sync-App zu Ihrem Repository hinzuzufügen.

   Es sollte eine Meldung angezeigt werden, dass die App erfolgreich installiert wurde.

### Schritt 6: Vorschau und Veröffentlichung Ihres Inhalts

Um Inhalte zu Ihrer Storefront hinzuzufügen, zeigen Sie eine Vorschau an und veröffentlichen Sie den Storefront-Inhalt mit der Sidekick-Erweiterung.

1. Öffnen Sie in Google Drive oder SharePoint Ihren Inhaltsordner.

1. Aktivieren Sie Sidekick, indem Sie in der Browser-Symbolleiste auf das Sidekick-Symbol klicken.

   ![[!DNL Turn on Sidekick from browser toolbar]](./assets/storefront-enable-sidekick-toolbar.png){width="700" zoomable="yes"}

   Wenn das Sidekick-Symbol nicht angezeigt wird, stellen Sie sicher, dass die Sidekick-Konfigurationsdatei, die auf der `main` Verzweigung Ihres GitHub-Repositorys `tools/Sidekick/config.json` ist[ korrekt konfiguriert ](#configure-the-sidekick-extension).

1. Verwenden Sie die Sidekick-Symbolleiste, um eine Vorschau anzuzeigen und Ihre Inhalte zu veröffentlichen.

   ![[Dateien für Vorschau und Veröffentlichung auswählen]](./assets/storefront-content-preview-publish.png){width="700" zoomable="yes"}

   Wählen Sie die Dateien in den einzelnen Ordnern separat aus und verwenden Sie die Sidekick-Symbolleiste, um eine Vorschau anzuzeigen und alle Dateien zu veröffentlichen.

   * **Preview**-Lädt Inhalte in die Staging-Umgebung hoch. Staging-URLs der Storefront enden mit `.aem.page`.

   * **Veröffentlichen** lädt Inhalte in die Produktionsumgebung hoch. Produktions-URLs enden mit `aem.live`.

Weitere Informationen finden Sie in der Dokumentation zu Adobe Experience Manager [Sidekick](https://www.aem.live/docs/sidekick).

### Schritt 7: Vorschau der Site

Stellen Sie sicher, dass sowohl der Beispielinhalt als auch die Daten aus der Adobe Commerce Optimizer-Demoinstanz korrekt angezeigt werden.

* **Beispielinhalt** wird aus Ihrem freigegebenen Inhaltsordner bereitgestellt. Dazu gehören die Seitenlayouts, Banner und andere Inhalte, die Sie mit Sidekick veröffentlicht haben.
* **Beispieldaten** werden von der [!DNL Adobe Commerce Optimizer] Demoinstanz bereitgestellt. Die Daten enthalten Produktdaten mit Produktattributen, Bildern, Produktbeschreibungen und Preisen, die auf der Grundlage der Header-Werte ausgefüllt werden, die in der Storefront-Konfigurationsdatei `config.json` angegeben sind.


#### Verbinden Sie sich mit Ihrer Site, um Beispielinhalte und -daten anzuzeigen

1. Verbinden Sie sich mit Ihrer Site, indem Sie zu `https://main--{SITE}--{ORG}.aem.live` navigieren.

   Ersetzen Sie `{ORG}` und `{SITE}` durch die Organisation und den Namen für Ihr Textbausteinrepository.

   ![[!DNL ACO storefront site with boilerplate]](./assets/aco-storefront-site-boilerplate.png){width="700" zoomable="yes"}

   Wenn die Seite eine 404 zurückgibt, stellen Sie sicher, dass Sie den Inhalt mit der Sidekick-Erweiterung veröffentlicht haben. Überprüfen Sie außerdem, ob der Bereitstellungspunkt in der aktualisierten `fstab.yaml`-Datei auf den von Ihnen erstellten Inhaltsordner verweist.

1. Zeigen Sie die Beispielkatalogdaten aus der Commerce Optimizer-Standardinstanz an.

   1. Suchen Sie nach `tires`, um eine Dropdown-Liste der verfügbaren Reifenprodukte anzuzeigen.

   ![[!DNL Discover Adobe Commerce Optimizer products]](./assets/storefront-site-with-aco-data.png){width="700" zoomable="yes"}

   Die Suchkomponente ist Teil des Textbausteincodes für die Storefront. Die Suchergebnisdaten werden basierend auf der Storefront-Konfiguration in `config.json` ausgefüllt.

   1. Drücken Sie **Eingabetaste**, um die Produktlistenseite anzuzeigen.

      ![[!DNL View product details page]](./assets/storefront-with-aco-pdp-page.png){width="675" zoomable="yes"}

   1. Zeigen Sie eine Produktdetailseite an, indem Sie ein beliebiges Reifenprodukt auf der Seite auswählen.

      Wenn Sie die Storefront erkunden, beachten Sie, dass einige der Komponenten nicht funktionieren. Wenn Sie beispielsweise ein Produkt zum Warenkorb hinzufügen, wird ein Fehler zurückgegeben, und die Komponenten für die Kontoverwaltung funktionieren nicht. Diese Probleme treten auf, weil diese Komponenten nicht für den Empfang von Daten aus einem Commerce-Backend konfiguriert wurden. Mit den Daten aus der [!DNL Adobe Commerce Optimizer]-Instanz werden nur die Seiten „Suchkomponente“, „Produktliste“ und „Produktdetails“ ausgefüllt.

   1. Fahren Sie nach dem Erkunden der Storefront mit dem Tutorial fort.


### Schritt 8: Entwickeln Sie die Storefront in Ihrer lokalen Umgebung

In diesem Abschnitt aktualisieren Sie die Storefront-Konfiguration aus Ihrer lokalen Entwicklungsumgebung.

* Aktualisieren Sie die Storefront-Konfiguration, um eine Verbindung zum GraphQL-Endpunkt für die [!DNL Adobe Commerce Optimizer]-Instanz herzustellen, die Adobe für Sie bereitgestellt hat.
* Aktualisieren Sie die Header-Werte, um Daten aus Ihrer -Instanz abzurufen.

#### Start der lokalen Entwicklung

1. Checken Sie in Ihrer IDE den Hauptzweig Ihres GitHub-Code-Repositorys aus.

   ```bash
   git checkout main
   ```

1. Installieren Sie die erforderlichen Abhängigkeiten.

   ```bash
   npm install
   ```

1. Starten Sie den lokalen Entwicklungsserver.

   ```bash
   npm start
   ```

   Die erste Seite Ihrer TextbausteinStorefront sollte in Ihrem Browser unter `http://localhost:3000` angezeigt werden.

![[!DNL Configure github repo to pull all branches from boilerplate repo]](./assets/aco-storefront-local-dev-env.png){width="700" zoomable="yes"}


#### Aktualisieren der Storefront-Konfiguration

Aktualisieren Sie die Konfigurationsdatei für die Storefront und zeigen Sie eine Vorschau der Änderungen in Ihrer lokalen Entwicklungsumgebung an.


1. Aktualisieren Sie in Ihrer IDE die Storefront-Konfiguration, um eine Verbindung zur [!DNL Adobe Commerce Optimizer]-Instanz herzustellen, die Adobe für Sie bereitgestellt hat.

   1. Öffnen Sie die `config.json`.

   1. Aktualisieren Sie die folgenden Werte mithilfe des -Endpunkts für Ihre [!DNL Adobe Commerce Optimizer]-Instanz:

      * **`commerce-endpoint`**-Ersetzen Sie den vorhandenen Wert durch Ihre Endpunkt-URL.

        ```json
        "commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/{tenantId}/graphql"
        ```

      * **`ac-environment-id`** - Ersetzen Sie den vorhandenen Wert durch die Mandanten-ID aus Ihrer Endpunkt-URL.

        ```json
        "ac-environment-id": "{tenantId}"
        ```

   1. Speichern Sie die Datei.

      Wenn Ihre lokale Vorschau ordnungsgemäß funktioniert, werden die Aktualisierungen auf Ihre lokale Storefront angewendet.

1. Überprüfen Sie die Site, um die Ergebnisse der Konfigurationsänderung anzuzeigen.

   1. Navigieren Sie im Browser zu `http://localhost:3000` und aktualisieren Sie die Seite.

   1. Klicken Sie in der Kopfzeile der Storefront auf die Lupe, um nach `tires` zu suchen.

      ![Nach Reifen suchen](./assets/storefront-header-empty-search-list.png){width="675" zoomable="yes"}

      Beachten Sie, dass die Dropdown-Liste nicht gefüllt wird.

   1. Drücken Sie **Eingabetaste**, um die Produktlistenseite anzuzeigen.

      ![Leere Suchergebnisse mit ungültigen Kopfzeilenwerten](./assets/storefront-configuration-with-incorrect-headers.png){width="675" zoomable="yes"}

      Die Suche gibt keine Ergebnisse zurück, da die Header-Werte in Ihrer Storefront-Konfigurationsdatei auf der Standardinstanz basieren. Jetzt, da die Konfiguration auf die für Sie bereitgestellte [!DNL Adobe Commerce Optimizer]-Instanz verweist, sind diese Werte ungültig.

### Nächste Schritte

Siehe den [End-to-End-Anwendungsfall für Storefront- und ](./use-case/admin-use-case.md)-Administratoren ), um mehr über die Verwaltung und Anzeige von Inhalten und Daten in der Storefront zu erfahren.

>[!MORELIKETHIS]
>
>* [Dokumentation zur Adobe Experience Manager-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de) um mehr über das Aktualisieren von Website-Inhalten und die Integration mit Commerce-Frontend-Komponenten und Backend-Daten zu erfahren.
></br></br>
>* [Dokumentation zur Adobe Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de) um mehr über das Aktualisieren von Website-Inhalten und die Integration mit Adobe Commerce-Frontend-Komponenten und Backend-Daten zu erfahren.
