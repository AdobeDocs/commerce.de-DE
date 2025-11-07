---
title: Voraussetzungen für ADL Commerce Lab
description: Lernen Sie die Voraussetzungen für das Labor der Bewertungserweiterung kennen.
role: Developer
hide: true
hidefromtoc: true
source-git-commit: ba4d096bcb99420c029d0b0674fc00f1f1445cea
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Adobe Developers Live - Voraussetzungen für Adobe Commerce Lab

Auf dieser Seite werden die Voraussetzungen und andere manuelle Einrichtungsschritte für das ([-Erweiterungslabor) &#x200B;](./workbook.md). Das Labor enthält auch ein Skript, das die meisten dieser Schritte automatisiert.

## Voraussetzungen für Erweiterungen

Bevor Sie beginnen, müssen Sie die folgenden Voraussetzungen erfüllen:

* Installieren des [!DNL Adobe I/O CLI]

  ```bash
  npm install -g @adobe/aio-cli
  ```

* Installieren des Commerce-Plug-ins

  ```bash
  aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce
  ```

* Herunterladen einer KI-unterstützten IDE wie [Cursor](https://cursor.com/download) (empfohlen), andere IDEs wie Claude Code, Gemini CLI oder Copilot werden ebenfalls unterstützt, könnten jedoch Änderungen an den Eingabeaufforderungen und anderen Schritten in diesem Tutorial erfordern.
<!-- 
### Create a new project on Adobe Developer Console

1. Navigate to [Adobe Developer Console](https://developer.adobe.com/).
1. Click [!UICONTROL **Create project from a template**].
1. Select the [!UICONTROL **App Builder**] template.
1. Enter a [!UICONTROL **Project Title**] and [!UICONTROL **App Name**].
1. Ensure the **[!UICONTROL Include Runtime]** checkbox is marked.

   ![Create project with App Builder template](./assets/app-builder-template.png){width="600" zoomable="yes"}

1. Click **Save**.

### Add APIs to the workspace

1. Click the [!UICONTROL **Stage**] workspace and then repeat the following steps for each API.

   ![APIs added to workspace](./assets/add-apis-workspace.png){width="600" zoomable="yes"}

1. Click [!UICONTROL **Add Service**] and select [!UICONTROL **API**].

1. Select the [!UICONTROL **Adobe Services**] filter and select one of the following APIs:

   * [!UICONTROL **I/O Management API**]
   * [!UICONTROL **I/O Events**]

1. Select the [!UICONTROL **Experience Cloud**] filter and select one of the following APIs:

   * [!UICONTROL **Adobe I/O Events for Adobe Commerce**]

1. Click [!UICONTROL **Next**].

1. Click[!UICONTROL **Save configured API**].

1. Repeat the previous steps until all APIs are added to the workspace.

   ![APIs added to workspace](./assets/apis-added.png){width="600" zoomable="yes"} -->

### Konfigurieren der AIO-CLI

1. Löschen Sie die vorhandene Konfiguration:

   ```bash
   aio config clear
   ```

   Melden Sie sich über die AIO-CLI an:

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

   ![CLI-Konfiguration](./assets/cli-configuration.png){width="600" zoomable="yes"}

### Clone-Integrations-Starter-Kit

Klonen Sie das Starter Kit-Repository der Commerce-Integration und bereiten Sie Ihr Projekt vor:

```bash
git clone --branch adl https://github.com/adobe/commerce-integration-starter-kit.git extension
cd extension
```

![Klonen des Starter-Kits](./assets/clone-starter-kit.png){width="600" zoomable="yes"}

### Erstellen der .env-Datei

Erstellen Sie die Konfigurationsdatei Ihrer Umgebung:

```bash
cp env.dist .env
```

<!-- Open the `.env` file in a text editor and add the following OAuth credentials:

```text
OAUTH_CLIENT_ID=
OAUTH_CLIENT_SECRET=
OAUTH_TECHNICAL_ACCOUNT_ID=
OAUTH_TECHNICAL_ACCOUNT_EMAIL=
OAUTH_ORG_ID=
```

You can copy these values from the **[!UICONTROL Credential details]** page in [Developer Console](https://developer.adobe.com/) by clicking the **[!UICONTROL OAuth Server-to-Server]** tab on your workspace.

![OAuth credentials](./assets/oauth-credentials.png){width="600" zoomable="yes"}

#### Add the Commerce configuration

Add the following Commerce instance details to your `.env` file:

```text
COMMERCE_BASE_URL=
COMMERCE_GRAPHQL_ENDPOINT=
```

To find these values:

1. Go to [Commerce Cloud Service instances](https://experience.adobe.com/#/@commerce/commerce/cloud-service/instances).
1. Click the information icon next to your assigned seat.
1. Copy the REST endpoint as `COMMERCE_BASE_URL`.
1. Copy the GraphQL Endpoint as `COMMERCE_GRAPHQL_ENDPOINT`.

#### Set event prefix

Set a temporary value for the event prefix:

```text
EVENT_PREFIX=test
```
 -->

### Workspace-Konfiguration herunterladen

Führen Sie den folgenden Befehl aus, um die Workspace-Konfigurationsdatei herunterzuladen:

```bash
aio console workspace download workspace.json
```

### Lokalen Arbeitsbereich mit Remote-Arbeitsbereich verbinden

Verknüpfen des lokalen Projekts mit dem Remote-Arbeitsbereich:

```bash
aio app use workspace.json -m
```

![Verbindung zu Workspace herstellen](./assets/connect-workspace.png){width="600" zoomable="yes"}

## Voraussetzungen für die Storefront

Die folgenden Elemente sind erforderlich, um den Abschnitt [Storefront](#connect-to-the-storefront) dieses Tutorials abzuschließen und die Produktbewertungen in Ihrem Store anzuzeigen.
<!-- 
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
  * Windows: Use [Git Bash](https://git-scm.com/install) or [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install).

* [Google Chrome](https://www.google.com/chrome/) - Required for testing the storefront -->

### Abrufen der Projektdateien

Sie haben zwei Möglichkeiten, um die Projektdateien abzurufen:

<!-- 
#### Option A: Clone the repository (recommended) -->

Wenn Sie [!DNL Git] installiert haben, öffnen Sie Ihr Terminal und klonen Sie das Repository:

```bash
git clone --branch agentic-dev https://github.com/hlxsites/aem-boilerplate-commerce.git storefront
cd storefront
```

<!-- #### Option B: Download the zip file

If you don't have [!DNL Git] installed:

1. Download the project zip file from: [https://github.com/hlxsites/aem-boilerplate-commerce/archive/refs/heads/agentic-dev.zip](https://github.com/hlxsites/aem-boilerplate-commerce/archive/refs/heads/agentic-dev.zip)
1. Extract the zip file to a folder on your machine.
1. Open your terminal and navigate into the unzipped folder:

   ```bash
   cd path/to/aem-boilerplate-commerce-agentic-dev
   ``` -->

### Installieren von Stammabhängigkeiten

Installieren Sie die wichtigsten Projektabhängigkeiten:

```bash
npm install
```

Dadurch werden alle erforderlichen Pakete für die Storefront-Anwendung installiert.

### MCP-Server-Abhängigkeiten installieren

Navigieren Sie zum MCP-Server-Verzeichnis und installieren Sie dessen Abhängigkeiten:

```bash
cd mcp-server
npm install
cd ..
```

<!-- ### Configure environment variables

The MCP server requires certain environment variables to connect to the RAG service.

Create a `.env` file in the `mcp-server` directory:

```bash
cd mcp-server
cp env.example .env
```

Edit the `.env` file and add the following values (we'll provide the actual URL during the lab):

```env
RAG_MODE=worker
WORKER_RAG_URL=<provided-during-lab>
```

>[!NOTE]
>
>The actual value for `WORKER_RAG_URL` will be provided by the lab facilitator at the start of the session. -->

### MCP im Cursor aktivieren

Der MCP-Server (Model Context Protocol) bietet KI-Agenten Zugriff auf [!DNL Adobe Commerce] Storefront-Dokumentation.

#### Cursor-MCP-Einstellungen öffnen

![Öffnen der Cursor-MCP-Einstellungen](./assets/cursor-mcp-settings.png){width="600" zoomable="yes"}

1. [!DNL Cursor] öffnen
1. Navigieren Sie zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]**

#### Aktivieren und Konfigurieren von MCP-Funktionen

Das Projekt enthält eine MCP-Konfigurationsdatei unter `.cursor/mcp.json`. Diese Datei sollte bereits für die Verwendung des lokalen MCP-Servers konfiguriert sein.

Überprüfen Sie die MCP-Konfiguration:

1. Stellen Sie sicher, dass der Server „commerce-documentation-rag“ aufgeführt und aktiviert ist.

Die Konfiguration sollte in etwa wie folgt aussehen:

![MCP-Konfiguration](./assets/mcp-configuration.png){width="600" zoomable="yes"}

>[!NOTE]
>
>Das `start-mcp.sh`-Skript lädt automatisch die Umgebungsvariablen aus Ihrer `.env`-Datei in das `mcp-server`.

#### Cursor neu starten

Nach der Aktivierung von MCP und der Konfiguration des Servers:

1. [!DNL Cursor] vollständig beenden
1. [!DNL Cursor] erneut öffnen und das `aem-boilerplate-commerce` Projekt öffnen

#### MCP-Verbindung überprüfen

Überprüfen Sie, ob der MCP-Server ordnungsgemäß ausgeführt wird:

1. Einen neuen Chat in [!DNL Cursor] öffnen
1. Suchen Sie nach einem Indikator, der anzeigt, dass der MCP-Server verbunden ist (normalerweise in der Chat-Oberfläche)
1. Stellen Sie eine Frage wie: „Durchsuchen Sie die Dokumente der Storefront nach Informationen über Slots“.

Wenn der MCP-Server funktioniert, sollten die entsprechenden Dokumentationsergebnisse angezeigt werden.

![MCP-Verbindung überprüft](./assets/mcp-connection-verified.png){width="600" zoomable="yes"}

### Starten des Entwicklungs-Servers

Starten Sie den lokalen Entwicklungs-Server:

```bash
npm run start
```

Der Entwicklungs-Server beginnt um `http://localhost:3000`.

Navigieren Sie zur Bekleidungsseite unter `http://localhost:3000/apparel`.

![Entwicklungs-Server wird ausgeführt](./assets/development-server-running.png){width="600" zoomable="yes"}
