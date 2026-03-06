---
title: Ratings-Erweiterung - Tutorial
description: Erfahren Sie, wie Sie mithilfe von App Builder und KI-unterstützten Entwicklungstools eine Produktbewertungserweiterung für Adobe Commerce as a Cloud Service erstellen.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
source-git-commit: 33ba97fd6766c9d11baea74170a7119d72e06379
workflow-type: tm+mt
source-wordcount: '1701'
ht-degree: 0%

---

# Tutorial zur Bewertungserweiterung

Dieses Tutorial führt Sie durch den Aufbau einer Produktbewertungserweiterung für [!DNL Adobe Commerce as a Cloud Service] mithilfe von [!DNL Adobe App Builder] und KI-unterstützten Entwicklungs-Tools.

Bevor Sie beginnen, absolvieren Sie die [Voraussetzungen](./tutorial-prerequisites.md).

## Voraussetzungen überprüfen

Stellen Sie sicher, dass die folgenden Voraussetzungen installiert sind:

```bash
# Check Node.js version (should be 22.x.x)
node --version

# Check npm version (should be 9.0.0 or higher)
npm --version

# Check Git installation
git --version

# Check Bash shell installation
bash --version
```

Wenn einer der vorherigen Befehle nicht die erwarteten Ergebnisse zurückgibt, finden Sie unter [Voraussetzungen](./tutorial-prerequisites.md) Anleitung.

## Entwicklung von Erweiterungen

Dieser Abschnitt führt Sie durch die Entwicklung einer Bewertungserweiterung für Adobe Commerce as a Cloud Service mithilfe von KI-unterstützten Entwicklungstools.

1. Navigieren Sie zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]** und stellen Sie sicher, dass das `commerce-extensibility`-Toolset fehlerfrei aktiviert ist. Wenn Fehler angezeigt werden, schalten Sie das Toolset aus und ein.

   ![Cursor-IDE-Einstellungen, für die das MCP Commerce-Extensibility-Toolset aktiviert ist](../assets/cursor-settings.png){width="600" zoomable="yes"}

   >[!NOTE]
   >
   >Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools sollten Sie natürliche Variationen im Code und den vom Agenten generierten Antworten erwarten.
   >Wenn Probleme mit dem Code auftreten, können Sie den Agenten jederzeit um Hilfe beim Debuggen bitten.

1. Deaktivieren Sie jede Dokumentation im Kontext des Cursors:

   * Navigieren Sie zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Indexing & Docs]** und löschen Sie die aufgelistete Dokumentation.

   ![Cursor-Indizierungs- und Dokumenteneinstellungen, wobei die Dokumentationsliste leer ist](../assets/disable-documentation.png){width="600" zoomable="yes"}

1. Generieren von Code für eine Produktbewertungserweiterung:
   * Wählen Sie im Cursor-Chat-Fenster den **[!UICONTROL Agent]** aus.
   * Geben Sie die folgende Eingabeaufforderung ein:

   ```shell-session
   Implement an Adobe Commerce as a Cloud Service extension to handle Product Ratings.
   
   Implement a REST API to handle GET ratings requests.
   
   GET requests will have to support the following query parameters:
   
   sku -> product SKU
   ```

   >[!NOTE]
   >
   >Wenn der Agent eine Suche in der Dokumentation anfordert, lassen Sie diese zu.

1. Beantworten Sie die Fragen des Agenten genau, damit er den besten Code generieren kann.

   ![Cursor-Chat-Fenster im Agent-Modus mit eingegebener Eingabeaufforderung für Erweiterung](../assets/enter-prompt.png){width="600" zoomable="yes"}

   ![KI-Agent, der Fragen zu Erweiterungsanforderungen stellt](../assets/agent-questions.png){width="600" zoomable="yes"}

1. Verwenden Sie den folgenden Beispieltext, um die Fragen des Agenten zu beantworten und randomisierte Bewertungsdaten einzurichten:

   ```shell-session
   Yes, this headless extension is for Adobe Commerce as a Cloud Service storefront,
   but we do not need any authentication for the GET API because guest users should be able to use it on the storefront.
   
   This extension is called directly from the storefront, no async invocation, such as events or webhooks, is required.
   
   Start with just the GET API for now, we will implement other CRUD operations at a later time.
   
   We do not need a DB or storage mechanism right now, just return random ratings data between 1 and 5 and a ratings count between 1 and 1000.
   
   The API should only return the average rating for the product and the total number of ratings.
   We do not need to add tests right now.
   ```

   Der Agent erstellt eine `requirements.md`-Datei, die als Datenquelle für die Implementierung dient.

   ![Vom KI-Agenten erstellte Datei Requirements.md mit Implementierungsdetails](../assets/requirements-file.png){width="600" zoomable="yes"}

1. Überprüfen Sie die `requirements.md` und überprüfen Sie den Plan.

   Wenn alles korrekt aussieht, weisen Sie den Agenten an, zu **Phase 2 - Architekturplanung** zu wechseln.

1. Überprüfen Sie den Architekturplan.

1. Weisen Sie den Agenten an, mit der Code-Generierung fortzufahren.

   Der Agent generiert den erforderlichen Code und stellt eine detaillierte Zusammenfassung der nächsten Schritte bereit.

   ![KI-Agent Phase-2-Architekturplan für die Bewertungs-API](../assets/architecture-planning.png){width="600" zoomable="yes"}

   ![Zusammenfassung der erzeugten Code-Dateien und der Struktur](../assets/code-generation-summary.png){width="600" zoomable="yes"}

   ![KI-Agent mit den nächsten Schritten für Tests und Bereitstellung](../assets/next-steps.png){width="600" zoomable="yes"}

### Lokales Testen der Erweiterung

In den folgenden Schritten wird beschrieben, wie Sie vor der Bereitstellung der Erweiterung überprüfen können, ob sie funktioniert.

1. Bitten Sie den Agenten, Ihnen beim lokalen Testen des Codes zu helfen.

   ```shell-session
   Test the ratings API locally on a dev server using cURL.
   ```

1. Befolgen Sie die Anweisungen des Agenten und bestätigen Sie, dass die API lokal funktioniert.

   ![KI-Agent-Anweisungen für lokale API-Tests](../assets/local-testing.png){width="600" zoomable="yes"}

   ![Terminal mit erfolgreichen Ergebnissen aus lokalen API-Tests mit cURL](../assets/local-testing-1.png){width="600" zoomable="yes"}

### Bereitstellen der Erweiterung

Stellen Sie die Erweiterung mithilfe des Agenten für [!DNL Adobe I/O Runtime] bereit.

1. Nachdem Sie den generierten Code überprüft haben, stellen Sie die Erweiterung mithilfe der folgenden Eingabeaufforderung bereit:

   ```shell-session
   Deploy the ratings API.
   ```

   Der Agent führt vor der Bereitstellung eine Bewertung der Bereitschaft durch.

   ![Checkliste zur Bewertung der Bereitschaft des KI-Agenten vor der Bereitstellung](../assets/pre-deployment-assessment.png){width="600" zoomable="yes"}

1. Wenn Sie mit den Bewertungsergebnissen vertraut sind, weisen Sie den Agenten an, mit der Bereitstellung fortzufahren.

   Der Agent verwendet das MCP-Toolkit, um automatisch zu überprüfen, zu erstellen und bereitzustellen.

   ![MCP Toolkit-Verifizierungs-Build- und Bereitstellungsprozess](../assets/deployment-process.png){width="600" zoomable="yes"}

### Überprüfen der Bereitstellung

Testen Sie die API, bevor Sie sie in die Storefront integrieren. Der Agent sollte den Speicherort der neuen Aktion und eine Teststrategie angeben.

![KI-Agent-Teststrategie mit bereitgestellter Aktions-URL und Testbefehlen](../assets/testing-strategy.png){width="600" zoomable="yes"}

Sie können die API auch manuell mit cURL in einem Terminal testen:

```bash
curl -s "https://<your-site>.adobeioruntime.net/api/v1/web/ratings/ratings?sku=TEST-SKU-123"
```

![Terminal mit erfolgreichem cURL-Test der bereitgestellten Bewertungs-API](../assets/curl-test.png){width="600" zoomable="yes"}

### Integration mit Edge Delivery Services

Um die Bewertungs-API in eine von [!DNL Adobe Commerce] unterstützte [!DNL Edge Delivery Services]-Storefront zu integrieren, bitten Sie den Agenten, einen Service-Vertrag mit den Anforderungen für die Bewertungs-API zu erstellen:

```shell-session
Create a service contract for the ratings api that I can pass on to the storefront agent. Name it RATINGS_API_CONTRACT.md
```

![KI-Agent erstellt Servicevertragsdatei für Storefront-Integration](../assets/create-contract.png){width="600" zoomable="yes"}

![Markdown-Datei der Bewertungs-API mit Endpunkt- und Antwortdetails](../assets/contract.png){width="600" zoomable="yes"}

Kehren Sie zum Terminal zurück und führen Sie den folgenden Befehl im Ordner `extension` aus, um die Vertragsdatei in den Ordner `storefront` zu kopieren:

```bash
cp RATINGS_API_CONTRACT.md ../storefront
```

## Verbindung zur Storefront herstellen

Dieser Abschnitt führt Sie durch die Implementierung des Storefront-Teils der Bewertungserweiterung mithilfe von [!DNL Edge Delivery Services]- und KI-unterstützten Entwicklungs-Tools.

>[!NOTE]
>
>Die angegebenen Eingabeaufforderungen sind Ausgangspunkte. Obwohl Sie sie ohne Änderungen verwenden können, sollten Sie ein natürliches Gespräch mit dem Agenten führen.
>
>Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools gibt es immer natürliche Variationen im Code und den vom Agenten generierten Antworten.
>
>Wenn Sie Probleme mit Ihrem Code haben, bitten Sie den Agenten, Ihnen beim Debugging zu helfen.

### Voraussetzungen für die Storefront

Bevor Sie mit der Storefront-Integration beginnen, überprüfen Sie Folgendes:

* Ein Storefront-Projekt, das mit Ihrer [!DNL Commerce]-Instanz verbunden ist
* Commerce Storefront AI-Tools [über die CLI installiert](./tutorial-prerequisites.md#install-the-storefront-ai-tools)

### Einrichten des Storefront-Arbeitsbereichs

Bereiten Sie Ihre lokale Storefront-Umgebung für die Entwicklung vor.

1. Navigieren Sie zum Ordner `storefront` :

   ```bash
   cd storefront
   ```

1. Öffnen Sie den Ordner „Storefront“ in einem neuen Cursor-Fenster.

   Alternativ können Sie, wenn Sie die [Cursor-CLI](https://cursor.com/docs/configuration/shell#installing-cli-commands) installiert haben, das Fenster öffnen, indem Sie den folgenden Befehl an Ihrem Terminal verwenden:

   ```bash
   cursor .
   ```

1. Starten Sie den lokalen Entwicklungs-Server:

   ```bash
   npm run start
   ```

1. Navigieren Sie in einem Browser zu einer Produktseite:

   ```shell-session
   http://localhost:3000/products/llama-plush-shortie/adb336
   ```

1. Beachten Sie die Produktdetailseite für die TextbausteinStorefront (PDP) und beachten Sie den Mangel an visuellen Produktbewertungen.

### Integrieren der Bewertungs-API

Verwenden Sie den Agenten, um die Bewertungs-API in die Produktdetailseite der Storefront zu integrieren.

1. Verwenden Sie die folgende Eingabeaufforderung mit Ihrem Agenten:

   ```shell-session
   Integrate the ratings API into the PDP to show star ratings and a review count for products. Here's the service contract: @RATINGS_API_CONTRACT.md
   ```

1. Der Agent bewertet die Aufgabenkomplexität und ruft einen stufenweisen Workflow auf. Während **Phase 1 (Anforderungserfassung)** erstellt der Agent ein Anforderungsdokument und stellt klärende Fragen wie:

   * Wo in der PDP sollten die Bewertungen erscheinen?
   * Sollte es sich um einen neuen eigenständigen Block oder eine Steckplatzanpassung innerhalb der vorhandenen Dropdown-Komponente von PDP handeln?
   * Was sollte der Fallback sein, wenn die API nicht verfügbar ist oder keine Daten zurückgibt?
   * Sollen Bewertungen auch auf der PLP (Produktliste) oder nur auf PDP erscheinen?
   * Gibt es Designspezifikationen oder Mockups?

   Beantworten Sie diese Fragen entsprechend Ihren Projektanforderungen. Der Agent aktualisiert das Anforderungsdokument und markiert die Phase als abgeschlossen.

1. Während **Phase 2 (Architekturplanung)** durchsucht der Agent die Dokumentation und Ihre Codebasis, bevor er eine Architektur vorschlägt. Der Agent soll:

   * Suchen Sie in [!DNL Commerce] Dokumentation nach PDP-Dropdown-Containern, Slots und Ereignis-Payloads.
   * Überprüfen Sie Ihr `blocks` und `scripts/initializers/` Ordner auf vorhandenen PDP-bezogenen Code.
   * Erkunden Sie TypeScript-Definitionen für verfügbare Container und Slotkontext-Shapes.

   Der Agent stellt dann Architekturoptionen bereit, z. B.:

   * **Option A:** Passen Sie einen vorhandenen PDP-Dropdown-Slot an, um Bewertungen in der Nähe des Produkttitels einzufügen - eine leichtere Berührung, die upgradefreundlich ist.
   * **Option B:** Erstellen Sie einen neuen eigenständigen `product-ratings`, der unabhängig von der API abgerufen wird - flexibler und entkoppelt.
   * **Option C:** Erstellen Sie einen neuen Block, der auch auf PDP-Ablageereignisse für die Produkt-SKU lauscht - ein hybrider Ansatz.

   Der Plan enthält auch Details zur API-Integration, Leistungsaspekte (verzögertes Laden, Caching), Sicherheit (Bereinigung der Eingabe) und einen Testansatz.

   Überprüfen Sie den Architekturplan und weisen Sie den Agenten an, fortzufahren.

1. Während **Phase 3 (Implementierungsansatz)** bittet der Agent Sie, zwischen folgenden Optionen zu wählen:

   * **Option A:** Überprüfen Sie vor der Code-Generierung einen detaillierten Implementierungsplan (sehen Sie sich zuerst alle Dateien, Muster und die Code-Struktur an).
   * **Option B:** Direkt mit der Code-Erstellung fortfahren.

   Wählen Sie Ihren bevorzugten Ansatz aus.

1. Während **Phase 4 (Implementierung)** generiert der Agent Code basierend auf der ausgewählten Architektur. Je nach Ansatz verwendet der Agent mehrere spezialisierte Fähigkeiten:

   * **Inhaltsmodellierung:** Wenn ein neuer Block erforderlich ist, entwirft der Agent eine benutzerfreundliche Inhaltsstruktur, z. B. eine Konfigurationstabelle mit der API-Endpunkt-URL.
   * **Blockentwicklung:** Der Agent erstellt Blockdateien gemäß [!DNL Edge Delivery Services] Konventionen, einschließlich JavaScript-Dekorationsfunktionen, CSS-Stilen in einem Umfang, ARIA-Kennzeichnungen für Barrierefreiheit sowie Lade- und Fehlerstatusbehandlung.
   * **Dropdown-Anpassung:** Wenn die Architektur die Anpassung von Slots verwendet, importiert der Agent den richtigen Container, verwendet einen verifizierten Slot in der Nähe des Produkttitels und abonniert Produktdatenereignisse für die aktuelle SKU.

   Beobachten Sie, wie der Code generiert wird, und stellen Sie Fragen oder leiten Sie den Agenten nach Bedarf weiter. Der Agent erstellt nach Abschluss der Code-Generierung eine Zusammenfassung der Produktionsbereitschaft.

1. Während **Phase 4.5 (Testen)** bietet der Agent an, die Implementierung zu testen. Wenn Sie akzeptieren, wird der Agent:

   * Erstellt eine lokale Testseite mit den richtigen Skripten und Stilen.
   * Startet einen Entwicklungsserver.
   * Führt eine browserbasierte Überprüfung für visuelles Rendering, Interaktivität, responsives Verhalten, Barrierefreiheit und Leistung durch.
   * Erzeugt einen strukturierten Testbericht mit den Ergebnissen.

   Folgen Sie im Browser, um das Verhalten zu bestätigen und Probleme zu melden.

1. Beobachten Sie die Änderungen in der Code-Basis und suchen Sie auf der Produktseite nach Updates.

   In Ihrer Entwicklungsumgebung und Ihrem Browser sollten die folgenden Änderungen angezeigt werden:

   * Eine Produktbewertungskomponente wird automatisch erstellt.
   * Die Komponente wird je nach ausgewählter Architektur mit [Drop-In-Steckplätzen](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/customize/slots) oder als eigenständiger Block in die PDP integriert.
   * Sterne werden mit korrekten Füllverhältnissen basierend auf den Bewertungswerten aus Ihrer API angezeigt.

   ![Produktdetailseite mit unter dem Produkttitel integrierten Sternebewertungen](../assets/product-ratings-implementation.png){width="600" zoomable="yes"}

## Tutorial-Zusammenfassung

Im Folgenden finden Sie eine Zusammenfassung der Themen, die in diesem Tutorial behandelt werden:

* **Erweiterungsentwicklung:** Erfahren Sie, wie Sie einem KI-Agenten neue Funktionen beschreiben und mithilfe von [!DNL App Builder] eine funktionierende REST-API generieren.
* **Lokales Testen und Bereitstellen:** Lokales Testen der API und deren Bereitstellung mit dem MCP-Toolkit.
* **Dienstverträge:** von API-Verträgen, die Backend-Erweiterungen und Storefront-Implementierungen überbrücken.
* **Schrittweise Storefront-Integration:** Anforderungen, Architektur und Implementierung mithilfe von KI-unterstützten Fähigkeiten durcharbeiten.
* **Drop-in-Integration:** Arbeiten mit [!DNL Adobe Commerce] Drop-in-Containern und -Slots.
* **Wiederverwendbarkeit von Komponenten:** Erstellen freigegebener Komponenten, die in mehreren Blöcken verwendet werden.

## Nächste Schritte

Verwenden Sie die folgenden Vorschläge, um Ihre Bewertungserweiterung anzupassen oder eigene Änderungen zu erstellen:

### Sternenfarben ändern

Verwenden Sie die folgende Eingabeaufforderung mit Ihrem Agenten:

```shell-session
Change the star fill color to red.
```

**Erwartetes Ergebnis:**

Die Sterne werden rot.

![Produktbewertungen mit roter Sternfüllfarbe angezeigt](../assets/red-star-colors.png){width="600" zoomable="yes"}

### Hinzufügen eines Bewertungsverteilungs-Modals

Die folgenden Schritte zeigen, wie der Agent komplexe Benutzeroberflächenfunktionen mit visuellen Verweisen verarbeitet.

1. **Vor dem Start:** Speichern Sie das folgende Pseudo-Bild und fügen Sie es in den Chat mit Ihrem Storefront-Agenten ein.

   ![Mockup, das die Verteilung der Bewertungen nach Sternen zeigt](../assets/rating-distribution-mockup.png){width="600" zoomable="yes"}

1. Führen Sie die folgenden Schritte aus, um das Modal „Bewertungsverteilung“ mithilfe des Referenzbilds als Anleitung zu erstellen:

   * Aktualisieren Sie die -API, um zusätzliche Daten zur Verteilung der Bewertungen zurückzugeben.
   * Aktualisieren Sie den API-Vertrag.
   * Aktualisieren Sie den Vertrag in der Code-Basis der Storefront.
   * Bitten Sie den Storefront-Agenten, das Referenzbild und den aktualisierten API-Vertrag zu verwenden, um die Bewertungsverteilung zur PDP-Seite hinzuzufügen.

1. Sehen Sie sich die folgenden Änderungen in der Code-Basis an und suchen Sie auf der Produktseite nach Aktualisierungen:

   * Interpretation des visuellen Mockups durch den Agenten
   * Ob eine geeignete HTML-Struktur für Barrierefreiheit verwendet wird
   * Handhabung der Positionierungs- und Interaktionsstatus

#### Fehlerbehebung beim Verteilungs-Modal

Wenn sich das Modal nicht wie erwartet verhält, versuchen Sie Folgendes:

* Wenn das Modal nicht angezeigt wird, überprüfen Sie die Browser-Konsole auf Fehler.
* Wenn die Positionierung deaktiviert ist, bitten Sie den Agenten, sie mithilfe des folgenden Formats zu beheben:

  ```shell-session
  adjust the modal position to be...
  ```

![Modal mit detaillierter Ratingverteilung mit Durchbruchbalken auf Sternebene](../assets/rating-distribution-modal.png){width="600" zoomable="yes"}
