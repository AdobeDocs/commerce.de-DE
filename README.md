---
source-git-commit: bdde436394667a2d5477fbc44eac5b90bd865c68
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---
# Technische Dokumentation zu Adobe Commerce

Wir freuen uns über Beiträge von der Community sowie von Adobe-Mitarbeitern von außerhalb der Dokumentations-Teams.

## Adobe Open Source-Verhaltenskodex

Dieses Projekt hat den [Open Source-Verhaltenskodex für Adobe ](code-of-conduct.md) den [.NET Foundation-Verhaltenskodex ](https://dotnetfoundation.org/code-of-conduct). Weitere Informationen finden Sie im Artikel [Beitragende](contributing.md) .

## Über Ihre Beiträge zu Adobe-Inhalten

Siehe das [Handbuch für Mitwirkende an Adobe-Dokumenten](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Wie Sie Beiträge einbringen, hängt davon ab, wer Sie sind und welche Art von Änderungen Sie beitragen möchten:

### Geringfügige Änderungen

Wenn Sie kleinere Aktualisierungen beitragen möchten, besuchen Sie den Artikel und klicken Sie auf den Feedback-Bereich unten im Artikel, klicken Sie auf **Detaillierte Feedback-Optionen** und dann auf **Bearbeiten vorschlagen**, um zur Markdown-Quelldatei auf GitHub zu gelangen. Verwenden Sie die GitHub-Benutzeroberfläche, um Ihre Aktualisierungen vorzunehmen. Weitere Informationen finden Sie im allgemeinen Leitfaden für Beitragende zu Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)Dokumenten .[

Kleinere Korrekturen oder Erläuterungen, die Sie zur Dokumentation und zu Code-Beispielen in diesem Repository eingeben, werden von den Adobe-Nutzungsbedingungen abgedeckt.

### Wichtige Änderungen oder neue Artikel von Community-Mitgliedern

Wenn Sie Teil der Adobe-Community sind und einen neuen Artikel erstellen oder wichtige Änderungen vornehmen möchten, verwenden Sie im Git-Repository die Registerkarte „Probleme“, um ein Problem zu senden und eine Konversation mit dem Dokumentations-Team zu beginnen. Sobald Sie sich auf einen Plan geeinigt haben, müssen Sie mit einem Mitarbeiter zusammenarbeiten, um diese neuen Inhalte durch eine Kombination von Arbeiten in den öffentlichen und privaten Repositorys einzubringen.

### Wesentliche Veränderungen durch Adobe Mitarbeiter

Wenn Sie technischer Redakteur/technische Redakteurin, Programm-Manager oder Entwickler(in) des Produkt-Teams für eine Adobe Experience Cloud-Lösung sind und es Ihre Aufgabe ist, technische Artikel zu erstellen oder zu diesen beizutragen, sollten Sie das private Repository unter `https://git.corp.adobe.com/AdobeDocs` verwenden.

## Tools und Einrichtung

Community-Mitwirkende können für eine einfache Bearbeitung die GitHub-Benutzeroberfläche oder für wichtige Beiträge das Repository nutzen.

Weitere Informationen finden Sie im Adobe-Handbuch für Mitwirkende ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) Dokumenten .[

## Verwenden von Markdown zum Formatieren des Themas

Alle Artikel in diesem Repository verwenden GitHub-Markdown. Wenn Sie mit Markdown nicht vertraut sind, lesen Sie:

- [Markdown-Grundlagen](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [Druckbare Markdown-Anleitung](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Pre-commit-Hooks für die Bildoptimierung

Dieses Repository enthält automatisierte Hooks zur Vorabbestätigung, mit denen Bilder vor dem Commit optimiert werden. **Alle Mitwirkenden sollten diese Erweiterungspunkte aktivieren** um eine konsistente Bildoptimierung und eine reduzierte Repository-Größe sicherzustellen.

### Schnelleinrichtung

Führen Sie nach dem Klonen des Repositorys Folgendes aus:

```bash
.githooks/setup-hooks.sh
```

### Was die Haken tun

- Gestaffelte Bilddateien automatisch erkennen (PNG, JPEG, GIF, SVG)
- Ausführen von `image_optim` zum Komprimieren und Optimieren von Rasterbildern (PNG, JPEG, GIF)
- Optimierte Bilder automatisch neu inszenieren
- Sicherstellen, dass alle übergebenen Rasterbilder ordnungsgemäß optimiert sind
- Überprüfen Sie bereitgestellte SVGs anhand einer Größenbeschränkung und brechen Sie den Commit ab, wenn eine SVG diese überschreitet

### Vorteile

- Verringerte Repository-Größe
- Schnelleres Laden von Seiten für die Dokumentation
- Konsistente Bildqualität für alle Mitwirkenden
- Keine manuelle Optimierung erforderlich

Detaillierte Setup-Anweisungen, Fehlerbehebung und Konfiguration finden Sie unter [`.githooks/README.md`](.githooks/README.md).

## Verfügbare Rake-Aufgaben

Dieses Repository verwendet RAKE-Aufgaben, die vom bereitgestellt werden.
[`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks)
gem. Um alle verfügbaren Aufgaben anzuzeigen, führen Sie Folgendes aus:

```bash
cd _jekyll
bundle exec rake --tasks
```
