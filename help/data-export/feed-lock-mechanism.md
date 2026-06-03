---
title: Feed-Lock-Mechanismus für SaaS-Datenexport
description: Erfahren Sie [!DNL SaaS Data Export]  wie -Feed-Sperren verwendet, um widersprüchliche Synchronisierungsvorgänge zu verhindern und die Datenintegrität während gleichzeitiger Feed-Aktualisierungen zu schützen.
role: Admin, Developer
feature: Services
source-git-commit: cfa1002653bf66afd3f6b8484b33076adcd1b7d4
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---


# Feed-Lock-Mechanismus für SaaS-Datenexport

Die [!DNL SaaS Data Export]-Erweiterung verwendet einen Feed-Sperrmechanismus, um Race-Bedingungen zu verhindern, wenn mehrere Prozesse versuchen, denselben Feed gleichzeitig zu synchronisieren. Dies kann beispielsweise vorkommen, wenn sich eine durch Cron ausgelöste Resynchronisation mit einem manuellen `saas:resync` CLI-Aufruf überschneidet.

## Funktionsweise der Vorschubsperre

Jeder Feed-Synchronisierungsvorgang - unabhängig davon, ob er durch einen Cron-Auftrag oder einen manuellen `saas:resync`-CLI-Aufruf ausgelöst wird - folgt derselben Sequenz:

1. Der Prozess versucht, die Vorschubsperre zu erhalten. Der Sperrversuch ist nicht blockierend und wird sofort zurückgegeben, wenn die Sperre bereits von einem anderen Prozess gehalten wird.
1. Wenn die Sperre **nicht verfügbar** ist, wird [Vorgang übersprungen und protokolliert].

   Es gehen keine Daten verloren. Der nächste Cron-Durchgang erfasst ausstehende Änderungen, nachdem der aktuelle Prozess abgeschlossen ist.
1. Wenn die Sperre **erworben** wird, zeichnet der Prozess ihren Namen und ihre PID zu Diagnosezwecken auf und führt dann die Synchronisierung aus.
1. Wenn die Synchronisierung abgeschlossen wird oder fehlschlägt, wird die Sperre bedingungslos aufgehoben, sodass der nächste geplante Cron-Auftrag normal fortgesetzt werden kann.

Die Feed-Sperre kann immer nur von einem Synchronisierungsvorgang gehalten werden, unabhängig davon, ob dieser von Cron oder der CLI gestartet wurde. Die Feed-Sperre wird über die `LockManagerInterface` von [!DNL Adobe Commerce] implementiert. Das Standard-Backend ist MySQL, das `GET_LOCK`- und `RELEASE_LOCK` verwendet. Informationen zum Konfigurieren eines anderen Sperranbieters finden Sie unter [Konfigurieren des Sperranbieters](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/lock-provider){target="_blank"}.

## Erwartete Protokollmeldungen

Die folgende Meldung in `commerce-data-export.log` ist normal und weist nicht auf ein Problem hin:

```json
{"feed":"products","operation":"partial sync","status":"operation skipped - process locked by \"full sync(1234)\"", ...}
```

Diese Meldung wird angezeigt, wenn eine durch Cron ausgelöste partielle Synchronisierung versucht, ausgeführt zu werden, während bereits eine vollständige Neuindizierung oder `saas:resync` ausgeführt wird. Der übersprungene Vorgang geht nicht verloren. Sobald der laufende Prozess abgeschlossen ist und die Sperre aufhebt, erfasst und synchronisiert die nächste Cron-Ausführung alle ausstehenden Änderungen.

>[!NOTE]
>
>Allgemeine Informationen zu Protokollformaten und Vorgangstypen, die in `commerce-data-export.log` aufgezeichnet wurden, finden Sie unter [Überprüfen von Protokollen und Fehlerbehebung](troubleshooting-logging.md).

## Weitere Hilfe zu diesem Thema

- [Synchronisieren von Daten mit dem SaaS-Datenexport](data-synchronization.md)
- [Synchronisieren von Feeds mit der Commerce-CLI](data-export-cli-commands.md)
- [Konfigurieren des Sperranbieters](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/lock-provider){target="_blank"}
