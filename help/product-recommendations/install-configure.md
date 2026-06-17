---
title: Installieren und Konfigurieren
description: Erfahren Sie, wie Sie installieren, aktualisieren und deinstallieren [!DNL Product Recommendations].
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
exl-id: 2e7f6454-d4cb-44bc-982f-354a179e8e59
TQID: https://experienceleague.adobe.com/z-ue-sojw9Iewuz-ZToCzkumP3qN-TCWWF3UWdpdIL0
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 641
ht-degree: 0%

---

# Installieren und Konfigurieren

Für die Bereitstellung von [!DNL Product Recommendations] in Ihrer Storefront und in Ihrem Administrator müssen Sie das Modul installieren und den [Commerce Services-Connector konfigurieren](../landing/saas.md). Sobald Updates veröffentlicht werden, können Sie die Installation einfach mit der neuesten Version aktualisieren.

- [Installieren von](#install)
- [Konfigurieren](#configure)
- [Aktualisieren](#update)
- [Deinstallieren](#uninstall)

## Installieren von [!DNL Product Recommendations] {#install}

Da das [!DNL Product Recommendations]-Modul ein eigenständiges Metapaket ist, werden Aktualisierungen häufiger veröffentlicht als Adobe Commerce. Um sicherzustellen, dass Sie über die neuesten Fehlerbehebungen und Funktionen verfügen, lesen Sie die [Versionshinweise](release-notes.md).

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie über die richtigen [Berechtigungen](../landing/saas.md#credentials) zur Verwendung von Produktempfehlungen verfügen.

Installieren Sie das Modul `magento/product-recommendations` mit Composer:

```bash
composer require magento/product-recommendations
```

### Hinzufügen der Page Builder-Unterstützung {#pbsupport}

[!DNL Product Recommendations] für Page Builder ist ein optionales Modul und wird separat installiert. Um [!DNL Product Recommendations] mit Page Builder zu verwenden, installieren Sie das -Modul, indem Sie den folgenden Befehl ausführen:

```bash
composer require magento/module-page-builder-product-recommendations
```

Durch die Aktivierung von [!DNL Product Recommendations] in Page Builder können Sie eine vorhandene, aktive [Empfehlungseinheit](https://experienceleague.adobe.com/de/docs/commerce-admin/page-builder/add-content/recommendations) zu allen in Page Builder erstellten Inhalten hinzufügen, z. B. Seiten, Blöcke und dynamische Blöcke.

Weitere [&#x200B; finden  [!DNL Product Recommendations]  unter „Verwenden &#x200B;](page-builder.md) Page Builder-Inhalten“.

### Hinzufügen des Empfehlungstyps für visuelle Ähnlichkeit {#vissimsupport}

Mit _Empfehlungstyp &quot;_ Ähnlichkeit“ können Sie eine Empfehlungseinheit auf Ihrer Produktdetailseite bereitstellen, die Produkte anzeigt, die dem angezeigten Produkt [visuell ähnlich](type.md#visualsim) sind. Dieser Empfehlungstyp ist am nützlichsten, wenn Bilder und visuelle Aspekte der Produkte wichtige Teile des Einkaufserlebnisses sind. Installieren Sie _Empfehlungstyp &quot;_ Ähnlichkeit“, indem Sie den folgenden Befehl ausführen:

```bash
composer require magento/module-visual-product-recommendations
```

## Konfigurieren von [!DNL Product Recommendations] {#configure}

1. Konfigurieren Sie nach der Installation des `magento/product-recommendations` den [Commerce Services-Connector](../landing/saas.md) indem Sie API-Schlüssel angeben und einen SaaS-Datenspeicher auswählen.

   Durch die Konfiguration dieser Verbindung wird die Datensynchronisation und Kommunikation zwischen der Commerce-Instanz, dem Katalog-Service und anderen unterstützenden Services aktiviert. Die Datensynchronisation wird von der [SaaS-Datenexporterweiterung“ &#x200B;](../data-export/overview.md).

1. Um sicherzustellen, dass der Katalogexport ordnungsgemäß ausgeführt werden kann, überprüfen Sie, ob [cron](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)-Vorgänge und [indexers](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/manage-indexers) ausgeführt werden und der `Product Feed`-Indexer auf `Update by Schedule` festgelegt ist.

Nachdem Sie die Commerce-Anwendung erfolgreich mit Commerce Services verknüpft und den [SaaS-Datenspeicher](../landing/saas.md#saas-configuration) angegeben haben, beginnt die Katalogsynchronisierung. Sie können [&#x200B; überprüfen](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/verify/) ob Verhaltensdaten an Ihre Storefront gesendet werden.

## Überwachen und Fehlerbehebung bei der Datensynchronisation

Vom Commerce-Administrator aus können Sie den Synchronisierungsprozess mithilfe des [Daten-Management-Dashboards“ &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard). Verwenden Sie die [Commerce-CLI](../data-export/data-export-cli-commands.md) und [Protokolle](../data-export/troubleshooting/logging.md), um den Prozess zu verwalten und Fehler zu beheben.

Sie können [&#x200B; überprüfen](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/verify/) ob Verhaltensdaten an Ihre Storefront gesendet werden.

## Aktualisieren der [!DNL Product Recommendations] {#update}

Wie alle Adobe Commerce-Versionen nutzt [!DNL Product Recommendations] Composer für die Installation und Aktualisierung. Führen Sie die folgenden Schritte aus, um das `magento/product-recommendations`-Modul zu aktualisieren:

```bash
composer update magento/product-recommendations --with-dependencies
```

Um auf eine Hauptversion zu aktualisieren, z. B. von 5.0 auf 6.0, müssen Sie die `composer.json` für Ihr Projekt bearbeiten. (Informationen zur [&#x200B; Version finden &#x200B;](release-notes.md) in den Versionshinweisen.) Beispiel: Öffnen Sie die `composer.json` und suchen Sie nach dem `magento/product-recommendations`:

```json
"require": {
    ...
    "magento/product-recommendations": "^5.0",
    ...
}
```

Lassen Sie uns die Hauptversion von `5.0` auf `6.0` anheben:

```json
"require": {
    ...
    "magento/product-recommendations": "^6.0",
    ...
}
```

Speichern Sie die `composer.json` und führen Sie Folgendes aus:

```bash
composer update magento/product-recommendations --with-dependencies
```

Oder wenn Sie die `magento/module-visual-product-recommendations` und `magento/module-page-builder-product-recommendations` Module installiert haben:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> In Version 3.x.x von Product Recommendations benötigen Sie nur einen einzigen API-Schlüssel. In Version 4.x.x und höher müssen Sie öffentliche und private API-Schlüssel für die Sandbox- und die Produktionsumgebung bereitstellen. Wenn Sie nicht beide Paare von API-Schlüsseln angeben, können Sie im Admin-Bereich nicht auf die Funktion „Produktempfehlungen“ zugreifen. Die Datenerfassung wird jedoch in Ihrer Storefront fortgesetzt und Ihren Kundinnen und Kunden werden weiterhin vorhandene Empfehlungen angezeigt.

## Firewalls

Um Produktempfehlungen durch eine Firewall zu lassen, fügen Sie `commerce.adobe.io` zur Zulassungsliste hinzu.

## [!DNL Product Recommendations] deinstallieren {#uninstall}

Bei Bedarf können Sie [&#x200B; Modul &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/uninstall-modules)product-recommendations“ (deinstallieren).
