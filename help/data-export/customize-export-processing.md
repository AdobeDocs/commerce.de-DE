---
title: Verbessern der SaaS-Datenexportleistung
description: Erfahren Sie, wie Sie die SaaS-Datenexportleistung für Commerce Services mithilfe des Multithread-Datenexportmodus verbessern können.
role: Admin, Developer
exl-id: 7151118c-5e30-44d0-b515-5801a73e44ec
source-git-commit: b8b7af1119163589b7d83654b13edae656fea339
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Verbessern der SaaS-Datenexportleistung

**Multi-Thread-Datenexportmodus** Beschleunigt den Exportvorgang, indem Feed-Daten in Batches aufgeteilt und parallel verarbeitet werden.

Entwickler oder Systemintegratoren können die Leistung verbessern, indem sie den Multithread-Datenexportmodus anstelle des standardmäßigen Einzelthread-Modus verwenden. Im Single-Thread-Modus gibt es keine Parallelisierung des Feed-Übermittlungsprozesses. Darüber hinaus sind aufgrund der standardmäßig festgelegten Beschränkungen alle Clients auf die Verwendung nur eines Threads beschränkt. In den meisten Fällen ist keine Anpassung der Konfiguration erforderlich.

## Überlegungen zur Verwendung des Multi-Thread-Modus

Beim Arbeiten mit Datenexportdiensten ist es wichtig, die Leistung zu optimieren und gleichzeitig eine genaue Synchronisierung sicherzustellen.
Adobe empfiehlt die Verwendung der Standardkonfiguration für die Datenaufnahme, die in der Regel die Synchronisierungsanforderungen für Commerce-Händler erfüllt. Es gibt jedoch Szenarien, in denen die Anpassung die Verarbeitungszeit beschleunigen kann.

Beachten Sie bei der Entscheidung, ob die Datenexportkonfiguration angepasst werden soll, die folgenden Schlüsselfaktoren:

- **Erstsynchronisierung**-Bewerten Sie die Anzahl der Produkte und [schätzen Sie das Datenvolumen und die Übertragungszeit](estimate-data-volume-sync-time.md) basierend auf der Standardkonfiguration. Fragen Sie sich: Können Sie nach der Einführung in einen Commerce-Service auf diese erste Datensynchronisation warten?

- **Hinzufügen neuer Store-Ansichten oder Websites**-Wenn Sie nach der Live-Schaltung Shop-Ansichten oder Websites mit derselben Produktanzahl hinzufügen möchten, schätzen Sie das Datenvolumen und die Übertragungszeit. Stellen Sie fest, ob die Synchronisierungszeit mit der Standardkonfiguration akzeptabel ist oder ob eine Verarbeitung mit mehreren Threads erforderlich ist.

- **Reguläre Importe:** Sie regelmäßige Importe voraus, z. B. Preisaktualisierungen oder Änderungen des Lagerstatus. Beurteilen, ob diese Aktualisierungen innerhalb eines akzeptablen Zeitraums angewendet werden können oder ob eine schnellere Verarbeitung erforderlich ist.

- **Produktgewicht** - Überlegen Sie, ob Ihre Produkte leicht oder schwer sind. Passen Sie die Stapelgröße entsprechend an, wenn die Produktbeschreibungen oder Attribute die Produktgröße erhöhen.

Denken Sie daran, dass eine sorgfältige Planung, einschließlich der Schätzung des Datenvolumens und der Synchronisierungszeit, oft die Notwendigkeit einer Anpassung eliminiert. Planen Sie die Feed-Aufnahme-Vorgänge basierend auf diesen Schätzungen, um optimale Ergebnisse zu erzielen.

>[!NOTE]
>
>Adobe empfiehlt, bei der Verwendung der Verarbeitung mehrerer Threads Vorsicht walten zu lassen. Wenn Sie Multi-Threading für eine schnellere Leistung konfigurieren, können Sie die enthaltenen Trigger Adobe Commerce Services-Leitplanken verwenden, um einen Missbrauch des Systems bei der Datenaufnahme zu verhindern. Diese Leitplanken verhindern auch, dass Benutzer Synchronisierungsänderungen auslösen, die das System überlasten können. Wenn die Leitplanken ausgelöst werden, werden -Anfragen blockiert und das System gibt 429 Fehler zurück. Wenn diese Fehler auftreten, passen Sie Ihre Konfiguration an und senden Sie ein Support-Ticket, um Hilfe zu erhalten.

## Multithreading konfigurieren

Der Multi-Thread-Modus wird für alle [Synchronisierungsmethoden](data-synchronization.md#synchronization-process) - Vollsynchronisierung, Teilsynchronisierung und Synchronisierung fehlgeschlagener Elemente unterstützt. Um Multithreading zu konfigurieren, geben Sie die Anzahl der Threads und die Batch-Größe an, die während der Synchronisierung verwendet werden sollen.

- `thread-count` ist die Anzahl der Threads, die für die Verarbeitung von Entitäten aktiviert werden. Der `thread-count` lautet `1`.
- `batch-size` ist die Anzahl der Entitäten, die in einer Iteration verarbeitet werden. Der `batch-size` ist `100` Datensätze für alle Feeds mit Ausnahme des Preis-Feeds. Für den Preis-Feed ist der Standardwert `500` Datensätze.

Sie können Multi-Threading als temporäre Option konfigurieren, wenn Sie einen Resynchronisierungsbefehl ausführen, oder indem Sie die Multi-Thread-Konfiguration zur Adobe Commerce-Anwendungskonfiguration hinzufügen.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie die Leistung des SaaS-Datenexports an das Ratenlimit ausrichten, das für einen Client auf Verbraucherseite definiert ist.

### Konfigurieren von Multithreading zur Laufzeit

Wenn Sie einen vollständigen Synchronisierungsbefehl über die Befehlszeile ausführen, geben Sie die Multi-Thread-Verarbeitung an, indem Sie die `thread-count`- und `batch-size` zum CLI-Befehl hinzufügen.

```
bin/magento saas:resync --feed=products --thread-count=2 --batch-size=200
```

In der Befehlszeile angegebene Optionen überschreiben die in der `config.php` der Adobe Commerce-Anwendung angegebene Datenexportkonfiguration.

### Hinzufügen von Multi-Threading zur Commerce-Konfiguration

Um alle Datenexportvorgänge mit Multithreading zu verarbeiten, können Systemintegratoren oder Entwickler die Anzahl der Threads und die Batch-Größe für jeden Feed in der Commerce-Anwendungskonfiguration ändern.

Diese Änderungen können angewendet werden, indem benutzerdefinierte Werte zum [Systemabschnitt](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/files/config-reference-configphp#system) der Konfigurationsdatei hinzugefügt werden, `app/etc/config.php`.

**Beispiel: Multithreading für Produkte und Preise konfigurieren**

```php
<?php
return [
    'system' => [
        'default' => [
            'commerce_data_export' => [
                'feeds' => [
                    'products' => [
                        'batch_size' => 100,
                        'thread_count' => 2,
                    ],
                    'prices' => [
                        'batch_size' => 400,
                        'thread_count' => 4,
                    ]
                ]
            ],
//   ...
```
