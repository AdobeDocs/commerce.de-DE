---
title: Synchronisieren von Feeds mit der Commerce-CLI
description: Erfahren Sie, wie Sie die Befehle der Befehlszeilenschnittstelle verwenden, um Feeds und Prozesse für die SaaS [!DNL data export extension] Services von Adobe Commerce zu verwalten.
exl-id: 1ebee09e-e647-4205-b90c-d0f9d2cac963
source-git-commit: 8233b2e184c8af293ffc41cb22e085388cf18049
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Synchronisieren von Feeds mit der Commerce-CLI

Mit dem Befehl `saas:resync` im `magento/saas-export` können Sie die Datensynchronisation für Adobe Commerce SaaS-Services verwalten.

Es wird von Adobe nicht empfohlen, den Befehl `saas:resync` regelmäßig zu verwenden. Typische Szenarien für die Verwendung des Befehls sind:

- Erstsynchronisierung
- Synchronisieren von Daten mit einem neuen Datenraum nach Änderung der [SaaS-Datenraum-ID](https://experienceleague.adobe.com/de/docs/commerce-admin/config/services/saas)
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

Bestimmte Entitäten anhand ihrer IDs teilweise neu synchronisieren. Unterstützt `products`-, `productAttributes`-, `productOverrides`-, `inventoryStockStatus`-, `prices`-, `variants`- und `categoryPermissions`.

Wenn Sie die Option &quot;`--by-ids`&quot; verwenden, geben Sie Werte standardmäßig mithilfe von Produkt-SKU-Werten an. Um stattdessen Produkt-IDs zu verwenden, fügen Sie die Option `--id-type=ProductID` hinzu.

**Beispiele:**

```shell
bin/magento saas:resync --feed products --by-ids='ADB102,ADB111,ADB112'

bin/magento saas:resync --feed= products --by-ids='1,2,3' --id-type='productId'
```


## `--cleanup-feed`

Bereinigen Sie die Feed-Indexertabelle, bevor Sie Daten neu indizieren und an SaaS senden. Wird nur für `products`, `productAttributes`, `productOverrides`, `inventoryStockStatus`, `prices`, `variants` und `categoryPermissions` unterstützt.

Bei Verwendung mit der Option `--dry-run` führt der Vorgang einen Probelauf-Resynchronisierungsvorgang für alle Elemente durch.

>[!IMPORTANT]
>
>Nur nach der Umgebungsbereinigung oder mit der Option `--dry-run` verwenden. In anderen Fällen kann der Bereinigungsvorgang zu Datenverlust und Problemen mit der Datensynchronisation führen.

**Beispiel:**

```shell
bin/magento saas:resync --feed products --cleanup-feed
```

## `--continue-resync`

Setzt einen unterbrochenen Resynchronisierungsvorgang fort. Wird nur für `products`-, `productAttributes`- und `productOverrides`-Feeds unterstützt.

**Beispiel:**

```shell
bin/magento saas:resync --feed productAttributes --continue-resync
```

## `--dry-run`

Führt den Feed-Neuindizierungsprozess aus, ohne den Feed an SaaS zu senden und ohne in der Feed-Tabelle zu speichern. Diese Option ist nützlich, um Probleme mit Ihrem Datensatz zu identifizieren.

Fügen Sie die Umgebungsvariable `EXPORTER_EXTENDED_LOG=1` hinzu, um die Payload in `var/log/saas-export.log` zu speichern.

**Beispiel:**

```shell
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed products --dry-run
```

### Testen spezifischer Feed-Elemente

Testen Sie bestimmte Feed-Elemente, indem Sie die Option `--by-ids` mit der erweiterten Protokollsammlung hinzufügen, um die generierte Payload in der `var/log/saas-export.log`-Datei anzuzeigen.

**Beispiel:**

```shell
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed products --dry-run --by-ids='ADB102,ADB111,ADB112'
```

### Alle Feed-Elemente testen

Standardmäßig enthält der während eines `resync --dry-run` gesendete Feed nur neue Elemente oder Elemente, die zuvor nicht exportiert werden konnten. Um alle Elemente in den zu verarbeitenden Feed einzubeziehen, verwenden Sie die Option `--cleanup-feed` .

**Beispiel**

```shell
bin/magento saas:resync --feed products --dry-run --cleanup-feed
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
bin/magento saas:resync --feed products
```

## `--no-reindex`

Sendet vorhandene Katalogdaten ohne Neuindizierung erneut an [!DNL Commerce Services]. Wird für produktbezogene Feeds nicht unterstützt.

Das Verhalten variiert je [Exportmodus](data-synchronization.md#synchronization-modes):

- Legacy-Modus: Setzt alle Daten erneut ab, ohne sie zu kürzen.
- Sofortiger Modus: Option wird ignoriert, nur Aktualisierungen/Fehler werden synchronisiert.

**Beispiel:**

```shell
bin/magento saas:resync --feed productAttributes --no-reindex
```

## `--id-type=ProductId`

Standardmäßig werden die Entitäten, die bei Verwendung des Befehls `saas:resync feed` mit der Option `--by-ids` angegeben werden, durch die Produkt-SKU angegeben. Verwenden Sie die Option `--id-type=ProductId` , um Entitäten nach Produkt-ID anzugeben.

```shell
bin/magento saas:resync --feed products --by-ids='1,2,3' --id-type='productId'
```

**Beispiel:**

## Fehlerbehebung

Wenn in Connected Commerce Services keine erwarteten Daten angezeigt werden, beheben Sie Probleme, indem Sie die Fehlerprotokolle für den Datenexport überprüfen und den `saas:resync`-Befehl mit Umgebungsvariablen verwenden, um Payloads und Profilerdaten zu überprüfen. Siehe [Protokolle überprüfen und Fehler beheben](troubleshooting-logging.md).
