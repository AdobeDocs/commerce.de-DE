---
title: Versionshinweise zu Adobe Commerce Optimizer
description: Monatliche Versionsinformationen für [!DNL Adobe Commerce Optimizer] einschließlich Aktualisierungen der Datenaufnahme-REST-API und der GraphQL-API für den Datenabruf im Storefront-Katalog.
feature: Release Notes
role: Admin, Developer, User, Leader
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: e420d461-9ea2-4e32-aa37-230b14a297d7
TQID: https://experienceleague.adobe.com/apcpxN0AOniRcHDCa5MMAVWysxRO5mTcudXXXjET-Lo
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 70f219ca854a0df0ac16ed31116ba9c510eebec2
workflow-type: tm+mt
source-wordcount: 1316
ht-degree: 0%

---

# Versionshinweise

Die folgenden Versionshinweise enthalten Aktualisierungen zu [!DNL Adobe Commerce Optimizer], darunter:

* Neue Funktionen und Verbesserungen in [[!DNL Adobe Commerce Optimizer Studio]](overview.md#quick-tour).
* Aktualisierungen der [Datenaufnahme-REST-API](https://developer.adobe.com/commerce/services/reference/rest/) und der [GraphQL-API für den Datenabruf im Storefront-](https://developer.adobe.com/commerce/services/reference/graphql/).

  {{aco-api-updates-and-dropins}}

## Juni 2026

>[!BEGINSHADEBOX]

### Semantische Suche

[!DNL Adobe Commerce Optimizer] unterstützt jetzt **[semantische Suche]** auf der Registerkarte [**Erweiterte Suche**](./settings.md#advanced-search) in **[!UICONTROL Settings]**. Die semantische Suche verwendet KI, um Produkte anhand von Bedeutung und Kontext neben der Keyword-Suche abzugleichen, wodurch die Anzahl leerer Suchseiten für Abfragen in natürlicher Sprache reduziert wird. Sie ist standardmäßig für geeignete englische Kataloge aktiviert. Sie können optional **[!UICONTROL Semantic boost]**, **[!UICONTROL Similarity threshold]** und **[!UICONTROL Fuzzy search]** auf derselben Registerkarte anpassen. Es sind keine Änderungen an der Attributeinrichtung oder der Storefront erforderlich. [Weitere Informationen](./setup/semantic-search.md).

### Preisfilter für Empfehlungen (Betaversion)

Produktempfehlungseinheiten unterstützen jetzt [**Preisfilter**](./merchandising/recommendations/filters.md#price) im **[!UICONTROL Filter products]**. Schließen Sie Kandidaten mithilfe von **static** Mindest- und Höchstbereichen oder **dynamic**-Regeln auf der Produktdetailseite ein, die empfohlene Produkte mit dem aktuell angezeigten Produkt (**berechneten Endpreis** aus dem aktiven Preisbuch der Storefront vergleichen. Preisregeln filtern das Kandidatenset. Produkte werden nicht neu eingestuft. [Weitere Informationen](./merchandising/recommendations/filters.md#price).

{{aco-release}}

>[!ENDSHADEBOX]

## Mai 2026

>[!BEGINSHADEBOX]

### Intelligente Ranking-Optimierung

[Merchandising-Regeln](./merchandising/rules/add.md#intelligent-ranking-boost) für Suche, Standardproduktlisten und [Kategorieseiten](./merchandising/rules/add.md#rule-types) enthalten jetzt **[!UICONTROL Intelligent Ranking Boost]**. Sie können anpassen, wie stark Strategien wie **Am häufigsten angezeigt** oder **Trend** die Produktreihenfolge in Bezug auf die textliche Relevanz bei Such- und Verhaltenssignalen in Kategorielisten beeinflussen. Die Regelvorschau spiegelt Ihre Einstellung wider. Die Steigerung wird zur Abfragezeit angewendet, sodass Sie keine erneute Synchronisierung des Katalogs benötigen, wenn Sie Änderungen daran vornehmen.

### API-Aktualisierungen

_28. Mai 2026_

<!-- v1.2 -->

![Korrigieren](../assets/fix.svg) **Vollständige Navigationsbäume** - Getaggte untergeordnete Kategorien werden jetzt korrekt in familiengefilterten `navigation` eingefügt, wenn ein nicht getaggter Zwischenknoten im Pfad vorhanden ist. Diese Fehlerbehebung stellt sicher, dass Käufern alle relevanten Kategorien in der Navigation angezeigt werden, sodass sie leichter durchsuchen und Artikel finden können.
<!--DATA-7183-->

![Beheben](../assets/fix.svg) **Leere Slug-Verarbeitung in `categoryTree`-**: Es wurde ein Problem behoben, bei dem die [`categoryTree`](https://developer.adobe.com/commerce/services/graphql-api/merchandising-api/index.html#query-categoryTree)-Abfrage einen internen Server-Fehler zurückgab, wenn das `slugs`-Argument eine leere Zeichenfolge enthielt. Leere Slug-Werte werden jetzt ignoriert, sodass Storefronts und Integrationen Kategoriedaten ohne fehlgeschlagene Anfragen auflösen können.
<!--DATA-7184-->

![Beheben](../assets/fix.svg) **`searchCategory`Anfragen geben Ergebnisse zurück, bei denen nicht zwischen Groß- und Kleinschreibung unterschieden wird** - Die `searchCategory` Abfrage sortiert Suchergebnisse jetzt alphabetisch ohne Unterscheidung zwischen Groß- und Kleinschreibung, was eine konsistente und vorhersehbare Reihenfolge gewährleistet. Kategorien mit kürzeren Präfixen werden zuerst angezeigt, wenn die Namen ansonsten identisch sind.
<!--COMOPT-2142-->

_4. Mai 2026_

<!--v1.53-->

**Korrekte Währungsanzeige** - Die Produktpreise der Storefront zeigen jetzt den korrekten Währungscode (z. B. USD) für alle Produkttypen an. Zuvor zeigten einige Produkte `NONE` anstelle der erwarteten Währung, was zu fehlenden Preisen führte.

<!--DATA-7115-->

{{aco-release}}

>[!ENDSHADEBOX]

## April 2026

**Veröffentlichungsdatum:**. April 2026

>[!BEGINSHADEBOX]

### Katalogregeln

[Kategorieregeln](./merchandising/rules/add.md) Erweitern Sie Merchandising-Regeln, damit Sie Kategorien auswählen und die Produktreihenfolge auf Kategorieseiten mit demselben Ranking und denselben Aktionen (Pin, Boost, Bury) wie die Suche steuern können.

### Preisfilter (Beta)

Empfehlungsfilter enthalten jetzt einen [Preisbereichsfilter](./merchandising/recommendations/filters.md#price) (Minimum und Maximum).

### API-Aktualisierungen

_29. April 2026_

<!--v1.52 release-->

**Anfrage-Batching erforderlich** - Die GraphQL-API erzwingt jetzt maximal 100 SKUs pro Anfrage, wenn Sie Katalogdaten abrufen. Siehe [dokumentierte Beschränkungen und ](https://experienceleague.adobe.com/en/docs/commerce/optimizer/boundaries-limits#product-discovery).

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

### Katalogansicht für Merchandising-Regeln und -Empfehlungen

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

Für IMS-Organisationen steht die EU **Produktionsregion** eu1) zur Verfügung. Wenn Sie [eine [!DNL Commerce Optimizer] Instanz“ ](./get-started.md#step-1-create-an-instance) Cloud Manager hinzufügen, wählen Sie **[!UICONTROL European Union]** als **[!UICONTROL Region]** aus (nur Produktion).

Die Basis-Produktions-URLs für die Region der Europäischen Union lauten:

* Administrator: `https://eu1.admin.commerce.adobe.com`
* REST und GraphQL: `https://eu1.api.commerce.adobe.com`

![Dialogfeld &quot;Cloud Manager-Instanz erstellen“ mit dem Feld „Region“](./assets/create-instance.png){width="600" align="center" zoomable="yes"}

{{aco-release}}

>[!ENDSHADEBOX]
