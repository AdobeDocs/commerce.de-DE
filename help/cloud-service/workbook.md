---
title: Tutorial zur Bewertungserweiterung
description: Erfahren Sie, wie Sie mithilfe von App Builder und KI-unterstützten Entwicklungstools eine Produktbewertungserweiterung für Adobe Commerce as a Cloud Service erstellen.
role: Developer
hide: true
hidefromtoc: true
source-git-commit: 453b21f89d2024a8d6927fa082affdd5abb6e5cd
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 0%

---

# Adobe Developers Live - Adobe Commerce Lab-Arbeitsmappe

Dieses Labor führt Sie durch den Aufbau einer Produktbewertungserweiterung für [!DNL Adobe Commerce as a Cloud Service] mithilfe von [!DNL Adobe App Builder] und KI-unterstützten Entwicklungstools.

## Voraussetzungen überprüfen

Überprüfen Sie, ob die folgenden Voraussetzungen installiert sind:

```bash
# Check Node.js version (should be 22.x.x)
node --version

# Check npm version (should be 9.0.0 or higher)
npm --version

# Check Git
git --version

# Check Bash
bash --version
```

## Melden Sie sich bei Adobe Developer Console an

1. Navigieren Sie zur [Adobe Developer Console](https://developer.adobe.com/console){target="_blank"}.
1. Wenn Sie bereits angemeldet sind, klicken Sie oben rechts auf Ihr Profilsymbol und dann auf die Schaltfläche **Abmelden**.
1. Melden Sie sich mit der Lab-E-Mail-ID und dem Passwort Ihres Sitzplatzes an.
1. Wenn Sie zum Hinzufügen einer sekundären E-Mail-Adresse oder Telefonnummer aufgefordert werden, klicken Sie auf **Jetzt nicht**.
1. Wenn Sie zum Auswählen eines Unternehmensprofils aufgefordert werden, wählen Sie **Adobe Commerce Labs** aus.

   ![select-organization](./assets/select-org.png){width="600" zoomable="yes"}

1. Wenn Sie aufgefordert werden, die Nutzungsbedingungen zu akzeptieren, klicken Sie auf den Link, um die Nutzungsbedingungen zu lesen. Klicken Sie dann auf **Akzeptieren und fortfahren**.

   ![Accept-Terms](./assets/accept-terms.png){width="600" zoomable="yes"}

## Ausführen des Setupskripts

Wenn die [Voraussetzungen](#verify-prerequisites) installiert sind und Sie sich bei der Adobe Developer Console angemeldet haben, laden Sie das Setup-Skript herunter und führen Sie es aus. Alternativ können Sie das Skript manuell einrichten, indem Sie die Schritte [Lab-Voraussetzungen](workbook-prerequisites.md) befolgen.

1. Klonen Sie das Repository, das das Setup-Skript enthält:

   ```bash
   git clone https://github.com/adobe-commerce/commerce-adl-2025.git
   ```

   >[!NOTE]
   >
   >Wenn das Skript fehlschlägt, verweisen Sie auf die [Voraussetzungen](workbook-prerequisites.md) und setzen Sie den Vorgang fort, bei dem das Skript einen Fehler festgestellt hat.

1. Navigieren Sie zum Repository:

   ```bash
   cd commerce-adl-2025
   ```

1. Ausführen des Setup-Skripts:

   ```bash
   bash adl-setup.sh
   ```

   Während das Skript ausgeführt wird, werden Sie aufgefordert, Ihren Benutzernamen und Ihr Kennwort einzugeben, die während des Labors bereitgestellt werden. Ihr Benutzername wird Ihre Standort- und Sitznummer widerspiegeln. Wenn Sie sich beispielsweise in San Jose, CA, mit Platz 123 befinden, wird Ihr Benutzername `sjc-adl-123@adobeeventlab.com`.

   Darüber hinaus sollten Sie das Projekt auswählen, das Ihrer Sitznummer und dem Arbeitsbereich **Phase** entspricht. Ihr Projektname wird Ihre Standort- und Sitznummer widerspiegeln. Wenn Sie sich beispielsweise in San Jose, CA, mit Platz 123 befinden, wird Ihr Projektname `SJC ADL 123`.

## Entwicklung von Erweiterungen

Dieser Abschnitt führt Sie durch den Prozess der Entwicklung einer Bewertungserweiterung für Adobe Commerce as a Cloud Service mithilfe von KI-unterstützten Entwicklungstools.

### Installieren von Erweiterbarkeits-KI-Tools

Richten Sie die KI-unterstützten Entwicklungs-Tools im Ordner `extension` ein:

```bash
cd extension
```

```bash
aio commerce extensibility tools-setup
```

![KI-Tools installieren](./assets/install-ai-tools.png){width="600" zoomable="yes"}

### Cursor öffnen

>[!NOTE]
>
>Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools gibt es natürliche Variationen im Code und den vom Agenten generierten Antworten.
>Wenn Probleme mit dem Code auftreten, können Sie den Agenten jederzeit um Hilfe beim Debuggen bitten.

Öffnen Sie die [!DNL Cursor] und navigieren Sie zum Ordner `extension`. Wenn Sie die [Cursor-CLI](https://cursor.com/docs/configuration/shell#installing-cli-commands) installiert haben, geben Sie den folgenden Befehl an Ihrem Terminal ein:

```bash
cursor .
```

![Cursor öffnen](./assets/open-cursor.png){width="600" zoomable="yes"}

Zu diesem Zeitpunkt sind alle [!DNL Cursor] im Ordner `.cursor/rules` installiert. MCP-Tools finden Sie in den **MCP-Einstellungen** in [!DNL Cursor]. Stellen Sie sicher, dass das `commerce-extensibility` Toolset fehlerfrei aktiviert ist. Wenn Fehler angezeigt werden, schalten Sie das Toolset aus und ein.

![Cursoreinstellungen](./assets/cursor-settings.png){width="600" zoomable="yes"}

Wenn Sie eine Dokumentation zum Kontext des Cursors hinzugefügt haben, müssen Sie sie deaktivieren. Navigieren Sie zu [!UICONTROL **Cursor**] > [!UICONTROL **Einstellungen**] > [!UICONTROL **Cursor-Einstellungen**] > [!UICONTROL **Indizierung und Dokumente**] und löschen Sie alle aufgelisteten Dokumentationen.

![Dokumentation deaktivieren](./assets/disable-documentation.png){width="600" zoomable="yes"}

### Codegenerierung

In diesem Abschnitt wird die Verwendung von KI-unterstützten Tools zum Generieren von Code für eine Produktbewertungserweiterung veranschaulicht.

#### Anforderungen definieren

Sie werden eine Erweiterung implementieren, die Produktbewertungen als API dient. Die [!DNL App Builder]-Erweiterung antwortet mit Bewertungsdetails für eine bestimmte SKU.

**Anfängliche Eingabeaufforderung:**

Verwenden Sie die folgende Eingabeaufforderung in [!DNL Cursor]:

1. Öffne das Chat-Fenster im Cursor.
1. Wählen Sie den **Agent** Modus aus.
1. Geben Sie die folgende Eingabeaufforderung ein:

   ```text
   Implement an Adobe Commerce as a Cloud Service extension to handle Product Ratings.
   Implement a REST API to handle GET ratings requests.
   GET requests will have to support the following query parameters:
   
   sku -> product SKU
   ```

1. Wenn der Agent eine Suche in der Dokumentation anfordert, lassen Sie diese zu.

![Eingabeaufforderung im Cursor eingeben](./assets/enter-prompt.png){width="600" zoomable="yes"}

Der Agent recherchiert die Anforderungen und stellt klärende Fragen. Beantworten Sie die Fragen des Agenten genau, damit er den besten Code generieren kann.

![Agent stellt klärende Fragen](./assets/agent-questions.png){width="600" zoomable="yes"}

**Eingabeaufforderung:**

Antworten Sie mit der folgenden Antwort auf die Fragen des Agenten:

```text
Yes, this headless extension is for Adobe Commerce as a Cloud Service storefront,
but we do not need any authentication for the GET API because guest users should be able to use it on the storefront.
This extension will be called directly from the storefront,
no async invocation, such as events or webhooks, is required.
Let's start with just the GET API for now,
we will implement other CRUD operations at a later time.
We do not need a DB or storage mechanism right now,
just return random ratings data between 1 and 5 and a ratings count between 1 and 1000.
The API should only return the average rating for the product and the total number of ratings.
We do not need to add tests right now.
```

Der Agent erstellt eine `requirements.md`-Datei, die als Datenquelle für die Implementierung dient.

![Anforderungsdatei erstellt](./assets/requirements-file.png){width="600" zoomable="yes"}

#### Überprüfen der Anforderungen und Planarchitektur

1. Überprüfen Sie die `requirements.md`.
1. Wenn alles korrekt aussieht, weisen Sie den Agenten an, zu **Phase 2 - Architekturplanung** zu wechseln.
1. Überprüfen Sie den Architekturplan.
1. Weisen Sie den Agenten an, mit der Code-Generierung fortzufahren.

![Architekturplanung](./assets/architecture-planning.png){width="600" zoomable="yes"}

#### Code generieren

Der Agent generiert den erforderlichen Code und stellt eine detaillierte Zusammenfassung der nächsten Schritte bereit.

![Zusammenfassung der Code-Erstellung](./assets/code-generation-summary.png){width="600" zoomable="yes"}

![Nächste Schritte](./assets/next-steps.png){width="600" zoomable="yes"}

### Lokale Tests

Bitten Sie den Agenten, Ihnen beim lokalen Testen des Codes zu helfen.

```text
Test the ratings API locally on a dev server using cURL.
```

Befolgen Sie die Anweisungen des Agenten und bestätigen Sie, dass die API lokal funktioniert.

![Lokale Tests](./assets/local-testing.png){width="600" zoomable="yes"}

![Lokale Testergebnisse](./assets/local-testing-1.png){width="600" zoomable="yes"}

### Bereitstellen der Erweiterung

Nachdem Sie den generierten Code überprüft haben, können Sie die Erweiterung über die folgende Eingabeaufforderung bereitstellen:

```text
Deploy the ratings API.
```

#### Bewertung vor der Bereitstellung

Der Agent führt vor der Bereitstellung eine Bewertung der Bereitschaft durch.

![Bewertung vor der Bereitstellung](./assets/pre-deployment-assessment.png){width="600" zoomable="yes"}

#### Bereitstellen

Wenn Sie mit den Bewertungsergebnissen vertraut sind, weisen Sie den Agenten an, mit der Bereitstellung fortzufahren. Der Agent verwendet das MCP-Toolkit, um automatisch zu überprüfen, zu erstellen und bereitzustellen.

![Bereitstellung](./assets/deployment-process.png){width="600" zoomable="yes"}

### Testen der API

Sie können die API testen, bevor Sie sie in die Storefront integrieren.

Der Agent gibt den Speicherort der neuen Aktion und eine Teststrategie an.

![Teststrategie](./assets/testing-strategy.png){width="600" zoomable="yes"}

#### Manuelles Testen mit cURL

Testen Sie die API manuell mit cURL in einem Terminal:

```bash
curl -s "https://<your-site>.adobeioruntime.net/api/v1/web/ratings/ratings?sku=TEST-SKU-123"
```

![cURL-Test](./assets/curl-test.png){width="600" zoomable="yes"}

### Integration mit Edge Delivery Services

Um die Bewertungs-API in eine von [!DNL Adobe Commerce] unterstützte [!DNL Edge Delivery Services]-Storefront zu integrieren, bitten Sie den Agenten, einen Service-Vertrag mit den Anforderungen für die Bewertungs-API zu erstellen:

```text
Create a service contract for the ratings api that I can pass on to the storefront agent. Name it RATINGS_API_CONTRACT.md
```

![Servicevertrag](./assets/create-contract.png){width="600" zoomable="yes"}

![Details zum Servicevertrag](./assets/contract.png){width="600" zoomable="yes"}

Kehren Sie zum Terminal zurück und führen Sie den folgenden Befehl im Ordner `extension` aus, um die Datei in den Ordner `storefront` zu kopieren:

```bash
cp RATINGS_API_CONTRACT.md ../storefront
```

## Verbindung zur Storefront herstellen

Dieser Abschnitt hilft Ihnen bei der Implementierung echter Storefront-Funktionen und zeigt Ihnen, wie Sie bei der Arbeit mit [!DNL Adobe Commerce] Dropins und [!DNL Edge Delivery Services] effektiv mit KI-Agenten kommunizieren können.

>[!NOTE]
>
>Die angezeigten Eingabeaufforderungen sind Ausgangspunkte. Sie sollten sich frei fühlen, ein natürliches Gespräch mit dem Agenten zu führen. Bei der Arbeit mit KI-unterstützten Entwicklungs-Tools gibt es natürliche Variationen im Code und den vom Agenten generierten Antworten.
>
>Wenn Probleme mit dem Code auftreten, können Sie den Agenten jederzeit um Hilfe beim Debuggen bitten.

### Bewertungssterne implementieren und Anzahl der Überprüfungen

1. Navigieren Sie zum Ordner `storefront` :

   ```bash
   cd storefront
   ```

1. Öffnen Sie den Ordner „Storefront“ in einem neuen Cursor-Fenster. Wenn Sie die [Cursor-CLI](https://cursor.com/docs/configuration/shell#installing-cli-commands) installiert haben, geben Sie den folgenden Befehl an Ihrem Terminal ein:

   ```bash
   cursor .
   ```

1. Starten Sie den lokalen Entwicklungs-Server:

   ```bash
   npm run start
   ```

1. Navigieren Sie in einem Browser zur Bekleidungsseite:

   ```text
   http://localhost:3000/apparel
   ```

1. Beachten Sie das Layout der Textbausteinfront-Benutzeroberfläche.

1. Verwenden Sie die folgende Eingabeaufforderung mit Ihrem Agenten:

   ```text
   Implement product ratings to the storefront.
   Add a 5-star rating display with a review count underneath each product name on the product list page, product details page, and product recommendations.
   Use the dropin slot system where available.
   
   Use the @RATINGS_API_CONTRACT.md to understand how to use the ratings api.
   ```

   >[!NOTE]
   >
   >Wenn Sie aufgefordert werden, den lokalen Entwicklungs-Server zu starten, informieren Sie den Agenten darüber, dass er bereits ausgeführt wird.

1. Beobachten Sie die Änderungen in der Code-Basis und sehen Sie sich die Seite Bekleidung für Aktualisierungen an.

**Erwartetes Ergebnis:**

* Eine Produktbewertung „Komponente“ wird automatisch erstellt.
* Die Komponente wird mithilfe von Steckplätzen in Produktdetails, Produktlistenseite und Produktempfehlungsblöcke integriert.
* Sterne werden mit korrekten Füllverhältnissen basierend auf Pseudo-Bewertungswerten angezeigt.

![Implementierung von Produktbewertungen](./assets/product-ratings-implementation.png){width="600" zoomable="yes"}

### Sternenfarben ändern

Verwenden Sie die folgende Eingabeaufforderung, um Ihren Agenten zu kontaktieren:

```text
Change the star fill color to red.
```

**Erwartetes Ergebnis:**

Die Sterne werden rot.

![Rote Sternenfarben](./assets/red-star-colors.png){width="600" zoomable="yes"}

## Zusammenfassung der Storefront

In diesem Tutorial haben wir die folgenden Themen behandelt:

* **Funktionsimplementierung**: Beschreibung neuer Funktionen für einen KI-Agenten.
* **Iterative Änderungen**: Schnelle Änderungen am vorhandenen Code.
* **Komplexe UI-Komponenten**: Erstellen interaktiver Funktionen mit visuellen Verweisen.
* **Dropin-Integration**: Arbeiten mit [!DNL Adobe Commerce] Dropin-Containern und -Slots.
* **Wiederverwendbarkeit von Komponenten**: Erstellen freigegebener Komponenten, die in mehreren Blöcken verwendet werden.

## Nächste Schritte

Wenn die Zeit es zulässt, können Sie Ihre Bewertungserweiterung weiter anpassen, indem Sie die folgenden Funktionen hinzufügen:

### Modal für die Bewertungsverteilung hinzufügen (optional)

Die folgenden Schritte zeigen, wie der Agent komplexe Benutzeroberflächenfunktionen mit visuellen Verweisen verarbeitet.

1. **Vor dem Start:** Speichern Sie das folgende Pseudo-Bild und fügen Sie es in den Chat mit Ihrem Storefront-Agenten ein.

   ![Rating Distribution Mockup](./assets/rating-distribution-mockup.png){width="600" zoomable="yes"}

1. Führen Sie die folgenden Schritte aus, um das Modal „Bewertungsverteilung“ basierend auf dem Referenzbild zu erstellen:

   * Aktualisieren Sie die -API, um zusätzliche Daten zur Verteilung der Bewertungen zurückzugeben.
   * Aktualisieren Sie den API-Vertrag.
   * Aktualisieren Sie den Kontakt in der Code-Basis der Storefront.
   * Bitten Sie den Storefront-Agenten, das Referenzbild und den aktualisierten API-Vertrag zu verwenden, um die Bewertungsverteilung zur PDP-Seite hinzuzufügen.

1. Sehen Sie sich die folgenden Änderungen in der Codebasis an und suchen Sie auf der Bekleidungsseite nach Aktualisierungen:

   * Interpretation des visuellen Mockups durch den Agenten
   * Ob eine geeignete HTML-Struktur für Barrierefreiheit verwendet wird
   * Handhabung der Positionierungs- und Interaktionsstatus

**Fehlerbehebung:**

* Wenn das Modal nicht angezeigt wird, überprüfen Sie die Browser-Konsole auf Fehler.
* Wenn die Positionierung deaktiviert ist, können Sie den Agenten bitten:

  ```text
  adjust the modal position to be...
  ```

![Rating-Verteilung Modal](./assets/rating-distribution-modal.png){width="600" zoomable="yes"}
