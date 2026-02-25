---
title: Tutorial zur Erweiterung der Versandmethode
description: Erfahren Sie, wie Sie mithilfe von App Builder, dem Checkout-Starter-Kit und KI-unterstützten Entwicklungs-Tools eine konfigurierbare Versandmethodenerweiterung für Adobe Commerce as a Cloud Service erstellen.
feature: App Builder, Cloud
role: Developer
level: Intermediate
source-git-commit: e55bc4db196d3d973b981bb2484be950dcd6b7c3
workflow-type: tm+mt
source-wordcount: '1849'
ht-degree: 0%

---

# Tutorial zur Erweiterung der Versandmethode

Dieses Tutorial führt Sie durch den Aufbau einer Versandmethodenerweiterung für [!DNL Adobe Commerce as a Cloud Service] mithilfe von [!DNL Adobe App Builder], dem [Checkout-Starter-Kit](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/){target="_blank"} und KI-unterstützten Entwicklungs-Tools.

Die Erweiterung fügt eine konfigurierbare Versandmethode an der Kasse hinzu, wobei die Preise von einem externen Pseudo-Versandratendienst stammen. Händler konfigurieren die Service-URL, den API-Schlüssel und die Warehouse-Adresse (Versandadresse) in der Admin-Benutzeroberfläche. An der Kasse fordern die Händler die Raten dieser Erweiterungsanfragen an und zeigen dem Kunden die zurückgegebenen Optionen an.

Bevor Sie beginnen, absolvieren Sie die [Voraussetzungen](./tutorial-prerequisites.md).

## Voraussetzungen überprüfen {#tutorial-verify-prerequisites}

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

## Erstellen der Pseudo-Versandraten-API

Erstellen Sie nach Abschluss des [Voraussetzungen](./tutorial-prerequisites.md) die Pseudo-Versandraten-API, damit Sie die Service-URL und den API-Schlüssel bereit haben, wenn Sie die Erweiterung in der [!DNL Commerce Admin] konfigurieren. Die Erweiterung ruft eine API für externe Versandraten auf. In diesem Tutorial verwenden Sie eine Pseudo-API, mit der Sie den Fluss ohne ein echtes Provider-Konto ausführen können. Sie erstellen die Pseudo-API mit [Pipedream](https://pipedream.com) (kostenloses Konto erforderlich). Die Pseudo-API verwendet einen Anfrage-/Antwortvertrag, der typischen echten Versandraten-APIs ähnelt. Daher sollte es einfach sein, diese Erweiterung später mit einem echten Anbieter zu verbinden.

Um die Pseudo-API zu erstellen, laden Sie die [Pseudo-Raten-API](../assets/mock-rates-api-spec.zip)Spezifikationsdatei herunter, öffnen Sie sie und fügen Sie die `.md`-Datei zu Ihrem Projekt hinzu (z. B. `docs/mock-rates-api-spec.md`).

**Zeit:** Das Erstellen der Pseudo-API sollte **5-** Minuten dauern.

### Erstellen eines Workflows und eines HTTP-Triggers

1. Gehen Sie [pipedream.com](https://pipedream.com) und melden Sie sich an oder melden Sie sich an.
1. Klicken Sie **Neuer Workflow** (oder **Workflow hinzufügen**).
1. Wählen Sie für den Trigger **HTTP / Webhook** aus.
1. Legen Sie in der Trigger-Konfiguration **HTTP-Antwort** auf **Eine benutzerdefinierte Antwort aus Ihrem Workflow zurückgeben** fest. Dadurch kann der Code-Schritt die JSON-Pseudoantwort senden.
1. Pipedream zeigt eine eindeutige **HTTP-Endpunkt-URL** an, z. B. `https://123456.m.pipedream.net`.
1. **Kopieren Sie diese URL** und verwenden Sie sie als **Service-URL** beim Konfigurieren der Erweiterung in Commerce Admin.

   ![Pipedream-Workflow mit HTTP/Webhook-Trigger und sichtbarer Endpunkt-URL](../assets/mock-api-trigger.png){width="600" zoomable="yes"}

Auf dem Trigger müssen Sie **Autorisierung** konfigurieren. Die Pseudo-API validiert den `API-Key`-Header im Code-Schritt.

### Schritt „Code hinzufügen“

1. Klicken Sie auf das Symbol **+** , um einen Schritt hinzuzufügen.
1. Wählen Sie **Node.js-Code ausführen** (Code-Schritt) aus.
1. **Ersetzen** Sie den Standardcode durch die folgende JavaScript.

   ```javascript
   export default defineComponent({
   async run({ steps, $ }) {
      const event = steps.trigger.event;
      const body = event.body ?? {};
      const headers = event.headers ?? {};
      const apiKey = headers["api-key"] ?? body.api_key ?? "";
   
      if (!apiKey || String(apiKey).trim() === "") {
         await $.respond({
         immediate: true,
         status: 401,
         headers: { "Content-Type": "application/json" },
         body: { error: "Missing or invalid API-Key header" },
         });
         return;
      }
   
      const shipment = body.shipment;
      if (!shipment || typeof shipment !== "object") {
         await $.respond({
         immediate: true,
         status: 400,
         headers: { "Content-Type": "application/json" },
         body: { error: "Missing or invalid shipment" },
         });
         return;
      }
   
      const rates = [
         {
         service_code: "mock_standard",
         service_name: "Mock Standard",
         carrier_friendly_name: "Mock Carrier",
         shipping_amount: { amount: 5.99 },
         shipment_cost: 5.99,
         cost: 5.99,
         },
         {
         service_code: "mock_express",
         service_name: "Mock Express",
         carrier_friendly_name: "Mock Carrier",
         shipping_amount: { amount: 12.99 },
         shipment_cost: 12.99,
         cost: 12.99,
         },
      ];
   
      await $.respond({
         immediate: true,
         status: 200,
         headers: { "Content-Type": "application/json" },
         body: { rates },
      });
   },
   });
   ```

1. Klicken Sie **Bereitstellen**.

   ![Pipedream Code-Schritt mit Pseudo-Versandraten-Skript](../assets/mock-api-code-step.png){width="600" zoomable="yes"}

Die Nachahmung gibt zwei Ratenoptionen (Pseudo-Standard und Pseudo-Express) für jede gültige Anfrage zurück, die eine nicht leere `API-Key`-Kopfzeile und ein `shipment`-Objekt enthält. Sie werden den API-Schlüssel im [!DNL Commerce Admin] weiter unten in diesem Tutorial konfigurieren. Sie werden auch die Pipeline-Workflow-URL auf demselben Konfigurationsbildschirm angeben. Notieren Sie sich diese also.

## Entwicklung von Erweiterungen

Dieser Abschnitt führt Sie durch die Entwicklung einer Versandmethodenerweiterung für [!DNL Adobe Commerce as a Cloud Service] mithilfe des [Checkout-Starter-Kits](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/){target="_blank"} und KI-unterstützter Entwicklungs-Tools.

1. Navigieren Sie zu den MCP-Einstellungen in Ihrem Codierungs-Agent. Gehen Sie beispielsweise im Cursor zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]**. Stellen Sie sicher, dass das `commerce-extensibility` Toolset fehlerfrei aktiviert ist. Wenn Fehler angezeigt werden, schalten Sie das Toolset aus und ein.

   ![Cursor-IDE-Einstellungen, für die das MCP Commerce-Extensibility-Toolset aktiviert ist](../assets/cursor-settings-shipping.png){width="600" zoomable="yes"}

   >[!NOTE]
   >
   >Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools sollten Sie natürliche Variationen im Code und den vom Agenten generierten Antworten erwarten.
   >
   >Wenn Probleme mit dem Code auftreten, können Sie den Agenten jederzeit um Hilfe beim Debuggen bitten.

1. Wenn Sie dem Kontext des Cursors eine Dokumentation hinzugefügt haben, deaktivieren Sie diese. Navigieren Sie zu [!UICONTROL **Cursor**] > [!UICONTROL **Einstellungen**] > [!UICONTROL **Cursor-Einstellungen**] > [!UICONTROL **Indizierung und Dokumente**] und löschen Sie alle aufgelisteten Dokumentationen.

   ![Cursor-Indizierungs- und Dokumenteneinstellungen, wobei die Dokumentationsliste leer ist](../assets/disable-documentation.png){width="600" zoomable="yes"}

1. Erteilen Sie dem Agenten Zugriff auf die Pseudo-Raten-API-Spezifikation, damit er den Client korrekt implementieren kann. Wenn Sie dies noch nicht getan haben, laden Sie die [Pseudo-Raten-API-Spezifikationsdatei](../assets/mock-rates-api-spec.zip) herunter, öffnen Sie sie und fügen Sie die `.md`-Datei zu Ihrem Projekt hinzu (z. B. `docs/mock-rates-api-spec.md`) und verweisen Sie dann in Ihrer Eingabeaufforderung auf diese Datei.

1. Erstellen Sie die Erweiterung der Versandmethode:

   - Wählen Sie im Chat-Fenster des Agenten den **Plan**-Modus aus, falls verfügbar. Dadurch wird verhindert, dass der Agent ohne Plan fortfährt.
   - Geben Sie die folgende Eingabeaufforderung ein:

   ```shell-session
   Build an Adobe Commerce extension that adds a shipping method at checkout. The rates come from an external mock shipping rates service: the merchant configures the service's URL and API key in Admin, and at checkout the extension asks that service for rates and shows the returned options to the customer.
   
   External service (mock shipping rates API):
   - The service endpoint URL is configurable by the merchant (for example https://123456.m.pipedream.net).
   - The API is specified in ./docs/mock-rates-api-spec.md.
   
   The merchant must be able to configure the following in the Adobe Commerce Admin UI. Use the Adobe Commerce Admin UI SDK (or equivalent App Builder extensibility options for the Admin) to add a configuration screen where the merchant can set:
   - The service URL (where the extension sends rate requests).
   - An API key the service expects (any non-empty value for the mock). The API key is sensitive data: it must be stored securely and must never appear in logs, error messages, or in the UI in full (e.g. mask in the UI).
   - The warehouse (ship-from) address: name, phone, street, city, state, postal code, country. This is the origin used when requesting rates.
   ```

   >[!NOTE]
   >
   >Wenn der Agent eine Suche in der Dokumentation anfordert, lassen Sie diese zu.

   ![Cursor-Chat-Fenster im Agent-Modus mit eingegebener Eingabeaufforderung für die Versanderweiterung](../assets/enter-prompt-shipping.png){width="600" zoomable="yes"}

1. Beantworten Sie die Fragen des Agenten genau, damit er den besten Code generieren kann. Wenn der Agent fragt, welches Kit oder welche Vorlage verwendet werden soll, leiten Sie ihn an das [Checkout-Starter-Kit](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/){target="_blank"} mit der SDK-Erweiterung für die Versand-Domain und die Admin-Benutzeroberfläche weiter, damit sowohl der Versand-Webhook als auch der Bildschirm für die Händlerkonfiguration implementiert sind.

   Der Agent kann eine `requirements.md`-Datei (oder eine entsprechende Datei) erstellen, die als Datenquelle für die Implementierung dient.

1. Überprüfen Sie die `requirements.md` (oder vergleichbare Datei) und überprüfen Sie den Plan. Wenn alles korrekt aussieht, weisen Sie den Agenten an, zur Architekturplanung (oder **Phase 2**) zu wechseln. Bestätigen Sie Folgendes:

   - Eine **shipping-methods**-Aktion (oder Ähnliches) verarbeitet den Commerce-Webhook und ruft die API für externe Raten auf.
   - Eine **shipping-config**-Aktion (oder eine entsprechende Aktion) unterstützt GET (Lesekonfiguration, API-Schlüssel maskiert) und SET (Dienst-URL speichern, API-Schlüssel, Warehouse-Adresse), wobei die Konfiguration sicher gespeichert ist, z. B. im Laufzeitstatus.
   - Die Admin-Benutzeroberfläche enthält eine Registerkarte **Pseudolieferung** (oder eine ähnliche Registerkarte) mit Feldern für die Service-URL, den API-Schlüssel (Kennwort/maskiert) und die Warehouse-Adresse.

   ![Vom KI-Agenten erstellte Anforderungsdatei mit Details zur Implementierung der Versanderweiterung](../assets/requirements-file-shipping.png){width="600" zoomable="yes"}

1. Überprüfen Sie den Architekturplan, wenn der Agent ihn bereitstellt.

   ![AI-Implementierungsplan für Agenten für Erweiterung der Pseudo-Versandraten](../assets/implementation-plan-shipping.png){width="600" zoomable="yes"}

1. Weisen Sie den Agenten an, mit der Code-Generierung fortzufahren. Der Agent sollte der Konfiguration der Versanddienstleister einen **Pseudo**-Provider hinzufügen, sodass Commerce die zurückgegebenen Methoden akzeptieren kann, und die Webhook-Methode `plugin.magento.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates` verwenden (Webhook-Typ **after**, erforderlich **optional**).

   Der Agent generiert den erforderlichen Code und stellt eine detaillierte Zusammenfassung für Ihre nächsten Schritte bereit (einschließlich der Installation von Abhängigkeiten, der Registrierung des Pseudo-Providers, der Konfiguration des Commerce-Webhooks und der Bereitstellung).

   ![Zusammenfassung des generierten Codes und der Implementierung für die Versanderweiterung](../assets/code-generation-summary-shipping.png){width="600" zoomable="yes"}

   ![Nächste Schritte des KI-Agenten für die Installation, Konfiguration des Webhooks und Bereitstellung der Versanderweiterung](../assets/next-steps-shipping.png){width="600" zoomable="yes"}

### Bereinigung vor der Bereitstellung

Entfernen Sie vor der Bereitstellung Code, den die Anwendung nicht benötigt. Das Checkout-Starter Kit kann nicht verwendete Domains (z. B. Zahlung, Steuer oder Ereignisse) und Strukturvorlagen enthalten. Lassen Sie den Support-Mitarbeiter diese entfernen und behalten Sie nur die Versand- und [!DNL Admin UI] bei, indem Sie eine Eingabeaufforderung wie die folgende verwenden:

```shell-session
Proceed with Phase 5 cleanup.
```

Der Agent erstellt einen Bereinigungsbericht, entfernt nicht verwendete Aktionen, Konfigurationen und Skripte und aktualisiert das Projekt. Führen Sie diesen Schritt vor der Bereitstellung aus.

![Bereinigungsbericht der KI-Agent-Phase 5 mit entfernten und gespeicherten Komponenten](../assets/cleanup-report-shipping.png){width="600" zoomable="yes"}

### Bereitstellen der Erweiterung

1. Nachdem Sie den generierten Code überprüft haben, stellen Sie die Erweiterung mithilfe der folgenden Eingabeaufforderung bereit:

   ```shell-session
   Deploy the app.
   ```

   Der Agent führt vor der Bereitstellung eine Bewertung der Bereitschaft durch (z. B. `.env` auf `COMMERCE_WEBHOOKS_PUBLIC_KEY`-, `COMMERCE_BASE_URL`- und OAuth/IMS-Variablen, wenn die Admin-Benutzeroberfläche oder die Commerce-API verwendet wird).

   ![Bereitstellungsschritte für den KI-Agenten und die Bereitstellungsschritte für die Pseudo-Versanderweiterung](../assets/pre-deployment-assessment-shipping.png){width="600" zoomable="yes"}

1. Wenn Sie mit den Bewertungsergebnissen vertraut sind, weisen Sie den Agenten an, mit der Bereitstellung fortzufahren. Der Agent verwendet das MCP-Toolkit, um automatisch zu überprüfen, zu erstellen und bereitzustellen.

   ![MCP Toolkit-Bereitstellungsausgabe mit bereitgestellten Paketen und Webhook-URL für die Versanderweiterung](../assets/deployment-process-shipping.png){width="600" zoomable="yes"}

### Nach der Bereitstellung

Führen Sie nach der Bereitstellung die folgenden Schritte aus, um den Pseudo-Provider zu registrieren, den Webhook und die [!DNL Admin UI] zu konfigurieren und die Erweiterung an der Kasse zu überprüfen.

1. **Pseudo-Provider in Commerce registrieren** (einmal nach der Bereitstellung ausführen):

   ```bash
   npm run create-shipping-carriers
   ```

   Stellen Sie sicher, dass Ihr `.env` über `COMMERCE_BASE_URL` und gültige OAuth/IMS-Anmeldeinformationen verfügt, damit das Skript den Provider registrieren kann.

1. **Konfigurieren des Versand-Webhooks in [!DNL Commerce Admin]:**

   - Navigieren Sie **Stores** > Einstellungen > **Konfiguration** > **Adobe Services** > **Commerce Webhooks**.
   - Webhook hinzufügen:
      - **Webhook-Methode:** `plugin.magento.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates`
      - **Webhook-Typ:** **after**
      - **URL:** die bereitgestellte **shipping-methods**-Web-Aktions-URL (aus der Bereitstellungsausgabe oder der [!DNL Adobe Developer Console]).
      - **Erforderlich:** **Optional** - Dadurch kann das Auschecken weiterhin funktionieren, wenn die externe API keine Raten zurückgibt.

   ![Commerce Admin Webhook-Konfiguration für Pseudo-Versandraten](../assets/admin-webhook-shipping.png){width="600" zoomable="yes"}

1. **Konfigurieren der [!DNL Admin UI SDK]:**

   - Navigieren Sie in [!DNL Commerce Admin] zu **Stores** > Einstellungen > **Konfiguration**.
   - Öffnen Sie **Adobe Services** > **Admin-Benutzeroberfläche - SDK**.
   - Setzen Sie **Admin-UI SDK aktivieren** auf **Ja** und klicken Sie auf **Konfiguration speichern**, falls diese noch nicht aktiviert ist.
   - Klicken Sie auf **Erweiterungen konfigurieren**, wählen Sie den Arbeitsbereich aus, in dem Ihre App bereitgestellt wird, und klicken Sie dann auf **Anwenden**. Sie können auch die Option **Benutzerdefiniert** auswählen und den Arbeitsbereichsnamen eingeben.
   - Wählen Sie Ihre [!DNL App Builder] App in der Liste aus und speichern Sie sie. Wenn die App nicht angezeigt wird, klicken Sie auf **Registrierungen aktualisieren** und versuchen Sie es erneut.

   ![Admin-Benutzeroberfläche SDK Konfigurieren Sie die modalen Erweiterungen mit Workspace- und Erweiterungsauswahl](../assets/admin-ui-configure-extensions.png){width="600" zoomable="yes"}

1. **Konfigurieren Sie die Pseudo-Versandmethode in der Admin-Benutzeroberfläche von Adobe Commerce:**
   - Öffnen Sie **Apps** und wählen Sie Ihre App aus.
   - Öffnen Sie die **Pseudo-**&quot; (oder eine entsprechende Option).
   - Geben Sie die folgenden Details ein:
      - **Service-URL:** die Pipedream-Workflow-URL, die Sie kopiert haben (z. B. `https://123456.m.pipedream.net`).
      - **API-Schlüssel** Beliebiger nicht leerer Wert für die Nachahmung, z. B. `tutorial-key`.
      - **Warehouse (Lieferadresse):**, Telefon, Straße, Stadt, Bundesland, Postleitzahl, Land.
   - Klicken Sie **Speichern**. Die Konfiguration wird im Laufzeitstatus gespeichert und von der Aktion „shipping-methods“ verwendet.

   ![Pseudo-Versandkonfigurationsformular mit Service-URL, API-Schlüssel und Warehouse-Adresse](../assets/admin-ui-mock-shipping.png){width="600" zoomable="yes"}

1. **Überprüfen an der Kasse:** Fügen Sie ein Produkt zum Warenkorb hinzu, gehen Sie zur Kasse und geben Sie eine Versandadresse ein. Sie sollten die Pseudo-Versandoptionen sehen, z. B. **Mock Standard** und **Mock Express**.

   ![Checkout-Seite mit Pseudo-Versandoptionen aus der API für externe Tarife](../assets/checkout-mock-shipping.png){width="600" zoomable="yes"}

### Fehlerbehebung

- **Konfiguration wird in der Admin-Benutzeroberfläche nicht gespeichert:** Wenn Sie „Antwort ist ungültig (message/http)“ sehen oder Werte nach dem Speichern nicht aktualisiert werden, überprüfen Sie die Laufzeitaktivierungsprotokolle für die Konfigurationsaktion mit einem Befehl, der dem folgenden ähnelt:

  ```bash
  aio app logs --action CustomMenu/shipping-config --limit 20
  ```

  Häufige Ursachen sind das Gateway, das ein bestimmtes Antwortformat erwartet (z. B. einen Zeichenfolgenkörper und `Content-Type: application/json`) oder die Statusbibliothek, die Zeichenfolgenwerte erfordert. Stellen Sie sicher, dass die Aktion die Konfiguration als Zeichenfolge speichert und sie beim Lesen analysiert und dass die Aktion „shipping-methods“ dieselbe Analyse verwendet. Überprüfen Sie den Agenten-Chat oder die Protokolle auf die genaue Ursache und beheben Sie diese.

- **„Die Antwort muss mindestens einen Vorgang enthalten“** (in Webhook-Protokollen): Commerce erfordert, dass der Versand-Webhook mindestens einen Vorgang zurückgibt. Bitten Sie den Agenten sicherzustellen, dass die Aktion Versandmethoden niemals ein leeres Vorgangs-Array zurückgibt (z. B. durch Rückgabe einer Ausweichrate, wenn die externe API keine Raten zurückgibt).

- **Keine Versandraten an der Kasse:** Vergewissern Sie sich, dass die Webhook-URL und -Methode korrekt sind, der Pseudo-Provider registriert ist (`npm run create-shipping-carriers`) und die Pseudo-Versandkonfiguration in der [!DNL Admin UI] festgelegt ist. Überprüfen Sie die Laufzeitprotokolle für die Aktion „shipping-methods“ auf API- oder Validierungsfehler und stellen Sie sicher, dass die Aktion mindestens einen Vorgang zurückgibt, sodass [!DNL Commerce] nicht anzeigt: „Die Antwort muss mindestens einen Vorgang enthalten.“

### Tutorial-Zusammenfassung

Im Folgenden finden Sie eine Zusammenfassung der Themen, die in diesem Tutorial behandelt werden:

- **Voraussetzungen und Einrichtung:** Überprüfen von Tools und Erstellen der Pseudo-Versandraten-API.
- **Agentengesteuerte Entwicklung:** Verwenden des Commerce-Erweiterbarkeits-Toolsets , um Anforderungen, einen Implementierungsplan und Code für den Versand-Webhook und die Admin-Benutzeroberfläche zu generieren.
- **Bereinigung der Phase 5:** Entfernen nicht verwendeter Checkout-Starter-Kit-Domains und -Strukturvorlagen vor der Bereitstellung.
- **Bereitstellung** Bewertung vor der Bereitstellung und MCP-Toolkit-Bereitstellung.
- **Konfiguration nach der Bereitstellung:** Registrieren des Pseudo-Carriers, Konfigurieren des [!DNL Commerce]-Webhooks, Aktivieren der [!DNL Admin UI SDK]-Erweiterung und Festlegen von Pseudo-Versand (Service-URL, API-Schlüssel, Warehouse) im [!DNL Admin UI].
- **Verifizierung:** Bestätigung der Pseudo-Versandoptionen wird an der Kasse angezeigt.

### Nächste Schritte

Beachten Sie für weitere Experimente mit diesem Tutorial Folgendes:

- Automatisieren Sie die Einrichtung nach der Bereitstellung mit einem Hook, der den Pseudo-Carrier in [!DNL Commerce] registriert und den Versand-Webhook nach jeder Bereitstellung konfiguriert.
- Richten Sie die Erweiterung auf eine echte Versandraten-API ein, indem Sie die Service-URL und den API-Schlüssel in der [!DNL Admin UI] ändern.
- Erweitern Sie die [!DNL Admin UI] , um den Provider-Status anzuzeigen oder die Verbindung zum Tarif-Service zu testen.
