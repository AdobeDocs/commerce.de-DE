---
title: Eine vorhandene Storefront modernisieren
description: Erfahren Sie, wie Sie eine inkrementelle Migration von einer alten Adobe Commerce-Storefront zu einer Storefront planen, die auf Edge Delivery Services- und Dropdown-Komponenten basiert.
role: Developer, Leader
feature: Storefront
recommendations: noCatalog
autotag-review: '2026-10-20T11:09:14.812Z'
TQID: 'https://experienceleague.adobe.com/1OR7uwncjLw-NpwMMuwKjDjpASdh74sfu6s5rNClqxg'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4273989f-0bf2-5361-a17a-6909488d18ab
    internal-label: Catalog Service
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
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: ca6bb3543583c865c42b8f4d84f01e27a04f9223
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%
---

# Eine vorhandene Storefront modernisieren

Sie können ältere Storefronts inkrementell zu Edge Delivery Services- und Commerce-Drop-in-Komponenten migrieren, anstatt alles gleichzeitig neu zu erstellen.

>[!NOTE]
>
>Dieses Handbuch gilt für Adobe Commerce as a Cloud Service, Adobe Commerce in der Cloud-Infrastruktur oder lokale Bereitstellungen, die entweder Storefront Services oder den Adobe Commerce Optimizer Connector verwenden. Dies gilt auch für eigenständige Adobe Commerce Optimizer mit einem vorhandenen Backend oder einem Backend eines Drittanbieters. Informationen dazu, welche Option für Ihr Projekt gilt, finden Sie unter [Optionen für die Implementierungsarchitektur](../architecture-options/implementation-architectures.md).

## Erste Schritte

1. Um zu verstehen, wie eine auf Edge Delivery Services aufbauende Storefront im Vergleich zu Ihrer aktuellen Implementierung aussieht, lesen Sie [Übersicht über die Adobe Commerce Storefront](https://experienceleague.adobe.com/en/tools/commerce-storefront/).

1. Verwenden Sie das [Storefront-Entwicklerhandbuch](https://experienceleague.adobe.com/en/tools/commerce-storefront/get-started/) um festzulegen, welche Seiten oder Flüsse zuerst migriert werden sollen.

1. Behalten Sie für Adobe Commerce as a Cloud Service Ihre bestehenden Commerce Services-Verbindungen ([!DNL Catalog Service], [!DNL Live Search], [!DNL Product Recommendations], [!DNL Payment Services]) bei - siehe [Einrichten von Commerce Services](set-up-commerce-services.md).

## Ergänzende Leitlinien

- [Neue Storefront erstellen](build-new-storefront.md)
- [Architekturoptionen](../architecture-options/overview.md)
