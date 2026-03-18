---
title: Tutorial zur Erweiterung der Stock-Benachrichtigungen
description: Erfahren Sie, wie Sie mithilfe von App Builder, Edge Delivery Services und KI-unterstützten Entwicklungstools eine lagernde Benachrichtigungserweiterung für Adobe Commerce as a Cloud Service erstellen.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
hide: true
hidefromtoc: true
source-git-commit: ce8882b8af21198a7bc57bc58124e8a2d1491a50
workflow-type: tm+mt
source-wordcount: '2599'
ht-degree: 0%

---

# Tutorial zur Erweiterung „Auf Lager-Benachrichtigungen“

Dieses Tutorial führt Sie durch den Aufbau einer lagernden Benachrichtigungserweiterung für [!DNL Adobe Commerce as a Cloud Service] mithilfe von [!DNL Adobe App Builder] und KI-unterstützten Entwicklungs-Tools. Mit der Erweiterung können Käuferinnen und Käufer nicht vorrätige Produkte abonnieren und eine Benachrichtigung erhalten, wenn das Produkt wieder auf Lager ist.

Sie bauen zwei Teile:

- **App Builder-Erweiterung** - Eine REST-API für die Verwaltung nicht vorrätiger Abonnements (Erstellen, Lesen, Löschen) mit ereignisgesteuerter und geplanter Erkennung von „Back-in-Stock“.
- **Storefront-Integration** - Ein Abonnementformular auf der Produktdetailseite (PDP), das nur angezeigt wird, wenn das ausgewählte Produkt oder die ausgewählte Variante nicht vorrätig ist.

>[!NOTE]
>
>KI-Agenten sind nicht deterministisch. Die Eingabeaufforderungen, Fragen und Ergebnisse in diesem Tutorial sind Beispiele. Ihr Agent kann verschiedene Fragen, Anforderungen oder Architekturvorschläge erstellen. Verwenden Sie die Beispiele in diesem Tutorial, um den Agenten auf ein ähnliches Ergebnis hinzusteuern.

Bevor Sie beginnen, absolvieren Sie die [Voraussetzungen](./tutorial-prerequisites.md). In diesem Tutorial wird das **Integration Starter Kit** verwendet. Stellen Sie sicher, dass Sie es bereits geklont haben und die auf der Seite Voraussetzungen beschriebenen Einrichtungsschritte ausgeführt haben.

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

- Sie haben eine [!DNL Adobe Commerce as a Cloud Service] mit Produktdaten. Siehe [Commerce Cloud Service-Instanzen](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview){target="_blank"}.
- Sie haben ein Storefront-Projekt mit Ihrer [!DNL Commerce] verbunden. Wenn Sie noch keine haben, führen Sie die Schritte in [Erstellen einer Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/){target="_blank"} aus.
- Die `aem` CLI wird installiert:

  ```bash
  npm install -g @adobe/aem-cli
  ```

## Entwicklung von Erweiterungen

Dieser Abschnitt führt Sie durch die Entwicklung einer standardmäßigen Benachrichtigungserweiterung für [!DNL Adobe Commerce as a Cloud Service] mithilfe von KI-unterstützten Entwicklungs-Tools. Die Erweiterung bietet eine REST-API für die Abonnementverwaltung und erkennt, wann Produkte über Commerce-Ereignisse und eine geplante Prüfung wieder auf Lager sind.

1. Navigieren Sie zu den MCP-Einstellungen in Ihrem Codierungs-Agent.

   Gehen Sie beispielsweise im Cursor zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]**. Stellen Sie sicher, dass das `commerce-extensibility` Toolset fehlerfrei aktiviert ist. Wenn Fehler angezeigt werden, schalten Sie das Toolset aus und ein.

   >[!NOTE]
   >
   >Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools sollten Sie natürliche Variationen im Code und den vom Agenten generierten Antworten erwarten.
   >Wenn Sie Probleme mit Ihrem Code haben, bitten Sie den Agenten, Ihnen beim Debugging zu helfen.

1. Wenn Sie dem Kontext des Cursors eine Dokumentation hinzugefügt haben, deaktivieren Sie diese.

   Navigieren Sie zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Indexing & Docs]** und löschen Sie die aufgelistete Dokumentation.

### Schritt 1: Eingeben der ersten Eingabeaufforderung

Den KI-Agenten auffordern, die Implementierung zu starten. Wenn Sie den Agenten anhalten und Fragen stellen, können Sie die Implementierung frühzeitig steuern.

Geben Sie die folgende Eingabeaufforderung im Chat-Fenster des Agenten ein:

```shell-session
Implement an Adobe Commerce as a Cloud Service extension to handle out-of-stock notifications for products.

The service should provide REST API endpoints for basic create, read, update, and delete (CRUD) operations on out-of-stock notifications, allowing storefronts to manage notifications for specific product SKUs.

Back-in-stock is detected by an inventory or product event or a scheduled action that checks Commerce API and then calls the REST API to send the notification.

STOP and ask me any clarifying questions you have about the requirements before you do any work.
```

>[!TIP]
>
>Wenn Sie den Agenten auffordern, vor dem Fortfahren anzuhalten und Fragen zu stellen, können Sie die Implementierung frühzeitig steuern. Dieser Prozess stellt sicher, dass wichtige Annahmen und fehlende Anforderungen frühzeitig erkannt werden. Zudem ist er erforderlich, um den in diesem Tutorial beschriebenen Workflow einzuleiten.

### Schritt 2: Beantworten der Fragen des Agenten

Der Agent gibt eine Reihe von Fragen zurück, die er benötigt, bevor er eine Lösung finden kann. Das folgende Beispiel zeigt typische Fragen und Antworten. Ihr Agent kann verschiedene Fragen stellen, aber die Themen sind im Allgemeinen dieselben.

**Beispielfragen für Agenten:**

1. **REST-API - Host und Verbraucher** - Soll die CRUD-REST-API Teil dieser App Builder-App sein (z. B. Web-Aktionen auf Adobe I/O Runtime), die von Storefronts aufgerufen wird? Wer wird es nennen (EDS-Storefront, benutzerdefinierte/Headless-Storefront oder beides)? Benötigen Sie CORS, öffentlichen (nicht authentifizierten) Zugriff oder verwenden Anrufer API-Schlüssel, OAuth- oder Commerce-Token?
1. **Datenmodell** - Was sollte eine „Benachrichtigung“ darstellen? Kundenkennung (nur E-Mail oder auch Kunden-ID)? Produktkennung (nur SKU oder SKU + Shop-Ansicht)? Kann derselbe Kunde dieselbe SKU mehrmals abonnieren oder sollten Abonnements dedupliziert werden?
1. **Erkennung im Lager - Ereignis vs. geplant** - Möchten Sie eine ereignisgesteuerte Erkennung (Reaktion auf ein Inventar-/Produktereignis von Commerce), eine geplante Erkennung (eine geplante Aktion, die regelmäßig den Bestand überprüft) oder beides? Was soll „Benachrichtigung senden“ bedeuten (einen externen Webhook aufrufen, E-Mail senden oder protokollieren)?
1. **Back-in-stock - Commerce-Quelle** - Haben Sie einen bevorzugten Ereignisnamen oder sollte der Entwurf den Inventar-/Bestandsaktualisierungsereignis verwenden, den Commerce bereitstellt? Für geplante Prüfungen, mit welcher API der Lagerstatus nach SKU abgerufen werden soll?
1. **Persistenz und Multi-Tenancy** - Ist `aio-lib-state` der richtige Ort, um Abonnements beizubehalten, oder haben Sie einen externen Store? Sollte das Design von mehreren Mandanten oder einem einzelnen Mandanten ausgehen?
1. **CRUD-Semantik und Lebenszyklus** - Sollte „Löschen“ bedeuten, dass das Abonnement gekündigt wird? Benötigen Sie „update“? Soll das Abonnement nach dem Versand einer Benachrichtigung zum Lagerhalt automatisch entfernt oder als benachrichtigt markiert werden?
1. **Nicht funktional** — Sollen Tarifbeschränkungen oder maximale Abonnements durchgesetzt werden? Besteht Compliance-Bedarf (doppelte Anmeldung, Einverständniskennzeichnung)?

**Beispielantworten:**

```shell-session
1. The CRUD REST API should be part of thie App Builder app. It will be called by the EDS Storefront. For this implementation there is no need for API keys or security tokens.
2. For this initial implementation the customer identifier will be the email, product is identified by SKU, customer emails should not be able to subscribe to the same SKU multiple times.
3. Implement both. For now instead of sending the notification, log it so I can audit in the Adobe Developer Console.
4. Research and use what the best event to use that commerce already provides. Research the simplest way to get the stock status by SKU.
5. Use the aio-lib-state. Single tenant for now
6. Delete means cancel subscription. Skip Update, it does not apply for this service. After subscription is sent, it should be marked as notified or removed so it won't send again until the user subscribes again.
7. No limits. Implement minimal compliance requirements.
```

>[!NOTE]
>
>Ihr Agent stellt möglicherweise andere Fragen. Verwenden Sie diese Antworten als Anleitung, um den Agenten auf dasselbe funktionale Ergebnis hinzusteuern: eine REST-API mit E-Mail- und SKU-Abonnements, ereignisgesteuerte und geplante Erkennung von „Back-in-Stock“, `aio-lib-state` Persistenz und protokollbasierte Benachrichtigungen.

### Schritt 3: Anforderungen und Architektur überprüfen

Der Agent generiert Anforderungen und Architekturdokumente, die Sie überprüfen können. Stellen Sie sicher, dass die Anforderungen mit den von Ihnen angegebenen Antworten übereinstimmen und dass die Architektur Folgendes abdeckt:

- Eine REST-API-Aktion für CRUD-Abonnements (Erstellen, Lesen, Aktualisieren und Löschen)
- Ein ereignisgesteuerter Handler für den Lagerbestand, der durch Commerce-Inventarereignisse ausgelöst wird
- Eine geplante Aktion zum Überprüfen des Lagerbestands als Fallback
- Persistenz mit `aio-lib-state`

>[!NOTE]
>
>KI-Agenten sind nicht deterministisch und ihr Verhalten unterscheidet sich je nach Modell und IDE. Möglicherweise erhalten Sie auch andere Fragen, die unterschiedliche Anforderungen und eine andere Architektur mit sich bringen. Wenn ja, versuchen Sie, den Agenten in eine Richtung zu lenken, sodass die Implementierung eng mit dem übereinstimmt, was in diesem Tutorial vorgestellt wird, bevor Sie fortfahren.

### Schritt 4: Implementierungsplan auswählen

Der Agent bietet Ihnen die Möglichkeit, einen detaillierten Implementierungsplan zu erstellen oder eine direkte Implementierung abzuschließen.

- Wenn Sie einen überprüfbaren Plan wünschen, den Sie in Phasen mit mehr Kontrolle ausführen können, wählen Sie die erste Option aus.
- Wählen Sie die zweite Option aus, wenn der Agent die vollständige Implementierung mit minimalem Eingriff durchführen soll.

### Schritt 5: Ereignisse bereitstellen, integrieren und abonnieren

Nachdem der Agent die Implementierung abgeschlossen hat, enthält er die nächsten Schritte zum Bereitstellen der App, zum Integrieren der Commerce-Instanz und zum Abonnieren von Ereignissen mithilfe der folgenden Befehle:

1. Bereitstellen der Erweiterung:

   ```bash
   aio app deploy
   ```

1. Führen Sie das Onboarding-Skript aus, um den Ereignisanbieter bei Commerce zu registrieren:

   ```bash
   npm run onboard
   ```

1. Commerce-Ereignisse abonnieren:

   ```bash
   npm run commerce-event-subscribe
   ```

1. Validieren des Ereignisabonnements.

   Navigieren Sie zu Ihrer Commerce-Instanz und öffnen Sie **[!UICONTROL System]** > **[!UICONTROL Event Subscriptions]**.

   Es sollte eine Tabelle mit Ereignisdatensätzen angezeigt werden.

   ![Commerce Admin-Menü mit hervorgehobenem Abschnitt „Ereignisabonnement“](../assets/in-stock-event-subscriptions.png){width="600" zoomable="yes"}

   ![Ereignisabonnement-Tabelle mit registrierten Ereigniseinträgen](../assets/in-stock-event-table.png){width="600" zoomable="yes"}

### Schritt 6: Erweiterung testen

Bitten Sie den Agenten, Testschritte bereitzustellen. Da es sich um einen API-Service handelt, können Sie Befehlszeilenanweisungen anfordern:

```shell-session
Give me step by step instructions to test the API service from the command line.
```

Führen Sie die vom Agenten bereitgestellten Schritte aus. Die folgenden Beispiele zeigen typische Testbefehle.

**Eine SKU abonnieren:**

```bash
API_URL="https://<your-runtime-url>/api/v1/web/notify-out-of-stock/api"; curl -X POST "$API_URL" \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","sku":"ADB153"}'
```

Die Antwort sieht in etwa so aus:

```json
{
  "createdAt": "2026-03-06T22:11:00.308Z",
  "email": "test@example.com",
  "id": "b3353bf5-1007-4b10-989d-430892dd4a66",
  "sku": "ADB153"
}
```

**Alle Abonnements auflisten:**

```bash
curl -X GET "$API_URL"
```

Die Antwort gibt eine Liste aller aktiven Abonnements zurück:

```json
{
  "subscriptions": [
    {
      "createdAt": "2026-03-06T22:11:00.308Z",
      "email": "test@example.com",
      "id": "b3353bf5-1007-4b10-989d-430892dd4a66",
      "sku": "ADB153"
    }
  ]
}
```

**Testen des Back-In-Stock-Flusses:**

1. Bearbeiten Sie in Ihrer Commerce-Instanz ein Produkt, für das Sie ein Abonnement erstellt haben.
1. Setzen Sie den Produktlagerstatus auf **[!UICONTROL Out of Stock]**.
1. Warten Sie etwa eine Minute und schalten Sie den Lagerstatus wieder auf **[!UICONTROL In Stock]** um.

   ![Commerce Admin-Produktbearbeitungsseite, auf der die Dropdown-Liste „Lagerstatus“ mit den Optionen „Auf Lager“ und „Nicht vorrätig“ angezeigt wird](../assets/in-stock-product-stock-status-toggle.png){width="600" zoomable="yes"}

1. Warten Sie etwa fünf Minuten, bis das Ereignis den Trigger erreicht hat und an Ihren -Service senden.

1. Navigieren Sie vom [!DNL Adobe Developer Console] zum Abschnitt App Builder-Protokolle .

   ![Abschnitt mit den Adobe Developer Console App Builder-Protokollen](../assets/in-stock-developer-console-logs.png){width="600" zoomable="yes"}

1. Überprüfen Sie in den Protokollen, ob Einträge vorhanden sind, die bestätigen, dass das Ereignis verarbeitet wurde, und ob das richtige E-Mail-SKU-Abonnementpaar identifiziert wurde.

   ![App Builder-Protokolleinträge, die eine Verarbeitung von Backin-Stock-Ereignissen anzeigen](../assets/in-stock-log-entries.png){width="600" zoomable="yes"}

>[!TIP]
>
>Sie können den Agenten fragen, wonach er in den Protokollen suchen soll, um zu überprüfen, ob die Benachrichtigungsaktion erfolgreich protokolliert wurde. Sie können auch die Protokolleinträge kopieren und einfügen, damit der Agent die Überprüfung durchführt.

Nach dem Ablauf des Back-in-Stock-Ereignisses sollte die Anforderung der Abonnement-Liste einen Eintrag weniger zurückgeben, da das benachrichtigte Abonnement entfernt wird.

### Servicevertrag erstellen

Nachdem die Service-Implementierung abgeschlossen ist, bitten Sie den Agenten, einen Service-Vertrag für die Arbeit an der Storefront zu erstellen:

```shell-session
Create an API service contract for the Out of Stock notification service and its endpoints. Ensure that the service contract is clear and detailed enough for a frontend developer to implement the storefront UI integration without needing to ask additional questions about the API. Name this file OUT_OF_STOCK_NOTIFICATION_CONTRACT.md
```

Kopieren Sie diese Datei in Ihr Storefront-Projekt, damit der Storefront-Agent darauf verweisen kann.

## Verbindung zur Storefront herstellen

Dieser Abschnitt führt Sie durch die Implementierung des Storefront-Teils der Erweiterung „Benachrichtigung auf Lager“ mithilfe von [!DNL Edge Delivery Services]- und KI-unterstützten Entwicklungs-Tools. Sie fügen der Produktdetailseite (PDP) ein Abonnementformular hinzu, das nur angezeigt wird, wenn das ausgewählte Produkt oder die ausgewählte Variante nicht vorrätig ist.

>[!NOTE]
>
>Die angegebenen Eingabeaufforderungen sind Ausgangspunkte. Obwohl Sie sie ohne Änderungen verwenden können, sollten Sie ein natürliches Gespräch mit dem Agenten führen.
>
>Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools gibt es immer natürliche Variationen im Code und den vom Agenten generierten Antworten.
>
>Wenn Sie Probleme mit Ihrem Code haben, bitten Sie den Agenten, Ihnen beim Debugging zu helfen.

### Voraussetzungen für die Storefront

Bevor Sie mit der Storefront-Integration beginnen, überprüfen Sie Folgendes:

- Ein Storefront-Projekt, das mit Ihrer [!DNL Commerce]-Instanz verbunden ist
- Commerce Storefront AI-Tools [über die CLI installiert](./tutorial-prerequisites.md#install-the-storefront-ai-tools)
- Die `OUT_OF_STOCK_NOTIFICATION_CONTRACT.md`-Datei wurde in Ihr Storefront-Projekt kopiert

### Schritt 1: Validieren der Umgebung

Öffnen Sie die `config.json` und stellen Sie sicher, dass die Werte für `commerce-core-endpoint` und `commerce-endpoint` auf Ihren [!DNL Adobe Commerce as a Cloud Service] GraphQL-Endpunkt verweisen.

```json
"commerce-core-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
```

### Schritt 2: Eingeben der ersten Eingabeaufforderung

Wenn sich der Service-Vertrag bereits in Ihrem Projekt befindet, fordern Sie den Agenten auf, die Benutzeroberfläche auf der Produktdetailseite zu erstellen. Verwenden Sie **Plan**-Modus, falls in Ihrem Agenten verfügbar, um zu verhindern, dass der Agent ohne Plan fortfährt.

```shell-session
Analyze @OUT_OF_STOCK_NOTIFICATION_CONTRACT.md. Add a form for subscribing to a notification for when a product is back in stock. Place this form on the product details page, underneath the add to cart and wishlist button. The form only displays when a product is out of stock. 

Use the project manager skill to plan this implementation.
```

>[!TIP]
>
>Insbesondere die Anforderung, die Projektmanager-Kenntnisse-Trigger für den stufenweisen Workflow zu verwenden, der Ihnen dabei hilft, die Implementierung in einem frühen Stadium des Prozesses zu steuern. Dieser Prozess stellt sicher, dass wichtige Annahmen und fehlende Anforderungen frühzeitig erkannt werden, und gibt dem Support-Mitarbeiter die Möglichkeit, Ihnen Details und Anforderungen zu präsentieren, die Sie in der ursprünglichen Eingabeaufforderung möglicherweise nicht angeben wollten.

### Schritt 3: Beantworten von Planungsfragen

Der Agent gibt eine Reihe von Fragen zurück, die er beantworten muss, bevor er eine Lösung finden kann. Das folgende Beispiel zeigt typische Fragen und Antworten. Ihr Agent kann verschiedene Fragen stellen, aber die Themen sind im Allgemeinen dieselben.

**Beispielfragen für Agenten:**

1. **API-Basis-URL** - Wie sollte die Storefront die nicht vorrätige API-Basis-URL für die Benachrichtigung abrufen? Zu den Optionen können ein Konfigurationsblock (z. B. eine Tabelle mit `out-of-stock-api-base-url`), globale Platzhalter oder Umgebungsvariablen oder ein anderer Ansatz gehören.
1. **Copy** - Sollte die Implementierung Platzhalter für Erfolgs- und Fehlermeldungen verwenden (z. B. für die Lokalisierung) oder sollte für diese Implementierung statisches Englisch verwendet werden?
1. **Nach erfolgreichem Abonnieren** - Soll das Formular ausgeblendet werden und nur „Sie haben abonniert“ (A) anzeigen, das Formular sichtbar bleiben, aber mit einer darüber liegenden Erfolgsmeldung deaktiviert bleiben (B) oder ein anderes Verhalten zeigen (C)?
1. **Konfigurierbare Produkte** - Soll die Sichtbarkeit des Formulars auf dem `inStock` der ausgewählten Variante basieren, sodass das Formular anzeigt, wenn die ausgewählte Variante nicht vorrätig ist?

**Beispielantworten:**

```shell-session
1. Global placeholder with baseurl value of `https://<your-runtime-url>/api/v1/web/notify-out-of-stock/api`
2. Use placeholders with static English fallback
3. B
4. Use selected variant's inStock value
```

>[!NOTE]
>
>Ersetzen Sie `<your-runtime-url>` durch die tatsächliche [!DNL Adobe I/O Runtime]-URL aus Ihrer App Builder-Bereitstellung.
>
>Ihr Agent stellt möglicherweise andere Fragen. Verwenden Sie diese Antworten als Anleitung:
>
>- Verwenden Sie einen globalen Platzhalter für die API-Basis-URL, damit sie ohne Code-Änderungen geändert werden kann.
>- Verwenden Sie Platzhalter für eine benutzerorientierte Kopie mit statischem Englisch als Fallback.
>- Lassen Sie das Formular nach erfolgreichem Abonnement sichtbar, aber deaktivieren Sie es mit einer darüber stehenden Erfolgsmeldung.
>- Verwenden Sie für konfigurierbare Produkte den `inStock` der ausgewählten Variante, um die Sichtbarkeit des Formulars zu steuern.

### Schritt 4: Anforderungen und Architektur überprüfen

Der Agent aktualisiert das Anforderungsdokument, damit Sie es überprüfen können. Überprüfen Sie, ob:

- Das Formular wird nur angezeigt, wenn das Produkt oder die ausgewählte Variante nicht vorrätig ist.
- Das Formular befindet sich auf der PDP unter den Schaltflächen „In den Warenkorb legen“ und „Wunschliste“.
- Die API-Integration verwendet die Basis-URL eines globalen Platzhalters.
- Erfolgs- und Fehlerstatus werden vertragsgemäß gehandhabt (201, 409, 400, 503/500).

>[!NOTE]
>
>KI-Agenten sind nicht deterministisch und ihr Verhalten unterscheidet sich je nach Modell und IDE. Möglicherweise erhalten Sie auch andere Fragen, die unterschiedliche Anforderungen und eine andere Architektur mit sich bringen. Wenn ja, versuchen Sie, den Agenten in eine Richtung zu lenken, sodass die Implementierung eng mit dem übereinstimmt, was in diesem Tutorial vorgestellt wird, bevor Sie fortfahren.

Während **Phase 2 (Architekturplanung)** durchsucht der Agent die Dokumentation und Ihre Codebasis, bevor er eine Architektur vorschlägt. Der Agent soll:

- Suchen Sie in [!DNL Commerce] Dokumentation nach PDP-Dropdown-Containern, Slots und Ereignis-Payloads.
- Überprüfen Sie Ihr `blocks` und `scripts/initializers/` Ordner auf vorhandenen PDP-bezogenen Code.
- Erkunden Sie TypeScript-Definitionen für verfügbare Container und Slotkontext-Shapes.

Der Agent zeigt dann Architekturoptionen an. Überprüfen Sie den Plan und weisen Sie den Agenten an, fortzufahren.

### Schritt 5: Implementierungsplan auswählen

Der Agent bietet Ihnen die Möglichkeit, einen detaillierten Implementierungsplan zu erstellen oder eine direkte Implementierung abzuschließen.

- Wenn Sie einen überprüfbaren Plan wünschen, den Sie in Phasen mit mehr Kontrolle ausführen können, wählen Sie die erste Option aus.
- Wählen Sie die zweite Option aus, wenn der Agent die vollständige Implementierung mit minimalem Eingriff durchführen soll.

Während **Phase 4 (Implementierung)** generiert der Agent Code basierend auf der ausgewählten Architektur. Je nach Ansatz verwendet der Agent mehrere spezialisierte Fähigkeiten:

- **Inhaltsmodellierung:** Wenn ein neuer Block erforderlich ist, entwirft der Agent eine benutzerfreundliche Inhaltsstruktur.
- **Blockentwicklung:** Der Agent erstellt Blockdateien gemäß [!DNL Edge Delivery Services] Konventionen, einschließlich JavaScript-Dekorationsfunktionen, CSS-Stilen in einem Umfang, ARIA-Kennzeichnungen für Barrierefreiheit sowie Lade- und Fehlerstatusbehandlung.
- **Dropdown-Anpassung:** Wenn die Architektur die Anpassung von Slots verwendet, importiert der Agent den richtigen Container, verwendet einen verifizierten Slot in der Nähe des Produkttitels und abonniert Produktdatenereignisse für die aktuelle SKU.

Beobachten Sie, wie der Code generiert wird, und stellen Sie Fragen oder leiten Sie den Agenten nach Bedarf weiter.

### Schritt 6: Server starten und testen

Starten Sie nach Abschluss der Implementierung des Agenten den Entwicklungs-Server und testen Sie das Formular.

1. Starten Sie den lokalen Entwicklungs-Server:

   ```bash
   npm run start
   ```

1. Navigieren Sie in einem Browser zu einer nicht vorrätigen Produktseite. Beispiel:

   ```shell-session
   http://localhost:3000/products/<out-of-stock-product-slug>/<sku>
   ```

1. Überprüfen Sie, ob das Abonnementformular unter den Schaltflächen „In den Warenkorb legen“ und „Wunschliste“ angezeigt wird.

Sie können manuelle Tests durchführen oder den Agenten bitten, seine Browser-Funktionen zum Testen für Sie zu verwenden:

```shell-session
Run complete browser testing. Use the following out of stock product 'http://localhost:3000/products/<out-of-stock-product-slug>/<sku>'
```

![Produktdetailseite mit dem Benachrichtigungsformular für Rücklieferungen unterhalb der Schaltfläche Zum Warenkorb hinzufügen](../assets/in-stock-notification-form.png){width="600" zoomable="yes"}

### Schritt 7: Bereinigen

Nachdem Sie den Test übersprungen oder abgeschlossen haben, werden Sie vom Agenten aufgefordert, mit der letzten Phase **Bereinigung** fortzufahren. Nach der Bestätigung archiviert der Agent alle während der Implementierung erstellten Dokumentationsartefakte.

## Fehlerbehebung

Verwenden Sie die folgenden Tipps, wenn während des Tutorials Probleme auftreten:

- **API-Fehler:** Verwenden Sie die CLI, um Anfragen direkt an die API zu senden, um Verhaltensweisen zu überprüfen. Verwenden Sie beispielsweise `curl`, um jeden Endpunkt unabhängig zu testen.
- **Agentenfehler:** Kopieren Sie Fehlermeldungen und fügen Sie sie in eine Chat-Sitzung für Agenten ein, um Probleme zu beheben. Der Agent kann häufige Probleme wie fehlende Umgebungsvariablen oder falsch konfigurierte Aktionen diagnostizieren.
- **Ereignis-Pipeline:** Wenn keine Trigger bei Backin-Stock-Ereignissen auftreten, überprüfen Sie, ob Sie die Schritte Onboarding und Ereignisabonnement abgeschlossen haben. Vergewissern Sie sich, dass sich `workspace.json` am richtigen Speicherort befindet und dass das Commerce-Ereignismodul aktiviert ist.
- **Stock-Status-Payload:** Commerce kann `is_in_stock` als Zeichenfolge (`"1"`) anstelle eines booleschen Werts (`true`) senden. Wenn der Handler „Back-In-Stock“ nicht ausgelöst wird, bitten Sie den Agenten, den Verbraucher-Code auf strenge Typvergleiche zu überprüfen und ihn zu aktualisieren, um beide Formate zu handhaben.

## Tutorial-Zusammenfassung

Im Folgenden finden Sie eine Zusammenfassung der Themen, die in diesem Tutorial behandelt werden:

- **Erweiterungsentwicklung:** Beschreiben neuer Funktionen für einen KI-Agenten und Generieren einer funktionierenden REST-API mit CRUD-Vorgängen mithilfe von [!DNL App Builder].
- **Ereignisgesteuerte Architektur:** Konfigurieren von Commerce-Ereignissen und einer geplanten Aktion, um zu erkennen, wann Produkte wieder auf Lager sind.
- **Lokales Testen und Bereitstellen:** Testen der API mit `curl` und Bereitstellen mithilfe der [!DNL Adobe I/O CLI].
- **Dienstverträge:** von API-Verträgen, die Backend-Erweiterungen und Storefront-Implementierungen überbrücken.
- **Schrittweise Storefront-Integration:** Anforderungen, Architektur und Implementierung mithilfe von KI-unterstützten Fähigkeiten durcharbeiten.
- **Drop-in-Integration:** Hinzufügen eines Abonnementformulars zur PDP mithilfe [!DNL Adobe Commerce] Drop-in-Container und -Slots.

## Nächste Schritte

Verwenden Sie die folgenden Vorschläge, um Ihren Service für Benachrichtigungen auf Lager zu erweitern:

- **Senden echter Benachrichtigungen:** Ersetzen Sie die protokollbasierte Benachrichtigung durch einen E-Mail-Service, z. B. [!DNL Adobe Campaign] oder einen Drittanbieter.
- **Seite zur Abonnementverwaltung hinzufügen:** Erstellen Sie eine Storefront-Seite, auf der Käufer ihre aktiven Abonnements anzeigen und stornieren können.
- **Unterstützung von Multi-Mandanten-Bereitstellungen:** Erweitern Sie die Statusverwaltung, um mehrere Commerce-Mandanten in einer einzigen App Builder-App zu unterstützen.
- **Ratenbegrenzung hinzufügen:** Sie Ratenbegrenzungen in der Abonnement-API ein, um Missbrauch zu verhindern.
