---
title: Tutorial zur Erweiterung von Versandschätzungen
description: Erfahren Sie, wie Sie mithilfe von App Builder, Edge Delivery Services und KI-unterstützten Entwicklungstools eine Erweiterung für Versanddatumsschätzungen für Adobe Commerce as a Cloud Service erstellen.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
hide: true
hidefromtoc: true
source-git-commit: ba445bf33ec9334c853245fce125af12cd244367
workflow-type: tm+mt
source-wordcount: '3398'
ht-degree: 0%

---

# Tutorial zur Erweiterung von Versandschätzungen

Dieses Tutorial führt Sie durch die Erstellung einer Erweiterung für Versanddatumsschätzungen für [!DNL Adobe Commerce as a Cloud Service] mithilfe von [!DNL Adobe App Builder]-, [!DNL Edge Delivery Services]- und KI-unterstützten Entwicklungs-Tools. Die Erweiterung ruft Schätzungen der Versandzeit und des Versanddatums von einer externen API ab und zeigt sie in der Storefront an.

Sie bauen zwei Teile:

- **App Builder-Erweiterung** - Eine Backend-für-Frontend-Aktion (BFF), die eine API für die Schätzung externer Versandschätzungen umschließt, ein Webhook, der Versandmethoden mit Versanddaten am Checkout anreichert, und eine Konfigurationsseite der Admin-Benutzeroberfläche für die Verwaltung von Einstellungen ohne erneute Bereitstellung.
- **Storefront-**: Auf der Produktdetailseite (PDP), der Warenkorbseite und der Kaufbestätigungsseite mithilfe [!DNL Edge Delivery Services] Dropdown-Komponenten und eines freigegebenen Client-Moduls angezeigte Versanddatumsschätzungen.

>[!NOTE]
>
>KI-Agenten sind nicht deterministisch. Die Eingabeaufforderungen, Fragen und Ergebnisse in diesem Tutorial sind Beispiele. Ihr Agent kann verschiedene Fragen, Anforderungen oder Architekturvorschläge erstellen. Verwenden Sie die Beispiele in diesem Tutorial, um den Agenten auf ein ähnliches Ergebnis hinzusteuern.

Bevor Sie beginnen, absolvieren Sie die [Voraussetzungen](./tutorial-prerequisites.md). In diesem Tutorial wird das **Checkout-Starter-Kit** verwendet. Stellen Sie sicher, dass Sie es bereits geklont haben und die auf der Seite Voraussetzungen beschriebenen Einrichtungsschritte ausgeführt haben.

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

Überprüfen Sie außerdem Folgendes:

- Sie haben eine [!DNL Adobe Commerce as a Cloud Service] mit Produktdaten. Siehe [Commerce Cloud Service-Instanzen](https://experienceleague.adobe.com/de/docs/commerce/cloud-service/overview){target="_blank"}.
- Sie haben ein Storefront-Projekt mit Ihrer [!DNL Commerce] verbunden. Wenn Sie noch keine haben, führen Sie die Schritte in [Erstellen einer Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/?lang=de){target="_blank"} aus.
- Die `aem` CLI wird installiert:

  ```bash
  npm install -g @adobe/aem-cli
  ```

- Sie haben ein **Kundenkonto** - einen registrierten Kunden in [!DNL Commerce] mit einer gespeicherten Standard-Versandadresse. Versandschätzungen auf PDP- und Warenkorbseiten werden nur angemeldeten Käufern angezeigt. An der Kasse werden Schätzungen für alle Käufer unabhängig vom Authentifizierungsstatus angezeigt.

>[!IMPORTANT]
>
>In diesem Tutorial wird das **Checkout-Starter-Kit** (nicht das Integrations-Starter-Kit) verwendet. Das Checkout-Starter-Kit bietet eine webhook-basierte Erweiterbarkeit für Zahlung, Versand, Steuern und Ereignisse. Stellen Sie sicher, dass Sie das Bootstrapping über das Checkout-Kit vornehmen.

## Einrichten der Pseudo-API für Versandschätzungen

Die Erweiterung ruft eine API für externe Versandschätzungen auf, um Schätzungen des Versanddatums und der Versandzeit zu erhalten. In diesem Tutorial verwenden Sie eine Pseudo-API, damit Sie den gesamten Fluss ohne echtes Provider-Konto ausführen können. Es stehen zwei Optionen zur Verfügung:

- **Option A: Pipedream-Workflow** - Freie Ebene, Schnelleinrichtung, aber mit monatlichen Aufrufbeschränkungen.
- **Option B: App Builder Runtime-Aktion** - Keine externe Abhängigkeit, die während der Backend-Entwicklungsschritte erstellt wurde.

>[!TIP]
>
>Während der Entwicklung können Sie mit Pipedream (Option A) beginnen und zu einer Laufzeitaktion (Option B) wechseln, wenn Sie das Free-Tier-Aufrufkontingent erreicht haben. Beide Optionen implementieren denselben API-Vertrag.

### API-Spezifikation

Die Pseudo-API akzeptiert eine POST-Anfrage und gibt Schätzungen des Versanddatums mit Provider, Transit-Tagen, Abschaltzeit und einer besten Schätzung zurück.

**Anfragetext** (alle Felder sind optional für die Nachahmung):

```json
{
  "origin": { "country_code": "US", "postal_code": "90210", "city": "Beverly Hills" },
  "destination": { "country_code": "US", "postal_code": "10001", "city": "New York" },
  "ship_date": "2026-03-10",
  "carriers": ["standard", "express"],
  "service_levels": ["standard", "express"]
}
```

**Antwort (200 OK):**

```json
{
  "estimates": [
    {
      "carrier_code": "standard",
      "service_code": "ground",
      "delivery_date": "2026-03-14",
      "safe_delivery_date": "2026-03-15",
      "transit_days": 4,
      "cutoff_datetime_utc": "2026-03-10T17:00:00.000Z"
    },
    {
      "carrier_code": "express",
      "service_code": "2day",
      "delivery_date": "2026-03-12",
      "safe_delivery_date": "2026-03-12",
      "transit_days": 2,
      "cutoff_datetime_utc": "2026-03-10T12:00:00.000Z"
    }
  ],
  "best_estimation": { "carrier_code": "express", "delivery_date": "2026-03-12", "transit_days": 2 }
}
```

**Fehlerantworten:** 401 (fehlender/ungültiger API-Schlüssel), 400 (ungültiges `ship_date`), 503 (simulierte Ausfallzeit).

### Einrichten der Nachahmung

>[!BEGINTABS]

>[!TAB Pipedream-Workflow]

Die Option „Pipedream“ verwendet die Bearer-Token-Authentifizierung und akzeptiert eine POST-Anfrage an die Workflow-Trigger-URL.

| Element | Beschreibung |
|------|-------------|
| Basis-URL | Die vollständige URL des Pipedream-Workflow-Triggers (z. B. `https://<id>.m.pipedream.net`) |
| Auth | `Authorization: Bearer <API_KEY>` |
| Methode | POST |

{style="table-layout:auto"}

**Workflow erstellen:**

1. Erstellen Sie einen neuen Workflow in [Pipedream](https://pipedream.com){target="_blank"} (**[!UICONTROL Workflows]** > **[!UICONTROL New Workflow]**).

1. Fügen Sie einen **HTTP/Webhook**-Trigger hinzu, der für POST konfiguriert ist. Pipedream weist eine Webhook-URL zu.

1. Fügen Sie **Schritt „Node.js-Code ausführen** hinzu und fügen Sie den folgenden Handler-Code ein:

   ```javascript
   const DEFAULT_CARRIERS = [
     { carrier_code: "standard", service_code: "ground", transit_days: 4 },
     { carrier_code: "express", service_code: "2day", transit_days: 2 },
     { carrier_code: "priority", service_code: "overnight", transit_days: 1 },
   ];
   
   const ISO_DATE = /^\d{4}-\d{2}-\d{2}$/;
   
   function parseShipDate(shipDate) {
     if (shipDate == null || typeof shipDate !== "string") return null;
     if (!ISO_DATE.test(shipDate)) return null;
     const d = new Date(shipDate + "T12:00:00.000Z");
     if (Number.isNaN(d.getTime())) return null;
     return shipDate;
   }
   
   function addBusinessDays(isoDate, days) {
     const d = new Date(isoDate + "T12:00:00.000Z");
     let added = 0;
     while (added < days) {
       d.setUTCDate(d.getUTCDate() + 1);
       const dow = d.getUTCDay();
       if (dow !== 0 && dow !== 6) added += 1;
     }
     return d.toISOString().slice(0, 10);
   }
   
   function cutoffUtc(isoDate, hour = 17) {
     return `${isoDate}T${String(hour).padStart(2, "0")}:00:00.000Z`;
   }
   
   function getBearerToken(headers) {
     const auth = headers?.Authorization ?? headers?.authorization ?? "";
     if (typeof auth !== "string" || !auth.startsWith("Bearer ")) return null;
     return auth.slice(7).trim() || null;
   }
   
   function handleDeliveryEstimate(body) {
     const shipDate = parseShipDate(body?.ship_date);
     const baseDate = shipDate ?? new Date().toISOString().slice(0, 10);
     let carriers = DEFAULT_CARRIERS;
     if (Array.isArray(body?.carriers) && body.carriers.length > 0) {
       const set = new Set(body.carriers.map((c) => String(c).toLowerCase()));
       carriers = DEFAULT_CARRIERS.filter((c) => set.has(c.carrier_code.toLowerCase()));
     }
     if (Array.isArray(body?.service_levels) && body.service_levels.length > 0) {
       const set = new Set(body.service_levels.map((s) => String(s).toLowerCase()));
       carriers = carriers.filter(
         (c) => set.has(c.service_code.toLowerCase()) || set.has(c.carrier_code.toLowerCase())
       );
     }
     if (carriers.length === 0) {
       return { status: 200, body: { estimates: [], best_estimation: null } };
     }
     const estimates = carriers.map((c) => {
       const delivery_date = addBusinessDays(baseDate, c.transit_days);
       const safe_delivery_date = addBusinessDays(baseDate, c.transit_days + 1);
       const cutoff_datetime_utc = cutoffUtc(baseDate, 17 - c.transit_days);
       return {
         carrier_code: c.carrier_code,
         service_code: c.service_code,
         delivery_date,
         safe_delivery_date,
         transit_days: c.transit_days,
         cutoff_datetime_utc,
       };
     });
     return { status: 200, body: { estimates, best_estimation: estimates[0] } };
   }
   
   export default defineComponent({
     async run({ steps, $ }) {
       const event = steps.trigger?.event ?? steps.trigger ?? {};
       const body = event.body ?? {};
       const headers = event.headers ?? {};
       const auth = getBearerToken(headers);
       const expectedKey =
         (typeof process.env.MOCK_API_KEY === "string" && process.env.MOCK_API_KEY.trim()) || null;
       if (expectedKey && (!auth || auth !== expectedKey)) {
         await $.respond({
           immediate: true,
           status: 401,
           headers: { "Content-Type": "application/json" },
           body: { error: "unauthorized", message: "Missing or invalid API key." },
         });
         return;
       }
       if (body?.ship_date != null && !parseShipDate(body.ship_date)) {
         await $.respond({
           immediate: true,
           status: 400,
           headers: { "Content-Type": "application/json" },
           body: { error: "bad_request", message: "Invalid ship_date; use YYYY-MM-DD." },
         });
         return;
       }
       const { status, body: responseBody } = handleDeliveryEstimate(body);
       await $.respond({
         immediate: true,
         status,
         headers: { "Content-Type": "application/json" },
         body: responseBody,
       });
     },
   });
   ```

1. (Optional) Fügen Sie eine `MOCK_API_KEY` Umgebungsvariable in den Workflow-Einstellungen hinzu, um die Authentifizierung des Bearer-Tokens zu erzwingen. Wenn nicht festgelegt, wird jede Anfrage akzeptiert.

1. Stellen Sie den Workflow bereit.

   Ihr Endpunkt ist die Webhook-Trigger-URL.

**Testen Sie die Nachahmung:**

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer mock-api-key" \
  -d '{"destination": {"country_code": "US", "postal_code": "10001"}}' \
  "https://<your-endpoint>.m.pipedream.net"
```

>[!TAB App Builder Runtime-Aktion]

Die Aktionsoption &quot;App Builder Runtime“ stellt die nachgeahmte Aktion als Laufzeitaktion innerhalb desselben [!DNL App Builder] bereit. Dieser Ansatz hat keine externe Abhängigkeit und keine Aufrufquoten.

Fordern Sie den Agenten auf, die Pseudo-Aktion zu erstellen:

```shell-session
Add a new runtime action to this project that implements the API in @docs/PIPEDREAM_API_SPEC.md
- Add it to a separate package
- Use the code in docs/pipedream as inspiration
```

Der Agent erstellt `actions/mock-delivery-api/index.js` mit demselben API-Vertrag wie die Option „Pipedream“. Nach der Bereitstellung lautet der Endpunkt:

```shell-session
https://<namespace>.adobeioruntime.net/api/v1/web/mock-delivery-api/delivery-estimate
```

Die Authentifizierung wird anhand einer `MOCK_API_KEY` Umgebungsvariablen in `.env` validiert.

>[!ENDTABS]

## Entwicklung von Erweiterungen

Dieser Abschnitt führt Sie durch die Entwicklung des [!DNL App Builder] Backends für die Erweiterung Versandschätzungen . Das Backend bietet drei Aktionen:

| Aktion | Typ | Zweck |
|--------|------|---------|
| `delivery-estimates` | Eigenständige Web-Aktion | BFF für Storefront — PDP und Warenkorb rufen dies für Lieferdaten auf |
| `shipping-methods` | Webhook-Aktion | Anreicherung der Versandraten mit Lieferterminen in `additional_data` an der Kasse |
| `delivery-estimates-config` | Admin-Backend-Aktion | CRUD für Konfiguration gespeichert in `aio-lib-state` |

{style="table-layout:auto"}

1. Stellen Sie in den MCP-Einstellungen in Ihren Codierungs-Agenten sicher, dass das `commerce-extensibility`-Toolset fehlerfrei aktiviert ist.

   Gehen Sie beispielsweise im Cursor zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]**.

   Wenn Fehler angezeigt werden, schalten Sie das Toolset aus und ein.

   >[!NOTE]
   >
   >Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools sollten Sie natürliche Variationen im Code und den vom Agenten generierten Antworten erwarten.
   >Wenn Sie Probleme mit Ihrem Code haben, bitten Sie den Agenten, Ihnen beim Debugging zu helfen.

1. Wenn Sie dem Kontext des Cursors eine Dokumentation hinzugefügt haben, deaktivieren Sie diese.

   Navigieren Sie zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Indexing & Docs]** und löschen Sie die aufgelistete Dokumentation.

### Schritt 1: Eingeben der ersten Eingabeaufforderung

Geben Sie dem Agenten die externe API-Spezifikation für den Kontext und fordern Sie ihn zum Starten auf. Wenn Sie den Agenten anhalten und Fragen stellen, können Sie die Implementierung frühzeitig steuern.

Geben Sie die folgende Eingabeaufforderung im Chat-Fenster des Agenten ein:

```shell-session
I want to build an Adobe App Builder extension that extends the checkout with shipping date and time estimates taken from an external API described in @docs/API_SPEC.md.
Delivery dates for a product will be shown in the product details page and on the cart page.
Implement this feature by using the skills in this workspace for backend code, and a separate workspace with storefront skills. For this extension, focus on the backend skills and create an API_SPEC to hand work over to the storefront skills.

STOP and ask me clarifying questions about the requirements before you do any work.
```

>[!TIP]
>
>Durch Referenzierung der externen API-Spezifikationsdatei (`@docs/API_SPEC.md`) in der Eingabeaufforderung erhält der Agent einen konkreten Kontext zum API-Vertrag eines Drittanbieters. Der Agent verwendet dies, um die Konfigurationsfelder für die BFF-Aktion, den freigegebenen HTTP-Client und die Admin-Benutzeroberfläche zu entwerfen. Wenn Sie den Agenten anweisen, STOPPEN zu starten und Fragen an Trigger zu stellen, führt Sie den Workflow durch und hilft Ihnen, die Implementierung frühzeitig zu steuern.

### Schritt 2: Beantworten der Fragen des Agenten

Der Agent gibt mit einer Reihe von klärenden Fragen zurück, die Themen wie Zielumgebung (PaaS vs. SaaS), Umfang (eigenständige BFF-Aktion, Webhook-Anreicherung oder beides), Ursprungsadressenquelle, Caching-Strategie und Testpräferenz abdecken. Das folgende Beispiel zeigt typische Fragen und Antworten. Ihr Agent kann verschiedene Fragen stellen, aber die Themen sind im Allgemeinen dieselben.

**Beispielfragen für Agenten:**

1. **Zielumgebung** - Wird für PaaS (On-Premise) oder SaaS (Adobe Commerce as a Cloud Service) erstellt?
2. **Scope** - Sollte es sich um eine eigenständige BFF-Aktion (von der Storefront direkt aufgerufen), eine Webhook-Anreicherung (Versandmethoden an der Kasse erweitern) oder um beides handeln?
3. **Admin-Konfigurierbarkeit** - Sollen Einstellungen wie API-URL, API-Schlüssel und Ursprungsadresse über den Commerce-Administrator konfigurierbar oder in `.env` gespeichert werden?
4. **Ursprungsadresse** — Woher kommt die Lieferadresse (Lager)? Sollte es sich um eine statische Konfiguration oder eine dynamisch aufgelöste Konfiguration handeln?
5. **Caching** - Sollen Versandschätzungen Server-seitig zwischengespeichert werden, um Aufrufe an die externe API zu reduzieren? Wenn ja, welche TTL?

**Beispielantworten:**

```shell-session
Clarifications:
1. Let's build for SaaS
2. Let's do this:
(A) Can the PDP/cart call the 3rd party API directly — or are there any benefits of wrapping this call with a runtime action?
(B) Let's use the shipping-methods webhook
3. Let's use a Single-page application (SPA) that uses the Admin UI SDK to integrate with the admin. Since we are adding this config screen, let's make anything else that makes sense configurable to avoid redeployments when changing settings
4. Static configuration — origin address should be configurable in the Admin UI (e.g. warehouse address)
5. Yes, cache on the server side; suggest a TTL (e.g. 30 minutes) and make it configurable in the Admin UI
```

>[!TIP]
>
>Wenn Sie den Agenten fragen, ob die Storefront die Drittanbieter-API direkt aufrufen soll oder eine Laufzeitaktion durchläuft, führt dies eine hilfreiche Architekturdiskussion durch. Der Agent erklärt die Vorteile des BFF-Musters (Backend-für-Frontend): Der API-Schlüssel bleibt Server-seitig, CORS wird gehandhabt, das Caching ist zentralisiert und Sie erhalten Anbieterabstraktion. Wenn Sie nach der Konfigurierbarkeit der Admin-Benutzeroberfläche fragen, wird der Agent dazu gedrängt, alle Einstellungen in `aio-lib-state` anstatt in `.env` zu speichern, sodass Neubereitstellungen beim Ändern von Einstellungen vermieden werden.

>[!NOTE]
>
>Ihr Agent stellt möglicherweise andere Fragen. Verwenden Sie diese Antworten als Anleitung, um den Agenten zum gleichen funktionalen Ergebnis zu führen: eine BFF-Aktion für Storefront-Aufrufe, einen Webhook für Versandmethoden für die Checkout-Anreicherung und eine Konfigurationsseite der Admin-Benutzeroberfläche, auf der Einstellungen in `aio-lib-state` gespeichert werden.

### Schritt 3: Anforderungen und Architektur überprüfen

Der Agent generiert Anforderungen und Architekturdokumente, die Sie überprüfen können. Stellen Sie sicher, dass die Anforderungen mit den von Ihnen angegebenen Antworten übereinstimmen und dass die Architektur Folgendes abdeckt:

- A **BFF action** (`delivery-estimates`) - Eine eigenständige Web-Aktion, die die Storefront von PDP- und Warenkorbseiten aufruft. Er liest die Konfiguration aus `aio-lib-state`, ruft die API für externe Versandschätzungen auf und gibt formatierte Schätzungen zurück.
- Eine **Webhook-Aktion** (`shipping-methods`) - Reichert Versandraten mit Versanddaten in `additional_data` während des Checkouts an. Verwendet die Webhook-Methode `plugin.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates`.
- Eine **Admin-Konfigurationsaktion** (`delivery-estimates-config`) - CRUD für die Konfiguration (API-URL, API-Schlüssel, Ursprungsadresse, Provider, Cache-TTL), die in `aio-lib-state` gespeichert ist.
- **Shared Libraries** - Ein HTTP-Client für die externe API und ein Konfigurationsmodul zum Lesen und Schreiben von `aio-lib-state`.

>[!NOTE]
>
>KI-Agenten sind nicht deterministisch und ihr Verhalten unterscheidet sich je nach Modell und IDE. Möglicherweise erhalten Sie auch andere Fragen, die unterschiedliche Anforderungen und eine andere Architektur mit sich bringen. Wenn ja, versuchen Sie, den Agenten in eine Richtung zu lenken, sodass die Implementierung eng mit dem übereinstimmt, was in diesem Tutorial vorgestellt wird, bevor Sie fortfahren.

### Schritt 4: Implementierungsplan auswählen

Der Agent bietet Ihnen die Möglichkeit, einen detaillierten Implementierungsplan zu erstellen oder eine direkte Implementierung abzuschließen.

- Wenn Sie einen überprüfbaren Plan wünschen, den Sie in Phasen mit mehr Kontrolle ausführen können, wählen Sie die erste Option aus.
- Wählen Sie die zweite Option aus, wenn der Agent die vollständige Implementierung mit minimalem Eingriff durchführen soll.

### Schritt 5: Bereinigen und bereitstellen

Sobald der Agent die Implementierung abgeschlossen hat, erfolgt die Bereinigung. Da nur die Versand-Domain verwendet wird, entfernt der Agent nicht verwendete Strukturvorlagen:

- Zahlungsaktionen und Konfiguration (`validate-payment/`, `filter-payment/`, `payment-methods.yaml`)
- Steueraktionen und Konfiguration (`collect-taxes/`, `collect-adjustment-taxes/`, `tax-integrations.yaml`)
- Ereignisaktionen und Konfiguration (`commerce-events/`, `3rd-party-events/`, `events.config.yaml`)
- Allgemeine Strukturvorlage (`generic/`)
- Admin-UI-SPA-Komponenten aus anderen Domains (z. B. steuerrelevante Seiten und Hooks)
- Nicht verwendete Skripte, Testdateien und Umgebungsvariablen

>[!TIP]
>
>Bitten Sie den Agenten, auch die SPA der Admin-Benutzeroberfläche auf Reste von anderen Domains zu überprüfen. Die Seite Steuerklassen und ihre Hooks können noch auf der Strukturvorlage des Starter Kits vorhanden sein und müssen entfernt werden.

Stellen Sie nach der Bereinigung die Bereitstellung mithilfe der folgenden Schritte **in dieser Reihenfolge**:

```bash
# 1. Copy env template and fill in credentials.
cp env.dist .env

# 2. Select your App Builder workspace.
aio app use --merge

# 3. Sync OAuth credentials from workspace.
npm run sync-oauth-credentials

# 4. Deploy the extension.
aio app deploy

# 5. Register shipping carriers in Commerce.
npm run create-shipping-carriers
```

>[!IMPORTANT]
>
>Schritte nicht überspringen oder neu anordnen. Die Schritte 1-3 sind Voraussetzungen für die Bereitstellung. Der `aio app deploy`-Befehl schlägt fehl, wenn keine Anmeldeinformationen konfiguriert wurden.

### Schritt 6: Webhook und Admin-Benutzeroberfläche konfigurieren

Konfigurieren Sie nach der Bereitstellung den Versand-Webhook. Der Agent kann ein Skript erstellen, das programmgesteuert abonniert werden soll:

```bash
npm run subscribe-webhook
```

Dieser Befehl abonniert den Versand-Webhook mit den folgenden Einstellungen:

| Feld | Wert |
|-------|-------|
| Webhook-Methode | `plugin.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates` |
| Webhook-Typ | `after` |
| Erforderlich | Optional (Fallback auf Standardversand möglich) |
| Zeitüberschreitung | 5.000 ms |

{style="table-layout:auto"}

>[!NOTE]
>
>Bei SaaS wird der Webhook-Methodenname aus dem Pfad `magento.`. Der Webhook-Name für PaaS wird `plugin.magento.out_of_process_shipping_methods...`, während der Webhook-Name für SaaS `plugin.out_of_process_shipping_methods...` ist.

Konfigurieren Sie anschließend die Admin-Benutzeroberfläche:

1. Aktivieren Sie die **Admin-Benutzeroberfläche - SDK** (**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Adobe Services]** > **[!UICONTROL Admin UI SDK]** > **[!UICONTROL Enable]** > **[!UICONTROL Yes]**).

1. Konfigurieren Sie Erweiterungen, indem Sie Ihren [!DNL App Builder] Arbeitsbereich und Ihre Erweiterung auswählen.

1. Klicken Sie auf **[!UICONTROL Refresh registrations]**.

1. Navigieren Sie in der [!DNL Admin] Seitenleiste zu **[!UICONTROL Apps]** > **[!UICONTROL Delivery Estimates]** .

1. Schließen Sie die Konfiguration ab, indem Sie die Funktion aktivieren und die erforderlichen Einstellungen angeben, einschließlich API-URL und API-Schlüssel, Ursprungsadresse, Standardnetzbetreiber, Cache-TTL und Provider-Code-Zuordnungen.

### Schritt 7: Erweiterung testen

Testet die BFF-Aktion der Versandschätzungen direkt:

```bash
curl -s -X POST \
  -H "Content-Type: application/json" \
  -d '{"destination": {"country_code": "US", "postal_code": "10001"}}' \
  "https://<your-runtime-url>/api/v1/web/commerce-checkout-starter-kit/delivery-estimates" | jq .
```

Die Antwort sollte in etwa wie folgt aussehen:

```json
{
  "estimates": [
    {
      "carrier": "standard",
      "service_level": "ground",
      "delivery_date": "2026-03-12",
      "safe_delivery_date": "2026-03-13",
      "transit_days": 4,
      "cutoff_datetime_utc": "2026-03-06T18:00:00Z"
    },
    {
      "carrier": "express",
      "service_level": "2day",
      "delivery_date": "2026-03-10",
      "safe_delivery_date": "2026-03-10",
      "transit_days": 2,
      "cutoff_datetime_utc": "2026-03-06T20:00:00Z"
    }
  ],
  "best_estimation": {
    "carrier": "express",
    "delivery_date": "2026-03-10",
    "transit_days": 2
  }
}
```

### Servicevertrag erstellen

Nachdem das Backend abgeschlossen ist, bitten Sie den Agenten, einen Servicevertrag für die Arbeit an der Storefront zu erstellen:

```shell-session
Produce a spec called STOREFRONT_API_SPEC that I can use in the storefront workspace with the corresponding agent. Also give me a prompt that I could use in that workspace.
```

Der Agent erzeugt `docs/STOREFRONT_API_SPEC.md` mit dem vollständigen BFF-Endpunktvertrag (Anfrage- und Antwortformat, z. B. Payloads, Fehlerbehandlung) und einer einsatzbereiten Eingabeaufforderung für den Storefront-Arbeitsbereich.

Kopieren Sie diese Datei in Ihr Storefront-Projekt, bevor Sie mit den Schritten für die Storefront-Entwicklung beginnen.

>[!TIP]
>
>Die Tatsache, dass der Agent sowohl einen Service **Vertrag als auch** Eingabeaufforderung für den anderen Arbeitsbereich generiert, stellt eine saubere Übergabe zwischen dem Backend- und dem Storefront-Team (oder den Agenten) sicher. Der Storefront-Agent kann sofort mit der Arbeit beginnen, ohne Fragen zur API stellen zu müssen.

## Verbindung zur Storefront herstellen

Dieser Abschnitt führt Sie durch die Implementierung des Storefront-Teils der Erweiterung Versandschätzungen mithilfe von [!DNL Edge Delivery Services]- und KI-unterstützten Entwicklungs-Tools. Sie fügen der PDP-, Warenkorb- und Checkout-Seite Schätzungen des Versanddatums hinzu.

>[!NOTE]
>
>Die angegebenen Eingabeaufforderungen sind Ausgangspunkte. Obwohl Sie sie ohne Änderungen verwenden können, sollten Sie ein natürliches Gespräch mit dem Agenten führen.
>
>Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools gibt es immer natürliche Variationen im Code und den vom Agenten generierten Antworten.
>
>Wenn Sie Probleme mit Ihrem Code haben, bitten Sie den Agenten, Ihnen beim Debugging zu helfen.

### Voraussetzungen für die Storefront

Bevor Sie mit der Storefront-Integration beginnen, stellen Sie sicher, dass Folgendes vorhanden ist:

- Ein Storefront-Projekt, das mit Ihrer [!DNL Commerce]-Instanz verbunden ist
- Commerce Storefront AI-Tools [über die CLI installiert](./tutorial-prerequisites.md#install-the-storefront-ai-tools)
- Die `STOREFRONT_API_SPEC.md`-Datei wurde in den `docs/`-Ordner Ihres Storefront-Projekts kopiert

### Schritt 1: Validieren der Umgebung

Öffnen Sie die `config.json` und stellen Sie sicher, dass die Werte für `commerce-core-endpoint` und `commerce-endpoint` auf Ihren [!DNL Adobe Commerce as a Cloud Service] GraphQL-Endpunkt verweisen.

```json
"commerce-core-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
```

### Schritt 2: Eingeben der ersten Eingabeaufforderung

Wenn der Service-Vertrag bereits in Ihrem Projekt vorhanden ist, fordern Sie den Agenten auf, die Storefront-Integration zu implementieren. Verwenden Sie **Plan**-Modus, falls in Ihrem Agenten verfügbar, um zu verhindern, dass der Agent ohne Plan fortfährt.

```shell-session
I need to implement delivery date estimates on the storefront for an Adobe Commerce (SaaS) store using Edge Delivery Services with storefront drop-ins. The backend is already built and deployed as an App Builder extension.

The full integration contract is in the `docs/STOREFRONT_API_SPEC.md` file— please read it first. It covers two integration points:

PDP and Cart pages — Call the delivery-estimates BFF action (HTTP POST) to fetch estimates for a destination and display the best delivery date.

Checkout shipping step — Delivery dates are already injected into each shipping method's `additional_data` by a webhook. No API call is needed. Just read `additional_data` from the shipping methods and display the delivery date next to each option.

Requirements:
- Show "Get it by [date]" on PDP using best_estimation.delivery_date
- Show a delivery date range on the cart page using delivery_date / safe_delivery_date
- Show delivery dates next to each shipping method at checkout, reading from additional_data
- Show "Order within X hours" countdown using cutoff_datetime_utc where appropriate
- Cache estimates client-side in sessionStorage to avoid redundant calls
- Never block the purchase flow — if estimates are unavailable, hide the UI silently

STOP and ask me any clarifying questions you have about the requirements before you do any work.
```

>[!TIP]
>
>Die Eingabeaufforderung wird detailliert angezeigt, da der vollständige API-Vertrag bereits vom Backend-Agenten verfügbar ist. Durch die Referenzierung von `@docs/STOREFRONT_API_SPEC.md` kennt der Agent die genaue Endpunkt-URL, das Anfrage- und Antwortformat und die Fehlerbehandlung. Die Liste der expliziten Anforderungen verhindert, dass der Agent den Umfang erfindet. Insbesondere erhalten Trigger, die den Planmodus anfordern, den stufenweisen Workflow, der Ihnen dabei hilft, die Implementierung frühzeitig zu steuern.

### Schritt 3: Klärende Fragen beantworten

Der Agent gibt mit Fragen zum Authentifizierungsumfang, zum Checkout-Ansatz und zur Formatierung zurück. Das folgende Beispiel zeigt typische Fragen und Antworten.

**Beispielfragen für Agenten:**

1. **Anonyme vs. angemeldete Benutzer** - Sollten Schätzungen für alle Kunden oder nur für authentifizierte Kunden auf den PDP- und Warenkorbseiten angezeigt werden?
2. **Checkout-Ansatz** - Der Dropdown-Container „ShippingMethods“ legt keine `additional_data` offen, sodass der Agent zwei Optionen vorschlägt:
   - **Option A:** Rufen Sie die BFF an der Kasse und DOM-Inject Liefertermine an (einfacher, konsistent mit PDP/Cart)
   - **Option B:** Erweitern Sie das GraphQL-Fragment zum Auschecken über `overrideGQLOperations`, um `additional_data` einzuschließen
3. **Styling** - Emojis im Vergleich zu vorhandenen Design-Token

**Beispielantworten:**

```shell-session
1. Only for logged-in users — that way we can use the shopper's default shipping address and avoid a zip code input
2. Let's do Option A if feasible
3. Use anything that matches the current styling
```

>[!TIP]
>
>Die Anzeige von Schätzungen nur für angemeldete Kunden ist eine pragmatische Wahl. Der Agent kann die Standard-Versandadresse des Käufers automatisch (über GraphQL) verwenden, sodass keine Postleitzahl eingegeben werden muss. Anonyme Käufer von PDP und Warenkorb würden die Eingabe einer Postleitzahl erfordern, was zu Reibung führt. An der Kasse sehen alle Käufer Liefertermine, da die Lieferadresse bereits eingegeben wurde.

>[!NOTE]
>
>Ihr Agent stellt möglicherweise andere Fragen. Verwenden Sie diese Antworten als Anleitung:
>
>- Zeigen Sie PDP- und Warenkorbschätzungen nur für angemeldete Kunden an (keine Postleitzahleingabe erforderlich).
>- Verwenden Sie zum Auschecken Option A (BFF-Aufruf + DOM-Injektion), um das Auschecken zu vereinfachen.
>- Verwenden Sie vorhandene Design-Token für die Formatierung.

### Schritt 4: Anforderungen und Architektur überprüfen

Der Agent entwirft eine freigegebene Modularchitektur. Stellen Sie sicher, dass Folgendes abgedeckt ist:

| Komponente | Zweck |
|-----------|---------|
| `scripts/delivery-estimates.js` | Gemeinsam genutztes Modul - BFF-Client, Caching (sessionStorage, 30-min TTL), Datumsformatierung, Countdown-Logik, Kundenadressen-Suche, Provider-Zuordnung |
| PDP-Integration | Zeigt „Get it by [date] mit optionalem Countdown zwischen Preis und Beschreibung |
| Warenkorb-Integration | Zeigt den Datumsbereich („Do, 12. März - Fr, 13. März„) in der rechten Spalte über der Bestellzusammenfassung an |
| Checkout-Integration | Ruft BFF auf, wenn der Versandschritt aktiv ist, fügt DOM Versanddaten über `MutationObserver` ein |

{style="table-layout:auto"}

Wichtige Design-Entscheidungen zur Überprüfung:

- Alle BFF-Aufrufe sind nicht blockierend - Seiten werden zuerst gerendert, Schätzungen werden asynchron angezeigt.
- Alle Fehler bleiben lautlos - nur `console.debug`, keine Fehler beim Erstkäufer.
- `CARRIER_MAP` ordnet Commerce-Provider-Codes (DPS, Fedex) den BFF-Provider-Codes (Standard, Express) zu.
- Dynamic `import()` verhindert, dass das Bereitstellungsmodul auf dem kritischen Renderpfad bleibt.

>[!NOTE]
>
>KI-Agenten sind nicht deterministisch und ihr Verhalten unterscheidet sich je nach Modell und IDE. Möglicherweise erhalten Sie auch andere Fragen, die unterschiedliche Anforderungen und eine andere Architektur mit sich bringen. Wenn ja, versuchen Sie, den Agenten in eine Richtung zu lenken, sodass die Implementierung eng mit dem übereinstimmt, was in diesem Tutorial vorgestellt wird, bevor Sie fortfahren.

### Schritt 5: Implementierungsplan auswählen

Der Agent bietet Ihnen die Möglichkeit, einen detaillierten Implementierungsplan zu erstellen oder eine direkte Implementierung abzuschließen.

- Wenn Sie einen überprüfbaren Plan wünschen, den Sie in Phasen mit mehr Kontrolle ausführen können, wählen Sie die erste Option aus.
- Wählen Sie die zweite Option aus, wenn der Agent die vollständige Implementierung mit minimalem Eingriff durchführen soll.

Während der Implementierung erstellt und ändert der Agent die folgenden Dateien:

**Neue Datei:**

- `scripts/delivery-estimates.js` - Freigegebenes Modul mit `fetchDeliveryEstimates()`, `getCustomerShippingAddress()`, `formatDeliveryDate()`, `buildCountdownText()`, `findEstimateForCarrier()`

**Geänderte Dateien:**

- `blocks/product-details/product-details.js` + `.css` — div der Versandschätzung in der rechten Spalte, asynchroner Abruf nach dem Hauptrendering
- `blocks/commerce-cart/commerce-cart.js` + `.css` — Versandschätzung div über der Bestellzusammenfassung
- `blocks/commerce-checkout/commerce-checkout.js`, `containers.js`, `.css` — `MutationObserver` DOM-Injektion für Versandart-Etiketten

Beobachten Sie, wie der Code generiert wird, und stellen Sie Fragen oder leiten Sie den Agenten nach Bedarf weiter.

### Schritt 6: Server starten und testen

Starten Sie nach Abschluss der Implementierung des Agenten den Entwicklungs-Server und testen Sie die Versandschätzungen.

1. Starten Sie den lokalen Entwicklungs-Server:

   ```bash
   npm run start
   ```

1. Melden Sie sich in einem Browser bei Ihrem Kundenkonto an.

   Versandschätzungen für PDP und Warenkorb erfordern eine authentifizierte Sitzung mit einer gespeicherten Standard-Versandadresse.

1. Navigieren Sie zu einer Produktseite und überprüfen Sie die folgenden Ergebnisse:

   | Seite | Erwartetes Ergebnis | Authentifizierung erforderlich |
   |------|-----------------|---------------|
   | PDP | „Get it by Thursday, 12. März“ mit optionalem Countdown | Ja (nur angemeldet) |
   | Warenkorb | „Voraussichtliche Lieferung: Do, 12. März - Fr, 13. März“ | Ja (nur angemeldet) |
   | Checkout | „Voraussichtliche Lieferung: Donnerstag, 12. März“ pro Versandart | Nein (Adresse an der Kasse eingegeben) |

   {style="table-layout:auto"}

>[!NOTE]
>
>Versandmethoden ohne passenden Spediteur (z. B. Flatrate) zeigen keine Schätzung an. Dies ist beabsichtigt - nur in `CARRIER_MAP` zugeordnete Provider erhalten die Lieferdaten.

Sie können manuelle Tests durchführen oder den Agenten bitten, seine Browser-Funktionen zum Testen für Sie zu verwenden:

```shell-session
Run complete browser testing using the following product page 'http://localhost:3000/products/<product-slug>/<sku>'
```

### Schritt 7: Bereinigen

Nachdem Sie den Test übersprungen oder abgeschlossen haben, werden Sie vom Agenten aufgefordert, mit der Bereinigung fortzufahren. Nach der Bestätigung archiviert der Agent alle während der Implementierung entstandenen Dokumentationsartefakte.

## Fehlerbehebung

Verwenden Sie die folgenden Tipps, wenn während des Tutorials Probleme auftreten.

### Backend (App Builder)

| Symptom | Ursache | Fehlerbehebung |
|---------|-------|-----|
| Die Aktion „Konfiguration der Admin-Benutzeroberfläche“ gibt `400 Bad Request` mit der Meldung „Anfrage definiert nicht zulässige Parameter (reservierte Eigenschaften)“ zurück. | Der Frontend-Hook sendet `__ow_method` im Anfragetext. Eigenschaften mit dem Präfix `__ow_` werden von OpenWhisk reserviert und zurückgewiesen, wenn die Aktion `final: true` ist. | Senden Sie eine benutzerdefinierte `method`-Eigenschaft anstelle von `__ow_method`. Die Backend-Aktion liest zuerst `params.method` und kehrt dann auf `params.__ow_method` zurück (was von Runtime automatisch bereitgestellt wird). |
| `aio app deploy` schlägt fehl mit „maxVersion ist in productDependencies erforderlich“ | Die CLI-Validierung erfordert sowohl `minVersion` als auch `maxVersion` in `app.config.yaml` Produktabhängigkeiten. | Fügen Sie jedem `productDependencies` in `app.config.yaml` einen `maxVersion` hinzu. |
| Bereitstellungsbefehl schlägt fehl | Anmeldedaten vor der Bereitstellung nicht konfiguriert. `.env`, Arbeitsbereichsauswahl und OAuth-Synchronisierung müssen zuerst erfolgen. | Folgen Sie der richtigen Reihenfolge: `cp env.dist .env` > `aio app use --merge` > `npm run sync-oauth-credentials` > `aio app deploy`. |

{style="table-layout:auto"}

### Storefront (Edge Delivery Services)

| Symptom | Ursache | Fehlerbehebung |
|---------|-------|-----|
| PDP-Versandschätzung wird für angemeldete Käufer nicht angezeigt | Der PDP-Block initialisiert die `account`-Dropdown-Liste nicht, sodass `getCustomerAddress()` im Hintergrund fehlschlägt und keine Schätzung abgerufen wird. | Verwenden Sie `CORE_FETCH_GRAPHQL.fetchGraphQl()` direkt, um Kundenadressen abzufragen, anstatt sich auf die Konto-Dropdown-API zu verlassen. Dies funktioniert auf jeder Seite. |
| PDP wird nach GraphQL-Fehlerbehebung immer noch nicht angezeigt | Tippfehler im Methodennamen: `CORE_FETCH_GRAPHQL.fetch()` wurde anstelle von `CORE_FETCH_GRAPHQL.fetchGraphQl()` verwendet. | Verwenden Sie den richtigen Methodennamen: `fetchGraphQl` (großes Q, Kleinbuchstaben l). |
| Checkout-Versanddaten werden beim ersten Laden nicht angezeigt | Der `checkout/updated`-Ereignis-Listener wurde registriert, nachdem `checkout/initialized` bereits ausgelöst wurde, sodass die ersten Daten fehlten. | Fügen Sie einen `checkout/initialized` Listener mit `{ eager: true }` hinzu, um Ereignisse zu erfassen, die vor der Registrierung ausgegeben werden. `checkout/updated`-Listener für nachfolgende Änderungen beibehalten. |
| Schätzung für Warenkorbversand wird nicht angezeigt | `block.appendChild(fragment)` verschiebt alle untergeordneten Elemente aus dem Fragment, sodass `fragment.querySelector('.cart__delivery-estimate')` null zurückgibt. | Abfrage von `block` statt `fragment` nach dem Append-Vorgang. |
| Pauschalversand zeigt kein Lieferdatum an der Kasse an | Per Design - `CARRIER_MAP` ordnet nur DPS zu Standard und Fedex zu Express. Die Flatrate hat in der externen API keinen entsprechenden Provider. | Kein Bug. Um Schätzungen für andere Provider hinzuzufügen, erweitern Sie die `CARRIER_MAP` in `scripts/delivery-estimates.js` und konfigurieren Sie den Provider in der Backend-Erweiterung. |

{style="table-layout:auto"}

### Commerce SaaS-Sandbox

| Symptom | Ursache | Fehlerbehebung |
|---------|-------|-----|
| Webhook gibt `429 Too Many Requests` zurück | [!DNL App Builder] Arbeitsbereich befindet sich im Debug-Modus, der über strikte Ratenbeschränkungen pro Minute verfügt. [!DNL Commerce] berechnet die Versandraten häufig während des Checkouts neu und erschöpft das Kontingent. | Bereitstellen in einem Produktionsarbeitsbereich (`aio app use` zum Wechseln und dann `aio app deploy`). Für Produktionsarbeitsbereiche gibt es keine Debug-Ratenbeschränkungen. |
| Webhook-Zeitüberschreitungswarnung (>1000 ms) | Die Webhook-Aktion für Versandmethoden dauerte länger als die [!DNL Commerce] weiche Zeitüberschreitung von 1000 ms. | Aktivieren Sie das Server-seitige Caching in `aio-lib-state` aggressiver, oder erhöhen Sie die Webhook-Zeitüberschreitung in [!DNL Commerce Admin] (Commerce Webhooks-Konfiguration). |

{style="table-layout:auto"}

## Tutorial-Zusammenfassung

Im Folgenden finden Sie eine Zusammenfassung der Themen, die in diesem Tutorial behandelt werden:

- **Pseudo-API-Einrichtung** Erstellen einer Pseudo-Bereitstellungsschätzungs-API mit Pipedream oder einer [!DNL App Builder] Runtime-Aktion.
- **BFF-Muster** Erstellen einer Backend-für-Frontend-Aktion, die die externe API umschließt, Anmeldeinformationen Server-seitig speichert und das Caching zentralisiert.
- **Webhook-Anreicherung:** Erweitern des Webhooks für Versandmethoden, um Lieferdaten an der Kasse in jede Versandoption einzufügen.
- **Konfigurierbarkeit der Admin-Benutzeroberfläche:** Hinzufügen einer Konfigurationsseite mithilfe der [!DNL Admin UI SDK], damit Händler API-Einstellungen, Ursprungsadressen und Provider-Zuordnungen ohne erneute Bereitstellung verwalten können.
- **Dienstverträge:** von API-Verträgen, die Backend-Erweiterungen und Storefront-Implementierungen überbrücken.
- **Storefront-Integration:** Anzeigen von Versandschätzungen für PDP („Erhalten nach„), Warenkorb (Datumsbereich) und Checkout (pro Versandmethode) mithilfe eines freigegebenen Client-Moduls.
- **Nicht blockierende UX:** Sicherstellen, dass Versandschätzungen nie den Kauffluss blockieren - Seiten werden zuerst gerendert und Schätzungen werden asynchron angezeigt.

## Nächste Schritte

Verwenden Sie die folgenden Vorschläge, um Ihren Service für Versandschätzungen zu erweitern:

- **Echte Provider-API verbinden:** Ersetzen Sie die Nachahmung durch eine Live-Versand-API wie UPS, FedEx oder USPS, indem Sie die Service-URL und den API-Schlüssel in der [!DNL Admin UI] ändern.
- **Anonyme Käufer unterstützen:** Fügen Sie auf den Seiten „PDP“ und „Warenkorb“ eine Postleitzahl hinzu, damit Käufer, die nicht angemeldet sind, auch die Versandschätzungen sehen können.
- **Provider-Zuordnungen erweitern:** Fügen Sie weitere Provider-Codes zu `CARRIER_MAP` hinzu, um Versanddaten für zusätzliche Versandmethoden anzuzeigen.
- **Server-seitiges Caching hinzufügen:** Implementieren Sie `aio-lib-state` Caching in der BFF-Aktion, um Aufrufe an die externe API für wiederholte Ursprungs- und Zielpaare zu reduzieren.
- **Kostenvoranschläge in Bestellbestätigung anzeigen** Zeigt das voraussichtliche Lieferdatum auf der Bestellbestätigungsseite und in Transaktions-E-Mails an.
