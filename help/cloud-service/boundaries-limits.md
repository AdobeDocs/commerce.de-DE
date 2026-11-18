---
title: Adobe Commerce as a Cloud Service-Beschränkungen und -Grenzen
description: Erfahren Sie mehr über Adobe Commerce as a Cloud Service-Lizenzbeschränkungen und Systemgrenzen. Planen Sie die Kapazität, verfolgen Sie die Nutzung und vermeiden Sie Latenz und Drosselung bei Überschreitung der Grenzwerte.
role: Admin, Developer
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und [!DNL Adobe Commerce as a Cloud Service] (von Adobe verwaltete SaaS-Infrastruktur)."
nudge: true
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a13aaee57732f27b51a2d2acdd0ca3de364ee6ab
workflow-type: tm+mt
source-wordcount: '1378'
ht-degree: 1%
---
# Beschränkungen und Grenzen

[!DNL Adobe Commerce as a Cloud Service] wendet **Lizenzbeschränkungen** und **Systemgrenzen** an, die definieren, wie viel Kapazität Ihr Projekt verwenden kann:

- **Lizenzbeschränkungen** basieren auf Ihrer erworbenen Kapazität und können durch den Kauf zusätzlicher Pakete erweitert werden.
- **Systemgrenzen** sind feste Beschränkungen, die Systemressourcen schützen und eine zuverlässige Leistung für alle Benutzer sicherstellen.

>[!IMPORTANT]
>
> Ihre Nutzung muss innerhalb dieser Grenzen bleiben. Sie zu überschreiten kann zu erhöhter Latenz und Anfragebeschränkung führen.

## Zusätzliche Kapazität anfordern

Sie können Ihre Lizenzbeschränkungen erhöhen, indem Sie die Lizenzpakete erwerben, die unter [Lizenzbeschränkungen und Systemgrenzen](#license-limits-and-system-boundaries) beschrieben sind, oder indem Sie benutzerdefinierte Lizenzen für eindeutige Anwendungsfälle aushandeln. Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um Ihre Anforderungen zu besprechen.

Wenden Sie sich bei Fragen zu Systemgrenzen an den [Adobe-Support](https://experienceleague.adobe.com/home?lang=de#support).

## Leistungsprobleme verhindern

Befolgen Sie diese Best Practices, um innerhalb der Beschränkungen zu bleiben und betriebliche Probleme zu vermeiden:

- **Überprüfen Sie Ihre Beschränkungen** - Machen Sie sich mit Ihren [Kapazitätsbeschränkungen](#license-limits-and-system-boundaries) vertraut, bevor Sie neue Storefronts oder Kampagnen starten.
- **Nutzung nachverfolgen** - Verwenden Sie integrierte Metriken-Dashboards oder CDN-Protokolle.

## Lizenzbeschränkungen und Systemgrenzen

In den folgenden Tabellen sind die Lizenzbeschränkungen und Systemgrenzen nach Funktionsbereich zusammengefasst. Sie enthalten gegebenenfalls Informationen zur Verwendung zusätzlicher Lizenzen zur Erweiterung der Kapazität.

### Umgebungsbeschränkungen

| **Umgebung** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| **Sandbox-Umgebung** | Die Anzahl der eingeschlossenen Sandbox-Umgebungen | 2 pro Instanz | Ja<p>Hinzufügen einer zusätzlichen Umgebungslizenz pro Instanz</p> |
| **Produktionsumgebung** | Die Anzahl der eingeschlossenen Produktionsumgebungen | 1 pro Instanz | Ja<p>Hinzufügen einer zusätzlichen Umgebungslizenz pro Instanz</p> |

{style="table-layout:auto"}

### Katalog

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Aufnahmegeschwindigkeit eines Produkts | Die Anzahl der erstellten oder aktualisierten Produkte | 1K Aktualisierungen pro Minute<p>Maximal 100.000 Aktualisierungen pro Tag</p> | Ja<p>Ein Lizenzpaket hinzufügen:</p><ul><li>5.000 Aktualisierungen pro Minute<br>maximal 5.000 Aktualisierungen pro Tag</li><li>10.000 Updates pro Minute<br>maximal 1.000 Updates pro Tag</li></ul><p>Die maximale Kapazität für die Datenaufnahme beträgt 1 Million Aktualisierungen pro Tag.</p> |
| Payload-Größe des Produkts | Die maximale Datenmenge, die beim Erstellen, Aktualisieren oder Aufnehmen von Produktinformationen mithilfe der API zulässig ist | 200 KB | Nein |
| Kategorien | Die Anzahl der Produktkategorien kann wie folgt gruppiert werden: | 6,000 | Nein |
| Anzahl der Produkte | Die Anzahl der im Katalog unterstützten SKUs | 250K SKUs | Ja<p>100K SKU-Lizenzpaket hinzufügen</p> |
| Varianten pro Produkt | Die Anzahl der pro Produkt zulässigen Produktvarianten (Größe, Farbkombinationen) | 10 K | Nein |
| Ansichten speichern | Die Anzahl der Kontexte für die Store-Ansicht (z. B. Gebietsschemata) | 50 | Nein |
| SLA für ein Produkt-Update, das bei der Suche angezeigt werden soll | Zeit, zu der eine Produkterstellung/-aktualisierung bei der Storefront-Suche angezeigt wird | 10 - 15 Minuten | Nein |

{style="table-layout:auto"}

### Checkout

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Produkte im Warenkorb | Die Anzahl der pro Warenkorb zulässigen Produkte | 650 | Nein |
| Kundenadressen pro Konto | Die Anzahl der pro Konto zulässigen Kundenadressen | 2,000 | Nein |
| Warenkorb-Preisregeln | Die Anzahl der Regeln für den Warenkorbpreis, die Rabatte auf Artikel im Warenkorb anwenden, basierend auf einer Reihe von Bedingungen | 100,000 | Nein |
| Coupons | Die Anzahl der Couponcodes, die mit Warenkorbpreisregeln verwendet werden | 1,000,000 | Nein |

{style="table-layout:auto"}

<!--
# Price books

# | **Capability** | **Description** | **Base allocation** | **Expandable?** |
# | --- | --- | --- | --- |
# | Price books | The number of price books allowed per instance | Based on the number of [Catalog variations](#catalog) | Yes<br>Increase catalog variations |
# | Discounts per price record | The number of discounts that can be applied to a product price within a single price book | 10 | No |

{style="table-layout:auto"}
-->

### [!DNL Product Visuals]

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Produktvisualisierung Power-User | Lizenzierter Anwender mit vollständigen Digital-Asset-Management-Funktionen, einschließlich KI-Tools, [!DNL Adobe Express]-/[!DNL Firefly]-Integrationen und Content Hub-Freigabe, Handhabung von DAM-Kernaufgaben und erweiterten Cloud-nativen Funktionen für optimale Effizienz. | 2 | Ja<p>Upgrade auf [!DNL AEM Assets] Lizenz</p> |
| Benutzer von Product Visuals Collaborator | Greifen Sie über die AEM Commerce-Integration auf Assets zu und arbeiten Sie mit ihnen, erstellen und bearbeiten Sie Inhalte mithilfe von [!DNL Adobe Express] und [!DNL Firefly] und nutzen Sie - falls aktiviert - genehmigte Assets über das Content Hub-Portal. | 2 | Ja<p>Upgrade auf [!DNL AEM Assets] Lizenz</p> |
| Speicherung von Produktbildern | Zugewiesener Speicherplatz für Assets | 1 TB Speicher | Nein |
| Verwendung von Dynamic Media | Toleranz für Dynamic Media-Verarbeitungsvorgänge, die Folgendes umfassen:<ul><li>Bildbereitstellung</li><li>Intelligente Bildbearbeitung</li><li>Videowiedergabe</li></ul><p>Weitere Informationen finden Sie *Berechnen der Dynamic Media-Nutzung* unten. | Basierend auf GMV (Bruttowarenwert)<p>Mindestzuweisung: 5 Mio. Operationen/Monat</p> | Ja<ul><li>Lizenz für zusätzliche Vorgänge erwerben</li><li>Upgrade auf [!DNL AEM Assets] Lizenz</li></ul> |
| Videobereitstellung | Toleranz für Videobereitstellung oder Downloads | 300 Videos, 1 Minute pro Video | Ja<p>Upgrade auf [!DNL AEM Assets] Lizenz</p> |
| Asset-Generierung | Zugriff auf [!DNL Adobe Express] und [!DNL Adobe Firefly] generative KI zum Erstellen von Bildern | Keine | Generative KI-Credits separat erwerben |

{style="table-layout:auto"}

>[!NOTE]
>
>**Power Users** können direkt oder innerhalb von [!DNL Adobe Commerce as a Cloud Service] auf [!DNL Adobe Express] zugreifen.
>
>**Collaborator-Benutzer** können direkt auf das [!DNL Adobe Express]-Programm zugreifen. Die Nutzung wird durch die [Adobe Express mit Firefly-spezifischen Lizenzbedingungen geregelt](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeExpressWFirefly-WW-2025v1.pdf).

>[!BEGINSHADEBOX „Berechnen der Dynamic Media-Nutzung“]

Die Verwendung von Dynamic Media verfolgt API-Anfragen, die innerhalb von [!DNL Adobe Commerce as a Cloud Service] in die Komponenten für visuelle Produktinformationen gelangen, um eine der folgenden Aktionen zu erleichtern:

- **Die Bildbereitstellung verbraucht einen Dynamic Media** Vorgang für jedes Vorkommen der folgenden:
  - **Grundlegende Bildumwandlung** eines digitalen Assets, z. B. Größenänderungs-, Skalierungs-, Formatkonvertierungs-, Komprimierungs- oder Zuschneidevorgänge.
  - **statische Bildbereitstellung oder Herunterladen** der digitalen Assets oder Ausgabedarstellung digitaler Assets (außer Video).
- **Die Bereitstellung intelligenter Bilder verbraucht 20 Dynamic Media-Vorgänge** für jede optimierte Bereitstellung eines einzelnen digitalen Assets, indem automatisch die am besten geeignete Bildausgabedarstellung für das Gerät und den Browser eines Endbenutzers generiert wird.
- **Die Videobereitstellung beansprucht 20 Dynamic Media** Vorgänge für eine einzelne Bereitstellung oder einen einzelnen Download eines Videos oder einer umgewandelten Variante eines Videos.

>[!ENDSHADEBOX]

>[!NOTE]
>
>Die oben genannten Beschränkungen betreffen die Zuweisung von Kapazität und Nutzung. Eine Übersicht über die Produktvisualisierungsfunktionen und funktionale Einschränkungen finden Sie unter [Produktvisualisierung mit AEM Assets](../optimizer/setup/product-visuals.md).

<!--
### Catalog views and policies

| **Capability** | **Description** | **Base allocation** | **Expandable?** |
| --- | --- | --- | --- |
| Catalog views | Number of configurable subsets of your master catalog | Based on the number of [Catalog variations](#catalog) | Yes<br>Increase catalog variations |
| Policies per catalog view | Number of data filters allowed | 10 | No |
| Attribute values in a policy | Number of product characteristics that can be configured for filtering | 100 | No |
| [Restricted access key assignment](setup/private-catalog-view.md) | Number of restricted access keys that can be assigned to a single catalog view | 3 | No |
| RSA key size (restricted access keys) | Minimum and maximum key strength accepted for a restricted access key | 2048-bit minimum, 8192-bit maximum | No |
| Restricted access keys | Key revocation propagation delay | Up to 5 minutes, due to caching. Tokens signed by a removed key are denied once the delay elapses. | Not applicable |

{style="table-layout:auto"}
-->

### Katalog-Storefront

Die Basiszuweisung für die Funktionen der Katalog-Storefront wird auf der Grundlage der GMV-Stufe (Bruttowarenwert) bestimmt. Die Tabelle zeigt die Mindestzuweisung für jede Funktion an.

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Abrufrate des Katalogs | Anzahl der Aufrufe einer Katalog-API pro Monat durch ein System (Storefront, Transaktionssystem, ERP oder sonstiges), um Daten aus dem Katalog abzurufen | Basierend auf GMV-Stufe<p>Mindestzuweisung: 10 Mio./Monat</p> | Ja<p>1 Million Anfragen pro Monat für Lizenzpakete hinzufügen</p> |
| Inhaltsanfragen | Anfragen an die Storefront für HTML-Seitenansichten oder JSON-API-Aufrufe. Wird als 1 Seitenansicht oder 5 API-Aufrufe gezählt. | Basierend auf GMV-Stufe<p>Mindestzuweisung: 2 Mio. pro Monat</p> | Ja<p>1 Million pro Monat Lizenzpaket hinzufügen</p> |
| Storefront GenAI-Varianten | Toleranz für die textbasierte Inhaltserstellung | Basierend auf GMV-Stufe<p>Mindestzuweisung: 1.000 Varianten/Monat</p> | Ja<p>Generative KI-Credits separat erwerben</p> |

{style="table-layout:auto"}

>[!NOTE]
>
>Für die Bildgenerierung ist eine [!DNL Adobe Firefly]-Lizenz erforderlich, die für dieselbe IMS-Organisation wie [!DNL Adobe Commerce as a Cloud Service] bereitgestellt wird.

### Produkterkennung

Die folgenden Einschränkungen gelten für die Storefront-Produktsuche, -Auflistung und -Merchandising-Konfiguration.

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- |---------------------------------------------------|
| Produktabruf | Maximale SKUs pro [!DNL Catalog Service] GraphQL-Anfrage beim Abrufen von Produktdaten mit `products`, `productSearch`, `refineProduct` und `variants`. Teilen Sie größere Anfragen auf mehrere Aufrufe auf. | 100 | Nein |
| Filterbare Attribute | Die Anzahl der Produktmerkmale (z. B. Farbe, Größe, Marke oder Material), die für die mehrschichtige Navigation und Facetten aktiviert werden können | 200 | Nein |
| Durchsuchbare Attribute | Die Anzahl der Produktmerkmale, die für die Katalogsuche indiziert werden können | 200 | Nein |
| Sortierbare Attribute | Die Anzahl der Produktmerkmale, die als Sortieroptionen auf Such- und Kategorieseiten verfügbar sind. | 50 | Nein |
| Paginierungstiefe suchen | Maximal erreichbare Produkte durch Suchpaginierung (z. B. Seite 100 × 100 Produkte/Seite) | 10 K | Nein |
| Facetten | Die Anzahl der filterbaren Produktattribute (wie Marke, Farbe, Größe, Preis), die konfiguriert werden können, um Käufern zu helfen, Suchergebnisse zu verfeinern und Kategorien zu durchsuchen | 100<p>Muss filterbare Attribute sein</p> | Ja<p>Kann über eine Support-Anfrage auf 500 erhöht werden</p> |
| Optionen pro Facette | Die Anzahl der filterbaren Produktattributwerte, die Käufer innerhalb einer Facette auswählen können (z. B. „Rot“, „Blau“ für Farbe; „Klein“, &quot;Medium&quot; für Größe) | 100 | Ja<p>Kann über eine Support-Anfrage erhöht werden</p> |

{style="table-layout:auto"}

### Recommendations

Die folgenden Funktionen sind für Produktempfehlungen verfügbar. Einige in anderen Adobe Commerce-Produkten verfügbare Funktionen werden in [!DNL Adobe Commerce as a Cloud Service] nicht unterstützt.

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** |
| --- | --- | --- | --- |
| Aktive Empfehlungseinheiten | Anzahl der Live-Empfehlungskomponenten in Ihrer Storefront (z. B. „Kunden haben sich auch angesehen“ oder „Ihnen könnte das auch gefallen„) | 50 aktive Einheiten pro Seitentyp für Produktempfehlungen, bei Bedarf mit expliziter Berechnung für Katalogmodelle | Nein |

{style="table-layout:auto"}
<!-- Talos complained about this even thought it was copied directly from the ACO version of this page. Commenting out for now, | Category or attribute inclusions/exclusions | Filter products to a specific set that qualifies for recommendations | Not supported | — | -->

### Erweiterbarkeit

| **Funktion** | **Beschreibung** | **Basiszuweisung** | **Erweiterbar?** | **Hinweise** |
| --- | --- | --- | --- | --- |
| Adobe Developer App Builder | Kapazität zum Erstellen Cloud-nativer Erweiterungen und Integrationen | Basierend auf GMV-Stufe<p>Mindestzuweisung: 1 Packung/Jahr</p> | Ja<p>Zusätzliche Packs hinzufügen</p> | Für die pro Packung definierten Grenzwerte siehe:<ul><li>[App Builder-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-developer-app-builder.html).</li><li>[Systemeinstellungen und Einschränkungen](https://developer.adobe.com/app-builder/docs/guides/runtime_guides/system-settings) in den *App Builder Runtime Guides*.</li><li>[Speicheranforderungen für App Builder](https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/storage/)</li></ul> |

{style="table-layout:auto"}

<!--
## How to size your solution

Ask your Adobe representative for a list of available packages to determine which most closely matches your project

To accurately size your [!DNL Adobe Commerce as a Cloud Service] solution, follow these steps:

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
   * Add-On: 10 × dynamic media packs (1M each)
-->
