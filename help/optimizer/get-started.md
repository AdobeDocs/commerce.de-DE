---
title: Erste Schritte
description: Erfahren Sie mehr über die ersten Schritte mit [!DNL Adobe Commerce Optimizer].
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: de57d93d-e156-45c1-86aa-de29a8c34bd2
source-git-commit: 87fbd979b0660af1bf3a8786eb1e1f5f79cea043
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# Erste Schritte

Diese Anleitung führt Sie durch die Einrichtung von [!DNL Adobe Commerce Optimizer] von Anfang bis Ende. Dieses Handbuch deckt zwar alle Rollen ab, doch finden [ in der ](https://developer.adobe.com/commerce/services/optimizer/) für Entwickler detaillierte Informationen zu den jeweiligen Inhalten.

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

   ![Instanz erstellen](./assets/create-aco-instance.png){width="60%" zoomable="yes"}

1. Instanzeinstellungen konfigurieren:
   - **Name**: Beschreibender Name (z. B. „Meine Unternehmens-Sandbox„)
   - **Beschreibung**: Kurze Beschreibung des Zwecks
   - **Region**: Wählen Sie Ihre bevorzugte Region aus
   - **Umgebungstyp**: Beginnen Sie zum Testen mit **Sandbox**-Umgebung

1. Klicken Sie **Instanz hinzufügen**.

   Die Cloud Manager wird aktualisiert und enthält jetzt auch Ihre neue Instanz. Weitere Informationen zum Zugriff und zur Verwaltung finden Sie unter [Verwalten einer Instanz](#manage-an-instance).

>[!NOTE]
>
>Sandbox-Instanzen sind auf die Region Nordamerika beschränkt. Sie können die Region nach der Erstellung nicht mehr ändern.

### Schritt 2. Einrichten der Umgebung

Nach dem Erstellen der Instanz:

1. [Instanz verwalten](#manage-an-instance) über Commerce Cloud Manager.
1. Konfigurieren Sie den Benutzerzugriff mithilfe des [Benutzerhandbuchs für die ](./user-management.md)&quot;

### Schritt 3. Beispieldaten hinzufügen (optional)

Zum Testen und Lernen folgen Sie den Anweisungen [Beispieldaten laden](#add-sample-data).

## Rollenbasierte Workflows

Die Einrichtung und Verwaltung von [!DNL Adobe Commerce Optimizer] beruht auf drei Schlüsselrollen. Jede Rolle hat bestimmte Aufgaben und Zuständigkeiten:

![Workflow auf hoher Ebene](./assets/high-level-workflow.png){zoomable="yes"}

### Administratoraufgaben

Administratoren verwalten Instanzen, Benutzer und Unternehmenseinstellungen.

| Aufgabe | Beschreibung | Link |
|---|---|---|
| **Benutzer verwalten** | Hinzufügen von Benutzern, Entwicklern und Administratoren | [Benutzerverwaltung](./user-management.md) |
| **Instanzen erstellen** | Einrichten von Sandbox- und Produktionsumgebungen | [Instanz erstellen](#create-an-instance) |
| **Verwalten von Instanzen** | Status überprüfen, Instanznamen und Beschreibung aktualisieren und wichtige URLs für den Anwendungs- und API-Zugriff abrufen | [Verwalten von Instanzen](#manage-instances) |
| **Zugriff konfigurieren** | Einrichten von Katalogansichten und Richtlinien | [Katalogansichten](./setup/catalog-view.md) |

### Entwickleraufgaben

Entwickler übernehmen die technische Implementierung und Datenintegration, einschließlich der Aufgaben der Plattformarchitektur.

| Aufgabe | Beschreibung | Link |
|---|---|---|
| **Zugriff auf Developer Console** | Erstellen von Projekten und Generieren von Anmeldeinformationen | [Developer Console](https://developer.adobe.com/developer-console/docs/guides/getting-started) |
| **Aufnehmen von Katalogdaten** | Importieren von Produktdaten aus vorhandenen Systemen | [Datenaufnahme-API](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/) |
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
>Nicht alle Adobe Commerce Optimizer-Benutzer haben Zugriff auf Cloud Manager. Der Zugriff hängt von der Rolle und den Berechtigungen ab, die dem Benutzerkonto zugewiesen sind.

1. Anmelden bei [Adobe Experience Cloud](https://experience.adobe.com/).

1. Öffnen Sie Commerce Cloud Manager:

   - Klicken **unter &quot;**&quot; auf **Commerce**.
   - Verfügbare Instanzen anzeigen.

### Instanzen suchen und filtern

Nach der Anmeldung zeigt das Dashboard alle in der Organisation verfügbaren Commerce-Produktinstanzen an.
Die Spalte Produkt gibt an, für welche Commerce-Anwendung die Instanz bereitgestellt wird.

Verwenden Sie die Filter- und Suchoptionen, um bestimmte Instanzen schnell zu finden. Sie können nach erstellten Daten, Region, Erstellt von, Produkttyp, Umgebung und Status suchen.

### Zugriff auf die [!DNL Adobe Commerce Optimizer]

Sobald die App geöffnet ist, können Sie einfach zwischen Umgebungen wie Sandbox und Produktion wechseln, um Daten und Einstellungen für jede Umgebung anzuzeigen, ohne zum Commerce Cloud Manager zurückzukehren.

1. Klicken Sie in Commerce Cloud Manager auf den Instanznamen, um die [!DNL Adobe Commerce Optimizer]-Anwendung zu öffnen.

1. Wechseln Sie zwischen [!DNL Adobe Commerce Optimizer] Instanzen, ohne die Anwendung zu verlassen.

   In der Dropdown-Liste Instanz werden alle in der Organisation verfügbaren Optimizer-Instanzen aufgelistet. Anzuzeigende Instanz auswählen.

   ![Instanzwechsel](./assets/context-switcher.png){zoomable="yes"}

### Instanzdetails abrufen

Zeigen Sie die Details der Instanz an, indem Sie auf das Informationssymbol neben Ihrem Instanznamen klicken.

![Details der Instanz](./assets/aco-instance-details.png){width="60%" zoomable="yes"}

Beachten Sie die folgenden wichtigen Informationen:

- **GraphQL-Endpunkt** zum Abrufen von Commerce-Katalogdaten mithilfe der Merchandising-API
- **Catalog Service-Endpunkt** für die Datenaufnahme mithilfe der REST-API
- **Commerce Optimizer-URL** für den Zugriff auf die [!DNL Adobe Commerce Optimizer]
- **Instanz-ID** Die eindeutige Mandanten-ID, die die Instanz identifiziert

Die Details zum Endpunkt und zur Instanz-ID sind erforderlich, um den API-Zugriff zu konfigurieren und ihn in Frontend-Anwendungen und Backend-Systeme zu integrieren.
Wenn Sie keinen Zugriff auf die Details der Instanz haben, wenden Sie sich an den Administrator Ihres Unternehmens, um die Werte abzurufen.

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

1. GitHub[Repository für die Datenaufnahme ](https://github.com/adobe-commerce/aco-sample-catalog-data-ingestion) Beispielkatalogs.

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
