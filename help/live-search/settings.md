---
title: Einstellungen
description: Konfigurieren Sie die Einstellungen für den  [!DNL Live Search] .
exl-id: 6387a365-7e23-4023-95ac-27908164d81c
source-git-commit: 70ff444afbe7ddf41e966e479e03975a02f4e10f
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Einstellungen

Verwenden Sie den Arbeitsbereich *Einstellungen*, um die Bereiche und Intervalle für die Preisfacette und die Standardsprache für den Index zu konfigurieren.

Die Preisfacettierung gibt die Anzahl der Preisbereichsgruppen und die Verteilung der Preiswerte untereinander an.

Die Spracheinstellung gibt dem [!DNL Live Search]-Service an, welche Sprache beim Schreiben des Index erwartet wird.

![Einstellungen](assets/settings.png)

## Preisfacettierung

Sie können die Anzahl der Preisbereichsgruppen und die Verteilung der Preiswerte untereinander angeben. Jede Preisspanne überschneidet sich mit der vorherigen Gruppe um eins. Beispielsweise erstellen fünf Gruppen mit einem Intervall von 20 die folgenden Preisbereiche: 0-20, 20-40, 40-60, 60-80 und >80. Wenn nicht genügend Produkte im Katalog vorhanden sind, um alle definierten Bereiche zu füllen, wird die Anzeige der verfügbaren Gruppen entsprechend angepasst. Beispiel: 0-20, 60-80, >80.

1. Gehen Sie im Admin zu **Marketing** > *SEO &amp; Search* > **[!DNL Live Search]**.
1. Gehen Sie im **Einstellungen** unter *Preisfacettierung* wie folgt vor:
   * Geben Sie die **Anzahl der** oder Preisgruppen ein, die verfügbar sein sollen. Mit [!DNL Live Search] 4.4.0 können bis zu 100 Preisgruppen definiert werden. Frühere Versionen erlaubten 50 Preisgruppen.
   * Geben Sie für jede Gruppe **Intervallwert** oder Preisbereich ein. Der maximale Wert ist 40.000.000.
1. Klicken Sie **Speichern**.

   Es dauert etwa 15 Minuten, bis die aktualisierten Einstellungen in der Storefront verfügbar sind.

### Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Anzahl der Auswahlen | Gibt die Anzahl der Preisbereichsgruppierungen an, die als Suchfilter in der Storefront verwendet werden können. Standardwert: 8, Höchstwert: 100 (ab [!DNL Live Search] 4.4.0) |
| Intervallwert | Gibt das Preisintervall für jede Gruppe an. Beispiel: Bei fünf Auswahlen mit einem Intervallwert von 20 werden fünf Gruppierungen von 0-20, 20-40, 40-60, 60-80 und >80 erstellt. Standardwert: 5, Höchstwert: 40.000.000 |

## Sprache

Die Spracheinstellung gibt an, [!DNL Live Search] welche Sprache beim Lesen des Katalogs und Schreiben des Index erwartet wird.

Sprachen haben unterschiedliche Grammatikregeln: wie Wörter getrennt werden, Verbformen und Wortformen zum Beispiel.
Die Spracheinstellung stellt sicher, dass der richtige Regelsatz auf den Indizierungsmechanismus angewendet wird.

Legen Sie die Spracheinstellung auf die primäre Sprache des Katalogs fest. Beim Ändern der Sprache des Index kann es je nach Größe und Komplexität des Katalogs zwischen 5 und 60 Minuten dauern, bis die Änderung an der Storefront widergespiegelt wird.

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
