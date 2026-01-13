---
title: Beschränkungen und Grenzen
description: Verstehen  [!DNL Adobe Commerce Optimizer]  Beschränkungen und Grenzen, um Kapazitäten zu planen und Leistungsprobleme zu vermeiden.
role: Admin, Developer
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 58d94da9-8d48-4513-8b6a-8e8c7c27a2a5
source-git-commit: f9ac230d448f071e6e8e6368b940f0c415abb02b
workflow-type: tm+mt
source-wordcount: '1350'
ht-degree: 0%

---

# Beschränkungen und Grenzen

[!DNL Adobe Commerce Optimizer] gibt zwei Arten von Beschränkungen:

- **Lizenzbeschränkungen** - Abhängig von Ihrer erworbenen Kapazität; kann durch den Kauf zusätzlicher Pakete erweitert werden.
- **Systemgrenzen** - Feste Grenzwerte, die Systemressourcen schützen und eine zuverlässige Leistung für alle Benutzer sicherstellen.

Ihre Nutzung muss innerhalb dieser Grenzen bleiben. Sie zu überschreiten kann zu erhöhter Latenz und Anfragebeschränkung führen.

## Zusätzliche Kapazität anfordern

Lizenzbeschränkungen können erhöht werden, indem Sie die Lizenzpakete erwerben, die im Abschnitt [Lizenzbeschränkungen und Systemgrenzen](#license-limits-and-system-boundaries) beschrieben sind, oder indem Sie benutzerdefinierte Lizenzen für eindeutige Anwendungsfälle aushandeln. Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um Ihre Anforderungen zu besprechen.

Wenden Sie sich bei Fragen zu Systemgrenzen an den [Adobe-Support](https://experienceleague.adobe.com/home?lang=de#support).

## Leistungsprobleme verhindern

Befolgen Sie diese Best Practices, um innerhalb der Beschränkungen zu bleiben und betriebliche Probleme zu vermeiden:

- **Überprüfen Sie Ihre**: Machen Sie sich mit Ihren [Kapazitätsbeschränkungen](#license-limits-and-system-boundaries) vertraut, bevor Sie neue Storefronts oder Kampagnen starten.
- **Nutzung nachverfolgen** - Verwenden Sie integrierte Metriken-Dashboards oder CDN-Protokolle.

## Lizenzbeschränkungen und Systemgrenzen

In den folgenden Tabellen sind die Lizenzbeschränkungen und Systemgrenzen nach Funktionsbereich zusammengefasst und gegebenenfalls Informationen zum Hinzufügen zusätzlicher Lizenzen zur Erweiterung der Kapazität enthalten.

### Umgebungsbeschränkungen

| **Umgebung** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| **Sandbox-Umgebung** | Die Anzahl der eingeschlossenen Sandbox-Umgebungen | 2 pro Instanz | Ja<p>Hinzufügen einer zusätzlichen Umgebungslizenz pro Instanz</p> |
| **Produktionsumgebung** | Die Anzahl der eingeschlossenen Produktionsumgebungen | 1 pro Instanz | Lizenz<p>Hinzufügen einer zusätzlichen Umgebungslizenz pro Instanz</p> |

{style="table-layout:auto"}

### Katalog

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Aufnahmegeschwindigkeit eines Produkts | Die Anzahl der erstellten oder aktualisierten Produkte | 1K Aktualisierungen pro Minute<p>Maximal 100.000 Aktualisierungen pro Tag</p> | Ja<p>Ein Lizenzpaket hinzufügen:</p><ul><li>5.000 Aktualisierungen pro Minute<br>maximal 5.000 Aktualisierungen pro Tag</li> <li>10.000 Updates pro Minute<br>maximal 1.000 Updates pro Tag</li></ul><p>Die maximale Kapazität für die Datenaufnahme beträgt 1 Million Aktualisierungen pro Tag.</p> |
| Payload-Größe des Produkts | Die maximale Datenmenge, die beim Erstellen, Aktualisieren oder Aufnehmen von Produktinformationen mithilfe der API zulässig ist | 200 KB | Nein |
| Katalogvarianten | Die Anzahl der Ansichten eines Katalogs, die Storefront-Benutzern zur Verfügung stehen,<p>die gezählt werden als (*Anzahl der Katalogansichten × Anzahl der Preisbücher*)</p> | 100 Varianten | Ja<p>100 Katalogvarianten-Lizenzpaket hinzufügen</p> |
| Produkte in einer einzigen Katalogquelle | Im Katalog unterstützte SKUs | 250K SKUs | Ja<p>100K SKU-Lizenzpaket hinzufügen</p> |
| Varianten pro Produkt | Die Anzahl der pro Produkt zulässigen Produktvarianten (Größe, Farbkombinationen) | 10 K | Nein |
| Katalogquellen | Die Anzahl der Katalogdatenkontexte (z. B. Gebietsschemata oder Datenquellen wie PIMs und ERPs) | 50 | Nein |

{style="table-layout:auto"}

### Preisbücher

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Preisbücher | Die Anzahl der pro Instanz zulässigen Preisverzeichnisse | Basierend auf der Anzahl der [Katalogvarianten](#catalog) | Ja<br>Katalogvarianten erhöhen |
| Rabatte pro Preisnachweis | Die Anzahl der Rabatte, die auf einen Produktpreis innerhalb eines einzigen Preisbuchs angewendet werden können | 10 | Nein |

{style="table-layout:auto"}

### Produktvisualisierungen mit AEM Assets

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Produktvisualisierung Power-User | Lizenzierter Anwender mit vollständigen Digital-Asset-Management-Funktionen, einschließlich KI-Tools, Adobe Express/Firefly-Integrationen und Content Hub-Freigabe, Handhabung von DAM-Kernaufgaben und erweiterten Cloud-nativen Funktionen für optimale Effizienz. | 2 | Ja<p>Upgrade auf AEM Assets-Lizenz</p> |
| Benutzer von Product Visuals Collaborator | Greifen Sie über die AEM Commerce-Integration auf Assets zu und arbeiten Sie mit ihnen, erstellen und bearbeiten Sie Inhalte mithilfe von Adobe Express und Firefly und nutzen Sie - falls aktiviert - genehmigte Assets über das Content Hub-Portal. | 2 | Ja<p>Upgrade auf AEM Assets-Lizenz</p> |
| Speicherung von Produktbildern | Zugewiesener Speicherplatz für Assets | 1 TB Speicher | Nein |
| Verwendung von Dynamic Media | Toleranz für Dynamic Media-Verarbeitungsvorgänge, die Folgendes umfassen:<ul><li>Bildbereitstellung</li><li>Intelligente Bildbearbeitung</li><li>Videowiedergabe</li></ul><p>Weitere Informationen finden Sie *Berechnen der Dynamic Media-Nutzung* unten. | Basierend auf GMV<p>Mindestzuweisung: 5 Mio. Operationen/Monat</p> | Ja<ul><li>Lizenz für zusätzliche Vorgänge erwerben</li><li>Upgrade auf AEM Assets-Lizenz</li></ul> |
| Videobereitstellung | Toleranz für Videobereitstellung oder Downloads | 300 Videos, 1 Minute pro Video | Ja<p>Upgrade auf AEM Assets-Lizenz</p> |
| Asset-Generierung | Zugriff auf die generative KI von Adobe Express und Adobe Firefly zum Erstellen von Bildern | Keine | Generative KI-Credits separat erwerben |

{style="table-layout:auto"}


>[!NOTE]
>
>**Power Users** können direkt oder innerhalb von Adobe Commerce Optimizer auf Adobe Express zugreifen. **Collaborator-Benutzer** können direkt auf das Adobe Express-Programm zugreifen. Die Nutzung wird durch die [Adobe Express mit Firefly-spezifischen Lizenzbedingungen geregelt](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeExpressWFirefly-WW-2025v1.pdf).


>[!BEGINSHADEBOX „Berechnen der Dynamic Media-Nutzung“]

Die Verwendung von Dynamic Media verfolgt API-Anfragen, die in die Produktvisualisierungskomponenten in Adobe Commerce Optimizer eingehen, um eine der folgenden Aktionen zu erleichtern:

- **Die Bildbereitstellung verbraucht einen Dynamic Media** Vorgang für jedes Vorkommen der folgenden:
   - **Grundlegende Bildumwandlung** eines digitalen Assets, z. B. Größenänderungs-, Skalierungs-, Formatkonvertierungs-, Komprimierungs- oder Zuschneidevorgänge.
   - **statische Bildbereitstellung oder Download** der digitalen Assets oder Ausgabedarstellung digitaler Assets (außer Video)
- **Die Bereitstellung intelligenter Bilder verbraucht 20 Dynamic Media-Vorgänge** für jede optimierte Bereitstellung eines einzelnen digitalen Assets, indem automatisch die am besten geeignete Bildausgabedarstellung für das Gerät und den Browser eines Endbenutzers generiert wird.
- **Die Videobereitstellung beansprucht 20 Dynamic Media** Vorgänge für eine einzelne Bereitstellung oder einen einzelnen Download eines Videos oder einer umgewandelten Variante eines Videos.

>[!ENDSHADEBOX]


### Katalogansichten und Richtlinien

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Katalogansichten | Anzahl der konfigurierbaren Teilmengen des Hauptkatalogs | Basierend auf der Anzahl der [Katalogvarianten](#catalog) | Ja<br>Katalogvarianten erhöhen |
| Richtlinien pro Katalogansicht | Anzahl der zulässigen Datenfilter | 10 | Nein |
| Attributwerte in einer Richtlinie | Anzahl der Produktmerkmale, die für die Filterung konfiguriert werden können | 100 | Nein |

{style="table-layout:auto"}

### Katalog-Storefront

Die Basiszuordnung für die Funktionen der Katalog-Storefront wird auf der Grundlage der GMV-Ebene bestimmt. Die Tabelle zeigt die Mindestzuweisung für jede Funktion an.

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Abrufrate des Katalogs | Anzahl der Aufrufe einer Katalog-API pro Monat durch ein System (Storefront, Transaktionssystem, ERP oder sonstiges), um Daten aus dem Katalog abzurufen | Basierend auf GMV-Stufe<p>Mindestzuweisung: 10 Mio./Monat</p> | Ja<p>1 Million Anfragen pro Monat für Lizenzpakete hinzufügen</p> |
| Inhaltsanfragen | Anfragen an die Commerce-Storefront für HTML-Seitenansichten oder JSON-API-Aufrufe. Wird als 1 Seitenansicht oder 5 API-Aufrufe gezählt. | Basierend auf GMV-Stufe<p>Mindestzuweisung: 2 Mio./Monat</p> | Ja<p>1 Million pro Monat Lizenzpaket hinzufügen</p> |
| Storefront GenAI-Varianten | Toleranz für die textbasierte Inhaltserstellung | Basierend auf GMV-Stufe<p>Mindestzuweisung: 1.000 Varianten/Monat</p> | Ja<p>Generative KI-Credits separat erwerben</p> |

{style="table-layout:auto"}

>[!NOTE]
>
>Für die Bildgenerierung ist eine Adobe Firefly-Lizenz erforderlich, die derselben IMS-Organisation wie Adobe Commerce Optimizer bereitgestellt wird.


### Produkterkennung

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Produkte pro Suchanfrage | Die maximale Anzahl von Produkten, die pro Seite in Suchergebnissen zurückgegeben wird | 100 | Nein |
| Filterbare Attribute | Die Anzahl der Produktmerkmale (z. B. Farbe, Größe, Marke oder Material), die für die mehrschichtige Navigation und Facetten aktiviert werden können | 200 | Nein |
| Durchsuchbare Attribute | Die Anzahl der Produktmerkmale, die für die Verwendung mit dem Produktkatalogsuchdienst konfiguriert werden können | 200 | Nein |
| Sortierbare Attribute | Die Anzahl der Produktmerkmale, die zur Bestimmung der Reihenfolge der Suchergebniswerte konfiguriert werden können | 50 | Nein |
| Paginierungstiefe suchen | Die maximale Anzahl von Produkten, auf die über Paginierung zugegriffen werden kann (z. B. Seite 100 × 100 Produkte/Seite) | 10 K | Nein |
| Facetten | Die Anzahl der filterbaren Produktattribute (wie Marke, Farbe, Größe, Preis), die konfiguriert werden können, um Käufern zu helfen, Suchergebnisse zu verfeinern und Kategorien zu durchsuchen | 100<p>Muss filterbare Attribute sein</p> | Nein |
| Optionen pro Facette | Die Anzahl der filterbaren Produktattributwerte (z. B. „Rot“, „Blau“ für Farbe; „Klein“, &quot;Medium&quot; für Größe), die Käufer aus einer Liste auswählen können | 100 | Ja<p>Kann über eine Support-Anfrage erhöht werden</p> |

{style="table-layout:auto"}

### Recommendations

Die folgenden Funktionen sind für Produktempfehlungen verfügbar. Einige in anderen Adobe Commerce-Produkten verfügbare Funktionen werden in [!DNL Adobe Commerce Optimizer] nicht unterstützt.

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Aktive Empfehlungseinheiten | Anzahl der Live-Empfehlungskomponenten in Ihrer Storefront (z. B. „Kunden haben sich auch angesehen“ oder „Ihnen könnte das auch gefallen„) | 50 | Nein |
| Ein-/Ausschlüsse von Kategorien oder Attributen | Produkte nach einem bestimmten Satz filtern, der für Recommendations geeignet ist | Nicht unterstützt | |
| Recommendations in der Vorschau anzeigen | Vorschau des Erscheinungsbilds von Recommendations vor der Veröffentlichung | Nicht unterstützt | |

{style="table-layout:auto"}

### Erweiterbarkeit

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** | **Hinweise** |
| --- | --- | --- | --- | --- |
| Adobe Developer App Builder | Kapazität zum Erstellen Cloud-nativer Erweiterungen und Integrationen | Basierend auf GMV-Stufe<p>Mindestzuweisung: 1 Packung/Jahr</p> | Ja<p>Zusätzliche Packs hinzufügen</p> | Für die pro Packung definierten Grenzwerte siehe:<ul><li>[App Builder-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-developer-app-builder.html) für pro Pack definierte Beschränkungen.</li><li>[Systemeinstellungen und Einschränkungen](https://developer.adobe.com/app-builder/docs/guides/runtime_guides/system-settings) in den *App Builder Runtime Guides*.</li><li>[Speicheranforderungen für App Builder](https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/storage/)</li></ul> |

{style="table-layout:auto"}

<!--## How to size your solution

Ask your Adobe representative for a list of available packages to determine which most closely matches your project

To accurately size your Adobe Commerce Optimizer solution, follow these steps:

1. Review the available packages, and start with a package that most closely matches your requirements.
1. Review the capabilities and metrics to ensure they align with your business requirements.
1. Purchase add-on packages for any metrics where you require additional capacity.

This approach ensures your solution is accurately sized for your business needs.

### Example use cases

1. **Seasonal Catalog Expansion**

   * Need: +20K SKUs
   * Add-On: 2 × SKU Packs (10K each)

1. **High Traffic Surge**

   * Need: +3M content requests/month
   * Add-On: 3 × content request packs (1M each)

1. **Global Presence**

   * Need: Additional environments for testing
   * Add-On: +1 Production, +2 Sandbox instances

1. **GenAI or Media Needs**

   * Need: +10M dynamic media ops/month
   * Add-On: 10 × dynamic media packs (1M each) -->
