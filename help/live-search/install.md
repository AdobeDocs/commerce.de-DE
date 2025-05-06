---
title: Erste Schritte mit [!DNL Live Search]
description: Erfahren Sie mehr über die Systemanforderungen und Installationsschritte für  [!DNL Live Search]  von Adobe Commerce.
role: Admin, Developer
exl-id: 45b985f1-9afb-4a07-93e8-f2fe231c5400
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: be1c739f3821a5f1e846b3026088e3a3ff45a60f
workflow-type: tm+mt
source-wordcount: '3139'
ht-degree: 0%

---

# Einrichten für eine erfolgreiche [!DNL Live Search]

Adobe Commerce [!DNL Live Search] und [[!DNL Catalog Service]](../catalog-service/guide-overview.md) arbeiten zusammen, um eine leistungsstarke, relevante und intuitive Suchlösung bereitzustellen, mit der Ihre Kunden schnell genau das finden können, was sie benötigen. Insbesondere zeigt [!DNL Catalog Service] Ihre Katalogdaten für SaaS-Services an, z. B. [!DNL Live Search].

Dieser Artikel enthält schrittweise Anweisungen zur Implementierung von [!DNL Live Search] mit [!DNL Catalog Service].

>[!IMPORTANT]
>
>Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Lesen Sie &quot;[ und Einschränkungen](boundaries-limits.md) vor der Implementierung, um sicherzustellen, dass [!DNL Live Search] zu Ihren Geschäftsanforderungen passt.

## Zielgruppe

Dieser Artikel richtet sich an Entwicklerinnen und Entwickler oder Systemintegratoren in Ihrem Team, die für die Installation und Konfiguration Ihrer Adobe Commerce-Instanz verantwortlich sind.

## Anforderungen

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP-Version 8.1, 8.2 oder 8.3
- [!DNL Composer]

## Unterstützte Plattformen

- Adobe Commerce on Cloud (ECE) : 2.4.4+
- Adobe Commerce On-Premise (EE) : 2.4.4+

## Workflow-Übersicht

Im Allgemeinen erfordert Onboarding-[!DNL Live Search] Folgendes:

1. [Installieren](#1-install-the-live-search-extension) der [!DNL Live Search]
1. [Konfigurieren](#2-configure-api-keys) der API-Schlüssel
1. [Synchronisieren](#3-sync-your-catalog-data) der Katalogdaten
1. [Überprüfen](#4-verify-that-the-data-was-exported) ob die Katalogdaten exportiert wurden
1. [Konfigurieren](#5-configure-the-data) der Daten
1. [Testen](#6-test-the-connection) der Verbindung
1. [Überprüfen](#7-validate-events-are-capturing-data) ob Ereignisse Daten erfassen
1. [Anpassen](#8-customize-for-your-storefront) Ihrer Storefront

## 1. Installieren der [!DNL Live Search]

[!DNL Live Search] wird als Erweiterung vom [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) bis zum [Composer](https://getcomposer.org/) installiert. Nach der Installation und Konfiguration von [!DNL Live Search] beginnt Adobe [!DNL Commerce] mit der Freigabe von Such- und Katalogdaten für SaaS-Services. Jetzt können *Admin*-Benutzer Suchfacetten, Synonyme und Merchandising-Regeln einrichten, anpassen und verwalten.

>[!NOTE]
>
>Ab [!DNL Live Search] 3.0.2 ist die [!DNL Catalog Service]-Erweiterung im Lieferumfang der [!DNL Live Search]-Installation enthalten.

>[!IMPORTANT]
>
>Ab [!DNL Live Search] 4.0.0 wird der Suchadapter nicht mehr unterstützt. Ab nun wird der Suchadapter nur noch aktualisiert, um Sicherheitsprobleme zu beheben.

1. Vergewissern Sie sich[ dass ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)Cron-Aufträge[ und -](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) ausgeführt werden.

   >[!IMPORTANT]
   >
   >Aufgrund der Ankündigung zum Ende der Unterstützung für Elasticsearch 7 im August 2023 wird empfohlen, dass alle Adobe Commerce-Kunden zur OpenSearch 2.x -Suchmaschine migrieren. Informationen zur Migration Ihrer Suchmaschine während eines Produkt-Upgrades finden Sie unter [Migration zu OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) im _Upgrade-Handbuch_.

1. Laden Sie das `live-search` Paket vom [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) herunter.

1. Führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/live-search
   ```

   Wenn Sie die [!DNL Live Search] Erweiterung zu einer &quot;**&quot;-Installation** Adobe Commerce hinzufügen, führen Sie den folgenden Befehl aus, um [!DNL OpenSearch] und zugehörige Module vorübergehend zu deaktivieren und [!DNL Live Search] zu installieren. Fahren Sie dann mit Schritt 4 fort.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   Wenn Sie die [!DNL Live Search]-Erweiterung zu einer **Adobe Commerce-** hinzufügen, führen Sie die folgenden Schritte aus, um die [!DNL Live Search] zu deaktivieren, die Storefront-Suchergebnisse bereitstellen. Fahren Sie dann mit Schritt 4 fort:

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] verwaltet weiterhin Suchanfragen aus der Storefront, während der [!DNL Live Search]-Service Katalogdaten synchronisiert und Produkte im Hintergrund indiziert.

1. Führen Sie Folgendes aus:

   ```bash
   bin/magento setup:upgrade
   ```

1. Stellen Sie sicher[ dass die folgenden ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) auf „Nach Zeitplan aktualisieren“ eingestellt sind:

   - Produkt-Feed
   - Produktvarianten-Feed
   - Feed für Katalogattribute
   - Produktpreise Futtermittel
   - Umfang des Website-Daten-Feeds
   - Umfänge des Kundengruppen-Daten-Feeds
   - Feed-Kategorien
   - Feed für Kategorieberechtigungen

1. Wenn Sie [!DNL Live Search] auf einer neuen Commerce-Instanz installieren, sind Sie fertig und können zur [2 wechseln. Konfigurieren von API-](#2-configure-api-keys): Abschnitt. Wenn Sie die Live Search auf einer bestehenden Commerce-Instanz installieren, fahren Sie mit dem nächsten Schritt fort.

1. Führen Sie die folgenden Befehle aus, um die [!DNL Live Search]-Erweiterung zu aktivieren, [!DNL OpenSearch] zu deaktivieren und `setup` auszuführen.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

### Installieren der [!DNL Live Search] Beta-Version

>[!IMPORTANT]
>
>Die folgende Funktion befindet sich in der Betaphase. Um an der Beta teilzunehmen, senden Sie eine E-Mail-Anfrage an [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Diese Beta-Version unterstützt drei neue Funktionen in der [`productSearch` Abfrage](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Mehrschichtige Suche** - Suche in einem anderen Suchkontext - Mit dieser Funktion können Sie bis zu zwei Suchebenen für Ihre Suchanfragen durchführen. Beispiel:

   - **Layer 1-Suche** - Suche nach „motor“ in „product_attribute_1“.
   - **Layer 2-Suche** - Suchen Sie nach „Teilenummer 123“ in „product_attribute_2“. In diesem Beispiel wird in den Ergebnissen nach „Motor“ nach „Teilenummer 123“ gesucht.

  Die mehrschichtige Suche ist sowohl für die `startsWith` als auch für die `contains` Suchindizierung verfügbar, wie unten beschrieben:

- **startsWith search indexation** - Suche mit `startsWith`. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach Produkten, bei denen der Attributwert mit einer bestimmten Zeichenfolge beginnt.
   - Konfigurieren der Suche „endet mit“, damit Käufer nach Produkten suchen können, bei denen der Attributwert mit einer bestimmten Zeichenfolge endet. Um eine Suche „endet mit“ zu aktivieren, muss das Produktattribut in umgekehrter Reihenfolge aufgenommen werden und der API-Aufruf sollte auch eine umgekehrte Zeichenfolge sein.

- **enthält Suchindizierung** - Das Suchattribut enthält die Indizierung. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach einer Abfrage innerhalb einer größeren Zeichenfolge. Beispiel: Ein Käufer sucht in der Zeichenfolge „HAPE-123“ nach der Produktnummer „PE-123“.

      - Hinweis: Dieser Suchtyp unterscheidet sich von dem vorhandenen Suchbegriff[ der eine ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) Suche durchführt. Wenn Ihr Produktattributwert beispielsweise „Outdoor Pants“ ist, gibt eine Suchphrase eine Antwort für „out pan“ zurück, aber keine Antwort für „or ants“. Eine Suche enthält jedoch eine Antwort für „oder Ameisen“.

Diese neuen Bedingungen verbessern den Filtermechanismus für Suchanfragen, um Suchergebnisse zu verfeinern. Diese neuen Bedingungen wirken sich nicht auf die Hauptsuchabfrage aus.

Sie können diese neuen Bedingungen auf Ihrer Suchergebnisseite implementieren. Sie können beispielsweise einen neuen Abschnitt auf der Seite hinzufügen, in dem der Erstkäufer seine Suchergebnisse weiter verfeinern kann. Sie können Käufern die Auswahl bestimmter Produktattribute ermöglichen, z. B. „Hersteller“, „Teilenummer“ und „Beschreibung“. Von dort aus suchen sie mithilfe der `contains` oder `startsWith` Bedingungen innerhalb dieser Attribute. Eine Liste mit durchsuchbaren (Attributen) finden [ im Administratorhandbuch ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types).

1. Um die Beta-Version zu installieren, fügen Sie die folgende Abhängigkeit zu Ihrem Projekt hinzu:

   ```bash
   composer require magento/module-live-search-search-types:"^1.0.0-beta1"
   ```

1. Übertragen Sie die Änderungen und übertragen Sie sie auf Ihre `composer.json` und `composer.lock` Dateien in Ihr Cloud-Projekt. [Weitere Informationen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension).

   Diese Beta-Version fügt **[!UICONTROL Search types]** Kontrollkästchen für **[!UICONTROL Autocomplete]**, **[!UICONTROL Contains]** und **[!UICONTROL Starts with]** in der Admin-Liste hinzu. Außerdem wird die [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-using-search-capability) GraphQL-API aktualisiert, um diese neuen Suchfunktionen aufzunehmen.

1. Legen Sie in „Admin[ ein Produktattribut ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes-add#step-5-describe-the-storefront-properties), damit es durchsucht werden kann, und geben Sie die Suchfunktion für dieses Attribut an, z. B **„Enthält** (Standard) oder **Beginnt mit**. Sie können maximal sechs Attribute angeben, die für &quot;**&quot; aktiviert** sollen, und sechs Attribute, die für „Beginnt **&quot;** werden sollen. Beachten Sie für die Beta-Version, dass der Administrator diese Einschränkung nicht erzwingt, sie jedoch bei API-Suchen erzwingt.

   ![Suchfunktion angeben](./assets/search-filters-admin.png)

1. In der [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-using-search-capability) erfahren Sie, wie Sie Ihre [!DNL Live Search]-API-Aufrufe mithilfe der neuen `contains` und `startsWith` Suchfunktionen aktualisieren können.

### Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| `Autocomplete` | Standardmäßig aktiviert und kann nicht geändert werden. Mit `Autocomplete` können Sie `contains` im [Suchfilter](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering) verwenden. Hier gibt die Suchabfrage in `contains` eine Suchantwort mit automatischer Vervollständigung zurück. Adobe empfiehlt, diesen Typ der Suche nach Beschreibungsfeldern zu verwenden, die in der Regel mehr als 50 Zeichen enthalten. |
| `Contains` | Aktiviert die Suche nach „in einer Zeichenfolge enthaltenem“ Text anstelle einer Suche mit automatischer Vervollständigung. Verwenden Sie `contains` im [Suchfilter](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-using-search-capability). Weitere Informationen finden [ unter ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#limitations) . |
| `Starts with` | Ermöglicht die Abfrage von Zeichenfolgen, die mit einem bestimmten Wert beginnen. Verwenden Sie `startsWith` im [Suchfilter](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-using-search-capability). |

## 2. API-Schlüssel konfigurieren

Der Adobe Commerce-API-Schlüssel und der zugehörige private Schlüssel sind erforderlich, um [!DNL Live Search] mit einer Adobe Commerce-Installation zu verbinden. Der API-Schlüssel wird im Konto des [!DNL Commerce]-Lizenzinhabers generiert und gepflegt, der ihn mit dem Entwickler oder Systemintegrator teilen kann. Der Entwickler kann dann die SaaS-Datenräume im Auftrag des Lizenzinhabers erstellen und verwalten. Wenn Sie bereits über einen Satz API-Schlüssel verfügen, müssen Sie diese nicht neu generieren.

Erfahren Sie im Artikel [ Commerce Services Connector&rbrace;, wie Sie Ihre API](../landing/saas.md)Schlüssel konfigurieren.

## 3. Synchronisieren der Katalogdaten

[!DNL Live Search] verschiebt Katalogdaten in die SaaS-Infrastruktur von Adobe. Die Daten werden indiziert und die Suchergebnisse von diesem Index werden direkt an die Storefront übermittelt. Je nach Größe und Komplexität kann die Indizierung zwischen 30 Minuten und einigen Stunden dauern.

Führen Sie die folgenden Befehle in dieser Reihenfolge aus, um die erste Synchronisierung Ihrer Katalogdaten mit SaaS-Services zu starten:

```bash
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

Wenn Sie diese Befehle ausführen, beginnt die erste Synchronisierung Ihrer Katalogdaten mit SaaS-Services.

>[!WARNING]
>
> Während die Daten indiziert und synchronisiert sind, sind die Such- und Kategoriebesuchvorgänge in der Storefront nicht verfügbar. Je nach Größe Ihres Katalogs kann der Prozess mindestens eine Stunde dauern, bevor `cron` ausgeführt wird, um Ihre Daten mit SaaS-Services zu synchronisieren.

### Fortschritt der Synchronisierung überwachen

Sie können die synchronisierten und freigegebenen Daten über das [Daten-Management-Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) anzeigen. Dieses Dashboard bietet wertvolle Einblicke in die Verfügbarkeit von Produktdaten für Ihre Storefront, sodass sie Ihren Kundinnen und Kunden sofort angezeigt werden können.

![Daten-Management-Dashboard](assets/data-management-dashboard.png)

Sie können auch Synchronisierungsbefehle ausführen und mithilfe der [Commerce-CLI](../data-export/data-export-cli-commands.md#troubleshooting) und der Protokolle der Datenexporterweiterung eine Fehlerbehebung beim Synchronisierungsprozess durchführen.

#### Künftige Produktaktualisierungen

Nach der ersten Synchronisierung kann es bis zu 15 Minuten dauern, bis inkrementelle Produktaktualisierungen für die Storefront-Suche verfügbar werden. Weitere Informationen finden Sie unter [Streaming von Produktaktualisierungen](indexing.md) in der Dokumentation zur Indizierung.

## 4. Überprüfen, ob die Daten exportiert wurden

Um zu überprüfen, ob Ihre Katalogdaten aus Adobe Commerce exportiert und mit [!DNL Live Search] synchronisiert wurden, haben Sie einige Optionen:

- Suchen Sie nach Einträgen in den folgenden Tabellen:

   - `cde_products_feed`
   - `cde_product_attributes_feed`

  >[!NOTE]
  >
  >Wenn Sie einen `table does not exist` Fehler erhalten, suchen Sie in den `catalog_data_exporter_products` und `catalog_data_exporter_product_attributes` Tabellen nach Einträgen. Diese Tabellennamen werden in [!DNL Live Search] Versionen vor 4.2.1 verwendet.

- Verwenden Sie den [GraphQL Playground](https://experienceleague.adobe.com/en/docs/commerce/live-search/live-search-admin/graphql) mit der Standardabfrage (weitere Informationen finden Sie [&#128279;](https://developer.adobe.com/commerce/services/graphql/live-search/) GraphQL-Referenz), um Folgendes zu überprüfen:

   - Die zurückgegebene Anzahl von Produkten entspricht fast den Erwartungen für die Store-Ansicht.
   - Facetten werden zurückgegeben.

Weitere Hilfe finden Sie unter [[!DNL Live Search] Katalog nicht synchronisiert](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) in der Support-Wissensdatenbank.

## 5. Konfigurieren der Daten

Die korrekte Konfiguration Ihrer Produktdaten sorgt für gute Suchergebnisse für Ihre Kunden. In diesem Abschnitt aktivieren Sie die Widgets für die Produktliste und weisen Kategorien zu.

### Aktivieren von Produktlisten-Widgets

Bei der Installation von [!DNL Live Search] 4.0.0+ sind Widgets für die Produktliste standardmäßig aktiviert. Wenn Widgets aktiviert sind, wird eine andere UI-Komponente für die Suchergebnisseite und die Produktlistenseite zum Durchsuchen von Kategorien verwendet. Diese UI-Komponente führt direkte Aufrufe an die [Catalog Service-API](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) durch, was zu schnelleren Antwortzeiten führt.

Wenn Sie eine [!DNL Live Search] Version älter als 4.0.0 haben, müssen Sie das Produktlisten-Widget manuell aktivieren.

1. Navigieren Sie *Admin* zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Wählen Sie unter **[!UICONTROL Live Search]** die Option **[!UICONTROL Storefront Features]**.
1. Legen Sie **[!UICONTROL Enable Product Listing Widgets]** auf `Yes` fest.

   ![Aktivieren von Produktlisten-Widgets](assets/ls-admin-enable-widget.png)

Wenn Sie diese Konfiguration ändern, wird die Meldung `Page cache is invalidated` angezeigt. Sie müssen den Magento-Cache leeren, um Ihre Änderungen zu speichern.

1. Greifen Sie auf [ Seite ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management)Cache-Verwaltung“ zu, indem Sie eine der folgenden Aktionen ausführen:

   - Klicken Sie auf den Link **[!UICONTROL Cache Management]** in der Nachricht über dem Arbeitsbereich.
   - Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Wählen Sie die [!UICONTROL Cache Type] **Konfiguration** aus und klicken Sie auf **[!UICONTROL Flush Magento Cache]**.

   Änderungen an der Storefront werden sofort nach der Leerung des Caches wirksam.

### Kategorien zuweisen

In [!DNL Live Search] zurückgegebene Produkte müssen einer [Kategorie“ ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). In Luma werden Produkte beispielsweise in Kategorien wie „Männer“, „Frauen“ und „Ausrüstung“ unterteilt. Unterkategorien sind auch für „Tops“, „Bottom“ und „Uhren“ eingerichtet. Diese Kategoriezuweisungen verbessern die Granularität beim Filtern.

## 6. Testen der Verbindung

Wenn sich Ihre Katalogdaten jetzt in SaaS befinden, testen Sie, um sicherzustellen, dass in den folgenden Szenarien Produktdaten zurückgegeben werden:

- Das [!UICONTROL Search] gibt die Ergebnisse korrekt zurück
- Kategoriebesuche gibt Ergebnisse korrekt zurück
- Facetten sind als Filter auf Suchergebnisseiten verfügbar

Wenn alles ordnungsgemäß funktioniert, ist [!DNL Live Search] installiert, angeschlossen und einsatzbereit.

Wenn Sie auf Probleme in der Storefront stoßen, überprüfen Sie die `var/log/system.log`-Datei auf API-Kommunikationsfehler oder -Fehler auf der Service-Seite.

Um [!DNL Live Search] durch eine Firewall zuzulassen, fügen Sie `commerce.adobe.io` zur Zulassungsliste hinzu.

## 7. Überprüfen, ob Ereignisse Daten erfassen

Stellen Sie sicher, dass die für Ihre Site bereitgestellten Storefront-Ereignisse funktionieren. Dies ist besonders für Headless-Implementierungen wichtig.

- Überprüfen Sie die [Ereignisse](events.md) die für die [!DNL Live Search] erforderlich sind.
- Stellen Sie sicher[ dass im ](performance.md)Live Search“ Daten aus Ihren produktionsfremden Umgebungen angezeigt werden.
- [Ereignissammlung überprüfen](../product-recommendations/verify.md). Obwohl diese Seite im [!DNL Product Recommendations]-Handbuch enthalten ist, gelten die Überprüfungsschritte auch für [!DNL Live Search].

## 8. Für Ihre Storefront anpassen

Sie haben die [!DNL Live Search]-Erweiterung installiert, synchronisiert, validiert und Ihre Daten konfiguriert. Der nächste Schritt besteht darin, sicherzustellen, dass die [!DNL Live Search] Widgets dem Erscheinungsbild Ihres Stores entsprechen.

Sie können die Pop-up- und PLP-Widgets nach Bedarf gestalten, indem Sie benutzerdefinierte CSS-Regeln definieren. Siehe [Formatieren von Popover](storefront-popover.md#styling-popover-example)Elementen und [Widget „Produktauflistungsseite“](plp-styling.md#styling-example).

Wenn Sie die Funktionalität der Widgets erweitern möchten, ist der Quell-Code für jedes Widget in einem öffentlichen Repository verfügbar.
In diesem Szenario können Sie die JavaScript für Ihre eigenen Anforderungen anpassen und dann Ihren benutzerdefinierten Code in Ihrem CDN hosten. Dieses benutzerdefinierte Skript kommuniziert mit dem [!DNL Live Search]-Service und gibt die Ergebnisse wie normal zurück, sodass Sie die Funktionalität des Widgets steuern können.

- [PLP Widget Repo](https://github.com/adobe/storefront-product-listing-page)
- [Suchleistenrepo](https://github.com/adobe/storefront-search-as-you-type)

## Aktualisieren von [!DNL Live Search]

Bevor Sie die Live Search aktualisieren, führen Sie Folgendes über die Befehlszeile aus, um die installierte Version der Live Search zu überprüfen:

```bash
composer show magento/module-live-search | grep version
```

Um [!DNL Live Search] zu aktualisieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/live-search --with-dependencies
```

Um auf eine Hauptversion zu aktualisieren, z. B. von 3.1.1 auf 4.0.0, bearbeiten Sie die [!DNL Composer]-`.json` des Projekts wie folgt:

1. Wenn Ihre derzeit installierte `magento/live-search` Version `3.1.1` oder niedriger ist und Sie ein Upgrade auf Version `4.0.0` oder höher durchführen, führen Sie vor dem Upgrade den folgenden Befehl aus:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Führen Sie den folgenden Befehl aus, um Informationen zur derzeit installierten `magento/live-search`-Version zu erhalten:

   ```bash
   composer show magento/live-search
   ```

1. Öffnen Sie die `composer.json` und suchen Sie nach `magento/live-search`.

1. Aktualisieren Sie im Abschnitt `require` die Versionsnummer wie folgt:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. `composer.json` speichern. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Deinstallieren von [!DNL Live Search]

Informationen zum Deinstallieren von [!DNL Live Search] finden Sie unter [Module deinstallieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## Pakete [!DNL Live Search]

Die [!DNL Live Search]-Erweiterung besteht aus den folgenden Paketen:

| Package | Beschreibung |
|--- |--- |
| `module-live-search` | Ermöglicht Händlern die Konfiguration ihrer Sucheinstellungen für Facetten, Synonyme, Abfrageregeln usw. und bietet Zugriff auf einen schreibgeschützten GraphQL-Playground zum Testen von Abfragen über *Admin*. |
| `module-live-search-adapter` | Leitet Suchanfragen von der Storefront zum [!DNL Live Search]-Service und rendert die Ergebnisse in der Storefront. <br />- Kategoriendurchsuchen - Leitet Anfragen von der Storefront ([ Navigation) ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) den Suchdienst weiter.<br />- Globale Suche - Leitet Anfragen aus dem Feld [Schnellsuche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) oben rechts in der Storefront an den [!DNL Live Search]-Service weiter. |
| `module-live-search-storefront-popover` | Ein Pop-up „Suche nach Eingabe“ ersetzt die standardmäßige Schnellsuche und gibt Daten und Miniaturansichten der wichtigsten Suchergebnisse zurück. |

## [!DNL Live Search] Abhängigkeiten

Das [!DNL Composer]-Metapaket zur Installation der [!DNL Live Search]-Erweiterung enthält die folgenden Modulabhängigkeiten.

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## Erweiterte Konzepte

In den folgenden Abschnitten finden Sie weiterführende Themen zur Verwendung von [!DNL Live Search] und [!DNL Catalog Service].

### Endpunkt

[!DNL Live Search] kommuniziert über den Endpunkt unter `https://catalog-service.adobe.io/graphql`.

Da [!DNL Live Search] keinen Zugriff auf die vollständige Produktdatenbank hat, weisen die [!DNL Live Search] GraphQL- und Commerce Core-GraphQL-APIs keine vollständige Parität auf.

Adobe empfiehlt, die SaaS-APIs direkt aufzurufen - insbesondere den Catalog Service-Endpunkt.

- Leistungssteigerung und Reduzierung der Prozessorlast durch Umgehung des Commerce-Datenbank-/GraphQL-Prozesses
- Nutzen Sie die [!DNL Catalog Service] Federation, um [!DNL Live Search], [!DNL Catalog Service] und [!DNL Product Recommendations] von einem einzigen Endpunkt aus aufzurufen.

Für einige Anwendungsfälle ist es möglicherweise besser, [!DNL Catalog Service] für Produktdetails und ähnliche Fälle aufzurufen. Weitere Informationen finden [ unter ](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/).

Wenn Sie über eine benutzerdefinierte Headless-Implementierung verfügen, finden Sie in den [!DNL Live Search] Referenzimplementierungen weitere Informationen:

- [PLP-Widget](https://github.com/adobe/storefront-product-listing-page)
- [Live Search-Feld](https://github.com/adobe/storefront-search-as-you-type)

Die automatische Erfassung von Benutzerinteraktionsdaten funktioniert nicht standardmäßig, wenn Sie nicht die Standardkomponenten wie den Suchadapter, Luma-Widgets oder AEM CIF-Widgets verwenden. Adobe Sensei verwendet diese erfassten Daten für intelligentes Merchandising und Leistungsüberwachung. Um dieses Problem zu beheben, müssen Sie eine benutzerdefinierte Lösung entwickeln, um diese Datenerfassung auf Headless-Weise zu implementieren.

Die neueste Version von [!DNL Live Search] verwendet bereits [!DNL Catalog Service].

### Sprachunterstützung

[!DNL Live Search]-Widgets unterstützen die folgenden Sprachen:

|  |  |  |  |
|--- |--- |--- |--- |
| Sprache | Region | Sprach-Code | Magento-Gebietsschema |
| Bulgarisch | Bulgarien | bg_BG | bg_BG |
| Katalanisch | Spanien | ca_ES | ca_ES |
| Tschechisch | Tschechische Republik | cs_cz | cs_cz |
| Dänisch | Dänemark | da_DK | da_DK |
| Deutsch | Deutschland | de_DE | de_DE |
| Griechisch | Griechenland | el_GR | el_GR |
| Englisch | Vereinigtes Königreich | en_GB | en_GB |
| Englisch | Vereinigte Staaten | en_US | en_US |
| Spanisch | Spanien | es_ES | es_ES |
| Estnisch | Estland | et_EE | et_EE |
| Baskisch | Spanien | eu_ES | eu_ES |
| Persisch | Iran | fa_IR | fa_IR |
| Finnisch | Finnland | fi_FI | fi_FI |
| Französisch | Frankreich | fr_FR | fr_FR |
| Galizisch | Spanien | gl_ES | gl_ES |
| Hindi | Indien | hi_IN | hi_IN |
| Ungarisch | Ungarn | hu_HU | hu_HU |
| Indonesisch | Indonesien | id_ID | id_ID |
| Italienisch | Italien | it_IT | it_IT |
| Koreanisch | Südkorea | ko_KR | ko_KR |
| Litauisch | Litauen | lt_LT | lt_LT |
| Lettisch | Lettland | lv_LV | lv_LV |
| Norwegisch | Norwegen Bokmal | nb_NO | nb_NO |
| Niederländisch | Niederlande | nl_NL | nl_NL |
| Polnisch | Polen | pl_PL | pl_PL |
| Portugiesisch | Brasilien | pt_BR | pt_BR |
| Portugiesisch | Portugal | pt_PT | pt_PT |
| Rumänisch | Rumänien | ro_RO | ro_RO |
| Russisch | Russland | ru_RU | ru_RU |
| Schwedisch | Schweden | sv_SE | sv_SE |
| Thailändisch | Thailand | th_TH | th_TH |
| Türkisch | Türkei | tr_TR | tr_TR |
| Chinesisch | China | zh_CN | zh_Hans_CN |
| Chinesisch | Taiwan | zh_TW | zh_hant_TW |

Wenn das Widget erkennt, dass die Commerce Admin-Spracheinstellung mit einer unterstützten Sprache übereinstimmt, wird standardmäßig diese Sprache verwendet. Andernfalls ist für das Widget standardmäßig Englisch festgelegt. In Admin wird die Spracheinstellung durch Navigieren zu _[!UICONTROL Stores]_> [!UICONTROL Settings] >_[!UICONTROL Configuration]_ > _[!UICONTROL General]_> [!UICONTROL Country Options] konfiguriert.

Admins können auch die Sprache des [Suchindex](settings.md#language) festlegen, um bessere Suchergebnisse sicherzustellen.

### Widget-Code-Repository

Der Code für das Widget für die Produktauflistungsseite und das Widget für das Live-Suchfeld können von GitHub heruntergeladen werden.

Entwickler, die Zugriff auf den Code haben, können seine Funktionsweise und sein Aussehen vollständig anpassen. Sie hosten den Code auf ihren eigenen Servern, verwenden jedoch weiterhin den [!DNL Live Search].

- [PLP-Widget](https://github.com/adobe/storefront-product-listing-page)
- [Suchleiste](https://github.com/adobe/storefront-search-as-you-type)

### Datenexporterweiterung

Nachdem die Live Search aktiviert wurde, synchronisiert die Datenexporterweiterung Commerce-Daten zwischen der Commerce-Anwendung und der Live Search. Dadurch wird sichergestellt, dass die aktuellen Commerce-Daten in der Storefront verfügbar sind. Im Admin-Bereich können Sie den Synchronisierungsstatus mithilfe des Daten-Management-Dashboards überprüfen. Sie können den Datenexportprozess mithilfe der Commerce-CLI und -Protokolle verwalten und Fehler beheben. Weitere Informationen finden Sie im [Datenexporthandbuch](../data-export/overview.md).

### Inventory management

[!DNL Live Search] unterstützt [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction)-Funktionen in Commerce (früher als Multi-Source Inventory oder MSI bezeichnet). Um die vollständige Unterstützung zu aktivieren[ müssen Sie ](install.md#updating-live-search) Abhängigkeitsmodul-`commerce-data-export` auf Version 102.2.0 oder höher aktualisieren.

[!DNL Live Search] gibt einen booleschen Wert zurück, der angibt, ob ein Produkt in Inventory management verfügbar ist, aber keine Informationen darüber enthält, welche Quelle den Bestand hat.

### Preisindexierer

Live Search-Kunden können den [SaaS-Preisindexer](../price-index/price-indexing.md) verwenden, der schnellere Preisänderungsaktualisierungen und Synchronisierungszeiten ermöglicht.

### Preisstützung

Live Search-Widgets unterstützen die meisten, aber nicht alle von Adobe Commerce unterstützten Preistypen.

Derzeit werden Basispreise unterstützt. Nicht unterstützte erweiterte Preise sind:

- Kosten
- Mindestpreis

Unter [API Mesh](../catalog-service/mesh.md) finden Sie komplexere Preisberechnungen.

Das Preisformat unterstützt die Gebietsschema-Konfigurationseinstellung in der Commerce-Instanz: *Stores* > Settings > *Configuration* > General > *General* > Local Options > Locale.

### Headless-Storefront-Unterstützung

Optional müssen Sie möglicherweise das Modul `module-data-services-graphql` installieren, das die bestehende GraphQL-Abdeckung des Programms erweitert, um Felder einzuschließen, die für die Verhaltensdatenerfassung in der Storefront erforderlich sind.

```bash
composer require magento/module-data-services-graphql
```

Dieses Modul fügt zusätzliche Kontexte zu GraphQL-Abfragen hinzu:

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### B2B-Unterstützung

[!DNL Live Search] unterstützt [B2B-](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview) mit zusätzlichen [Einschränkungen](boundaries-limits.md#b2b-and-category-permissions).

### PWA-Support

[!DNL Live Search] funktioniert mit PWA Studio, aber die Benutzenden sehen möglicherweise leichte Unterschiede im Vergleich zu anderen Commerce-Implementierungen. Grundlegende Funktionen wie die Suche und die Produktlistenseite funktionieren in Venia, aber einige Permutationen von GraphQL funktionieren möglicherweise nicht richtig. Es können auch Leistungsunterschiede auftreten.

- Die aktuelle PWA-Implementierung von [!DNL Live Search] benötigt mehr Verarbeitungszeit, um Suchergebnisse zurückzugeben, als mit der nativen Commerce-Storefront [!DNL Live Search].
- [!DNL Live Search] in PWA unterstützt nicht [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Daher funktionieren Suchberichte und intelligentes Merchandising nicht in PWA-Storefronts.
- Bei Verwendung von [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) unterstützt GraphQL das direkte Filtern nach `description`, `name` oder `short_description` nicht. Diese Felder können jedoch mit einem allgemeineren Filter zurückgegeben werden.

Um [!DNL Live Search] mit PWA Studio verwenden zu können, müssen Integratoren außerdem:

1. Installieren Sie [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Legen Sie die `environmentId` im `storeDetails` fest.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Cookies

[!DNL Live Search] sammelt Benutzerinteraktionsdaten im Rahmen seiner grundlegenden Funktionalität, und Cookies werden zum Speichern dieser Daten verwendet. Bei der Erfassung von Benutzerinformationen muss der Benutzer der Speicherung von Cookies zustimmen. [!DNL Live Search] und [!DNL Product Recommendations] teilen den Datenstrom und verwenden daher denselben Cookie-Mechanismus. Weitere Informationen hierzu finden Sie unter [ von Cookie-Einschränkungen](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/developer/setting-cookie).
