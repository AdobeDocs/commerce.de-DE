---
title: Adobe Commerce Optimizer-Connector
description: Erfahren Sie, wie Sie Ihre Daten aus Ihrem Commerce Cloud- oder lokalen Projekt mit Adobe Commerce Optimizer verbinden
feature: Personalization, Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: 380d2c91a17a3e6b84d435774de1b05ada7d3a52
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---


# Adobe Commerce Optimizer-Connector

Der Adobe Commerce Optimizer-Connector ist die Integrationsbrücke, die Katalog- und Preisdaten zwischen einer Adobe Commerce in der Cloud-Infrastruktur oder einer lokalen Bereitstellung und [!DNL Adobe Commerce Optimizer] synchronisiert. Das Synchronisieren von Daten mit Adobe Commerce Optimizer ermöglicht Funktionen wie dynamische KI-Suchen, Empfehlungen, schnell ladende Headless-Storefronts, einschließlich Adobe Commerce-Storefronts auf Edge Delivery Services, und Echtzeit-Leistungsanalysen.

## Architektur und Erfahrung

Der Adobe Commerce Optimizer-Connector funktioniert durch die Zuordnung von Commerce-Websites und -Speicheransichten zu einem Commerce Optimizer-Projekt, wie in der folgenden Abbildung dargestellt:

![Zuordnen von Commerce-Daten zu Adobe Commerce Optimizer](./assets/storeview-to-catalogview-mapping.svg){width="600" zoomable="yes"}

Wenn Daten von Commerce nach Commerce Optimizer exportiert werden:

* Commerce-Store-Ansichten werden Katalogquellen zugeordnet
* Websites werden Preisbüchern zugeordnet

Die zugehörigen Katalog- und Preisdaten werden exportiert und später zum Erstellen von Katalogansichten und optional zum Definieren einer Richtlinie zum Filtern der Katalog- und Preisdaten für bestimmte geschäftliche Anwendungsfälle verwendet.

Anstatt Commerce-Services (Live Search und Product Recommendations) über den Commerce-Administrator zu konfigurieren und zu verwalten, verwenden Sie [[!DNL Adobe Commerce Optimizer] Merchandising-Tools](../optimizer/merchandising/overview.md) um die Regelkonfiguration für die Produkterkennung (Live Search) und Recommendations (Product Recommendations) zu verwalten. Die Adobe Commerce-Instanz wird zur Datenquelle für Katalog- und Preisdaten. Wenn die Daten in Commerce aktualisiert werden, werden die Aktualisierungen mit der [!DNL Adobe Commerce Optimizer] synchronisiert.

## Workflows

Der Connector ermöglicht mehrere wichtige Workflows:

* **Exportieren von Commerce-Katalogdaten nach[!DNL Adobe Commerce Optimizer]** - Preis- und Preisbuchdaten werden auf Website- und Kundengruppenebene exportiert. Produkt- und Produktattributdaten werden auf `store view` exportiert. Standardmäßig ist die Synchronisierung von Katalogdaten für alle Commerce-Bereiche (Websites und Store-Ansichten) aktiviert.

  Um diesen Workflow zu aktivieren, installieren Sie die `adobe-commerce/commerce-data-export-aco-adapter` PHP-Erweiterung, überprüfen Sie die Exporter-Konfiguration und aktivieren Sie dann über die Commerce-Admin die Integration zwischen Commerce und Commerce Optimizer. Detaillierte Anweisungen finden Sie unter [Erste Schritte](#get-started).

* **Ordnen Sie die Commerce-Website zu und speichern Sie Ansichtsdaten, die in exportiert werden sollen[!DNL Adobe Commerce Optimizer]**

  Optional können Sie die Exporteinstellungen anpassen, um Daten nur für bestimmte Websites oder Store-Ansichten zu synchronisieren. Sie können beispielsweise festlegen, dass Katalogdaten für nur eine Store-Ansicht exportiert werden, um sie für einen bestimmten Anwendungsfall zu verwenden, z. B. die Optimierung der Suche für einen bestimmten Markt oder eine bestimmte Region.

* **Konfiguration und Verwaltung von Merchandising-Regeln**

  Wenn der Connector aktiviert ist, werden Merchandising-Regeln für die Produkterkennung und Empfehlungen über die [!DNL Adobe Commerce Optimizer] Benutzeroberfläche definiert und verwaltet, nicht über die Seiten [!UICONTROL Live Search] und [!UICONTROL Product Recommendations] in Commerce Admin.

* **Bereitstellen der Commerce-Storefront auf Edge Delivery Services**

  Nach der Einrichtung der Integration mit [!DNL Adobe Commerce Optimizer] können Sie eine Commerce-Storefront auf Edge Delivery Services einrichten und bereitstellen, um mithilfe der zusammenstellbaren, API-gesteuerten Architektur und der modularen Komponenten, die mit [!DNL Adobe Commerce Optimizer] verfügbar sind, ultraschnelle Leistung, Skalierbarkeit, nahtlose Inhaltserstellung, integrierte Personalisierung und reduzierte Betriebskosten zu erzielen.

Weitere Informationen zum Einrichten der Integration und Aktivieren dieser Workflows finden Sie unter [Erste Schritte](get-started.md).
