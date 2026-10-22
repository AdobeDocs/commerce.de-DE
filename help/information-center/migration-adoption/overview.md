---
title: Migration und Einführung
description: Erfahren Sie mehr über die Routen für die Übernahme von Adobe Commerce Optimizer, die Modernisierung einer bestehenden Storefront oder die vollständige Migration zu Adobe Commerce as a Cloud Service.
role: Admin, Developer, Leader
feature: Storefront, Integration, Configuration
recommendations: noCatalog
TQID: 'https://experienceleague.adobe.com/2iEJ6fA-wLr18bi9C8l-w3srx1AWlAtiGt1cG9RPv0Q'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
feature_v2:
  - id: 1783ae9f-7157-5aeb-a915-91e260301e46
    internal-label: Routes
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 72863f3c-9d27-5dda-afe1-d9f934b1fba0
    internal-label: Extensibility
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
    internal-label: Order Management System
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: dec06508-d41f-555a-87e8-29e8bcdfa95a
    internal-label: Recommendations
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 4c3c267873a68560a885c6376cd1137a7503710a
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%
---

# Migration und Einführung

Die Übernahme muss keine einzige, umfassende Plattformänderung sein. Wählen Sie eine Route aus, je nachdem, ob Ihr unmittelbares Ziel die Modernisierung der Storefront, die Verbesserung des Merchandising, die Backend-Modernisierung oder ein vollständiger Wechsel zu Managed Software as a Service (SaaS) ist.

## Anpassungswege

### Modernisieren der vorhandenen Adobe Commerce-Bereitstellung

- Die bestehende Commerce Foundation als Transaktions-Backend beibehalten.
- Übernehmen Sie die Commerce Storefront powered by [!DNL Edge Delivery Services].
- Verwenden Sie Storefront-Services, App Builder, API Mesh und eine optionale AEM Assets-Integration.

### Verwenden von Commerce Optimizer als Brücke

- Verbinden Sie [!DNL Adobe Commerce] Cloud oder On-Premise über die [!DNL Adobe Commerce Optimizer Connector].
- Einführung von Merchandising-Services, Erkennung, Empfehlungen und einer Edge Delivery Services-Storefront.
- [!DNL Adobe Commerce] als primäres Aufzeichnungssystem für Produkte, Preise, Katalogstruktur, Warenkorb, Checkout, Kunden und Bestellungen beibehalten.
- Verwenden Sie diese Architektur als möglichen Übergang zu [!DNL Adobe Commerce as a Cloud Service].

### Vollständige Migration zu Adobe Commerce as a Cloud Service

- Bewertung des aktuellen Programms, der Anpassungen, Integrationen, Storefront und Daten.
- Modernisieren Sie Anpassungen mithilfe SaaS-kompatibler Erweiterbarkeitsmuster.
- Erstellen oder passen Sie die Storefront und die Integrationen an.
- Migrieren und validieren Sie Kataloge, Kunden, Bestellungen, Konfigurationen und unterstützte benutzerdefinierte Daten.
- Testen, Ausschalten und Betreiben der neuen SaaS-Umgebung.

### Eigenständige Adobe Commerce Optimizer übernehmen

- Nehmen Sie Katalog- und Preisdaten von einer Commerce-Plattform, einem PIM, ERP oder einer anderen Quelle eines Drittanbieters auf.
- Verwenden Sie [!DNL Adobe Commerce Optimizer] Merchandising-Services für Katalogabruf, Erkennung, Empfehlungen und Merchandising.
- Verwenden Sie die Commerce-Storefront powered by [!DNL Edge Delivery Services].
- Warenkorb, Kasse, Kunden, Bestellungen, Zahlungen, Steuer, Versand und Fulfillment in den verbundenen Drittanbietersystemen aufbewahren.

## Empfohlene Reihenfolge

1. Bewerten Sie den aktuellen Status und definieren Sie die Systembesitzerschaft.
1. Legen Sie die Grenzen für die API-First-Integration fest.
1. Modernisieren Sie die Storefront und die Erlebnisebene.
1. Nehmen Sie Merchandising-Services und AEM Assets parallel an.
1. Migrieren Sie bei Bedarf Commerce Foundation.
1. Validieren, Ausschneiden, Überwachen und Optimieren.

## Ergänzende Leitlinien

- [Commerce-Option auswählen](../portfolio/choose-commerce-option.md)
- [Architekturoptionen](../architecture-options/overview.md)
- [Eine vorhandene Storefront modernisieren](../implementation-guides/modernize-storefront.md)
- [Adobe Commerce Optimizer aktivieren](../implementation-guides/enable-aco.md)
