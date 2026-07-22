---
source-git-commit: 94514c6b52ed78e6f739e3067a206e69fa05bed5
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---
# Pre-commit-Hooks für die Bildoptimierung

Dieses Verzeichnis enthält Pre-Commit-Hooks, die Bilder automatisch optimieren, bevor sie in das Repository übertragen werden.

## Was die Haken tun

- **Staging** Bilddateien (PNG, JPEG, GIF, SVG) automatisch erkennen
- **Ausführen von`image_optim`** zum Komprimieren und Optimieren von Rasterbildern (PNG, JPEG, GIF)
- **Optimierte Bilder automatisch neu**.
- **Sicherstellen, dass alle übergebenen Rasterbilder** optimiert sind
- **Überprüfen Sie bereitgestellte SVGs** anhand einer Größenbeschränkung und brechen Sie den Commit ab, wenn eine SVG diese überschreitet

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
- **JPEG**: Für Fotos verwenden (wird automatisch optimiert)
- **GIF**: Für Animationen verwenden (wird automatisch optimiert)
- **SVG**: Für Symbole und einfache Grafiken verwenden (nicht optimiert, aber auf eine Größenbeschränkung geprüft; Commit schlägt fehl, wenn die Grenze überschritten wird)

Die Pre-Commit-Hooks optimieren beim Commit automatisch PNG-, JPEG- und GIF-Bilder und überprüfen gestaffelte SVGs mit einer Größenbeschränkung (140 KB).

Wenn eine gestaffelte SVG das Limit überschreitet, wird der Commit abgebrochen. Konvertieren Sie sie stattdessen in PNG:

```bash
cd _jekyll
bundle exec rake images:svg_to_png path=path/to/image.svg
```

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
- **SVG**: Nicht optimiert (von der `image_optim` ausgeschlossen, um Vektorgrafiken und Animationen beizubehalten), aber mit einer Größenbeschränkung von 140 KB überprüft

## Fehlerbehebung

### Hook läuft nicht

- Konfiguration des Hooks überprüfen: `git config core.hooksPath`
- Stellen Sie sicher, dass die Hook-Datei ausführbar ist: `chmod +x .githooks/pre-commit`
- Stellen Sie sicher, dass Sie sich im richtigen Repository mit `_jekyll` Verzeichnis befinden

### Optimierungsfehler

- Stellen Sie sicher, dass `bundle install` im `_jekyll` ausgeführt wurde.
- Überprüfen Sie, ob der `adobe-comdox-exl-rake-tasks` Gem installiert ist (bietet `image_optim`)
- Überprüfen der `.image_optim.yml` Konfigurationsdatei

### SVG überschreitet Größenbeschränkung

- Der Commit wird abgebrochen, wenn ein gestaffelter SVG 140 KB überschreitet
- Konvertieren des SVGS in PNG: `cd _jekyll && bundle exec rake images:svg_to_png path=path/to/image.svg`
- Staging Sie dann das PNG anstelle des SVGS und übertragen Sie erneut

### Leistungsprobleme

- Anpassen der Thread-Anzahl in `_jekyll/.image_optim.yml`
- Festlegen `DEBUG=1` Umgebungsvariablen für detaillierte Fehlerinformationen

## Funktionsweise

1. **Pre-commit-Trigger**: Wenn Sie `git commit` ausführen, wird der Hook automatisch ausgeführt
2. **Bilderkennung**: Durchsucht gestaffelte Dateien nach Bilderweiterungen
3. **Optimierung**: Wird `image_optim` für jedes bereitgestellte PNG, jede JPEG oder jede GIF ausgeführt
4. **Re-Staging**: Fügt dem Staging-Bereich automatisch optimierte Bilder zurück
5. **Größenüberprüfung für SVG**: Prüft jedes bereitgestellte SVG anhand der Größenbeschränkung von 140 KB
6. **Commit wird fortgesetzt**: Wenn die Optimierung erfolgreich ist und kein SVG die Größenbeschränkung überschreitet, wird der Commit normal fortgesetzt. Andernfalls wird der Commit abgebrochen

## Unterstützte Bildformate

- **PNG** (`.png`) - Verlustfreie und verlustbehaftete Komprimierung
- **JPEG** (`.jpg`, `.jpeg`) - Verlustbehaftete Komprimierung mit Metadatenbereinigung
- **GIF** (`.gif`) - Animation und statische Optimierung
- **SVG** (`.svg`) - Nicht optimiert (Commit unverändert, um die Qualität zu erhalten), aber mit einer Größenbeschränkung von 140 KB verglichen. Der Commit wird abgebrochen, wenn der Grenzwert überschritten wird

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
