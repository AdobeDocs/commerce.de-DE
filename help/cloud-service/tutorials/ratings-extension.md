---
title: Tutorial zur Bewertungserweiterung
description: Erfahren Sie, wie Sie mithilfe von App Builder und KI-unterstützten Entwicklungstools eine Produktbewertungserweiterung für Adobe Commerce as a Cloud Service erstellen.
feature: App Builder, Cloud
role: Developer
level: Intermediate
source-git-commit: fb3595284761e9478c819150c27d06631de67e18
workflow-type: tm+mt
source-wordcount: '603'
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

1. Wenn Sie dem Kontext des Cursors eine Dokumentation hinzugefügt haben, deaktivieren Sie diese:

   - Navigieren Sie zu [!UICONTROL **Cursor**] > [!UICONTROL **Einstellungen**] > [!UICONTROL **Cursor-Einstellungen**] > [!UICONTROL **Indizierung und Dokumente**] und löschen Sie alle aufgelisteten Dokumentationen.

   ![Cursor-Indizierungs- und Dokumenteneinstellungen, wobei die Dokumentationsliste leer ist](../assets/disable-documentation.png){width="600" zoomable="yes"}

1. Generieren von Code für eine Produktbewertungserweiterung:
   - Wählen Sie im Cursor-Chat-Fenster [!UICONTROL **Agent**]-Modus aus.
   - Geben Sie die folgende Eingabeaufforderung ein:

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

### Lokale Tests

1. Bitten Sie den Agenten, Ihnen beim lokalen Testen des Codes zu helfen.

   ```shell-session
   Test the ratings API locally on a dev server using cURL.
   ```

1. Befolgen Sie die Anweisungen des Agenten und bestätigen Sie, dass die API lokal funktioniert.

   ![KI-Agent-Anweisungen für lokale API-Tests](../assets/local-testing.png){width="600" zoomable="yes"}

   ![Terminal mit erfolgreichen Ergebnissen aus lokalen API-Tests mit cURL](../assets/local-testing-1.png){width="600" zoomable="yes"}

### Bereitstellen der Erweiterung

1. Nachdem Sie den generierten Code überprüft haben, stellen Sie die Erweiterung mithilfe der folgenden Eingabeaufforderung bereit:

   ```shell-session
   Deploy the ratings API.
   ```

   Der Agent führt vor der Bereitstellung eine Bewertung der Bereitschaft durch.

   ![Checkliste zur Bewertung der Bereitschaft des KI-Agenten vor der Bereitstellung](../assets/pre-deployment-assessment.png){width="600" zoomable="yes"}

1. Wenn Sie mit den Bewertungsergebnissen vertraut sind, weisen Sie den Agenten an, mit der Bereitstellung fortzufahren.

   Der Agent verwendet das MCP-Toolkit, um automatisch zu überprüfen, zu erstellen und bereitzustellen.

   ![MCP Toolkit-Verifizierungs-Build- und Bereitstellungsprozess](../assets/deployment-process.png){width="600" zoomable="yes"}

### Nach der Bereitstellung

Sie können die API testen, bevor Sie sie in die Storefront integrieren. Der Agent sollte den Speicherort der neuen Aktion und eine Teststrategie angeben.

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
<!-- 
Return to the terminal and run the following command in the `extension` folder to copy the file to the `storefront` folder:

```bash
cp RATINGS_API_CONTRACT.md ../storefront
``` -->

### Nächste Schritte

Nachdem Sie nun über den Vertrag für die Ratings-API verfügen, können Sie mit dem Erstellen des Frontend-Teils der Ratings-Erweiterung beginnen.

<!-- 
## Connect to the storefront

This section teaches you how to implement real storefront features and communicate effectively with AI agents when working with [!DNL Adobe Commerce] dropins and [!DNL Edge Delivery Services].

>[!NOTE]
>
>The prompts provided are starting points. Although you can use them without modification, consider having a natural conversation with the agent.
>
>When working with AI-assisted development tools, there are always natural variations in the code and responses generated by the agent.
>
>If you encounter any issues with your code, ask the agent to help you debug it.

### Ratings stars and review count implementation

1. Navigate to the `storefront` folder:

   ```bash
   cd storefront
   ```

1. Open the storefront folder in a new Cursor window.

    Alternatively, if you have the [Cursor CLI](https://cursor.com/docs/configuration/shell#installing-cli-commands) installed, open the window by using the following command in your terminal:

   ```bash
   cursor .
   ```

1. Start the local development server:

   ```bash
   npm run start
   ```

1. In a browser, navigate to the Apparel page:

   ```shell-session
   http://localhost:3000/apparel
   ```

1. Observe the boilerplate storefront UI layout and note the lack of visual product ratings.

1. Use the following prompt with your agent:

   ```shell-session
   Implement product ratings in the storefront.

   Add a 5-star rating display with a review count underneath each product name on the product list page, product details page, and product recommendations.

   Use the dropin slot system where available.

   Use @RATINGS_API_CONTRACT.md to understand how to use the ratings API.
   ```

1. Observe the changes in the codebase, and watch the Apparel page for updates.

   You should see the following changes in your development environment and browser:

   * A product rating "component" is automatically created.
   * The component is integrated into product-details, product-list-page, and product-recommendations blocks using [dropin slots](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/customize/slots).
   * Stars display with proper fill proportions based on mock rating values.

![Product Ratings Implementation](../assets/product-ratings-implementation.png){width="600" zoomable="yes"}

## Tutorial recap

Here is a summary of the topics covered in this tutorial:

* **Feature implementation**: How to describe new functionality to an AI agent.
* **Iterative changes**: Making quick modifications to existing code.
* **Complex UI components**: Building interactive features with visual references.
* **Dropin integration**: Working with [!DNL Adobe Commerce] dropin containers and slots.
* **Component reusability**: Creating shared components used across multiple blocks.

## Next steps

For further experimentation with this tutorial, use the following suggestions to further customize your ratings extension, or create your own modifications:

### Change the star colors

Use the following prompt to your agent:

```shell-session
Change the star fill color to red.
```

**Expected outcome:**

The stars are changed to red.

![Red Star Colors](../assets/red-star-colors.png){width="600" zoomable="yes"}

### Add rating distribution modal

The following steps show how the agent handles complex UI features with visual references.

1. **Before starting:** Save the following mock image and paste it into the chat with your storefront agent.

   ![Rating Distribution Mockup](../assets/rating-distribution-mockup.png){width="600" zoomable="yes"}

1. Follow these steps to create the ratings distribution modal using the reference image as a guide:

   * Update the API to return additional data representing the ratings distribution.
   * Update the API Contract.
   * Update the contact in the storefront codebase.
   * Ask the storefront agent to use the reference image and updated API Contract to add the ratings distribution to the PDP page.

1. Observe the following changes in the codebase, and watch the Apparel page for updates:

   * How the agent interprets the visual mockup
   * Whether it uses appropriate HTML structure for accessibility
   * How it handles the positioning and interaction states

#### Troubleshooting

* If the modal does not appear, check the browser console for errors.
* If positioning is off, ask the agent to fix it using the following format:

   ```shell-session
   adjust the modal position to be...
   ```

![Rating Distribution Modal](../assets/rating-distribution-modal.png){width="600" zoomable="yes"}
 -->
