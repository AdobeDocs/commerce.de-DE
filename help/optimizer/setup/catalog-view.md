---
title: Katalogansicht
description: Erfahren Sie, was Katalogansichten sind und wie Sie sie erstellen, um Ihren Produktkatalog nach Geschäftsstruktur, Richtlinien und Preisen zu organisieren.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 76c1b81c-b456-4334-89bd-6027308cbc47
source-git-commit: 769aafeb261d978623e68c466888924c92632883
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---


# Katalogansichten für Merchandising-Services

Katalogansichten sind die Grundlage von Adobe Commerce Optimizer Merchandising Services und ermöglichen es Ihnen, Ihren Produktkatalog nach Geschäftsstruktur, Richtlinien und Preisen zu organisieren. Dieses flexible Datenmodell unterstützt Szenarien mit mehreren Marken, mehreren Geschäftseinheiten und mehreren Sprachen bei gleichzeitiger Wahrung der betrieblichen Effizienz.

## Was sind Katalogansichten?

Katalogansichten definieren, wie Ihr Produktkatalog organisiert und angezeigt wird. Sie dienen als Filter, die Folgendes bestimmen:

- **Welche Produkte sichtbar sind** basierend auf der Unternehmensstruktur (Marken, Regionen, Händler)
- **Welche Preise werden angezeigt** durch verknüpfte Preisbücher
- **Filterung von Produkten** Verwendung von Richtlinien (Attribute wie Marke, Modell, Kategorie)
- **Welche Katalogquelle verwendet wird** basierend auf Attributen wie „locale“

Stellen Sie sich Katalogansichten als verschiedene „Linsen“ vor, durch die Kunden Ihren Katalog sehen. Beispiel:

- In einer Händlerkatalogansicht werden möglicherweise nur Produkte angezeigt, die für diesen Händler verfügbar sind
- In einer regionalen Katalogansicht können Produkte und Preise angezeigt werden, die für ein geografisches Gebiet spezifisch sind
- In einer Markenkatalogansicht werden möglicherweise nur Produkte einer bestimmten Marke angezeigt

## Erstellen einer Katalogansicht

In diesem Abschnitt erstellen Sie eine Katalogansicht, wählen eine [Richtlinie](policies.md) und ein [Preisbuch](pricebooks.md).

Bevor Sie eine Katalogansicht erstellen, stellen Sie sicher, dass Sie Folgendes haben:

- [Erstellte Richtlinien](policies.md) um Produktfilter zu definieren.

- [Definierte Katalogebenen](catalog-layer.md) um Varianten Ihrer Produkte zu definieren.

- [Aufgenommene Preisbücher](pricebooks.md) für die Preisgestaltung.

1. Navigieren Sie im linken Menü zu _Store-Einrichtung_ und klicken Sie auf **[!UICONTROL Catalog views]**.

1. Klicken Sie auf **[!UICONTROL Create catalog view]**. &#x200B;

1. Konfigurieren Sie die Details der Katalogansicht:

   - **Name** - Geben Sie den Namen der Katalogansicht ein, z. B. `Celport`. &#x200B;
   - **Katalogquellen** - Wählen Sie die Katalogquelle (Gebietsschema) aus, z. B. `en-US`.
   - **Katalogebenen** Überprüfen der aufgenommenen Ebenen und der Priorität.
   - **Richtlinien** - Wählen Sie in der Dropdown-Liste die entsprechenden Richtlinien aus. Beispiel: „Marke“, „Modell“. &#x200B;Stellen Sie sicher, dass Sie bereits [eine Richtlinie erstellt haben](policies.md).

1. Wählen Sie das Preisbuch aus, das mit der Katalogansicht verknüpft werden soll.

   - **Alle verfügbaren Preisverzeichnisse verwenden** - Mit dieser Option werden die Preisdaten aus allen verfügbaren Preisverzeichnissen abgerufen.
   - **Nur ausgewählte Preisbücher zulassen** - Mit dieser Option wird das Dialogfeld **Zulässige Preisbücher hinzufügen** angezeigt, in dem Sie auswählen können, welches spezifische Preisbuch für die Katalogansicht verwendet werden soll.
   - **Preise deaktivieren**-Diese Option ist derzeit nicht verfügbar.

1. Klicken Sie auf **[!UICONTROL Add]** , um die Katalogansicht mit den verknüpften Preisbüchern und Richtlinien zu erstellen.

Die Seite mit den Katalogansichten wird aktualisiert, um die neue Katalogansicht anzuzeigen&#x200B;

Nachdem Sie diese Schritte ausgeführt haben, ist die Katalogansicht jetzt so konfiguriert, dass Produkte und Preise basierend auf Ihren ausgewählten Quellen und Richtlinien angezeigt werden.

## Katalogebenen

Mit Katalogebenen können Sie Produktdaten in einer Katalogansicht ändern, ohne die ursprünglichen Quelldaten zu ändern. Ebenen wenden Änderungen an bestimmten Produktattributen an, z. B. Name, Beschreibung, Bilder, Links und Metadaten, indem eine Ebene über Ihrem Basiskatalog erstellt wird. Ihre ursprünglichen Produktdaten bleiben intakt, sodass Sie Produkte sicher anpassen und Änderungen jederzeit rückgängig machen können.

Häufige Anwendungsfälle für Katalogebenen sind:

- **SEO-Optimierung** - Überschreiben von Produktmetadaten-Titeln und -Beschreibungen basierend auf KI-Empfehlungen von [Sites Optimizer](../manage-results/opportunities.md)
- **Saisonale Kampagnen** - Aktualisieren Sie vorübergehend Produktnamen, Beschreibungen oder Bilder für Werbeaktionen
- **Regionale Anpassung** - Anzeige unterschiedlicher Produktinformationen basierend auf geografischem Standort oder Sprache
- **A/B-Tests** - Testen Sie verschiedene Produktpräsentationen, um die Konversionsraten zu optimieren
- **Mehrmarken-Management** - Passen Sie Produktattribute für verschiedene Ansichten des Markenkatalogs an.

Weitere Informationen zum Erstellen, Verwalten und Priorisieren von Katalogebenen finden Sie unter [Katalogebenen](catalog-layer.md).

## Katalogansicht verwalten

Befolgen Sie diese Anweisungen, um die Eigenschaften vorhandener Katalogansichten zu aktualisieren oder anzuzeigen.

### Katalogansicht bearbeiten

1. Suchen Sie im Arbeitsbereich *Katalogansichten* die Katalogansicht in dem Raster, das Sie bearbeiten möchten, und klicken Sie auf **…**, um das Aktionsmenü zu öffnen.
1. Klicken Sie **Bearbeiten**, um auf den Editor für die Katalogansicht zuzugreifen.
1. Aktualisieren Sie den Namen, die Katalogquellen, Richtlinien und Preisbuchinformationen nach Bedarf.
1. Speichern Sie die Änderungen.

### Katalogansicht löschen

1. Suchen Sie im Arbeitsbereich *Katalogansichten* die Katalogansicht in dem Raster, das Sie bearbeiten möchten, und klicken Sie auf **…**, um das Aktionsmenü zu öffnen.
1. Klicken Sie **Löschen**.

   Wenn das Bestätigungsdialogfeld angezeigt wird, klicken Sie auf **[!UICONTROL Delete]**.

### Details anzeigen

Diese Option bietet eine schnelle Möglichkeit, alle Parameter der Katalogansicht anzuzeigen, während Sie in der Tabelle *Katalogansichten* bleiben.

Suchen Sie im Arbeitsbereich *Katalogansichten* die Katalogansicht in dem Raster, das Sie bearbeiten möchten, und klicken Sie auf das Symbol ![Informationen](../assets/info-icon.png).

![Details zur Katalogansicht](../assets/catalog-view-details.png)

Von hier aus können Sie Konfigurationsdetails der Katalogansicht sehen, z. B.:

- Ansichts-ID
- -Name
- Katalogquellen
- Richtlinien
- Erstellt am
- Data Modified

Einige dieser Konfigurationseinstellungen werden benötigt, wenn Sie Ihre Storefront einrichten oder die Datenerfassungs-API verwenden.

## Überblick über die Architektur

Katalogansichten sind Teil des Merchandising Services-Frameworks, das das in Adobe Commerce Foundations verwendete Website-, Store- und Store-Review-Framework durch ein flexibleres Modell ersetzt:

![[!DNL Merchandising Services] Architektur](../assets/merchandising-svcs-architecture.png)

### Funktionsweise

**1. Datenaufnahme**
Katalogdaten aus PIM, ERP und anderen Systemen werden in das Merchandising Services-Framework aufgenommen. Jede SKU enthält Gebietsschema-Informationen und Produktattribute, die Katalogansichten, Richtlinien und Gebietsschemata zugeordnet sind. Weitere Informationen zur Datenaufnahme finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/).

**2. Unified Base Catalog**
Die erfassten Daten erstellen einen einheitlichen Basiskatalog in der Katalog-Service-Datenpipeline. Durch diese zentrale Quelle werden Datenduplikate in allen Geschäftsbereichen vermieden.

**3. Katalogansichten**
Mehrere Katalogansichten stellen verschiedene Geschäftseinheiten dar (z. B. „Texas Retail“, „Texas Retail Seasonal„). Gebietsschemata, Richtlinien und Preisverzeichnisse können aus Gründen der Flexibilität über Katalogansichten hinweg gemeinsam genutzt werden.

**4. Multi-Channel-Versand**
Die gefilterten Katalogdaten werden für verschiedene Ziele bereitgestellt, einschließlich Edge Delivery Services-Storefronts, Marktplätzen, Werbeplattformen und benutzerdefinierten Mikro-Storefronts. Weitere Informationen zur Bereitstellung von Katalogdaten finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/).

### Schlüsselkomponenten

| Komponente | Zweck | Beispiel |
|---|---|---|
| **Katalogansicht** | Geschäftseinheit oder Vertriebskanal | Händlernetzwerk, regionaler Store |
| **Richtlinie** | Produktfilter basierend auf Attributen | Marke, Modell, Kategorie |
| **Gebietsschema** | Einstellung für Sprache/Region | en-US, fr-CA, es-MX |
| **Preisbuch** | Preisstruktur | Einzelhandel, Großhandel, Mitarbeiter |

### Datenfluss

1. **Aufnehmen** - Produktdaten aus PIM/ERP-Systemen
2. **Prozess** - Anwenden von Katalogansichten, Richtlinien und Preisen
3. **Versand** - Bereitstellung eines gefilterten Katalogs an Storefronts, Marktplätze usw.

## Wichtigste Funktionen

| Funktion | Vorteil |
|---|---|
| **Single Base Catalog** | Eliminierung von Datenduplikaten in allen Geschäftsbereichen |
| **Flexible Preisgestaltung** | Mehrere Preisbücher pro SKU für verschiedene Kundensegmente |
| **skalierbar** | Effiziente Verwaltung von mehr als 200 Millionen SKUs |
| **Multi-Channel** | Kataloge für Storefronts, Marktplätze und Werbeplattformen bereitstellen |
| **Echtzeit-Updates** | Schnelles Aktualisieren von Katalogdaten für Promotions und Kampagnen |

## Anwendungsszenarien

### Mehrmarkenkonglomerat

**Challenge**: Verwaltung mehrerer Marken, Länder und Sprachen<br>
**Lösung**: Einzelner Katalog mit Katalogansichten für jede Kombination aus Marke und Region

### Autoteilehändler

**Challenge**: 3.000 Händler mit den gleichen Produkten, aber unterschiedlichen Preisen<br>
**Lösung**: Ein Katalog mit händlerspezifischen Katalogansichten und Preisbüchern

### Retailer mit mehreren Standorten

**Challenge**: Unterschiedliche Preise und Lagerbestände pro Standort<br>
**Lösung**: Standortbasierte Katalogansichten mit regionsspezifischen Richtlinien

>[!INFO]
>
>Detaillierte Informationen zur Aufnahme und Bereitstellung von Katalogdaten finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/).

## Ähnliche Themen

- [Katalogebenen](catalog-layer.md) Erfahren Sie, wie Sie Produktdaten ändern, ohne die ursprüngliche Quelle zu ändern
- [Richtlinien](policies.md) - Erstellen von Richtlinien zum Filtern von Produkten in Katalogansichten
- [Preisbücher](pricebooks.md) - Verwalten von Preisstrukturen für verschiedene Kundensegmente
