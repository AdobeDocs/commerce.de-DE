---
title: Erste Schritte
description: Erfahren Sie mehr über die ersten Schritte mit [!DNL Adobe Commerce Optimizer].
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: de57d93d-e156-45c1-86aa-de29a8c34bd2
TQID: https://experienceleague.adobe.com/1dcKMjOut1GtiOevvGJECsaU7URFmYg-mQ-m9wi7n4Y
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
subfeature_v2:
  - id: f8ddfd3b-6194-46e8-a176-0e918039be56
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: dba482e5-29a8-4127-afa2-c4b913512ef8
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 423b35b15e845e49b1cf36910ffbad775de9758c
workflow-type: tm+mt
source-wordcount: 1332
ht-degree: 0%

---

# Erste Schritte

Diese Anleitung führt Sie durch die Einrichtung von [!DNL Adobe Commerce Optimizer] von Anfang bis Ende. Dieses Handbuch deckt zwar alle Rollen ab, doch finden [&#x200B; in der &#x200B;](https://developer.adobe.com/commerce/services/optimizer/) für Entwickler detaillierte Informationen zu den jeweiligen Inhalten.

## Instanztypen und Umgebungsisolierung

Adobe Commerce Optimizer verwendet separate Instanzen für verschiedene Umgebungen wie **Sandbox** und **Produktion**. Jede Instanz verfügt über eine eigene Instanz-ID und eigene isolierte Daten, einschließlich Katalogansichten, Richtlinien, Suchkonfiguration und Produktempfehlungen.

Bei der Integration mit Adobe Commerce as a Cloud Service stimmen Commerce-Plattformen von Drittanbietern oder Edge Delivery Services-Storefronts immer mit den Umgebungen überein:

- Verbinden Sie **Sandbox Optimizer-**) mit Nicht-Produktions-Commerce- und Storefront-Umgebungen.
- Verbinden **Produktions-Optimizer-Instanzen** mit Produktions-Commerce- und Storefront-Umgebungen.

Das Mischen von Sandbox-Umgebungen mit Produktionsumgebungen führt zu inkonsistenten Katalogdaten, unerwartetem Such- und Merchandising-Verhalten und unzuverlässigen Metriken. Verwenden Sie bei der Konfiguration von Integrationen den Instanztyp und die Instanz-ID in Commerce Cloud Manager als Informationsquelle.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie Folgendes sicher:

- **Adobe Experience Cloud-** mit [!DNL Adobe Commerce Optimizer] Berechtigungen
- **Organisations-Administratorzugriff** um Instanzen zu erstellen und Benutzer zu verwalten
- **GitHub-Konto** zum Laden von Beispieldaten und für die Storefront-Entwicklung
- **Grundlegendes** E-Commerce-Konzepte

## Schnellstartanleitung

Führen Sie die folgenden Schritte aus, um Ihre [!DNL Adobe Commerce Optimizer]-Umgebung zum Laufen zu bringen:

### Schritt 1. Instanz erstellen

1. Anmelden bei [Adobe Experience Cloud](https://experience.adobe.com/).
1. Navigieren Sie zu **Commerce** > **Commerce Cloud Manager**.
1. Klicken Sie **Instanz hinzufügen** > **Commerce Optimizer**.

   ![Adobe Commerce Cloud Manager-Bildschirm „Instanz hinzufügen“ zum Erstellen einer Commerce Optimizer-Umgebung](./assets/create-aco-instance.png){width="60%" zoomable="yes"}

1. Instanzeinstellungen konfigurieren:
   - **Instance Name**: Beschreibender Name (z. B. „My Company Sandbox„)
   - **Beschreibung**: Kurze Beschreibung des Zwecks
   - **Umgebungstyp**: Beginnen Sie zum Testen mit **Sandbox**-Umgebung
   - **Region**: Wählen Sie Ihre bevorzugte Region aus

1. Klicken Sie **Instanz hinzufügen**.

   Die Cloud Manager wird aktualisiert und enthält jetzt auch Ihre neue Instanz. Weitere Informationen zum Zugriff und zur Verwaltung finden Sie unter [Verwalten einer Instanz](#manage-instances).

>[!NOTE]
>
>Sie können Sandbox-Umgebungen nur in der nordamerikanischen Region erstellen. Nachdem eine Instanz erstellt wurde, kann die Region nicht mehr geändert werden.

### Schritt 2. Einrichten der Umgebung

Nach dem Erstellen der Instanz:

1. [Instanz verwalten](#manage-instances) über Commerce Cloud Manager.
1. Konfigurieren Sie den Benutzerzugriff mithilfe des [Benutzerhandbuchs für die &#x200B;](./user-management.md)&quot;

### Schritt 3. Beispieldaten hinzufügen (optional)

Zum Testen und Lernen folgen Sie den Anweisungen [Beispieldaten laden](#add-sample-data).

## Rollenbasierte Workflows

Die Einrichtung und Verwaltung von [!DNL Adobe Commerce Optimizer] beruht auf drei Schlüsselrollen. Jede Rolle hat bestimmte Aufgaben und Zuständigkeiten:

![Rollenbasierter Workflow für [!DNL Adobe Commerce Optimizer] Setup mit Administrator-, Entwickler- und Benutzeraufgaben](./assets/high-level-workflow.png){zoomable="yes"}

### Administratoraufgaben

Administratoren verwalten Instanzen, Benutzer und Unternehmenseinstellungen.

| Aufgabe | Beschreibung | Link |
|---|---|---|
| **Benutzer verwalten** | Hinzufügen von Benutzern, Entwicklern und Administratoren | [Benutzerverwaltung](./user-management.md) |
| **Instanzen erstellen** | Einrichten von Sandbox- und Produktionsumgebungen | [Instanz erstellen](#step-1-create-an-instance) |
| **Verwalten von Instanzen** | Status überprüfen, Instanznamen und Beschreibung aktualisieren und wichtige URLs für den Anwendungs- und API-Zugriff abrufen | [Verwalten von Instanzen](#manage-instances) |
| **Zugriff konfigurieren** | Einrichten von Katalogansichten und Richtlinien | [Katalogansichten](./setup/catalog-view.md) |

### Entwickleraufgaben

Entwickler übernehmen die technische Implementierung und Datenintegration, einschließlich der Aufgaben der Plattformarchitektur.

| Aufgabe | Beschreibung | Link |
|---|---|---|
| **Zugriff auf Developer Console** | Erstellen von Projekten und Generieren von Anmeldeinformationen | [Developer Console](https://developer.adobe.com/developer-console/docs/guides/getting-started) |
| **Aufnehmen von Katalogdaten** | Importieren von Produktdaten aus vorhandenen Systemen | Informationen zum direkten Aufnehmen von Daten in Adobe Commerce Optimizer finden Sie [Datenaufnahme-API](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/){target="_blank"}.<br><br>Informationen zum Aufnehmen von Daten aus Commerce in Cloud- oder lokalen Umgebungen oder anderen Drittanbietersystemen finden Sie unter [Integrationen](./integrations/integrations-overview.md){target="_blank"}. |
| **Einrichten der Storefront** | Konfigurieren der Edge Delivery Services-Storefront | [Storefront-Setup](./storefront.md) |

### Merchandiser-Aufgaben

Merchandiser optimieren und personalisieren das Einkaufserlebnis durch Produkterkennung und Empfehlungen. Sie verwenden auch Kundendaten und Analysen, um strategische Entscheidungen über Produktplatzierung, Preise und Werbeaktionen in der Storefront zu treffen.

| Aufgabe | Beschreibung | Link |
|---|---|---|
| **Produkterkennung** | Konfigurieren von Suche und Filterung | [Merchandising - Übersicht](./merchandising/overview.md) |
| **Recommendations** | Einrichten von KI-gestützten Produktempfehlungen | [Produktempfehlungen](./merchandising/recommendations/overview.md) |
| **Leistungsverfolgung** | Überwachen von Erfolgsmetriken | [Erfolgsmetriken](./manage-results/success-metrics.md) |

## Verwalten von Instanzen

Verwalten von Instanzen über Commerce Cloud Manager.

>[!NOTE]
>
>Nicht alle [!DNL Adobe Commerce Optimizer] haben Zugriff auf Cloud Manager. Der Zugriff hängt von der Rolle und den Berechtigungen ab, die dem Benutzerkonto zugewiesen sind.

1. Anmelden bei [Adobe Experience Cloud](https://experience.adobe.com/).

1. Öffnen Sie Commerce Cloud Manager:

   - Klicken **unter &quot;**&quot; auf **Commerce**.
   - Verfügbare Instanzen anzeigen.

### Instanzen suchen und filtern

Nach der Anmeldung zeigt das Dashboard alle in der Organisation verfügbaren Commerce-Produktinstanzen an.
Die Spalte Produkt gibt an, für welche Commerce-Anwendung die Instanz bereitgestellt wird.

![Dashboard mit Such- und Filteroptionen für Adobe Commerce Cloud-Produktinstanzen](./assets/search-filter-instances.png){zoomable="yes"}

Verwenden Sie die Filter- und Suchwerkzeuge, um bestimmte Instanzen schnell nach Erstellungsdatum, Region, Ersteller, Produkttyp, Umgebung oder Status zu finden.

### Zugriff auf die [!DNL Adobe Commerce Optimizer Studio] Admin-Benutzeroberfläche

Sobald die App geöffnet ist, können Sie einfach zwischen Umgebungen wie Sandbox und Produktion wechseln, um Daten und Einstellungen für jede Umgebung anzuzeigen, ohne zum Commerce Cloud Manager zurückzukehren.

1. Klicken Sie in Commerce Cloud Manager auf den Instanznamen, um [!DNL Adobe Commerce Optimizer Studio] zu öffnen.

1. Wechseln Sie zwischen [!DNL Adobe Commerce Optimizer] Instanzen, ohne die Anwendung zu verlassen.

   - Klicken Sie auf die Dropdown-Liste Instanz , um alle in der Organisation verfügbaren Optimizer-Instanzen anzuzeigen.

     ![Dropdown-Liste „Instanzwechsel“ zur Auswahl [!DNL Adobe Commerce Optimizer] Umgebungen](./assets/context-switcher.png){zoomable="yes"}

- Anzuzeigende Instanz auswählen.

>[!NOTE]
>
>Um zu Commerce Cloud Manager zurückzukehren, um Instanzdetails anzuzeigen oder Instanzen zu verwalten, klicken Sie auf das Symbol ![Symbol zum Öffnen von Experience Cloud Applications](./assets/apps-icon.png) (Apps) in der oberen linken Ecke des oberen Navigationsbereichs von Commerce Optimizer.

### Instanzdetails abrufen

Zeigen Sie die Details der Instanz an, indem Sie auf das Informationssymbol neben Ihrem Instanznamen klicken.

Bedienfeld mit Details zur ![[!DNL Adobe Commerce Optimizer]-Instanz, das Endpunkte und die Instanz-ID anzeigt](./assets/aco-instance-details.png){width="60%" zoomable="yes"}

Beachten Sie die folgenden wichtigen Informationen:

- **GraphQL-Endpunkt** GraphQL-Endpunkt, den Ihre Storefront verwendet, um Katalog- und Merchandising-Daten von dieser Instanz mithilfe der [Merchandising Service-API abzufragen](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/){target=„_blank}
- **Katalog-Endpunkt** REST-API-Endpunkt, mit dem Sie Produkte und Preise aus Ihrem Commerce- oder PIM-System in Adobe Commerce Optimizer aufnehmen. Siehe [Datenaufnahme-API](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/)
- **Commerce Optimizer-URL** Öffnet die Admin-Benutzeroberfläche von [Adobe Commerce Optimizer &#x200B;](overview.md)Studio&rbrace; zum Konfigurieren und Verwalten von Katalogansichten, Richtlinien und Merchandising.
- **Instanz-ID**: Eindeutiger Bezeichner (Mandanten-ID) für diese Adobe Commerce Optimizer-Instanz, der von Storefronts, APIs und Tools zur Verbindung mit der richtigen Umgebung verwendet wird.

Wenn Sie Entwickler sind, benötigen Sie diese Details, um Ihre Entwicklungsumgebung einzurichten und eine Verbindung zu den [!DNL Adobe Commerce Optimizer]-APIs herzustellen.

>[!NOTE]
>
>Um auf die Details der Instanz zugreifen zu können, müssen Sie in Ihrer Adobe IMS-Organisation über die erforderlichen Berechtigungen verfügen. Wenn die Details der Instanz nicht angezeigt werden oder Sie nicht auf die Anwendung zugreifen können, wenden Sie sich an den Administrator Ihrer Organisation.

### Instanznamen und Beschreibung bearbeiten

Aktualisieren Sie den Instanznamen und die Beschreibung nach Bedarf.

1. Klicken Sie auf **Bearbeiten**-Symbol neben einem Instanznamen.
1. Aktualisieren Sie den **Instanznamen** und **Beschreibung** nach Bedarf.
1. Klicken Sie **Speichern**.

## Beispieldaten hinzufügen

Adobe bietet ein GitHub-Repository mit Beispieldaten und Tools, mit denen Sie [!DNL Adobe Commerce Optimizer] Funktionen erlernen und testen können.
Die Beispieldaten basieren auf dem [Carvelo-Geschäftsszenario](./use-case/admin-use-case.md) und umfassen:

- Produktkatalog mit Kfz-Teilen
- Mehrere Preisbücher und Preisszenarien
- Katalogansichten und Richtlinien für verschiedene Händler
- Vollständige Beispiele für End-to-End-Workflow

**Beispieldaten laden:**

1. GitHub[Repository für die Datenaufnahme &#x200B;](https://github.com/adobe-commerce/aco-sample-catalog-data-ingestion) Beispielkatalogs.

1. Befolgen Sie die Setup-Anweisungen in der README-Datei des Repositorys, um die folgenden Aufgaben auszuführen:

   - Einrichten der Umgebung
   - Abschließen des Datenerfassungsprozesses
   - Erstellen von Katalogansichten und Richtlinien mithilfe der Beispieldaten
   - Überprüfen Sie die Datenaufnahme, indem Sie die Daten des Katalog-Service auf der Seite [Datensynchronisierung](./setup/data-sync.md) überprüfen

## Nächste Schritte

Nach Abschluss der Einrichtung:

1. Einrichten der Storefront:
   - [Edge Delivery Services-Storefront konfigurieren](./storefront.md)
   - Herstellen einer Verbindung zu Ihren Katalogdaten

1. Erkunden Sie den Anwendungsfall Carvelo:
   - Befolgen Sie [End-to-End-Workflow](./use-case/admin-use-case.md)
   - Üben mit realen Szenarien

1. Merchandising konfigurieren:
   - Einrichten [Produkterkennung](./merchandising/overview.md)
   - Erstellen [Recommendations](./merchandising/recommendations/overview.md)

1. Überwachen der Leistung:
   - [Erfolgsmetriken](./manage-results/success-metrics.md)
   - Analysieren [Suchleistung](./manage-results/search-performance.md)

## Fehlerbehebung

### Häufige Probleme

| Problem | Lösung |
|---|---|
| **Instanz kann nicht erstellt werden** | Vergewissern Sie sich, dass Sie über [!DNL Adobe Commerce Optimizer] Berechtigungen und Administratorrechte verfügen. |
| **Instanz wird nicht angezeigt** | Überprüfen Sie Ihre Adobe IMS-Organisation und aktualisieren Sie die Seite. |
| **Zugriff auf Instanz nicht möglich** | Stellen Sie sicher, dass Sie als Benutzer in der Admin Console hinzugefügt werden. |
| **Beispieldaten werden nicht geladen** | Überprüfen Sie Ihre Instanzanmeldeinformationen und API-Endpunkte. |

### Hilfe erhalten

- **Entwicklerressourcen**: [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/)
- **Storefront-Ressourcen**: [Dokumentation zur Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/)
- **Tutorials**: [Commerce Optimizer-Tutorials](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-commerce-optimizer/overview)
- **Support**: [Adobe Commerce-Support-Ressourcen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview)
