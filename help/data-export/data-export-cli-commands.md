---
title: Synchronisieren von Feeds mit der Commerce-CLI
description: Erfahren Sie, wie Sie Commerce-CLI-Befehle verwenden, um Feeds und Synchronisierungsprozesse für die  [!DNL data export extension]  in Adobe Commerce SaaS-Services zu verwalten.
autotag-review: '2026-06-17T15:08:59.000Z'
exl-id: 1ebee09e-e647-4205-b90c-d0f9d2cac963
TQID: 'https://experienceleague.adobe.com/Vi8hMKOBjTPkSQp0t8DCkjZsJ8s3Q5GSbSXyX2gmWRo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: ef1a9efc579d8d21c145e6981235489a2e4ea203
workflow-type: tm+mt
source-wordcount: 728
ht-degree: 0%

---

# Synchronisieren von Feeds mit der Commerce-CLI

Mit dem `saas:resync`-Befehl im `magento/saas-export` können Sie die Datensynchronisation für [!DNL Adobe Commerce] SaaS-Services verwalten.

>[!NOTE]
>
>Der Befehl `saas:resync` gilt auch für [!DNL Adobe Commerce Optimizer Connector]-Feeds wie `products`, `categories` und `priceBooks`. Unter [Unterstützte Feeds](../aco-connector/reference/connector-reference.md#supported-feeds) finden Sie eine vollständige Liste der Connector-Feeds und Indexernamen.

Es wird von Adobe nicht empfohlen, den Befehl `saas:resync` regelmäßig zu verwenden. Typische Szenarien für die Verwendung des Befehls sind:

- Erstsynchronisierung
- Synchronisieren von Daten mit einem neuen Datenraum nach Änderung der [SaaS-Datenraum-ID](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas)
- Fehlerbehebung

Überwachen von Synchronisierungsvorgängen in der `var/log/saas-export.log`.

## Erstsynchronisierung

>[!NOTE]
>
>Die Erstsynchronisierung wird automatisch ausgeführt, wenn die Live Search oder die Produktempfehlungen aktiviert sind. Manuelle Befehle werden nicht benötigt.
>
>Bei [!DNL Adobe Commerce Optimizer Connector] Bereitstellungen plant der Befehl `aco:config:init` die anfängliche vollständige Synchronisierung, indem alle Connector-Feed-Indexer ungültig gemacht werden. Siehe [Aktivieren der  [!DNL Commerce Optimizer] -Integration](../aco-connector/get-started.md#enable-the-adobe-commerce-optimizer-integration) und [Verwalten der Synchronisierung mit [!DNL Commerce Optimizer]](../aco-connector/data-sync-manage.md).

Beim Trigger eines `saas:resync` über die Befehlszeile kann es je nach Kataloggröße einige Minuten bis einige Stunden dauern, bis die Daten aktualisiert werden.

Die Feed-Synchronisierung kann in beliebiger Reihenfolge ausgeführt werden. Es gibt keine festen Abhängigkeiten zwischen ihnen. Die folgende Sequenz beginnt mit den Bereichsdaten , was ein logischer Ausgangspunkt ist, da Bereiche die Speicheransichten definieren, auf die andere Feeds verweisen.

```shell
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed productAttributes
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed products
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed productoverrides
```

>[!NOTE]
>
>Ihre Umgebung enthält möglicherweise nicht alle Feeds in dieser Sequenz. Unter [Unterstützte Feeds](reference/feed-table-reference.md#supported-feeds) finden Sie die vollständige Feed-Liste, CLI-Feed-Namen und Modulanforderungen.

## Befehlsoptionen

Der `saas:resync`-Befehl unterstützt verschiedene Synchronisierungsvorgänge:

- Teilweise Synchronisierung nach SKU
- Unterbrochene Synchronisationen fortsetzen
- Daten ohne Synchronisierung validieren

Alle Befehlsoptionen und Flags anzeigen:

```shell
bin/magento saas:resync --help
```

In den folgenden Abschnitten finden Sie Optionsbeschreibungen mit Beispielen.

>[!NOTE]
>
>Erweiterte Optionen zur Verwaltung der Exportverarbeitung finden Sie unter [Exportverarbeitung anpassen](customize-export-processing.md).

## `--feed`

Erforderlich. Gibt die Feed-Entität an, die neu synchronisiert werden soll.

`bin/magento saas:resync --help` von Dokumenten - Befehlsoptionen und Flags. Es werden nicht alle in Ihrer Umgebung verfügbaren Feeds aufgelistet. Die vollständige Feed-Liste mit CLI-Feed-Namen, Indexer-IDs und Feed-Tabellen finden Sie unter [Unterstützte Feeds](reference/feed-table-reference.md#supported-feeds).

>[!NOTE]
>
>Installierte Module bestimmen, welche Feeds neu synchronisiert werden können. `productOverrides` erfordert beispielsweise [!DNL Adobe Commerce] in der Cloud, On-Premise oder Commerce as a Cloud Service und `orders` das Modul „Kundenaufträge“.

>[!NOTE]
>
>Der Befehl `saas:resync` übermittelt nur neue Elemente, aktualisierte Elemente und Elemente, die zuvor nicht exportiert werden konnten. Elemente, deren Inhaltshash seit dem letzten Export nicht geändert wurde, werden übersprungen.

**Beispiel:**

```shell
bin/magento saas:resync --feed products
```

## `--by-ids`

Bestimmte Entitäten anhand ihrer IDs teilweise neu synchronisieren. Unterstützt `products`-, `productAttributes`-, `productOverrides`-, `inventoryStockStatus`-, `prices`-, `variants`- und `categoryPermissions`.

Wenn Sie die Option &quot;`--by-ids`&quot; verwenden, geben Sie Werte standardmäßig mithilfe von Produkt-SKU-Werten an. Um stattdessen Produkt-IDs zu verwenden, fügen Sie die Option `--id-type=productId` hinzu.

>[!NOTE]
>
>Im Gegensatz zu einer standardmäßigen Neusynchronisierung umgeht `--by-ids` die Hash-Überprüfung und erzwingt, dass die angegebenen Entitäten an verbundene Commerce-Services gesendet werden, unabhängig davon, ob sich ihr Inhalt seit dem letzten Export geändert hat.

**Beispiele:**

```shell
bin/magento saas:resync --feed products --by-ids='ADB102,ADB111,ADB112'

bin/magento saas:resync --feed products --by-ids='1,2,3' --id-type='productId'
```

## `--cleanup-feed`

Bereinigen Sie die Feed-Indexertabelle, bevor Sie Daten neu indizieren und an SaaS senden. Wird nur für `products`, `productAttributes`, `productOverrides`, `inventoryStockStatus`, `prices`, `variants` und `categoryPermissions` unterstützt.

Bei Verwendung mit der Option `--dry-run` führt der Vorgang einen Probelauf-Resynchronisierungsvorgang für alle Elemente durch.

>[!WARNING]
>
>Wenn Sie den Befehl resynchronisieren mit der Option `cleanup-feed` verwenden, wird der Status des lokalen Feed-Exports gelöscht und die Synchronisierung kann unvollständig sein. Zum Beispiel werden Entitätslöschungen in [!DNL Adobe Commerce] möglicherweise nicht in den verbundenen Commerce Services angezeigt oder veraltete Entitäten verbleiben möglicherweise in den Remote-Commerce Services-Indizes, auch wenn sie in [!DNL Adobe Commerce] gelöscht oder aktualisiert wurden. Verwenden Sie diese Option nur für vollständige Neuaufbauten der Umgebung, z. B. nach einer SaaS-Datenspeicherbereinigung.

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

**Beispiel:**

```shell
bin/magento saas:resync --feed products --dry-run --cleanup-feed
```

## `--no-reindex`

Sendet vorhandene Katalogdaten ohne Neuindizierung erneut an [!DNL Commerce Services]. Wird für produktbezogene Feeds nicht unterstützt.

Das Verhalten variiert je [Exportmodus](sync-overview.md#synchronization-modes):

- Legacy-Modus: Setzt alle Daten erneut ab, ohne sie zu kürzen.
- Sofortiger Modus: Option wird ignoriert, nur Aktualisierungen/Fehler werden synchronisiert.

**Beispiel:**

```shell
bin/magento saas:resync --feed productAttributes --no-reindex
```

>[!MORELIKETHIS]
>
> - [Überprüfen von Protokollen und Fehlerbehebung](troubleshooting/logging.md) - Diagnostizieren von Datenexport- und SaaS-Exportfehlern.
> - [Fehlerbehebungsszenarien](troubleshooting/troubleshooting-scenarios.md) — Beheben Sie Konfigurationsfehler und unerwartete Synchronisierungsergebnisse.
> - [Funktionsweise der Synchronisierung](sync-overview.md) — Erfahren Sie mehr über Synchronisierungsmodi und das Verhalten bei erneuten Zustellversuchen.
