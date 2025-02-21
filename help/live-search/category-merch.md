---
title: Kategorie-Merchandising
description: Verwenden  [!DNL Live Search]  Kategorie-Merchandising für ein schnelleres Einkaufserlebnis.
gourl: ls_catalog_merchandising
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 0%

---

# Kategorie-Merchandising

Mit dem Kategorie-Merchandising können Store-Besitzer [!DNL Live Search] intelligente [ (Regeln](rules.md) auf Produktkategorien und Unterkategorien anwenden.

Dieses Video ist eine Einführung in das Kategorie-Merchandising.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

Die Funktion ist im Administrator unter **Marketing** > SEO &amp; Search > **[!DNL Live Search]** > (Kategorie **Merchandising** verfügbar.

>[!NOTE]
>
>Kategorie-Merchandising ist ab Version [!DNL Live Search] [.0.0 ](release-notes.md). Wenn Sie die Kategorie Merchandising-Arbeitsbereich sehen, sie jedoch nicht mit Daten gefüllt ist, aktualisieren Sie das [!DNL Live Search].

![Kategorie Merchandising](assets/category_workspace.png)

Die Merchandising-Ansicht „Kategorie“ zeigt definierte Kategorieregeln mit Spalten für:

* Kategorie
* Rangfolgestrategie
* Übernommene Rangfolge
* Zuletzt aktualisiert
* Aktion

Sie können im Feld „Suche nach Kategorie“ nach einer Kategorie oder Unterkategorie suchen.

## Rangfolgestrategien

Kategorie-Merchandising verwendet dieselben Ranking-Typen wie bei [einzelnen Produkten](rules-workspace.md).
Es gibt zwei Arten von Rankings: Intelligent und Manual.

**Intelligent Ranking** nutzt die Verhaltensdatenanalyse der Storefront durch [Adobe Sensei](https://www.adobe.com/sensei.html) um alle Produkte innerhalb ausgewählter Kategorien nach einem bestimmten Algorithmus zu sortieren. Sobald ein Intelligent-Ranking ausgewählt wurde, wird erwartet, dass sich die spezifische Produktreihenfolge im Laufe der Zeit ändert, da die zugrunde liegenden Daten von Adobe Sensei laufend neu analysiert werden. Die beliebtesten Produkte ändern sich beispielsweise automatisch im Laufe der Zeit, wenn sich die Kundenpräferenzen ändern.
Intelligente Ranking-Methoden sind:

* Am häufigsten gekauft: Sortiert Produkte nach der Häufigkeit, mit der sie von Käufern in den letzten sieben Tagen gekauft wurden.
* Am häufigsten zum Warenkorb hinzugefügt: Sortiert Produkte nach der Häufigkeit, mit der sie von Käufern in den letzten sieben Tagen zum Warenkorb hinzugefügt wurden.
* Am häufigsten angezeigt: Sortiert Produkte nach der Häufigkeit, mit der sie von Käufern in den letzten sieben Tagen angezeigt wurden.
* Empfohlen: Anhand des vorherigen und aktuellen Onsite-Verhaltens jedes Käufers werden Produkte nach der Wahrscheinlichkeit geordnet, mit der der Käufer mit jedem Kontakt interagiert.
* Trends: Sortiert Produkte nach den jüngsten Popularitätsaufschwüngen auf der Grundlage von Ansichten.
* Keine: Produkte werden nach ihrer Standardreihenfolge sortiert.

**Manuelles Ranking** Ermöglicht es Benutzern, die automatische Produktsortierreihenfolge durch Definieren von manuellen Pin-, Boost-, Bury- und Hide-Regeln außer Kraft zu setzen.

## Übernommene Rangfolge

Als Merchandiser möchten Sie vielleicht alle Damenbekleidungskategorien nach „Trend“ sortieren. Dazu gehören die Unterkategorien „Damenhosen“, „Damenhemden“ und „Damenaccessoires“. Kategorien von Männern sollten nicht betroffen sein. Sie können übernommene Ranglisten verwenden, um dies zu erreichen.

Wenn Sie eine intelligente Rangfolgenmethode für eine Kategorie oder Unterkategorie mit Unterkategorien auswählen, können Sie die Option **Intelligente Rangfolgen auf Unterkategorien anwenden** aktivieren. Dies wendet die Rangfolgenmethode auf alle Unterkategorien an.

Diese Unterkategorien übernehmen diese Regel jetzt von der übergeordneten Kategorie („Ja“ in der Spalte „Übernommenes Ranking„). In der Spalte Aktion sind nur die Optionen **Regel bearbeiten** und **Details anzeigen** verfügbar. Die **Löschen**-Option ist für übernommene Regeln für Unterkategorien deaktiviert. Das Löschen der Unterkategorievererbung erfordert das Rückgängigmachen der Vererbung von der übergeordneten Kategorie.

Für jede Kategorie oder Unterkategorie kann jeweils nur eine intelligente Rangfolge angewendet werden. Sie können auch zusätzliche manuelle Rankings anwenden.

Wenn Sie eine intelligente Rangfolge auf eine Kategorie anwenden und die Option **Intelligente Rangfolge auf Unterkategorien anwenden** aktivieren, werden alle bereits auf die Unterkategorien angewendeten intelligenten Rangfolgen überschrieben.

![Unterkategorieliste überschrieben](assets/category_overwite_subs.png){width="700"}

Wenn Sie auf **Alle anzeigen** klicken, wird ein Dialogfeld mit Details zu den vorgeschlagenen Änderungen geöffnet.

![Details zu Ranking-Änderungen](assets/category_overwrite.png)

Wenn Sie eine intelligente Rangfolge direkt zu einer Kategorie hinzufügen, die über eine geerbte intelligente Rangfolge verfügt, wird die Vererbung durch die neue intelligente Rangfolge überschrieben.

Wenn Sie das intelligente Ranking aus der Kategorie löschen, wird die Vererbung wieder hergestellt.
In beiden Szenarien werden alle manuellen Rankings beibehalten.

Wenn Sie ein intelligentes Ranking aus einer Kategorie entfernen und die Unterkategorievererbung ausgewählt ist, werden nur die vererbten intelligenten Rankings aus den Unterkategorien entfernt. Manuelle Rankings unterliegen nicht der Vererbung und bleiben erhalten.

Es wird ein Dialogfeld angezeigt, in dem erläutert wird, welche übernommenen Unterkategorien von den Änderungen an einer übergeordneten Kategorie betroffen sind.

![Modaler Dialog für Ranking-Änderungen](assets/category_overwrite_modal.png){width="1200"}

## Kategorieregel erstellen

So erstellen Sie eine Kategorieregel:

1. Klicken Sie auf **Schaltfläche** Regel hinzufügen“.
1. Klicken Sie in _Ansicht_ Kategorie auswählen“ durch die Kategorien und Unterkategorien.
1. Aktivieren Sie das Kontrollkästchen, um die Kategorie auszuwählen, die Sie ordnen möchten.
1. Klicken Sie **Apply**.

   ![Kategorie auswählen](assets/category_select.png)

1. Wählen _in der Ansicht_Kategorieregel hinzufügen“ die intelligente Rangfolgenmethode aus, die Sie auf die Kategorie anwenden möchten.
Die Kategorievorschauseite zeigt die tatsächlichen Ergebnisse der ausgewählten Rangfolge unter Verwendung Ihrer Live Search-Daten an.
1. Klicken Sie **Speichern und Veröffentlichen**, um die Regel zu speichern.

![Wählen Sie die intelligente Rangfolgenmethode aus](assets/category_ranking.png)

Der [!DNL Live Search]-Service verarbeitet die Regel und aktiviert sie nach Abschluss des Vorgangs im Store.

## Kategorieregel ändern

So ändern Sie eine vorhandene Regel:

1. Klicken Sie auf **…** in der Spalte Aktion und wählen Sie **Bearbeiten**.
1. Nehmen Sie in der Ansicht Kategorieregel bearbeiten alle erforderlichen Änderungen vor und klicken Sie auf **Speichern und veröffentlichen**.

Die Änderungen werden im Speicher angezeigt, wenn [!DNL Live Search] die Änderung verarbeitet hat.

## Kategorieregel löschen

So löschen Sie eine Kategorieregel:

1. Klicken Sie auf **…** in der Spalte Aktion und wählen Sie **Löschen**.
1. Wählen Sie im _Regel löschen_ die Option **Löschen**, um die Regel zu entfernen, oder **Abbrechen**, um die Aktion abzubrechen.

## Manuelle Rangfolge

Mit der manuellen Rangfolge können Sie die Produktreihenfolge überschreiben, die durch intelligente Ranking-Regeln bestimmt wird (falls vorhanden), und manuell steuern, wo Produkte in den Ergebnissen angezeigt werden.

Ereignisse sind Aktionen, die die Suchergebnisse ändern, wenn definierte Bedingungen erfüllt sind. Eine manuelle Rangfolge kann bis zu 25 Ereignisse umfassen.

* Verstärken: Verschiebt ein Produkt in den Suchergebnissen nach oben.
* Beerdigung: Verschiebt ein Produkt weiter unten in den Suchergebnissen.
* Produkt anheften: Verschiebt ein Produkt an eine bestimmte Position in den Ergebnissen.
* Produkt ausblenden: Schließt ein Produkt aus den Suchergebnissen aus.

Manuelle Rangfolge erstellen:

1. Richten Sie wie oben beschrieben eine intelligente Rangfolgenregel für eine Kategorie ein. Die Ergebnisse der Abfrage werden in der Vorschau der Kategorieseite angezeigt. Dabei werden Ihre tatsächlichen Live Search-Daten zur Vorschau der Ergebnisse verwendet.

1. Klicken und ziehen Sie ein Produkt in die Seitenansicht der Kategorie Vorschau . Ziehen Sie sie per Drag-and-Drop an die gewünschte Position. Die Felder Produkt und Position werden automatisch im Bereich Ereignisse ausgefüllt.

Sie können auch auf das Anheften-Symbol klicken, um ein Produkt an seinen aktuellen Speicherort anzuheften. Verwenden Sie das Kontextmenü mit den Auslassungspunkten, um „Nach oben“ oder „Nach unten“ anzuheften.

So fügen Sie ein Ereignis manuell hinzu:

1. Klicken Sie unter Manuelle Rangfolge auf das **Ereignis auswählen** und wählen Sie ein Ereignis aus, das ausgeführt werden soll, wenn die entsprechenden Bedingungen erfüllt sind.
1. Geben Sie den Namen des Produkts ein, auf das Sie Einfluss haben möchten. Produkte werden bei der Eingabe vorgeschlagen.
1. Wählen Sie für mehrere Ereignisse alle anderen Ereignisse aus, die Sie bei Erfüllung der Bedingungen als Trigger festlegen möchten.
