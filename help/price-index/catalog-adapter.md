---
title: Catalog Adapter-Erweiterung
description: Verwenden des Katalogadapters zum Rendern von Preisen aus Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Katalogadapter

Die `[!DNL Catalog Adapter]`-Erweiterung deaktiviert den standardmäßigen Produktpreisindex, der in der Commerce-Anwendung enthalten ist, und verwendet stattdessen Preise, die vom [Katalog-Service](../catalog-service/overview.md) bereitgestellt werden.

Der Adapter ist für die Verwendung mit dem [SaaS-Datenexport](../data-export/overview.md) und dem Adobe Commerce-Service konzipiert. Der SaaS-Datenexport ist für die Übermittlung der Preise verantwortlich, und der [!DNL Catalog Adapter] ruft alle Preise vom Adobe Commerce-Service ab.

Wenn Sie die [!DNL Catalog Adapter] aktivieren, werden Preisindizierung und -vorgänge wie folgt beeinflusst:

- Der im Adobe Commerce-Programm enthaltene Preisindizer ist deaktiviert.
- Die Preisverwaltung erfolgt über den SaaS-Datenexport und den [SaaS-Preisindex](price-indexing.md).
- Wenn ein Kunde ein Produkt, eine Kategorie oder eine andere Seite öffnet, die Produktpreise anzeigt, werden die Preise über den Adobe Commerce-Service abgerufen.
- Die Preise werden an den Adobe Commerce-Service gesendet, indem Daten aus dem [SaaS-Datenexport“ ](../data-export/overview.md) werden.
- Checkout berechnet Preise dynamisch neu.

Sie können die Preisindizierung in der Commerce-Anwendung erneut aktivieren, indem Sie die Katalogadaptererweiterung entfernen oder deaktivieren.

## Anforderungen

- Adobe Commerce 2.4.4+
- Installieren Sie einen der folgenden Commerce-Services:

   - [Live Search](../live-search/install.md)
   - [Produkt Recommendations](../product-recommendations/install-configure.md)
   - [Katalog-Service](../catalog-service/installation.md)

## Installation

Die Catalog Adapter-Erweiterung ist ein Composer-Metapaket, das die folgenden Module installiert:

- **Price Indexer Disabler** Dieses Modul deaktiviert den Preisindex in der Commerce-Anwendung, sodass Preise über SaaS-Preisindizierung bereitgestellt werden. Der Produktpreisindizierer in der Commerce-Anwendung kann nicht aktiviert werden, wenn die SaaS-Preisindizierungserweiterung installiert ist.
- **Prices Provider**-Dieses Modul liefert Preise für Produkte aus dem Adobe Commerce Service. Es bildet die Suchanfrage und erhält die Preise für die Produkte im Frontend.
- **Catalog Service Search Adapter**: Dieses Modul überträgt Preise von der Adobe Commerce-Anwendung an einen Adobe Commerce-Service als Reaktion auf eine Produktsuchanfrage.

## Installationsschritte

>[!BEGINTABS]

>[!TAB Cloud-Infrastruktur]

Verwenden Sie diese Methode, um die [!DNL Catalog Adapter] für eine Commerce Cloud-Instanz zu installieren.

1. Wechseln Sie auf Ihrer lokalen Workstation in das Projektverzeichnis für Ihr Adobe Commerce on Cloud-Infrastrukturprojekt.

   >[!NOTE]
   >
   >Informationen zur lokalen Verwaltung von Commerce-Projektumgebungen finden Sie unter [Verwalten von Verzweigungen mit der CLI](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/cli-branches) im _Benutzerhandbuch für Adobe Commerce auf Cloud-Infrastruktur_.

1. Checken Sie die Umgebungsverzweigung aus, um sie mithilfe der Adobe Commerce Cloud-CLI zu aktualisieren.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Fügen Sie das Modul Katalogadapter hinzu.

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Paketabhängigkeiten aktualisieren.

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. Code-Änderungen für `composer.json` und `composer.lock` übertragen und übertragen.

1. Fügen Sie die Code-Änderungen für die `composer.json`- und `composer.lock`-Dateien hinzu, übertragen Sie sie und übertragen Sie sie in die Cloud-Umgebung.

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   Durch Pushen der Aktualisierungen in die Cloud-Umgebung wird der [Commerce-Cloud-Bereitstellungsprozess](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/process) gestartet, um die Änderungen anzuwenden. Überprüfen Sie den Bereitstellungsstatus im [Bereitstellungsprotokoll](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB On-Premises]

Verwenden Sie diese Methode, um die [!DNL Catalog Adapter] für eine lokale Instanz zu installieren.

1. Fügen Sie den Katalogadapter mithilfe von Composer zu Ihrem Projekt hinzu:

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. Adobe Commerce aktualisieren:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >In einigen Fällen, insbesondere bei der Bereitstellung in der Produktion, empfiehlt es sich möglicherweise, kompilierten Code nicht zu löschen, da dies einige Zeit in Anspruch nehmen kann. Stellen Sie sicher, dass Sie Ihr System sichern, bevor Sie Änderungen vornehmen.

>[!ENDTABS]


## Erneutes Aktivieren des Adobe Commerce-Produktpreisindexers

Wenn Sie Anwendungen von Drittanbietern haben, die auf dem standardmäßigen Adobe Commerce-Produktpreisindizierer basieren, können Sie ihn mit den folgenden Befehlen erneut aktivieren:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## Deaktivieren des Produktpreisindexers für das Headless-Storefront-Szenario

Wenn Sie über eine Commerce-Headless-Instanz verfügen, müssen Sie möglicherweise den Adobe Commerce-Produktpreisindexer deaktivieren, um die Last auf Ihrer Adobe Commerce-Instanz zu reduzieren. Sie können diese Aufgabe abschließen, indem Sie das `magento/module-price-indexer-disabler` Modul installieren:

```bash
composer require magento/module-price-indexer-disabler
```

## Nutzungsszenarien

Im Folgenden finden Sie einige gängige `[!DNL Catalog Adapter]`.

### Keine Abhängigkeiten vom Adobe Commerce-Produktpreisindizierer

- Sie sind ein Händler von Luma oder Adobe Commerce Core GraphQL, der einen erforderlichen Service installiert hat (Live Search, Produktempfehlungen, Katalog-Service)
- Keine Integrationen mit Erweiterungen von Drittanbietern, die auf dem Adobe Commerce-Produktpreisindexer basieren

1. Installieren Sie die [!DNL Catalog Adapter].

### Mit Abhängigkeiten vom Adobe Commerce-Produktpreisindizierer

- Sie sind ein Händler von Luma oder Adobe Commerce Core GraphQL, der einen unterstützten Service installiert hat (Live Search, Produktempfehlungen, Katalog-Service)
- Sie verwenden eine Drittanbietererweiterung, die auf dem Adobe Commerce-Produktpreisindexer basiert

1. Installieren Sie die [!DNL Catalog Adapter].
1. Aktivieren Sie erneut den standardmäßigen Adobe Commerce-Produktpreisindizierer.

### Headless Commerce-Instanzen

- Ein Händler mit einer Headless-Commerce-Instanz, auf der die erforderlichen Services installiert sind (Live Search, Produktempfehlungen, Katalog-Service)
- Keine Abhängigkeit vom standardmäßigen Adobe Commerce-Produktpreisindizierer

1. Installieren Sie das `magento/module-price-indexer-disabler` aus dem [!DNL Catalog Adapter].

