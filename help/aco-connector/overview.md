---
title: Adobe Commerce Optimizer-Connector
description: Erfahren Sie, wie Sie Ihre Daten aus Ihrem Commerce Cloud- oder lokalen Projekt mit Adobe Commerce Optimizer verbinden
feature: Personalization, Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: c9cce4766ef3f30390d50f53237328be1cfeefdf
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# Adobe Commerce Optimizer-Connector

Der Adobe Commerce Optimizer-Connector ist eine native First-Party-Integration zwischen Adobe Commerce (Cloud oder On-Premise) und Adobe Commerce Optimizer. Es synchronisiert Katalog- und Preisdaten aus Ihren Adobe Commerce-Stores in Commerce Optimizer, sodass Sie:

- Power **KI-gesteuerte Produkterkennung und Empfehlungen**
- Ausführen **Hochleistungs-Headless-Storefronts** (einschließlich Commerce-Storefronts mit Edge Delivery)
- Analyse **vor und nach** KPIs und des Zustands der Datensynchronisation an einem Ort

Commerce bleibt Ihr Aufzeichnungssystem für Produkte, Preise und Katalogstruktur. Commerce Optimizer wird zu Ihrer Erlebnis- und Merchandising-Ebene und liefert schnelle, relevante Ergebnisse für jede verbundene Storefront oder jeden verbundenen Kanal.

## Die wichtigsten Vorteile {#key-benefits}

| Vorteil | Was es für Sie bedeutet |
| --- | --- |
| **Kein benutzerdefinierter Connector zum Erstellen** | Verwenden Sie eine unterstützte First-Party-Integration, anstatt maßgeschneiderte Feeds und Skripte zu schreiben und zu pflegen. |
| **Schnellere Wertschöpfung mit Commerce Optimizer** | Aktivieren Sie KI-Suchen, Empfehlungen und Headless-Storefronts zusätzlich zu Ihrer bestehenden Adobe Commerce-Bereitstellung. |
| **Abgestimmt auf Commerce-Bereiche** | Ordnet automatisch Websites, Shop-Ansichten und Kundengruppen Commerce Optimizer-Katalogkonstrukten (Katalogquellen und Preisbüchern) zu. |
| **Operative Sichtbarkeit** | Überwachen Sie den Status des Feeds, die letzten Synchronisierungszeiten und den Status pro SKU über eine dedizierte Ansicht für den Synchronisierungsstatus des Daten-Feeds. |
| **Zukunftsfähiger Weg zu SaaS** | Bietet einen risikoarmen Modernisierungspfad von PaaS zu Adobe Commerce as a Cloud Service + Optimizer, ohne eine erneute Plattform. |

## Connector-Architektur {#connector-architecture}

Das folgende Diagramm veranschaulicht die End-to-End-Architektur für den Connector, von Adobe Commerce über Commerce Optimizer und Out bis hin zu Storefronts und Checkout-Systemen.

![Diagramm zur End-to-End-Architektur des Commerce Optimizer-Connectors für Commerce](./assets/aco-connector-end2end-architecture.png){width="700" zoomable="yes"}

In dieser Architektur:

- Adobe Commerce (On-Cloud oder On-Premise) ist das System von Datensatz- und Feed-Produzenten
- Der Connector exportiert Katalog-, Preis- und Kategorie-Feeds
- Commerce Optimizer nimmt die Feed-Daten in Katalogquellen, Preislisten und Katalogansichten auf und normalisiert sie
- Storefronts (Commerce-Storefront in Edge Delivery oder benutzerdefinierte Headless-Builds) rufen Commerce Optimizer GraphQL-APIs zur Erkennung und Empfehlung auf und rufen Commerce oder eine andere verbundene Drittanbieterplattform für Warenkorb- und Kaufvorgänge auf

## Funktionsweise des Connectors mit Adobe Commerce {#how-it-works}

- Commerce Optimizer nimmt die Feed-Daten in Katalogquellen, Preislisten und Katalogansichten auf und normalisiert sie.

- Storefronts (Commerce-Storefront in Edge Delivery oder benutzerdefinierte Headless-Builds) rufen Commerce Optimizer GraphQL-APIs zur Erkennung und Empfehlung auf und rufen Commerce oder eine andere verbundene Drittanbieterplattform für Warenkorb- und Checkout-Vorgänge auf.

## Funktionsweise des Connectors mit Adobe Commerce

Der Adobe Commerce Optimizer-Connector funktioniert mithilfe Ihrer bestehenden Commerce-Bereiche (Websites und Store-Ansichten) und der Kundensegmentierung, um das Commerce Optimizer-Katalogmodell zu befüllen:

![Zuordnen von Commerce-Daten zu Adobe Commerce Optimizer](/help/aco-connector/assets/storeview-to-catalogview-mapping.png){width="750" zoomable="yes"}

- **Store-Ansichten → Katalogquellen** - Jede Store-Ansicht wird zu einem separaten Katalog-Source in Commerce Optimizer. Diese Quelle enthält lokalisierte Produktattribute und alle Store-View-spezifischen Daten
- **Websites → Preisbücher** - Jede Commerce-Website wird einem oder mehreren Preisbüchern in Commerce Optimizer zugeordnet. Website-Preisfindung und Kundengruppenpreisexport als Preisbücher und Preiseinträge
- **Kundengruppen → Preisvarianten** — Die Preise der Commerce Kundengruppen werden als zusätzliche Einträge in den entsprechenden Preisbüchern angezeigt

Nachdem Commerce Optimizer die Daten aufgenommen hat, können Sie Folgendes konfigurieren:

- **Katalogansichten und Richtlinien** in Commerce Optimizer (für Gebäuderegion, Marke oder kundenspezifische Untergruppen)
- **Produkterkennung** (Suche, Facetten, Merchandising-Regeln)
- **Produktempfehlungen**

Wenn Sie den Connector aktivieren, bleibt die Adobe Commerce-Instanz das Aufzeichnungssystem für Katalog- und Preisdaten. Wenn Sie Daten in Commerce aktualisieren, synchronisiert der Connector diese Aktualisierungen mit der [!DNL Adobe Commerce Optimizer].

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von Commerce Optimizer finden Sie unter [[!DNL Adobe Commerce Optimizer] Merchandising-Tools](../optimizer/overview.md#quick-tour).

## Typische Workflows {#typical-workflows}

Diese Workflows beschreiben, wie Teams den Adobe Commerce Optimizer-Connector einrichten und verwenden. Weitere Informationen zum Einrichten der Integration und Aktivieren dieser Workflows finden Sie unter [Erste Schritte](get-started.md).

### Ersteinrichtung und -konfiguration {#initial-setup}

1. **Installieren Sie das Connector-Paket in Adobe Commerce** mithilfe von Composer:

   `composer require adobe-commerce/commerce-data-export-aco-adapter`

1. **Konfigurieren der Authentifizierung und Umgebungsdetails** in Commerce Admin oder über CLI:

   ```terminal
   bin/magento aco:config:init \
     --org_id=<your-org> \
     --tenant_id=<your-tenant> \
     --client_id=<your-client-id> \
     --client_secret=<your-secret> \
     --region=na1 \
     --type=production
   ```

1. **Zuordnen von Commerce-Bereichen zu Commerce Optimizer:**

   - Bestätigen, welche Websites und Store-Ansichten im Umfang sein müssen
   - Stellen Sie sicher, dass Kundengruppen und Preisregeln wie erwartet modelliert werden

1. **Überprüfen Sie die Konnektivität:**

   - Führen Sie eine Testsynchronisierung durch und überprüfen Sie, ob Katalogquellen, Preislisten und Anfangsprodukte in Commerce Optimizer angezeigt werden.
   - Verwenden Sie die Seite „Status der Daten-Feed-Synchronisierung“ in Commerce und die Dashboards zur Datensynchronisierung in Commerce Optimizer zur Validierung

### Laufende Datensynchronisation {#ongoing-sync}

Nach der ersten Konfiguration unterstützt der Connector Folgendes:

- **Vollständige Katalogsynchronisierung** für die Erstmigration oder große strukturelle Änderungen
- **Delta-Synchronisationen** für laufende Aktualisierungen, wenn sich Produkte oder Preise ändern
- **Befehle neu synchronisieren** für zielgerichtete Feeds (einschließlich Kategorien ab Version 1.0.12):

   - `bin/magento saas:resync --feed=products`
   - `bin/magento saas:resync --feed=prices`
   - `bin/magento saas:resync --feed=categories`

### Konfigurieren von Merchandising und Storefronts {#merchandising-storefronts}

Sobald Commerce-Daten in Commerce Optimizer verfügbar sind, können Sie mit Commerce Optimizer Studio Merchandising- und Storefront-Erlebnisse mit Ihrem synchronisierten Katalog verbinden.

**So konfigurieren Sie Merchandising- und Storefronts:**

1. **Erstellen von Katalogansichten und** in Commerce Optimizer Studio:

   - Den Katalog nach Marke, Region, Kundensegment oder Kanal filtern
   - Erzwingen von Datenzugriffsregeln pro Storefront oder Partner

1. **Konfigurieren von Produkterkennung und Empfehlungen** in der Optimizer-Benutzeroberfläche:

   - Erstellen von Merchandising-Regeln, Facetten, Synonymen und Empfehlungseinheiten
   - Der Connector lädt alle Such- und Empfehlungskonfigurationen auf Commerce Optimizer ab (Live-Suchregeln und Produktempfehlungen in Commerce Admin gelten für diese Flüsse nicht mehr)

1. **Verbinden von Storefronts** mit Commerce Optimizer:

   - Für eine Commerce-Storefront mit Edge Delivery Services konfigurieren Sie die Storefront so, dass der richtige Optimizer-Mandant und die richtige Katalogansicht verwendet werden und dass die Such- und Empfehlungsendpunkte über die Merchandising-API aufgerufen werden
   - Verwenden Sie für Storefronts von Drittanbietern öffentliche Optimizer-APIs oder -SDKs für Such- und Empfehlungsaufrufe

   >[!NOTE]
   >
   >Ein Beispiel für eine Drittanbieterintegration finden Sie unter [Salesforce Commerce Connector für Commerce Optimizer](../optimizer/developer/salesforce-connector.md).

1. **Auschecken beibehalten** auf Ihrer vorhandenen Plattform:

   - Warenkorb, Checkout, Bestellverwaltung und Kundenkonten in Adobe Commerce oder einer Drittanbieterplattform aufbewahren
   - Verwenden Sie App Builder und API Mesh für die Übergabe an den Warenkorb bei der Integration mit externen Checkout-Systemen

## Unterstützte Szenarien {#supported-scenarios}

Der Connector wurde für B2C-Händler mit Adobe Commerce in Cloud- und On-Premise-Bereitstellungen entwickelt, die Commerce Optimizer übernehmen möchten, ohne ihr Backend neu zu erstellen.

**Häufige Anwendungsfälle:**

- **Nur die Storefront modernisieren**
Behalten Sie Ihr bestehendes Commerce-Backend bei und verschieben Sie PLP/Search/PDP zu Edge Delivery-Storefronts mit Commerce Optimizer

- **Skalieren der Katalog- und Suchleistung**
Entlastung umfangreicher Katalogindizierung und -suche für die SaaS-Services von Commerce Optimizer bei gleichzeitiger Beibehaltung des Produkt- und Preisbesitzes in Commerce

- **Inkrementelle SaaS-Einführung**
Verwenden Sie den Connector als Sprungbrett zu Adobe Commerce as a Cloud Service + Optimizer mit einem kompatiblen zusammenstellbaren Commerce-Katalog

## Zuständigkeiten und Voraussetzungen für die Implementierung {#responsibilities-prerequisites}

Commerce ist die wahre Informationsquelle für Produkte, Preise und Kundengruppen. Nehmen Sie Änderungen in Commerce vor; der Connector synchronisiert sie mit Commerce Optimizer.

**Commerce Optimizer ist verantwortlich für:**

- Katalogmodellierung (Katalogquellen, Preislisten, Katalogansichten, Richtlinien)
- Produkterkennung und Empfehlungen
- Berichte zu Storefront-Metriken, Datensynchronisations-Dashboards und Erfolgsmetriken

**Der Connector funktioniert nicht:**

- Ändern des Commerce-Warenkorbs, des Checkout oder der Bestellflüsse
- Automatische Bereitstellung von Storefront-Projekten (Commerce Storefront / Edge Delivery-Tools, die dies verarbeiten)

**Bevor Sie beginnen:**

- Stellen Sie sicher, dass Commerce die Mindestanforderungen an Version und Services-Connector erfüllt. Weitere Informationen [&#x200B; Sie unter &#x200B;](get-started.md#prerequisites) Schritte .
- Stellen Sie sicher, dass Sie Zugriff auf die IMS-Organisation, eine [!DNL Adobe Commerce Optimizer]-Instanz und die erforderlichen Anmeldeinformationen und Regionsdetails haben.

## Verwandte Dokumentation {#related-documentation}

- Einrichten der Integration und Aktivieren wichtiger Workflows: [Erste Schritte mit dem Adobe Commerce Optimizer-Connector](get-started.md)
- Erfahren Sie mehr über Commerce Optimizer-Konzepte und -Architektur: [Was ist Adobe Commerce Optimizer?](../optimizer/overview.md)
