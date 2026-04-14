---
title: Commerce Optimizer-Integrationen
description: Erfahren Sie mehr über Adobe Commerce Optimizer-Integrationen für Katalogsynchronisierung, Asset-Management, Storefront-Optimierung und Salesforce Commerce Cloud-Konnektivität.
solution: Commerce
feature: Integration, Catalog Management
role: Developer, Admin
level: Beginner
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für  [!DNL Adobe Commerce Optimizer]  (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 8f3a2c1b-9d4e-5f6a-bc7d-1e2f3a4b5c6d
source-git-commit: d8cd6f543353e1b11f3aa14b3b97b02155d23809
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# [!DNL Adobe Commerce Optimizer] Integrationen

[!DNL Adobe Commerce Optimizer] umfasst Integrationen, mit denen Sie Daten aus Adobe Commerce in der Cloud oder lokal synchronisieren, Assets verwalten, Storefront-Erlebnisse verbessern und externe Systeme verbinden können. In den folgenden Abschnitten wird beschrieben, wie jede Integration mit [!DNL Adobe Commerce Optimizer] funktioniert. Folgen Sie den Links für die Einrichtung, Konfiguration und tägliche Verwendung.

## Adobe Commerce Optimizer-Connector {#aco-connector}

Der Adobe Commerce Optimizer-Connector ist die Brücke, die Katalog- und Preisdaten zwischen Adobe Commerce (Cloud oder On-Premise) und [!DNL Adobe Commerce Optimizer] synchronisiert. Wenn Sie den Connector aktivieren, bleibt Commerce das Aufzeichnungssystem für Produktdaten, während [!DNL Adobe Commerce Optimizer] die Produkterkennung, Empfehlungen, Merchandising-Regeln, Analysen und Headless-Storefront-Erlebnisse unterstützt.

- [Übersicht über den Adobe Commerce Optimizer-Connector](../../aco-connector/overview.md){target="_blank"}
- [Erste Schritte mit dem Connector](../../aco-connector/get-started.md){target="_blank"}

## Produktvisualisierung mit AEM Assets {#product-visuals}

Mit Produktvisualisierungen können Sie Produktbilder über Adobe Experience Manager (AEM) Assets verwalten. Konfigurieren Sie AEM Assets für Commerce Optimizer, um Produktvisualisierung zu aktivieren. Nach Abschluss der Konfiguration verwenden Sie AEM Assets als zentralisierte Lösung für das Digital Asset Management für Ihre Produktbilder mit automatisierten Asset-Review- und -Management-Workflows, die die Bilder mit Ihrem Commerce Optimizer-Katalog synchronisieren. Die Integration ordnet Assets Produkten nach SKU zu. Aktualisierungen fließen durch die Integrations-Services von Adobe, sodass Storefronts die neuesten Medien widerspiegeln, ohne dass ein erneutes Hochladen erforderlich ist.

- [Produktvisualisierung mit AEM Assets](../setup/product-visuals.md)
- [Konfigurieren von AEM Assets für Commerce Optimizer](../../aem-assets-integration/get-started/configure-aco.md){target="_blank"}

## Adobe Experience Manager Sites Optimizer {#aem-sites-optimizer}

Adobe Experience Manager Sites Optimizer analysiert Commerce-Websites und verbessert die Leistung, indem KI-gesteuerte **[!UICONTROL Opportunities]** angezeigt werden - Empfehlungen, die Sie bei der Verbesserung der Erkennung, Interaktion und Konversionen unterstützen.

>[!AVAILABILITY]
>
>Für diese Funktion ist die **Ultima** Adobe Sites Optimizer-Lizenz erforderlich. Sie können eine Lizenz über Ihren technischen Adobe-Kundenberater anfordern. Sobald Ihr Konto bereitgestellt wurde, ist die Funktion „Opportunitys“ in der [!DNL Adobe Commerce Optimizer] verfügbar und Sie können mit KI-gesteuerten Einblicken beginnen, um Ihre Storefront- und Merchandising-Strategien zu optimieren.

- [Opportunities](../manage-results/opportunities.md)

## Commerce Salesforce Connector {#commerce-salesforce-connector}

Der Commerce Salesforce Connector (auf Adobe App Builder basiert) synchronisiert Katalog- und Preisdaten aus Salesforce Commerce Cloud B2C in [!DNL Adobe Commerce Optimizer], damit Sie Adobe-Storefront- und Merchandising-Funktionen verwenden können, ohne Ihr Salesforce Commerce-Backend neu zu platzieren. Sie können Synchronisationen planen, On-Demand-Aktualisierungen ausführen und die Integration mithilfe von Salesforce Commerce-APIs erweitern.

- [Salesforce Commerce Connector](../developer/salesforce-connector.md)

>[!MORELIKETHIS]
>
>- Technische Dokumentation zu [Adobe Commerce Optimizer](https://developer.adobe.com/commerce/services/optimizer/){target="_blank"}
>- [Erste Schritte mit Adobe Commerce Optimizer](../get-started.md)
