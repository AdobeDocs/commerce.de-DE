---
title: '[!DNL Adobe Commerce Optimizer Connector]'
description: Erfahren Sie mehr über  [!DNL Adobe Commerce Optimizer Connector]  für Katalogsynchronisierung, Suche und Storefront-Bereitstellung zwischen  [!DNL Adobe Commerce]  und  [!DNL Adobe Commerce Optimizer].
feature: Integration, Storefront, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T19:00:00.000Z'
TQID: 'https://experienceleague.adobe.com/-C-XP5YYxwyGrkvVR6CDd-FpDybqnlaKMmFPKOKUbFA'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
subfeature_v2:
  - id: ae62cf09-5996-4921-bda8-fbe67b62e470
  - id: f8ddfd3b-6194-46e8-a176-0e918039be56
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 1075
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

Die [!DNL Adobe Commerce Optimizer Connector] verwendet Ihre vorhandenen Commerce-Bereiche (Websites und Store-Ansichten) und die Kundensegmentierung, um das [!DNL Adobe Commerce Optimizer] Katalogmodell zu füllen:

![Zuordnen von Commerce-Daten zu Adobe Commerce Optimizer](./assets/storeview-to-catalogview-mapping.png){width="750" zoomable="yes"}

- **Store-Ansicht → Katalogquellen** - Jede Store-Ansicht wird zu einem separaten Katalog-Source in [!DNL Adobe Commerce Optimizer]. Diese Quelle enthält lokalisierte Produktattribute und alle Store-View-spezifischen Daten
- **Website → Preisbücher** - Jede [!DNL Adobe Commerce] Website ist einem oder mehreren Preisbüchern in [!DNL Adobe Commerce Optimizer] zugeordnet. Website-Preisfindung und Kundengruppenpreisexport als Preisbücher und Preiseinträge
- **Kundengruppe → Preisvarianten** — [!DNL Adobe Commerce] Kundengruppenpreise erscheinen als zusätzliche Einträge in den entsprechenden Preisbüchern

Nachdem [!DNL Adobe Commerce Optimizer] die Daten aufgenommen hat, können Sie Folgendes konfigurieren:

- **Katalogansichten und Richtlinien** in [!DNL Adobe Commerce Optimizer] Studio (für das Erstellen von Regionen, Marken oder kundenspezifischen Untergruppen)
- **Produkterkennung** (Suche, Facetten, Merchandising-Regeln)
- **[!DNL Product Recommendations]**

Wenn Sie den Connector aktivieren, bleibt die [!DNL Adobe Commerce] das Aufzeichnungssystem für Katalog- und Preisdaten. Wenn Sie Daten in [!DNL Adobe Commerce] aktualisieren, synchronisiert der Connector diese Aktualisierungen mit der [!DNL Adobe Commerce Optimizer].

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
- **Befehle neu synchronisieren** für Feeds

Informationen zum automatisierten Synchronisierungsverhalten, Cron-Zeitplänen und zur Fehlerbehandlung finden Sie unter [Connector-Synchronisierungs-Pipeline](/help/aco-connector/connector-sync-pipeline.md). Verwenden Sie vor einer vollständigen Katalogsynchronisierung oder einer großen Aktualisierung [Geschätzte Datenmenge und Synchronisierungszeit](/help/aco-connector/reference/estimate-data-volume-sync-time.md), um den Zeitpunkt zu planen und Site-Unterbrechungen zu vermeiden.

Für die [!DNL Adobe Commerce Optimizer Connector] stehen die folgenden Feeds zur Verfügung:

- `products` - Produktdaten
- `productAttributes` - Metadaten für Produktattribute
- `priceBooks` - Preisbücher
- `prices` - Produktpreise
- `categories` - Daten zu Kategorien

Weitere Informationen finden Sie in den folgenden Themen:

- Überprüfen der Synchronisierung von Katalogdaten und manuelles Neusynchronisieren der Connector-Feeds: [Synchronisierung verwalten](/help/aco-connector/data-sync-manage.md)
- Informationen zu [!DNL Adobe Commerce] Neusynchronisierungsvorgängen für CLI finden Sie unter [Synchronisieren von Feeds mit der Commerce-CLI](/help/data-export/data-export-cli-commands.md)
- [[!DNL Adobe Commerce Optimizer Connector] Module und Feed-Endpunkte](/help/aco-connector/reference/connector-reference.md)
- [Feldzuordnung für Connector-Feeds](/help/aco-connector/reference/field-mapping.md)

### Konfigurieren von Merchandising und Storefronts {#merchandising-storefronts}

Sobald [!DNL Adobe Commerce] Daten in [!DNL Adobe Commerce Optimizer] verfügbar sind, verwenden Sie [[!DNL Adobe Commerce Optimizer] Studio](/help/optimizer/overview.md#quick-tour), um Merchandising- und Storefront-Erlebnisse mit Ihrem synchronisierten Katalog zu verbinden. Zu den typischen nächsten Schritten gehören:

- **Katalogansichten und -richtlinien** - Definieren von Regions-, Marken- oder kundenspezifischen Untergruppen und Zugriffsregeln über das Menü [!UICONTROL Store setup] .
- **Produkterkennung und Empfehlungen** - Konfigurieren von Suche, Facetten, Merchandising-Regeln, Synonymen und Empfehlungseinheiten im [!UICONTROL Merchandising]. Das Verhalten bei Suchen und Empfehlungen wird in [!DNL Adobe Commerce Optimizer] verwaltet. Die [!DNL Live Search]- und [!DNL Product Recommendations]-Einstellungen in der [!DNL Adobe Commerce] Admin gelten für diese Flüsse nicht mehr.
- **Storefront-Verbindungen** - Verweisen Sie Commerce-Storefronts auf Headless-Builds von [!DNL Edge Delivery Services] oder Drittanbietern auf die richtigen [!DNL Adobe Commerce Optimizer]-Mandanten-, Katalogansichts- und Merchandising-API-Endpunkte. Informationen zu benutzerdefinierten Headless-Integrationen finden Sie unter [Headless-Storefront-Integration](/help/aco-connector/headless-storefront.md). Ein Beispiel für eine Drittanbieterintegration finden Sie unter [Salesforce Commerce Connector für [!DNL Adobe Commerce Optimizer]](/help/optimizer/developer/salesforce-connector.md)
- **Checkout** - Warenkorb, Checkout, Bestellverwaltung und Kundenkonten auf [!DNL Adobe Commerce] oder einer verbundenen Drittanbieterplattform aufbewahren. Verwenden Sie bei Bedarf [!DNL App Builder] und [!DNL API Mesh] für die Übergabe an den Warenkorb

Eine schrittweise Konfigurationsanleitung finden Sie unter [Erste Schritte](/help/aco-connector/get-started.md) und [[!DNL Adobe Commerce Optimizer] Merchandising-Tools](/help/optimizer/overview.md#quick-tour).

## Unterstützte Szenarien {#supported-scenarios}

Der Connector wurde für B2C-Händler mit [!DNL Adobe Commerce] in Cloud- und On-Premise-Bereitstellungen entwickelt, die [!DNL Adobe Commerce Optimizer] übernehmen möchten, ohne ihr Backend neu zu erstellen.

**Häufige Anwendungsfälle:**

- **Storefront-Migration zu Edge Delivery**
Behalten Sie Ihr vorhandenes [!DNL Adobe Commerce]-Backend bei, verschieben Sie PLP/Search/PDP zu [!DNL Edge Delivery Services] Storefronts mit [!DNL Adobe Commerce Optimizer]

- **Skalieren der Katalog- und Suchleistung**
Entlastung umfangreicher Katalogindizierungen und Suchvorgänge für die SaaS-Services von [!DNL Adobe Commerce Optimizer] bei gleichzeitiger Beibehaltung des Produkt- und Preisbesitzes in [!DNL Adobe Commerce]

- **Inkrementelle SaaS-Einführung**
Verwenden Sie den Connector als Sprungbrett in Richtung [!DNL Adobe Commerce as a Cloud Service] + [!DNL Adobe Commerce Optimizer] mit einem kompatiblen zusammensetzbaren [!DNL Adobe Commerce]

## Zuständigkeiten und Voraussetzungen für die Implementierung {#responsibilities-prerequisites}

[!DNL Adobe Commerce] ist die Quelle der Wahrheit für Produkte, Preise und Kundengruppen. Nehmen Sie Änderungen in [!DNL Adobe Commerce] vor, und der Connector synchronisiert sie mit [!DNL Adobe Commerce Optimizer].

**[!DNL Adobe Commerce Optimizer]ist verantwortlich für:**

- Katalogmodellierung (Katalogquellen, Preislisten, Katalogansichten, Richtlinien)
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
> - [Synchronisierung verwalten](/help/aco-connector/data-sync-manage.md) - Überprüfen Sie die Synchronisierung von Katalogdaten und synchronisieren Sie Feeds manuell neu.
> - [Feldzuordnung für Connector-Feeds](/help/aco-connector/reference/field-mapping.md) — Überprüfen Sie die Datenzuordnung auf Feldebene für alle Feeds.
> - [Fehlerbehebungsszenarien](/help/aco-connector/troubleshooting/troubleshooting-scenarios.md) — Beheben Sie Konfigurationsfehler oder unerwartete Synchronisierungsergebnisse.
> - [Versionshinweise](/help/aco-connector/release-notes.md) - Überprüfen Sie Connector-Aktualisierungen und bekannte Probleme.
