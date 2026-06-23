---
title: Referenz zum Feed-Tabellenschema
description: Erfahren Sie mehr über das Feed-Tabellenschema, das von  [!DNL Adobe Commerce Optimizer Connector]  verwendet wird, um den Status von Feed-Elementen, den Exportstatus und Fehlerdetails zu verfolgen.
autotag-review: '2026-06-23T00:00:00.000Z'
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 19de20caafd45e3a00896d0d4b29b7e96dfe94e1
workflow-type: tm+mt
source-wordcount: 324
ht-degree: 0%

---


# Referenz zum Feed-Tabellenschema

Jeder Feed verfügt über eine dedizierte MySQL-Tabelle in der [!DNL Adobe Commerce]. Alle Feed-Tabellen verwenden dieselbe Spaltenstruktur.

## Unterstützte Feeds

Eine vollständige Liste der unterstützten Feeds mit API-Endpunkten, Batch-Beschränkungen, Indexernamen und Feed-Tabellennamen finden Sie unter [Connector-Module und Feed-Endpunkte](connector-reference.md#supported-feeds).

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
| `status` | INT | Übermittlungsstatus-Code vom letzten Exportversuch. Siehe [Feed-Übermittlung und Fehlerbehandlung](../connector-sync-pipeline.md#feed-submission-and-error-handling). |
| `errors` | TEXT | Von der [!DNL Commerce Optimizer]-API für dieses Element zurückgegebene JSON-kodierte Fehlerdetails |
| `metadata` | JSON | Interne Synchronisierungs-Flags und Sperr-Metadateninformationen, die vom Export-Framework verwendet werden |

## Häufige Diagnoseabfragen

Verwenden Sie die folgenden SQL-Abfragen, um den Status der Feed-Tabelle direkt zu überprüfen. Die Spalte `feed_data` speichert Daten im [!DNL Adobe Commerce Optimizer]-API-Format. Ersetzen Sie Platzhalterwerte wie `<SKU>`, `<ATTRIBUTE_CODE>`, `<SLUG>` und `<PRICE_BOOK_ID>` durch tatsächliche Werte aus Ihrer Umgebung.

**Produkt-Feed - nach SKU:**

```sql
SELECT JSON_EXTRACT(f.feed_data, '$.sku') AS 'SKU',
       JSON_EXTRACT(f.feed_data, '$.source.locale') AS 'locale',
       f.status, f.modified_at, f.is_deleted, f.errors
FROM cde_products_feed f
WHERE JSON_EXTRACT(f.feed_data, '$.sku') IN ('<SKU>');
```

**Feed für Produktattribute - nach Attributcode:**

```sql
SELECT JSON_EXTRACT(f.feed_data, '$.code') AS 'code',
       JSON_EXTRACT(f.feed_data, '$.source.locale') AS 'locale',
       f.status, f.modified_at, f.is_deleted, f.errors
FROM cde_product_attributes_feed f
WHERE JSON_EXTRACT(f.feed_data, '$.code') IN ('<ATTRIBUTE CODE>');
```

**Feed der Kategorien - nach URL-Pfad:**

```sql
SELECT JSON_EXTRACT(f.feed_data, '$.slug') AS 'slug',
    JSON_EXTRACT(f.feed_data, '$.source.locale') AS 'locale',
    f.status, f.modified_at, f.is_deleted, f.errors
FROM cde_categories_feed f
WHERE JSON_EXTRACT(f.feed_data, '$.slug') IN ('<SLUG>');
```

**Preise Feed - nach SKU:**

```sql
SELECT JSON_EXTRACT(f.feed_data, '$.sku') AS 'SKU',
       JSON_EXTRACT(f.feed_data, '$.priceBookId') AS 'price book ID',
       f.status, f.modified_at, f.is_deleted, f.errors
FROM cde_product_prices_feed f
WHERE JSON_EXTRACT(f.feed_data, '$.sku') IN ('<SKU>');
```

**Preisbuch-Feed - nach Preisbuch-ID:**

```sql
SELECT JSON_EXTRACT(f.feed_data, '$.priceBookId') AS 'price book ID',
    JSON_EXTRACT(f.feed_data, '$.name') AS 'name',
    JSON_EXTRACT(f.feed_data, '$.parentId') AS 'parent price book ID',
    JSON_EXTRACT(f.feed_data, '$.currency') AS 'currency',
    f.status, f.modified_at, f.is_deleted, f.errors
FROM cde_price_books_feed f
WHERE JSON_UNQUOTE(JSON_EXTRACT(f.feed_data, '$.priceBookId'))  IN ('<PRICE_BOOK_ID>');
```

>[!MORELIKETHIS]
>
>- [Connector-Module und Feed-Endpunkte](connector-reference.md)
>- [Connector-Synchronisierungs-Pipeline](../connector-sync-pipeline.md)
>- [Synchronisierung verwalten](../data-sync-manage.md)
>- [Feldzuordnung für Connector-Feeds](field-mapping.md)
