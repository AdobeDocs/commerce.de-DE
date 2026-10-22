---
title: Optionen für die Implementierungsarchitektur
description: Vergleichen Sie Adobe Commerce-Architekturen, einschließlich Commerce Foundation, Adobe Commerce as a Cloud Service, Optimizer Connector und eigenständiger Optimizer.
role: Developer, Leader
feature: Storefront, Integration
recommendations: noCatalog
autotag-review: '2026-10-20T01:39:51.406Z'
TQID: 'https://experienceleague.adobe.com/tYkxRAfJWOY7C0OEqYxEb4onwvnnL9wEofEG2e6qnKA'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: ef0c45ae-6bee-4821-a65e-e1e118e8a01c
    internal-label: Commerce Optimizer
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4273989f-0bf2-5361-a17a-6909488d18ab
    internal-label: Catalog Service
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
    internal-label: Order Management System
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dec06508-d41f-555a-87e8-29e8bcdfa95a
    internal-label: Recommendations
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 4c3c267873a68560a885c6376cd1137a7503710a
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%
---

# Optionen für die Implementierungsarchitektur

Adobe Commerce-Implementierungsarchitekturen kombinieren drei Ebenen: ein Commerce-Backend ([!DNL Adobe Commerce] oder [!DNL Adobe Commerce Optimizer]), eine Storefront und eine Reihe miteinander verbundener Services und Integrationen. Vergleichen Sie die folgenden Optionen, um in jeder Architektur zu ermitteln, welches System Eigentümer von Katalog, Preisen, Warenkorb, Checkout, Bestellungen und Kundentransaktionen ist.

## Zusammenfassung der Architekturoptionen

Vergleichen Sie die Optionen nach Transaktionseigentum und Storefront-Erlebnis.

### Commerce-Plattform und Transaktionen

| Option | Aufzeichnungssystem | Transaktionspfad | Beste Anpassung |
| --- | --- | --- | --- |
| **[!DNL Adobe Commerce as a Cloud Service]mit Commerce Foundation** | Von Adobe verwaltetes Commerce Foundation | Managed Commerce Foundation und Connected Commerce Services | Kunden, die Adobe Managed Software as a Service (SaaS) Commerce mit reduziertem Infrastruktureigentum wünschen |
| **[!DNL Adobe Commerce]in der Cloud oder lokal mit dem[!DNL Adobe Commerce Optimizer Connector]** | Vorhandene Commerce Foundation, für Commerce-Daten und -Transaktionen | Bestehende Commerce Foundation-APIs und verbundene Transaktionsdienste | Kunden, die einer vorhandenen [!DNL Adobe Commerce]-Bereitstellung Optimizer-Erkennungs- und Merchandising-Funktionen hinzufügen möchten |
| **Eigenständige [!DNL Adobe Commerce Optimizer] mit einem externen Commerce-Backend** | Bestehende Commerce-Plattform oder Plattform eines Drittanbieters. Katalog- und Preisdaten werden Optimizer aus einer externen Quelle hinzugefügt | API Mesh-, App Builder- oder Direct-Integrationen verbinden die Storefront mit Warenkorb-, Checkout-, Kunden-, Bestell-, Zahlungs-, Steuer-, Versand- und Fulfillment-Services von Drittanbietern | Kunden, die Optimizer-Funktionen wünschen, während sie eine bestehende oder Drittanbieter-Transaktions-Commerce-Plattform beibehalten |
| **[!DNL Adobe Commerce]in der Cloud oder lokal mit Commerce Foundation** | Commerce Foundation | Commerce Foundation-APIs und konfigurierte Zahlungs-, Steuer-, Versand-, Inventar- und Erfüllungsintegrationen | Kunden, die die vollständige [!DNL Adobe Commerce] Plattform mit Bereitstellungssteuerung über Cloud- oder On-Premise-Infrastruktur benötigen |

### Storefront-Erlebnis

Storefronts stellen eine Verbindung zu Commerce Foundation-APIs, Storefront Services ([!DNL Catalog Service], [!DNL Live Search] und [!DNL Product Recommendations]) oder [!DNL Adobe Commerce Optimizer] Merchandising Services her.

| Option | Storefront-Erlebnis | Storefront-Datenpfad |
| --- | --- | --- |
| **[!DNL Adobe Commerce as a Cloud Service]mit Commerce Foundation** | Commerce-Storefront mit Edge Delivery Services oder einem anderen unterstützten Headless-Erlebnis | Storefront-Services plus Commerce Foundation-APIs für zentrale Plattformdaten |
| **[!DNL Adobe Commerce]in der Cloud oder lokal mit dem[!DNL Adobe Commerce Optimizer Connector]** | Edge Delivery Services oder benutzerdefinierte Headless-Storefront mit Optimizer-Erlebnissen | Commerce Optimizer Merchandising Services GraphQL-APIs für vom Optimizer verwaltete Kataloge und Merchandising-Daten |
| **Eigenständige [!DNL Adobe Commerce Optimizer] mit einem externen Commerce-Backend** | Commerce-Storefront mit Edge Delivery Services oder benutzerdefinierte Headless-Storefront | Commerce Optimizer Merchandising Services GraphQL-APIs für Katalog- und Merchandising-Daten |
| **[!DNL Adobe Commerce]in der Cloud oder lokal mit Commerce Foundation** | Edge Delivery Services, Luma, PWA oder benutzerdefinierte Headless-Storefront | Commerce Foundation-APIs plus Storefront-Services bei Konfiguration |

## Adobe Commerce as a Cloud Service

![Architekturdiagramm von Adobe Commerce as a Cloud Service mit verwalteten Commerce Foundation- und Storefront-Services, die eine Commerce-Storefront speisen](../assets/architecture/commerce-cloud-service-storefront-services-arch.drawio.png){width="600" zoomable="yes"}

**Schlüsselgrenze** - Adobe verwaltet die Commerce Foundation-Plattform. Die Architektur verwendet Storefront-Services, einschließlich [!DNL Catalog Service], [!DNL Live Search] und [!DNL Product Recommendations], für Storefront-Erlebnisse. [!DNL Product Visuals] powered by AEM Assets ist eine optionale SaaS-Integration. Siehe [AEM Assets-Integration für Commerce](../aem-assets/aem-assets-integration.md).

**Verweise:**

- [Übersicht über [!DNL Adobe Commerce as a Cloud Service]](/help/cloud-service/overview.md)
- [Commerce-Storefront](https://experienceleague.adobe.com/en/tools/commerce-storefront/)
- [Storefront Services-GraphQL-Schema](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/)

## Adobe Commerce mit Commerce Foundation

![Architekturdiagramm von Adobe Commerce in der Cloud oder lokal mit Storefront-Services und Commerce Foundation-APIs, die eine Commerce-Storefront speisen](../assets/architecture/commerce-paas-storefront-services-arch.drawio.png){width="600" zoomable="yes"}

**Schlüsselgrenze** - Commerce Foundation ist der Eigentümer der Commerce-Plattform und der Transaktionsflüsse. [!DNL Catalog Service], [!DNL Live Search] und [!DNL Product Recommendations] bieten bei der Konfiguration optimierten Zugriff auf Kataloge, Suchen und Empfehlungen in der Storefront. Die AEM Assets-Integration ist optional. Siehe [AEM Assets-Integration für Commerce](../aem-assets/aem-assets-integration.md).

**Verweise:**

- [Commerce-Storefront](https://experienceleague.adobe.com/en/tools/commerce-storefront/)
- [Commerce GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/)
- [Storefront Services-GraphQL-Schema](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/)


## Adobe Commerce mit dem Optimizer-Connector

![Architekturdiagramm des Adobe Commerce Optimizer-Connectors, der Katalog- und Preisdaten von Adobe Commerce mit Adobe Commerce Optimizer synchronisiert und dabei eine Commerce-Storefront über Merchandising Services-APIs speist](../assets/architecture/adobe-commerce-optimizer-architecture.drawio.png){width="600" zoomable="yes"}

**Schlüsselgrenze** - Der Connector synchronisiert Katalog- und Preisdaten von [!DNL Adobe Commerce] nach [!DNL Adobe Commerce Optimizer]. [!DNL Adobe Commerce] bleibt das Transaktionssystem, während Optimizer über seine Merchandising Services-APIs Erkennungs- und Merchandising-Erlebnisse bereitstellt.

**Verweise:**

- [Commerce Optimizer-Integrationen](/help/optimizer/integrations/integrations-overview.md)
- [Commerce Optimizer Merchandising-Services](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/)
- [Commerce GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/)
- [Commerce-Storefront](https://experienceleague.adobe.com/en/tools/commerce-storefront/)

## Eigenständige Commerce Optimizer mit einem Backend eines Drittanbieters

![Architekturdiagramm der kundeneigenen Quellsysteme, die Katalog- und Preisdaten über die Datenaufnahme an eine eigenständige Adobe Commerce Optimizer senden und dabei eine Commerce-Storefront speisen, die mit einem Commerce-Backend eines Drittanbieters verbunden ist](../assets/architecture/adobe-commerce-optimizer-standalone-detailed.drawio.png){width="800" zoomable="yes"}

**Schlüsselgrenze** - Eigenständige [!DNL Adobe Commerce Optimizer] steuert Katalogerkennung und Merchandising-Erlebnisse, nicht jedoch das Transaktions-Commerce-Backend. Katalog- und Preisdaten werden über die Datenaufnahme-REST-API eingegeben. Die Edge Delivery Services-Storefront verwendet GraphQL-APIs für Merchandising-Services für Produkterlebnisse und stellt eine Verbindung zum Drittanbieter-Backend für Warenkorb und Checkout her.

**Verweise:**

- [Was ist Adobe Commerce Optimizer?](/help/optimizer/overview.md)
- [Commerce Optimizer-Datenaufnahme](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/)
- [Commerce Optimizer Merchandising-Services](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/)
- [Commerce-Storefront](https://experienceleague.adobe.com/en/tools/commerce-storefront/)

## Kurzanleitung zur Terminologie

| Bevorzugter Begriff | Bedeutung | Vermeiden Sie die Verwendung von als aktuelle Architekturbezeichnung |
| --- | --- | --- |
| **Commerce Foundation** | Basis-Commerce- und Transaktionsfunktionen | Core Commerce, PHP-Grundlagenebene |
| **Storefront-Services** | Storefront-orientierte APIs für Katalog-Service, Live Search und Produktempfehlungen | Eine Bezeichnung, die auf nur eine Commerce-Plattform beschränkt ist |
| **Commerce Optimizer-Merchandising-Services** | Optimizer-APIs für die Katalogerkennung und Merchandising-Erlebnisse | Commerce Foundation-APIs |
| **Commerce Storefront powered by Edge Delivery Services** | Kundenorientierte Storefront-Implementierung | Eine API-Familie |

## Ergänzende Leitlinien

- [Referenzarchitekturen](reference-architectures.md)
- [Commerce-Option auswählen](../portfolio/choose-commerce-option.md)
- [Schaufenster](../storefronts/overview.md)
- [APIs](../apis/commerce-apis.md)
