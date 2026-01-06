---
title: Voraussetzungen für das Tutorial zur Bewertungserweiterung
description: Lernen Sie die Voraussetzungen für das Labor der Bewertungserweiterung kennen.
feature: App Builder, Cloud
role: Developer
level: Intermediate
hide: true
hidefromtoc: true
source-git-commit: 4ca909c2f8f95fbc404ce6a745d769958b2c01f4
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Voraussetzungen für das Tutorial zur Bewertungserweiterung (Beta)

>[!NOTE]
>
>Die in diesem Tutorial verwendeten KI-Tools befinden sich derzeit in Beta und können Fehler oder andere Probleme umfassen.

Auf dieser Seite werden die Voraussetzungen und Einrichtungsschritte für [!DNL Adobe Commerce as a Cloud Service] Tutorials aufgelistet, z. B. das [Erweiterungs-Tutorial für Bewertungen](./ratings-extension.md).

## Voraussetzungen für Adobe Commerce as a Cloud Service

* Installieren des [!DNL Adobe I/O CLI]

  ```bash
  npm install -g @adobe/aio-cli
  ```

* Installieren Sie die Plug-ins [Adobe I/O CLI Commerce](https://github.com/adobe-commerce/aio-cli-plugin-commerce), [Adobe I/O CLI Runtime](https://github.com/adobe/aio-cli-plugin-runtime) und [App Builder CLI](https://github.com/adobe/aio-cli-plugin-app-dev):

  ```bash
  aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce @adobe/aio-cli-plugin-app-dev @adobe/aio-cli-plugin-runtime
  ```

* Herunterladen einer KI-unterstützten IDE wie [Cursor](https://cursor.com/download) (empfohlen), andere IDEs wie Claude Code, Gemini CLI oder Copilot werden ebenfalls unterstützt, könnten jedoch Änderungen an den Eingabeaufforderungen und anderen Schritten im Tutorial erfordern.

### Voraussetzungen für Adobe Developer Console

1. Navigieren Sie zur [Adobe Developer Console](https://developer.adobe.com/console){target="_blank"}.
1. Melden Sie sich mit Ihrer E-Mail-Adresse und Ihrem Passwort an.

#### Neues Projekt erstellen

1. Navigieren Sie zu [Adobe Developer Console](https://developer.adobe.com/).
1. Klicken Sie [!UICONTROL **Projekt aus einer Vorlage erstellen**].
1. Wählen Sie die Vorlage [!UICONTROL **App Builder**] aus.
1. Geben Sie einen [!UICONTROL **Projekttitel**] und [!UICONTROL **App-Namen**] ein.
1. Stellen Sie sicher, dass das Kontrollkästchen **[!UICONTROL Include Runtime]** markiert ist.

   ![Adobe Developer Console-Projekterstellung mit ausgewählter App Builder-Vorlage](../assets/app-builder-template.png){width="600" zoomable="yes"}

1. Klicken Sie [!UICONTROL **Speichern**].

#### Hinzufügen von APIs zum Arbeitsbereich

1. Klicken Sie auf [!UICONTROL **Staging**]-Arbeitsbereich und wiederholen Sie dann die folgenden Schritte für jede API.

   ![Staging-Arbeitsbereich mit Option „Service hinzufügen“ für APIs](../assets/add-apis-workspace.png){width="600" zoomable="yes"}

1. Klicken Sie auf [!UICONTROL **Service hinzufügen**] und wählen Sie [!UICONTROL **API**] aus.

1. Wählen Sie eine der folgenden APIs aus. Sie müssen diesen Vorgang für jede der unten aufgeführten APIs wiederholen:

   * [!UICONTROL **Adobe Services**]-Filter:
      * [!UICONTROL **I/O-Management-API**]
      * [!UICONTROL **I/O Events**] API
   * [!UICONTROL **Experience Cloud**]-Filter:
      * [!UICONTROL **Adobe I/O Events für Adobe Commerce**]-API

1. Klicken Sie [!UICONTROL **Weiter**].

1. Klicken Sie [!UICONTROL **Konfigurierte API speichern**].

1. Wiederholen Sie die vorherigen Schritte, bis alle APIs zum Arbeitsbereich hinzugefügt wurden.

   ![Workspace mit allen erfolgreich hinzugefügten erforderlichen APIs](../assets/apis-added.png){width="600" zoomable="yes"}

### Konfigurieren der Adobe I/O-CLI

1. Löschen Sie eine vorhandene Konfiguration:

   ```bash
   aio config clear
   ```

   Melden Sie sich mit dem [!DNL Adobe I/O CLI] an:

   ```bash
   aio auth login -f
   ```

1. Wählen Sie Ihre Organisation, Ihr Projekt und Ihren Arbeitsbereich mithilfe der folgenden Befehle aus:

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

### Klonen des Integrations-Starter-Kits

Klonen Sie das Starter Kit-Repository der Commerce-Integration und bereiten Sie Ihr Projekt vor:

```bash
git clone https://github.com/adobe/commerce-integration-starter-kit.git extension
cd extension
```

![Terminal-Ausgabe mit dem Git-Klonbefehl für das Commerce Integration Starter Kit](../assets/clone-starter-kit.png){width="600" zoomable="yes"}

### Erstellen einer .env-Datei

Erstellen Sie die Konfigurationsdatei Ihrer Umgebung:

```bash
cp env.dist .env
```

Öffnen Sie die `.env` in einem Texteditor und fügen Sie die folgenden OAuth-Anmeldeinformationen hinzu:

```shell-session
OAUTH_CLIENT_ID=
OAUTH_CLIENT_SECRET=
OAUTH_TECHNICAL_ACCOUNT_ID=
OAUTH_TECHNICAL_ACCOUNT_EMAIL=
OAUTH_ORG_ID=
```

Sie können diese Werte von der **[!UICONTROL Credential details]** in [Developer Console kopieren](https://developer.adobe.com/) indem Sie auf die Registerkarte **[!UICONTROL OAuth Server-to-Server]** in Ihrem Arbeitsbereich klicken.

![Seite mit OAuth Server-zu-Server-Anmeldeinformationen in Adobe Developer Console](../assets/oauth-credentials.png){width="600" zoomable="yes"}

#### Hinzufügen der Commerce-Konfiguration

Fügen Sie die folgenden Commerce-Instanzdetails zu Ihrer `.env` hinzu:

```shell-session
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

```shell-session
EVENT_PREFIX=test
```

### Workspace-Konfiguration herunterladen

Führen Sie den folgenden Befehl aus, um die Workspace-Konfigurationsdatei herunterzuladen:

```bash
aio console workspace download workspace.json
```

Kopieren Sie die Workspace-Konfigurationsdatei in das `scripts`:

```bash
cp workspace.json scripts/
```

### Lokalen Arbeitsbereich mit Remote-Arbeitsbereich verbinden

Verknüpfen des lokalen Projekts mit dem Remote-Arbeitsbereich:

```bash
aio app use workspace.json -m
```

![Terminal, das eine erfolgreiche Arbeitsbereich-Verbindung mit dem AIO-Programm-Anwendungsbefehl anzeigt](../assets/connect-workspace.png){width="600" zoomable="yes"}

### Installieren von Erweiterbarkeits-KI-Tools

Aktualisieren Sie die Cursor-Regeldatei und die MCP-Konfiguration so, dass sie das `commerce-extensibility-tools`-Paket enthalten.

1. Richten Sie die KI-unterstützten Entwicklungstools mithilfe der folgenden Befehle im Ordner &quot;`extension`&quot; ein:

   ```bash
   cd extension
   ```

   ```bash
   aio commerce extensibility tools-setup
   ```

   ![Terminal mit der Befehlsausgabe für die Einrichtung von KI-Erweiterbarkeitstools](../assets/install-ai-tools.png){width="600" zoomable="yes"}
<!--
## Storefront prerequisites

The following items are required to complete the [storefront](./ratings-extension.md#connect-to-the-storefront) section of [this tutorial](./ratings-extension.md) and see the product ratings in your store.

* Install [!DNL Node.js] (version `22.x.x`) and npm (`9.0.0` or higher). Verify your installation:

   ```bash
   node --version
   npm --version
   ```

* Install [Git](https://git-scm.com) (Optional) - Required only if [cloning the repository directly](#option-a-clone-the-repository-recommended)(recommended), not needed if you [download the zip file](#option-b-download-the-zip-file). Verify your installation:

  ```bash
  git --version
  ```

* Bash shell
  * macOS/Linux: No installation required
  * Windows: Use [Git Bash](https://git-scm.com/install) or [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install)

* [Google Chrome](https://www.google.com/chrome/) - Required for testing the storefront

### Get the project files

You can obtain the project files using one of the following methods:

#### Option A: Clone the repository (recommended)

If you have [!DNL Git] installed, open your terminal and clone the repository:

```bash
git clone --branch agentic-dev https://github.com/hlxsites/aem-boilerplate-commerce.git storefront
cd storefront
```

#### Option B: Download the zip file

If you do not have [!DNL Git] installed:

1. Download the project zip file from: [https://github.com/hlxsites/aem-boilerplate-commerce/archive/refs/heads/agentic-dev.zip](https://github.com/hlxsites/aem-boilerplate-commerce/archive/refs/heads/agentic-dev.zip)
1. Extract the zip file to a folder on your machine.
1. Open your terminal and navigate into the unzipped folder:

   ```bash
   cd path/to/aem-boilerplate-commerce-agentic-dev
   ```

### Install root dependencies

Install the main project dependencies:

```bash
npm install
```

This will install all the necessary packages for the storefront application.

### Install MCP server dependencies

Navigate to the MCP server directory and install its dependencies:

```bash
cd mcp-server
npm install
cd ..
```

### Configure environment variables

The MCP server requires certain environment variables to connect to the RAG service.

Create an `.env` file in the `mcp-server` directory:

```bash
cd mcp-server
cp env.example .env
```

Edit the `.env` file and add the following values:

```env
RAG_MODE=worker
WORKER_RAG_URL=
```

### Enable MCP in Cursor

The Model Context Protocol (MCP) server provides AI agents with access to [!DNL Adobe Commerce] Storefront documentation.

#### Open Cursor MCP settings

![Open Cursor MCP Settings](../assets/cursor-mcp-settings.png){width="600" zoomable="yes"}

1. Open [!DNL Cursor].
1. Navigate to **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]**.

#### Enable and configure MCP features

The project includes an MCP configuration file at `.cursor/mcp.json`. This file should already be configured to use the local MCP server.

Verify the MCP configuration:

1. Ensure the "commerce-documentation-rag" server is listed and enabled

The configuration should look similar to this:

![MCP Configuration](../assets/mcp-configuration.png){width="600" zoomable="yes"}

>[!NOTE]
>
>The `start-mcp.sh` script will automatically load the environment variables from your `.env` file in the `mcp-server` directory.

#### Restart Cursor

After enabling MCP and configuring the server:

1. Quit [!DNL Cursor] completely.
1. Reopen [!DNL Cursor] and open the `aem-boilerplate-commerce` project.

#### Verify MCP connection

Check that the MCP server is running correctly:

1. Open a new chat in [!DNL Cursor].
1. Look for an indicator showing the MCP server is connected. This indicator is typically located in the chat interface.
1. Try entering a prompt like the following:

   ```shell-session
   Search the storefront docs for information about slots
   ```

If the MCP server is working, you should see relevant documentation results.

![MCP Connection Verified](../assets/mcp-connection-verified.png){width="600" zoomable="yes"}

If this works, you are ready to continue with the [tutorial](./ratings-extension.md).
 -->
