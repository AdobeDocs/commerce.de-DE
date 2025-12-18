---
title: Dokumentations-RAG-Service
description: Erfahren Sie, wie Sie den KI-gestützten Dokumentationssuchdienst für die Adobe Commerce-Entwicklung verwenden.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Developer
hide: true
hidefromtoc: true
source-git-commit: 28396828516645abec3b42a2c6874afe9134dfb8
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---

# Dokumentations-RAG-Service (Beta)

>[!NOTE]
>
>Der Dokumentations-RAG-Service befindet sich derzeit in Beta und das Erlebnis kann sich ändern.

Der Dokumentations-RAG-Service (Retrieval-Augmented Generation) bietet KI-gestützte semantische Suchfunktionen für die entsprechende Dokumentation zu Adobe Commerce und App Builder.

Dieses ARG bietet eine IDE-Oberfläche für Fragen zu Adobe Commerce und kann Sie bei Best Practices für die Entwicklung von Anwendungen und anderen Migrationsaufgaben beraten.

Der RAG-Service ist Teil des MCP-Servers (Model Context Protocol) [&#x200B; &#x200B;](./coding-tools.md)Commerce-Erweiterungstools, der mit Cursor und anderen MCP-kompatiblen KI-Assistenten integriert wird.

## Verfügbare Dokumentation

In der folgenden Tabelle wird beschrieben, welche Dokumentation derzeit vom RAG-Service indiziert wird, und welche Keywords Sie verwenden können, um den zugehörigen Trigger zu durchsuchen. Die enthaltene Dokumentation wird mit der Entwicklung des RAG-Service weiter erweitert.

| Kategorie | Index | Enthaltene Inhalte | Schlüsselwörter |
|-------|---------|---------|------------------------|
| [Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de) | commerce-storefront-docs | Edge Delivery Services, Dropdown-Listen, Storefront-Komponenten | Storefront, Dropin, EDS, Produktliste, Checkout |
| [Erweiterbarkeit](https://developer.adobe.com/commerce/extensibility/) | commerce-extensibility-docs | Webhooks, Ereignisse, Erweiterungen, Integrationen | Webhook, Ereignis, Erweiterung, API-Mesh, GraphQL |
| [Commerce](https://experienceleague.adobe.com/de/docs/commerce/cloud-service/overview) | commerce-core-docs | Core Commerce (Katalog, Kunden, Bestellungen) | Katalog, Produkt, Kunde, Bestellung, Bestand |
| [App Builder](https://developer.adobe.com/app-builder/docs/intro_and_overview/) | app-builder-docs | App Builder, Laufzeitaktionen, Benutzeroberflächenerweiterungen | App Builder, Laufzeitaktion, React Spectrum |

Weitere Informationen zur Indexauswahl finden Sie unter [Automatische Indexauswahl](#automatic-index-selection-recommended) und [Explizite Indexauswahl](#explicit-index-selection).

Ausführliche Informationen zur Dokumentation, die in den einzelnen Indizes enthalten ist, finden Sie in der [Liste der aufgenommenen Quellen](https://github.com/adobe-commerce/azure-commerce-documentation-agent/blob/develop/docs/INGESTED_SOURCES.md).

## Sicherheit und Datenschutz

* **IMS-Authentifizierung** - Alle API-Aufrufe verwenden Adobe IMS OAuth2-Token.
* **Kein Datenspeicher** - Der MCP-Server speichert keine Anmeldeinformationen oder Daten.
* **Lokale Ausführung** - Alle Tools werden lokal auf Ihrem Computer ausgeführt.
* **Sichere Kommunikation** - Die Dokumentationssuche verwendet HTTPS mit Token-Validierung.

Der Produktions-Endpunkt ist durch [Azure Front Door](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview) geschützt, die die folgenden Schutzmaßnahmen umfasst:

* Web Application Firewall (WAF) mit Microsoft Standard RuleSet 2.1 und Bot Manager RuleSet 1.0
* Geoblocking für die von den USA blockierten Regionen (Kuba, Iran, Nordkorea, Syrien, Krim, Luhansk, Donezk)
* DDoS-Schutz am Edge
* API-Management-Backend gesperrt, um nur Traffic von der Haustür zu akzeptieren

Für verschiedene Sicherheitsanforderungen können Sie einen benutzerdefinierten Endpunkt verwenden. Weitere Informationen [&#x200B; Sie unter &#x200B;](#custom-front-door-endpoint)-Endpunkt für benutzerdefinierte Fronttüren .

## Voraussetzungen

Stellen Sie vor der Installation Folgendes sicher:

* [Node.js](https://nodejs.org/en/download){target="_blank"} 18+ (LTS empfohlen)
* [Cursor-IDE](https://cursor.com/download){target="_blank"} (empfohlen) oder eine andere MCP-kompatible IDE

  >[!NOTE]
  >
  >Es werden zwar andere MCP-kompatible IDEs unterstützt, für ein optimales Benutzererlebnis wird jedoch Cursor als IDE empfohlen. Wenn Sie eine andere IDE verwenden, müssen Sie die Eingabeaufforderungen und anderen Schritte in der Dokumentation ändern, um mit der ausgewählten IDE zu arbeiten.

## Installation

1. Installieren Sie [Adobe I/O CLI](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) global:

   ```bash
   npm install -g @adobe/aio-cli
   ```

1. Authentifizierung bei Adobe IMS:

   ```bash
   aio auth login
   ```

1. Klonen Sie das Repository der Commerce-Erweiterbarkeits-Tools und navigieren Sie zum Verzeichnis :

   ```bash
   git clone https://github.com/adobe-commerce/commerce-extensibility-tools.git
   cd commerce-extensibility-tools
   ```

1. Installieren von Abhängigkeiten:

   ```bash
   npm install
   ```

1. Erstellen oder aktualisieren Sie `.cursor/mcp.json` in Ihrem Commerce-Projektverzeichnis (nicht global), um den `commerce-extensibility-tools` MCP-Server einzuschließen:

   ```json
   {
     "mcpServers": {
       "commerce-extensibility-tools": {
         "command": "node",
         "args": [
           "/<your-project-directory>/commerce-extensibility-tools/index.js"
         ],
         "env": {
           "NODE_ENV": "production"
         }
       }
     }
   }
   ```

   Ersetzen Sie `<your-project-directory>` durch den tatsächlichen Pfad, unter dem Sie das Repository geklont haben.

   >[!NOTE]
   >
   >Wenn unter Windows Probleme beim Bereitstellen des Pfads zu Ihrem Projektverzeichnis auftreten, lesen Sie den Abschnitt [Fehlerbehebung bei Pfadproblemen](#path-issues-windows).

1. Starten Sie die Cursor-IDE zum Laden des MCP-Servers neu.

1. Überprüfen Sie die Installation, indem Sie den KI-Assistenten fragen:

   ```shell-session
   Can you show me the available Adobe Commerce tools?
   ```

## Nutzung

Nach der Installation können Sie die Indizes ([) &#x200B;](#automatic-index-selection-recommended) [explizit](#explicit-index-selection) aufrufen. Sie können auch den Befehl [`/search-commerce-docs` verwenden](#command-based-search).

>[!NOTE]
>
>Der RAG-Service gibt die fünf wichtigsten Ergebnisse zurück.

### Automatische Indexauswahl (empfohlen)

Indem Sie Fragen in natürlicher Sprache zu Ihrem Commerce-Projekt stellen, durchsucht das Tool automatisch den entsprechenden Dokumentationsindex und stellt relevante Informationen bereit:

>[!BEGINSHADEBOX]

Die folgende Eingabeaufforderung wählt automatisch den `commerce-storefront-docs` aus:

```shell-session
"How do I use Edge Delivery Services drop-ins for product listing?"
```

Die folgende Eingabeaufforderung wählt automatisch den `commerce-extensibility-docs` aus:

```shell-session
"How do I create a webhook in Adobe Commerce?"
```

Die folgende Eingabeaufforderung wählt automatisch den `commerce-core-docs` aus:

```shell-session
"How to configure product catalog settings?"
```

Die folgende Eingabeaufforderung wählt automatisch den `app-builder-docs` aus:

```shell-session
"What are App Builder runtime action best practices?"
```

>[!ENDSHADEBOX]

### Explizite Indexauswahl

Sie können auch den Index angeben, den Sie in der Eingabeaufforderung verwenden möchten.

```shell-session
Search commerce-storefront-docs for authentication drop-in
```

```shell-session
Using app-builder-docs, how do I deploy runtime actions?
```

### Befehlsbasierte Suche

Wenn Sie sicherstellen möchten, dass der RAG-Service verwendet wird, können Sie den `/search-commerce-docs` Cursor-Befehl manuell aufrufen, um die Dokumentation an Ihrer Eingabeaufforderung zu durchsuchen:

```shell-session
/search-commerce-docs "How do I subscribe to Commerce events?"
```

## Benutzerdefinierter Endpunkt der Fronttür

Standardmäßig verwendet die Dokumentationssuche den Produktions-Endpunkt [Azure Front Door](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview) mit WAF-Schutz. Zu Test- oder Entwicklungszwecken können Sie dies mit der Umgebungsvariablen `FRONT_DOOR_URL` überschreiben.

Um einen benutzerdefinierten Endpunkt zu verwenden, fügen Sie ihn Ihrer Cursor-MCP-Konfiguration hinzu:

```json
{
  "mcpServers": {
    "commerce-extensibility-tools": {
      "command": "node",
      "args": ["/<your-project-directory>/commerce-extensibility-tools/index.js"],
      "env": {
        "NODE_ENV": "production",
        "FRONT_DOOR_URL": "https://<custom-endpoint>.azurefd.net"
      }
    }
  }
}
```

>[!NOTE]
>
>Die meisten Entwickler sollten den standardmäßigen Produktions-Endpunkt verwenden und müssen die `FRONT_DOOR_URL` nicht festlegen.

## Fehlerbehebung

In den folgenden Abschnitten finden Sie Tipps zur Fehlerbehebung bei häufigen Problemen, die bei der Verwendung des Dokumentations-RAG-Service auftreten können.

### Authentifizierungsfehler

Das Dokumentationssuch-Tool erfordert die Adobe IMS-Authentifizierung. Wenn Authentifizierungsfehler auftreten, führen Sie die folgenden Schritte aus, um das Problem zu beheben.

1. Vergewissern Sie sich, dass Sie angemeldet sind:

   ```bash
   aio where
   ```

1. Vergewissern Sie sich, dass Ihr IMS-Token angezeigt wird:

   ```bash
   aio auth login --bare
   ```

1. Wenn die Authentifizierungsfehler weiterhin bestehen, versuchen Sie, sich abzumelden und wieder anzumelden:

   ```bash
   aio auth logout
   aio auth login
   ```

### MCP-Server wird nicht geladen

Wenn der MCP-Server keine Verbindung herstellt oder Ihr Agent sagt, dass er keine Verbindung zum RAG herstellen kann, führen Sie die folgenden Schritte aus, um das Problem zu beheben.

1. Öffnen Sie die Cursoreinstellungen mit **Befehl ,** (macOS) oder **Strg ,** (Windows und Linux).

1. Suchen Sie nach „MCP“ und stellen Sie sicher, dass `commerce-extensibility-tools` aufgeführt und aktiviert ist.

1. Prüfen Sie das Bedienfeld MCP-Einstellungen auf Fehlermeldungen.

1. Überprüfen Sie, ob die `mcp.json` Datei in Ihrem Projekt vorhanden ist:

   ```bash
   cat .cursor/mcp.json
   ```

1. Überprüfen Sie, ob der Pfad korrekt und absolut ist:

   ```bash
   ls -la /<your-project-directory>/commerce-extensibility-tools/index.js
   ```

### Tool nicht gefunden

1. Beenden Sie den Cursor und öffnen Sie ihn erneut.

1. Überprüfen Sie die MCP-Serverprotokolle in der Cursor-Entwicklerkonsole, indem Sie **Befehlstaste+Umschalt+P** (macOS) oder **Strg+Umschalt+P** (Windows/Linux) verwenden und nach „Entwickler: Ordner „Protokolle öffnen“ suchen.

1. Überprüfen Sie die Installation:

   ```bash
   cd commerce-extensibility-tools
   npm install
   node index.js
   ```

   Der Server sollte fehlerfrei starten.

### Pfadprobleme (Windows)

Verwenden Sie unter Windows Schrägstriche `/` oder umgekehrte Schrägstriche mit Escape-Zeichen `\\`:

```json
{
  "args": ["C:/Users/yourname/projects/commerce-extensibility-tools/index.js"]
}
```

```json
{
  "args": ["C:\\Users\\yourname\\projects\\commerce-extensibility-tools\\index.js"]
}
```

## Zusätzliche Ressourcen

* [Entwicklerdokumentation für Adobe Commerce](https://developer.adobe.com/commerce/docs/){target="_blank"}
* [Dokumentation zu App Builder](https://developer.adobe.com/app-builder/docs/){target="_blank"}
* [Modell-Kontextprotokoll](https://modelcontextprotocol.io/){target="_blank"}
* [Cursor-IDE](https://cursor.sh/docs){target="_blank"}
