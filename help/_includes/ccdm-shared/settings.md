---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%
---
Verwenden Sie den Arbeitsbereich *Einstellungen*, um die Suche und Produktsuche für Ihre Storefront zu konfigurieren. Die folgenden Registerkarten sind verfügbar:

- **Facetten** - Konfigurieren Sie Preisbereichsgruppen und -intervalle, die als Suchfilter verwendet werden.
- **Language** - Legt die Katalogsprache für die Indizierung und Suche fest.
- **Erweiterte Suche** - Aktivieren Sie die semantische Suche und die Fuzzy-Suche und passen Sie Schwellenwerte für semantische Steigerung und Ähnlichkeit an.

## Zugriff auf den Arbeitsbereich Einstellungen

Wie Sie den Arbeitsbereich *Einstellungen* öffnen, hängt vom verwendeten Produkt ab:

- **Adobe Commerce Admin** (Adobe Commerce as a Cloud Service) - Wählen Sie *Merchandising* > **Merchandising-Einstellungen** aus.
- **Adobe Commerce Optimizer Studio**—Wählen Sie *Merchandising* > **Einstellungen**.

>[!BEGINTABS]

>[!TAB Preisfacetten]

## Preisfacetten {#price-facets}

Sie können die Anzahl der Preisbereichsgruppen und die Verteilung der Preiswerte untereinander angeben. Jede Preisspanne überschneidet sich mit der vorherigen Gruppe um eins. Beispielsweise erstellen fünf Gruppen mit einem Intervall von 20 Preisspannen: 0-20, 20-40, 40-60, 60-80 und >80. Wenn nicht genügend Produkte im Katalog vorhanden sind, um alle definierten Bereiche zu füllen, wird die Anzeige der verfügbaren Gruppen entsprechend angepasst. Beispiel: 0-20, 60-80, >80.

**So konfigurieren Sie Preisfacetten:**

1. Wählen Sie im **Einstellungen** die Option **[!UICONTROL Facets]** aus.
1. Gehen Sie **Abschnitt** Preisfacette“ wie folgt vor:
   - Geben Sie die **[!UICONTROL Number of selections]** oder Preisgruppen ein, die verfügbar sein sollen. Es können bis zu 100 Preisgruppen definiert werden.
   - Geben Sie für jede Gruppe den **[!UICONTROL Interval value]** oder die Preisspanne ein. Der maximale Wert ist 40.000.000.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Es dauert etwa 15 Minuten, bis die aktualisierten Einstellungen in der Storefront verfügbar sind.

### Beschreibung der Preisfacettenfelder

| Feld | Beschreibung |
| --- | --- |
| Anzahl der Auswahlen | Gibt die Anzahl der Preisbereichsgruppierungen an, die als Suchfilter in der Storefront verwendet werden können. Standardwert: 8, Höchstwert: 100 |
| Intervallwert | Gibt das Preisintervall für jede Gruppe an. Beispielsweise ergeben fünf Auswahlen mit einem Intervallwert von 20 Gruppierungen von 0-20, 20-40, 40-60, 60-80 und >80. Standardwert: 5, Höchstwert: 40.000.000 |

>[!TAB language]

## Sprache {#language}

Die Spracheinstellung gibt dem System an, welche Sprache beim Lesen des Katalogs und Schreiben des Index erwartet wird.

Sprachen haben unterschiedliche Grammatikregeln: wie Wörter getrennt werden, Verbformen und Wortformen zum Beispiel.
Die Spracheinstellung stellt sicher, dass der richtige Regelsatz auf den Indizierungsmechanismus angewendet wird.

Legen Sie die Spracheinstellung auf die primäre Sprache des Katalogs fest. Je nach Kataloggröße und -komplexität dauert es 5 bis 60 Minuten, bis die Indexsprache geändert wird.

| Sprache | Code |
|----|----|
| Arabisch | AR |
| Armenisch | hy |
| Baskisch | EU |
| Bengalisch | Bn |
| Brasilianisch | pt-br |
| Bulgarisch | BG |
| Katalanisch | CA |
| Chinesisch (vereinfacht) | zh-CN |
| Chinesisch (traditionell) | zh-tw |
| Tschechisch | CS |
| Dänisch | DA |
| Niederländisch | NL |
| Englisch | de |
| Estnisch | et |
| Finnisch | FI |
| Französisch | fr |
| Galizisch | GL |
| Deutsch | de |
| Griechisch | EL |
| Hindi | Hallo |
| Ungarisch | HU |
| Indonesisch | ID |
| Irisch | GA |
| Italienisch | IT |
| Japanisch (Katakana) | JA |
| Koreanisch | KO |
| Lettisch | LV |
| Litauisch | LT |
| Norwegisch | Nein |
| Persisch | Fa |
| Portugiesisch | Punkt |
| Rumänisch | oder |
| Russisch | ru |
| Sorani | ku |
| Spanisch | es |
| Schwedisch | SV |
| Türkisch | tr |
| Thailändisch | th |

>[!TAB Erweiterte Suche]

## Erweiterte Suche {#advanced-search}

Verwenden Sie die Registerkarte **[!UICONTROL Advanced search]** , um die Suche an einer Stelle zu verwalten. Das System bietet ein einheitliches Sucherlebnis in der Storefront. Sie konfigurieren keine Keyword-Suche und semantische Suche separat für Kunden. **[!UICONTROL Enable semantic search]** ist **standardmäßig aktiviert** für geeignete englische Kataloge. Die semantische Suche funktioniert neben Ihrer vorhandenen Konfiguration. [Merchandising-](./merchandising/rules/overview.md)), [Synonyme](./merchandising/synonyms/overview.md), [Facetten](./merchandising/facets/overview.md), Verstärkungen und Filter gelten weiterhin. Das System verwendet vordefinierte Katalogattribute automatisch - Attribute in den Einstellungen werden nicht ausgewählt oder priorisiert. Es sind keine Änderungen an der Storefront oder am Entwickler erforderlich.

![Erweiterte Sucheinstellungen](/help/assets/ccdm-shared/advanced-search.png)

**So verwalten Sie die semantische Suche:**

1. Wählen Sie im **Einstellungen** die Registerkarte **[!UICONTROL Advanced search]** aus.
1. Bestätigen Sie unter **[!UICONTROL Enable semantic search]**, dass die semantische Suche aktiviert ist, oder deaktivieren Sie diese, wenn Sie keine semantische Übereinstimmung wünschen.
1. Klicken Sie auf **[!UICONTROL Save]** , wenn Sie die Umschalt- oder Abstimmsteuerelemente ändern.

   Aktualisierung der Suchergebnisse nach Abschluss der Indizierung. Bei einem mittelgroßen Katalog kann die Indizierung bis zu 30 Minuten dauern. Bei großen Katalogen mit Millionen von Produkten kann es ein paar Stunden dauern.

### Optionale Optimierung

Nachdem die semantische Suche aktiviert ist, können Sie Folgendes auf derselben Registerkarte anpassen:

- **[!UICONTROL Semantic boost]** - Um semantisch relevante Ergebnisse in der Rangfolge zu priorisieren, sollten Sie einen Schub anwenden. Erhöhen Sie den Wert, wenn semantische Übereinstimmungen in der Ergebnismenge eine größere Gewichtung haben sollen, und senken Sie ihn, wenn die Ergebnisse zu umfangreich sind.
- **[!UICONTROL Similarity threshold]** () - Legt den minimalen Ähnlichkeitswert (als Prozentsatz) für eine semantische Übereinstimmung fest. Niedrigere Werte geben mehr Ergebnisse zurück (höhere Rückrufaktion), können aber schwächere Übereinstimmungen enthalten. Höhere Werte geben weniger, engere Übereinstimmungen zurück (höhere Genauigkeit).
- **[!UICONTROL Fuzzy search]**: Um Übereinstimmungen mit Suchabfragen zu finden und Tippfehler und kleinere Varianten zu korrigieren, aktivieren **die**.
- **[!UICONTROL Fuzzy search similarity threshold]** () - Legen Sie die minimale Ähnlichkeit (in Prozent) fest, die erforderlich ist, damit Fuzzy Matches angezeigt werden. Niedrigere Schwellenwerte geben ungefährere Übereinstimmungen zurück. Erhöhen Sie den Schwellenwert, wenn sich unscharfe Ergebnisse zu weit anfühlen.

>[!NOTE]
>
> Die semantische Suche wird nur für Kataloge **Englisch** unterstützt. Wenn Sie auf der Registerkarte **[!UICONTROL Language]** eine andere Sprache auswählen, wird die **[!UICONTROL Enable semantic search]** deaktiviert.

Zu den Vorteilen, Anleitungen zur Validierung, Best Practices, Fehlerbehebung und Einschränkungen finden Sie unter [Semantische Suche](/help/optimizer/setup/semantic-search.md).

### Erweiterte Suchfeldbeschreibungen

| Kontrolle | Beschreibung |
| --- | --- |
| Semantische Suche aktivieren | Wenn diese Option aktiviert ist, verwendet die Suche neben der Keyword-Übereinstimmung auch die Bedeutung und den Kontext. Vordefinierte Katalogattribute werden automatisch verwendet. In den Einstellungen ist keine Attributeinrichtung erforderlich. Standardmäßig aktiviert. |
| Semantischer Schub | Verstärken zur Priorisierung semantisch relevanter Ergebnisse im Ranking. |
| Ähnlichkeitsschwelle | Minimaler Ähnlichkeitswert (Prozentsatz) für eine semantische Übereinstimmung. Niedrigere Werte begünstigen Rückruf, höhere Werte Präzision. |
| Ungenaue Suche | Wenn **on**, findet die Suche in der Nähe Übereinstimmungen für Abfragen (z. B. kleinere Varianten). |
| Ähnlichkeitsschwellenwert für unscharfe Suche | Minimale Ähnlichkeit (Prozentsatz) Fuzzy Matches müssen erfüllt sein, damit sie in den Ergebnissen angezeigt werden. |

>[!ENDTABS]
