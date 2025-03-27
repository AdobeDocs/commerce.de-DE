---
title: Regeln hinzufügen
description: Erfahren Sie, wie Sie Merchandising-Suchregeln erstellen.
exl-id: 7175ccf7-d838-43b0-a176-957e7db040e0
source-git-commit: 449b281e46d16de56f4c3d2e01e7165c59ee78a2
workflow-type: tm+mt
source-wordcount: '1650'
ht-degree: 0%

---

# Regeln hinzufügen

Um eine Regel zu erstellen, müssen Sie zunächst mit dem Regeleditor die Bedingungen im Abfragetext des Käufers definieren, unter denen die zugehörigen Ereignisse Trigger werden. Füllen Sie dann die Regeldetails aus, testen Sie die Ergebnisse und veröffentlichen Sie die Regel.

## Regel hinzufügen

1. Gehen Sie im Admin zu **Marketing** > SEO &amp; Search > **[!DNL Live Search]**.
1. Legen Sie den **Bereich** fest, um die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) zu identifizieren, für die die Regel gilt.
1. Klicken Sie auf den **Merchandising suchen**-Arbeitsbereich.
1. Klicken Sie **Regel hinzufügen**, um den Regeleditor zu starten.

## Regeltyp

Bei einer Suchanfrage definieren Sie einen bestimmten Suchbegriff, Bedingungen und Ranking-Typen.

Es kann eine Standardregel festgelegt werden, die auf alle Abfragen angewendet wird, es sei denn, es wird eine spezifischere Suchanfrage definiert. Es kann nur eine Standardregel festgelegt werden, die keine Bedingungen enthalten kann. Wenn Sie Standard auswählen, wird die Bedingungsschnittstelle nicht angezeigt.
Wählen Sie den standardmäßigen Intelligent Ranking-Typ und alle manuellen Rankings aus, die auf alle Standardsuchen angewendet werden sollen. Manuelle Rankings werden immer angewendet.

## Bedingungen

Bedingungen sind die Voraussetzungen für den Trigger eines Ereignisses. Eine Regel kann bis zu zehn Bedingungen und 25 Ereignisse enthalten. Eine Standardregel darf keine Bedingungen enthalten.

![Regel - Regel erstellen](assets/rules-add-workspace.png)

>[!NOTE]
>
>Derzeit ist es nicht möglich, Regeln auf eine bestimmte Kundengruppe auszurichten.

### Einzel-Bedingung

1. Wählen *unter „Regel erstellen* die **Bedingung** aus und befolgen Sie die Anweisungen, um die Anweisung abzuschließen.

   * Suchanfrage enthält : Geben Sie die Textzeichenfolge ein, die in der Abfrage des Erstkäufers enthalten sein muss. Die Einstellung Übereinstimmung bestimmt das Ausmaß, in dem die Abfrage des Käufers mit dem Katalog übereinstimmt. Optionen: <br /> Beliebig - Jeder Teil des Abfragetextes des Käufers kann mit der Bedingung übereinstimmen.<br />Alle - Die Abfrage des Käufers muss der Bedingung entsprechen.
   * Suchabfrage ist - Geben Sie eine Textzeichenfolge ein, die genau mit der Abfrage des Erstkäufers übereinstimmt. Zum Beispiel: „Yogahose“. Regeln mit den `All` &quot;`Search query is`&quot; und „Übereinstimmung“ können nur eine Bedingung haben.
   * Suchabfrage beginnt mit : Geben Sie ein Zeichen oder eine Zeichenfolge ein, die am Anfang der Abfrage des Erstkäufers stehen muss.
   * Suchabfrage endet mit : Geben Sie ein Zeichen oder eine Zeichenfolge ein, die am Ende der Abfrage des Erstkäufers stehen muss.

   Die Ergebnisse werden sofort im Bereich *Regel testen* angezeigt und nach Priorität nummeriert. Sie können den Schieberegler *Ergebnisse pro Zeile* im oberen Bereich verwenden    Berechtigung zur Änderung der Anzahl der Produkte in jeder Zeile.

   ![Regel - einfach](assets/rule-simple-test.png)

1. Um andere Abfragen zu testen, ändern Sie den Abfragetext im Suchfeld *Regel testen* und drücken Sie **Return**.
Zunächst rendert der Testbereich die Abfrage aus dem Suchfeld Bedingungen . Jetzt wird die Abfrage jedoch aus dem Feld Testabfrage gerendert. Im Testbereich wird jeweils nur eine Abfrage gerendert.
1. Wenn Ihnen das Ergebnis gefällt, aktualisieren Sie den Text im Suchfeld *Bedingungen* . Klicken Sie dann auf eine beliebige Stelle auf der Seite, um die Ergebnisse im Testbereich zu aktualisieren.
1. Um eine einfache Regel mit einer Bedingung zu erstellen, gehen Sie zu Schritt 3: [Ereignisse hinzufügen](#events).

### Mehrere Bedingungen

1. Um eine Regel mit mehreren Bedingungen zu erstellen, klicken Sie auf **Bedingung hinzufügen**.
Eine Regel kann bis zu zehn Bedingungen enthalten. Der logische Operator, der zwei Bedingungen verknüpft, basiert auf der aktuellen Einstellung *Übereinstimmung*. Standardmäßig ist *Match* `All` und der logische Operator ist `AND`.

1. Wählen Sie die zweite Bedingung aus und geben Sie den erforderlichen Abfragetext ein.

1. Um die Logik der Regel zu ändern, ändern Sie die Einstellung **Übereinstimmung**, um zu bestimmen, wie genau die Suchkriterien des Käufers mit der Abfragebedingung übereinstimmen müssen. Legen **Match** auf eine der folgenden Einstellungen fest:

   * Beliebig - (Standard) Alle logischen Operatoren in der Regel sind auf `OR` festgelegt, und die Ergebnisse werden im Testbereich angezeigt.
   * Alle - Alle logischen Operatoren in der Regel sind auf `AND` festgelegt, und die Ergebnisse werden im Testbereich angezeigt.

   Der *Match*-Wert bestimmt den logischen Operator, der zum Verbinden mehrerer Bedingungen verwendet wird. Durch Ändern der *Übereinstimmung*-Einstellung werden alle logischen Operatoren in der Regel geändert. `AND` und `OR` können nicht in derselben Regel kombiniert werden.

   In diesem Beispiel gibt es zwei separate Abfragen, die nach „Yoga“ oder „Hose“ suchen, anstatt nach „Yoga-Hose“ zu suchen. Diese Regel ist weniger spezifisch und wird häufiger in der Storefront ausgelöst als in der anderen.

   ![Regeln - Übereinstimmung](assets/rules-match.png)

1. Um eine weitere Bedingung hinzuzufügen, klicken Sie auf **Bedingung hinzufügen** und wiederholen Sie den Vorgang.

## Intelligente Rangfolge

Intelligente Rangfolge kombiniert Benutzerverhalten und Website-Statistiken, um das Produkt-Ranking zu bestimmen.
Store-Inhaber können die folgenden Arten von Rangfolgestrategien einrichten:

![Regeln - Übereinstimmung](assets/rules-ranking-type.png)

* Am häufigsten gekauft: Hierbei werden Produkte nach Gesamteinkäufen pro SKU in den letzten 7 Tagen sortiert.
* Am häufigsten zum Warenkorb hinzugefügt - Ordnet die Aktivitäten „Zum Warenkorb hinzufügen“ in den letzten 7 Tagen der Reihe nach zu.
* Am häufigsten angezeigt: Sortiert die Gesamtzahl der Ansichten pro SKU in den letzten 7 Tagen.
* Empfohlen für Sie - Verwendet den `viewed-viewed` Datenpunkt - Käufer, die diese SKU angesehen haben, haben sich auch diese anderen SKUs angesehen.
* Trends: Blicken Sie auf die Seitenansichtsereignisse der letzten 72 Stunden für Hintergrundereignisse und 24 Stunden für Vordergrundereignisse zurück.
* Keine: Die Produkte werden nach Relevanz sortiert.

Wählen Sie den Strategietyp für die Regel aus. Das Fenster **Regel testen** zeigt die erwarteten Ergebnisse an.

### Einschränkungen

* Apostrophe und Anführungszeichen in Abfragen können zu einigen kleineren Problemen mit Rangfolge und Relevanz in einigen Sprachen führen.
* Um sicherzustellen, dass das intelligente Ranking ordnungsgemäß funktioniert, stellen Sie sicher, dass **Suchgewichtung** für alle Produktattribute, die für die Suche oder Filterung (Facetten) verwendet werden, `5` oder kleiner ist. So finden Sie diese Einstellung im [!DNL Commerce] Admin:

   1. Wählen Sie **Stores** > _Attribute_ > **product** aus.
   1. Suchen Sie nach dem Attribut, z. B. „name“.
   1. Legen Sie auf der **Attributinformationen** > **Storefront-Eigenschaften** die Suchgewichtung auf kleiner oder gleich `5` fest.

      ![Produkt - Suchgewichtung](assets/set-search-weight.png)

## Manuelle Rangfolge

Manuelles Ranking (früher als „Ereignisse“ bezeichnet) sind Aktionen, die die Suchergebnisse ändern, wenn definierte Bedingungen erfüllt sind. Eine einzelne Regel kann bis zu 25 Ereignisse enthalten.

* Verstärken - Verschiebt ein Produkt in den Suchergebnissen nach oben.
* Beerdigen - Verschiebt eine SKU in den Suchergebnissen nach unten.
* Produkt anheften - Das Produkt wird an der ausgewählten „Position“ auf der Seite angezeigt.
* Produkt ausblenden - Schließt eine SKU aus den Suchergebnissen aus.

Die einfachste Möglichkeit, ein Produkt anzuheften, besteht darin, es per Drag-and-Drop zu ziehen.

1. Klicken und ziehen Sie ein Produkt in den Testbereich. Ziehen Sie sie per Drag-and-Drop an die gewünschte Position. Die Felder Produkt und Position werden automatisch im Bereich Ereignisse ausgefüllt.

   ![Regeln - Übereinstimmung](assets/rule-event-pin-product.png)

Sie können auch auf das Anheften-Symbol klicken, um ein Produkt an seinen aktuellen Speicherort anzuheften. Verwenden Sie das Kontextmenü mit den Auslassungspunkten, um „Nach oben“ oder „Nach unten“ anzuheften.

>[!NOTE]
>
>Sie können nur Produkte anheften, die in der Abfrage zurückgegeben werden.

Oder Ereignisse können manuell festgelegt werden:

1. Wählen *unter* die Option **Ereignis** aus, die ausgeführt werden soll, wenn die zugehörigen Bedingungen erfüllt sind.

   Wählen Sie beispielsweise `Hide a product`. Geben Sie dann den Namen des Produkts ein, das Sie ausblenden möchten. Produkte werden bei der Eingabe vorgeschlagen.

1. Wählen Sie für mehrere Ereignisse alle anderen Ereignisse aus, die Sie bei Erfüllung der Bedingungen als Trigger festlegen möchten.

## Zusätzliche Details

Die hier eingegebenen Informationen werden im Bedienfeld [Regeldetails](rules-workspace.md) angezeigt.

1. Geben *unter* einen **Namen** für die Regel ein. Alle Regelnamen müssen eindeutig sein.
1. Geben Sie eine kurze **Beschreibung** der Regel ein.
1. Geben Sie **Startdatum** und **Enddatum** ein, damit die Regel aktiv ist, oder wählen Sie die Datumsangaben aus dem Kalender aus.

   Um einen Datumsbereich auszuwählen, klicken Sie auf das erste Datum und ziehen Sie, um den Bereich auszuwählen.

   ![Regel - Abgeschlossen](assets/rule-add-details.png)

## Regel abschließen

1. Untersuchen Sie die Ergebnisse der Regel im Testbereich.
1. Wenn die Regel mehrere Abfragen umfasst, testen Sie jede, die von der Regel betroffen sein könnte.
1. Klicken Sie abschließend auf **Speichern und**.

   Die Regel wird der Liste im Arbeitsbereich *Regeln* hinzugefügt.

1. Obwohl aktive Regeln sofort in Kraft treten, müssen Sie möglicherweise bis zu 15 Minuten warten, bis die zwischengespeicherten Abfrageergebnisse in der Storefront aktualisiert werden.

>[!NOTE]
>
>Regeln und manuell sortierte Produkte werden auf die Suchergebnisse angewendet, wenn die standardmäßige Sortierreihenfolge „Sortieren nach: Am relevantesten“ ausgewählt ist. Wenn ein Käufer die Sortierreihenfolge ändert, sodass sie etwa nach Name oder Preis sortiert wird, sind Regeln und manuelle Rankings nicht mehr wirksam.

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
