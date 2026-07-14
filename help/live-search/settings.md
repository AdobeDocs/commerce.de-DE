---
title: Einstellungen
description: Konfigurieren Sie die semantische Suche, die Preisfacettenbereiche und die standardmäßige Indizierungssprache für den  [!DNL Live Search] .
exl-id: 6387a365-7e23-4023-95ac-27908164d81c
TQID: https://experienceleague.adobe.com/Dn4x8Boo-1F5RQgMXVx6Dpt7iYWFIlqOlO5QwhJrjVU
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 1f5246b6f5853f8b53a356ae2d6d58077b07a9a5
workflow-type: tm+mt
source-wordcount: 679
ht-degree: 0%

---

# Einstellungen

Verwenden Sie den **Einstellungen**, um die semantische Suche, die Bereiche und Intervalle der Preisfacetten und die Standardsprache für den Index zu konfigurieren.

![Einstellungen](assets/settings.png)

## Semantische Suche {#semantic-search}

>[!AVAILABILITY]
>
>Die semantische Suche ist für Händler verfügbar, die die Adobe Commerce-Versionen 2.4.4 und höher verwenden.

Die semantische Suche verwendet KI, um Produkte anhand von Bedeutung und Kontext abzugleichen, nicht nur anhand exakter Keywords. Wenn **[!UICONTROL Semantic search]** aktiviert ist, können Käufer, die eine natürliche Sprache oder Formulierung verwenden, die nicht wörtlich mit Ihrem Katalog übereinstimmt, dennoch relevante Produkte finden. [!DNL Live Search] bietet Keyword- und semantische Übereinstimmungen in einem einheitlichen Sucherlebnis auf der Storefront. Die semantische Suche funktioniert neben Ihrer vorhandenen Konfiguration. [Suchregeln](rules.md), [Synonyme](synonyms.md), [Facetten](facets.md), Boosts und [Kategorie-](category-merch.md) gelten weiterhin.

**So aktivieren Sie die semantische Suche (nur PaaS):**

1. Gehen Sie im Admin zu **Marketing** > *SEO &amp; Search* > **[!DNL Live Search]**.
1. Aktivieren Sie im **Einstellungen** die Option **[!UICONTROL Semantic search]**.

   Wenn diese Option aktiviert ist, gleicht die Suche Produkte basierend auf ihrer Bedeutung und ihrem Kontext ab, was zu relevanteren Ergebnissen, weniger Suchvorgängen ohne Ergebnis und verbesserter Konversion führt.

1. Klicken Sie auf **[!UICONTROL Save]**.

   Aktualisierung der Suchergebnisse nach Abschluss der Indizierung. Bei einem mittelgroßen Katalog kann die Indizierung bis zu einer halben Stunde dauern. Bei großen Katalogen mit Millionen von Produkten kann es ein paar Stunden dauern.

>[!NOTE]
>
> Die semantische Suche ist nur für Kataloge **Englisch** verfügbar. Wenn Sie **Language** auf einen nicht englischen Katalog setzen (siehe [Language](#language)), wird **[!UICONTROL Semantic search]** automatisch deaktiviert.

Zu den Vorteilen, Anleitungen zur Validierung, Best Practices, Fehlerbehebung und Einschränkungen finden Sie unter [Semantische Suche](semantic-search.md).

### Feldbeschreibungen

| Feld | Beschreibung |
| --- | --- |
| Semantische Suche | Wenn diese Option aktiviert ist, verwendet [!DNL Live Search] Bedeutung und Kontext neben der Keyword-Zuordnung. Vordefinierte Katalogattribute werden automatisch verwendet. In der Admin ist keine Attributeinrichtung erforderlich. Standardmäßig für [!DNL Adobe Commerce as a Cloud Service] aktiviert; PaaS-Händler aktivieren es manuell. |

## Preisfacettierung {#price-faceting}

Sie können die Anzahl der Preisbereichsgruppen und die Verteilung der Preiswerte untereinander angeben. Jede Preisspanne überschneidet sich mit der vorherigen Gruppe um eins. Beispielsweise erstellen fünf Gruppen mit einem Intervall von 20 die folgenden Preisbereiche: 0-20, 20-40, 40-60, 60-80 und >80. Wenn nicht genügend Produkte im Katalog vorhanden sind, um alle definierten Bereiche zu füllen, wird die Anzeige der verfügbaren Gruppen entsprechend angepasst. Beispiel: 0-20, 60-80, >80.

**So konfigurieren Sie die Preisfacettierung:**

1. Gehen Sie im Admin zu **Marketing** > *SEO &amp; Search* > **[!DNL Live Search]**.
1. Gehen Sie im **Einstellungen** unter *Preisfacettierung* wie folgt vor:
   * Geben Sie die **Anzahl der** oder Preisgruppen ein, die verfügbar sein sollen. Mit [!DNL Live Search] 4.4.0 können bis zu 100 Preisgruppen definiert werden. Frühere Versionen erlaubten 50 Preisgruppen.
   * Geben Sie für jede Gruppe **Intervallwert** oder Preisbereich ein. Der maximale Wert ist 40.000.000.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Es dauert etwa 15 Minuten, bis die aktualisierten Einstellungen in der Storefront verfügbar sind.

### Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Anzahl der Auswahlen | Gibt die Anzahl der Preisbereichsgruppierungen an, die als Suchfilter in der Storefront verwendet werden können. Standardwert: 8, Höchstwert: 100 (ab [!DNL Live Search] 4.4.0) |
| Intervallwert | Gibt das Preisintervall für jede Gruppe an. Beispiel: Bei fünf Auswahlen mit einem Intervallwert von 20 werden fünf Gruppierungen von 0-20, 20-40, 40-60, 60-80 und >80 erstellt. Standardwert: 5, Höchstwert: 40.000.000 |

## Sprache {#language}

Die Spracheinstellung gibt an, [!DNL Live Search] welche Sprache beim Lesen des Katalogs und Schreiben des Index erwartet wird.

Sprachen haben unterschiedliche Grammatikregeln: wie Wörter getrennt werden, Verbformen und Wortformen zum Beispiel.Die Spracheinstellung stellt sicher, dass der richtige Regelsatz auf den Indizierungsmechanismus angewendet wird.

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
