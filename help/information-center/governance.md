---
title: Commerce Information Center Governance
description: Erfahren Sie mehr über das interne Governance-Modell für das Commerce Information Center. Nicht in Experience League veröffentlicht.
source-git-commit: a91925091da28cd0745923894a3faab0374f0a0c
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%
---

# Commerce Information Center Governance

Diese interne Referenz für das Dokumentations-Team ist nicht in `TOC.md` aufgeführt und wird daher nicht in Adobe Experience League veröffentlicht.

## Eigentum

Das Dokumentations-Team von Adobe Commerce ist für das Informationszentrum verantwortlich. Sie wurde in `Adobe-Enterprise-Docs/commerce.en` verfasst, dem Repository, das in `metadata.md` als `git-repo` aufgeführt ist.

Kein einzelnes Produkt-Team ist dafür verantwortlich, da es produktübergreifend ist. Eskalieren Sie produktspezifische Korrekturen an den Dokumentkontakt des besitzenden Produkt-Teams, anstatt sie hier zu beheben.

## Was im Informationszentrum gehört

| Gehört hierher | Gehört zum Produkt-Repository |
| --- | --- |
| Inhalte, die mehr als ein Produkt oder einen Service umfassen, z. B. Anleitungen zur Produktauswahl, produktübergreifende Implementierungs-Journey, Architekturmuster und Whitepapers | Einzelproduktinhalte, z. B. schrittweise Konfiguration, API/CLI/config-Referenz und Fehlerbehebung |
| Kurze Kuratierungsseiten, die auf autorisierende Produktdokumente verlinken | |

- Wenn eine Seite hier Einzelproduktdetails sammelt, verschieben Sie sie in das Produkthandbuch und verknüpfen Sie sie damit.
- Das Informationszentrum konsolidiert oder migriert keine Produktdokumentation und dokumentiert auch keine einzelnen Produktfunktionen. Verlinken Sie zu vorhandenen autoritativen Inhalten, bevor Sie etwas Neues schreiben.

## Hinzufügen neuer Inhalte

### Artikel in einem vorhandenen Abschnitt

1. Fügen Sie die Datei dem Ordner hinzu, der dem Abschnitt entspricht.
1. Fügen Sie unter diesem Abschnitt einen Eintrag zu `TOC.md` hinzu.

Über die normale PR-Prüfung hinaus ist keine Genehmigung erforderlich.

| Inhaltsverzeichnisabschnitt | Ordner |
| --- | --- |
| Commerce-Plattformen und -Services | `portfolio/`, `storefronts/`, `aem-assets/`, `apis/` |
| Erste Schritte nach Rolle | `get-started/` |
| Erkenntnisse und Anleitungen | `guidance-and-insights/` |
| Architektur | `architecture-options/` |
| Migration und Einführung | `migration-adoption/` |
| Implementierungshandbücher | `implementation-guides/` |

### Artikel zu Insights und Anleitungen

1. Kopieren Sie `whitepaper-template.md` oder `security-guidance-template.md` aus `guidance-and-insights/templates/` in `guidance-and-insights/`. Die Vorlagen werden nicht veröffentlicht. Den vollständigen Authoring-Prozess, einschließlich des COMDOX-Eintrittstickets, finden Sie unter [readme.md](guidance-and-insights/readme.md).
1. Löschen Sie die Platzhalterkommentare der Vorlage.
1. Fügen Sie einen `TOC.md` Eintrag unter Einblicke und Anleitungen hinzu, wenn die Inhalte zur Veröffentlichung bereit sind.

### Abschnitte der obersten Ebene

Eine neue Gruppe auf oberster Ebene in `TOC.md` ändert die Navigation des Handbuchs. Daher ist eine Überprüfung der Benutzeroberflächenanalyse erforderlich. Kontaktieren Sie den Eigentümer der Commerce IA-Überprüfung. Verwenden Sie zuerst einen vorhandenen Abschnitt wieder, z. B. Erste Schritte mit der Rolle für Partner- oder Aktivierungsinhalte.

### Veröffentlichte URLs

URLs werden aus der Guide-ID, den Abschnitt-IDs in `TOC.md` (z. B. `{#insights-and-guidance}`) und dem Dateinamen erstellt. Ordnernamen werden nicht in der URL angezeigt. Geben Sie jedem Abschnitt eine eindeutige ID und stellen Sie sicher, dass keine zwei Artikel auf dieselbe URL aufgelöst werden.

## Überprüfungskadenz

- **Ereignisgesteuert** - Lesen Sie die Abschnitte Erkunden von Commerce-Plattformen und -Services, Erste Schritte nach Rolle, Architektur, Migration und Einführung sowie Implementierungshandbücher, wenn ein Commerce-Produkt umbenannt, gestartet oder veraltet wird oder seine Verfügbarkeit sich ändert. Überprüfen Sie sie beispielsweise, ob Adobe Commerce as a Cloud Service und Adobe Commerce Optimizer eine Integration erhalten. Diese Seiten werden zuerst veraltet.
- **Geplant** - Führen Sie alle sechs Monate ein automatisiertes Content Audit und eine Überprüfung durch, um veraltete Terminologie, Branding oder technische Ungenauigkeiten zu ermitteln.

## Beziehung zu Hilfe/Landing/

`help/landing/` (“Adobe Commerce Services Guides„) ist ein separates Handbuch, das nicht zum Informationszentrum gehört. Der Schwerpunkt liegt auf Commerce-Services wie Katalog-Service, Live Search, Produktempfehlungen und Zahlungs-Services sowie auf den Links zum Informationszentrum, die Details enthalten. Die Erweiterung oder Konsolidierung der beiden ist eine Folgeentscheidung, die in diesem Handbuch nicht aufgelöst wird.
