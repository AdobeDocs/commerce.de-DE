---
title: Einrichten der Storefront
description: Erfahren Sie, wie Sie Ihre Storefront  [!DNL Adobe Commerce Optimizer] .
role: Developer
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 2b4c9e98-a30c-4a33-b356-556de5bd721a
source-git-commit: 7ff78711972cbd73fc75f7523d8ac734081dbe10
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 0%

---

# Einrichten der Storefront

>[!NOTE]
>
>In dieser Dokumentation wird ein Produkt beschrieben, das sich in der Entwicklung für den frühzeitigen Zugriff befindet und nicht alle für die allgemeine Verfügbarkeit vorgesehenen Funktionen enthält.

In diesem Tutorial erfahren Sie, wie Sie eine [Adobe Commerce-Storefront mit Edge Delivery Services](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/) einrichten und verwenden, um eine leistungsstarke, skalierbare und sichere Commerce-Storefront auf der Grundlage von Daten aus Ihrer [!DNL Adobe Commerce Optimizer]-Instanz zu erstellen.


## Voraussetzungen

* Stellen Sie sicher, dass Sie über ein GitHub-Konto (github.com) verfügen, das Repositorys erstellen kann und für die lokale Entwicklung konfiguriert ist.

* Erfahren Sie mehr über die Konzepte und den Workflow zur Entwicklung von Commerce-Storefronts mit Adobe Edge Delivery Services [ Sie in der Dokumentation ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started) Adobe Commerce-Storefront .
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
>Zusätzliche Ressourcen zum Erweitern und Anpassen Ihrer [!DNL Adobe Commerce Optimizer]-Lösung sind über [App Builder für Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) und [API Mesh für Adobe Developer App Builder](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/api-mesh/getting-started-api-mesh) verfügbar. Wenden Sie sich für Informationen zu Zugriff und Nutzung an Ihren Adobe-Kundenbetreuer.

#### Installieren von Sidekick

Installieren Sie die Sidekick-Browser-Erweiterung, um Inhalte zu bearbeiten, in der Vorschau anzuzeigen und in der Storefront zu veröffentlichen. Siehe [Sidekick-Installationsanweisungen](https://www.aem.live/docs/sidekick#installation).

## Erstellen einer Storefront

Die Storefront, die Sie für Ihr [!DNL Adobe Commerce Optimizer]-Projekt erstellen, verwendet eine angepasste Version des Textbausteins Adobe Commerce on Edge Delivery Services Storefront . Das Textbaustein ist ein Satz von Dateien und Ordnern, die einen Ausgangspunkt für die Entwicklung von Storefronts bieten. Dieser Einrichtungsprozess unterscheidet sich vom standardmäßigen Einrichtungsprozess für eine [Adobe Commerce in der Edge Delivery Services-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/).

>[!NOTE]
>
>In diesem Tutorial werden macOS, Chrome und Visual Studio Code als Entwicklungsumgebung verwendet. Der Bildschirm erfasst und Anweisungen spiegeln diese Einrichtung wider. Sie können ein anderes Betriebssystem, einen anderen Browser und einen anderen Code-Editor verwenden, aber die angezeigte Benutzeroberfläche und die von Ihnen durchgeführten Schritte variieren entsprechend.

### Workflow-Übersicht

Führen Sie diese Schritte aus, um eine Storefront zur Verwendung mit [!DNL Adobe Commerce Optimizer] einzurichten.

1. **[Erstellen eines Code-Repositorys](#step-1-create-site-code-repository)**-Erstellen Sie ein GitHub-Repository aus der Textvorlage Adobe Commerce + Edge Delivery Services . Schließen Sie alle Verzweigungen aus dem Quell-Repository ein.
1. **[Storefront-Textbaustein aktualisieren](#step-2-update-the-storefront-boilerplate)**-Aktualisieren Sie die benutzerdefinierte Textbausteinvorlage auf der `aco` Verzweigung, um Ihren Inhaltsordner mit der Storefront zu verbinden.
1. **[Änderungen bereitstellen](#step-3-deploy-changes)** - Überschreiben Sie den Code auf der `main` Verzweigung mit dem aktualisierten Code aus der `aco` Verzweigung.
1. **[Fügen Sie die CodeSync-App hinzu](#step-5-add-the-aem-code-sync-app)**-Verbinden Sie Ihr Repository mit dem Edge Delivery-Service. Verbinden Sie die Code-Synchronisierungs-App erst, wenn Sie die Anpassung des Quell-Codes abgeschlossen und den Code in die `main` Verzweigung verschoben haben.
1. **[Inhalt hinzufügen](#step-6-add-content)**-Verwenden Sie das Tool zum Klonen von Demoinhalten, um Ihren Storefront-Inhalt in der auf `https://da.live` gehosteten Dokumentenautorenumgebung zu erstellen und zu initialisieren.
1. **[Vorschau der Demo-Site](#step-7-preview-demo-site)**-Stellen Sie eine Verbindung zu Ihrer Storefront-Site her, um die Beispielinhalte und -daten aus der [!DNL Adobe Commerce Optimizer] Demo-Instanz anzuzeigen.
1. **[Entwickeln Sie in Ihrer lokalen Umgebung](#step-8-develop-in-your-local-environment)**-Installieren Sie die erforderlichen Abhängigkeiten. Starten Sie den lokalen Entwicklungs-Server und aktualisieren Sie die Storefront-Konfiguration, um eine Verbindung zur [!DNL Adobe Commerce Optimizer]-Instanz herzustellen, die Adobe für Sie bereitgestellt hat.
1. **[Nächste Schritte](#next-steps)**-Erfahren Sie mehr über die Verwaltung und Anzeige von Inhalten und Daten in der Storefront.


### Schritt 1: Erstellen des Site-Code-Repositorys

Erstellen Sie mithilfe der Textbausteinvorlage von Edge Delivery Services und Adobe Commerce ein GitHub-Repository für den Site-Textbausteincode für Ihre Storefront.

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

### Schritt 2: Schaufenster aktualisieren

Sie benötigen die folgenden Informationen, um den Textbausteincode der Storefront zu aktualisieren:

* **GitHub-Repository-URL aus Schritt 2**— `github.com/{ORG}/{SITE}`

   * `{ORG}` ist der Organisationsname oder Benutzername für das Repository.

   * `{SITE}` ist Ihr Repository-Name

* **Inhaltsordner-URL aus Schritt 1**— `https://drive.google.com/drive/folders/{YOUR_FOLDER_ID}`

  `{YOUR_FOLDER_ID}` ist die ID des Ordners, den Sie mit den Beispielinhaltsdaten erstellt haben.

#### Verknüpfen des Repositorys mit der Dokumentautorenumgebung

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

   1. Öffnen Sie die [fstab.yaml](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/#vocabulary) Konfigurationsdatei.

      ```yaml
      mountpoints:
        /:
          url: https://content.da.live/{org}/{site}/
          type: markup
      
      folders:
       /products/: /products/default
      ```

   1. Ersetzen Sie die `{ORG}` und `{SITE}` Zeichenfolgen durch die Werte für das GitHub-Repository, die Sie für Ihren Textbausteincode erstellt haben.

      Der aktualisierte Code sollte beispielsweise wie folgt aussehen.

      ```yaml
      mountpoints:
        /:
          url: https://content.da.live/owner-name/aco-storefront/
          type: markup
      ```

   1. Speichern Sie die Datei.

#### Konfigurieren der Sidekick-Erweiterung

1. Fügen Sie die Projektkonfiguration für die Sidekick-Erweiterung hinzu. Durch diese Konfiguration wird sichergestellt, dass Sidekick zum Verwalten von Inhalten für Ihr Storefront-Projekt verfügbar ist.

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

   Weitere Informationen finden Sie in der Dokumentation [ Sidekick-Bibliothek ](https://www.aem.live/docs/sidekick-library).

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

### Schritt 3: Änderungen bereitstellen

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

1. Wählen Sie im Formular **Nur Repositorys auswählen** und wählen Sie dann das von Ihnen erstellte Repository aus.

1. Wählen Sie **Installieren** aus, um die AEM Code Sync-App zu Ihrem Repository hinzuzufügen.

   Es sollte eine Meldung angezeigt werden, dass die App erfolgreich installiert wurde.

### Schritt 6: Inhalt hinzufügen

Erstellen und initialisieren Sie Ihren Storefront-Inhalt in der auf `https://da.live` gehosteten Dokumentautorenumgebung mit dem Site Creator -Tool. Dieses Tool importiert den Beispielinhalt in die Dokumentautorenumgebung und schließt den Inhaltsvorschau- und Veröffentlichungsprozess für alle Dokumente im Beispielinhalt ab. Der Beispielinhalt umfasst die Seitenlayouts, Banner, Beschriftungen und andere Elemente, die in Ihre Storefront eingefügt werden.

1. Öffnen Sie das [Tool Site Creator](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator).

1. Konfigurieren des Repositorys:

   * Wählen Sie **[!UICONTROL Use Existing Repository]** aus.
   * Geben Sie die **[!UICONTROL Organization/Username]** für Ihr Textbausteinprojekt für die Storefront ein.
   * Geben Sie die **[!UICONTROL Repository Name]** ein.

1. Importieren Sie die Inhalte in die Dokumentenautorenumgebung, zeigen Sie eine Vorschau an und veröffentlichen Sie sie, indem Sie **Site erstellen** auswählen.

   ![[!DNL AEM demo content clone tool]](./assets/storefront-edit-initial-content.png){width="700" zoomable="yes"}

   Nachdem die Site erstellt wurde, können Sie die Links in den Abschnitten [!UICONTROL Edit content] und [!UICONTROL View Site] verwenden, um die Demo-Storefront zu erkunden.

   Die wichtigsten Links zu Ihrem Inhalt und Ihrer Site folgen diesen Formaten:

   * **Stamminhaltsordner**— `https://da.live/#/{ORG}/{SITE}`
   * **Site-Vorschau**—   `https://main--{SITE}--{ORG}.aem.page/`
   * **Site-Produktion:**— `https:/main--{SITE}--{ORG}.ae.live/`

1. Öffnen Sie den Link für den Stamminhaltsordner, um den Inhalt anzuzeigen.

   ![[!DNL Storefront Document Author environment]](./assets/storefront-document-author-environment.png){width="700" zoomable="yes"}

   >[!TIP]
   >
   >Verwenden Sie in der Seitennavigation die Links [!UICONTROL **Lernen**] und [!UICONTROL **Entdecken**], um auf Lernressourcen zur Verwaltung Ihrer Site- und Site-Inhalte zuzugreifen.

### Schritt 7: Vorschau der Demo-Site

Stellen Sie sicher, dass sowohl der Beispielinhalt als auch die Daten aus der Adobe Commerce Optimizer-Demoinstanz korrekt angezeigt werden.

* **Beispielinhalt** wird aus dem Inhaltsordner in der Dokumentautorenumgebung bereitgestellt. Sie enthält die Seitenlayouts, Banner und Beschriftungen für Ihre Site.
* **Beispieldaten** werden von der [!DNL Adobe Commerce Optimizer] Demoinstanz bereitgestellt. Die Daten enthalten Produktdaten mit Produktattributen, Bildern, Produktbeschreibungen und Preisen, die auf der Grundlage der Header-Werte ausgefüllt werden, die in der Storefront-Konfigurationsdatei `config.json` angegeben sind.

#### Verbinden Sie sich mit Ihrer Site, um Beispielinhalte und -daten anzuzeigen

1. Zeigen Sie Ihre Site an, indem Sie zu `https://main--{SITE}--{ORG}.aem.live` navigieren.

   Ersetzen Sie `{ORG}` und `{SITE}` durch die Organisation und den Namen für Ihr Textbausteinrepository.

   ![[!DNL ACO storefront site with boilerplate]](./assets/aco-storefront-site-boilerplate.png){width="700" zoomable="yes"}

   Wenn die Seite eine 404 zurückgibt, überprüfen Sie Folgendes:

   * [Der Bereitstellungspunkt in Ihrer `fstab.yaml` verweist auf die richtige Inhalts-URL](#link-the-repository-to-the-document-author-environment): `https://content.da.live/{ORG}/{SITE}/`
   * [Sie haben die Code-Sync-App so konfiguriert, dass sie eine Verbindung zu Ihrem GitHub-Repository herstellt](#step-5%3A-add-the-aem-code-sync-app).
   * [Sie haben den Inhalt mithilfe des Demo-Tools zum Klonen von Inhalten in der Dokumentautorenumgebung veröffentlicht](#step-6%3A-add-content-documents-for-your-storefront).


1. Zeigen Sie die Beispielkatalogdaten aus der Commerce Optimizer-Standardinstanz an.

   1. Klicken Sie in der Kopfzeile der Storefront auf die Lupe, um nach `tires` zu suchen.

      ![[!DNL View product list page]](./assets/storefront-site-with-aco-data.png){width="675" zoomable="yes"}

   1. Drücken Sie **Eingabetaste**, um die Suchergebnisseite anzuzeigen.

      ![[!DNL View search results page]](./assets/storefront-with-aco-search-results-page.png){width="675" zoomable="yes"}

      Die Komponenten der Suchergebnisseite werden durch das `search` Inhaltsdokument definiert. Die Suchergebnisdaten werden basierend auf der Storefront-Konfiguration in `config.json` ausgefüllt.

   1. Zeigen Sie die Seite mit den Produktdetails an, indem Sie ein beliebiges Reifenprodukt auf der Seite auswählen.

      ![[!DNL View product details page]](./assets/storefront-with-aco-pdp-page.png){width="675" zoomable="yes"}

      Die Komponenten der Produktdetailseite werden durch das `default` Inhaltsdokument im `product` definiert.

### Schritt 8: Entwickeln in Ihrer lokalen Umgebung

In diesem Abschnitt aktualisieren Sie die Storefront-Konfiguration aus Ihrer lokalen Entwicklungsumgebung.

* Aktualisieren Sie die Storefront-Konfiguration, um eine Verbindung zum GraphQL-Endpunkt für die [!DNL Adobe Commerce Optimizer]-Instanz herzustellen, die Adobe für Sie bereitgestellt hat.
* Aktualisieren Sie die Header-Werte, um Daten aus Ihrer -Instanz abzurufen.

#### Start der lokalen Entwicklung

1. Checken Sie in Ihrer IDE Ihren Hauptzweig aus und setzen Sie ihn auf den letzten Commit auf der Remote-Verzweigung zurück.

   ```bash
   git checkout main
   git reset --hard origin/main
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

   1. Drücken Sie **Eingabetaste**, um die Suchergebnisseite anzuzeigen.

      ![Leere Suchergebnisse mit ungültigen Kopfzeilenwerten](./assets/storefront-configuration-with-incorrect-headers.png){width="675" zoomable="yes"}

      Die Suche gibt keine Ergebnisse zurück, da die Header-Werte in Ihrer Storefront-Konfigurationsdatei auf der Standardinstanz basieren. Jetzt, da die Konfiguration auf die für Sie bereitgestellte [!DNL Adobe Commerce Optimizer]-Instanz verweist, sind diese Werte ungültig.

### Nächste Schritte

Siehe den [End-to-End-Anwendungsfall für Storefront- und ](./use-case/admin-use-case.md)-Administratoren ), um mehr über die Verwaltung und Anzeige von Inhalten und Daten in der Storefront zu erfahren.

>[!MORELIKETHIS]
>
> Weitere Informationen zum Aktualisieren von Website-Inhalten und [ Integration mit Commerce-Frontend-Komponenten und Backend-Daten finden Sie in der Dokumentation zur ](https://experienceleague.adobe.com/developer/commerce/storefront/)Adobe Commerce Storefront .
