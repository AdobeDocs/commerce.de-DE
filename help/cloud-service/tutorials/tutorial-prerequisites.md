---
title: Voraussetzungen für das Tutorial
description: Erfahren Sie mehr über die Voraussetzungen und Einrichtungsschritte für Adobe Commerce as a Cloud Service-Tutorials, einschließlich Erweiterungs- und Storefront-Entwicklungs-Tools.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
source-git-commit: 1848c9dda4a1976e1bccb4d1f9d5a2e21540fc0b
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---

# Voraussetzungen für das Tutorial

Auf dieser Seite werden die Voraussetzungen und Einrichtungsschritte für [!DNL Adobe Commerce as a Cloud Service] Tutorials aufgelistet, z. B[ das Tutorial zur Erweiterung von Bewertungen ](./ratings-extension.md) das Tutorial [Erweiterung der Versandmethode](./shipping-method-extension.md).

## Allgemeine Voraussetzungen

In diesem Tutorial sind die folgenden Tools für die Entwicklung von Erweiterungen und Storefronts erforderlich.

* [!DNL Node.js] (Version `22.x.x`) und npm (`9.0.0` oder höher): Überprüfen Sie Ihre Installation mit dem folgenden Befehl:

  ```bash
  node --version
  npm --version
  ```

* Installieren von [Git](https://git-scm.com) - Überprüfen Sie Ihre Installation:

  ```bash
  git --version
  ```

* Bash-Shell
   * macOS/Linux: Keine Installation erforderlich
   * Windows: Verwenden Sie [Git Bash](https://git-scm.com/install) oder [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install)

* Laden Sie eine KI-unterstützte IDE herunter, z. B[Cursor](https://cursor.com/download) (empfohlen). Andere IDEs wie Claude Code, Gemini CLI oder Copilot werden ebenfalls unterstützt, erfordern jedoch möglicherweise Änderungen an den Eingabeaufforderungen und anderen Schritten im Tutorial.

## Voraussetzungen für [!DNL Adobe Commerce as a Cloud Service]

* Installieren des [!DNL Adobe I/O CLI]

  ```bash
  npm install -g @adobe/aio-cli
  ```

* Installieren Sie die Plug-ins [Adobe I/O CLI Commerce](https://github.com/adobe-commerce/aio-cli-plugin-commerce), [Adobe I/O CLI Runtime](https://github.com/adobe/aio-cli-plugin-runtime) und [App Builder CLI](https://github.com/adobe/aio-cli-plugin-app-dev):

  ```bash
  aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce @adobe/aio-cli-plugin-app-dev @adobe/aio-cli-plugin-runtime
  ```

### Voraussetzungen für Adobe Developer Console

Richten Sie in der Adobe Developer Console ein Projekt mit den erforderlichen APIs und Anmeldeinformationen ein.

1. Navigieren Sie zur [Adobe Developer Console](https://developer.adobe.com/console){target="_blank"}.
1. Melden Sie sich mit Ihrer E-Mail-Adresse und Ihrem Passwort an.

#### Neues Projekt erstellen

Erstellen Sie ein App Builder-Projekt in der Adobe Developer Console, um Ihre Erweiterung zu hosten.

1. Navigieren Sie zu [Adobe Developer Console](https://developer.adobe.com/).
1. Klicken Sie auf **[!UICONTROL Create project from a template]**.
1. Wählen Sie die **[!UICONTROL App Builder]** aus.
1. Geben Sie einen **[!UICONTROL Project Title]** und einen **[!UICONTROL App Name]** ein.
1. Stellen Sie sicher, dass das Kontrollkästchen **[!UICONTROL Include Runtime]** markiert ist.

   ![Adobe Developer Console-Projekterstellung mit ausgewählter App Builder-Vorlage](../assets/app-builder-template.png){width="600" zoomable="yes"}

1. Klicken Sie auf **[!UICONTROL Save]**.

#### Hinzufügen von APIs zum Arbeitsbereich

Fügen Sie Ihrem Staging-Arbeitsbereich die erforderlichen APIs für die Ereignisverwaltung und Commerce-Integration hinzu.

1. Klicken Sie auf Arbeitsbereich **[!UICONTROL Stage]** und wiederholen Sie dann die folgenden Schritte für jede API.

   ![Staging-Arbeitsbereich mit Option „Service hinzufügen“ für APIs](../assets/add-apis-workspace.png){width="600" zoomable="yes"}

1. Klicken Sie auf **[!UICONTROL Add Service]** und wählen Sie **[!UICONTROL API]** aus.

1. Wählen Sie eine der folgenden APIs aus. Wiederholen Sie diesen Vorgang für jede unten aufgeführte API:

   * **[!UICONTROL Adobe Services]**:
      * **[!UICONTROL I/O Management API]**
      * **[!UICONTROL I/O Events]** API
   * **[!UICONTROL Experience Cloud]**:
      * **[!UICONTROL Adobe I/O Events for Adobe Commerce]** API

1. Klicken Sie auf **[!UICONTROL Next]**.

1. Klicken Sie auf **[!UICONTROL Save configured API]**.

1. Wiederholen Sie die vorherigen Schritte, bis Sie alle APIs zum Arbeitsbereich hinzufügen.

   ![Workspace mit allen erfolgreich hinzugefügten erforderlichen APIs](../assets/apis-added.png){width="600" zoomable="yes"}

### Konfigurieren der Adobe I/O-CLI

Verbinden Sie die [!DNL Adobe I/O CLI] mit Ihrer Organisation, Ihrem Projekt und Ihrem Arbeitsbereich.

1. Löschen Sie eine vorhandene Konfiguration:

   ```bash
   aio config clear
   ```

1. Melden Sie sich mit dem [!DNL Adobe I/O CLI] an:

   ```bash
   aio auth login -f
   ```

1. Wählen Sie Ihre Organisation, Ihr Projekt und Ihren Arbeitsbereich mit jedem der folgenden Befehle aus:

   ```bash
   aio console org select
   ```

   ```bash
   aio console project select
   ```

   ```bash
   aio console workspace select
   ```

   ![Terminal mit Auswahl der Adobe I/O CLI-Organisationsprojekte und des Arbeitsbereichs](../assets/cli-configuration.png){width="600" zoomable="yes"}

### Klonen der Starter Kits

Klonen Sie eines der folgenden Commerce Starter Kit-Repositorys für die Erweiterung, die Sie erstellen, und bereiten Sie Ihr Projekt vor:

Integrations-Starter-Kit:

```bash
git clone https://github.com/adobe/commerce-integration-starter-kit.git extension
cd extension
```

Checkout-Starterkit:

```bash
git clone https://github.com/adobe/commerce-checkout-starter-kit.git extension
cd extension
```

>[!BEGINTABS]

>[!TAB Integrations-Starter-Kit]

### Erstellen einer .env-Datei

Erstellen Sie die Konfigurationsdatei Ihrer Umgebung:

```bash
cp env.dist .env
```

Öffnen Sie die `.env` in einem Texteditor und fügen Sie die folgenden OAuth-Anmeldeinformationen hinzu:

```bash
OAUTH_CLIENT_ID=
OAUTH_CLIENT_SECRET=
OAUTH_TECHNICAL_ACCOUNT_ID=
OAUTH_TECHNICAL_ACCOUNT_EMAIL=
OAUTH_ORG_ID=
```

Kopieren Sie diese Werte von der **[!UICONTROL Credential details]** in [Developer Console](https://developer.adobe.com/) indem Sie auf die Registerkarte **[!UICONTROL OAuth Server-to-Server]** in Ihrem Arbeitsbereich klicken.

![Seite mit OAuth Server-zu-Server-Anmeldeinformationen in Adobe Developer Console](../assets/oauth-credentials.png){width="600" zoomable="yes"}

#### Hinzufügen der Commerce-Konfiguration

Fügen Sie die folgenden Commerce-Instanzdetails zu Ihrer `.env` hinzu:

```bash
COMMERCE_BASE_URL=
COMMERCE_GRAPHQL_ENDPOINT=
```

So suchen Sie diese Werte:

1. Navigieren Sie zu [Commerce Cloud Service-Instanzen](https://experience.adobe.com/#/@commerce/commerce/cloud-service/instances).
1. Klicken Sie auf das Informationssymbol neben Ihrer Instanz.
1. Kopieren Sie den REST-Endpunkt nach `COMMERCE_BASE_URL`.
1. Kopieren Sie den GraphQL-Endpunkt nach `COMMERCE_GRAPHQL_ENDPOINT`.

#### Festlegen des Ereignispräfixes

Legen Sie einen temporären Wert für das Ereignispräfix fest:

```bash
EVENT_PREFIX=test
```

### Herunterladen der Workspace-Konfiguration

Führen Sie den folgenden Befehl aus, um die Workspace-Konfigurationsdatei herunterzuladen:

```bash
aio console workspace download workspace.json
```

Kopieren Sie die Workspace-Konfigurationsdatei in das `scripts`:

```bash
cp workspace.json scripts/
```

### Verbinden des lokalen Arbeitsbereichs mit dem Remote-Arbeitsbereich

Verknüpfen des lokalen Projekts mit dem Remote-Arbeitsbereich:

```bash
aio app use workspace.json -m
```

![Terminal, das eine erfolgreiche Arbeitsbereich-Verbindung mit dem AIO-Programm-Anwendungsbefehl anzeigt](../assets/connect-workspace.png){width="600" zoomable="yes"}

>[!TAB Checkout-Starterkit]

### Lokalen Arbeitsbereich mit Remote-Arbeitsbereich verbinden

Verknüpfen des lokalen Projekts mit dem Remote-Arbeitsbereich. Führen Sie im Stammverzeichnis des Projekts (`extension` Ordner) Folgendes aus:

```bash
aio app use --merge
```

Wählen Sie bei Aufforderung die Option aus, die die Organisation, das Projekt und den Arbeitsbereich verwendet, die Sie beim Konfigurieren der Adobe I/O-CLI ausgewählt haben. Dadurch wird die Workspace-Konfiguration in Ihre App geschrieben, damit sie bereitgestellt und für die lokale Entwicklung verwendet werden kann.

![Terminal, das eine erfolgreiche Arbeitsbereich-Verbindung mit dem AIO-Programm-Anwendungsbefehl anzeigt](../assets/connect-workspace.png){width="600" zoomable="yes"}

>[!ENDTABS]

### Installieren der KI-Tools für die Erweiterbarkeit

Dieser Prozess erstellt die MCP-Konfiguration (`.<agent>/mcp.json`), das Skills-Verzeichnis (`.<agent>/skills/`) und fügt `AGENTS.md` zum Projektstamm hinzu. Sie werden aufgefordert, ein Starter Kit, einen Codierungsagenten und einen Package Manager auszuwählen.


1. Richten Sie die KI-unterstützten Entwicklungstools mithilfe der folgenden Befehle im Ordner &quot;`extension`&quot; ein:

   ```bash
   cd extension
   ```

   ```bash
   aio commerce extensibility tools-setup
   ```

   ![Terminal mit der Befehlsausgabe für die Einrichtung von KI-Erweiterbarkeitstools](../assets/install-ai-tools.png){width="600" zoomable="yes"}

1. Starten Sie nach Abschluss des Setups Ihren Codierungsagenten neu, damit er die neuen MCP-Tools und -Kenntnisse laden kann. Die Commerce App Builder-Tools sind jetzt in Ihrer Umgebung verfügbar.

   >[!NOTE]
   >
   >Wenn eine Warnung angezeigt wird, dass keine Kenntnisse für das Starter Kit gefunden wurden, ist ein Fehler aufgetreten - häufig, weil das Setup in einem anderen Ordner als dem, in dem das Starter Kit geklont wurde, ausgeführt wurde. Führen Sie `aio commerce extensibility tools-setup` aus dem `extension`-Ordner (dem Stammverzeichnis des Starter Kit-Projekts) aus und wählen Sie das entsprechende Starter Kit aus, wenn Sie dazu aufgefordert werden.

   ![Terminal mit KI-Erweiterbarkeits-Tools-Setup mit ausgewähltem Checkout-Starter-Kit](../assets/tools-setup-checkout.png){width="600" zoomable="yes"}

## Voraussetzungen für die Storefront

Die folgenden Elemente sind erforderlich, um den Abschnitt [Storefront](./ratings-extension.md#connect-to-the-storefront) des Tutorials [Ratings-Erweiterung](./ratings-extension.md) abzuschließen und Produktbewertungen in Ihrem Store anzuzeigen.

* [Google Chrome](https://www.google.com/chrome/) - Zum Testen der Storefront erforderlich

* Ein Storefront-Projekt, das mit Ihrer [!DNL Commerce] verbunden ist. Wenn Sie kein Storefront-Projekt haben, führen Sie die Schritte in [Storefront erstellen](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/){target="_blank"} aus, einschließlich des Abschnitts [Repo mit Commerce-Daten verknüpfen](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/#link-repo-to-commerce-data){target="_blank"}.

### Klonen des Storefront-Repositorys

Öffnen Sie Ihr Terminal und klonen Sie das Repository :

```bash
git clone --branch agentic-dev https://github.com/hlxsites/aem-boilerplate-commerce.git storefront
cd storefront
```

### Installieren der Abhängigkeiten

Installieren Sie die Projektabhängigkeiten:

```bash
npm install
```

### Installieren der KI-Tools für die Storefront

Richten Sie die KI-unterstützten Entwicklungs-Tools im Ordner `storefront` ein. Führen Sie den folgenden Befehl aus dem Stammverzeichnis Ihres Textbausteinprojekts aus:

```bash
aio commerce extensibility tools-setup
```

Der Befehl führt Sie durch zwei Eingabeaufforderungen:

1. **Starter Kit auswählen** — Wählen Sie **AEM Boilerplate Commerce**.

1. **Codierungsagent auswählen** - Wählen Sie Ihren Agenten aus der Liste der unterstützten Agenten aus.

Der Befehl installiert das `@adobe-commerce/commerce-extensibility-tools`-Paket als Dev-Abhängigkeit, kopiert die Skill-Dateien in das Skill-Verzeichnis Ihres Agenten und konfiguriert MCP (Model Context Protocol), damit Ihr Agent auf Commerce-Dokumentationssuchwerkzeuge zugreifen kann.