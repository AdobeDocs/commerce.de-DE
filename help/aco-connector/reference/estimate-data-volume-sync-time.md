---
title: Schätzen des Datenvolumens und der Synchronisierungszeit
description: Erfahren Sie, wie Sie das Datenvolumen und die Synchronisierungszeit für Feeds  [!DNL Adobe Commerce Optimizer Connector] , um Katalogsynchronisierungen zu planen und Unterbrechungen zu vermeiden.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7id: c32adafa-ed01-4b31-997e-2413013911b0
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 469
ht-degree: 0%

---


# Schätzen des Datenvolumens und der Synchronisierungszeit

Adobe empfiehlt, das Datenvolumen und die Synchronisierungszeit zu schätzen, bevor eine Feed-Synchronisierung gestartet wird, um eine reibungslose Planung sicherzustellen und Unterbrechungen im Site-Betrieb zu vermeiden. Dies ist besonders wichtig bei der Planung von anfänglichen Synchronisationen oder umfangreichen Katalogaktualisierungen, wie z. B. Massenpreisänderungen.

Standardmäßig verarbeitet der Connector -Feeds im Einzelthread-Modus. Es gibt keine Parallelisierung des Feed-Übermittlungsprozesses. Die Aufnahme-API akzeptiert bis zu 2 Anfragen pro Sekunde. Die Basiszuweisung für die [!DNL Adobe Commerce Optimizer]-Aufnahmerate begrenzt jedoch den Durchsatz auf Folgendes:

- Bis zu 1.000 Produkte pro Minute (ein Produkt ist eine SKU mit Attributen in einer bestimmten Store-Ansicht). Siehe [Beschränkungen und Grenzen](../../optimizer/boundaries-limits.md) für Details zur Basiszuweisung.
- Bis zu 50.000 Preise pro Minute

## Faktoren, die sich auf die Synchronisierungszeit auswirken

Die folgenden Schätzungen gehen von folgenden Bedingungen aus:

- Thread-Anzahl: 1 (Standard)
- Feed-Akzeptanzrate: 2 Anfragen pro Sekunde (0,5 Sekunden pro Anfrage)
- Alle Produkte sind allen bestehenden Websites zugeordnet

Die tatsächliche Übertragungsgeschwindigkeit hängt von der Größe der Anfrage-Payload und der aktuellen Last auf dem Commerce-Anwendungsserver ab.

## Synchronisierungszeit pro Feed berechnen

Verwenden Sie die folgende Tabelle, um die Anzahl der Datensätze, Anfragen und die Synchronisierungszeit für jeden Connector-Feed zu schätzen. Die Werte der Batch-Größe entsprechen den in der Referenz [Unterstützte Feeds](connector-reference.md#supported-feeds) definierten Beschränkungen.

>[!NOTE]
>
>Die Produktsynchronisierungszeit basiert auf dem Basiszuweisungslimit von 1.000 Produkten pro Minute. Bei anderen Feeds basieren die Berechnungen auf einer Übertragungsrate von 2 Anfragen pro Sekunde. Die tatsächliche Geschwindigkeit hängt von der Payload-Größe und der Server-Last ab.
>
>Die Preisschätzung geht davon aus, dass alle Kundengruppen über individuelle Preise verfügen.

| Futter | Datenbeispiel | Formel | Prognostizierte Anforderungen | Voraussichtliche Synchronisierungszeit |
| ---- | ------------ | ------- | ------------------ | ------------------- |
| PRODUCT | Produkte (P): 10.000, Shop-Ansichten (SV): 4 | P × SV = 40.000 Datensätze | 40.000 ÷ Stapelgröße (100) = 400 | 40.000 ÷ 1.000 Datensätze/min = **40 min** |
| Kategorien | Kategorien (C): 500, Shop-Ansichten (SV): 4 | C × SV = 2.000 Datensätze | 2.000 ÷ Stapelgröße (100) = 20 | (20 × 0,5 s) ÷ 60 = **~10 s** |
| Produktattribute | Attribute (A): 200, Store-Ansichten (SV): 4 | A × SV = 800 Datensätze | 800 ÷ Stapelgröße (100) = 8 | (8 × 0,5 s) ÷ 60 = **~4 s** |
| Preise | Produkte (P): 10.000, Websites (WS): 2, Kundengruppen (CG): 6 | P × WS × CG = 120.000 Datensätze | 120.000 ÷ Stapelgröße (500) = 240 | (240 × 0,5 s) ÷ 60 = **2 min** |
| Preisbücher | Websites (WS): 2, Kundengruppen (CG): 6 | WS × CG = 12 Datensätze | 12 ÷ Stapelgröße (500) = 1 | (1 × 0,5 s) ÷ 60 = **&lt; 1 s** |

>[!MORELIKETHIS]
>
> - [Connector-Module und Feed-](connector-reference.md): Überprüfen Sie Batch-Beschränkungen und unterstützte Feeds
> - [Synchronisierung verwalten](../data-sync-manage.md) - Überwachen des Synchronisierungsstatus und manuelle Neusynchronisierung des Triggers
> - [Connector-Synchronisations-Pipeline](../connector-sync-pipeline.md) - Erfahren Sie, wie Cron-Zeitpläne und automatisierte Synchronisierung funktionieren
