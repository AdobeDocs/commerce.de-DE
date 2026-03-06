---
title: Merchandising-Regeln - Workspace
description: Lernen Sie den Arbeitsbereich „Merchandising-Regeln“ kennen.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 3deac529-731d-44b9-87f3-3c9cb36e28e7
source-git-commit: 9cb231055df45bbfcff3303c6e1c257c883cb852
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---

# Merchandising-Regeln - Workspace

Der *Merchandising-Regeln*-Arbeitsbereich listet die aktuelle Auswahl von Regeln und deren Status auf und bietet Zugriff auf Tools, die Sie zum Erstellen und Verwalten von Regeln benötigen. Sie können Regeln auf alle [Katalogansichten](../../setup/catalog-view.md) (global) oder auf eine einzelne Katalogansicht beschränken. Informationen [&#x200B; Filtern nach Katalogansicht und &#x200B;](#select-catalog-view) Erstellen von Regeln pro Katalogansicht finden Sie unter „Auswählen Katalogansicht“. Im Arbeitsbereich haben Sie folgende Möglichkeiten:

- Nach Regeln suchen
- Regeldetails anzeigen
- Regeln aktivieren/deaktivieren
- Regeln löschen
- Zugriff auf den Regeleditor

![Merchandising-Regeln - Workspace](../../assets/rules-workspace.png)

## Spalten ein-/ausblenden

1. Klicken Sie oben rechts auf die Spalten **Anzeigen/Ausblenden** ![Spaltenauswahl](../../assets/btn-show-hide-columns.png).

1. Führen Sie im Menü eine der folgenden Aktionen aus:

   - Um eine ausgeblendete Spalte anzuzeigen, klicken Sie auf einen beliebigen Spaltennamen ohne Häkchen.
   - Um eine sichtbare Spalte auszublenden, klicken Sie auf einen beliebigen Spaltennamen mit einem Häkchen.

## Regeln nach Status filtern

1. Wenn Ihr Store viele Regeln hat, können Sie die Regeln nach Status filtern, um die Liste zu verkürzen. Standardmäßig werden in der Liste Regeln alle Regeln angezeigt.

1. Um nur Regeln mit einer bestimmten Statuseinstellung aufzulisten, setzen Sie **Status** auf eine der folgenden Optionen:

   - Alle
   - Aktiv
   - Inaktiv
   - Geplant
   - Entwurf

   Sie können auch nach **Bedingungen**, **Startdatum**, **Enddatum** und **Zuletzt aktualisiert**.

## Details anzeigen

Im Detailbereich werden der Regelname, der Status, Bedingungen und Ereignisse, das Start- und Enddatum, die Beschreibung und das Datum der letzten Bearbeitung angezeigt. Regeln können im Detailbereich aktiviert, bearbeitet und gelöscht werden.

1. Suchen Sie im Arbeitsbereich *Merchandising* Regeln“ die Regel in dem Raster, das Sie anzeigen möchten, und klicken Sie auf das Symbol (![Weitere &#x200B;](../../assets/btn-more.png)).

   Im Menü können Sie eine der folgenden Aktionen ausführen:

   - Regel bearbeiten
   - Regel löschen
   - Regel aktivieren/deaktivieren

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
| Regel hinzufügen | Öffnet den [Regeleditor](add.md). |
| Katalogansicht | Filtert die Tabelle nach Regeln, die für die ausgewählte Katalogansicht gelten. Legt den Umfang auch fest, wenn Sie [eine Regel erstellen](add.md). Optionen: *Alle Ansichten* oder eine bestimmte [Katalogansicht](../../setup/catalog-view.md). Siehe [Auswählen einer Katalogansicht](#select-catalog-view). |
| Status | Filtert die Liste der Regeln nach Status. Optionen: Alle, aktiv, inaktiv, geplant |
| ![Spaltenauswahl](../../assets/btn-show-hide-columns.png) | Gibt die im Raster sichtbaren Spalten an. Optionen: Zuletzt aktualisiert, Startdatum, Enddatum, Status |
| Suche | Sucht nach einer Regel anhand des vollständigen Namens oder einer teilweisen Übereinstimmung. |
| ![Auswahl Mehr](../../assets/btn-more.png) | Zeigt ein Menü mit weiteren Aktionen an, die auf die ausgewählte Regel angewendet werden können. Optionen: Bearbeiten, Details anzeigen, Löschen |

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

## Katalogansicht auswählen

>[!IMPORTANT]
>
>Diese Funktion befindet sich derzeit in der Betaphase.

Der **[!UICONTROL Catalog view]**-Selektor auf der Seite „Merchandising-Regeln“ hat zwei Aufgaben:

1. **Filtert die Tabelle** - Zeigt nur Regeln (und deren Details) an, die für die ausgewählte Katalogansicht gelten.
1. **Legt den Umfang für neue Regeln fest** - Wenn Sie [Regel erstellen](add.md) wird die ausgewählte Katalogansicht als Umfang der Regel verwendet. Die Optionen sind *Alle*) oder eine bestimmte [Katalogansicht](../../setup/catalog-view.md).

   - **Alle Ansichten** - Die Regel gilt für alle Katalogansichten. Das Such- und Ranking-Verhalten ist in jeder Storefront, die den Katalog verwendet, identisch.
   - **Katalogansicht** - Die Regel gilt nur für die ausgewählte Katalogansicht (z. B. eine Storefront, Region, Händler oder Marke). Verwenden Sie dies, wenn verschiedene Katalogansichten eine andere Merchandising-Logik benötigen.

Weitere Informationen zum Erstellen einer Regel und Festlegen ihres Umfangs finden Sie unter [Regeln erstellen und verwalten](add.md).

### Warum eine Regel pro Katalogansicht erstellen?

Erstellen Sie Regeln pro Katalogansicht, wenn verschiedene Storefronts, Regionen oder Marken ein unterschiedliches Such- und Ranking-Verhalten benötigen. Beispiele:

- **Händlernetzwerke oder Händlernetzwerke** - Jeder Händler hat seine eigene Katalogansicht; Sie möchten verschiedene angeheftete, geboosterte oder verschüttete Produkte pro Händler.
- **Multi-Region** - Separate Katalogansichten für die EU, die USA oder andere Regionen mit regionsspezifischen Merchandising-Regeln.
- **Mehrmarken** - Jede Marke verfügt über eine eigene Katalogansicht und Sie möchten markenspezifische Regeln (z. B. unterschiedliche Standard-Rankings oder beworbene Produkte pro Marke).

Verhaltensdaten, die [intelligentes Ranking“ &#x200B;](add.md#intelligent-ranking) (z. B. am häufigsten angezeigt, am häufigsten gekauft, Trends), werden standardmäßig pro Katalogansicht berechnet. Regeln, die ein intelligentes Ranking verwenden, spiegeln daher das Käuferverhalten dieser Katalogansicht wider. Wenn Ihr Konto über eine große Anzahl von Katalogansichten verfügt, kann das System Verhaltensdaten global aggregieren, um die Leistung aufrechtzuerhalten. In diesem Fall kann das Ranking stärker durch Katalogansichten mit hohem Traffic beeinflusst werden, und die Relevanz für Ansichten mit niedrigerem Traffic kann reduziert werden. Siehe [Beschränkungen und Grenzen](../../boundaries-limits.md) für aktuelle Beschränkungen.

### Einrichten einer Regel pro Katalogansicht

1. Verwenden *im Arbeitsbereich „Merchandising* Regeln“ das Dropdown-**[!UICONTROL Catalog view]**, um die Katalogansicht auszuwählen, in der die Regel angewendet werden soll.
1. Klicken Sie auf **[!UICONTROL Create rule]**.

   Die von Ihnen erstellte Regel wird auf die ausgewählte Katalogansicht angewendet.
1. Erstellen Sie Ihre Regel im [Regeleditor](add.md).

   Definieren Sie im Editor Bedingungen, Ereignisse und Details. Die Regel gilt nur für Suchergebnisse in dieser Katalogansicht.

Sie können die Katalogansicht (den Umfang) einer Regel nicht ändern, nachdem sie erstellt wurde. Um eine ähnliche Logik auf eine andere Katalogansicht anzuwenden, erstellen Sie eine neue Regel und wählen Sie diese Katalogansicht aus, bevor Sie sie erstellen.
