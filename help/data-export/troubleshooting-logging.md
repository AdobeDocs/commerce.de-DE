---
title: Überprüfen von Protokollen und Fehlerbehebung
description: Erfahren Sie, wie Sie  [!DNL data export]  Fehler mithilfe der Protokolle „data-export“ und „saas-export“ beheben können.
feature: Services
exl-id: d022756f-6e75-4c2a-9601-31958698dc43
source-git-commit: a1afed7b635a2b05c5c0e0d1c9bf4a07fc5eef31
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# Überprüfen von Protokollen und Fehlerbehebung

Die [!DNL data export]-Erweiterung stellt Protokolle zum Nachverfolgen von Datenerfassungs- und Synchronisierungsprozessen bereit.

## Protokolle

Protokolle sind im `var/log` auf dem Commerce-Anwendungsserver verfügbar.

| Protokollname | Dateiname | Beschreibung |
|-----------------| ----------| -------------|
| SaaS-Datenexportprotokoll | `commerce-data-export.log` | Stellt Informationen zu Datenexportaktivitäten bereit, z. B. zu Entitätsereignissen und vollständigen Resynchronisierungs-Triggern.  Jeder Protokolldatensatz hat eine bestimmte Struktur und enthält Informationen zu Feed, Vorgang, Status, verstrichener Zeit, Prozess-ID und dem Aufrufer. |
| SaaS-Datenexport-Fehlerprotokoll | `data-export-errors.log` | Stellt Fehlermeldungen und Stacktraces für Fehler bereit, die während des Datensynchronisierungsprozesses auftreten. |
| SaaS-Exportprotokoll | `saas-export.log` | Stellt Informationen zu den Daten bereit, die an Commerce SaaS-Services gesendet werden. |
| SaaS-Exportfehlerprotokoll | `saas-export-errors.log` | Enthält Informationen zu Fehlern, die beim Senden von Daten an Commerce SaaS-Services auftreten. |

Wenn keine erwarteten Daten für einen Adobe Commerce-Service angezeigt werden, können Sie anhand der Fehlerprotokolle für die Datenexporterweiterung feststellen, wo das Problem aufgetreten ist. Außerdem können Sie Protokolle um zusätzliche Daten zur Nachverfolgung und Fehlerbehebung erweitern. Siehe [Erweiterte Protokollierung](#extended-logging).

### Protokollformat

Jeder Protokolldatensatz weist die folgende Struktur auf.

```
[<log record datetime>] report.<log level>:
{
   "feed": "<feed name>",
   "operation": "<executed operation>",
   "status": "<status of operation>",
   "elapsed": "<time elapsed from script run>",
   "pid": "<process id that executed `operation`>",
   "caller": "<who called this `operation`>"
} [] []
```

>[!NOTE]
>
>Die JSON-basierte Zeichenfolge wird zur besseren Lesbarkeit geschönt.

In der folgenden Tabelle werden die Vorgangstypen beschrieben, die in den Protokollen aufgezeichnet werden können.

| Bedienung | Beschreibung | Beispiel für einen Aufrufer |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Vollständige Synchronisierung | Sammelt alle Daten für einen bestimmten Feed und sendet sie an die SaaS. | `bin/magento saas:resync --feed=products` |
| Teilweise Neuindizierung | Sammelt nur aktualisierte Entitäten in einem bestimmten Feed und sendet Daten an SaaS. Dieses Protokoll ist nur vorhanden, wenn aktualisierte Entitäten vorhanden sind. | `bin/magento cron:run --group=index` |
| Fehlgeschlagene Elemente wiederholen | Elemente für einen bestimmten Feed erneut an SaaS senden, wenn der vorherige Synchronisierungsvorgang aufgrund eines Commerce-Anwendungs- oder Server-Fehlers fehlgeschlagen ist. Dieses Protokoll ist nur vorhanden, wenn fehlgeschlagene Elemente vorhanden sind. | `bin/magento cron:run --group=saas_data_exporter` (beliebige &quot;*_data_Exporter“-Cron-Gruppe) |
| Vollständige Synchronisierung (veraltet) | Erfasst alle Daten für einen bestimmten Feed im alten Exportmodus und sendet sie an SaaS. | `bin/magento saas:resync --feed=categories` |
| Partielle Neuindizierung (veraltet) | Sendet aktualisierte Entitäten für einen bestimmten Feed im alten Exportmodus an SaaS. Dieses Protokoll ist nur vorhanden, wenn aktualisierte Entitäten vorhanden sind. | `bin/magento cron:run --group=index` |
| Teilweise Synchronisierung (veraltet) | Sendet aktualisierte Entitäten für einen bestimmten Feed im alten Exportmodus an SaaS. Dieses Protokoll ist nur vorhanden, wenn aktualisierte Entitäten vorhanden sind. | `bin/magento cron:run --group=saas_data_exporter` (beliebige &quot;*_data_Exporter“-Cron-Gruppe) |


### Beispiele für die Protokollierung

Während einer vollständigen Neusynchronisierung wird der Fortschritt verfolgt und standardmäßig alle 30 Sekunden protokolliert. Im Folgenden finden Sie einen Beispiel-Protokolleintrag.

```json
{
   "feed": "prices",
   "operation": "full sync",
   "status": "Progress: 2/5, processed: 200, synced: 100",
   "elapsed": "00:00:00 190 ms",
   "pid": "12824",
   "caller": "bin/magento saas:resync --feed=products"
}
```

In diesem Beispiel geben die `status` Informationen zum Synchronisierungsvorgang an:

- **`"Progress 2/5"`** zeigt an, dass zwei von fünf Iterationen abgeschlossen wurden. Die Anzahl der Iterationen hängt von der Anzahl der exportierten Entitäten ab.
- **`"processed: 200"`** gibt an, dass 200 Elemente verarbeitet wurden.
- **`"synced: 100"`** gibt an, dass 100 Artikel an SaaS gesendet wurden. Es wird erwartet, dass `"synced"` nicht gleich `"processed"` ist. Beispiel:
   - **`"synced" < "processed"`** bedeutet, dass die Feed-Tabelle im Vergleich zur zuvor synchronisierten Version keine Änderungen am Element erkannt hat. Solche Elemente werden beim Synchronisierungsvorgang ignoriert.
   - **`"synced" > "processed"`** dieselbe Entitäts-ID (z. B. `Product ID`) kann mehrere Werte in verschiedenen Bereichen haben. Beispielsweise kann ein Produkt fünf Websites zugewiesen werden. In diesem Fall sind möglicherweise „1 verarbeitetes“ Element und „5 synchronisierte“ Elemente vorhanden.

+++ **Beispiel: Vollständiges Resynchronisierungsprotokoll für den Preis-Feed**

```
Price feed full resync:

[2024-03-05T21:00:51.754687+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Initialize","elapsed":"383 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.803178+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Creating batch table `catalog_data_exporter_product_prices_index_batches`. Start position: 30515","elapsed":"434 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.851878+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Batch table `catalog_data_exporter_product_prices_index_batches` created. Total Items: 500, batches: ~1","elapsed":"482 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.852548+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"start processing `500` items in `1` threads with `500` batch size","elapsed":"483 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:52.288369+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 0","elapsed":"919 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.994249+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 100","elapsed":"00:00:02 625 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.995168+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Complete","elapsed":"00:00:02 626 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
```

+++

## Anzeigen und Fehlerbehebung in Protokollen mit New Relic

Wenn Sie Adobe Commerce-Protokolle in der New Relic speichern, können Sie Parsing-Regeln hinzufügen, um die Lesbarkeit und das Abfrageerlebnis zu verbessern.

1. Melden Sie sich bei New Relic an.

1. Gehe zu `Logs => Parsing`.

1. Klicken Sie auf `Create parsing rule`.

1. Konfigurieren Sie die Parsing-Regel, indem Sie die folgenden Werte hinzufügen.

   - **Filtern von Protokollen basierend auf NRQL**

     `filePath LIKE '%commerce-data-export%.log'`

   - **Parser-Regel**

     `\[%{DATA:timestamp}\] report.%{DATA:logLevel}: %{GREEDYDATA:feed:json}`

In diesem Beispiel wird eine Regel hinzugefügt, mit der Sie New Relic-Protokolle nach Feed-Typ, Vorgang usw. abfragen können.

**Beispiel-Abfragezeichenfolge**—`feed.feed:"products" and feed.status:"Complete"`

## Fehlerbehebung

Wenn Daten in Commerce Services fehlen oder falsch sind, überprüfen Sie die Protokolle auf Meldungen zu Fehlern, die während der Synchronisierung von Adobe Commerce mit der Commerce Services-Plattform aufgetreten sind. Verwenden Sie bei Bedarf die erweiterte Protokollierung, um den Protokollen zusätzliche Informationen zur Fehlerbehebung hinzuzufügen.

- Das Datenexportfehlerprotokoll (`commerce-data-export-errors.log`) erfasst Fehler, die während der Erfassungsphase auftreten.
- Das SaaS-Exportfehlerprotokoll (`saas-export-errors.log`) erfasst Fehler, die während der Übertragungsphase auftreten.

Wenn Sie Fehler sehen, die nicht mit der Konfiguration oder Erweiterungen von Drittanbietern in Zusammenhang stehen, senden Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) mit so vielen Informationen wie möglich.

### Beheben von Katalogsynchronisierungsproblemen {#resolvesync}

Beim Trigger einer erneuten Synchronisierung von Daten kann es bis zu einer Stunde dauern, bis die Daten aktualisiert sind und in Benutzeroberflächenkomponenten wie Live-Suche und Empfehlungseinheiten angezeigt werden. Wenn weiterhin Diskrepanzen zwischen Ihrem Katalog und den Daten in der Commerce-Storefront auftreten oder die Katalogsynchronisierung fehlgeschlagen ist, gehen Sie wie folgt vor:

#### Datendiskrepanz

1. Zeigt die detaillierte Ansicht des betreffenden Produkts in den Suchergebnissen an.
1. Kopieren Sie die JSON-Ausgabe und überprüfen Sie, ob der Inhalt mit dem übereinstimmt, was Sie im [!DNL Commerce] Katalog haben.
1. Wenn der Inhalt nicht übereinstimmt, nehmen Sie eine geringfügige Änderung am Produkt in Ihrem Katalog vor, z. B. das Hinzufügen eines Leerzeichens oder eines Punkts.
1. Warten Sie auf eine erneute Synchronisierung oder auf einen [Trigger eine manuelle Neusynchronisierung](#resync).

#### Synchronisierung läuft nicht

Wenn die Synchronisierung nicht nach einem Zeitplan ausgeführt wird oder nichts synchronisiert wird, lesen Sie diesen [KnowledgeBase](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce)Artikel.

#### Synchronisierung fehlgeschlagen

Wenn der Status der Katalogsynchronisierung &quot;**&quot; lautet** senden Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).

## Erweiterte Protokollierung

Verwenden Sie Umgebungsvariablen, um Protokolle mit zusätzlichen Daten für Tracking und Fehlerbehebung zu erweitern. Fügen Sie die Umgebungsvariable der Befehlszeile hinzu, wenn Sie Datenexport-CLI-Befehle ausführen, wie in den folgenden Beispielen gezeigt.

### Überprüfen der Feed-Payload

Schließen Sie die Feed-Payload in das SaaS-Exportprotokoll ein, indem Sie die `EXPORTER_EXTENDED_LOG=1` Umgebungsvariable hinzufügen, wenn Sie den Feed neu synchronisieren.

```shell script
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products
```

Nach Abschluss des Vorgangs kann die Feed-Payload im SaaS-Exportprotokoll (`var/.log/saas-export.log`) überprüft werden.

### Payload in Feed-Indextabelle beibehalten

Für die Commerce SaaS-Datenexporterweiterung (`magento/module-data-exporter`) 103.3.0 und höher behalten sofortige Export-Feeds nur die erforderlichen Mindestdaten in der Indextabelle bei. Die Feeds umfassen alle Feeds für den Katalog- und Bestandsstatus.

Die Beibehaltung von Payload-Daten in der Indextabelle wird in Produktionsumgebungen nicht empfohlen, kann aber in einer Entwicklungsumgebung nützlich sein. Schließen Sie die Feed-Payload in den Index ein, indem Sie die `PERSIST_EXPORTED_FEED=1` Umgebungsvariable hinzufügen, wenn Sie den Feed neu synchronisieren.

```shell script
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

### Ausführen des Profilers zur Fehlerbehebung bei langsamer Leistung

Wenn der Neuindizierungsprozess eines bestimmten Feeds unangemessen lange dauert, führen Sie den Profiler aus, um zusätzliche Daten zu erfassen, die für das Support-Team nützlich sein können.

Führen Sie den Profiler aus, indem Sie beim Ausführen des Befehls „reindex“ die `EXPORTER_PROFILER=1` Umgebungsvariable hinzufügen.

```
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Profildaten werden im Datenexportprotokoll (`var/log/commerce-data-export.log`) in folgendem Format gespeichert:

```
<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>
```
