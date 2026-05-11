---
title: Versionshinweise zu Adobe Commerce Optimizer
description: Monatliche Versionsinformationen für [!DNL Adobe Commerce Optimizer] einschließlich Aktualisierungen der Datenaufnahme-REST-API und der GraphQL-API für den Datenabruf im Storefront-Katalog.
feature: Release Notes
role: Admin, Developer, User, Leader
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: e420d461-9ea2-4e32-aa37-230b14a297d7
source-git-commit: 744a85738ab77cb7d1844a353dacab26f30aec5b
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 0%

---

# Versionshinweise

Die folgenden Versionshinweise enthalten Aktualisierungen zu [!DNL Adobe Commerce Optimizer], darunter:

* Neue Funktionen und Verbesserungen in [[!DNL Adobe Commerce Optimizer Studio]](overview.md#quick-tour).
* Aktualisierungen der [Datenaufnahme-REST-API](https://developer.adobe.com/commerce/services/reference/rest/) und der [GraphQL-API für den Datenabruf im Storefront-](https://developer.adobe.com/commerce/services/reference/graphql/).

  {{aco-api-updates-and-dropins}}

## Mai 2026

Derzeit gibt es in diesem Monat keine [[!DNL Adobe Commerce Optimizer Studio]](overview.md#quick-tour) Versionen. Siehe API-Aktualisierungen unten.

>[!BEGINSHADEBOX]

### API-Aktualisierungen

_4. Mai 2026_

<!--v1.53-->

Die Produktpreise der Storefront zeigen jetzt für alle Produkttypen den korrekten Währungscode an (z. B. USD). Zuvor zeigten einige Produkte `NONE` anstelle der erwarteten Währung, was zu fehlenden Preisen führte.

<!--DATA-7115-->

{{aco-release}}

>[!ENDSHADEBOX]

## April 2026

**Veröffentlichungsdatum:**. April 2026

>[!BEGINSHADEBOX]

### Katalogregeln (Betaversion)

[Kategorieregeln](./merchandising/rules/add.md) Erweitern Sie Merchandising-Regeln, damit Sie Kategorien auswählen und die Produktreihenfolge auf Kategorieseiten mit demselben Ranking und denselben Aktionen (Pin, Boost, Bury) wie die Suche steuern können.

### Preisfilter (Beta)

Empfehlungsfilter enthalten jetzt einen [Preisbereichsfilter](./merchandising/recommendations/filters.md#price) (Minimum und Maximum).

### API-Aktualisierungen

_29. April 2026_

<!--v1.52 release-->

**Anfrage-Batching erforderlich** - Die GraphQL-API erzwingt jetzt maximal 100 SKUs pro Anfrage, wenn Sie Katalogdaten abrufen. Siehe [dokumentierte Beschränkungen und &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/optimizer/boundaries-limits#product-discovery).

<!--DATA-7156-->

_17. April 2026_

<!--v1.51 release-->

**Kategorien nach Namen mit GraphQL suchen** - Die neue [`searchCategory`](https://developer.adobe.com/commerce/services/reference/graphql/)-Abfrage gibt übereinstimmende Kategorien mit Paginierung für Storefronts und Integrationen zurück. Parameter und Antwortfelder finden Sie in der API-Referenz. <!--COMOPT-1819-->

_7. April 2026_

<!--v1.50 release-->

**Einfachere Kategoriesuche** - Die [categoryTree](https://developer.adobe.com/commerce/services/graphql-api/merchandising-api/index.html#query-categoryTree)-Abfrage behandelt `family` als optional, sodass Sie Kategorien durch einen Slug auflösen können, ohne eine Familie bereitzustellen.

{{aco-release}}

>[!ENDSHADEBOX]

## März 2026

In diesem Monat wurden keine [[!DNL Adobe Commerce Optimizer Studio]](overview.md#quick-tour) veröffentlicht. Siehe API-Aktualisierungen unten.

>[!BEGINSHADEBOX]

### API-Aktualisierungen

_24. März 2026_

Dynamische Pakete geben jetzt eine berechnete Preisspanne zurück. <!--DATA-7014-->

{{aco-release}}

>[!ENDSHADEBOX]

## Februar 2026

**Veröffentlichungsdatum**: 19. Februar 2026

>[!BEGINSHADEBOX]

### Katalogansicht für Merchandising-Regeln und -Empfehlungen (Beta)

Sie können jetzt eine Katalogansicht angeben, wenn Sie [Empfehlungseinheiten erstellen](./merchandising/recommendations/create.md) oder [Merchandisingregeln](./merchandising/rules/add.md).

### API-Aktualisierungen

_19. Februar 2026_

<!--v1.48-->

**Inhalte mit umfangreicheren Kategorien für Storefronts** - Die [categoryTree](https://developer.adobe.com/commerce/services/graphql-api/merchandising-api/index.html#query-categoryTree)-Abfrage gibt jetzt Beschreibungen, Bilder und SEO-Meta-Tags zurück, damit Storefronts Seiten mit umfangreicheren Kategorien rendern können.<!--DATA-6933-->

_12. Februar 2026_

<!--v1.49-->

**Erweiterte Produktdaten nach Kategorie** - Die GraphQL-API fügt den [`CategoryProductView`](https://developer.adobe.com/commerce/services/graphql-api/merchandising-api/index.html#definition-CategoryProductView){target="blank"} hinzu, damit Sie Produkte mit weniger Roundtrips nach Kategorie abfragen und filtern können.

{{aco-release}}

>[!ENDSHADEBOX]

## Januar 2026

In diesem Monat wurden keine [[!DNL Adobe Commerce Optimizer Studio]](overview.md#quick-tour) veröffentlicht. Siehe API-Aktualisierungen unten.

>[!BEGINSHADEBOX]

### API-Aktualisierungen

_19. Januar 2026_

* **Unterstützung umfangreicherer Kategorien mit der REST-**: [Kategorien-API](https://developer.adobe.com/commerce/services/reference/rest/#operation/createCategories) -Vorgänge akzeptieren jetzt neben `families` auch optionale `metaTags`-, `images`- und `description`-Werte, sodass Sie umfangreichere Merchandising- und SEO-Details für Kategorien bereitstellen können.

{{aco-release}}

>[!ENDSHADEBOX]

## Dezember 2025

**Veröffentlichungsdatum:**. Dezember 2025

>[!BEGINSHADEBOX]

### Opportunities

Merchandiser können jetzt KI-gestützte Empfehlungen über [Adobe Sites Optimizer](./manage-results/opportunities.md) erhalten, um Site-Probleme zu erkennen und Leistungskorrekturen vorzuschlagen.

### Katalogebenen

Merchandiser können jetzt [Katalogebenen](./setup/catalog-layer.md) verwenden, um Produktdaten zu überlagern, ohne den Quellkatalog zu bearbeiten, die Ebenenpriorität zu verwalten und die automatische Fehlerbehebung in Adobe Sites Optimizer zu verwenden.

{{aco-release}}

>[!ENDSHADEBOX]

## November 2025

In diesem Monat wurden keine [[!DNL Adobe Commerce Optimizer Studio]](overview.md#quick-tour) veröffentlicht. Siehe API-Aktualisierungen unten.

>[!BEGINSHADEBOX]

### API-Aktualisierungen

_21. November 2025_

**Aktualisierte Authentifizierungsanweisungen für die Datenaufnahme-REST-API** - Die Anweisungen verweisen jetzt auf OAuth-Zugriffstoken und die richtigen Developer Console-Berechtigungsbereiche für den Datenaufnahme-Service. Wenn Ihre Berechtigungsbereiche veraltet sind, generieren Sie sie neu, um den Zugriff zu behalten.

_3. November 2025_

<!-- v1.43 -->

**Mehrschichtige, lokalisierte Produktinhalte in GraphQL** - Sie können jetzt kanalspezifische, gebietsschemaspezifische Produktinhalte aus [!DNL Adobe Commerce Optimizer] bereitstellen.

* Anpassen von Produktinhalten nach Kundensegment
* Anwenden von gebietsschemaspezifischen Überschreibungen ohne Duplizieren von Basiskatalogdaten
* Überschreibungen auf Feldebene mit Ebenenmasken steuern
* Verwenden von Premium-, saisonalen und für Mobilgeräte optimierten Inhaltsebenen

Keine Änderung des GraphQL-API-Schemas: Ebenen werden über die vorhandenen `products` Abfrage- und Anfrage-Header angewendet. Siehe [Katalogebene](./setup/catalog-layer.md).

{{aco-release}}

>[!ENDSHADEBOX]

## Oktober 2025

**Veröffentlichungsdatum:**. Oktober 2025

>[!BEGINSHADEBOX]

### Commerce Optimizer Salesforce Commerce Connector

Das [!DNL Commerce Optimizer Salesforce Commerce Connector] ist ein neues App Builder-Starter-Kit, das Salesforce B2C Commerce-Katalogdaten in [!DNL Commerce Optimizer] synchronisiert.<!--COMOPT-536-->

**Für Administratoren:**

* Salesforce-Katalogänderungen (Produkte, Preise, Metadaten, Preislisten) werden automatisch mit [!DNL Commerce Optimizer] synchronisiert.
* Läuft außerhalb von [!DNL Adobe Commerce] für weniger Integrations-Touchpoints.
* Geplante Aktualisierungen halten [!DNL Commerce Optimizer] Daten für Merchandising und Recommendations auf dem neuesten Stand.

**Für Entwickler:**

* Erweiterbares Framework für die Aufnahme des Salesforce-Katalogs in SaaS-Merchandising-Services.
* Referenzimplementierungen, Designdokumente und Code-Beispiele für schnellere Builds und die Fehlerbehebung.

### Mehrschichtige Suche

* **Layered Search (GA)** - Die Produktsuche unterstützt jetzt den `startsWith`- und `contains`. Siehe [Mehrschichtige Suche und erweiterte Suchtypen](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#layered-search-and-expansion-of-search-types).

### API-Aktualisierungen

* _17. Oktober 2025_

  **Hinzufügen von REST-API-Unterstützung zur Aufnahme von**: Verwenden Sie die [Catalog Layers API](https://developer.adobe.com/commerce/services/reference/rest/#tag/Product-Layers), um Basisproduktdaten für bestimmte Kontexte, Gebietsschemata oder Geschäftsanforderungen anzupassen und zu überschreiben. Nachdem Sie Ebenen erstellt haben, können Sie sie über [Adobe Commerce Optimizer Studio](./setup/catalog-layer.md) anwenden und verwalten<!--DATA-6632-->

* _14. Oktober 2025_

  **Programmgesteuerte Kategoriestrukturen** - Erstellen, Aktualisieren und Verwalten von Kategoriestrukturen für Navigation und Gruppierung über REST (global oder kanalspezifisch) im benötigten Maßstab - bis zu 10.000 Bäume und 500 Kategorien pro Baum. Siehe [Kategorien](https://developer.adobe.com/commerce/services/reference/rest/#tag/Categories){target="blank"} in der _Catalog Data Ingestion REST API Reference_.<!--DCAT-2649-->

* _8. Oktober 2025_

  **Übersichtlichere Kategoriezuordnung für die Datenaufnahme** - Neue Richtlinien erklären die Format- und Hierarchieregeln von Kategorie-Slug und stellen klar, dass die `routes.path` mit einem vorhandenen Kategorie-Slug übereinstimmen müssen (z. B. `men/clothing`).

{{aco-release}}

>[!ENDSHADEBOX]

## September 2025

In diesem Monat wurden keine [[!DNL Adobe Commerce Optimizer Studio]](overview.md#quick-tour) veröffentlicht. Siehe API-Aktualisierungen unten.

>[!BEGINSHADEBOX]

### API-Aktualisierungen

_23. September 2025_

* **Kategorien mithilfe der REST-API verwalten** - Verwenden Sie die [Kategorien-API](https://developer.adobe.com/commerce/services/reference/rest/#operation/createCategories), um Kategorien zu erstellen und zu verwalten. Kategorien organisieren Produkte in logische Gruppen und unterstützen verschachtelte Hierarchien über Slug-basierte Pfade. Nachdem Sie den Produkten Kategorien zugewiesen haben, rufen Sie sie mit dem GraphQL-`[navigation](https://developer.adobe.com/commerce/services/reference/graphql/#navigation)` ab und `[categoryTree](https://developer.adobe.com/commerce/services/reference/graphql/#categorytree)` Sie Abfragen, um Storefront-Menüs und Kategoriestrukturen zu rendern.<!--DCAT-2626-->

{{aco-release}}

>[!ENDSHADEBOX]

## August 2025

**Veröffentlichungsdatum:**. August 2025

>[!BEGINSHADEBOX]

### EU-Region jetzt verfügbar

Für IMS-Organisationen steht die EU **Produktionsregion** eu1) zur Verfügung. Wenn Sie [eine [!DNL Commerce Optimizer] Instanz“ &#x200B;](./get-started.md#step-1-create-an-instance) Cloud Manager hinzufügen, wählen Sie **[!UICONTROL European Union]** als **[!UICONTROL Region]** aus (nur Produktion).

Die Basis-Produktions-URLs für die Region der Europäischen Union lauten:

* Administrator: `https://eu1.admin.commerce.adobe.com`
* REST und GraphQL: `https://eu1.api.commerce.adobe.com`

![Dialogfeld &quot;Cloud Manager-Instanz erstellen“ mit dem Feld „Region“](./assets/create-instance.png){width="600" align="center" zoomable="yes"}

{{aco-release}}

>[!ENDSHADEBOX]
