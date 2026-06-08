---
title: Einstellungen
description: Einstellungen konfigurieren für [!DNL Adobe Commerce Optimizer].
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 6ac223de-8e03-4842-8b67-92ce321d323d
TQID: https://experienceleague.adobe.com/9-BMXoWad0bbvsnwgHQrs19ZC9ngGrVE9J7PszcX4Zc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 015f88e540fe5bf7acc4469d7c91b4f606709809
workflow-type: tm+mt
source-wordcount: 867
ht-degree: 0%

---

# Einstellungen

Verwenden Sie den Arbeitsbereich *Einstellungen*, um die Suche und Produktsuche für Ihre Storefront zu konfigurieren. Die folgenden Registerkarten sind verfügbar:

- **Preisfacetten** - Konfigurieren Sie Preisbereichsgruppen und -intervalle, die als Suchfilter verwendet werden.
- **Language** - Legt die Katalogsprache für die Indizierung und Suche fest.
- **Erweiterte Suche** - Aktivieren Sie die semantische Suche und die Fuzzy-Suche und stimmen Sie die Schwellenwerte für semantische Optimierung und Ähnlichkeit ab.

>[!BEGINTABS]

>[!TAB Preisfacetten]

## Preisfacetten {#price-facets}

Sie können die Anzahl der Preisbereichsgruppen und die Verteilung der Preiswerte untereinander angeben. Jede Preisspanne überschneidet sich mit der vorherigen Gruppe um eins. Wenn Sie beispielsweise fünf Gruppen mit einem Intervall von 20 verwenden, erhalten Sie Preisspannen wie 0-20, 20-40, 40-60, 60-80 und >80. Wenn nicht genügend Produkte im Katalog vorhanden sind, um alle definierten Bereiche zu füllen, wird die Anzeige der verfügbaren Gruppen entsprechend angepasst. Beispiel: 0-20, 60-80, >80.

**So konfigurieren Sie Preisfacetten:**

1. Wählen Sie **Arbeitsbereich** Einstellungen“ die Option **[!UICONTROL Facets]** aus.
1. Gehen Sie **Abschnitt** Preisfacette“ wie folgt vor:
   - Geben Sie die **[!UICONTROL Number of selections]** oder Preisgruppen ein, die verfügbar sein sollen. Es können bis zu 100 Preisgruppen definiert werden.
   - Geben Sie für jede Gruppe den **[!UICONTROL Interval value]** oder die Preisspanne ein. Der maximale Wert ist 40.000.000.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Es dauert etwa 15 Minuten, bis die aktualisierten Einstellungen in der Storefront verfügbar sind.

### Feldbeschreibungen

| Feld | Beschreibung |
| --- | --- |
| Anzahl der Auswahlen | Gibt die Anzahl der Preisbereichsgruppierungen an, die als Suchfilter in der Storefront verwendet werden können. Standardwert: 8, Höchstwert: 100 |
| Intervallwert | Gibt das Preisintervall für jede Gruppe an. Beispielsweise ergeben fünf Auswahlen mit einem Intervallwert von 20 Gruppierungen von 0-20, 20-40, 40-60, 60-80 und >80. Standardwert: 5, Höchstwert: 40.000.000 |

>[!TAB language]

## Sprache {#language}

Die Spracheinstellung gibt an, [!DNL Adobe Commerce Optimizer] welche Sprache beim Lesen des Katalogs und Schreiben des Index erwartet wird.

Sprachen haben unterschiedliche Grammatikregeln: wie Wörter getrennt werden, Verbformen und Wortformen zum Beispiel.
Die Spracheinstellung stellt sicher, dass der richtige Regelsatz auf den Indizierungsmechanismus angewendet wird.

Legen Sie die Spracheinstellung auf die primäre Sprache des Katalogs fest. Wenn Sie die Sprache des Index ändern, kann es je nach Größe und Komplexität des Katalogs zwischen 5 und 60 Minuten dauern, bis die Änderung in der Storefront angezeigt wird.

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

Verwenden Sie die Registerkarte **[!UICONTROL Advanced search]** , um die Suche an einer Stelle zu verwalten. [!DNL Adobe Commerce Optimizer] bietet ein einheitliches Sucherlebnis in der Storefront. Sie konfigurieren keine Keyword-Suche und semantische Suche separat für Kunden. **[!UICONTROL Enable semantic search]** ist **standardmäßig aktiviert** für geeignete englische Kataloge. Die semantische Suche funktioniert neben Ihrer vorhandenen Konfiguration. [Merchandising-](./merchandising/rules/overview.md)), [Synonyme](./merchandising/synonyms/overview.md), [Facetten](./merchandising/facets/overview.md), Verstärkungen und Filter gelten weiterhin. Das System verwendet vordefinierte Katalogattribute automatisch, d. h., Sie wählen im Administrator keine Attribute aus bzw. haben keine Priorität für sie. Es sind keine Änderungen an der Storefront oder am Entwickler erforderlich.

![Erweiterte Sucheinstellungen](./assets/advanced-search.png)

**So verwalten Sie die semantische Suche:**

1. Wählen Sie im **Einstellungen** die Registerkarte **[!UICONTROL Advanced search]** aus.
1. Bestätigen Sie unter **[!UICONTROL Enable semantic search]**, dass die semantische Suche aktiviert ist, oder deaktivieren Sie diese, wenn Sie keine semantische Übereinstimmung wünschen.
1. Klicken Sie auf **[!UICONTROL Save]** , wenn Sie die Umschalt- oder Abstimmsteuerelemente ändern.

   Aktualisierung der Suchergebnisse nach Abschluss der Indizierung. Bei einem mittelgroßen Katalog kann die Indizierung bis zu einer halben Stunde dauern. Bei großen Katalogen mit Millionen von Produkten kann es ein paar Stunden dauern.

### Optionale Optimierung

Nachdem die semantische Suche aktiviert ist, können Sie Folgendes auf derselben Registerkarte anpassen:

- **[!UICONTROL Semantic boost]** - Verstärken Sie die Rangfolge, um semantisch relevante Ergebnisse zu priorisieren. Erhöhen Sie den Wert, wenn semantische Übereinstimmungen in der Ergebnismenge eine größere Gewichtung haben sollen, und senken Sie ihn, wenn die Ergebnisse zu umfangreich sind.
- **[!UICONTROL Similarity threshold]** - Legen Sie den minimalen Ähnlichkeitswert (als Prozentsatz) für eine semantische Übereinstimmung fest. Niedrigere Werte geben mehr Ergebnisse zurück (höhere Rückrufaktion), können aber schwächere Übereinstimmungen enthalten. Höhere Werte geben weniger, engere Übereinstimmungen zurück (höhere Genauigkeit).

  >[!NOTE]
  >
  > Die semantische Suche wird nur für Kataloge **Englisch** unterstützt. Wenn Sie auf der Registerkarte **[Sprache](#language)** eine andere Sprache auswählen, wird die **[!UICONTROL Enable semantic search]** deaktiviert.

- **[!UICONTROL Fuzzy search]** — Schalten Sie **ein** um Treffer für Suchabfragen zu finden, was bei der Korrektur von Tippfehlern und kleineren Varianten hilft.
- **[!UICONTROL Fuzzy search similarity threshold]** - Legen Sie die minimale Ähnlichkeit (in Prozent) fest, die erforderlich ist, damit Fuzzy Matches angezeigt werden. Niedrigere Schwellenwerte geben ungefährere Übereinstimmungen zurück. Erhöhen Sie den Schwellenwert, wenn sich unscharfe Ergebnisse zu weit anfühlen.

Zu den Vorteilen, Anleitungen zur Validierung, Best Practices, Fehlerbehebung und Einschränkungen finden Sie unter [Semantische Suche](setup/semantic-search.md).

### Feldbeschreibungen

| Kontrolle | Beschreibung |
| --- | --- |
| Semantische Suche aktivieren | Wenn diese Option aktiviert ist, verwendet die Suche neben der Keyword-Übereinstimmung auch die Bedeutung und den Kontext. Vordefinierte Katalogattribute werden automatisch verwendet. In der Admin ist keine Attributeinrichtung erforderlich. Standardmäßig für [!DNL Adobe Commerce Optimizer] Kunden aktiviert. |
| Semantischer Schub | Verstärken zur Priorisierung semantisch relevanter Ergebnisse im Ranking. |
| Ähnlichkeitsschwelle | Minimaler Ähnlichkeitswert (Prozentsatz) für eine semantische Übereinstimmung. Niedrigere Werte begünstigen Rückruf, höhere Werte Präzision. |
| Ungenaue Suche | Wenn **on**, findet die Suche in der Nähe Übereinstimmungen für Abfragen (z. B. kleinere Varianten). |
| Ähnlichkeitsschwellenwert für unscharfe Suche | Minimale Ähnlichkeit (Prozentsatz) Fuzzy Matches müssen erfüllt sein, damit sie in den Ergebnissen angezeigt werden. |

>[!ENDTABS]
