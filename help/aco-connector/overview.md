---
title: Adobe Commerce Optimizer-Connector
description: Erfahren Sie mehr über die [!DNL Adobe Commerce Optimizer Connector] für Katalogsynchronisierung, Suche und Storefront-Bereitstellung zwischen [!DNL Adobe Commerce] und [!DNL Adobe Commerce Optimizer].
feature: Integration, Storefront, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T19:00:00.000Z'
nudge: true
TQID: 'https://experienceleague.adobe.com/v769V06jl-9YfovpL3HOB-FxovIMZyHxOlHXHvkQmbc'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: adedf70c-c1e1-5734-acdc-c5c43b114964
    internal-label: Release Notes
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dec06508-d41f-555a-87e8-29e8bcdfa95a
    internal-label: Recommendations
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
subfeature_v2:
  - id: ae62cf09-5996-4921-bda8-fbe67b62e470
    internal-label: Storefront configuration
  - id: f8ddfd3b-6194-46e8-a176-0e918039be56
    internal-label: Cloud architecture
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
    internal-label: Data integration
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a3ade1a31d3c2905b601f71bda118de89c43cf59
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 0%
---
# [!DNL Adobe Commerce Optimizer Connector]

Die [!DNL Adobe Commerce Optimizer Connector] ist eine native First-Party-Integration zwischen [!DNL Adobe Commerce] (Cloud oder On-Premise) und [!DNL Adobe Commerce Optimizer]. Es synchronisiert Katalog- und Preisdaten aus Ihren [!DNL Adobe Commerce] Stores in [!DNL Adobe Commerce Optimizer], sodass Sie:

- Power **KI-gesteuerte Produkterkennung und Empfehlungen**
- Ausführen **Hochleistungs-Headless-Storefronts** (einschließlich Commerce-Storefronts mit [!DNL Edge Delivery Services])
- Analyse **vor und nach** KPIs und des Zustands der Datensynchronisation an einem Ort

[!DNL Adobe Commerce] bleibt Ihr Aufzeichnungssystem für Produkte, Preise und Katalogstruktur. [!DNL Adobe Commerce Optimizer] wird zu Ihrer Erlebnis- und Merchandising-Ebene und liefert schnelle, relevante Ergebnisse für jede verbundene Storefront oder jeden verbundenen Kanal.

## Die wichtigsten Vorteile {#key-benefits}

| Vorteil | Was es für Sie bedeutet |
| --- | --- |
| **Kein benutzerdefinierter Connector zum Erstellen** | Verwenden Sie eine unterstützte First-Party-Integration, anstatt maßgeschneiderte Feeds und Skripte zu schreiben und zu pflegen. |
| **Schnellere Wertschöpfung mit[!DNL Adobe Commerce Optimizer]** | Aktivieren Sie KI-Suchen, Empfehlungen und Headless-Storefronts zusätzlich zu Ihrer bestehenden [!DNL Adobe Commerce]-Bereitstellung. |
| **Abgestimmt auf Commerce-Bereiche** | Ordnet automatisch Websites, Shop-Ansichten und Kundengruppen [!DNL Adobe Commerce Optimizer] Katalogkonstrukten (Katalogquellen und Preisbüchern) zu. |
| **Operative Sichtbarkeit** | Überwachen Sie den Feed-Zustand, die letzten Synchronisierungszeiten und den Status pro SKU über eine dedizierte [!UICONTROL Data Feed Sync Status]. |
| **Zukunftsfähiger Weg zu SaaS** | Bietet einen stufenweisen Migrationspfad von Commerce on Cloud oder On-Premise zu [!DNL Adobe Commerce as a Cloud Service] + [!DNL Adobe Commerce Optimizer] ohne erneute Plattform. |

## Connector-Architektur {#connector-architecture}

Das folgende Diagramm veranschaulicht die End-to-End-Architektur für den Connector, von [!DNL Adobe Commerce] über [!DNL Adobe Commerce Optimizer] und Out bis hin zu Storefronts und Checkout-Systemen.

![Diagramm zur End-to-End-Architektur des Adobe Commerce Optimizer-Connectors](./assets/aco-connector-end2end-architecture.png){width="700" zoomable="yes"}

In dieser Architektur:

- [!DNL Adobe Commerce] (in der Cloud oder vor Ort) ist das Aufzeichnungssystem und der Futtermittelhersteller
- Der Connector exportiert Katalog-, Preis- und Kategorie-Feeds
- [!DNL Adobe Commerce Optimizer] nimmt die Feed-Daten in Katalogquellen, Preislisten und Katalogansichten auf und normalisiert sie
- Storefronts (Commerce-Storefront mit [!DNL Edge Delivery Services] oder benutzerdefinierten Headless-Builds) rufen [!DNL Adobe Commerce Optimizer] GraphQL-APIs zur Erkennung und Empfehlung auf und rufen [!DNL Adobe Commerce] oder eine andere verbundene Drittanbieterplattform für Warenkorb- und Kaufvorgänge auf

Der auf [[!DNL SaaS Data Export]](/help/data-export/overview.md) aufbauende Connector ordnet erfasste Feeds dem [!DNL Catalog Data Ingestion API]-Format zu und verarbeitet die Authentifizierung und Übermittlung. Siehe [Connector-Synchronisierungs](/help/aco-connector/connector-sync-pipeline.md)Pipeline) für das Synchronisierungsverhalten, die Umfangskontrolle und die Fehlerbehandlung.

## Funktionsweise des Connectors mit [!DNL Adobe Commerce] {#how-the-connector-works-with-adobe-commerce}

Die [!DNL Adobe Commerce Optimizer Connector] unterstützt die B2C-Katalogsynchronisierung. Es synchronisiert Katalog- und Preis-Feeds aus einer [!DNL Adobe Commerce]-Instanz und ordnet Ansichten, Websites und Kundengruppen Katalogquellen und Preisbüchern in [!DNL Adobe Commerce Optimizer] zu. Der freigegebene B2B-Katalog oder die Konfiguration der Unternehmenszuweisung werden nicht synchronisiert. Konfigurieren Sie nach der Synchronisierung Katalogansichten und Richtlinien in [!DNL Adobe Commerce Optimizer] Studio.

![Zuordnen [!DNL Adobe Commerce] Daten zu [!DNL Adobe Commerce Optimizer]](./assets/storeview-to-catalogview-mapping.png){width="750" zoomable="yes"}

### Zuordnung des Basiskatalogs

Der Connector ordnet [!DNL Adobe Commerce] Katalogdaten dem [!DNL Adobe Commerce Optimizer] Katalogmodell zu:

- **Store-Ansicht → Katalogquellen** - Jede Store-Ansicht wird zu einer separaten Katalogquelle in [!DNL Adobe Commerce Optimizer]. Diese Quelle enthält lokalisierte Produktattribute und alle Store-View-spezifischen Daten.
- **Website → Preisbücher** - Jede [!DNL Adobe Commerce] Website ist einem oder mehreren Preisbüchern in [!DNL Adobe Commerce Optimizer] zugeordnet. Website-Preise und Kundengruppenpreise exportieren als Preisbücher und Preiseinträge.
- **Kundengruppe → Preisbucheinträge** — [!DNL Adobe Commerce] Kundengruppenpreise erscheinen als zusätzliche Einträge in den entsprechenden Preisbüchern.

Nachdem der Connector die Katalogdaten synchronisiert hat, konfigurieren Sie das Merchandising-Modell in [!DNL Adobe Commerce Optimizer] Studio. Konfigurieren Sie beispielsweise:

- **Katalogansichten und Richtlinien** für Regions-, Marken- oder kundenspezifische Untergruppen
- **Produkterkennung** für Suche, Facetten und Merchandising-Regeln
- **[!DNL Product Recommendations]**

### B2B-Connector-Verhalten {#b2b-shared-catalog-projection-specification}

Die [!DNL Adobe Commerce Optimizer Connector for B2B] erweitert den Basis-Connector mit einer unidirektionalen Projektion des freigegebenen B2B-Katalogs und der Konfiguration der Unternehmenszuweisung in geschützte Katalogerlebnisse. [!DNL Adobe Commerce] bleibt die Quelle der Wahrheit für Katalog- und Preisdaten. Der B2B-Connector baut auf dem Basiskatalog und der Preissynchronisierung auf und verwaltet die von Connectoren generierten Projektionen.

Informationen zu Projektionszuordnung, Laufzeitautorisierungsfluss und Schutzgrenze finden Sie unter [B2B-Shared-Catalog-Projektion](b2b-shared-catalog-projection.md). Setup-Anweisungen finden Sie unter [Erste Schritte mit dem B2B-Connector](/help/aco-connector/get-started-b2b-shared-catalogs.md).

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von [!DNL Adobe Commerce Optimizer] finden Sie unter [[!DNL Adobe Commerce Optimizer] Merchandising-Tools](/help/optimizer/overview.md#quick-tour).

## Typische Workflows {#typical-workflows}

Diese Workflows beschreiben, wie Teams die [!DNL Adobe Commerce Optimizer Connector] einrichten und verwenden. Weitere Informationen zum Einrichten der Integration und Aktivieren dieser Workflows finden Sie unter [Erste Schritte](/help/aco-connector/get-started.md).

### Ersteinrichtung und -konfiguration {#initial-setup}

Siehe [Konfigurationsschritte](/help/aco-connector/get-started.md#configuration-steps) im _Erste Schritte_.

### Laufende Datensynchronisation {#ongoing-sync}

Nach der ersten Konfiguration unterstützt der Connector Folgendes:

- **Vollständige Katalogsynchronisierung** für die Erstmigration oder große strukturelle Änderungen
- **Delta-Synchronisationen** für laufende Aktualisierungen, wenn sich Produkte oder Preise ändern
- **Befehle neu synchronisieren** um Feeds zu synchronisieren

Informationen zum automatisierten Synchronisierungsverhalten, Cron-Zeitplänen und zur Fehlerbehandlung finden Sie unter [Connector-Synchronisierungs-Pipeline](/help/aco-connector/connector-sync-pipeline.md). Verwenden Sie vor einer vollständigen Katalogsynchronisierung oder einer großen Aktualisierung [Geschätzte Datenmenge und Synchronisierungszeit](/help/aco-connector/reference/estimate-data-volume-sync-time.md), um den Zeitpunkt zu planen und Site-Unterbrechungen zu vermeiden.

Für die [!DNL Adobe Commerce Optimizer Connector] stehen die folgenden Feeds zur Verfügung:

- `products` - Produktdaten
- `productAttributes` - Metadaten für Produktattribute
- `priceBooks` - Preisbücher
- `prices` - Produktpreise
- `categories` - Daten zu Kategorien

Weitere Informationen finden Sie in den folgenden Themen:

- Überprüfen der Synchronisierung von Katalogdaten und manuelles Neusynchronisieren der Connector-Feeds: [Synchronisierung verwalten](/help/aco-connector/data-sync-status.md)
- Informationen zu [!DNL Adobe Commerce] Neusynchronisierungsvorgängen für CLI finden Sie unter [Synchronisieren von Feeds mit der Commerce-CLI](/help/data-export/data-export-cli-commands.md)
- [[!DNL Adobe Commerce Optimizer Connector] Module und Feed-Endpunkte](/help/aco-connector/reference/connector-reference.md)
- [Feldzuordnung für Connector-Feeds](/help/aco-connector/reference/field-mapping.md)

### Konfigurieren von Merchandising und Storefronts {#merchandising-storefronts}

Sobald [!DNL Adobe Commerce] Daten in [!DNL Adobe Commerce Optimizer] verfügbar sind, verwenden Sie [[!DNL Adobe Commerce Optimizer] Studio](/help/optimizer/overview.md#quick-tour), um Merchandising- und Storefront-Erlebnisse mit Ihrem synchronisierten Katalog zu verbinden. Zu den typischen nächsten Schritten gehören:

- **Katalogansichten und -richtlinien** - Definieren Sie für den Basis-Connector im Menü [!UICONTROL Store setup] regions-, marken- oder kundenspezifische Untergruppen und Zugriffsregeln. Informationen dazu, wer eine Katalogansicht abfragen kann, finden Sie unter [Private Katalogansichten](/help/optimizer/setup/private-catalog-view.md)
- **Produkterkennung und Empfehlungen** - Konfigurieren von Suche, Facetten, Merchandising-Regeln, Synonymen und Empfehlungseinheiten im [!UICONTROL Merchandising]. Das Verhalten bei Suchen und Empfehlungen wird in [!DNL Adobe Commerce Optimizer] verwaltet. Die [!DNL Live Search]- und [!DNL Product Recommendations]-Einstellungen in der [!DNL Adobe Commerce] Admin gelten für diese Flüsse nicht mehr.
- **Storefront-Verbindungen** - Verweisen Sie Commerce-Storefronts auf Headless-Builds von [!DNL Edge Delivery Services] oder Drittanbietern auf die richtigen [!DNL Adobe Commerce Optimizer]-Mandanten-, Katalogansichts- und Merchandising-API-Endpunkte. Informationen zu benutzerdefinierten Headless-Integrationen finden Sie unter [Headless-Storefront-Integration](/help/aco-connector/headless-storefront.md). Ein Beispiel für eine Drittanbieterintegration finden Sie unter [Salesforce Commerce Connector für [!DNL Adobe Commerce Optimizer]](/help/optimizer/developer/salesforce-connector.md)
- **Checkout** - Warenkorb, Checkout, Bestellverwaltung und Kundenkonten auf [!DNL Adobe Commerce] oder einer verbundenen Drittanbieterplattform aufbewahren. Verwenden Sie bei Bedarf [!DNL App Builder] und [!DNL API Mesh] für die Übergabe an den Warenkorb

Eine schrittweise Konfigurationsanleitung finden Sie unter [Erste Schritte](/help/aco-connector/get-started.md) und [[!DNL Adobe Commerce Optimizer] Merchandising-Tools](/help/optimizer/overview.md#quick-tour).

## Unterstützte Szenarien {#supported-scenarios}

Die [!DNL Adobe Commerce Optimizer Connector] unterstützt B2C-Händler mit [!DNL Adobe Commerce] in Cloud- und On-Premise-Bereitstellungen, die [!DNL Adobe Commerce Optimizer] übernehmen möchten, ohne ihr Backend neu zu erstellen.

Die separate [!DNL Adobe Commerce Optimizer Connector for B2B] erweitert den Basis-Connector, um die Konfiguration freigegebener Kataloge zu synchronisieren und benutzerdefinierte freigegebene Kataloge automatisch als private Katalogansichten zu projizieren. Weitere Informationen finden Sie unter [B2B-Katalogprojektion](b2b-shared-catalog-projection.md).

**Häufige Anwendungsfälle:**

- **Storefront-Migration zu Edge Delivery**
Behalten Sie Ihr vorhandenes [!DNL Adobe Commerce]-Backend bei und verschieben Sie PLP/Search/PDP auf [!DNL Edge Delivery Services] Storefronts mit [!DNL Adobe Commerce Optimizer].

- **Skalieren der Katalog- und Suchleistung**
Entlastung umfangreicher Katalogindizierungen und Suchvorgänge für [!DNL Adobe Commerce Optimizer] SaaS-Services (Software as a Service) bei gleichzeitiger Beibehaltung des Produkt- und Preisbesitzes in [!DNL Adobe Commerce].

## Zuständigkeiten und Voraussetzungen für die Implementierung {#responsibilities-prerequisites}

[!DNL Adobe Commerce] ist das „System of Record“ für Produkte, Preise und Kundengruppen. Nehmen Sie Änderungen in [!DNL Adobe Commerce] vor, und der Connector synchronisiert sie mit [!DNL Adobe Commerce Optimizer].

**[!DNL Adobe Commerce Optimizer]ist verantwortlich für:**

- Katalogmodellierung (Katalogquellen, Preisbücher, Katalogansichten, Richtlinien)
- Produkterkennung und Empfehlungen
- Berichte zu Storefront-Metriken, Datensynchronisations-Dashboards und Erfolgsmetriken

**Der Connector funktioniert nicht:**

- Ändern [!DNL Adobe Commerce] Warenkorb-, Checkout- oder Bestellflüssen
- Automatische Bereitstellung von Storefront-Projekten (Commerce Storefront / [!DNL Edge Delivery Services]-Tools, die dies verarbeiten)

**Bevor Sie beginnen:**

- Stellen Sie sicher, dass [!DNL Adobe Commerce] die Mindestanforderungen an Version und [!DNL Adobe Commerce Optimizer Connector] erfüllt. Weitere Informationen [&#x200B; Sie unter &#x200B;](/help/aco-connector/get-started.md#requirements-to-use-the-integration) Schritte .
- Stellen Sie sicher, dass Sie Zugriff auf die IMS-Organisation, eine [!DNL Adobe Commerce Optimizer]-Instanz und die erforderlichen Anmeldeinformationen und Regionsdetails haben.

>[!MORELIKETHIS]
>
> - [Erste Schritte mit dem [!DNL Adobe Commerce Optimizer Connector]](/help/aco-connector/get-started.md) - Einrichten der Integration und Aktivieren wichtiger Workflows.
> - [Connector-Synchronisierungs](/help/aco-connector/connector-sync-pipeline.md)-Pipeline - Verstehen des Synchronisierungsmechanismus, der Initialisierung und der Fehlerbehandlung.
> - [Synchronisierung verwalten](/help/aco-connector/data-sync-status.md) - Überprüfen Sie die Synchronisierung von Katalogdaten und synchronisieren Sie Feeds manuell neu.
> - [Feldzuordnung für Connector-Feeds](/help/aco-connector/reference/field-mapping.md) — Überprüfen Sie die Datenzuordnung auf Feldebene für alle Feeds.
> - [Fehlerbehebungsszenarien](/help/aco-connector/troubleshooting/troubleshooting-scenarios.md) — Beheben Sie Konfigurationsfehler oder unerwartete Synchronisierungsergebnisse.
> - [Versionshinweise](/help/aco-connector/release-notes.md) - Überprüfen Sie Connector-Aktualisierungen und bekannte Probleme.
