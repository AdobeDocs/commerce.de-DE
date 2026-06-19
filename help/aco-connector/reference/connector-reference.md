---
title: '[!DNL Adobe Commerce Optimizer Connector] Module und Feed-Endpunkte'
description: Erfahren Sie  [!DNL Adobe Commerce Optimizer Connector]  über -Module, Katalog-Feed-API-Endpunkte, Batch-Beschränkungen und core_config_data-Konfigurationspfade für  [!DNL Adobe Commerce].
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T15:48:19.494Z'
TQID: 'https://experienceleague.adobe.com/UM6Y-xoQpUDzWpaMe1GRPp4XoAtHBLBsHw388kumN8g'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7id: c32adafa-ed01-4b31-997e-2413013911b0id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 296
ht-degree: 1%

---

# Connector-Module und Feed-Endpunkte

Diese Referenz listet die [!DNL Adobe Commerce Optimizer Connector], unterstützten Feed-API-Endpunkte und Konfigurationsschlüsselpfade auf, die in `core_config_data` gespeichert sind. Informationen zur Zusammenarbeit dieser Komponenten während der Synchronisierung finden Sie unter [Connector-Synchronisierungs-Pipeline](../connector-sync-pipeline.md).

## Module

Der Connector enthält mehrere Magento-Module, die Katalogdaten erfassen, Feed-Daten dem von der [!DNL Commerce Optimizer]-API unterstützten Format zuordnen und Übermittlung und Umfangssteuerung verwalten. In der folgenden Tabelle sind die einzelnen Module und ihre Rollen zusammengefasst.

| Modul | Rolle |
| ------ | ---- |
| `DataExporterAdapter` | Ordnet [!DNL Adobe Commerce] Feeds dem Format zu, das für die [!DNL Adobe Commerce Optimizer]-API erforderlich ist. Überschreibt den Feed-Pool und die Schemakonfiguration. |
| `SaasExportAdapter` | Leitet [!DNL Commerce Optimizer] Feeds zur Aufnahme-API weiter und blockiert nicht unterstützte Feeds bei der Übermittlung. |
| `CommerceAcoExporter` | Verwaltet [!DNL Commerce Optimizer] Anmeldeinformationen und stellt CLI-Setup-Befehle bereit |
| `CommerceAdapter` | [!DNL Commerce Optimizer] API-Kompatibilitätsebene (GraphQL, Bundle, In den Warenkorb legen, Benutzeroberfläche konfigurieren) |
| `PriceBookDataExporter` | Preisbuch-Feed indiziert nach Website und Kundengruppe |
| `SaasPriceBook` | SaaS-Infrastruktur für die Preisbucheinreichung |
| `CommerceOptimizerScopeMapper` | Aktivierung der Synchronisierung pro Website und pro Store-Ansicht |

## Unterstützte Feeds

Der Connector sendet mehrere Feed-Typen an die [!DNL Commerce Optimizer] [[!DNL Catalog Data Ingestion API]](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/){target="_blank"}. In der folgenden Tabelle sind alle Feeds mit ihrem Endpunkt, ihrer Batch-Grenze, ihrem Indexernamen und ihrer Feed-Tabelle in [!DNL Adobe Commerce] aufgeführt.

| Futter | API-Endpunkt [!DNL Commerce Optimizer] | Batch-Limit | AC-Indexname | Vorschubtisch |
| ---- | ----------------------------------- | ----------- | ------------- | ---------- |
| `products` | `POST /v1/catalog/products` | 100 | `catalog_data_exporter_products` | `cde_products_feed` |
| `categories` | `POST /v1/catalog/categories` | 100 | `catalog_data_exporter_categories` | `cde_categories_feed` |
| `productAttributes` | `POST /v1/catalog/products/metadata` | 100 | `catalog_data_exporter_product_attributes` | `cde_product_attributes_feed` |
| `prices` | `POST /v1/catalog/products/prices` | 500 | `catalog_data_exporter_product_prices` | `cde_product_prices_feed` |
| `priceBooks` | `POST /v1/catalog/price-books` | 500 | `data_exporter_price_books` | `cde_price_books_feed` |

Die `products`-, `productAttributes`-, `categories`- und `prices`-Feeds verwenden von [!DNL SaaS Data Export]-Indexern erfasste Daten wieder. Der Connector generiert den `priceBooks`-Feed aus der Website- und Kundengruppenkonfiguration und verlässt sich nicht auf einen [!DNL SaaS Data Export].

Details zur Zuordnung auf Feldebene für jeden Feed finden Sie unter [Feldzuordnung für  [!DNL Commerce Optimizer Connector] -Feeds](field-mapping.md).
Informationen zur Schätzung der Dauer einer Synchronisierung basierend auf Ihrer Kataloggröße finden Sie unter [Schätzen des Datenvolumens und der Synchronisierungszeit](estimate-data-volume-sync-time.md).

## Konfigurationspfade

[!DNL Commerce Optimizer Connector] Anmeldeinformationen und Service-URLs werden in `core_config_data` unter dem Präfix `aco_exporter/general/` gespeichert. Führen Sie `bin/magento aco:config:show` aus, um die aktuellen Werte zu überprüfen. Der Befehl zeigt das Client-Geheimnis nicht an.

```text
aco_exporter/general/org_id
aco_exporter/general/tenant_id
aco_exporter/general/client_id
aco_exporter/general/client_secret       (encrypted)
aco_exporter/general/type
aco_exporter/general/ingestion_url
aco_exporter/general/optimizer_studio_url
```
