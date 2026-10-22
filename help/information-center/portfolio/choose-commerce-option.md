---
title: Commerce-Option auswählen
description: Vergleichen Sie Adobe Commerce-Architekturen basierend auf Transaktionseigentum, Bereitstellungsmodell und Merchandising-Anforderungen.
role: Admin, Developer, Leader, User
feature: Storefront, Integration, Configuration
recommendations: noCatalog
TQID: 'https://experienceleague.adobe.com/5y0IU5nji50eqfFNQHbVDV-R81Mx0I8v5Y0a6nccL-w'
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
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
    internal-label: Order Management System
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
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 4c3c267873a68560a885c6376cd1137a7503710a
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%
---

# Commerce-Option auswählen

Ermitteln Sie zunächst, welchem System der Warenkorb, der Checkout, die Bestellungen und andere Transaktionen gehören. Wählen Sie dann den Merchandising-Pfad aus, der zu diesem Backend passt.

## Fragen zur Entscheidungsfindung

Verwenden Sie die folgenden Fragen, um zu ermitteln, welche Optionen ausgewertet werden sollen. Berücksichtigen Sie Ihr bestehendes Commerce-Backend, wie viel Infrastrukturverantwortung Sie beibehalten möchten und ob Sie die Produkterkennung und das Merchandising verbessern müssen. Adobe Commerce Optimizer bietet Such- und Merchandising-Funktionen. Es ersetzt nicht das Backend, das Transaktionen verarbeitet.

1. **Soll Adobe die Commerce-Plattform als Software as a Service (SaaS) verwalten?**
   - Ja: Adobe Commerce as a Cloud Service auswerten.
   - Nein: Wenn Sie Adobe Commerce benötigen und die Kontrolle über Ihre Cloud- oder On-Premise-Infrastruktur behalten möchten, sollten Sie Adobe Commerce in der Cloud oder On-Premise bewerten.
1. **Benötigt Adobe Commerce Warenkorb-, Checkout-, Bestellungen- und andere Transaktionen?**
   - Ja: Bewerten Sie Adobe Commerce in der Cloud oder lokal oder Adobe Commerce as a Cloud Service. Diese Optionen verwenden Commerce Foundation als Transaktions-Backend.
   - Nein: Vorhandenes Transaktions-Backend von Drittanbietern beibehalten. Wenn Sie auch Discovery- und Merchandising-Funktionen von Adobe benötigen, sollten Sie die eigenständige Adobe Commerce Optimizer evaluieren.
1. **Möchten Sie Adobe Commerce Optimizer verwenden, um die Produkterkennung und das Merchandising mit Ihrem bestehenden Commerce-Backend eines Drittanbieters zu verbessern?**
   - Ja: Bewerten Sie das eigenständige Adobe Commerce Optimizer unter Beibehaltung des Drittanbieter-Backends für Transaktionen.
1. **Betreiben Sie Adobe Commerce bereits in der Cloud oder lokal und wünschen Sie sich eine bessere Erkennung und besseres Merchandising?**
   - Ja: Bewerten Sie den Adobe Commerce Optimizer-Connector, um Katalog- und Preisdaten zu synchronisieren, während Adobe Commerce weiterhin Transaktionen verarbeitet.

Verwenden Sie die folgende Vergleichstabelle, um Ihre Antworten einem Ausgangspunkt zuzuordnen. Detaillierte Systemdiagramme finden Sie unter [Architekturoptionen](../architecture-options/overview.md).

## Commerce-Optionen vergleichen

| Ihre Anforderung | Empfohlener Ausgangspunkt | System, dem Transaktionen gehören | Merchandising und Erkennung |
| --- | --- | --- | --- |
| Adobe verwaltet die Commerce-Plattform als SaaS. | [Adobe Commerce as a Cloud Service](/help/cloud-service/overview.md) | Adobe Commerce as a Cloud Service Foundation | Verwenden Sie die für Adobe Commerce as a Cloud Service bereitgestellten Commerce-Services. Informationen zur Verfügbarkeit der Adobe Commerce Optimizer-Integration finden Sie im Hinweis unten in dieser Tabelle. |
| Sie benötigen Adobe Commerce und möchten die Kontrolle über Ihre Cloud- oder On-Premise-Infrastruktur behalten. | [Adobe Commerce in der Cloud oder lokal](https://experienceleague.adobe.com/en/docs/commerce-admin/start/guide-overview) | Adobe Commerce Foundation | Verwenden Sie nach Bedarf unterstützte Commerce-Services. |
| In Adobe Commerce in der Cloud oder vor Ort und möchten Adobe Commerce Optimizer für die Erkennung und das Merchandising übernehmen. | Adobe Commerce mit dem [Adobe Commerce Optimizer-Connector](/help/aco-connector/overview.md) | Adobe Commerce bleibt das Aufzeichnungssystem für Transaktionen. | Der Connector synchronisiert Katalog- und Preisdaten mit Adobe Commerce Optimizer, um Erlebnisse für Erkennung und Merchandising bereitzustellen. |
| Sie verfügen über ein Commerce-Backend eines Drittanbieters und möchten Adobe Commerce Optimizer Discovery und Merchandising, ohne dieses Backend zu ersetzen. | Eigenständige [Adobe Commerce Optimizer](/help/optimizer/overview.md) | Ihr Commerce-Backend eines Drittanbieters | Senden Sie Katalog- und Preisdaten an Adobe Commerce Optimizer. Integrieren Sie Warenkorb-, Checkout- und andere Transaktionsvorgänge über API Mesh, App Builder oder eine Direktintegration in das Backend. |

>[!NOTE]
>
>Eine Integration zwischen Adobe Commerce as a Cloud Service und Adobe Commerce Optimizer ist Teil der Commerce-Roadmap. Wenn Sie beide Plattformen benötigen, sollten Sie sie vorerst als separate Architekturoptionen verwenden. Wenden Sie sich an Ihren Adobe Account Manager, um mehr über den Zeitplan für die Integration zu erfahren.

## Ergänzende Leitlinien

- [Plattformen und Services](platform-and-services.md)
- [Architekturoptionen](../architecture-options/overview.md)
- [Erste Schritte](../get-started/get-started-by-role.md)
