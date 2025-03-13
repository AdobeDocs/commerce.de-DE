---
title: Synchronisieren von Feeds mit der Commerce-CLI
description: Erfahren Sie, wie Sie die Befehle der Befehlszeilenschnittstelle verwenden, um Feeds und Prozesse für die SaaS [!DNL data export extension] Services von Adobe Commerce zu verwalten.
exl-id: 1ebee09e-e647-4205-b90c-d0f9d2cac963
source-git-commit: 086a571b69e8ad76a912c339895409b0037642b9
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# Synchronisieren von Feeds mit der Commerce-CLI

Mit dem Befehl `saas:resync` im `magento/saas-export` können Sie die Datensynchronisation für Adobe Commerce SaaS-Services verwalten.

Es wird von Adobe nicht empfohlen, den Befehl `saas:resync` regelmäßig zu verwenden. Typische Szenarien für die Verwendung des Befehls sind:

- Erstsynchronisierung
- Synchronisieren von Daten mit dem neuen Datenraum nach Änderung der [SaaS-Datenraum-ID](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas)
- Fehlerbehebung

Überwachen von Synchronisierungsvorgängen in der `var/log/saas-export.log`.

## Erstsynchronisierung

>[!NOTE]
>
>Die Erstsynchronisierung wird automatisch ausgeführt, wenn die Live Search oder die Produktempfehlungen aktiviert sind. Manuelle Befehle werden nicht benötigt.

Beim Trigger eines `saas:resync` über die Befehlszeile kann es je nach Kataloggröße einige Minuten bis einige Stunden dauern, bis die Daten aktualisiert werden.

Für die Erstsynchronisierung empfiehlt Adobe, die Befehle in der folgenden Reihenfolge auszuführen:

```shell
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

## Mit CLI-Befehlen synchronisieren

Der `saas:resync`-Befehl unterstützt verschiedene Synchronisierungsvorgänge:

- Teilweise Synchronisierung nach SKU
- Unterbrochene Synchronisationen fortsetzen
- Daten ohne Synchronisierung validieren

Alle verfügbaren Optionen anzeigen:

```shell
bin/magento saas:resync --help
```

In den folgenden Abschnitten finden Sie Optionsbeschreibungen mit Beispielen.


>[!NOTE]
>
>Erweiterte Optionen zur Verwaltung der Exportverarbeitung finden Sie unter [Exportverarbeitung anpassen](customize-export-processing.md).

## `--by-ids`

Bestimmte Entitäten anhand ihrer IDs teilweise neu synchronisieren. Unterstützt `products`-, `productAttributes`- und `productOverrides`.

Standardmäßig werden Entitäten durch die Produkt-SKU angegeben. Verwenden Sie stattdessen `--id-type=ProductID` , um Produkt-IDs zu verwenden.

**Beispiele:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>' --by-ids='<SKU-1>,<SKU-2>,<SKU-3>'

bin/magento saas:resync --feed='<FEED_NAME>' --by-ids='<ID-1>,<ID-2>,<ID-3>' --id-type='productId'
```

## `--cleanup-feed`

Bereinigt die Feed-Indexertabelle, bevor Daten neu indiziert und an SaaS gesendet werden. Wird nur für `products`-, `productOverrides`- und `prices`-Feeds unterstützt.

>[!IMPORTANT]
>
>Nur nach der Bereinigung der Umgebung verwenden. Kann zu Problemen bei der Datensynchronisation in Commerce Services führen.

**Beispiel:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>' --cleanup-feed
```

## `--continue-resync`

Setzt einen unterbrochenen Resynchronisierungsvorgang fort. Wird nur für `products`-, `productAttributes`- und `productOverrides`-Feeds unterstützt.

**Beispiel:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>' --continue-resync
```

## `--dry-run`

Führt den Feed-Neuindizierungsprozess aus, ohne an SaaS zu senden oder in der Feed-Tabelle zu speichern. Zur Datenvalidierung verwenden.

Fügen Sie die Umgebungsvariable `EXPORTER_EXTENDED_LOG=1` hinzu, um die Payload in `var/log/saas-export.log` zu speichern.

**Beispiel:**

```shell
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed='<FEED_NAME>' --dry-run
```

## `--feed`

Erforderlich. Gibt die Feed-Entität an, die neu synchronisiert werden soll.

Verfügbare Feeds:

- `categories`
- `categoryPermissions`
- `inventoryStockStatus`
- `orders`
- `prices`
- `products`
- `productAttributes`
- `productOverrides`
- `scopesWebsite`
- `scopesCustomerGroup`
- `variants`

**Beispiel:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>'
```

## `--no-reindex`

Sendet vorhandene Katalogdaten ohne Neuindizierung erneut an [!DNL Commerce Services]. Wird für produktbezogene Feeds nicht unterstützt.

Das Verhalten variiert je [Exportmodus](data-synchronization.md#synchronization-modes):

- Legacy-Modus: Setzt alle Daten erneut ab, ohne sie zu kürzen.
- Sofortiger Modus: Option wird ignoriert, nur Aktualisierungen/Fehler werden synchronisiert.

**Beispiel:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>' --no-reindex
```

## Fehlerbehebung

Wenn in Connected Commerce Services keine erwarteten Daten angezeigt werden, beheben Sie Probleme, indem Sie die Fehlerprotokolle für den Datenexport überprüfen und den `saas:resync`-Befehl mit Umgebungsvariablen verwenden, um Payloads und Profilerdaten zu überprüfen. Siehe [Protokolle überprüfen und Fehler beheben](troubleshooting-logging.md).
