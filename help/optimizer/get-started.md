---
title: Erste Schritte mit [!DNL Adobe Commerce Optimizer]
description: Erfahren Sie mehr über die ersten Schritte mit [!DNL Adobe Commerce Optimizer].
hide: true
recommendations: noCatalog
source-git-commit: d716dd9d75beb642bfad30271b6ecd3490ee7328
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Erste Schritte

>[!NOTE]
>
>In dieser Dokumentation wird ein Produkt beschrieben, das sich in der Entwicklung für den frühzeitigen Zugriff befindet und nicht alle für die allgemeine Verfügbarkeit vorgesehenen Funktionen enthält.

Dieses Handbuch führt Sie durch die Erstellung und Arbeit mit einer [!DNL Adobe Commerce Optimizer].

<!--Click the tabs below to see high-level workflow overviews for the following user types:

- Administrators
- Merchants
- Developers

>[!BEGINTABS]

>[!TAB Administrator and merchant workflow]

This diagram provides a high-level overview of how administrators and merchants access and manage [!DNL Adobe Commerce Optimizer] instances. See the [Adobe Admin Console Guide](https://helpx.adobe.com/de/enterprise/admin-guide.html) for more information about administrator workflows.

NEED DIAGRAM

>[!TAB Developer workflow]

This diagram provides a high-level overview of how developers create integrations for [!DNL Adobe Commerce Optimizer] using App Builder. See the [API documentation](https://developer.adobe.com/commerce/services/cloud/) for more information.

NEED DIAGRAM

>[!ENDTABS]
-->

## Bereitstellung

Sobald die [!DNL Adobe Commerce Optimizer] Instanzen fertig sind, stellt Ihnen das [!DNL Adobe Commerce Optimizer]-Bereitstellungs-Team die folgenden Endpunkte bereit:

| Element | Beispiel-URL | Zweck |
|---|---|---|
| [!DNL Adobe Commerce Optimizer] Benutzeroberfläche | `https://experience.adobe.com/#/@commerceprojectbeacon/commerce-optimizer-studio?tenant=<tenantId>` | Greifen Sie auf die Commerce Optimizer-Benutzeroberfläche zu, um Ihren Katalog über:<br>1 zu verwalten. Merchandising-Regeln (Produkterkennung, Produktempfehlungen).<br>2. Katalogverwaltung (Erstellung von Kanälen und Richtlinien).<br>3. Data Insights (Anzeigen des Datenerfassungsstatus Ihres Katalogs). |
| Storefront-APIs | `https://na1-sandbox.api.commerce.adobe.com/<tenantId>/graphql` | Greifen Sie auf die APIs zu, die zum Einrichten Ihrer Commerce-Storefront mit Edge Delivery Services erforderlich sind. |
| APIs zur Katalogdatenaufnahme | `https://na1-sandbox.api.commerce.adobe.com/<tenantId>/v1/catalog/<entity>` | Greifen Sie auf die APIs zu, die zum Aufnehmen Ihrer Katalogdaten erforderlich sind. |

Als Teilnehmer mit frühzeitigem Zugriff erhalten Sie eine E-Mail mit einem sicheren Link, über den Sie sich zusammen mit Ihrem IMS-Token bei [!DNL Adobe Commerce Optimizer] anmelden oder API-Aufrufe ausführen können.

## Einrichten der Storefront

Nachdem Sie nun über eine [!DNL Adobe Commerce Optimizer]-Instanz verfügen, können Sie mit dem Einrichten [ Commerce-Storefront ](./storefront.md) Edge Delivery Services fortfahren.

## Verfügbare Katalogdaten für Teilnehmer mit frühzeitigem Zugriff

Als Teilnehmer mit frühzeitigem Zugriff enthält die [!DNL Adobe Commerce Optimizer]-Instanz Pseudo-Katalogdaten, die auf dem [Carvelo-Anwendungsfall“ ](./use-case/admin-use-case.md). Die Pseudo-Daten sowie einige vorkonfigurierte Kanäle und Richtlinien helfen Ihnen, sich mit der [!DNL Adobe Commerce Optimizer]-Benutzeroberfläche vertraut zu machen.

<!--Ingest catalog data

By default, [!DNL Adobe Commerce Optimizer] instances do not include any product data.

See the [Ingestion API](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/using-the-api/) documentation to learn how you can import your catalog data into [!DNL Adobe Commerce Optimizer].

The catalog data that you ingest is visible in the [data insights](./insights-overview.md) page. Additionally, you can use the [Catalog](./catalog-overview.md) page to define the channels and policies.-->
