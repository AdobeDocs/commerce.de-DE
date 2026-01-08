---
source-git-commit: e97db43bcd167acc5d537a6c53479923fd761cc9
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---
# Pre-commit-Hooks für die Bildoptimierung

Dieses Verzeichnis enthält Pre-Commit-Hooks, die Bilder automatisch optimieren, bevor sie in das Repository übertragen werden.

## Was die Haken tun

- **Staging** Bilddateien (PNG, JPG, JPEG, GIF, SVG) automatisch erkennen
- **`image_optim`** ausführen, um Bilder zu komprimieren und zu optimieren
- **Optimierte Bilder automatisch neu**.
- **Sicherstellen, dass alle übergebenen Bilder** optimiert sind

## Vorteile

- Verringerte Repository-Größe
- Schnelleres Laden von Seiten für die Dokumentation
- Konsistente Bildqualität für alle Mitwirkenden
- Keine manuelle Optimierung erforderlich

## Voraussetzungen

- Ruby 3.0 oder höher
- Bundler
- Git

## Setup

### Automatisches Setup (empfohlen)

```bash
.githooks/setup-hooks.sh
```

### Manuelles Setup

```bash
git config core.hooksPath .githooks
chmod +x .githooks/*
```

### Projekt-Setup abschließen

1. Klonen Sie das Repository :

   ```bash
   git clone <repository-url>
   cd commerce-admin.en
   ```

2. Pre-Commit-Hooks aktivieren:

   ```bash
   .githooks/setup-hooks.sh
   ```

3. Jekyll-Abhängigkeiten installieren:

   ```bash
   cd _jekyll
   bundle install
   ```

## Testen der Erweiterungspunkte

1. Hinzufügen einer Bilddatei zu Ihrem Repository
2. Staging-IT: `git add <image-file>`
3. Versuchen zu übertragen: `git commit -m 'test'`
4. Der Hook sollte das Bild automatisch optimieren

### Erwartete Ausgabe

```bash
Found 1 staged image(s). Running optimization...
Optimizing: path/to/your/image.png
Re-staged optimized image: path/to/your/image.png
Image optimization complete!
```

## Bildrichtlinien

- **PNG**: Für Screenshots und Benutzeroberflächenelemente verwenden (wird automatisch optimiert)
- **SVG**: Für Symbole und einfache Grafiken verwenden (Optimierung standardmäßig deaktiviert)
- **JPEG**: Für Fotos verwenden (wird automatisch optimiert)
- **GIF**: Für Animationen verwenden (wird automatisch optimiert)

Die Pre-Commit-Hooks optimieren automatisch alle Bilder beim Commit.

## Manuelle Optimierung

Für die manuelle Bildoptimierung:

```bash
cd _jekyll
bundle exec rake images:optimize path=../path/to/images
```

## Konfiguration

Die Erweiterungspunkte verwenden die Konfigurationsdatei `_jekyll/.image_optim.yml` zum Anpassen der Optimierungseinstellungen:

- **PNG**: Verwendet `advpng`, `optipng` und `pngquant`
- **JPEG**: Verwendet `jhead`, `jpegoptim` und `jpegtran`
- **GIF**: Verwendet `gifsicle`
- **SVG**: Die SVG-Optimierung ist standardmäßig deaktiviert (kann komplexe Vektorgrafiken und Animationen beschädigen)

## Fehlerbehebung

### Hook läuft nicht

- Konfiguration des Hooks überprüfen: `git config core.hooksPath`
- Stellen Sie sicher, dass die Hook-Datei ausführbar ist: `chmod +x .githooks/pre-commit`
- Stellen Sie sicher, dass Sie sich im richtigen Repository mit `_jekyll` Verzeichnis befinden

### Optimierungsfehler

- Stellen Sie sicher, dass `bundle install` im `_jekyll` ausgeführt wurde.
- Überprüfen Sie, ob der `adobe-comdox-exl-rake-tasks` Gem installiert ist (bietet `image_optim`)
- Überprüfen der `.image_optim.yml` Konfigurationsdatei

### Leistungsprobleme

- Anpassen der Thread-Anzahl in `_jekyll/.image_optim.yml`
- Festlegen `DEBUG=1` Umgebungsvariablen für detaillierte Fehlerinformationen

## Funktionsweise

1. **Pre-commit-Trigger**: Wenn Sie `git commit` ausführen, wird der Hook automatisch ausgeführt
2. **Bilderkennung**: Durchsucht gestaffelte Dateien nach Bilderweiterungen
3. **Optimierung**: Führt `image_optim` für jedes Staging-Bild aus
4. **Re-Staging**: Fügt dem Staging-Bereich automatisch optimierte Bilder zurück
5. **Commit wird fortgesetzt**: Wenn die Optimierung erfolgreich ist, wird der Commit normal fortgesetzt

## Unterstützte Bildformate

- **PNG** (`.png`) - Verlustfreie und verlustbehaftete Komprimierung
- **JPEG** (`.jpg`, `.jpeg`) - Verlustbehaftete Komprimierung mit Metadatenbereinigung
- **GIF** (`.gif`) - Animation und statische Optimierung
- **SVG** (`.svg`) - Vektoroptimierung (standardmäßig deaktiviert)

## Best Practices

1. **Den Hook testen**: Versuchen Sie zuerst, ein kleines Bild zu übergeben, um sicherzustellen, dass es funktioniert
2. **Änderungen überprüfen**: Überprüfen Sie die Git-Differenz, um Optimierungsergebnisse anzuzeigen
3. **Überwachen der Leistung**: Die Optimierung großer Bilder kann einige Zeit in Anspruch nehmen
4. **Versionskontrolle**: In diesem `.githooks/` werden Hooks gespeichert

## Support

Bei Problemen mit den Pre-Commit-Hooks:

1. Überprüfen der Hook-Ausgabe auf Fehlermeldungen
2. Überprüfen, ob die `image_optim` funktioniert
3. Zuerst mit den manuellen Rechenaufgaben testen
4. Überprüfen Sie die Hook-Protokolle und die Konfiguration
5. Überprüfen Sie die Hook-Konfiguration: `git config core.hooksPath`
