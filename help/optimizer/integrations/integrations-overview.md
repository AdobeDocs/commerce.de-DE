---
title: Commerce Optimizer-Integrationen
description: Erfahren Sie mehr über Adobe Commerce Optimizer-Integrationen für Katalogsynchronisierung, Asset-Management, Storefront-Optimierung und Salesforce Commerce Cloud-Konnektivität.
solution: Commerce
feature: Integration, Catalog Management
role: Developer, Admin
level: Beginner
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 8f3a2c1b-9d4e-5f6a-bc7d-1e2f3a4b5c6d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: ef0c45ae-6bee-4821-a65e-e1e118e8a01c
    internal-label: Commerce Optimizer
feature_v2:
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
source-git-commit: 9b3448a40c2e829e09de5e394b0972c527ee0e9b
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%
---

# [!DNL Adobe Commerce Optimizer] Integrationen

[!DNL Adobe Commerce Optimizer] umfasst Integrationen, mit denen Sie Daten aus Adobe Commerce in der Cloud oder lokal synchronisieren, Assets verwalten, Storefront-Erlebnisse verbessern und externe Systeme verbinden können. In den folgenden Abschnitten wird beschrieben, wie jede Integration mit [!DNL Adobe Commerce Optimizer] funktioniert. Folgen Sie den Links für die Einrichtung, Konfiguration und tägliche Verwendung.

{{aco-integration-environment-alignment}}

## Produktvisualisierung mit AEM Assets {#product-visuals}

Mit Produktvisualisierungen können Sie Produktbilder über Adobe Experience Manager (AEM) Assets verwalten. Konfigurieren Sie AEM Assets für Commerce Optimizer, um Produktvisualisierung zu aktivieren. Nach Abschluss der Konfiguration verwenden Sie AEM Assets als zentralisierte Lösung für das Digital Asset Management für Ihre Produktbilder mit automatisierten Asset-Review- und -Management-Workflows, die die Bilder mit Ihrem Commerce Optimizer-Katalog synchronisieren. Die Integration ordnet Assets Produkten nach SKU zu. Aktualisierungen fließen durch die Integrations-Services von Adobe, sodass Storefronts die neuesten Medien widerspiegeln, ohne dass ein erneutes Hochladen erforderlich ist.

- [Produktvisualisierung mit AEM Assets](../setup/product-visuals.md)

## Adobe Experience Manager Sites Optimizer {#aem-sites-optimizer}

Adobe Experience Manager Sites Optimizer analysiert Commerce-Websites und verbessert die Leistung, indem KI-gesteuerte **[!UICONTROL Opportunities]** angezeigt werden - Empfehlungen, die Sie bei der Verbesserung der Erkennung, Interaktion und Konversionen unterstützen.

>[!AVAILABILITY]
>
>Für diese Funktion ist die **Ultima** Adobe Sites Optimizer-Lizenz erforderlich. Sie können eine Lizenz über Ihren technischen Adobe-Kundenberater anfordern. Sobald Ihr Konto bereitgestellt wurde, ist die Funktion „Opportunitys“ in der [!DNL Adobe Commerce Optimizer] verfügbar und Sie können mit KI-gesteuerten Einblicken beginnen, um Ihre Storefront- und Merchandising-Strategien zu optimieren.

- [Möglichkeiten](../manage-results/opportunities.md)

## Adobe Commerce Optimizer-Connector {#aco-connector}

Der Adobe Commerce Optimizer-Connector ist die Brücke, die Katalog- und Preisdaten zwischen Adobe Commerce (Cloud oder On-Premise) und [!DNL Adobe Commerce Optimizer] synchronisiert. Wenn Sie den Connector aktivieren, bleibt Commerce das Aufzeichnungssystem für Produktdaten, während [!DNL Adobe Commerce Optimizer] die Produkterkennung, Empfehlungen, Merchandising-Regeln, Analysen und Headless-Storefront-Erlebnisse unterstützt. Informationen dazu, wer eine synchronisierte Katalogansicht abfragen kann, finden Sie unter [Private Katalogansichten](../setup/private-catalog-view.md).

- [Übersicht über den Adobe Commerce Optimizer-Connector](../../aco-connector/overview.md){target="_blank"}
- [Erste Schritte mit dem Connector](../../aco-connector/get-started.md){target="_blank"}

## Integration von Warenkorb und Checkout von Drittanbietern

Adobe Commerce Optimizer kann die Produkterkennung und das Merchandising für eine Storefront unterstützen, die eine separate Commerce-Plattform für Transaktionen verwendet. Die Storefront verwendet Commerce Optimizer Merchandising Services-APIs für Produktdaten, Suche, Empfehlungen und Merchandising. Die Host-Commerce-Plattform bleibt für Kundenkonten, Warenkorb, Checkout und Bestellabwicklung verantwortlich. Die Integration mit der Hostplattform ist eine benutzerdefinierte Implementierung, bei der API Mesh, App Builder, direkte APIs oder eine Kombination dieser Tools verwendet werden.

Für Salesforce Commerce Cloud (SFCC) bietet das [Adobe Commerce Optimizer SFCC Checkout Starter Kit](https://github.com/adobe-commerce/aco-sfcc-checkout-starter-kit) Beispiel-Edge Delivery Services-Bausteine und -Skripte zum Verbinden einer Adobe Commerce Optimizer-Storefront mit SFCC-Funktionen für Einkäufer, Warenkorb und Checkout. Verwenden Sie ihn als Referenzimplementierung und passen Sie ihn an Ihre Storefront an. Er ist kein generischer, vorkonfigurierter Connector. Ein [Headless-Storefront-Beispiel für Next.js](https://github.com/adobe-commerce/aco-sfcc-storefront-next){target="_blank"} ist ebenfalls verfügbar.


## Commerce Salesforce Connector {#commerce-salesforce-connector}

Der Commerce Salesforce Connector (auf Adobe App Builder basiert) synchronisiert Katalog- und Preisdaten aus Salesforce Commerce Cloud B2C in [!DNL Adobe Commerce Optimizer], damit Sie Adobe-Storefront- und Merchandising-Funktionen verwenden können, ohne Ihr Salesforce Commerce-Backend neu zu platzieren. Sie können Synchronisationen planen, On-Demand-Aktualisierungen ausführen und die Integration mithilfe von Salesforce Commerce-APIs erweitern.

- [Salesforce Commerce Connector](../developer/salesforce-connector.md)

>[!MORELIKETHIS]
>
>- Technische Dokumentation zu [Adobe Commerce Optimizer](https://developer.adobe.com/commerce/services/optimizer/){target="_blank"}
>- [Erste Schritte mit Adobe Commerce Optimizer](../get-started.md)
