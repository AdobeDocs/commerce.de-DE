---
title: Referenz zum Feed-Tabellenschema
description: Erfahren Sie mehr über das Feed- [!DNL SaaS Data Export] -Schema, das von zur Verfolgung des Status von Feed-Elementen, des Exportstatus und von Fehlerdetails verwendet wird.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
feature: Services
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: cc250cf1-34eb-4863-80d0-d170d45ea067
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 416
ht-degree: 0%

---


# Referenz zum Feed-Tabellenschema

Jeder Feed verfügt über eine dedizierte MySQL-Tabelle in der [!DNL Adobe Commerce]. Alle Feed-Tabellen verwenden dieselbe Spaltenstruktur. In der folgenden Tabelle sind alle Feeds mit ihrem CLI-Feed-Namen, ihrer Indexer-ID und ihrem Feed-Tabellennamen aufgeführt.

## Unterstützte Feeds

Die tatsächliche Liste der Feeds hängt vom installierten [!DNL SaaS Data Export] ab.


| Feed (`--feed`) | Zweck | Indexer-ID | Vorschubtisch | Exportmodus |
| --- | ------------------------------------------------------------------- | --- | --- | --- |
| `products` | Produktkatalog (Attribute, Kategorien, Bilder usw.) | `catalog_data_exporter_products` | `cde_products_feed` | Immediate |
| `productAttributes` | Attributdefinitionen und Metadaten. Wird zum Definieren des Suchschemas verwendet. | `catalog_data_exporter_product_attributes` | `cde_product_attributes_feed` | Immediate |
| `categories` | Kategoriedaten | `catalog_data_exporter_categories` | `cde_categories_feed` | Immediate |
| `prices` | Produktpreise mit Kundengruppenpreisen und Stufenpreisen | `catalog_data_exporter_product_prices` | `cde_product_prices_feed` | Immediate |
| `variants` | Konfigurierbare Produktvarianten | `catalog_data_exporter_product_variants` | `cde_product_variants_feed` | Immediate |
| `scopesWebsite` | Website mit Shop-Ansichtscodes | `scopes_website_data_exporter` | `scopes_website_data_exporter` | Veraltet |
| `scopesCustomerGroup` | Definitionen der Kundengruppen | `scopes_customergroup_data_exporter` | `scopes_customergroup_data_exporter` | Veraltet |
| `productOverrides` | Berechnete Produktberechtigungen | `catalog_data_exporter_product_overrides` | `cde_product_overrides_feed` | Immediate |
| `categoryPermissions` *(EE)* | Rohdaten für Kategorieberechtigungen | `catalog_data_exporter_category_permissions` | `cde_category_permissions_feed` | Immediate |
| `orders` | Status der Kundenaufträge | `sales_order_data_exporter_v2` | `sales_data_exporter_orders_v2` | Veraltet |

Die Spalte **Exportmodus** gibt an, wie jeder Feed Daten erfasst und sendet:

- **Feeds im sofortigen Modus** - Erfassen Sie Daten, überspringen Sie unveränderte Elemente mithilfe von Inhalts-Hashes (Hash-Deduplizierung) und senden Sie Aktualisierungen im selben Indexerlauf.
- **Legacy-Modus-Feeds** (`scopesWebsite`, `scopesCustomerGroup`, `orders`) - Speichern Sie zusammengestellte Daten zuerst in der Feed-Tabelle und senden Sie sie über einen separaten Cron-Auftrag.

Siehe [Synchronisierungsmodi](../sync-overview.md#synchronization-modes).

## Schema

| Spalte | Typ | Beschreibung |
| --- | --- | ---------------- |
| `id` | INT (PK) | Primärschlüssel automatisch inkrementieren |
| `source_entity_id` | INT | Entitäts-ID aus der Commerce-Quelltabelle (z. B. `catalog_product_entity.entity_id`) |
| `feed_id` | VARCHAR | Eindeutige Kennung für ein Feed-Element. Wird als Hash der Identitätsfelder des Elements (z. B. `sku + storeViewCode`) berechnet und nicht als automatischer Inkrementwert. |
| `feed_data` | JSON | Feed-Payload für dieses Element. Es werden nur minimale Informationen als Entitätskennung und Umfang ausgefüllt. Wenn `PERSIST_EXPORTED_FEED=1` festgelegt ist, wird die vollständige Payload gespeichert. |
| `feed_hash` | VARCHAR | Für die Änderungserkennung verwendeter Inhaltshash Aus der Payload berechnet, ohne Zeitstempel (`modifiedAt`, `updatedAt`). Wenn der Hash mit dem vorherigen Export übereinstimmt, wird das Element nicht erneut übermittelt. |
| `is_deleted` | TINYINT | Markierung für Soft-Löschen. Legen Sie dies auf `1` fest, wenn die Entität in Commerce gelöscht wird. |
| `modified_at` | ZEITSTEMPEL | Letztes Mal, als dieses Feed-Element geändert wurde |
| `status` | INT | Übermittlungsstatus-Code vom letzten Exportversuch. Siehe [Feed-Übermittlung und HTTP-](../sync-overview.md#feed-submission-and-http-error-handling). |
| `errors` | TEXT | JSON-kodierte Fehlerdetails, die vom SaaS-Service für dieses Element zurückgegeben werden |
| `metadata` | JSON | Interne Synchronisierungs-Flags und Sperr-Metadateninformationen, die vom Export-Framework verwendet werden |

## Häufige Diagnoseabfragen

Verwenden Sie die folgenden SQL-Abfragen, um den Status der Feed-Tabelle direkt zu überprüfen. Ersetzen Sie `cde_products_feed` durch die Tabelle für den Feed, den Sie untersuchen. Siehe [Unterstützte Feeds](#supported-feeds) für die vollständige Liste der Tabellennamen.

**Suchen Sie alle Elemente, die nicht erfolgreich exportiert wurden:**

```sql
SELECT source_entity_id, status, errors, modified_at
FROM cde_products_feed
WHERE status != 200
ORDER BY modified_at DESC
LIMIT 50;
```

**Überprüfen des Exportstatus für eine bestimmte SKU über alle Bereiche hinweg:**

```sql
SELECT p.sku, f.status, f.modified_at, f.is_deleted, f.feed_data, f.errors
FROM catalog_product_entity p
LEFT JOIN cde_products_feed f ON f.source_entity_id = p.entity_id
WHERE p.sku = 'ADB295';
```


>[!MORELIKETHIS]
>
>- [Synchronisieren von Daten mit dem SaaS-Datenexport](../sync-overview.md)
>- [Synchronisierung anzeigen und verwalten](../data-sync-manage.md)
>- [Synchronisieren Sie Feeds mithilfe der Commerce-CLI](../data-export-cli-commands.md)
