---
title: Überblick über die Commerce-Architektur
description: Erfahren Sie mehr über das Adobe Commerce-Produktmodell und wo Sie detaillierte Architekturoptionen, Storefront und API-Anleitungen finden.
role: Developer, Leader
feature: Storefront, Integration
recommendations: noCatalog
autotag-review: '2026-10-20T10:11:03.706Z'
TQID: 'https://experienceleague.adobe.com/V9Zp0eS8b45xYEay4EK91tPVnKhRdkWGDj4Vv7hB79U'
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
  - id: 4273989f-0bf2-5361-a17a-6909488d18ab
    internal-label: Catalog Service
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dec06508-d41f-555a-87e8-29e8bcdfa95a
    internal-label: Recommendations
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: da3860b0-d637-47df-bef0-273751180266
    internal-label: Digital asset management
source-git-commit: ca6bb3543583c865c42b8f4d84f01e27a04f9223
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%
---

# Überblick über die Commerce-Architektur

Adobe Commerce-Architekturen umfassen im Allgemeinen drei Ebenen: ein Commerce-Backend ([!DNL Adobe Commerce] oder [!DNL Adobe Commerce Optimizer]), eine Storefront und eine Reihe miteinander verbundener Services und Integrationen. In diesem Abschnitt erhalten Sie eine Orientierung zum Produktmodell und einen Verweis auf die detaillierten Vergleiche, Diagramme und API-Referenzen, die auf jeder dedizierten Seite gepflegt werden.

## Erste Schritte

| Abschnitt | Verwenden Sie ihn, um |
| ------- | --------- |
| [Plattformen und Services](../portfolio/platform-and-services.md) | Machen Sie sich mit den einzelnen Commerce-Produkten vertraut - Adobe Commerce, Commerce Foundation, Adobe Commerce Optimizer und Adobe Commerce as a Cloud Service. |
| [Commerce-Option auswählen](../portfolio/choose-commerce-option.md) | Vergleichen Sie Commerce-Optionen basierend auf Transaktionseigentum, Bereitstellungsmodell und Merchandising-Anforderungen. |
| [Architekturoptionen](../architecture-options/implementation-architectures.md) | Vergleichen Sie alle vier unterstützten Architekturen im Detail, einschließlich Systemdiagrammen und Referenzlinks. |
| [Storefronts](../storefronts/overview.md) | Verstehen der Storefront-Optionen und wie sie mit jeder Architektur verbunden sind. |
| [APIs](../apis/commerce-apis.md) | Vergleichen Sie die in Commerce Foundation, Storefront Services und Commerce Optimizer verwendeten API-Familien. |
| [AEM Assets-Integration für Commerce](../aem-assets/aem-assets-integration.md) | Hinzufügen einer zentralisierten Digital Asset Management-Verwaltung zu einer beliebigen Commerce- oder Optimizer-Architektur. |
| [Migration und Einführung](../migration-adoption/overview.md) | Planen Sie einen Wechsel zwischen Architekturen oder eine schrittweise Einführung von Adobe Commerce Optimizer. |

## Kurzanleitung zur Terminologie

| Bevorzugter Begriff | Bedeutung | Vermeiden Sie die Verwendung von als aktuelle Architekturbezeichnung |
| --- | --- | --- |
| **Commerce Foundation** | Basis-Commerce- und Transaktionsfunktionen | Grundlegende Commerce- und PHP-Ebene |
| **Storefront-Services** | Storefront-orientierte APIs für Katalog-Service, Live Search und Produktempfehlungen | Eine Bezeichnung, die auf nur eine Commerce-Plattform beschränkt ist |
| **Commerce Optimizer-Merchandising-Services** | Optimizer-APIs für die Katalogerkennung und Merchandising-Erlebnisse | Commerce Foundation-APIs |
| **Commerce Storefront powered by Edge Delivery Services** | Kundenorientierte Storefront-Implementierung | Eine API-Familie |

## Ergänzende Leitlinien

- [Implementierungsarchitekturen](implementation-architectures.md)
- [Referenzarchitekturen](reference-architectures.md)
- [Neue Storefront erstellen](../implementation-guides/build-new-storefront.md)
