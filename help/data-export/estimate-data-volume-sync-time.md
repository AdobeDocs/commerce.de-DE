---
title: Schätzen des Datenvolumens und der Übertragungszeit
description: Erfahren Sie, wie Sie das Datenvolumen und die Übertragungszeit schätzen, die für das  [!DNL data export] -Tool zum Synchronisieren von Feed-Daten zwischen Adobe Commerce und Connected Services erforderlich sind.
role: Admin, Developer
exl-id: 787d05d6-fc2f-4f23-8ea7-ef54330e1f37
source-git-commit: 86f7473e994348d81c0a8f71548bb7a8d3923a21
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Schätzen des Datenvolumens und der Übertragungszeit für die Datensynchronisation

Adobe empfiehlt, das Datenvolumen und die Synchronisierungszeit zu schätzen, bevor Sie eine Daten-Feed-Synchronisierung starten, um eine reibungslose Planung sicherzustellen und Unterbrechungen im Site-Betrieb zu vermeiden. Diese Schätzung ist wichtig bei der Planung von anfänglichen Synchronisationen oder umfangreichen Katalogaktualisierungen, z. B. Massenpreisänderungen.

Standardmäßig verarbeitet das Datenexporttool Daten im Einzelthreadmodus mit einer standardmäßigen Batch-Größe. Bei der Standardkonfiguration gibt es keine Parallelisierung des Feed-Übermittlungsprozesses. Darüber hinaus akzeptiert diese Komponente Anfragen pro Sekunde (RPS), was Folgendes bedeutet:

- Bis zu 10.000 Produkte pro Minute, bei denen ein Produkt eine SKU mit Attributen in einer bestimmten Storeview ist
- Bis zu 50.000 Preise pro Minute

Die folgenden Faktoren beeinflussen die Datenübertragungszeit während der Synchronisierung.

- Die Thread-Anzahl ist auf 1 festgelegt (standardmäßig)
- Die Batch-Größe wird für alle Feeds auf _100_ festgelegt, mit Ausnahme des `prices` Feeds, für den sie auf _500_ festgelegt ist.
- Die Feed-Akzeptanzrate beträgt 2 Anfragen pro Sekunde.
- Alle Produkte sind allen bestehenden Websites zugeordnet
- Für die Preiskalkulationsszenarien sind allen Produkten Sonderpreise und Gruppenpreise zugeordnet


## Datenübertragung pro Feed berechnen

Verwenden Sie die Werte und Formeln in der folgenden Tabelle, um das Datenvolumen und die Synchronisierungszeit für jeden Daten-Feed zu berechnen.

>[!NOTE]
>
>Diese Berechnungen basieren auf einer Übertragungsrate von 2 Anfragen pro Sekunde. Die Geschwindigkeit basiert auf der Zeit, die für die Datenerfassung und Datenübermittlung erforderlich ist. Die tatsächliche Übertragungsgeschwindigkeit hängt von der Größe der Anfrage-Payload und der aktuellen Last auf dem Commerce-Anwendungsserver ab.

| Futter | Datenbeispiel | Formel zur Berechnung der Datensätze | Vorhergesagte Anfragenanzahl | Prognostizierte Resynchronisationszeit |
| --- | --- | --- | --- | --- |
| PRODUCT | Produkte (P): 10000, Shop-Ansichten (SV): 4 | P * SV = 40000 | 40000/Batch-Größe (100) = 400 Anfragen | (400 Anfragen * 0,5 Sekunden pro Anfrage) / 60 = 3,3 Minuten |
| Kategorien | Kategorien (C): 500, Shop-Ansichten (SV): 4 | C * SV = 2000 | 2000 / Batch-Größe (100) = 20 Anfragen | (20 Anfragen * 0,5 Sekunden pro Anfrage) / 60 = 0,1 Minuten (4 Sekunden) |
| Preise | Produkte (P): 10000, Kundengruppen (CG): 6 (zum Beispiel eindeutiger Preis im freigegebenen Katalog), Websites (WS): 2 | P \* WS * CG = 120000 | 120000/Batch-Größe (500) = 240 Anfragen | (240 Anfragen * 0,5 Sekunden pro Anfrage) / 60 = 2 Minuten |
| Produktüberschreibungen | Produkte mit Berechtigungen oder im freigegebenen Katalog (P): 10000, Betroffene Kundengruppen (CG): 5, Zugewiesene Websites WS: 2 | P \* WS * CG = 100000 | 100000 / Batch-Größe (100) = 1000 Anfragen | (1000 Anfragen * 0,5 Sekunden pro Anfrage) / 60 = 8,3 Minuten |
| Produktvarianten | Varianten (untergeordnete Produkte), die konfigurierbaren Produkten (PV) zugewiesen sind: 100000 | PV = 100000 | 100000 / Batch-Größe (100) = 1000 Anfragen | (1000 Anfragen * 0,5 Sekunden pro Anfrage) / 60 = 8,3 Minuten |
| Kategorieberechtigungen | Anzahl aller Kategorieberechtigungen + 4 Fallback-Datensätze (CP): 10000 | CP = 10000 | 10000/Batch-Größe (100) = 100 Anfragen | (100 Anfragen * 0,5 Sekunden pro Anfrage) / 60 = 0,8 Minuten (50 Sekunden) |
| Lagerbestand | Produkte (P): 10000, Lager Produkte zugeordnet zu (S): 5 (vorausgesetzt, jedes Produkt ist jedem Lager zugeordnet) | P * S = 50000 | 50000/Batch-Größe (100) = 500 Anfragen | (500 Anfragen * 0,5 Sekunden pro Anfrage) / 60 = 4,2 Minuten |
| Kundenaufträge | Alle Auftragsdatensätze (einschließlich Rechnungen, Lieferungen usw.): 10000 | SO = 10000 | 10000/Batch-Größe (100) = 100 Anfragen | (100 Anfragen * 0,5 Sekunden pro Anfrage) / 60 = 0,8 Minuten (50 Sekunden) |
