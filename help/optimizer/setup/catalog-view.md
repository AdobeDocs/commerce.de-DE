---
title: Katalogansicht
description: Erfahren Sie, wie Sie in Katalogansichten erstellen und verwalten [!DNL Adobe Commerce Optimizer].
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 553490762ef10e43ccce1654acec59aeb83bb5f9
workflow-type: tm+mt
source-wordcount: '1896'
ht-degree: 0%

---

# Katalogansicht erstellen

[Katalogansichten](#catalog-views) helfen Ihnen, Ihre Einzelhandelsstruktur in aussagekräftige Geschäftsgruppen zu definieren. Eine Katalogansicht beeinflusst die Sichtbarkeit von Produkten, indem bestimmte Richtlinien und Filter angewendet werden, die bestimmen, welche Produkte in einer Storefront angezeigt werden. Diese Richtlinien können Attribute wie Marke, Modell oder Teilekategorie enthalten, sodass basierend auf der Konfiguration der Katalogansicht nur relevante Produkte für den Käufer sichtbar sind. Darüber hinaus können Katalogansichten Preislisten verwenden, um kundenspezifische Preise anzuzeigen und so das Einkaufserlebnis weiter anzupassen. [Weitere Informationen](#catalog-views) über Katalogansichten.

In diesem Abschnitt erstellen Sie eine Katalogansicht, wählen eine [Richtlinie](policies.md) und ein [Preisbuch](pricebooks.md).

1. Navigieren Sie im linken Menü zu _Store-Setup_ und klicken Sie auf **[!UICONTROL Catalog views]**.

1. Klicken Sie auf **[!UICONTROL Create catalog view]**. &#x200B;

1. Fügen Sie die Details der Katalogansicht hinzu:

   - **Name** - Geben Sie den Namen der Katalogansicht ein. Beispiel: „Celport“. &#x200B;
   - **Katalogquellen** - Fügen Sie die Katalogquelle (Gebietsschema) hinzu. Beispiel: „en-US“. Drücken Sie die **Eingabetaste**.
   - **Richtlinien** - Wählen Sie in der Dropdown-Liste die entsprechenden Richtlinien aus. Beispiel: „Marke“, „Modell“. &#x200B;Stellen Sie sicher, dass Sie bereits [eine Richtlinie erstellt haben](policies.md).

1. Wählen Sie das Preisbuch aus, das mit Ihrer Katalogansicht verknüpft werden soll. Weitere Informationen über [Preisbücher](pricebooks.md).

1. Klicken Sie auf **[!UICONTROL Add]** , um die Katalogansicht mit dem verknüpften Preisbuch und den verknüpften Richtlinien zu erstellen.

   Wenn die Schaltfläche **[!UICONTROL Add]** nicht aktiv ist, stellen Sie sicher, dass die Katalogquelle ordnungsgemäß hinzugefügt wird, indem Sie den Cursor in das Feld Katalogquellen einfügen und die **Eingabetaste** drücken. &#x200B;

Die Seite mit den Katalogansichten wird aktualisiert, um die neue Katalogansicht anzuzeigen&#x200B;

Nachdem Sie diese Schritte abgeschlossen haben, wird die neue Katalogansicht so konfiguriert, dass Produkte und Preise basierend auf den ausgewählten Katalogquellen und Richtlinien angezeigt werden.

## Katalogansichten

Ein Produktkatalog ist für Online-Shopping-Erlebnisse von entscheidender Bedeutung, da Kunden ihn durchsuchen, suchen und Käufe tätigen können. Um die betriebliche Effizienz zu gewährleisten, sollte ein Produktkatalog die Geschäftsstruktur des Unternehmens genau widerspiegeln. Unternehmen müssen Produkte oft zu unterschiedlichen Preisen verkaufen, die auf dem geografischen Markt, der Vertriebskatalogansicht, dem Kundensegment und anderen Variablen basieren. Um dies zu ermöglichen, muss eine E-Commerce-Plattform ein flexibles Katalogdatenmodell bieten, mit dem Unternehmen Varianten ihres Katalogs erstellen können, die auf diese Szenarien zugeschnitten sind. Adobe erfüllt diese Anforderungen durch Merchandising-Services, die auf Katalogansichten und Richtlinien basieren. Merchandising Services bietet Bausteine, mit denen Händler Kataloge in großem Umfang erstellen und verwalten können. Dies ermöglicht es Unternehmen, Kataloge zu konfigurieren, die mit ihrer Geschäftsstruktur und ihren Markteinführungsstrategien übereinstimmen.

Mit Merchandising-Services haben Sie folgende Möglichkeiten:

- Verwenden Sie einen einzigen Basiskatalog für alle Ihre Geschäftsanforderungen. Skalieren Sie Ihren Katalog schnell auf neue Marken, Märkte, Geschäftsbereiche, marktreife Katalogsichten und Kundensegmente, ohne dass eine vollständige Neuarchitektur erforderlich ist. Dadurch werden Datenduplikate vermieden und Ihre E-Commerce-Plattform für hohe betriebliche Effizienz eingerichtet.
- Entfesseln Sie die Syndikation von Katalogen und stellen Sie die richtigen Inhalte bereit, indem Sie Ihren Produktkatalog so gestalten, dass er Ihr Geschäft widerspiegelt, einschließlich Produkte, Kunden, Preise und Vertrieb.
- Schnelles Aufnehmen und Aktualisieren von Katalogdaten und schnelle Bereitstellung der Aktualisierungen für die Storefront für Ihre Promotions und Kampagnenanforderungen.
- Erzielen Sie perfekte Lighthouse-Werte mit einsatzbereiten, blitzschnellen Benutzeroberflächenkomponenten auf Basis von Edge Delivery Services für nahtloses Produktbrowsen und Empfehlungen.
- Nutzen Sie eine moderne zusammensetzbare Architektur mit der Erweiterbarkeitsarchitektur von Adobe ([App Builder](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-development)), um Produktdaten zu importieren und Headless-Commerce-Storefronts mit der Adobe-API [Mesh) ](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-and-api-mesh).

>[!INFO]
>
>Weitere Informationen zu den in Merchandising Services verfügbaren APIs auf Basis von Katalogansichten und Richtlinien finden Sie unter [Entwicklerdokumentation](https://developer-stage.adobe.com/commerce/services/composable-catalog).

## Architektur

Merchandising Services, die auf Katalogansichten und Richtlinien basieren, ist ein hochgradig skalierbares, flexibles Katalogdatenmodell, das mühelos Anwendungsfälle für mehrere Marken, mehrere Geschäftseinheiten und mehrere Sprachen ermöglicht. Dieses Modell ersetzt die Verwendung der klassischen Adobe Commerce-Produktkatalogquellen (Website, Store, Storeview) durch neue Merchandising Services-Produktkatalogquellen (Katalogansicht, Richtlinie und Gebietsschema).

Das folgende Diagramm zeigt eine allgemeine Ansicht des Merchandising-Frameworks.

![[!DNL Merchandising Services] Architektur](../assets/merchandising-svcs-architecture.png)

Oben in diesem Diagramm werden Katalogdaten (PIM, ERP usw.) in das Merchandising Services-Framework aufgenommen. Diese Katalogdaten enthalten Artikelnummern. Jede SKU enthält Katalogquellendetails (Gebietsschema) und Produktattribute, die den neuen Merchandising Services-Produktkatalogquellen (Katalogansichten, Richtlinien und Gebietsschema) zugeordnet sind.

Wenn alle diese Daten in das Merchandising-Framework aufgenommen werden, ist das Ergebnis ein neuer einheitlicher Basiskatalog, der in der Datenpipeline des Katalog-Services verfügbar ist. Im nächsten Teil des Diagramms sehen Sie mehrere Katalogansichten. Jede Katalogansicht stellt eine Geschäftseinheit dar. Beispiel: *Texas*, *Texas retail saisonale* usw. Wie Sie sehen können, können Gebietsschemata, Richtlinien und Preisverzeichnisse über Katalogansichten hinweg gemeinsam genutzt werden&#x200B;

Schließlich zeigt das Diagramm, wie diese unterschiedlichen Katalogdaten an verschiedenen Stellen angezeigt werden können, z. B. in einer Edge Delivery Services-Storefront, einem Marktplatz, einer Anzeigenkatalogansicht, einer benutzerdefinierten Mikro-Storefront usw.

Informationen dazu, wie Sie Ihre Katalogdaten mithilfe der Katalogdatenaufnahme-API in das Merchandising aufnehmen können und wie Sie Ihre Gebietsschemata, Richtlinien und Preisbücher mithilfe der Katalogverwaltungs- und Regel-API einrichten, finden Sie unter [Entwicklerdokumentation](https://developer-stage.adobe.com/commerce/services/composable-catalog/).

Weitere Informationen zu den Konzepten von Merchandising Services finden Sie in den folgenden Abschnitten.

## Verwaltung des Produktkatalogs

Die Verwaltung des Produktkatalogs umfasst zwei verschiedene Aspekte: Produktdaten und Produktkontext. Merchandising Services respektiert die Trennung dieser Pflichten und bietet eine unabhängige Verwaltung für jede.

- **Produktdaten** - Welches Produkt wird verkauft und zu welchem Preis?
- **Produktkontext** - Wer verkauft an wen und wo?

![[!DNL Merchandising Services] Aspekte](../assets/merchandising-svcs-parts.png)

### Produktdaten

Produktdaten umfassen die folgenden Typen:

- **Produkte** - Einzelne SKUs oder Kollektionen von SKUs, die physische Waren oder immaterielle Services mit Attributen repräsentieren, die das Produkt repräsentieren, einschließlich Beschreibung, Gewicht, Größe, Abmessungen und mehr. Attribute geben auch die Katalogansicht und die Richtlinienkatalogquellen für eine SKU an. Produkte können in verschiedene Produktarten gruppiert werden, z. B. „simple“, „configurable“, „bundle“, „bundle of bundles“, „subscriptions“ und mehr.
- **Metadaten** - Produktattribut-Metadaten definieren und verwalten, wie Produktattribute in der Storefront in Produktlisten, Detailseiten, Suchergebnissen usw. angezeigt werden. Metadaten definieren auch, wie Produktattribute bei der Suche verwendet werden - beim Sortieren, Filtern, Suchen, bei der Gewichtung usw.
- **Preisbücher und Preise** - Bestimmt die Verkaufspreise von Produkten. In Merchandising-Services sind Produkt-SKU und Preis entkoppelt, sodass Sie mehrere Preislisten für eine einzelne SKU definieren können. Durch die Entkopplung der Preise von der SKU können Sie quellenspezifische Katalogpreise über verschiedene Kundenstufen, Geschäftseinheiten und Regionen hinweg freisetzen. Sie können reguläre und ermäßigte Preise definieren und all dies skaliert verwalten.
- **Assets** - Artefakte, die mit Produkten wie Bildern, Videos, PDFs oder anderen Dateitypen verknüpft sind (künftige Roadmap).

### Produktkontext-Management

Das Produktkontext-Management umfasst die folgenden Aspekte:

- **Katalogansicht** - Die Verteilungskatalogansicht definiert den Pfad, über den ein Unternehmen Produkte verkaufen möchte. Eine Katalogansicht ist die Abstraktion auf höchster Ebene, die Gebietsschemata und Richtlinien kapselt.
   - Beispiel: Händler für die Automobilindustrie. Tochtergesellschaften für Mehrmarkenkonglomerate. Produktionsstandort für Lieferanten.
- **Richtlinie** - Datenzugriffsfilter, mit dem Sie die richtigen Inhalte für das richtige Ziel bereitstellen können. Dieses Konzept ermöglicht Funktionen zur Katalogsyndikation.
   - Beispiel: Physische Ladengeschäfte, Marktplätze, Werbe-Pipelines (Google, Facebook, Instagram)
- **Katalogquelle** - Stellt die Sprache (Gebietsschema) für Kataloge dar, z. B. `en-US`. Die Katalogquelle wird während der Aufnahme von Katalogdaten auf SKU-Ebene festgelegt.

Während der Aufnahme und Aktualisierung von Produktdaten enthält eine SKU die Details von Katalogquellen und -attributen (die Attribute werden Katalogansichten und Richtlinien zugeordnet). Diese definieren die Produktkontextkennungen, zu denen eine SKU gehört:

![[!DNL Merchandising Services] Produktkontext-Kennungen](../assets/merchandising-svcs-product-id.png)

In der obigen Abbildung stellt jede SKU Folgendes bereit:

- Katalogquellenkennungen&#x200B;
   - Gebietsschema: Obligatorisch&#x200B;
- Produktattribute
   - Produktattribute werden verwendet, um den relevanten Katalogansichten und Richtlinien zuzuordnen&#x200B;
   - Beispiel: Als Automobilhersteller können Sie eine Katalogansicht und eine Richtlinienkombination für Produktattribute erstellen: (1) Händler (2) Automarken&#x200B;
- Preise und zugewiesene Preisbücher
   - Für jede SKU können mehrere Preise mithilfe mehrerer Preisbücher definiert werden.
   - Beispiel: Sie bieten Mitarbeitern einen reduzierten regulären Preis für Autoteile mit einem zusätzlichen Rabatt von 25%. Sie bieten Kunden von VIP einen höheren regulären Preis mit einem Rabatt von 10 %. Die Produkt-SKU-Preisinformationen stellen sicher, dass für jedes Kundensegment der richtige Preis angezeigt wird.

Die Katalogansicht und Richtliniendefinitionen werden mithilfe dedizierter APIs erstellt:

![[!DNL Merchandising Services] Katalogansicht, Richtlinie und Katalogquellenzuordnung](../assets/merchandising-svcs-scope-map.png)

- **Katalogquelle** (Gebietsschema) - Wird bei der Aufnahme von Produktdaten auf SKU-Ebene festgelegt&#x200B;
- **Katalogansicht** - Definition, die mit dedizierten APIs erstellt wurde. &#x200B;
- **Richtlinie** - Definition, die mit dedizierten APIs erstellt wurde.

## Wichtigste Funktionen

| Wichtigste Funktionen | Vorteil |
|---|---|
| **Direkte Katalogdatenaufnahme in die Storefront-Services-Pipeline**: Nehmen Sie Ihre Katalogdaten direkt in die Katalog-Service-Pipeline für den Storefront-Durchsuchen- und Suchlebenszyklus auf (Produktanzeigeseite, Produktlistenseite, Suchergebnisseite usw.). | <ul><li>Nehmen Sie Katalogdaten direkt in die Service-Pipeline für die Storefront auf, die für Folgendes zuständig ist: Katalog-Service, Produkterkennung und Empfehlungen. Auf diese Weise können Sie Katalogaktualisierungen im benötigten Umfang für Millionen von SKUs bereitstellen. Dies ermöglicht ein zeitkritisches, umfangreiches Promotion-Management. </li></ul> |
| **Neue Katalogproduktkatalogquellen**: Katalogansicht, Richtlinie und Katalogquelle sind neue Produktkatalogquellen, die von Merchandising Services eingeführt wurden. Diese Produktkatalogquellen ersetzen die Katalogquellen „Website“, „Store“ und „StoreReview“ in der Storefront-Service-Ebene. [Weitere Informationen](#product-context-management). | <ul><li>Mit den neuen Katalogquellen erschließt Merchandising Services die Möglichkeit, mithilfe eines einzigen Basiskatalogs auf Anwendungsfälle für mehrere Regionen, mehrere Geschäftseinheiten, mehrere Marken und mehrere Sprachen zu skalieren.</li><li>Beseitigen Sie Datenredundanz im Katalog-Management.</li></ul> |
| **Skalierung auf mehrere zehn Millionen SKUs** | Entsperren Sie die Katalogverwaltung in großem Maßstab. Hier können Sie mühelos über 200-MM-SKUs aufnehmen und verwalten. |
| **Unterstützung von Produkttypen** | <ul><li>Einfach, konfigurierbar</li><li>Bundles und Bundles (künftige Roadmap)</li><li>Abonnements und Pläne (künftige Roadmap)</li></ul> |
| **Headless-Commerce** | <ul><li>Vollständige Unterstützung für Headless-Commerce-Implementierungen über Katalog-Service, Produkterkennung und Recommendations-APIs.</li></ul> |
| **Moderne, blitzschnelle Benutzeroberflächenkomponenten** | <ul><li>Vorkonfigurierte UI-Komponentenunterstützung für die Produktsuche und Empfehlungen.</li><li>Die Benutzeroberflächenkomponenten sind erweiterbar und flexibel, sodass sie sowohl vom Edge Delivery-Service von Adobe als auch von jeder anderen Storefront-Implementierung verwendet werden können.</li></ul> |

## Welche Art von Händler profitiert am meisten von Merchandising-Services?

In der folgenden Tabelle werden häufige Herausforderungen, vor denen Händler stehen, und die Möglichkeiten, wie Merchandising-Services, die auf Katalogansichten und Richtlinien basieren, darauf reagieren, beschrieben.

| Händler-Typ | Anwendungsfall | Probleme gelöst |
|---|---|---|
| Mehrmarkenkonglomerat | <ul><li>Sie verkaufen mehrere Marken</li><li>Sie verkaufen in mehreren Ländern</li><li>Sie verkaufen in verschiedenen Sprachen</li></ul> | Verwenden Sie einen einheitlichen Basiskatalog und erreichen Sie so betriebliche Effizienz bei gleichzeitiger Erweiterung auf mehrere Marken, Regionen und Sprachen. |
| Automobil-/Fertigteilkonglomerat | <ul><li>Verkauft Auto- oder Maschinenteile. Die Produkte sind für alle Kunden gleich.</li><li>Verschiedene Händler verkaufen Teile an Kunden</li><li>Jeder Händler hat seine eigenen Preise, Lager und Versandmethoden</li></ul> | Um unterschiedliche Versandintegrationen zu haben, sollte jeder Händler über eine separate Website verfügen. Separate Websites erzwingen jedoch, dass das typische Katalogdatenmodell die Daten dupliziert. Wenn es also 3000 Händler in den USA gibt, erstellt ein Händler 3000 Katalogkopien, obwohl derselbe Katalog von allen Händlern verwendet wird. Diese Datenduplizierung beeinträchtigt die Leistungsgrenzen. Merchandising-Services eliminieren Datenduplizierung. |
| Verpackungs-/Logistikunternehmen | <ul><li>Sie haben mehrere Versandstandorte</li><li>Sie haben für jeden Kunden einen anderen Preis</li><li>Das gleiche Produkt, das an 2 Standorten für 2 Kunden verfügbar ist, hat 4 mögliche Preise</li></ul> | Trotz der Verwendung von Kundengruppen zur Abdeckung der Preise pro Kunde verfügt das typische Katalogdatenmodell nicht über die Möglichkeit, den Preis pro Standort zu verwalten. Darüber hinaus wünschen sich Händler eindeutige Sichtbarkeitsregeln pro Standort/Website. Die Verwaltung solch komplexer Preis- und Sichtbarkeitsregeln kann mit Merchandising-Services im großen Maßstab freigeschaltet werden. |
