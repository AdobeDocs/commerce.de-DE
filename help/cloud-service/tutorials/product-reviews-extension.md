---
title: Tutorial zur Erweiterung „Produktbewertungen“
description: Erfahren Sie, wie Sie mithilfe von App Builder, Edge Delivery Services und KI-unterstützten Entwicklungs-Tools Produktüberprüfungen und eine Erweiterung mit Fragen und Antworten für Adobe Commerce as a Cloud Service erstellen.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
hide: true
hidefromtoc: true
source-git-commit: 9c76bae29c05909406a40ca03a2b3d242db05f3f
workflow-type: tm+mt
source-wordcount: '2470'
ht-degree: 0%

---

# Tutorial zur Erweiterung „Produktbewertungen“

Dieses Tutorial führt Sie durch den Aufbau einer Erweiterung, mit der Kunden mithilfe von [!DNL Adobe Commerce as a Cloud Service]- und KI-unterstützten Entwicklungs-Tools Produktüberprüfungs- und Frage- und Antwortinhalte (Q&amp;A) für Storefronts mit einem [!DNL Adobe App Builder]-Backend senden können. Die Erweiterung bietet REST-API-Endpunkte, mit denen Käufer Inhalte zu Produktprüfungen und Fragen und Antworten (Q&amp;A) anzeigen und senden und auf der Produktdetailseite (PDP) anzeigen können.

Sie bauen zwei Teile:

- **App Builder-Erweiterung** - Eine REST-API mit GET- und POST-Vorgängen zum Erstellen und Anzeigen von Produktüberprüfungs- und Q&amp;A-Inhalten mit Validierung, Paginierung und Persistenz in `aio-lib-state`.
- **Storefront-Integration** - Ein Produktüberprüfungsblock in der PDP, der Bewertungen und Fragen und Antworten mit Formularen für Käufer anzeigt, um Bewertungen, Fragen und Antworten einzureichen.

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

- Sie haben eine [!DNL Adobe Commerce as a Cloud Service] mit Produktdaten. Siehe [Commerce Cloud Service-Instanzen](https://experienceleague.adobe.com/de/docs/commerce/cloud-service/overview){target="_blank"}.
- Sie haben ein Storefront-Projekt mit Ihrer [!DNL Commerce] verbunden. Wenn Sie noch keine haben, führen Sie die Schritte in [Erstellen einer Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/?lang=de){target="_blank"} aus.
- Die `aem` CLI wird installiert:

  ```bash
  npm install -g @adobe/aem-cli
  ```

## Entwicklung von Erweiterungen

Dieser Abschnitt führt Sie durch die Entwicklung einer Erweiterung zum Senden und Anzeigen von Produktüberprüfungs- und Q&amp;A-Inhalten für die Erweiterung für Storefronts mit einem [!DNL Adobe Commerce as a Cloud Service]-Backend mithilfe von KI-unterstützten Entwicklungs-Tools. Die Erweiterung bietet eine REST-API zum Senden und Anzeigen von Produktüberprüfungs- und Frageninhalten und zum Anzeigen derselben in der PDP.

1. Navigieren Sie zu den MCP-Einstellungen in Ihrem Codierungs-Agent. Gehen Sie beispielsweise im Cursor zu **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]**. Stellen Sie sicher, dass das `commerce-extensibility` Toolset fehlerfrei aktiviert ist. Wenn Fehler angezeigt werden, schalten Sie das Toolset aus und ein.

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
I want to build an Adobe Commerce as a Cloud Service extension that allows shoppers to submit and view product review and question and answer (Q&A) content that displays on product detail pages (PDP).

## Product Reviews
The application has REST API endpoints that can be called by a storefront to retrieve and submit product reviews for a given SKU.

The GET endpoint accepts the following query parameters:
- sku (string, required): The SKU of the product to fetch reviews for
- limit (integer, optional): The maximum number of reviews to return (default: 10)
- offset (integer, optional): The number of reviews to skip for pagination (default: 0)

The POST endpoint accepts the following JSON body parameters:
- sku (string, required): The SKU of the product to submit a review for
- rating (integer, required): The rating for the product (1-5)
- review (string, optional): The text of the review
- user (string, optional): The name of the user submitting the review

The POST endpoint validates the input and returns appropriate error responses for invalid data. The reviews are stored and associated with the corresponding product SKU.

## Questions and Answers
The application has REST API endpoints that can be called by a storefront to retrieve and submit questions and answers for a given SKU.

The GET endpoint accepts the following query parameters:
- sku (string, required): The SKU of the product to fetch questions and answers for
- limit (integer, optional): The maximum number of questions and answers to return (default: 10)
- offset (integer, optional): The number of questions and answers to skip for pagination (default: 0)

The POST endpoint accepts the following JSON body parameters:
- sku (string, required): The SKU of the product to submit a question or answer for
- type (string, required): The type of submission ("question" or "answer")
- questionId (string, required if type is "answer"): The ID of the question being answered
- content (string, required): The text of the question or answer
- user (string, optional): The name of the user submitting the question or answer

The POST endpoint validates the input and returns appropriate error responses for invalid data. The questions and answers are stored and associated with the corresponding product SKU. Answers are also associated with the corresponding question.

Do not require Adobe IMS authentication for these endpoints. They will be called directly from the storefront.

STOP and ask me any clarifying questions you have about the requirements before you do any work.
```

>[!TIP]
>
>Wenn Sie den Agenten auffordern, den Vorgang zu beenden und Fragen zu stellen, bevor Sie fortfahren, können Sie die Implementierung schon frühzeitig steuern. Dadurch wird sichergestellt, dass wichtige Annahmen und fehlende Anforderungen frühzeitig erkannt werden. Zudem ist dies erforderlich, um den in diesem Tutorial beschriebenen Workflow einzuleiten.

### Schritt 2: Beantworten der Fragen des Agenten

Der Agent gibt eine Reihe von Fragen zurück, die er beantworten muss, bevor er eine Lösung finden kann. Das folgende Beispiel zeigt typische Fragen und Antworten. Ihr Agent kann verschiedene Fragen stellen, aber die Themen sind im Allgemeinen dieselben.

**Beispielfragen für Agenten:**

1. **REST-API - Host und Verbraucher** - Soll die CRUD-REST-API Teil dieser App Builder-App (Web-Aktionen auf Adobe I/O Runtime) sein, die von Storefronts aufgerufen wird? Wer wird es nennen (EDS-Storefront, benutzerdefinierte/Headless-Storefront oder beides)? Benötigen Sie CORS, öffentlichen (nicht authentifizierten) Zugriff oder verwenden Anrufer API-Schlüssel oder OAuth?
1. **Datenmodell** - Was sollte eine „Überprüfung“ oder „Frage“ darstellen? Kundenkennung (nur E-Mail oder auch Kunden-ID)? Produktkennung (nur SKU oder SKU + Shop-Ansicht)? Kann ein und derselbe Kunde mehrere Bewertungen für dieselbe SKU einreichen?
1. **Persistenz** - Ist `aio-lib-state` der richtige Ort, um Rezensionen und Fragen und Antworten beizubehalten, oder haben Sie einen externen Store? Sollte das Design von mehreren Mandanten oder einem einzelnen Mandanten ausgehen?
1. GET **Paginierungssemantik** - Gilt `limit` für Fragen und Antworten mit Fragen nur für Fragen (mit verschachtelten Antworten) oder für die Gesamtzahl der Fragen plus Antworten?

**Beispielantworten:**

```shell-session
1. The REST API should be part of this App Builder app. It will be called by the EDS Storefront. No authentication — public access for both GET and POST.
2. For reviews: sku, rating (1-5), optional review text, optional user name. For Q&A: sku, type (question or answer), content, optional user. Answers linked to questions via questionId. Allow multiple reviews per SKU from the same user.
3. Use aio-lib-state. Single tenant for now.
4. Pagination by question — limit and offset apply to questions; each question includes its nested answers.
```

>[!NOTE]
>
>Ihr Agent stellt möglicherweise andere Fragen. Verwenden Sie diese Antworten als Anleitung, um den Agenten auf dasselbe funktionale Ergebnis hinzusteuern: eine öffentliche REST-API mit Überprüfungen und Fragen und Antworten, `aio-lib-state` Persistenz und keine Authentifizierung.

### Schritt 3: Anforderungen und Architektur überprüfen

Der Agent generiert Anforderungen und Architekturdokumente, die Sie überprüfen können. Stellen Sie sicher, dass die Anforderungen mit den von Ihnen angegebenen Antworten übereinstimmen und dass die Architektur Folgendes abdeckt:

- Vier Web-Aktionen: `reviews-get`, `reviews-post`, `qa-get`, `qa-post`
- Persistenz bei Verwendung von `aio-lib-state` mit Schlüsseln, die dem zulässigen Muster entsprechen (`[a-zA-Z0-9-_.]` - keine Doppelpunkte)
- Statuswerte werden als JSON-Zeichenfolgen gespeichert (keine rohen Objekte oder Arrays)
- Eigenständiges Paket - Freigegebener Code (Utils, Konstanten) innerhalb des `product-reviews`-Pakets, nicht über `../../` Pfade, die dem Bundle entgehen

>[!NOTE]
>
>KI-Agenten sind nicht deterministisch und ihr Verhalten unterscheidet sich je nach Modell und IDE. Möglicherweise erhalten Sie auch andere Fragen, die unterschiedliche Anforderungen und eine andere Architektur mit sich bringen. Wenn ja, versuchen Sie, den Agenten so in die Richtung zu lenken, dass die Implementierung eng mit dem übereinstimmt, was in diesem Tutorial vorgestellt wird, bevor Sie fortfahren.

### Schritt 4: Implementierungsplan auswählen

Der Agent bietet Ihnen die Möglichkeit, einen detaillierten Implementierungsplan zu erstellen oder eine direkte Implementierung abzuschließen.

- Wenn Sie einen überprüfbaren Plan wünschen, den Sie in Phasen mit mehr Kontrolle ausführen können, wählen Sie die erste Option aus.
- Wählen Sie die zweite Option aus, wenn der Agent die vollständige Implementierung mit minimalem Eingriff durchführen soll.

### Schritt 5: Bereitstellen der Erweiterung

Stellen Sie nach Abschluss der Implementierung durch den Agenten die Erweiterung bereit:

```bash
aio app deploy
```

Wenn der Agent `require-adobe-auth: true` zu den Aktionen hinzugefügt hat, bitten Sie ihn, die Authentifizierung zu entfernen, damit die Endpunkte direkt über die Storefront aufgerufen werden können:

```shell-session
Remove the requirement to provide a valid Adobe IMS access token from all product-reviews actions.
```

Dann erneut bereitstellen:

```bash
aio app deploy
```

### Schritt 6: Erstellen Sie Pseudo-Daten und füllen Sie sie vorab zum Testen aus.

Erstellen Sie eine Pseudo-Datendatei und verwenden Sie cURL zum Vorausfüllen der API, sodass Sie Beispielinhalte für Überprüfungen und Fragen zum Testen in der CLI und Storefront haben.

1. Erstellen Sie eine Datei `docs/mock-product-reviews-data.json` (oder Ähnliches) mit Beispieldaten. Beispiel:

   ```json
   {
     "reviews": [
       { "sku": "ADB153", "rating": 5, "review": "Great product, highly recommend!", "user": "shopper@example.com" },
       { "sku": "ADB153", "rating": 4, "review": "Good value for money.", "user": "buyer@example.com" }
     ],
     "questions": [
       { "sku": "ADB153", "type": "question", "content": "Does this come in other colors?", "user": "curious@example.com" }
     ]
   }
   ```

1. Verwenden Sie curl , um die Daten an Ihre bereitgestellte API zu senden.

   Ersetzen Sie `<your-runtime-url>` durch Ihre eigentliche App Builder-Laufzeit-URL (z. B. `https://1172492-prodreviewqa135-stage.adobeioruntime.net`):

   ```bash
   API_URL="https://<your-runtime-url>/api/v1/web/product-reviews"
   
   # Submit reviews
   curl -s -X POST "$API_URL/reviews-post" \
     -H "Content-Type: application/json" \
     -d '{"sku":"ADB153","rating":5,"review":"Great product, highly recommend!","user":"shopper@example.com"}'
   
   curl -s -X POST "$API_URL/reviews-post" \
     -H "Content-Type: application/json" \
     -d '{"sku":"ADB153","rating":4,"review":"Good value for money.","user":"buyer@example.com"}'
   
   # Submit a question (save the returned id for the answer)
   curl -s -X POST "$API_URL/qa-post" \
     -H "Content-Type: application/json" \
     -d '{"sku":"ADB153","type":"question","content":"Does this come in other colors?","user":"curious@example.com"}'
   
   # Submit an answer (replace <QUESTION-UUID> with the id from the question response)
   curl -s -X POST "$API_URL/qa-post" \
     -H "Content-Type: application/json" \
     -d '{"sku":"ADB153","type":"answer","questionId":"<QUESTION-UUID>","content":"Yes, it comes in blue and red.","user":"seller@example.com"}'
   ```

1. Überprüfen Sie die Daten mit GET-Anfragen:

   ```bash
   curl -s "$API_URL/reviews-get?sku=ADB153"
   curl -s "$API_URL/qa-get?sku=ADB153"
   ```

>[!TIP]
>
>Verwenden Sie SKU-`ADB153` für ein Produkt, das sowohl Review- als auch Frage- und `ADB152` enthält, sowie für ein Produkt ohne Bewertungen. Diese Datenkonfiguration ermöglicht das Testen sowohl ausgefüllter als auch leerer Status in der Storefront.

### Schritt 7: Erweiterung testen

Bitten Sie den Agenten, Testschritte bereitzustellen, oder verwenden Sie die cURL-Beispiele aus dem vorherigen Schritt. Die folgenden Beispiele zeigen typische Testbefehle.

**Eine Überprüfung einreichen:**

```bash
API_URL="https://<your-runtime-url>/api/v1/web/product-reviews"
curl -s -X POST "$API_URL/reviews-post" \
  -H "Content-Type: application/json" \
  -d '{"sku":"ADB153","rating":5,"review":"Excellent!","user":"test@example.com"}'
```

**Kundenbewertungen auflisten:**

```bash
curl -s "$API_URL/reviews-get?sku=ADB153"
```

**Frage einreichen:**

```bash
curl -s -X POST "$API_URL/qa-post" \
  -H "Content-Type: application/json" \
  -d '{"sku":"ADB153","type":"question","content":"Is this dishwasher safe?","user":"test@example.com"}'
```

**Antwort senden** (Verwenden Sie wie `id` die `questionId` aus der Fragebogenantwort):

```bash
curl -s -X POST "$API_URL/qa-post" \
  -H "Content-Type: application/json" \
  -d '{"sku":"ADB153","type":"answer","questionId":"<QUESTION-UUID>","content":"Yes, it is.","user":"support@example.com"}'
```

### Servicevertrag erstellen

Nachdem die Service-Implementierung abgeschlossen ist, bitten Sie den Agenten, einen Service-Vertrag für die Arbeit an der Storefront zu erstellen:

```shell-session
Create a service contract for the Product Review and Q&A application that defines the API endpoints, request and response formats, and any necessary data models. Ensure that the service contract is clear and detailed enough for a frontend developer to implement the storefront integration without needing to ask additional questions about the API. Name this file PRODUCT_REVIEW_QA_CONTRACT.md
```

Kopieren Sie diese Datei in Ihr Storefront-Projekt, damit der Storefront-Agent darauf verweisen kann.

## Verbindung zur Storefront herstellen

Dieser Abschnitt führt Sie durch die Implementierung des Storefront-Teils der Produktbewertungen und der Q&amp;A-Erweiterung mithilfe von [!DNL Edge Delivery Services] und KI-unterstützten Entwicklungs-Tools. Sie fügen dem PDP einen Produktüberprüfungsblock hinzu, der sowohl Überprüfungs- als auch Frageninhalte anzeigt und es Käufern ermöglicht, neue Inhalte einzureichen.

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
- Die `PRODUCT_REVIEW_QA_CONTRACT.md`-Datei wurde in Ihr Storefront-Projekt kopiert

### Schritt 1: Validieren der Umgebung

Öffnen Sie die `config.json` und stellen Sie sicher, dass die Werte für `commerce-core-endpoint` und `commerce-endpoint` auf Ihren [!DNL Adobe Commerce as a Cloud Service] GraphQL-Endpunkt verweisen.

```json
"commerce-core-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
```

### Schritt 2: Eingeben der ersten Eingabeaufforderung

Wenn der Service-Vertrag bereits in Ihrem Projekt vorhanden ist, fordern Sie den Support-Mitarbeiter auf, den Produktüberprüfungsblock zu implementieren. Verwenden Sie **Plan**-Modus, falls in Ihrem Agenten verfügbar, um zu verhindern, dass der Agent ohne Plan fortfährt.

```shell-session
Analyze @PRODUCT_REVIEW_QA_CONTRACT.md and build a product review block using the API specified in the contract. The block displays both reviews and Q&A content on the product detail page, with forms for shoppers to submit reviews, questions, and answers. Use the project manager skill to plan this implementation.
```

>[!TIP]
>
>Insbesondere die Anforderung, die Projektmanager-Kenntnisse-Trigger für den stufenweisen Workflow zu verwenden, der Ihnen bei der Steuerung der Implementierung hilft. Dadurch wird sichergestellt, dass wichtige Annahmen und fehlende Anforderungen frühzeitig erkannt werden.

### Schritt 3: Klärende Fragen beantworten

Der Agent gibt eine Reihe von Fragen zurück, die er beantworten muss, bevor er eine Lösung finden kann. Das folgende Beispiel zeigt typische Fragen und Antworten. Ihr Agent kann verschiedene Fragen stellen, aber die Themen sind im Allgemeinen dieselben.

**Beispielfragen für Agenten:**

1. **API-Basis-URL** - Wie sollte die Storefront die API-Basis-URL für Produktprüfungen abrufen? Zu den Optionen können ein Konfigurationsblock (z. B. eine Tabelle mit `apiBaseUrl`), globale Platzhalter oder ein anderer Ansatz gehören.
1. **SKU-Quelle** - Soll der Block die SKU aus dem PDP-Kontext (aktuelles Produkt) oder aus der Blockkonfiguration lesen?
1. **Formularverhalten** - Soll das Formular nach erfolgreicher Übermittlung ausgeblendet, eine Erfolgsmeldung angezeigt oder sichtbar, aber deaktiviert bleiben?

**Beispielantworten:**

```shell-session
1. Block table config with apiBaseUrl (required). Each block instance can point to its own deployment.
2. From block table if set; otherwise use getProductSku() so it works on PDP without authoring a SKU.
3. Show a success message above the form; keep the form visible but disabled.
```

>[!NOTE]
>
>Ersetzen Sie den Platzhalter in der Blockkonfiguration durch Ihre eigentliche App Builder-Laufzeit-URL (z. B. `https://1172492-prodreviewqa135-stage.adobeioruntime.net`).
>
>Ihr Agent stellt möglicherweise andere Fragen. Verwenden Sie diese Antworten als Anleitung:
>
>- Die API-Basis-URL sollte aus der Blocktabelle stammen, damit sie ohne Code-Änderungen geändert werden kann.
>- SKU aus Blocktabelle, falls festgelegt; andernfalls aus dem aktuellen Produkt in der PDP.
>- Nach erfolgreicher Übermittlung eine Erfolgsmeldung anzeigen und das Formular deaktivieren.

### Schritt 4: Anforderungen und Architektur überprüfen

Der Agent aktualisiert das Anforderungsdokument, damit Sie es überprüfen können. Überprüfen Sie, ob:

- Der Block rendert Bewertungen (mit Bewertung, Benutzer, Datum, Text) und Fragen und Antworten (mit verschachtelten Antworten).
- Forms ist für die Einreichung von Bewertungen, Fragen und Antworten vorgesehen.
- Die Paginierung wird sowohl für Überprüfungs- als auch für Frageninhalte unterstützt.
- Die API-Integration verwendet die Basis-URL aus der Blocktabelle.
- Erfolgs- und Fehlerstatus werden vertragsgemäß behandelt.

>[!NOTE]
>
>KI-Agenten sind nicht deterministisch und ihr Verhalten unterscheidet sich je nach Modell und IDE. Möglicherweise erhalten Sie auch andere Fragen, die unterschiedliche Anforderungen und eine andere Architektur mit sich bringen. Wenn ja, versuchen Sie, den Agenten so in die Richtung zu lenken, dass die Implementierung eng mit dem übereinstimmt, was in diesem Tutorial vorgestellt wird, bevor Sie fortfahren.

### Schritt 5: Implementierungsplan auswählen

Der Agent bietet Ihnen die Möglichkeit, einen detaillierten Implementierungsplan zu erstellen oder eine direkte Implementierung abzuschließen.

- Wenn Sie einen überprüfbaren Plan wünschen, den Sie in Phasen mit mehr Kontrolle ausführen können, wählen Sie die erste Option aus.
- Wählen Sie die zweite Option aus, wenn der Agent die vollständige Implementierung mit minimalem Eingriff durchführen soll.

Während der Implementierung erstellt und ändert der Agent Blockdateien. Beobachten Sie, wie der Code generiert wird, und stellen Sie Fragen oder leiten Sie den Agenten nach Bedarf weiter. Wenn der Block nicht gerendert wird, bitten Sie den Agenten, das Schnittdekorations- und Blockerkennungsmuster zu analysieren. Das Blockelement muss dem Abschnitt direkt untergeordnet sein, damit das Framework ihn finden kann.

### Schritt 6: Hinzufügen des Blocks zur Produktseite beim Erstellen von Dokumenten

Fügen Sie den Produktüberprüfungsblock zur Produktseitenvorlage hinzu, damit er in allen PDPs angezeigt wird. Verwenden Sie den Document Authoring-Service (da.live), um den Block hinzuzufügen und zu konfigurieren.

1. Öffnen Sie den Dokumenterstellungsdienst, z. B[&#x200B; „da.live](https://da.live/)

1. Klicken Sie auf Ihren Projektbereich, öffnen Sie den Ordner **Produkte** und wählen Sie **Standard** (`products/default`) aus.

1. Neuen Blockabschnitt hinzufügen.

   Fügen Sie der Blocktabelle eine Zeile mit dem Blocknamen (**-product-review** (oder dem Blocknamen, den Ihr Agent erstellt hat) hinzu.

1. Konfigurieren Sie den Block mit den erforderlichen Einstellungen:
   - **apiBaseUrl** - Ihre App Builder-Runtime-URL (z. B. `https://<namespace>-<app-name>-stage.adobeioruntime.net`)
   - **sku** - Lassen Sie das Feld leer, um die SKU des aktuellen Produkts in der PDP zu verwenden, oder geben Sie eine bestimmte SKU ein, um nur Bewertungen für dieses Produkt anzuzeigen.

1. Klicken Sie auf **[!UICONTROL Publish]** , um Ihre Änderungen zu veröffentlichen.

### Schritt 7: Server starten und testen

Nachdem Sie den Block zur Produktseite im Dokumenterstellungsprozess hinzugefügt haben, starten Sie den Entwicklungs-Server und testen Sie den Block.

1. Starten Sie den lokalen Entwicklungs-Server:

   ```bash
   npm run start
   ```

1. Navigieren Sie in einem Browser zu einer Produktseite, die vorausgefüllte Reviews und Fragen enthält. Beispiel:

   ```shell-session
   http://localhost:3000/products/<product-slug>/ADB153
   ```

1. Überprüfen Sie, ob der Produktüberprüfungsblock Prüf- und Q&amp;A-Inhalte anzeigt und ob die Übermittlungsformulare funktionieren.

Sie können manuelle Tests durchführen oder den Agenten bitten, seine Browser-Funktionen zum Testen für Sie zu verwenden:

```shell-session
Run complete browser testing. Use the following product page 'http://localhost:3000/products/<product-slug>/ADB153'
```

### Schritt 8: Bereinigen

Nachdem Sie den Test übersprungen oder abgeschlossen haben, werden Sie vom Agenten aufgefordert, mit der letzten Phase **Bereinigung** fortzufahren. Nach der Bestätigung archiviert der Agent alle während der Implementierung erstellten Dokumentationsartefakte.

## Fehlerbehebung

Verwenden Sie die folgenden Tipps, wenn während des Tutorials Probleme auftreten.

### Backend (App Builder)

| Symptom | Ursache | Fehlerbehebung |
|---------|-------|-----|
| GET oder POST gibt 500 „Modul wurde nicht gefunden“ zurück | Die Aktionen zur Produktüberprüfung verwenden `require("../../utils")` oder `require("../../constants")`, die dem Paket entzogen sind. Diese Dateien sind bei der Bereitstellung des Pakets nicht enthalten. | Machen Sie das Paket mit den Produktbewertungen eigenständig. Fügen Sie `actions/product-reviews/lib/constants.js` und `actions/product-reviews/lib/utils.js` hinzu und aktualisieren Sie alle vier Aktionen so, dass sie von `../lib/...` anstelle von `../../` angefordert werden. |
| GET gibt 500 mit der Zeichenfolge „Schlüssel muss dem Muster entsprechen“ zurück. | Bei Statusschlüsseln werden Doppelpunkte verwendet (z. B. `reviews:ADB153`). `aio-lib-state` erlaubt nur `[a-zA-Z0-9-_.]`. | Ändern Sie Präfixe von `reviews:` und `qa:` in `reviews.` und `qa.`. Fügen Sie einen `stateKey(prefix, sku)` Helper hinzu, der die SKU bereinigt (ersetzen Sie ungültige Zeichen durch `_`). |
| POST gibt 500 mit „Wert muss Zeichenfolge sein“ zurück. | `aio-lib-state` akzeptiert nur Zeichenfolgenwerte. Der Code übergibt Arrays oder Objekte an `state.put()`. | Serialisieren mit `JSON.stringify()` beim Schreiben und `JSON.parse()` beim Lesen. Aktualisieren Sie alle vier Aktionen. |

{style="table-layout:auto"}

### Storefront (Edge Delivery Services)

| Symptom | Ursache | Fehlerbehebung |
|---------|-------|-----|
| Block wird auf Testseite nicht gerendert | Das Blockelement ist in einem zusätzlichen `div` verschachtelt, sodass die Blockauswahl (`decorateSections`) nach dem `div.section > div > div` nicht übereinstimmt. | Definieren Sie den Block als direktes untergeordnetes Element des Abschnitts. Struktur: `section > div.product-review` (oder entsprechende Blockklasse). Vermeiden Sie `section > div > div.product-review`. |
| Ungültige CSS-Token | Der Block verwendet Design-Token, die in `styles/styles.css` nicht vorhanden sind (z. B. `--color-error-100`, `--type-detail-font-size`). | Bitten Sie den Agenten, Token anhand der `styles/styles.css` des Projekts zu validieren und ungültige Token durch vorhandene zu ersetzen (z. B. `--color-alert-*`, `--type-details-caption-*`). |

{style="table-layout:auto"}

## Tutorial-Zusammenfassung

Im Folgenden finden Sie eine Zusammenfassung der Themen, die in diesem Tutorial behandelt werden:

- **Erweiterungsentwicklung:** Beschreibung der Funktion zum Erstellen und Anzeigen von Produktüberprüfungs- und Frageninhalten in einer Storefront mit einem Adobe Commerce as a Cloud Service-Backend für einen KI-Agenten und wie diese Funktion implementiert wird, indem eine funktionierende REST-API mit vier Endpunkten mithilfe von [!DNL App Builder] generiert wird.
- **Persistenz:** Verwenden von `aio-lib-state` mit dem richtigen Schlüsselformat und serialisierten JSON-Werten.
- **Pseudo-Daten und Vorausfüllen:** Erstellen einer Pseudo-Datendatei und Verwenden von cURL zum Vorausfüllen der API für CLI- und Storefront-Tests.
- **Dienstverträge:** von API-Verträgen, die Backend-Erweiterungen und Storefront-Implementierungen überbrücken.
- **Schrittweise Storefront-Integration:** Anforderungen, Architektur und Implementierung mithilfe von KI-unterstützten Fähigkeiten durcharbeiten.
- **PDP-Block:** Hinzufügen eines Produktüberprüfungsblocks zur PDP, der Überprüfungen und Fragen mit Übermittlungsformularen und Paginierung anzeigt.

## Nächste Schritte

Verwenden Sie die folgenden Vorschläge, um Ihren Service für Produktbewertungen zu erweitern:

- **Moderation hinzufügen** Implementieren eines Moderations-Workflows zur Überprüfung und Beantwortung von Fragen und Antworten vor der Veröffentlichung.
- **Authentifizierung hinzufügen** Erfordert, dass Käufer angemeldet sind, um Bewertungen oder Fragen und Antworten zu senden und Einreichungen mit Kundenkonten zu verknüpfen.
- **Abonnement-Verwaltungsseite hinzufügen:** Erstellen Sie eine Storefront-Seite, auf der Käufer ihre Bewertungen anzeigen und bearbeiten können.
- **Unterstützung von Multi-Mandanten-Bereitstellungen:** Erweitern Sie die Statusverwaltung, um mehrere Commerce-Mandanten in einer einzigen App Builder-App zu unterstützen.
- **Ratenbegrenzung hinzufügen:** Sie Ratenbegrenzungen in der API ein, um Missbrauch zu verhindern.
