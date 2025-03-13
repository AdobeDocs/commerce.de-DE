---
title: '[!DNL SaaS Data Export Extension] Versionshinweise'
description: Die neuesten Versionsinformationen für  [!DNL Data Export Extension]  für Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 8ae51d3d-8c12-4607-b7e5-985033143a84
source-git-commit: 14231826dba842edb908005ea43b1893a324c68f
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 0%

---

# Versionshinweise zur [!DNL SaaS Data Export]-Erweiterung

In diesen Versionshinweisen werden die neuesten Versionen der [!DNL SaaS data export]-Erweiterung beschrieben. Unterstützung wird für die aktuelle Hauptversion bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.

Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bug](../assets/bug.svg) Bekannte Probleme


>[!NOTE]
>
>Die SaaS-Datenexporterweiterung ist eine Sammlung von Modulen, die automatisch mit der Live-Suche, Produktempfehlungen und dem Katalog-Service installiert werden. Sie können die auf Ihrem System installierte Version mit dem Composer überprüfen. In einigen Fällen empfiehlt es sich, ein Upgrade der Datenexporterweiterung auf dem System durchzuführen, um Fehlerbehebungen oder neue Funktionen zu erhalten, ohne die Commerce Service-Version zu aktualisieren.

## Aktuelle Hauptversion

## Version 103.3.21

![Korrektur](../assets/new.svg) Es wurde eine Funktion hinzugefügt, um `products`-, `productOverrides`- und `productAttributes`-Feeds basierend auf einer bestimmten Liste von Produkt-SKUs teilweise zu synchronisieren. Verwenden Sie die neue Funktion, indem Sie dem Befehl CLI neu synchronisieren die Option `--by-ids` hinzufügen: <!--MDEE-606-->

```shell
bin/magento saas:resync --feed=<FEED_NAME> --by-ids='<SKU1>,<SKU2>,<SKU3>
```

![Beheben](../assets/fix.svg) Reduzierte potenzielle Kompatibilitätsprobleme mit PHP 8.4, indem veraltete Funktionen adressiert wurden. <!--MDEE-1002-->

## Version 103.3.20

![Beheben](../assets/fix.svg) Behebung nicht nachverfolgbarer `BulkException` im `cron.log` durch Verbesserung der Fehlermeldung im Zusammenhang mit Fehlern beim Katalogdatenexport aus Cron-Auftragsfehlern.<!--MDEE-966-->
![Korrektur](../assets/fix.svg) Verbesserte Leistung des Prozesses der Neusynchronisierung von Produkten auf Instanzen mit einer hohen Anzahl von Store-Ansichten. <!--MDEE-974-->

## Version 103.3.19

![Korrigieren](../assets/fix.svg) Die Datenexporterweiterung wurde aktualisiert, um die Erweiterbarkeit von Feeds zu verbessern. <!--MDEE-936-->
![Korrektur](../assets/fix.svg) Der Datenexportprozessor überprüft jetzt den Indexerstatus vor einer vollständigen Neusynchronisierung, um einen versehentlichen Datenverlust in der Feed-Tabelle zu vermeiden.

## Version 103.3.18

![Behebung](../assets/fix.svg) Staging-Updates für Produkt- und Kategorienentitäten werden jetzt bei Aktualisierungen von Datenexportdaten korrekt ausgelöst.<!--MDEE-963-->

## Version 103.3.17

![Fix](../assets/fix.svg) Hinzugefügte Kompatibilität für PHP 8.4. <!--MDEE-941-->

## Version 103.3.16

![Fix](../assets/fix.svg) Optionswerte können für konfigurierbare Produkte für mehrere Store-Ansichten leer sein. <!--MDEE-926-->

## Version 103.3.15

![Fix](../assets/fix.svg) Sicherstellen eines stabilen Betriebs von Integrationstests auf älteren Konfigurationen. <!--MDEE-869-->
![Beheben](../assets/fix.svg) Beenden der Übertragung unnötiger Attributoptionen. <!--MDEE-882-->
![Behebung](../assets/fix.svg) Es wurde die Fehlermeldung behoben, die an das Datenexportprotokoll gesendet wurde, wenn die Datenserialisierung fehlschlägt. <!--MDEE-913-->
![Fix](../assets/fix.svg) Die Zuverlässigkeit einfacher Produktaktualisierungen wurde durch zusätzliche Testabdeckung verbessert. <!--MDEE-886-->

## Version 103.3.14

![Fehlerbehebung](../assets/fix.svg) Der Exporter-Indexer behält jetzt den richtigen Status für abhängige Indexer. Zuvor wurden diese Indizes fälschlicherweise ungültig gemacht und erforderten zusätzliche Prüfungen und Validierungen, die die Indizierungsleistung verlangsamten. <!--MDEE-866-->

## Version 103.3.13

![Korrektur](../assets/fix.svg) Verbesserte Leistung des Datensynchronisierungsprozesses durch Hinzufügen eines lokalen Cache für Attributdatenoptionen.<!--MDEE-864-->

## Version 103.3.12

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, das die Synchronisierungszeit für einfache und virtuelle Produkte verlängerte. <!--MDEE-861-->

## Version 103.3.11

![Fehlerbehebung](../assets/fix.svg) Der Datenexportdienst sendet jetzt Sonderpreisdaten für Bundle-Produkte als Prozentsatz und korrigiert so ein vorheriges Problem, bei dem er als Endpreis gesendet wurde. <!--MDEE-854-->
![Korrigieren](../assets/fix.svg) Die Monolog-Implementierung wurde aus Kompatibilitätsgründen mit Monolog 3 aktualisiert. <!--MDEE-858-->

## Version 103.3.10

![Korrigieren](../assets/fix.svg) Es wurde eine Filterung mehrerer Storeviews für den Feed mit benutzerdefinierten Optionen für das Produkt behoben. <!--MDEE-842-->
![Korrigieren](../assets/fix.svg) Ungültige Feeds werden erst erneut gesendet, wenn sich der Hash-Wert des Feeds geändert hat.<!--MDEE-848-->

## Version 103.3.9

![Behebung](../assets/fix.svg) Wenn eine Entität gelöscht wird, wird das `deleted`-Flag jetzt für die Scoping-Service-Feeds für die Website (`scopesWebsite`) und die Kundengruppe (`scopesCustomerGroup`) übernommen.<!--MDEE-839-->

## Version 103.3.8

![Beheben](../assets/fix.svg) Deaktivierte Konfigurationsoptionen werden nicht mehr als aktive Optionen exportiert.<!--MDEE-812-->
![Beheben](../assets/fix.svg) Optionen und Werte werden jetzt für ein konfigurierbares Produkt aktualisiert, wenn Änderungen an einem untergeordneten Produkt vorgenommen werden. <!--MDEE-835-->
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, zusätzliche Systemattributdaten in den Produktattribut-Feed aufzunehmen.

## Version 103.3.7

![Beheben](../assets/fix.svg) Es wurden unnötige Abhängigkeiten aus dem InventoryDataExporter-Modul entfernt.
![Behebung](../assets/fix.svg) Erforderliche Versionen für im Modul CatalogInventoryDataExporter enthaltene Inventarmodule wurden geändert, um Adobe Commerce Version 2.4.4 zu unterstützen.

## Version 103.3.6

![Beheben](../assets/fix.svg) Es wurden Deadlocks behoben, die während der Feed-Neuindizierung im Multi-Thread-Modus aufgetreten sind. Abfragen sind jetzt in Einfüge- und Aktualisierungsvorgänge unterteilt.
![Fix](../assets/fix.svg) Die Preisabfrage für große Kataloge mit vielen Websites wurde optimiert.
![Neu](../assets/new.svg) Es wurde eine Wiederholungslogik hinzugefügt, um fehlgeschlagene Transaktionen erneut auszuführen, wenn Deadlocks auftreten.

## Version 103.3.5

![Korrigieren](../assets/fix.svg) Setzen Sie die Abhängigkeit für die neueste kompatible Datenexportversion für das SaaS-Common-Modul.

![Beheben](../assets/fix.svg) hat `ScopeConfig` Instanz durch `ServiceConfigInterface` ersetzt, um verschiedene Service-Konfigurationen zu unterstützen.

## Version 103.3.4

![Korrektur](../assets/fix.svg) Es wurde Unterstützung für die Datenübertragungs-Auditprotokollierung hinzugefügt, indem ein Mechanismus hinzugefügt wird, um jedes Mal, wenn Daten von der Commerce-Instanz an einen Commerce-Service-<!--MDEE-785--> übertragen werden, ein `data_sent_outside`-Ereignis zu senden

## Version 103.3.3

![Neu](../assets/new.svg) Der SaaS-Datenexport speichert jetzt Entitäts-Attribut-Wert(EAV)-Attribute für die Attributmetadatenabfrage zwischen.

![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem der `InventoryStockStatus`-Feed beim erneuten Versuch nicht gespeichert wurde, wenn das Produkt gelöscht wurde.

## Version 103.3.2

![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem das `modifiedAt` Feld in entfernten Entitäts-Feeds fehlte.

## Version 103.3.1

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, das dazu führte, dass bei der Neuindizierung von Produkt-Feeds nach der Installation von Page Builder eine `Invalid Template File` angezeigt wurde.

## Version 103.3.0

![Neu](../assets/new.svg) Migrierte Feed-Tabellen für den sofortigen Export in die einheitliche Struktur:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Neu](../assets/new.svg) Migrierte Katalog- und Inventar-Feeds zur sofortigen Exportlösung.

![Neu](../assets/new.svg) Umbenannte Cron-Jobs für den sofortigen Export von Feed nach `*_feed_resend_failed_items`.

![Neu](../assets/new.svg) Umbenannte sofortige Export-Feeds, Indexeransichts-IDs und Änderungsprotokolltabellen.
- Feed-Tabellen (und Indexeransichts-IDs):
   - `catalog_data_exporter_products` -> `cde_products_feed`
   - `catalog_data_exporter_product_attributes` -> `cde_product_attributes_feed`
   - `catalog_data_exporter_categories` -> `cde_categories_feed`
   - `catalog_data_exporter_product_prices` -> `cde_product_prices_feed`
   - `catalog_data_exporter_product_variants` -> `cde_product_variants_feed`
   - `inventory_data_exporter_stock_status` -> `inventory_data_exporter_stock_status_feed`
- Ändern von Protokolltabellennamen - folgt demselben Benennungsmuster wie die Feed-Tabellen, aber ändern Sie die Protokolltabellennamen, um ein `_cl` Suffix hinzuzufügen.  Beispiel: `catalog_data_exporter_products_cl`-> `cde-products_feed_cl`
Wenn Sie über benutzerdefinierten Code verfügen, der auf eine dieser Entitäten verweist, aktualisieren Sie die Verweise mit den neuen Namen, um sicherzustellen, dass Ihr Code weiterhin ordnungsgemäß funktioniert.

![Korrigieren](../assets/fix.svg) Legen Sie `modified_at` Feld in den Feed-Daten nur für Feeds fest, die dies erfordern.

![Korrigieren](../assets/fix.svg) Ändern Sie die `productAttributes` Abfrage, um nur Produktattribute abzurufen.

## Version 103.2.6

![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, das verhinderte, dass Feeds neu indiziert wurden, wenn Tabellen ein Präfix hatten.

## Version 103.2.5

![Korrigieren](../assets/fix.svg) Die Preisabfrage wurde optimiert.

## Version 103.2.4

![Beheben](../assets/fix.svg) Es wurde ein falscher Lagerstatus behoben, der für ein Produkt angezeigt wurde, wenn Commerce Inventory management aktiviert ist.

## Version 103.2.3

![Fix](../assets/fix.svg) Feste Sonderpreise auf Website-Ebene.
![Korrigieren](../assets/fix.svg) Es wurde ein Mutex für alle Feeds hinzugefügt, die verarbeitet werden.


## Version 103.2.2

![Beheben](../assets/fix.svg) Verbesserte Strategie für Feeds-Batching für große Kataloge. Die Tabelle Batches ist jetzt mit einer begrenzten Anzahl von IDs gefüllt, um die Speichernutzung zu reduzieren.

![Fix](../assets/fix.svg) Beseitigt die Abhängigkeit von CommerceInventoryDataExporter von MSI-Modulen.

![Korrigieren](../assets/fix.svg) Verbesserte `commerce-data-exporter`, um mehr Informationen zu sammeln und nach verschiedenen Exportphasen zu organisieren.

## Version 103.2.1

- Aktualisierte Version veröffentlicht.

## Version 103.2.0

- Multi-Thread-Datensynchronisation für Produkte und Preise hinzugefügt.
