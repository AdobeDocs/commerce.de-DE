---
title: Schaufenster
description: Erfahren Sie mehr über die Optionen der Adobe Commerce-Storefront, einschließlich der Commerce-Storefront mit Edge Delivery Services und benutzerdefinierten Headless-Implementierungen.
role: Developer, Leader
feature: Storefront, Integration
recommendations: noCatalog
autotag-review: '2026-10-20T01:12:22.967Z'
TQID: 'https://experienceleague.adobe.com/1mQm2s3UGzr7S4j9RMZAaRoUVtzu93N1IFbOypR8vkA'
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
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: ca6bb3543583c865c42b8f4d84f01e27a04f9223
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%
---

# Schaufenster

Die Storefront ist vom Commerce-Backend und den API-Ebenen getrennt. Je nach ausgewählter Architektur kann eine Storefront Daten von Commerce Foundation-APIs, Storefront Services-APIs, [!DNL Adobe Commerce Optimizer] Merchandising Services-APIs oder verbundenen Systemen über API Mesh, App Builder oder andere Integrationsmechanismen abrufen. Siehe [Architekturoptionen](../architecture-options/overview.md), wie jede Storefront mit einem Commerce-Backend kombiniert wird.

## Commerce Storefront powered by Edge Delivery Services

Die Commerce Storefront powered by [!DNL Edge Delivery Services] ist eine kundenorientierte Storefront-Option, die auf dem Adobe Commerce-Textbaustein basiert und Dropdown-Komponenten und Inhaltsblöcke verwendet. Es ist mit allen Architekturübersichten kompatibel[&#x200B; die je nach &#x200B;](../architecture-options/overview.md) eine Verbindung mit Commerce Foundation, Storefront-Services oder [!DNL Adobe Commerce Optimizer] Merchandising-Services herstellen. Siehe [Übersicht über die Adobe Commerce-Storefront](https://experienceleague.adobe.com/en/tools/commerce-storefront/).

## Storefront-Services

[!DNL Storefront Services] sind Storefront-orientierte Services, die mit [!DNL Adobe Commerce] verwendet werden. Die Service-APIs bieten optimierten Zugriff auf Funktionen wie:

- [!DNL Catalog Service]
- [!DNL Live Search]
- [!DNL Product Recommendations]

Sowohl [!DNL Adobe Commerce] in der Cloud als auch lokal (falls konfiguriert) und verwenden [!DNL Adobe Commerce as a Cloud Service] Storefront-Services. Sie sind nicht ausschließlich für [!DNL Adobe Commerce as a Cloud Service] und sollten nicht als Unterscheidungsmerkmal zwischen den beiden [!DNL Adobe Commerce] Plattformoptionen verwendet werden. Siehe das [Storefront Services-GraphQL-Schema](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/).

## Benutzerdefinierte Headless-Storefronts

Die Storefront-Optionen jenseits der Commerce-Storefront, die von [!DNL Edge Delivery Services] unterstützt wird, umfassen je nach Plattform-Support und Implementierungsanforderungen [!DNL Luma], [!DNL PWA Studio] oder eine benutzerdefinierte Headless-Storefront. Eine benutzerdefinierte Headless-Storefront verbindet sich mit denselben API-Familien wie jede andere Storefront-Option - Commerce Foundation, Storefront Services oder Commerce Optimizer Merchandising Services - basierend auf der ausgewählten [Architekturoption](../architecture-options/overview.md).

## Integration von Warenkorb und Checkout

Wo Warenkorb- und Checkout-Transaktionen verarbeitet werden, hängt vom Commerce-Backend ab, nicht von der Storefront-Technologie:

- Wenn [!DNL Adobe Commerce] Commerce Foundation das Backend ist, verwendet die Storefront Commerce Foundation-APIs für Warenkorb-, Checkout-, Kunden- und Bestellvorgänge sowie konfigurierte Zahlungs-, Steuer-, Versand- und Erfüllungsintegrationen.
- Wenn es sich bei der Commerce-Plattform eines Drittanbieters um das Backend handelt (wie bei eigenständigen [!DNL Adobe Commerce Optimizer]), stellt die Storefront über API Mesh, App Builder oder eine direkte Integration eine Verbindung mit dem Warenkorb, der Kasse, dem Kunden, der Bestellung, der Zahlung, der Steuer, dem Versand und den Fulfillment-Services dieser Plattform her.

## Ergänzende Leitlinien

- [Überblick über die Architektur](../architecture-options/overview.md)
- [APIs](../apis/commerce-apis.md)
