---
title: Feed-Lock-Mechanismus für SaaS-Datenexport
description: Erfahren Sie [!DNL SaaS Data Export]  wie -Feed-Sperren verwendet, um widersprüchliche Synchronisierungsvorgänge zu verhindern und die Datenintegrität während gleichzeitiger Feed-Aktualisierungen zu schützen.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
feature: Services
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 355
ht-degree: 0%

---


# Feed-Lock-Mechanismus für SaaS-Datenexport

Die [!DNL SaaS Data Export]-Erweiterung verwendet einen Feed-Sperrmechanismus, um Race-Bedingungen zu verhindern, wenn mehrere Prozesse versuchen, denselben Feed gleichzeitig zu synchronisieren. Dies kann beispielsweise vorkommen, wenn sich eine durch Cron ausgelöste Resynchronisation mit einem manuellen `saas:resync` CLI-Aufruf überschneidet.

## Funktionsweise der Vorschubsperre

Jeder Feed-Synchronisierungsvorgang - unabhängig davon, ob er durch einen Cron-Auftrag oder einen manuellen `saas:resync`-CLI-Aufruf ausgelöst wird - folgt derselben Sequenz:

1. Der Prozess versucht, die Vorschubsperre zu erhalten. Der Sperrversuch ist nicht blockierend und wird sofort zurückgegeben, wenn die Sperre bereits von einem anderen Prozess gehalten wird.
1. Wenn die Sperre **nicht verfügbar** wird der Vorgang übersprungen und protokolliert.

   Es gehen keine Daten verloren. Der nächste Cron-Durchgang erfasst ausstehende Änderungen, nachdem der aktuelle Prozess abgeschlossen ist.
1. Wenn die Sperre **erworben** wird, zeichnet der Prozess ihren Namen und ihre PID zu Diagnosezwecken auf und führt dann die Synchronisierung aus.
1. Wenn die Synchronisierung abgeschlossen wird oder fehlschlägt, wird die Sperre bedingungslos aufgehoben, sodass der nächste geplante Cron-Auftrag normal fortgesetzt werden kann.

Die Feed-Sperre kann immer nur von einem Synchronisierungsvorgang gehalten werden, unabhängig davon, ob dieser von Cron oder der CLI gestartet wurde. Die Feed-Sperre wird über die `LockManagerInterface` von [!DNL Adobe Commerce] implementiert. Das Standard-Backend ist MySQL, das `GET_LOCK`- und `RELEASE_LOCK` verwendet. Informationen zum Konfigurieren eines anderen Sperranbieters finden Sie unter [Konfigurieren des Sperranbieters](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/lock-provider){target="_blank"}.

## Erwartete Protokollmeldungen

Die folgende Meldung in `commerce-data-export.log` ist normal und weist nicht auf ein Problem hin:

```json
{"feed":"products","operation":"partial sync","status":"operation skipped - process locked by \"full sync(1234)\"", ...}
```

Diese Meldung wird angezeigt, wenn eine durch Cron ausgelöste partielle Synchronisierung versucht, ausgeführt zu werden, während bereits eine vollständige Neuindizierung oder `saas:resync` ausgeführt wird. Der übersprungene Vorgang geht nicht verloren. Sobald der laufende Prozess abgeschlossen ist und die Sperre aufhebt, erfasst und synchronisiert die nächste Cron-Ausführung alle ausstehenden Änderungen.

>[!NOTE]
>
>Allgemeine Informationen zu Protokollformaten und Vorgangstypen, die in `commerce-data-export.log` aufgezeichnet wurden, finden Sie unter [Überprüfen von Protokollen und Fehlerbehebung](troubleshooting/logging.md).

>[!MORELIKETHIS]
>
> - [Synchronisieren von Daten mit dem SaaS-Datenexport](sync-overview.md)
> - [Synchronisieren Sie Feeds mithilfe der Commerce-CLI](data-export-cli-commands.md)
> - [Connector-Synchronisierungs-Pipeline](../aco-connector/connector-sync-pipeline.md)
> - [Konfigurieren des Sperranbieters](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/lock-provider){target="_blank"}
