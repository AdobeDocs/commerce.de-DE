---
title: Commerce-Dokumentations-Governance
description: Erfahren Sie mehr über das interne Governance-Modell für die Commerce Insights. Nicht in Experience League veröffentlicht - wurde absichtlich von TOC.md ausgeschlossen.
source-git-commit: 1da6d9753acbeadf3a0df5fae86a9386643c6d6d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Commerce-Dokumentations-Governance

Dies ist eine interne Referenz für das Dokumentations-Team. Sie wird nicht in `TOC.md` aufgeführt, daher wird sie nicht erstellt oder in Experience League veröffentlicht. Hier so ablegen, dass der Inhalt immer nah am Geschehen ist.

## Eigentum

Commerce Insights-Artikel gehören dem Autor oder Team des Verlags, der für die Einhaltung der Artikelgenauigkeit und -währung verantwortlich ist. Diese Artikel werden derzeit im `commerce.en`-Repository gehostet. Das Dokumentations-Team von Commerce unterstützt Sie bei der Sicherstellung der Inhaltsqualität und der Veröffentlichung des Artikels in der Produktionsumgebung.

## Was in Commerce Insights gehört

- **Gehört hierher**: Strategische Leitfäden und Whitepapers zu Commerce-Lösungen, die Implementierungsanleitungen auf der Grundlage von realen Szenarien abdecken. Links zu relevanten Commerce-Dokumentationsseiten für die -Unterstützung enthalten.

- **Gehört stattdessen zum Produkt-Repository**: schrittweise Konfiguration, Tutorials, Referenzmaterial (API/CLI/config-Referenz) und Fehlerbehebung. Wenn ein Beitrag hier beginnt, diese Art von Details zu akkumulieren, verschieben Sie ihn in das entsprechende Produkthandbuch und verknüpfen Sie ihn stattdessen mit ihm.

## Hinzufügen neuer Inhalte

Erstellen Sie ein COMDOX JIRA-Ticket für den zu veröffentlichenden Artikel. Kopieren Sie `[templates/comdox-intake-template.md](templates/comdox-intake-template.md)` in die Ticketbeschreibung und füllen Sie sie aus. Der Antragsteller wird aufgefordert, die Zielgruppe zu identifizieren, zu kennzeichnen, ob der Inhalt temporär ist (mit einem Ablaufdatum), und zu bestätigen, dass er in das Insights-Handbuch und nicht in die Commerce-Produktdokumentation gehört.

Sobald das Ticket den Umfang hat, starten Sie den Artikel aus einer Vorlage in `templates/` (`whitepaper-template.md`, `security-guidance-template.md`, `insight-perspective-template.md` - nicht veröffentlicht, kopieren Sie den entsprechenden in die Zieldatei und löschen Sie die eigenen Platzhalterkommentare für die Vorlage). Fügen Sie einen `TOC.md` hinzu, sobald der Inhalt zur Veröffentlichung bereit ist.

- **Neuer Abschnitt der obersten Ebene** (z. B. Insights > Katalogverwaltung) erfordert vor dem Hinzufügen eine Überprüfung der Benutzeroberflächenanalyse, da dadurch die Navigationsform des Handbuchs geändert wird. Die Commerce-IA-Prüfung für die Story oder Aufgabe wird von demjenigen durchlaufen, der sie besitzt.

- **Zum Inhaltsverzeichnis hinzufügen** - Zum Inhaltsverzeichnis vor der Veröffentlichung ein neues Thema hinzufügen. Verwenden Sie bei Bedarf Metadaten ausblenden , um einen ausgeblendeten Artikel zu veröffentlichen, der nur für Personen zugänglich ist, die über den Link verfügen. Siehe [Ausblenden von ](https://experienceleague.adobe.com/en/docs/authoring-guide/using/authoring/hiding-files) im ExL-Autorenhandbuch.

## Überprüfungskadenz

Lesen Sie den Artikelinhalt, wenn neue Commerce-Lösungen umbenannt oder aktualisiert werden oder Einblicke nicht mehr relevant sind.
