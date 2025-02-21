---
title: '[!DNL Product Recommendations] Workspace'
description: Erfahren Sie, wie Sie die Leistung von Produktempfehlungen konfigurieren, verwalten und überwachen.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# [!DNL Product Recommendations] Workspace

Der Arbeitsbereich [!DNL Product Recommendations] zeigt eine Liste der zuvor konfigurierten Empfehlungen mit Metriken an, mit denen Sie den Erfolg jeder Empfehlung verfolgen können. Die Liste kann so konfiguriert werden, dass Metriken für den letzten Tag, die letzte Woche oder den letzten Monat berechnet werden. Sie können die Metriken verwenden, um umsetzbare Insights zu erstellen, die darauf basieren, wie oft eine Empfehlungseinheit angezeigt oder angeklickt wird, oder um zu analysieren, wie gut Ihre Empfehlungen funktionieren.

>[!INFO]
>
>Eine Empfehlungseinheit ist ein Widget, das das empfohlene Produkt (_)_.

![Recommendations-Arbeitsbereich](assets/workspace.png)
_Recommendations Workspace_

## Festlegen des Umfangs

Zunächst wird [Umfang](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) aller Empfehlungseinstellungen auf `Default Store View` festgelegt. Wenn Ihre Commerce-Installation mehrere Store-Ansichten enthält, setzen Sie **Umfang** auf die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings), für die Ihre Empfehlungen gelten.

## Festlegen des Datumsbereichs von Metriken

1. Klicken Sie auf **Steuerelement** Kalender![Selektor](assets/icon-calendar.png) .

1. Wählen Sie eine der folgenden Optionen:

   - Letzte 24 Stunden
   - Letzte 7 Tage
   - Letzte 30 Tage

   Die berechneten Werte in den Metrikspalten ändern sich entsprechend dem aktuellen Datumsbereich.

   >[!NOTE]
   >
   >Metriken für Produktempfehlungen sind für Luma-Storefronts optimiert. Wenn Ihre Storefront nicht auf Luma basiert, hängt die Art und Weise, wie die Metriken Daten verfolgen, davon ab, wie Sie [die Ereigniserfassung implementieren](events.md).

## Spalten ein-/ausblenden

1. Klicken Sie in der oberen linken Ecke auf **Anzeigen/Ausblenden** ![Spaltenauswahl](assets/icon-show-hide-columns.png) Spalten.

   Die sichtbaren Spalten sind mit einem blauen Häkchen versehen.

1. Führen Sie im Menü eine der folgenden Aktionen aus:

   - Um eine ausgeblendete Spalte anzuzeigen, klicken Sie auf einen beliebigen Spaltennamen ohne Häkchen.
   - Um eine sichtbare Spalte auszublenden, klicken Sie auf einen beliebigen Spaltennamen mit einem Häkchen.

   Die Tabelle wird aktualisiert und enthält nur die ausgewählten Spalten.

   ![Recommendations-Arbeitsbereich](assets/workspace-select-columns.png)
   _Spalten ein-/ausblenden_

## Einstellungen

Die Einstellungen bestimmen den SaaS-Datenspeicher, der die Recommendations-Verhaltensdaten bereitstellt.

- Um zu ändern, wo Recommendations-Verhaltensdaten ihren Ursprung haben, wählen Sie einen anderen SaaS-Datenbereich aus.

- Um einen neuen SaaS-Datenbereich zu konfigurieren, klicken Sie auf **Konfiguration bearbeiten**. Weitere Informationen finden Sie unter [Einstellungen](settings.md).

![Recommendations-Einstellungen](assets/settings.png)
_Recommendations-Einstellungen_

## Details anzeigen

1. Klicken Sie in der Tabelle auf die Empfehlung, die Sie untersuchen möchten.

   ![Recommendations-Arbeitsbereich](assets/recommendation-detail.png)
   _Details zur Konversionsrate der Startseite_

1. Um den Status der Empfehlung zu ändern, klicken Sie auf **Aktivieren** oder **Deaktivieren**.

## Empfehlung bearbeiten

Klicken Sie auf der Seite mit den Empfehlungsdetails auf **Bearbeiten**. Weitere Informationen finden Sie unter [Empfehlungen bearbeiten](edit.md).

## Empfehlung erstellen

Klicken Sie auf der Seite mit den Empfehlungsdetails auf **Erstellen**. Weitere Informationen finden Sie unter [Empfehlungen erstellen](create.md).

## Workspace-Steuerelemente

| Kontrolle | Beschreibung |
|---|---|
| ![Kalenderauswahl](assets/icon-calendar.png) | Bestimmt den Zeitbereich, der für Metrikberechnungen verwendet wird. Optionen: 24 Stunden / 7 Tage / 30 Tage |
| ![Spaltenauswahl](assets/icon-show-hide-columns.png) | Bestimmt die Spalten, die in der [!DNL Product Recommendations] Tabelle angezeigt werden. |
| Einstellungen | Bestimmt den SaaS-Datenraum, in dem Recommendations-Verhaltensdaten abgerufen werden, und ermöglicht außerdem den Empfehlungstyp „Visuelle Ähnlichkeit“. |
| Empfehlung erstellen | Öffnet die Seite [Neue Empfehlung erstellen](create.md). |

## Spaltenbeschreibungen

| Spalte | Beschreibung |
|---|---|
| -Name | Der Name der Empfehlung. |
| Seite | Die Seite, auf der die Empfehlung angezeigt wird. |
| Typ | Der Empfehlungstyp. |
| Status | Der Empfehlungsstatus. Optionen: inaktiv/aktiv/Entwurf |
| Erstellt | Das Datum, an dem die Empfehlung erstellt wurde. |
| Zuletzt bearbeitet | Das Datum, an dem die Empfehlung zuletzt bearbeitet wurde. |
| Impressionen | Die Häufigkeit, mit der eine Empfehlungseinheit auf einer Seite geladen und gerendert wird. Eine Empfehlungseinheit, die sich unter dem Falz des Darstellungsfelds des Browsers befindet, wird auf der Seite gerendert, auch wenn sie nicht vom Käufer angezeigt wird. In diesem Fall wird die gerenderte Einheit als Impression gezählt, eine Ansicht wird jedoch nur gezählt, wenn der Käufer die Einheit in die Ansicht scrollt. |
| Impressions | (Sichtbare Impressions) Die Anzahl der Empfehlungseinheiten, die mindestens eine Ansicht registrieren. Wenn die Empfehlungseinheit beispielsweise zwei Zeilen mit jeweils zwei Produkten hat und die letzten beiden Produkte vom Käufer nicht gesehen werden, die ersten beiden jedoch, wird die Aktivität weiterhin als Impression gezählt. |
| Ansichten | Die Anzahl der Empfehlungseinheiten, die im Ansichtsfenster des Browsers des Käufers angezeigt werden. Wenn der Käufer die Seite mehrmals nach oben oder unten scrollt, wird das Ereignis mehrmals ausgelöst, und zwar jedes Mal, wenn das Gerät angezeigt wird. |
| Klicks | Die Summe der Klicks eines Kunden auf einen Artikel in der Empfehlungseinheit und die Anzahl der Klicks des Kunden auf die Schaltfläche **Zum Warenkorb hinzufügen** in der Empfehlungseinheit |
| Einnahmen | Der durch die Empfehlung generierte Umsatz für den aktuellen Zeitraum. |
| LT-Umsatz | (Lebensdauerumsatz) Der durch eine Empfehlung gesteuerte lebenslange Umsatz. |
| Sichtbarkeit | Der Prozentsatz der Empfehlungseinheiten, die sich für die Ansicht registrieren. |
| CTR | (Klickrate) Der Prozentsatz der Einheitenimpressionen für die Empfehlung, die einen Klick registriert. CTR zählt alle Impressionen, auch wenn die Einheit nicht in die Ansicht des Käufers gelangt. Wenn die Empfehlungseinheit nicht angezeigt wird, ist es unwahrscheinlich, dass darauf geklickt wird. Diese unsichtbaren Impressionen werden jedoch auf den CTR-Score angerechnet und reduzieren den CTR-Gesamtprozentsatz. |
| vCTR | (Sichtbare Clickthrough-Rate) Misst Klicks nur auf der Grundlage von sichtbaren Impressions (Empfehlungen, die tatsächlich im sichtbaren Teil des Käuferbildschirms erschienen sind) und bietet so einen genaueren Maßstab für die Interaktion mit Kunden. |
