---
title: Merchandising-Workspace durchsuchen
description: Lernen Sie Merchandising-Arbeitsbereich durchsuchen kennen.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 1%

---

# Merchandising-Workspace durchsuchen

Der *Merchandising durchsuchen*-Arbeitsbereich listet die aktuelle Auswahl von Regeln und deren Status auf und bietet Zugriff auf Tools, die Sie zum Erstellen und Verwalten von Regeln benötigen. Im Arbeitsbereich haben Sie folgende Möglichkeiten:

* Nach Regeln suchen
* Regeldetails anzeigen
* Regeln aktivieren/deaktivieren
* Regeln löschen
* Zugriff auf den Regeleditor

![Merchandising-Workspace suchen](assets/rules-workspace.png)

## Festlegen des Umfangs

Wenn Ihre Adobe Commerce-Installation mehrere Store-Ansichten enthält, legen Sie **Umfang** auf die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=de#scope-settings) fest, für die Ihre Regeln gelten.

## Spalten ein-/ausblenden

1. Klicken Sie oben rechts auf die Spalten **Anzeigen/Ausblenden** ![Spaltenauswahl](assets/btn-show-hide-columns.png).
Die sichtbaren Spalten sind im Optionsmenü mit einem blauen Häkchen versehen. Der Regelname ist die einzige Spalte, die nicht ausgeblendet werden kann.

1. Führen Sie im Menü eine der folgenden Aktionen aus:

   * Um eine ausgeblendete Spalte anzuzeigen, klicken Sie auf einen beliebigen Spaltennamen ohne Häkchen.
   * Um eine sichtbare Spalte auszublenden, klicken Sie auf einen beliebigen Spaltennamen mit einem Häkchen.

## Regeln nach Status filtern

1. Wenn Ihr Store viele Regeln hat, können Sie die Regeln nach Status filtern, um die Liste zu verkürzen. Standardmäßig werden in der Liste Regeln alle Regeln angezeigt.

1. Um nur Regeln mit einer bestimmten Statuseinstellung aufzulisten, setzen Sie **Status** auf eine der folgenden Optionen:

   * Alle
   * Aktiv
   * Inaktiv
   * Geplant

## Suchen von Suchregeln nach Namen

Geben Sie den Namen der Regel oder ein beliebiges Wort in den Regelnamen ein.
Die Suche findet die passenden Regeln während der Eingabe. Die Zeichenfolge mit übereinstimmenden Zeichen wird im Namen jeder gefundenen Regel hervorgehoben.

![Regeln - Nach Namen suchen](assets/rules-workspace-search-name.png)

## Details anzeigen

Im Detailbereich werden der Regelname, der Status, Bedingungen und Ereignisse, das Start- und Enddatum, die Beschreibung und das Datum der letzten Bearbeitung angezeigt. Regeln können im Detailbereich aktiviert, bearbeitet und gelöscht werden.

1. Suchen Sie im Arbeitsbereich *Merchandising durchsuchen* die Regel in dem Raster, das Sie anzeigen möchten, und klicken Sie auf **Mehr** (…).
1. Klicken Sie **Details anzeigen**.
Sie können einen der folgenden Schritte im Bedienfeld Details anzeigen ausführen:

   * Regel bearbeiten
   * Regel löschen
   * Regel aktivieren/deaktivieren

1. Um das Bedienfeld *Details anzeigen* zu schließen, klicken Sie oben rechts auf **Schließen** (X).

   ![Regel - Details](assets/rules-workspace-details.png)

## Spaltenbeschreibungen

| Spalte | Beschreibung |
|--- |--- |
| -Name | Der Name der Regel. |
| Zuletzt aktualisiert | Das Datum der letzten Aktualisierung der Regel. |
| Startdatum | Das Startdatum einer geplanten Regel. |
| Enddatum | Das Enddatum einer geplanten Regel. |
| Status | Der farbcodierte Status gibt den aktuellen Status der Regel an. Verwenden Sie die Statussteuerung über dem Raster, um Regeln nach Status zu filtern. Werte:<br />Alle Status - Zeigt alle Regeln unabhängig vom Status an.<br />Aktiv (blau) - Zeigt nur aktive Regeln an.<br />Geplant (orange) - zeigt nur geplante Regeln an.<br />Inaktiv (grau) - zeigt nur inaktive Regeln an. |

## Kontrollen

| Kontrolle | Beschreibung |
|--- |--- |
| Regel hinzufügen | Öffnet den [Regeleditor](rules-add.md). |
| Status | Filtert die Liste der Regeln nach Status. Optionen: Alle, aktiv, inaktiv, geplant |
| ![Spaltenauswahl](assets/btn-show-hide-columns.png) | Gibt die im Raster sichtbaren Spalten an. Optionen: Zuletzt aktualisiert, Startdatum, Enddatum, Status |
| Suche | Sucht nach einer Regel anhand des vollständigen Namens oder einer teilweisen Übereinstimmung. |
| ![Auswahl Mehr](assets/btn-more.png) | Zeigt ein Menü mit weiteren Aktionen an, die auf die ausgewählte Regel angewendet werden können. Optionen: Bearbeiten, Details anzeigen, Löschen |

## Regeldetails

| Feld | Beschreibung |
|--- |--- |
| Status | Der aktuelle Status der Regel. |
| Bedingungen | Die Suchabfrage, die die mit der Regel verknüpften Bedingungen beschreibt. |
| Startdatum | Das Datum, an dem die Regel wirksam wird, falls geplant. |
| Enddatum | Das Datum, an dem die Regel abläuft, falls geplant. |
| Beschreibung | Eine kurze Beschreibung der Regel. |
| Zuletzt aktualisiert | Datum und Uhrzeit der letzten Aktualisierung der Regel. |
| Aktiviert | Ein Steuerelement, das den Status der Regel ändert. Optionen: aktiviert/deaktiviert |
