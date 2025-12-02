---
title: KI-Kodierungstools für Erweiterungen
description: Erfahren Sie, wie Sie die KI-Tools zum Erstellen von Commerce App Builder-Erweiterungen verwenden.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Developer
hide: true
hidefromtoc: true
source-git-commit: b62dafbf381eb11501c901d6e8d6ad3da972a307
workflow-type: tm+mt
source-wordcount: '1838'
ht-degree: 0%

---

# KI-Kodierungstools für Erweiterungen

Bei der Migration zu [!DNL Adobe Commerce as a Cloud Service] können Sie die KI-Kodierungstools verwenden, um vorhandene [!DNL Adobe Commerce] PHP-Erweiterungen in [!DNL Adobe Developer App Builder]-Erweiterungen zu konvertieren. Sie kann auch verwendet werden, um neue [!DNL App Builder] zu erstellen.

Die Verwendung der KI-Kodierungs-Tools bietet die folgenden Vorteile:

* **Verbesserter Entwicklungs-Workflow**: Integrierte Adobe Commerce-Entwicklungs-Tools.
* **KI-gestützte Hilfe**: Kontextabhängige Code-Generierung und -Debugging.
* **Commerce-spezifische Funktionen**: Spezialisierte Tools für die Entwicklung von Adobe Commerce App Builder.
* **Automatisierte Workflows**: Optimierte Entwicklungs- und Bereitstellungsprozesse.

## Voraussetzungen

* Einer der folgenden Codierer:
   * [Cursor](https://cursor.com/download)&#x200B;(empfohlen)
   * [GitHub-Copilot](https://github.com/features/copilot)
   * [Google Gemini CLI](https://github.com/google-gemini/gemini-cli)
   * [Claude Code](https://www.claude.com/product/claude-code)
* [Node.](https://nodejs.org/en/download): LTS-Version
* Package Manager: [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) oder [arn](https://classic.yarnpkg.com/lang/en/docs/install/#mac-stable)
* [Git](https://github.com/git-guides/install-git): Für das Klonen von Repositorys und die Versionskontrolle

## Installation

1. Installieren Sie die neueste [Adobe I/O CLI](https://github.com/adobe/aio-cli) global:

   ```bash
   npm install -g @adobe/aio-cli
   ```

1. Installieren Sie das [Adobe I/O CLI Commerce-Plug-in](https://github.com/adobe-commerce/aio-cli-plugin-commerce):

   ```bash
   aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce
   ```

1. Klonen Sie das Commerce [Integrations-Starter-Kit](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/create-integration):

   ```bash
   git clone git@github.com:adobe/commerce-integration-starter-kit.git
   ```

1. Navigieren Sie zum Verzeichnis Starter Kit :

   ```bash
   cd commerce-integration-starter-kit
   ```

1. Installieren Sie die Commerce AI-Erweiterbarkeits-Tools, indem Sie den interaktiven Einrichtungsbefehl ausführen:

   ```bash
   aio commerce extensibility tools-setup
   ```

Der Einrichtungsprozess fragt Sie nach den Konfigurationsoptionen. Wählen Sie als Setup-Speicherort „Aktuelles Verzeichnis“, um die Tools in Ihrem aktuellen Arbeitsbereich zu installieren:

```terminal
? Where would you like to setup the tools?
❯ Current directory
  New directory
```

Bei der Auswahl des Codierungs-Agenten empfiehlt Adobe die Auswahl von `Cursor` für ein optimales Entwicklungserlebnis:

```terminal
? Which coding agent would you like to use?
❯ Cursor
  Copilot
  Gemini CLI
  Claude Code
```

Bei der Auswahl des Package Managers empfiehlt Adobe aus Konsistenzgründen die Verwendung von `npm`:

```terminal
? Which package manager would you like to use?
❯ npm
  yarn
```

1. Nach erfolgreicher Installation der Kodierungstools wird während des Installationsprozesses Folgendes konfiguriert:

   * MCP-Serverintegration für die Adobe Commerce-Entwicklung
   * Cursor-IDE-Regeln für ein verbessertes Entwicklungserlebnis
   * Commerce-spezifische Entwicklungstools und -Workflows

   Die folgenden Dateien werden Ihrem Arbeitsbereich hinzugefügt:

   **Cursor**

   * MCP-Konfiguration: `.cursor/mcp.json`
   * Regelverzeichnis: `.cursor/rules/`

   **Kopilot**

   * MCP-Konfiguration: `.vscode/mcp.json`
   * Regelverzeichnis: `.github/copilot-instructions.md`

>[!NOTE]
>
>Vor der Bereitstellung des Projekts müssen Sie die folgenden Konfigurationsaufgaben durchführen:
>
>* Melden Sie sich über die Adobe I/O-CLI [&#x200B; &#x200B;](https://developer.adobe.com/console)Adobe Developer Console an.
>* Erstellen Sie ein App Builder-Projekt (siehe [Projekt-Setup](https://developer.adobe.com/commerce/extensibility/events/project-setup)).
>* Einrichten von Umgebungsvariablen in einer `.env`.
>
>Sie können diese Konfigurationsschritte manuell durchführen oder die KI-Kodierungs-Tools nutzen, um Sie durch den Prozess zu führen. Siehe [Erstellen einer Integration](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/create-integration/) für detaillierte Konfigurationsanweisungen.

## Konfiguration nach der Installation

### Beim [!DNL Adobe I/O CLI] anmelden

Nach der Installation des [!DNL Adobe I/O CLI] müssen Sie sich jederzeit anmelden, wenn Sie den MCP-Server verwenden möchten.

```bash
aio auth login
```

Um sicherzustellen, dass Sie angemeldet sind, führen Sie den folgenden Befehl aus:

```bash
aio where
```

Wenn Probleme auftreten, versuchen Sie, sich abzumelden und wieder anzumelden:

```bash
aio auth logout
aio auth login
```

>[!NOTE]
>
>Einige Funktionen des MCP-Servers funktionieren ohne Anmeldung, aber der RAG-Service (Retrieval-Augmented Generation) funktioniert nicht. Der RAG-Service bietet dem KI-Codierungs-Agenten Echtzeitzugriff auf den vollständigen Adobe Commerce-Dokumentationssatz, sodass er Fragen beantworten und Code basierend auf aktuellen Commerce-Entwicklungspraktiken, APIs und Architekturmustern generieren kann.
>
>In einer zukünftigen Version wird der RAG-Service unabhängig zugänglich sein, ohne dass andere Tools installiert werden müssen.

### Cursor

1. Starten Sie die Cursor-IDE neu, um die neuen MCP-Tools und die neue Konfiguration zu laden.

1. Überprüfen Sie die Installation, indem Sie bestätigen, dass die Regeln im Ordner `.cursor/rules/` vorhanden sind.

1. MCP-Server aktivieren:

   * Öffnen Sie die Cursor-MCP-Einstellungen mit **Befehlstaste+Umschalt+P** (macOS) oder **Strg+Umschalt+P** (Windows und Linux).
   * Typ **Ansicht: MCP-Einstellungen öffnen**
   * Suchen Sie **Commerce-Extensibility MCP Server** in der Liste.
   * Schalten Sie den Server **EIN** um, um die Kodierungstools zu aktivieren

1. Überprüfen Sie den Serverstatus. Der Commerce Extensibility MCP-Server sollte wie folgt aussehen:

   ```terminal
   Status: Connected/Active
   Server: commerce-extensibility
   Configuration: Automatically configured via .cursor/mcp.json
   ```

1. Verwenden Sie die folgende Eingabeaufforderung, um zu sehen, ob der Agent den MCP-Server verwendet. Ist dies nicht der Fall, bitten Sie den Agenten ausdrücklich, die verfügbaren MCP-Tools zu verwenden.

```terminal
What are the differences between Adobe Commerce PaaS and Adobe Commerce as a Cloud Service when configuring a webhook that activates an App Builder runtime action?
```

### Kopilot

1. Starten Sie Visual Studio Code neu, um die neuen MCP-Tools und -Konfigurationen zu laden.

1. Überprüfen Sie die Installation, indem Sie bestätigen, dass die `copilot-instructions.md` Datei im `.github` vorhanden ist.

1. MCP-Server aktivieren:

   * Öffnen Sie den Bereich „Erweiterungen“, indem Sie auf **Erweiterungen** in der Aktivitätsleiste auf der linken Seitenleiste klicken oder **Befehlstaste+Umschalt+X** (macOS) oder **Strg+Umschalt+X** (Windows und Linux) verwenden.
   * Klicken Sie **MCP SERVERS - INSTALLED**.
   * Klicken Sie auf das Zahnradsymbol neben **Commerce-Extensibility MCP Server** und wählen Sie **Server starten**, wenn der Server angehalten wird.
   * Klicken Sie erneut auf das Zahnradsymbol und wählen Sie **Ausgabe anzeigen**.

1. Überprüfen Sie den Serverstatus. Die `MCP:commerce-extensibility` sollte wie folgt aussehen:

   ```terminal
   2025-11-13 12:58:50.652 [info] Starting server commerce-extensibility
   2025-11-13 12:58:50.652 [info] Connection state: Starting
   2025-11-13 12:58:50.652 [info] Starting server from LocalProcess extension host
   2025-11-13 12:58:50.657 [info] Connection state: Starting
   2025-11-13 12:58:50.657 [info] Connection state: Running
   
   (...)
   
   2025-11-13 12:58:50.753 [info] Discovered 10 tools
   ```

1. Verwenden Sie die folgende Eingabeaufforderung, um zu sehen, ob der Agent den MCP-Server verwendet. Ist dies nicht der Fall, bitten Sie den Agenten ausdrücklich, die verfügbaren MCP-Tools zu verwenden.

   ```terminal
   What are the differences between Adobe Commerce PaaS and SaaS when configuring a webhook that activates an App Builder runtime action?
   ```

## Eingabeaufforderung für Muster

Die folgende Beispiel-Eingabeaufforderung erstellt eine Erweiterung, um Benachrichtigungen zu senden, wenn eine Bestellung aufgegeben wird.

```terminal
Implement an Adobe Commerce SaaS extension that will send an ERP notification when a customer places an order. The ERP notification must be sent as a POST HTTP call to <ERP URL> with the following details in the request JSON body:

Order ID -> orderID
Order Total -> total
Customer Email ID -> emailID
Payment Type -> pType
```

## Eingabeaufforderungsbefehle

Zusätzlich zur Eingabeaufforderung können Sie den `/search-commerce-docs`-Befehl verwenden, um die Dokumentation in Konversationen mit Ihrem Agenten zu durchsuchen. Beispiel:

```text
/search-commerce-docs "How do I subscribe to Commerce events?"
```

## Best Practices

Adobe empfiehlt bei der Verwendung der KI-Kodierungs-Tools die folgenden Best Practices:

### Checkliste

Bevor Sie eine Entwicklungssitzung starten:

* Auf `REQUIREMENTS.md` prüfen
* Überprüfen, ob die MCP-Tools funktionieren
* Aktuelle Phase und Ziele überprüfen
* Beginnen Sie mit Beispiel-Code oder strukturierten Projekten

Während der Entwicklung:

* Vertrauen Sie dem Vier-Phasen[Protokoll](#protocol)
* Anfordern von Implementierungsplänen für die komplexe Entwicklung
* MCP-Tools verwenden, sofern verfügbar
* Testen der einzelnen Funktionen nach der Implementierung
* Zuerst lokal testen, dann bereitstellen und erneut testen
* Nutzen der Kodierungstools für die Testunterstützung
* Unnötige Komplexität hinterfragen
* Inkrementelle Bereitstellung für schnellere Entwicklung

Beim Starten eines neuen Chats:

* Sicherstellen einer ordnungsgemäßen Sitzungsübergabe
* Referenzschlüssel-Dateien mit `@`
* Legen Sie klare Ziele für die Sitzung fest
* Verwenden von phasenbasierten Grenzen

### Workflow

Beginnen Sie bei der Entwicklung mit den KI-Kodierungs-Tools mit Beispiel-Code oder Strukturvorlagen-Projekten. Dieser Ansatz stellt sicher, dass Sie auf einer soliden Grundlage aufbauen, anstatt aus dem Nichts zu beginnen, und optimiert gleichzeitig Ihren KI-Entwicklungs-Workflow.

Auf diese Weise können Sie auch die Vorlagen von Adobe nutzen und auf bewährten Mustern und Architekturen aufbauen, während Sie etablierte Verzeichnisstrukturen und Konventionen beibehalten.

Lesen Sie die folgenden Ressourcen, um loszulegen:

* [Integrations-Starter-Kit](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/create-integration)
* [Adobe Commerce Starter Kit-Vorlagen](https://github.com/adobe/adobe-commerce-samples/tree/main/starter-kit)
* [Adobe I/O Events Starter-Vorlagen](https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/adobe-developer-app-builder/io-events/getting-started-io-events)
* [Beispielanwendungen für App Builder](https://developer.adobe.com/app-builder/docs/resources/sample_apps)

#### Warum Sie diese Ressourcen verwenden sollten

* **Bewährte Muster**: Starter Kits enthalten Best Practices und architektonische Entscheidungen von Adobe
* **Schnellere Entwicklung**: Reduziert den Zeitaufwand für Textbaustein und Konfiguration
* **Konsistenz**: Stellt sicher, dass Ihre Erweiterung den etablierten Konventionen entspricht
* **Wartbarkeit**: Einfachere Pflege und Aktualisierung bei der Einhaltung von Standardmustern
* **Dokumentation**: Starter Kits enthalten Beispiele und Dokumentation
* **Community-Support**: Einfachere Hilfe bei der Verwendung von Standardansätzen
* **KI-Kontexteffizienz**: Verwenden Sie vertraute Muster und Strukturen, um mit ihnen zu arbeiten, und reduzieren Sie so den Bedarf an umfangreichen Erläuterungen. Außerdem wird die Genauigkeit der Code-Generierung verbessert
* **Reduzierte Token-Nutzung**: Verweisen Sie auf vorhandene Muster, anstatt alles von Grund auf neu zu generieren, was zu effizienteren Konversationen und weniger Kontextzusammenfassungen führt

### Protokoll

Das folgende Vierphasenprotokoll wird automatisch vom Regelsystem durchgesetzt. Die Tools sollten dieses Protokoll beim Entwickeln von Erweiterungen automatisch befolgen:

* Phase 1: Anforderungsanalyse und -klärung
   * Wenn Sie Fragen zur Klärung stellen, geben Sie vollständige Antworten.
* Phase 2: Architektonische Planung und Anwendergenehmigung
   * Wenn ein Plan vorgelegt wird, prüfen Sie ihn sorgfältig, bevor Sie ihn genehmigen.
* Phase 3: Code-Erstellung und -Implementierung
* Phase 4: Dokumentation und Validierung

### Anfordern von Implementierungsplänen für die komplexe Entwicklung

Für komplexe Entwicklungen mit mehreren Laufzeitaktionen, Touchpoints oder Integrationen fordern Sie ausdrücklich an, dass die KI-Tools einen detaillierten Implementierungsplan erstellen. Wenn Sie in Phase 2 einen Plan [&#x200B; hoher Ebene sehen](#protocol) der mehrere Komponenten umfasst, fragen Sie nach einem detaillierten Implementierungsplan, um ihn in überschaubare Aufgaben aufzuteilen:

```terminal
Create a detailed implementation plan for this complex development.
```

Komplexe Adobe Commerce-Erweiterungen umfassen häufig Folgendes:

* Mehrere Laufzeitaktionen
* Ereigniskonfiguration über mehrere Touchpoints hinweg
* Integration mit externen Systemen
* Anforderungen an die Statusverwaltung
* Testen über mehrere Komponenten hinweg

### MCP-Tools verwenden

>[!NOTE]
>
>Stellen Sie vor der Verwendung der MCP-Tools [, dass Sie bei der Adobe I/O CLI angemeldet &#x200B;](#log-in-to-the-adobe-io-cli).

Das Tool ist standardmäßig auf MCP-Tools eingestellt, kann jedoch unter bestimmten Umständen stattdessen CLI-Befehle verwenden. Wenn Sie die Verwendung des MCP-Tools sicherstellen möchten, fordern Sie diese in Ihrer Eingabeaufforderung explizit an.

Wenn CLI-Befehle verwendet werden und Sie stattdessen MCP-Tools verwenden möchten, verwenden Sie die folgende Eingabeaufforderung:

```terminal
Use only MCP tools and not CLI commands
```

* MCP-Tools: aio-app-deploy, aio-app-dev, aio-dev-invoke
* CLI-Befehle: aio app deploy, aio app dev

CLI-Befehle können für die folgenden Szenarien verwendet werden:

* Komplexe Bereitstellungsszenarien
* Debugging bei bestimmten Problemen
* Wenn MCP-Tools Einschränkungen aufweisen
* Einmalige Vorgänge, die nicht von der MCP-Integration profitieren

### Entwicklung

Es ist wichtig, unnötige Komplexität zu hinterfragen, die durch die KI-Tools verursacht wird.

Wenn unnötige Dateien (`validator.js`, `transformer.js`, `sender.js`) für einfache schreibgeschützte Endpunkte hinzugefügt werden, verwenden Sie die folgenden Eingabeaufforderungen:

```terminal
Why do we need these files for a simple read-only endpoint?
Perform a root cause analysis before adding complexity
Verify if simpler solutions exist
```

### Test läuft

Verwenden Sie beim Testen die folgenden Best Practices:

#### Testen der einzelnen Funktionen nach der Implementierung

Nach Abschluss der Entwicklung einer Funktion im Implementierungsplan sollten Sie diese sofort testen. Frühzeitige Tests verhindern zusammengesetzte Probleme und erleichtern das Debugging.

* Nicht warten, bis alle Funktionen abgeschlossen sind
* Inkrementelles Testen zur frühzeitigen Erkennung von Problemen
* Validieren der Funktionalität vor dem Übergang zur nächsten Funktion

#### Erst lokal testen

Testen Sie immer zuerst lokal mit dem `aio-app-dev`. Dies bietet sofortiges Feedback und ermöglicht schnellere Iterationszyklen, einfacheres Debugging und keinen Bereitstellungsaufwand.

1. Starten Sie den lokalen Entwicklungs-Server:

   ```bash
   aio-app-dev
   ```

1. Aktionen lokal testen:

   ```bash
   aio-dev-invoke action-name --parameters '{"test": "data"}'
   ```

#### Erneutes Bereitstellen und Testen

Sobald die lokalen Tests erfolgreich waren, können Sie sie in der Laufzeitumgebung bereitstellen und testen. Laufzeitumgebungen können sich anders verhalten als die lokale Entwicklung.

1. Bereitstellen für die Laufzeit:

   ```bash
   aio-app-deploy
   ```

1. Testen bereitgestellter Aktionen

1. Webbrowser oder direkte HTTP-Anfragen verwenden

1. Überprüfen der Aktivierungsprotokolle auf das Debugging

#### Nutzen der Kodierungstools für die Testunterstützung

Bitten Sie um Hilfe beim Testen. Die Tools können beim Debuggen, bei der Protokollanalyse und beim Erstellen geeigneter Testdaten für Ihre spezifischen Laufzeitaktionen hilfreich sein.

**Laufzeitaktionen testen**:

```terminal
Help me test the customer-created runtime action running locally
```

**Fehler beim Debuggen**:

```terminal
Why did the subscription-updated runtime action activation fail?
```

**Protokolle überprüfen**:

```terminal
Help me check the logs for the last stock-monitoring runtime action invocation
```

**Erstellen von Test-Payloads**:

```terminal
Generate test data for this Commerce event
```

```terminal
Create a test payload for the customer_save_after event
```

**Laufzeitendpunkte suchen**:

```terminal
What's the URL for this deployed action?
```

**Authentifizierung verarbeiten**:

```terminal
How do I authenticate with this external API?
```

**Fehlerbehebung**:

```terminal
Help me debug why this action is returning 500 errors
```

### Debugging

Stoppen und beurteilen, wann etwas schief geht. Wenn Probleme auftreten:

* Beenden und bewerten - Nicht in beschädigtem Zustand fortfahren
* Protokolle überprüfen - Verwenden Sie Aktivierungsprotokolle, um Probleme zu identifizieren.
* Vereinfachen - Entfernen von Komplexität zur Isolierung von Problemen
* Inkrementelles Testen - Beheben eines Problems auf einmal
* Validieren : Testen Sie jede Fehlerbehebung, bevor Sie fortfahren.

### Bereitstellung

Verwenden Sie bei der Bereitstellung die folgenden Best Practices:

#### Inkrementelle Bereitstellung

Stellen Sie nur geänderte Aktionen bereit, um die Entwicklung zu beschleunigen. Dadurch wird das Risiko verringert, dass vorhandene Funktionen beeinträchtigt werden, und es wird schnelleres Feedback zu Änderungen bereitgestellt. Außerdem wird das Risiko minimiert, dass vorhandene Funktionen beschädigt werden.

* Verwenden von MCP-Tools zum Bereitstellen spezifischer Aktionen

  ```bash
  aio-app-deploy --actions action-name
  ```

* Bereitstellen einzelner Aktionen nach lokalen Tests
* Inkrementelle Bereitstellung und Vermeidung vollständiger Anwendungsbereitstellungen während der Entwicklung

#### Laufzeitbereinigung

Nutzen Sie nach umfangreichen Änderungen die Tools, um verwaiste Aktionen zu bereinigen. Lassen Sie die KI-Tools den Bereinigungsprozess systematisch durchführen. Sie können verwaiste Aktionen effizient identifizieren, ihren Status überprüfen und sie ohne manuelles Eingreifen sicher entfernen.

```terminal
Help me identify and clean up orphaned runtime actions
```

Anfordern des KI-Tools zum Auflisten bereitgestellter Aktionen und Identifizieren nicht verwendeter Aktionen

```terminal
List all deployed actions and identify which ones are no longer needed
```

Lassen Sie die KI-Tools verwaiste Aktionen mit entsprechenden Befehlen entfernen

```terminal
Remove the orphaned actions that are no longer part of the current implementation
```

### Überwachung

Verwenden Sie bei der Überwachung Ihrer Anwendung die folgenden Best Practices:

#### Auf Kontext-Qualitätsindikatoren achten

* **Guter Kontext**: KI speichert aktuelle Entscheidungen, verweist auf korrekte Dateien
* **Schlechter Kontext**: KI fragt nach zuvor angegebenen Informationen, wiederholt gelöste Probleme

#### Entwicklungsgeschwindigkeit verfolgen

* **Hohe Geschwindigkeit**: Klare Fortschritte, minimale Klärung erforderlich
* **Niedrige Geschwindigkeit**: Wiederholte Erklärungen, KI-Verwirrung, langsamer Fortschritt

#### Kosteneffizienz überwachen

Verfolgen Sie Token-Nutzungsmuster:

* **Effizient**: Geringe Token-Nutzung, wenige Kontextzusammenfassungen
* **Ineffizient**: Hohe Token-Nutzung, mehrere Zusammenfassungen, wiederholte Arbeit

## Was zu vermeiden ist

Bei Verwendung der KI-Kodierungs-Tools sollten Sie die folgenden Anti-Muster vermeiden:

* **Die Klärungsphase nicht überspringen** - Stellen Sie sicher, dass Phase 1 vor der Implementierung abgeschlossen ist.
* **Test nach jeder Funktion nicht überspringen** - Inkrementelles Testen, nicht warten, bis alles abgeschlossen ist.
* **Komplexität nicht ohne Ursachenanalyse hinzufügen** - Fragen Sie unnötige Dateihinzufügungen und fordern Sie eine ordnungsgemäße Untersuchung an.
* **Deklarieren Sie keinen Erfolg ohne echte Datentests** - Testen Sie immer mit tatsächlichen Daten, nicht nur mit Edge-Fällen.
* **Vergessen Sie nicht die Laufzeitbereinigung** - Bereinigen Sie verwaiste Aktionen immer nach größeren Änderungen.
