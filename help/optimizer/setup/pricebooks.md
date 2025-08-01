---
title: Preisbücher
description: Erfahren Sie, wie Sie Preislisten in  [!DNL Adobe Commerce Optimizer] verwalten.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: a1849830-3d0e-4df9-ab73-380659c3f9dc
source-git-commit: 502d8d21ff052f4ecb212176459b38ce51f85dfc
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Preisbücher

Mit Preislisten können Sie Produktpreise für eine Katalogquelle über verschiedene Kundenebenen und Märkte hinweg definieren. Preisbücher unterstützen ein hierarchisches Modell, das bis zu drei Ebenen verschachtelter untergeordneter Preisbücher unter jedem Grundpreisbuch ermöglicht. Jedes Preisbuch kann auf ein übergeordnetes Preisbuch verweisen und so eine Baumstruktur für Preiskatalogquellen bilden.

Der Basispreis definiert die Währung für sich selbst und alle untergeordneten Preisbücher. Untergeordnete Preisbücher übernehmen diese Währung und können sie nicht überschreiben.

In der [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/reference/rest/) erfahren Sie, wie Sie Preisbücher für [!DNL Adobe Commerce Optimizer] mithilfe der Preisbuch-API erstellen, aktualisieren und löschen können.

## Schlüsselkonzepte

| Begriff | Beschreibung |
|------|-------------|
| **Preisbuch** | Logische Gruppierung, die Preise für eine Katalogquelle definiert, z. B. eine bestimmte Region oder Kundenebene, und zur Verwaltung von Produktpreisen verwendet wird. |
| **Fallback-Preisbuch** | Das beste Preisbuch in einer Hierarchie. Es hat kein übergeordnetes Element und ist das *einzige* Preisbuch, das die Währung für sich selbst und alle seine untergeordneten Preisbücher definiert.<br/><br/>Wenn bei der Erstellung des Preisbuchs (über die API) kein übergeordnetes Element definiert wird, wird ein neues Fallback-Preisbuch erstellt. |
| **Übergeordnetes Preisbuch** | Ein übergeordnetes Preisbuch, aus dem ein untergeordnetes Preisbuch Preise übernehmen kann, wenn diese nicht explizit im Kind festgelegt sind. |
| **Hierarchietiefe** | Maximal drei Ebenen (Fallback -> Untergeordnet -> Enkelkind), <br/><br/> bei der Aufnahme nicht erzwungen werden. |
| **Währung** | Wird nur für das Fallback-Preisbuch definiert. Von allen untergeordneten Preisbüchern übernommen.<br/><br/>Wenn die Währung bei der Erstellung des Fallback-Preisbuchs (über die API) nicht angegeben wird, ist die Währung standardmäßig USD. |
| **Produktpreis** | Der spezifische Preis, der einem Produkt (SKU) innerhalb eines bestimmten Preisbuchs zugewiesen ist. |
| **Rabatte** | Rabatte sind im Produktpreis definiert. Nicht vererbt. |
