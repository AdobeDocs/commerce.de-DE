---
title: Regeln erstellen und verwalten
description: Erfahren Sie, wie Sie Merchandising-Regeln erstellen und verwalten.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: fd4df2b2-83de-4c5c-b18c-e97aa07ef8f6
source-git-commit: c6725fc524e9d239ccc0f16701e92ad5d2fc7729
workflow-type: tm+mt
source-wordcount: '2103'
ht-degree: 0%

---

# Regeln erstellen und verwalten

Um eine Regel zu erstellen, müssen Sie zunächst mit dem Regeleditor die Bedingungen im Abfragetext des Käufers definieren, unter denen die zugehörigen Ereignisse Trigger werden. Füllen Sie dann die Regeldetails aus, testen Sie die Ergebnisse und veröffentlichen Sie die Regel.

## Erstellen einer Regel

1. Navigieren Sie in der linken Leiste zu _Merchandising_ > **Merchandising-Regeln**.
1. Klicken Sie **Regel erstellen**, um den Regeleditor zu starten.

![Regel erstellen](../../assets/create-rule.png)

Im **Regel erstellen** definieren Sie bestimmte Suchkriterien, Bedingungen und Ranking-Typen.

1. Geben Sie im Feld **[!UICONTROL Name]** einen Namen für die Regel ein. Alle Regelnamen müssen eindeutig sein.
1. Geben Sie im Feld **[!UICONTROL Description]** eine Beschreibung für die Regel ein.
1. Geben Sie im Feld **[!UICONTROL Date range]** das Datum oder den Datumsbereich an, zu dem die Regel aktiv sein soll.
1. Im Abschnitt **[!UICONTROL Rule applies to]** stehen zwei Optionen zur Verfügung: **[!UICONTROL All product listings]** oder **[!UICONTROL Specific conditions]**.

   - **Alle Produktlisten** - Dies ist im Wesentlichen Ihre Standardregel und wird auf alle Suchabfragen angewendet, es sei denn, es ist eine spezifischere Suchabfrage definiert. Sie können nur eine Standardregel erstellen und sie kann keine Bedingungen enthalten. Wählen Sie den Intelligent-Ranking-Typ und alle manuellen Rankings aus, die auf alle Standardsuchen angewendet werden sollen.
   - **Spezifische Bedingungen** - Im nächsten Abschnitt erfahren Sie mehr über die Bedingungstypen, die Sie für Ihre Regel festlegen können.

### Bedingungen

Bedingungen sind die Voraussetzungen für den Trigger eines Ereignisses. Eine Regel kann bis zu zehn Bedingungen und 25 Ereignisse enthalten. Eine Standardregel darf keine Bedingungen enthalten.

![Regelbedingung auswählen](../../assets/rule-set-condition.png)

#### Einzel-Bedingung

1. Wählen *unter „Regel erstellen* die **Bedingung** aus und befolgen Sie die Anweisungen, um die Anweisung abzuschließen.

   - Suchanfrage enthält : Geben Sie die Textzeichenfolge ein, die in der Abfrage des Erstkäufers enthalten sein muss. Die Einstellung Übereinstimmung bestimmt das Ausmaß, in dem die Abfrage des Käufers mit dem Katalog übereinstimmt. Optionen: <br /> Beliebig - Jeder Teil des Abfragetextes des Käufers kann mit der Bedingung übereinstimmen.<br />Alle - Die Abfrage des Käufers muss der Bedingung entsprechen.
   - Suchabfrage ist - Geben Sie eine Textzeichenfolge ein, die genau mit der Abfrage des Erstkäufers übereinstimmt. Zum Beispiel: „Yogahose“. Regeln mit den `Search query is` &quot;`All`&quot; und „Übereinstimmung“ können nur eine Bedingung haben.
   - Suchabfrage beginnt mit : Geben Sie ein Zeichen oder eine Zeichenfolge ein, die am Anfang der Abfrage des Erstkäufers stehen muss.
   - Suchabfrage endet mit : Geben Sie ein Zeichen oder eine Zeichenfolge ein, die am Ende der Abfrage des Erstkäufers stehen muss.

   Die Ergebnisse werden sofort im Bereich *Regel testen* angezeigt und nach Priorität nummeriert. Mit dem Schieberegler *Ergebnisse pro Zeile* oben rechts können Sie die Anzahl der Produkte in jeder Zeile ändern.

1. Um andere Abfragen zu testen, ändern Sie den Abfragetext im Suchfeld *Regel testen* und drücken Sie **Return**.
Zunächst rendert der Testbereich die Abfrage aus dem Suchfeld Bedingungen . Jetzt wird die Abfrage jedoch aus dem Feld Testabfrage gerendert. Im Testbereich wird jeweils nur eine Abfrage gerendert.
1. Wenn Ihnen das Ergebnis gefällt, aktualisieren Sie den Text im Suchfeld *Bedingungen* . Klicken Sie dann auf eine beliebige Stelle auf der Seite, um die Ergebnisse im Testbereich zu aktualisieren.

#### Mehrere Bedingungen

1. Um eine Regel mit mehreren Bedingungen zu erstellen, klicken Sie auf **Bedingung hinzufügen**.
Eine Regel kann bis zu zehn Bedingungen enthalten. Der logische Operator, der zwei Bedingungen verknüpft, basiert auf der aktuellen Einstellung *Übereinstimmung*. Standardmäßig ist *Match* `All` und der logische Operator ist `AND`.

1. Wählen Sie die zweite Bedingung aus und geben Sie den erforderlichen Abfragetext ein.

1. Um die Logik der Regel zu ändern, ändern Sie die Einstellung **Übereinstimmung**, um zu bestimmen, wie genau die Suchkriterien des Käufers mit der Abfragebedingung übereinstimmen müssen. Legen **Match** auf eine der folgenden Einstellungen fest:

   - Beliebig - (Standard) Alle logischen Operatoren in der Regel sind auf `OR` festgelegt, und die Ergebnisse werden im Testbereich angezeigt.
   - Alle - Alle logischen Operatoren in der Regel sind auf `AND` festgelegt, und die Ergebnisse werden im Testbereich angezeigt.

   Der *Match*-Wert bestimmt den logischen Operator, der zum Verbinden mehrerer Bedingungen verwendet wird. Durch Ändern der *Übereinstimmung*-Einstellung werden alle logischen Operatoren in der Regel geändert. `AND` und `OR` können nicht in derselben Regel kombiniert werden.

   In diesem Beispiel gibt es zwei separate Abfragen, die nach „Yoga“ oder „Hose“ suchen, anstatt nach „Yoga-Hose“ zu suchen. Diese Regel ist weniger spezifisch und wird häufiger in der Storefront ausgelöst als in der anderen.

1. Um eine weitere Bedingung hinzuzufügen, klicken Sie auf **Bedingung hinzufügen** und wiederholen Sie den Vorgang.

### Intelligente Rangfolge

Intelligente Rangfolge kombiniert Benutzerverhalten und Website-Statistiken, um das Produkt-Ranking zu bestimmen.
Store-Inhaber können die folgenden Arten von Rangfolgestrategien einrichten:

![Intelligente Rangfolgen](../../assets/rule-intelligent-ranking.png)

- Am häufigsten gekauft: Hierbei werden Produkte nach Gesamteinkäufen pro SKU in den letzten 7 Tagen sortiert.
- Am häufigsten zum Warenkorb hinzugefügt - Ordnet die Aktivitäten „Zum Warenkorb hinzufügen“ in den letzten 7 Tagen der Reihe nach zu.
- Am häufigsten angezeigt: Sortiert die Gesamtzahl der Ansichten pro SKU in den letzten 7 Tagen.
- Empfohlen für Sie - Verwendet den `viewed-viewed` Datenpunkt - Käufer, die diese SKU angesehen haben, haben sich auch diese anderen SKUs angesehen.
- Trends: Blicken Sie auf die Seitenansichtsereignisse der letzten 72 Stunden für Hintergrundereignisse und 24 Stunden für Vordergrundereignisse zurück.
- Keine: Die Produkte werden nach Relevanz sortiert.

Wählen Sie den Strategietyp für die Regel aus. Das Fenster **Regel testen** zeigt die erwarteten Ergebnisse an.

#### Funktionsweise der intelligenten Rangfolgenbewertung

Das intelligente Ranking bestimmt die endgültige Produktreihenfolge durch die Kombination zweier Schlüsselfaktoren: **Textrelevanz** und **Verhaltenssignale**. Wenn Sie verstehen, wie diese Faktoren interagieren, können Sie realistische Erwartungen an Ihre Suchergebnisse stellen.

**Bewertungskomponenten:**

- **Textrelevanz**: Der dominante Faktor bei der Bewertung. Dadurch wird gemessen, wie gut der Name, die Beschreibung und die Attribute eines Produkts mit der Suchanfrage übereinstimmen. Die Textrelevanz-Bewertung ist unbegrenzt (hat keine bestimmte Obergrenze) und wird durch Faktoren wie folgende beeinflusst:

   - Häufigkeit des Auftretens von übereinstimmenden Wörtern.
   - Länge (in Worten) der Produktnamen/-beschreibungen.

- **Verhaltenssignale**: Ein begrenzter Verstärker, der zusätzlich zum Textrelevanzwert angewendet wird. Wenn Sie eine intelligente Rangfolgestrategie wie „Am häufigsten angezeigt“ oder „Am häufigsten gekauft“ auswählen, erhalten Produkte mit höheren Verhaltenssignalen eine feste Steigerung ihrer Bewertungen. Dieser Schub hat jedoch eine definierte Grenze.

**Warum das am häufigsten angezeigte Produkt möglicherweise nicht zuerst angezeigt wird:**

Die textliche Relevanz dominiert in der Regel das Ranking, da die Punktzahl unbegrenzt ist, während die Verhaltenssteigerungen fixiert sind. Daher übertreffen Produkte mit starkem Text häufig diejenigen mit höheren Interaktionssignalen. Verhaltenssteigerungen allein können große Lücken in der Textrelevanz möglicherweise nicht ausgleichen. Das intelligente Ranking berücksichtigt dies, indem sowohl die Spielqualität als auch die Kundeninteraktion berücksichtigt werden, was die Gesamtrelevanz verbessert. Die Qualität der Textübereinstimmung bleibt jedoch der primäre Treiber der Rangfolge.

**Beispiel:**

Ein Händler verwendet die „am häufigsten angesehene“ intelligente Rangfolgestrategie und sucht nach „Candle“. Sie erwarten, dass die Produkt-SKU YAN-K-E-512 an der Spitze der Ergebnisse angezeigt wird, da sie die höchste Ansichtsanzahl aufweist. Andere Produkte sind jedoch höher:

- **Texas Candle** (1. Position): Hat einen kürzeren, saubereren Produktnamen, der einen sehr hohen Textrelevanzwert erzeugt. Obwohl es weniger Ansichten als YAN-K-E-512 hat, überwiegt seine überlegene Textübereinstimmung den Verhaltensschub.

- **YAN-K-E-512** (untere Position): Obwohl der Name das höchste Ansichts-Perzentil in den Verhaltensdaten mit dem Status „Am häufigsten angezeigt“ hat, erzeugt sein komplexer, auf SKU basierender Name einen niedrigeren Textrelevanzwert. Der feste Verhaltensschub reicht nicht aus, um diese Lücke in der Textrelevanz zu schließen.

Unter [Suchregeln](./best-practice.md#tips-to-optimize-search-rules) erfahren Sie, wie Sie die Auffindbarkeit von Produkten mithilfe von Regeln verbessern.

#### Einschränkungen

- Apostrophe und Anführungszeichen in Abfragen können zu einigen kleineren Problemen mit Rangfolge und Relevanz in einigen Sprachen führen.
- Um sicherzustellen, dass das intelligente Ranking ordnungsgemäß funktioniert, stellen Sie sicher, dass **Suchgewichtung** für alle Attribute, die für die Suche oder Filterung (Facetten) verwendet werden, `5` oder kleiner ist.

Informationen zum Festlegen der Suchgewichtung finden Sie unter [Metadaten-API](https://developer.adobe.com/commerce/services/reference/rest/).

### Manuelle Rangfolge

**Manuelles Ranking** sind Aktionen, die die Suchergebnisse ändern, wenn definierte Bedingungen erfüllt sind. Eine einzelne Regel kann bis zu 25 Ereignisse enthalten.

- Verstärken - Verschiebt ein Produkt in den Suchergebnissen nach oben.
- Beerdigen - Verschiebt eine SKU in den Suchergebnissen nach unten.
- Produkt anheften - Das Produkt wird an der ausgewählten „Position“ auf der Seite angezeigt.
- Produkt ausblenden - Schließt eine SKU aus den Suchergebnissen aus.

Die einfachste Möglichkeit, ein Produkt anzuheften, besteht darin, es per Drag-and-Drop zu ziehen.

1. Klicken und ziehen Sie ein Produkt in den Testbereich. Ziehen Sie sie per Drag-and-Drop an die gewünschte Position. Die Felder Produkt und Position werden automatisch im Bereich Ereignisse ausgefüllt.

Sie können auch auf das Anheften-Symbol klicken, um ein Produkt an seinen aktuellen Speicherort anzuheften. Verwenden Sie das Kontextmenü mit den Auslassungspunkten, um „Nach oben“ oder „Nach unten“ anzuheften.

>[!NOTE]
>
>Sie können nur Produkte anheften, die in der Abfrage zurückgegeben werden.

Oder Ereignisse können manuell festgelegt werden:

1. Wählen *unter* die Option **Ereignis** aus, die ausgeführt werden soll, wenn die zugehörigen Bedingungen erfüllt sind.

   Wählen Sie beispielsweise `Hide a product`. Geben Sie dann den Namen des Produkts ein, das Sie ausblenden möchten. Produkte werden bei der Eingabe vorgeschlagen.

1. Wählen Sie für mehrere Ereignisse alle anderen Ereignisse aus, die Sie bei Erfüllung der Bedingungen als Trigger festlegen möchten.

### Regel abschließen

1. Untersuchen Sie die Ergebnisse der Regel im Testbereich.
1. Wenn die Regel mehrere Abfragen umfasst, testen Sie jede, die von der Regel betroffen sein könnte.
1. Klicken Sie abschließend auf **Speichern und**.

   Die Regel wird der Liste im Arbeitsbereich *Regeln* hinzugefügt.

1. Obwohl aktive Regeln sofort in Kraft treten, müssen Sie möglicherweise bis zu 15 Minuten warten, bis die zwischengespeicherten Abfrageergebnisse in der Storefront aktualisiert werden.

>[!NOTE]
>
>Regeln und manuell sortierte Produkte werden auf die Suchergebnisse angewendet, wenn die standardmäßige Sortierreihenfolge „Sortieren nach: Am relevantesten“ ausgewählt ist. Wenn ein Käufer die Sortierreihenfolge ändert, sodass sie etwa nach Name oder Preis sortiert wird, sind Regeln und manuelle Rankings nicht mehr wirksam.

## Regeln bearbeiten, anzeigen und löschen

Befolgen Sie diese Anweisungen, um die Eigenschaften vorhandener Regeln zu aktualisieren.

### Regel bearbeiten

1. Suchen Sie im Arbeitsbereich *Merchandising* Regeln“ die Regel in dem Raster, das Sie bearbeiten möchten, und klicken Sie auf **Mehr** (…) Optionen.
1. Klicken Sie **Bearbeiten**, um auf den Regeleditor zuzugreifen.
1. Aktualisieren Sie die Bedingungen, Operatoren und Ereignisse nach Bedarf.
1. Aktualisieren Sie die Felder Name, Start- und Enddatum sowie Beschreibung nach Bedarf. Alle Regelnamen müssen eindeutig sein.
1. Testen Sie die Regel.
1. Veröffentlichen Sie die Änderungen.
Die Regel wird der Liste im Arbeitsbereich *Regeln* hinzugefügt. Obwohl aktive Regeln sofort in Kraft treten, kann es bis zu 15 Minuten dauern, bis zwischengespeicherte Abfrageergebnisse in der Storefront aktualisiert werden.

### Details anzeigen

Diese Option bietet eine schnelle Möglichkeit, alle Regelparameter anzuzeigen, während Sie auf der Tabelle *Regeln* bleiben.

1. Suchen Sie im Arbeitsbereich *Merchandising* Regeln“ die Regel in dem Raster, das Sie bearbeiten möchten, und klicken Sie auf **Mehr** (…) Optionen.
1. Klicken Sie **Details anzeigen**, um die Regelparameter anzuzeigen.
1. Wählen Sie **Bearbeiten** oder **Löschen** oder klicken Sie auf das X, um das Bedienfeld zu schließen.

### Regel löschen

1. Suchen Sie im Arbeitsbereich *Regeln* die Regel in dem Raster, das Sie bearbeiten möchten, und klicken Sie auf **Mehr** (…) Optionen.
1. Klicken Sie **Löschen**.

## Feldbeschreibungen

### Bedingungen (falls)

| Bedingung | Beschreibung |
|--- |--- |
| Suchanfrage enthält | Ein Zeichen oder eine Zeichenfolge, das bzw. die in der Abfrage des Käufers enthalten ist. Die Abfrage des Käufers muss nur einem einzigen Zeichen entsprechen, um diese Bedingung zu erfüllen. |
| Suchabfrage ist | Ein Zeichen oder eine Textzeichenfolge, das bzw. die genau mit der Abfrage des Käufers übereinstimmt. Komplexe Abfragen mit mehreren Bedingungen können nicht erstellt werden, wenn diese Bedingung verwendet wird. |
| Suchanfrage beginnt mit | Die Abfrage des Käufers beginnt mit diesem Zeichen oder dieser Zeichenfolge. |
| Suchanfrage endet mit | Die Abfrage des Käufers endet mit diesem Zeichen oder dieser Zeichenfolge. |

### Logische Operatoren

| Benutzerin oder Benutzer | Beschreibung |
|--- |--- |
| ODER | (Standard) Der logische Operator `OR` vergleicht zwei Bedingungen und erfüllt die Anforderungen für den Trigger eines Ereignisses, wenn mindestens eine Bedingung erfüllt ist. |
| UND | Der logische Operator `AND` vergleicht zwei Bedingungen und erfüllt die Anforderungen für den Trigger eines Ereignisses, wenn beide Bedingungen erfüllt sind. |

### Operatoren abgleichen

| Benutzerin oder Benutzer | Beschreibung |
|--- |--- |
| Beliebig | Ändert alle logischen Operatoren in der Regel in `OR` und gibt den Satz übereinstimmender Produkte zurück. |
| Alle | Ändert alle logischen Operatoren in der Regel in `AND` und gibt den Satz übereinstimmender Produkte zurück. |

### Manuelle Rangfolge

| Ereignis | Beschreibung |
|--- |--- |
| Verstärken | Verschiebt eine SKU oder einen Bereich von SKUs in den Suchergebnissen nach oben. Jedes wird in den Testsuchergebnissen mit einem „erweiterten“ Vorschausymbol gekennzeichnet. |
| begraben | Verschiebt eine SKU oder einen SKU-Bereich in den Suchergebnissen nach unten. Jeder wird in den Testsuchergebnissen mit einem „Buried“-Vorschauabzeichen gekennzeichnet. |
| Produkt anheften | Hängt eine einzelne SKU an eine bestimmte Position in den Suchergebnissen an. Das Produkt ist in den Testsuchergebnissen mit einem „angehefteten“ Vorschauabzeichen gekennzeichnet. |
| Produkt ausblenden | Schließt eine SKU oder einen Bereich von SKUs aus den Suchergebnissen aus. |

### Details

| Feld | Beschreibung |
|--- |--- |
| -Name | Der Name der Regel. Regelnamen müssen eindeutig sein. |
| Regeltyp | Standard oder Abfrage. Der Standardwert wird auf alle Regeln angewendet, es sei denn, es ist eine spezifischere Abfrageregel definiert. |
| Startdatum | Das Startdatum der Regel, falls geplant. |
| Enddatum | Das Enddatum der Regel, falls geplant. |
| Beschreibung | Eine kurze Beschreibung der Regel. |
