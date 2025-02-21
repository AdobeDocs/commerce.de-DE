---
title: SaaS-Datenexport-Befehlszeilenschnittstelle
description: Erfahren Sie, wie Sie die Befehle der Befehlszeilenschnittstelle verwenden, um Feeds und Prozesse für die SaaS [!DNL data export extension] Services von Adobe Commerce zu verwalten.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Referenz zur Befehlszeilenschnittstelle für den SaaS-Datenexport

Entwickler und Systemadministratoren können Synchronisierungsvorgänge für den SaaS-Datenexport mithilfe des [Adobe Commerce-Befehlszeilen-Tools (](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli)) verwalten. Der Befehl `saas:resync` ist im `magento/saas-export` enthalten.

Es wird von Adobe nicht empfohlen, den Befehl `saas:resync` regelmäßig zu verwenden. Typische Szenarien für die Verwendung des Befehls sind:

- Die Erstsynchronisierung
- Die [SaaS-Datenraum](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas)ID) wurde geändert, und Sie müssen Daten mit dem neuen Datenraum synchronisieren.
- Fehlerbehebung

## Erstsynchronisierung

>[!NOTE]
>Wenn Sie die Live Search oder Product Recommendations verwenden, müssen Sie die Erstsynchronisierung nicht ausführen. Der Prozess wird automatisch initiiert, nachdem Sie den Service mit Ihrer Commerce-Instanz verbunden haben.

Beim Trigger eines `saas:resync` über die Befehlszeile kann es je nach Kataloggröße einige Minuten bis einige Stunden dauern, bis die Daten aktualisiert werden.

Für die Erstsynchronisierung empfiehlt Adobe, die Befehle in der folgenden Reihenfolge auszuführen:

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

## Beispiele für Befehle

Bevor Sie `saas:resync` Befehle verwenden, überprüfen Sie die [Optionsbeschreibungen](#command-options).

- Vollständige Neusynchronisierung für einen Entitäts-Feed durchführen.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Bereits erfolgreich exportierte Feeds werden nicht resynchronisiert.

- Angegebene Feed- und Bereinigungsdaten vollständig neu synchronisieren

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Nur nach Durchführung eines [!DNL Data Space ID Cleanup] verwenden.

- Senden Sie bei sofortigen Export-Feeds alle Daten erneut an verbundene Commerce-Services, ohne die Indexdaten in der Feed-Tabelle zu kürzen

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Auflisten der verfügbaren Befehle und Optionen mit Beschreibungen.

  ```
  bin/magento saas:resync --help
  ```

## Befehlsoptionen

Die folgenden Optionen stehen für die Verwaltung von `saas:resync` zur Verfügung.

>[!NOTE]
>
>Der `saas:resync`-Befehl unterstützt außerdem erweiterte Optionen zur Verbesserung von Datenexportbefehlen durch Erhöhung der Batch-Größe und Hinzufügen von Multi-Thread-Verarbeitung. Siehe [Exportverarbeitung anpassen](customize-export-processing.md).

### `feed`

Diese erforderliche Option gibt an, welche Feed-Entität neu synchronisiert werden soll, z. B. `products`.

Der `feed` Optionswert kann jeden der verfügbaren Entitäts-Feeds enthalten:

- `products`: Produktdaten-Feed
- `productAttributes`: Datenfeed für Produktattribute
- `categories`: Daten-Feed für Kategorien
- `variants`: Konfigurierbarer Datenfeed für Produktvarianten
- `prices`: Daten-Feed für Produktpreise
- `categoryPermissions`: Daten-Feed für Kategorieberechtigungen
- `productOverrides`: Daten-Feed für Produktberechtigungen
- `inventoryStockStatus`: Datenfeed für den Lagerbestandsstatus
- `scopesWebsite`: Websites mit Stores und Store-Ansichten Daten-Feed
- `scopesCustomerGroup`: Kundengruppen-Daten-Feed
- `orders`: Daten-Feed für Kundenaufträge

Je nachdem, welche [Commerce](../landing/saas.md)-Services installiert sind, stehen möglicherweise andere Feeds für den `saas:resync`-Befehl zur Verfügung.

### `no-reindex`

Mit dieser Option werden die vorhandenen Katalogdaten ohne Neuindizierung erneut an [!DNL Commerce Services] übermittelt. Wenn diese Option nicht angegeben ist, führt der Befehl eine vollständige Neuindizierung durch, bevor die Daten synchronisiert werden.

Das Verhalten dieser Option hängt davon ab, ob der Feed im alten [ im sofortigen Exportmodus exportiert wird](data-synchronization.md#synchronization-modes)

- Bei älteren Export-Feeds kürzt der Synchronisierungsprozess indizierte Daten in der Feeds-Tabelle nicht. Stattdessen werden alle Daten erneut an den Adobe Commerce-Service gesendet.
- Bei Feeds mit sofortigem Export wird diese Option ignoriert, wenn sie angegeben wird. Bei diesen Feeds kürzt der Resynchronisierungsprozess den Index nicht und synchronisiert nur Aktualisierungen oder Elemente, bei denen zuvor ein Fehler aufgetreten ist, neu.

### `cleanup`

Diese Option bereinigt die Feed-Indexertabelle vor einer Synchronisierung. Wenn angegeben, führt der SaaS-Datenexport eine vollständige Neusynchronisierung für den angegebenen Feed durch und bereinigt alle vorhandenen Daten in der Feed-Tabelle.

Adobe empfiehlt, diesen Befehl nur nach Durchführung des [!DNL Data Space ID Cleanup]-Vorgangs zu verwenden.

>[!WARNING]
>
>**Verwenden Sie diese Option nicht regelmäßig**. Dies kann zu Problemen bei der Datensynchronisation in Adobe Commerce Services führen. Beispielsweise wird der `delete product event` möglicherweise nicht an den Adobe Commerce-Service weitergegeben, wenn die Option `cleanup` verwendet wird.

## Fehlerbehebung

Wenn in Connected Commerce Services keine erwarteten Daten angezeigt werden, beheben Sie Probleme, indem Sie die Fehlerprotokolle für den Datenexport überprüfen und den `saas:resync`-Befehl mit Umgebungsvariablen verwenden, um Payloads und Profilerdaten zu überprüfen. Siehe [Protokolle überprüfen und Fehler beheben](troubleshooting-logging.md).
