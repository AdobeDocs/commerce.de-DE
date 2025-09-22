---
title: '[!DNL SaaS Data Export Extension] Versionshinweise'
description: Die neuesten Versionsinformationen für  [!DNL Data Export Extension]  für Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 8ae51d3d-8c12-4607-b7e5-985033143a84
source-git-commit: 4a25bcb82f98eb44c83a186caa6e5d6d664851d4
workflow-type: tm+mt
source-wordcount: '1669'
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

## Version 103.4.12

![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem auf der Produktdetailseite (PDP) keine Rabatte für Katalogpreisregeln angezeigt wurden, wenn die Preisgestaltung für Kundengruppen vorhanden war. Die PDP zeigt nun korrekt den niedrigsten Preis an.<!--MDEE-1158-->

## Version 103.4.11

![Neu](../assets/new.svg) [!BADGE nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."}
Es wurde Unterstützung für zusätzliche Produktattribute hinzugefügt, um Steuerklasse-, Attributsatz- und Bestandsdaten aus Commerce-Produktkonfigurationen im Produkt-Feed einzuschließen. Kunden, die diese Attribute in Produktexport-Feeds einbeziehen möchten, müssen das Modul Zusätzliche Produktattribute zu ihrem Adobe Commerce-Projekt hinzufügen. Siehe [Hinzufügen von Steuerklassen-, Attributsatz- und Bestandsattributen](add-tax-attribute-set-inventory-attributes.md).<!--MDEE-1135-->
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, das zu einer falschen Synchronisierung gelöschter Produktaktualisierungen führte, wenn während eines vollständigen Produktindex ein Fehler auftrat. Jetzt werden alle Produktlöschungen korrekt synchronisiert, selbst wenn während des Indizierungsprozesses ein Fehler auftritt. <!--MDEE-1144-->

## Version 103.4.10

![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem für einige dynamisch erstellte Attribute der falsche Typ (`text` statt `OBJECT`) zurückgegeben wurde. Jetzt werden durchgängig die richtigen Typinformationen zurückgegeben, sodass keine manuellen Neusynchronisierungen oder Workarounds mehr erforderlich sind.<!--MDEE-1131-->
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem die Erfassung von Produktdaten während partieller Synchronisierungen aufgrund von Fehlern im Lagerplatzanbieter fehlschlagen konnte. Diese Fehlerbehebung stellt sicher, dass Produktdaten zuverlässig exportiert werden und keine Produkt-IDs aufgrund von Fehlern im Zusammenhang mit LowStock übersprungen werden.<!--MDEE-1132-->

## Version 103.4.9

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Produktpreis-Feeds nicht neu generiert wurden, wenn ein Produkt gelöscht oder die Produkt-SKU geändert wurde.<!--MDEE-1125-->
![Korrektur](../assets/fix.svg) Die Verarbeitung von Produktaktualisierungen wurde verbessert, um sicherzustellen, dass Änderungen beim Aktualisieren eines neu erstellten Produkts mit derselben SKU wie ein zuvor gelöschtes Produkt korrekt widergespiegelt werden. Die Produktsynchronisierung verwendet jetzt korrekt aktualisierte Produkt-IDs, um einen korrekten und zuverlässigen Datenexport zu gewährleisten.<!--MDEE-1126-->
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem der Katalog-Service veraltete Variantendaten für konfigurierbare Produkte zurückgeben konnte, indem sichergestellt wurde, dass Produktaktualisierungsereignisse nach dem Löschen von Attributen veröffentlicht wurden.<!--MDEE-1127-->

## Version 103.4.8

![Neu](../assets/new.svg) Es wurden Stufenpreisinformationen zum Feed „Preise“ hinzugefügt. <!--MDEE-1070-->
![Fehlerbehebung](../assets/fix.svg) Die Data Exporter-Erweiterung exportiert jetzt die Paketauswahlpreise für die Website korrekt, um sicherzustellen, dass die Storefront-Preise die genauen Werte basierend auf der Konfiguration „Katalogpreisbereich“ widerspiegeln.<!--MDEE-1115-->
![Beheben](../assets/fix.svg) Zuvor wurden Produkte mit einem falschen `lowStock=true` synchronisiert, wenn Inventory management (Multi-Source-Inventory management) mit Schwellenwertkonfiguration verwendet wurde. Dieses Problem wurde behoben, um genaue Berichte über niedrige Lagerbestände sicherzustellen.<!--MDEE-1113-->

## Version 103.4.7

![Beheben](../assets/fix.svg) Veraltete Tabellen wurden entfernt, in denen Kategorieberechtigungen für Produkte gespeichert waren. <!--MDEE-1065-->

## Version 103.4.6

![Korrigieren](../assets/fix.svg) Exportieren Sie herunterladbare Adobe Commerce-Produktdaten mithilfe des `ac_downloadable`-Attributs zur Verwendung mit Adobe Commerce Optimizer. <!--MDEE-1043-->
![Behebung](../assets/fix.svg) Behebung eines kritischen Installationsfehlers für Adobe Commerce Version 2.4.4. <!--MDEE-1074-->

## Version 103.4.5

![Neu](../assets/new.svg) Der SaaS-Datenexport unterstützt jetzt den Adobe Commerce `giftcard`-Produkttyp. Im Daten-Feed werden Geschenkkartenprodukte als einfache Produkte mit dem Produkteigenschaftstyp `ac_giftcard` exportiert. <!--MDEE-1042-->
![Beheben](../assets/fix.svg) Verbessertes Reporting zu Datenexportfehlern. Die Protokolle enthalten jetzt detailliertere Fehlermeldungen, einschließlich originaler technischer Details, um das Debugging und die Verfolgung von Fehlern zu vereinfachen. <!--MDEE-1064-->

## Version 103.4.4

![Neu](../assets/new.svg) Es wurde eine Warnmeldung hinzugefügt, die angezeigt wird, wenn das `cleanup-feed`-Argument zum `saas:resync` CLI-Befehl hinzugefügt wird. Die Option `--cleanup-feed` sollte vorsichtig und nur in bestimmten Szenarien wie nach der Umgebungsbereinigung oder mit der Option `--dry-run` verwendet werden. Die Verwendung in anderen Fällen kann zu Datenverlust und Synchronisationsproblemen führen. <!--MDEE-1047-->
![Beheben](../assets/fix.svg) Der `x-request-id` aus der Server-Antwort wurde hinzugefügt, um die Rückverfolgbarkeit zu verbessern. <!--MDEE-1041-->
![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem der Synchronisierungsstatus nicht für den gesamten Feed-Batch gespeichert wurde, was zu einer unnötigen Neusynchronisierung führte. <!--MDEE-1049-->
![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem alle Feeds im Feed-Batch während der Synchronisierung übersprungen wurden, wenn ein Feed einen Fehler enthielt. <!--MDEE-976-->
![Korrigieren](../assets/fix.svg) Es wurde Unterstützung für Dimensionen im Kategorienberechtigungs-Indexer hinzugefügt. <!--MDEE-654-->

## Version 103.4.3

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Produkte während des Datenexports aufgrund fehlender EAV-Attribute übersprungen wurden. <!--MDEE-970-->

## Version 103.4.2

![Beheben](../assets/fix.svg) Es wurde die Möglichkeit hinzugefügt, beim Ausführen der Testresynchronisierung mithilfe des Befehls `saas-export.log` mit der Umgebungsvariablen `saas:resync --dry-run` Entitäts-Payloads im `EXPORTER_EXTENDED_LOG=1` zu erfassen. <!--MDEE-1023-->

## Version 103.4.1

![Beheben](../assets/fix.svg) Es wurde ein Präfix zu QueryXml-Cache-Schlüsseln hinzugefügt, um Namenskonflikte mit anderen Modulen zu verhindern. <!--MDEE-1019-->

## Version 103.4.0

![Fehlerbehebung](../assets/fix.svg) Der Feed „Produktüberschreibungen“ sendet keine Berechtigungen mehr, wenn das Produkt keiner Kategorie zugewiesen ist.<!--MDEE-449-->

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

![Korrektur](../assets/fix.svg) Es wurde Unterstützung für die Datenübertragungs-Auditprotokollierung hinzugefügt, indem ein Mechanismus hinzugefügt wird, um jedes Mal, wenn Daten von der Commerce-Instanz an einen Commerce-Service-`data_sent_outside` übertragen werden, ein <!--MDEE-785-->-Ereignis zu senden

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
