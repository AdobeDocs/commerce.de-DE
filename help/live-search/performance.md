---
title: Leistung
description: Der  [!DNL Live Search] -Performance-Arbeitsbereich bietet insight zu den Suchbegriffen, die Käufer verwenden.
exl-id: 07a63df8-b981-4913-841a-7e81ec634281
source-git-commit: 5978a400d985e3099962af8bcefdd6f29f687d67
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# Leistung

Der *Performance*-Arbeitsbereich bietet insight zu den Suchbegriffen, die Käufer verwenden. Die Informationen können verwendet werden, um Trends zu identifizieren, den Clickthrough zu erhöhen und die Konversionsrate zu verbessern. Der Arbeitsbereich Leistung bietet eine Momentaufnahme der Suchmetriken für einen bestimmten Datumsbereich und umfasst die folgenden Berichte:

* Eindeutige Suchvorgänge
* Keine Ergebnisse
* Beliebte Ergebnisse

![Leistung](assets/performance-unique-searches.png)

Weitere Informationen zur Datensynchronisation finden [ auch im ](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html)Daten-Management-Dashboard).

>[!NOTE]
>
>Der Leistungsarbeitsbereich wird alle 12 Stunden aktualisiert.

## Anzeigen eines Berichts

1. Um den **Datumsbereich“**, klicken Sie auf den Kalender ![Kalender](assets/btn-calendar.png) und führen Sie einen der folgenden Schritte aus:

   * Um ein einzelnes Datum anzugeben, doppelklicken Sie auf das Datum im Kalender.
   * Um einen Datumsbereich anzugeben, klicken Sie auf das erste und letzte Datum im Kalender.

>[!NOTE]
>
>Der Datumsbereich darf ein Jahr nicht überschreiten.

## Feldbeschreibungen

| Momentaufnahmen-Daten | Beschreibung | Berechnungsbeispiel |
|--- |--- |--- |
| Eindeutige Suchvorgänge | Die Gesamtzahl der eindeutigen Suchvorgänge für den angegebenen Datumsbereich. Mehrere Suchvorgänge desselben Kunden, selbst wenn sie für dieselbe Abfrage durchgeführt werden, gelten als eindeutig, wenn sie im Abstand von mehr als einer Stunde eingereicht werden. | **Beispiel:**<br /> Suchen:<br />- „pants“ at 10:00 AM<br />- „pants“ at 10:30 AM (within 1 hour → not unique)<br />- „pants“ at 12:00 PM (after 1 hour → unique)<br />- „shirt“ at 1:00 PM <br /><br />**Total unique searches = 3** |
| Clickthrough-Rate | Der Prozentsatz der Suchvorgänge, die damit enden, dass der Einkäufer auf ein Produkt klickt. Die Clickthrough-Rate beträgt zum Beispiel 50 %, wenn der Käufer nach „pants“ und „shirt“ sucht und dann auf ein Ergebnis in der „shirt“-Suche klickt. | **Formel:**<br /> Klickrate = Suchvorgänge mit ≥1 Klick ÷ Eindeutige Suchvorgänge insgesamt <br /><br />**Beispiel:**<br /> Eindeutige Suchvorgänge insgesamt = 4<br />Suchvorgänge mit mindestens einem Klick = 2<br /><br />CTR = 2 ÷ 4 = **50%** |
| Konversionsrate | Der Prozentsatz der Produkte, die der Einkäufer kauft, im Vergleich zur Anzahl der Produkte, auf die der Einkäufer für den angegebenen Datumsbereich klickt. Beispielsweise liegt die Konversionsrate der Interaktion bei 100 %, wenn der Käufer sechs Produkte im Popover anzeigt, auf eines klickt und einen Kauf tätigt. <br /><br />Die Konversionsrate wird durch die Anzahl der Ansichten eines bestimmten Produkts nicht beeinflusst. Beispielsweise bleibt die Konversionsrate gleich, wenn der Käufer die Suche verwendet, aber nicht auf Produkte klickt. | **Formel:**<br /> Konversionsrate = Insgesamt gekaufte Produkte ÷ Insgesamt angeklickte Produkte <br /><br />**Beispiel 1:**<br /> Angeklickte Produkte = 5<br />Gekaufte Produkte = 2<br /><br />CVR = 2 ÷ 5 = **40%**<br /><br />**Beispiel 2 (5-Stunden-Aggregation):**<br /> Klicks nach Stunde: 4, 5, 6, 10, 2<br />Käufe nach Stunde: 1, 3, 0, 4, 1<br /><br />Gesamte Klicks = 4 + 5 + 6 + 10 + 2 = 27<br />Gesamtkäufe = 1 + 3 + 0 + 4 + 4 + 1 = 9<br /><br />9 ÷ 27 = **33,33 %** |
| Rate der Nullergebnisse | Der Prozentsatz der eindeutigen Suchvorgänge, die für den angegebenen Datumsbereich keine Ergebnisse zurückgeben. Beispielsweise liegt die Null-Ergebnisrate bei 66,67 %, wenn der Käufer zweimal (ohne Ergebnisse) nach „fjjajfjfjf“ und einmal (mit Ergebnissen) nach „pants“ sucht. | **Formel:**<br /> Null-Ergebnisrate = Eindeutige Suchvorgänge mit null Ergebnissen ÷ Eindeutige Suchvorgänge insgesamt <br /><br />**Beispiel:**<br /> Eindeutige Suchvorgänge insgesamt = 3<br />Suchvorgänge mit null Ergebnissen = 2<br /><br />Null-Ergebnisrate = 2 ÷ 3 = **66,67%** |
| Durchschnitt Klick-Position | Die relative Position der durchschnittlichen Klickrate auf der Grundlage eindeutiger Suchvorgänge für den angegebenen Datumsbereich. | **Formel:**<br /> Durchschnittliche Klickposition = Summe der Klickpositionen ÷ Klicks insgesamt <br /><br />**Beispiel:**<br /> Klicks an Positionen: 1, 3, 2<br /><br />Durchschnittliche Klickposition = (1 + 3 + 2) ÷ 3 = **2** |

| Berichte | Beschreibung |
|--- |--- |
| Eindeutige Suchvorgänge | Listet die eindeutigen Suchanfragen auf, die im angegebenen Datumsbereich verwendet wurden. Die Berichtsdaten werden auf die gleiche Weise berechnet wie die Daten eindeutiger Such-Momentaufnahmen. Wenn ein Käufer dieselbe Suchanfrage zweimal, aber im Abstand von mehr als einer Stunde eingibt, wird die Suche als zwei eindeutige Suchvorgänge betrachtet. <br />**Berichtslimit:** Die 500 wichtigsten Begriffe beim Generieren der CSV-Datei. |
| Keine Ergebnisse | Listet die Suchabfragen auf, die keine Ergebnisse zurückgeben, und gibt an, wie oft im angegebenen Datumsbereich verwendet wurde. <br />**Berichtslimit:** Die 500 wichtigsten Begriffe beim Generieren der CSV-Datei. |
| Beliebte Ergebnisse | Listet die Namen von Produkten auf, die im angegebenen Datumsbereich die meisten Ansichten erhalten haben. Beliebte Ergebnisse werden nur auf der Grundlage von Impressions berechnet und sind von der Anzahl der Klicks oder des generierten Umsatzes nicht betroffen. <br />**Berichtslimit:** Die 500 wichtigsten Begriffe beim Generieren der CSV-Datei. |
