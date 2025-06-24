---
title: Preisbücher
description: Erfahren Sie, wie Sie Preislisten in  [!DNL Adobe Commerce Optimizer] verwalten.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 553490762ef10e43ccce1654acec59aeb83bb5f9
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Preisbücher

In diesem Artikel wird beschrieben, wie Sie Preislisten definieren und Katalogansichten mit ordnungsgemäßen Data Governance-Kontrollen zuweisen.

In der [Entwicklerdokumentation](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/api-reference/#tag/Price-Books) erfahren Sie, wie Sie Preisbuchinformationen von einem Drittanbietersystem mithilfe der Preisbuch-API in [!DNL Adobe Commerce Optimizer] aufnehmen können.

Mit Preisverzeichnissen können Sie Preiskatalogquellen definieren, um Produktpreise über verschiedene Kundenebenen und Märkte hinweg zu verwalten. Preisbücher unterstützen ein hierarchisches Modell, das bis zu drei Ebenen verschachtelter untergeordneter Preisbücher unter jedem Grundpreisbuch ermöglicht. Jedes Preisbuch kann auf ein übergeordnetes Preisbuch verweisen und so eine Baumstruktur für Preiskatalogquellen bilden.

Der Basispreis definiert die Währung für sich selbst und alle untergeordneten Preisbücher. Untergeordnete Preisbücher übernehmen diese Währung und können sie nicht überschreiben.

## Schlüsselkonzepte

| Begriff | Beschreibung |
|------|-------------|
| **Preisbuch** | Logische Gruppierung, die die Preiskatalogquelle definiert, z. B. eine bestimmte Region oder Kundenebene, und zur Verwaltung von Produktpreisen verwendet wird. |
| **Fallback-Preisbuch** | Das beste Preisbuch in einer Hierarchie. Es hat kein übergeordnetes Element und ist das *einzige* Preisbuch, das die Währung für sich selbst und alle seine untergeordneten Preisbücher definiert.<br/><br/>Wenn bei der Erstellung des Preisbuchs (über die API) kein übergeordnetes Element definiert wird, wird ein neues Fallback-Preisbuch erstellt. |
| **Übergeordnetes Preisbuch** | Ein übergeordnetes Preisbuch, aus dem ein untergeordnetes Preisbuch Preise übernehmen kann, wenn diese nicht explizit im Kind festgelegt sind. |
| **Hierarchietiefe** | Maximal drei Stufen (Fallback → Kind → Enkelkind), <br/><br/> bei der Aufnahme nicht erzwungen werden. |
| **Währung** | Wird nur für Fallback-Preisbuch definiert. Von allen Kindern geerbt, Preisbücher.<br/><br/>Wenn die Währung bei der Erstellung des Fallback-Preisbuchs (über die API) nicht angegeben wird, ist die Währung standardmäßig USD. |
| **Produktpreis** | Der spezifische Preis, der einem Produkt (SKU) innerhalb eines bestimmten Preisbuchs zugewiesen ist. |
| **Rabatte** | Rabatte sind im Produktpreis definiert. Nicht vererbt. |
