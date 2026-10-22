---
title: Commerce-APIs
description: Vergleichen Sie Adobe Commerce-API-Familien, einschließlich Commerce Foundation, Storefront Services, Commerce Optimizer Merchandising Services und Datenaufnahme.
role: Developer, Leader
feature: Storefront, Integration
recommendations: noCatalog
autotag-review: '2026-10-20T01:36:11.529Z'
TQID: 'https://experienceleague.adobe.com/JBpnpCy9QITdcYtKnL2btd9grmgIk1prYaCNasgWkok'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
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
  - id: 72863f3c-9d27-5dda-afe1-d9f934b1fba0
    internal-label: Extensibility
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dec06508-d41f-555a-87e8-29e8bcdfa95a
    internal-label: Recommendations
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: da3860b0-d637-47df-bef0-273751180266
    internal-label: Digital asset management
source-git-commit: ca6bb3543583c865c42b8f4d84f01e27a04f9223
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%
---

# APIs

| API-Familie | Primärer Zweck | Verwendet von |
| --- | --- | --- |
| **Commerce Foundation GraphQL-APIs** | Zentrale Commerce- und Transaktionsfunktionen wie Katalogvorgänge, Warenkorb, Checkout, Kunden und Bestellungen | [!DNL Adobe Commerce] in der Cloud, [!DNL Adobe Commerce] vor Ort und [!DNL Adobe Commerce as a Cloud Service] |
| **Storefront Services GraphQL-APIs** | Storefront-orientierte Katalog-, Such- und Empfehlungs-Erlebnisse durch [!DNL Catalog Service], [!DNL Live Search] und [!DNL Product Recommendations] | [!DNL Adobe Commerce] in der Cloud oder lokal mit konfigurierten Services und [!DNL Adobe Commerce as a Cloud Service] |
| **Commerce Optimizer Merchandising Services GraphQL-APIs** | Abrufen von vom Optimizer verwalteten Katalogen, Katalogansichten, Preiskontexten, Suchen, Empfehlungen und Merchandising-Ergebnissen | [!DNL Adobe Commerce] in der Cloud oder lokal mit dem Optimizer-Connector und eigenständigen [!DNL Adobe Commerce Optimizer] |
| **Commerce Optimizer-Datenaufnahme-REST-API** | Hinzufügen von Katalog- und Preisdaten zu einer eigenständigen [!DNL Adobe Commerce Optimizer] | Eigenständige [!DNL Adobe Commerce Optimizer] mit einer externen Datenquelle verbunden |

## Commerce Foundation GraphQL-APIs

Zentrale Commerce-Funktionen wie Katalog, Warenkorb, Checkout, Kunden und Bestellungen. Wird von [!DNL Adobe Commerce] in der Cloud verwendet, [!DNL Adobe Commerce] vor Ort und [!DNL Adobe Commerce as a Cloud Service]. Siehe [Commerce GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/).

## Storefront Services GraphQL-APIs

Storefront-orientierte Katalog-, Such- und Empfehlungserlebnisse durch [!DNL Catalog Service], [!DNL Live Search] und [!DNL Product Recommendations]. Wird von [!DNL Adobe Commerce] in der Cloud, lokal und [!DNL Adobe Commerce as a Cloud Service] verwendet. Siehe das [Storefront Services-GraphQL-Schema](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/).

## Commerce Optimizer Merchandising Services GraphQL-APIs

Rufen Sie vom Optimizer verwaltete Kataloge, Katalogansichten, Preiskontexte, Suchen, Empfehlungen und Merchandising-Ergebnisse ab. Wird von [!DNL Adobe Commerce] in der Cloud, On-Premise mit dem [!DNL Adobe Commerce Optimizer Connector] und eigenständigen [!DNL Adobe Commerce Optimizer] verwendet. Siehe [Commerce Optimizer Merchandising Services](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/).

## Commerce Optimizer-Datenaufnahme-REST-APIs

Hinzufügen von Katalog- und Preisdaten zu einer eigenständigen [!DNL Adobe Commerce Optimizer] aus einer externen Datenquelle. Siehe [Commerce Optimizer-Datenaufnahme](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/).

## Commerce Optimizer-Integrationen

[!DNL Adobe Commerce Optimizer] stellt über mehrere Integrationspfade eine Verbindung zu anderen Systemen her, je nachdem, ob es mit [!DNL Adobe Commerce] oder einem Backend eines Drittanbieters gepaart ist.

### Adobe Commerce Optimizer-Connector

Synchronisiert Katalog- und Preisdaten von [!DNL Adobe Commerce] in der Cloud oder lokal mit [!DNL Adobe Commerce Optimizer], wobei [!DNL Adobe Commerce] als Transaktionssystem beibehalten wird, während Optimizer Erkennung und Merchandising bereitstellt. Siehe [Commerce Optimizer-Integrationen](/help/optimizer/integrations/integrations-overview.md).

### Commerce-Integrationen von Drittanbietern

nimmt Katalog- und Preisdaten von einer Drittanbieter-Commerce-Plattform, PIM, ERP oder einer anderen Quelle über die Datenaufnahme-REST-API in eigenständige [!DNL Adobe Commerce Optimizer] auf, während die Drittanbieter-Plattform das Transaktionssystem der Aufzeichnung bleibt.

### API-Mesh und App Builder

Verwenden Sie API Mesh, um Adobe Commerce-APIs mit privaten oder Drittanbieter-APIs zu orchestrieren. Verwenden Sie Adobe Developer App Builder, um benutzerdefinierte Programme und Integrationen zu erstellen. Weitere Informationen zur Commerce-Erweiterbarkeit finden Sie unter [API-](https://developer.adobe.com/graphql-mesh-gateway/) und [Adobe Commerce-Erweiterbarkeit](https://developer.adobe.com/commerce/extensibility/).

Speziell für ereignisgesteuerte Integrationen siehe [Adobe I/O Events für Adobe Commerce](https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/extensibility/adobe-developer-app-builder/io-events/getting-started-io-events).


### Warenkorb- und Kassenübergabe

Bei eigenständigen [!DNL Adobe Commerce Optimizer] mit einem externen Backend verwendet die Storefront die Merchandising Services-GraphQL-APIs für Produkterlebnisse und übergibt dann Warenkorb, Checkout, Kunde, Bestellung, Zahlung, Steuer, Versand und Erfüllung über API Mesh, App Builder oder direkte Integration an das Backend.

### AEM Assets

AEM Assets ist eine optionale, bereichsübergreifende Digital-Asset-Management-Integration, die zu jeder Commerce- oder Optimizer-Architektur hinzugefügt werden kann, anstatt über einen eigenen Integrationspfad. Siehe [AEM Assets-Integration für Commerce](../aem-assets/aem-assets-integration.md).

## Ergänzende Leitlinien

- [Überblick über die Architektur](../architecture-options/overview.md)
- [Schaufenster](../storefronts/overview.md)
- [AEM Assets-Integration für Commerce](../aem-assets/aem-assets-integration.md)
