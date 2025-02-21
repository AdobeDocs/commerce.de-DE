---
title: '[!DNL Composable Catalog Data Model]'
description: Erfahren Sie [!DNL Composable Catalog Data Model]  wie Sie mit dem für Adobe Commerce Ihren Katalog entsprechend Ihrem Geschäftsmodell und Ihrer Markteinführungsstrategie einrichten können
hidefromtoc: true
hide: true
recommendations: noCatalog
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 0%

---

# [!DNL Composable Catalog Data Model]

Ein Produktkatalog ist für Online-Shopping-Erlebnisse von entscheidender Bedeutung, da Kunden ihn durchsuchen, suchen und Käufe tätigen können. Um die betriebliche Effizienz zu gewährleisten, sollte ein Produktkatalog die Geschäftsstruktur des Unternehmens genau widerspiegeln. Unternehmen müssen Produkte häufig zu unterschiedlichen Preisen verkaufen, die auf dem geografischen Markt, dem Vertriebskanal, dem Kundensegment und anderen Variablen basieren. Um diesem Umstand Rechnung zu tragen, muss eine E-Commerce-Plattform ein flexibles Katalogdatenmodell bieten, das es Unternehmen ermöglicht, Varianten ihres Katalogs zu erstellen, die auf diese Szenarien zugeschnitten sind. Das zusammensetzbare Katalogdatenmodell (Composable Catalog Data Model, CCDM) von Adobe Commerce erfüllt diese Anforderungen. CDM bietet Bausteine, mit denen Händler Kataloge im benötigten Umfang erstellen und verwalten können. Dies ermöglicht es Unternehmen, Kataloge zu konfigurieren, die mit ihrer Geschäftsstruktur und ihren Markteinführungsstrategien übereinstimmen.

Mit CCDM können Sie auf allgemeiner Ebene:

- Verwenden Sie einen einzigen Basiskatalog für alle Ihre Geschäftsanforderungen. Skalieren Sie Ihren Katalog schnell auf neue Marken, Märkte, Geschäftsbereiche, Go-to-Market-Kanäle und Kundensegmente, ohne dass eine vollständige Neuarchitektur erforderlich ist. Dadurch werden Datenduplikate vermieden und Ihre E-Commerce-Plattform für hohe betriebliche Effizienz eingerichtet.
- Entfesseln Sie die Syndikation von Katalogen und stellen Sie die richtigen Inhalte bereit, indem Sie Ihren Produktkatalog so gestalten, dass er Ihr Geschäft widerspiegelt, einschließlich Produkte, Kunden, Preise und Vertrieb.
- Schnelles Aufnehmen und Aktualisieren von Katalogdaten und schnelle Bereitstellung der Aktualisierungen für die Storefront für Ihre Promotions und Kampagnenanforderungen.
- Erzielen Sie perfekte Lighthouse-Werte mit einsatzbereiten, blitzschnellen Benutzeroberflächenkomponenten auf Basis von Edge Delivery Services für nahtloses Produktbrowsen und Empfehlungen.
- Nutzen Sie eine moderne zusammensetzbare Architektur mit der Erweiterbarkeitsarchitektur von Adobe ([App Builder](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-development)), um Produktdaten zu importieren und Headless-Commerce-Storefronts mit der Adobe-API [Mesh) ](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-and-api-mesh).

>[!INFO]
>
>Weitere Informationen zu den in CDM verfügbaren APIs finden Sie unter [Entwicklerdokumentation](https://developer-stage.adobe.com/commerce/services/composable-catalog).

## Architektur

CCDM ist ein hochgradig skalierbares, flexibles Katalogdatenmodell, das mühelos Anwendungsfälle für mehrere Marken, mehrere Geschäftseinheiten und mehrere Sprachen ermöglicht. Das Modell ersetzt die Verwendung der klassischen Adobe Commerce-Produktbereiche (Website, Store, Storeview) durch neue CDM-Produktbereiche (Kanal, Richtlinie und Gebietsschema).

Das folgende Diagramm bietet eine allgemeine Ansicht des CDM-Frameworks.

![[!DNL Composable Catalog Data Model] Architektur](assets/ccdm-architecture.png)

Am Anfang dieses Diagramms werden Katalogdaten (PIM, ERP usw.) in das CDM-Framework aufgenommen. Diese Katalogdaten enthalten Artikelnummern. Jede SKU enthält Bereichsdetails (Gebietsschema) und Produktattribute, die den neuen CDM-Produktbereichen (Kanälen, Richtlinien und Gebietsschema) zugeordnet sind.

Wenn alle diese Daten in das CDM-Framework aufgenommen werden, ist das Ergebnis ein neuer einheitlicher Basiskatalog, der in der Katalog-Service-Datenpipeline verfügbar ist. Im nächsten Teil des Diagramms sehen Sie mehrere Kanäle. Jeder Kanal stellt eine Geschäftseinheit dar. Beispiel: *Texas*, *Texas retail saisonale* usw. Wie Sie aus dem Diagramm sehen können, können Gebietsschemata, Richtlinien und Preisbücher kanalübergreifend geteilt werden&#x200B;

Schließlich zeigt das Diagramm, wie diese unterschiedlichen Katalogdaten an verschiedenen Stellen angezeigt werden können, z. B. in einer Edge Delivery Services-Storefront, einem Marktplatz, einem Werbekanal, einer benutzerdefinierten Mikro-Storefront usw.

Informationen dazu, wie Sie Ihre Katalogdaten mithilfe der Katalogdatenaufnahme-API in CDM aufnehmen können und wie Sie Ihre Gebietsschemata, Richtlinien und Preisverzeichnisse mithilfe der Katalogverwaltungs- und Regel-API einrichten, finden Sie unter [Entwicklerdokumentation](https://developer-stage.adobe.com/commerce/services/composable-catalog/).

Weitere Informationen zu den Konzepten von CDM finden Sie in den folgenden Abschnitten.

## Verwaltung des Produktkatalogs

Die Verwaltung des Produktkatalogs umfasst zwei verschiedene Aspekte: Produktdaten und Produktkontext. Der CCDM respektiert die Trennung dieser Aufgaben und bietet eine unabhängige Verwaltung für jede Aufgabe.

- **Produktdaten** - Welches Produkt wird verkauft und zu welchem Preis?
- **Produktkontext** - Wer verkauft an wen und wo?

![[!DNL Composable Catalog Data Model] Aspekte](assets/ccdm-parts.png)

### Produktdaten

Produktdaten umfassen die folgenden Typen:

- **Produkte** - Einzelne SKUs oder Kollektionen von SKUs, die physische Waren oder immaterielle Services mit Attributen repräsentieren, die das Produkt repräsentieren, einschließlich Beschreibung, Gewicht, Größe, Abmessungen und mehr. Attribute geben auch den Kanal und die Richtlinienbereiche für eine SKU an. Produkte können in verschiedene Produktarten gruppiert werden, z. B. „simple“, „configurable“, „bundle“, „bundle of bundles“, „subscriptions“ und mehr.
- **Metadaten** - Produktattribut-Metadaten definieren und verwalten, wie Produktattribute in der Storefront in Produktlisten, Detailseiten, Suchergebnissen usw. angezeigt werden. Metadaten definieren auch, wie Produktattribute bei der Suche verwendet werden - beim Sortieren, Filtern, Suchen, bei der Gewichtung usw.
- **Preisbücher und Preise** - Bestimmt die Verkaufspreise von Produkten. In CDM werden eine Produkt-SKU und ein Preis entkoppelt, sodass Sie mehrere Preislisten für eine einzelne SKU definieren können. Durch die Entkopplung der Preise von der SKU können Sie bereichsspezifische Preise für verschiedene Kundenstufen, Geschäftseinheiten und Regionen freisetzen. Sie können reguläre und ermäßigte Preise definieren und all dies skaliert verwalten.
- **Assets** - Artefakte, die mit Produkten wie Bildern, Videos, PDFs oder anderen Dateitypen verknüpft sind (künftige Roadmap).

### Produktkontext-Management

Das Produktkontext-Management umfasst die folgenden Aspekte:

- **Channel** - Der Vertriebskanal definiert den Pfad, über den ein Unternehmen Produkte verkaufen möchte. Ein Kanal ist die Abstraktion auf höchster Ebene, die Gebietsschemata und Richtlinien kapselt.
   - Beispiel: Händler für die Automobilindustrie. Tochtergesellschaften für Mehrmarkenkonglomerate. Produktionsstandort für Lieferanten.
- **Richtlinie** - Datenzugriffsfilter, mit dem Sie die richtigen Inhalte für das richtige Ziel bereitstellen können. Dieses Konzept ermöglicht Funktionen zur Katalogsyndikation.
   - Beispiel: Physische Ladengeschäfte, Marktplätze, Werbe-Pipelines (Google, Facebook, Instagram)
- **Scope** - Stellt die Sprache (Gebietsschema) für Kataloge dar, z. B. `en-US`. Der Umfang wird während der Aufnahme von Katalogdaten auf SKU-Ebene festgelegt.

Während der Aufnahme und Aktualisierung von Produktdaten enthält eine SKU die Details von Bereichen und Attributen (die Attribute sind Kanälen und Richtlinien zugeordnet). Diese definieren die Produktkontextkennungen, zu denen eine SKU gehört:

![[!DNL Composable Catalog Data Model] Produktkontext-Kennungen](assets/ccdm-product-id.png)

In der obigen Abbildung stellt jede SKU Folgendes bereit:

- Bereichskennungen&#x200B;
   - Gebietsschema: Obligatorisch&#x200B;
- Produktattribute
   - Produktattribute werden verwendet, um den relevanten Kanälen und Richtlinien zuzuordnen&#x200B;
   - Beispiel: Als Automobilhersteller können Sie eine Kanal- und Richtlinienkombination für Produktattribute erstellen: (1) Händler (2) Automarken&#x200B;
- Preise und zugewiesene Preisbücher
   - Für jede SKU können mehrere Preise mithilfe mehrerer Preisbücher definiert werden.
   - Beispiel: Sie bieten Mitarbeitern einen reduzierten regulären Preis für Autoteile mit einem zusätzlichen Rabatt von 25%. Sie bieten Kunden von VIP einen höheren regulären Preis mit einem Rabatt von 10 %. Die Produkt-SKU-Preisinformationen stellen sicher, dass für jedes Kundensegment der richtige Preis angezeigt wird.

Die Kanal- und Richtliniendefinitionen werden mit dedizierten APIs erstellt:

![[!DNL Composable Catalog Data Model] Kanal-, Richtlinien- und Bereichszuordnung](assets/ccdm-scope-map.png)

- **Umfang** (Gebietsschema): Wird bei der Aufnahme von Produktdaten auf SKU-Ebene festgelegt&#x200B;
- **channel** - Definition, die mit dedizierten APIs erstellt wurde. &#x200B;
- **Richtlinie** - Definition, die mit dedizierten APIs erstellt wurde.

## Wichtigste Funktionen

| Wichtigste Funktionen | Vorteil |
|---|---|
| **Direkte Katalogdatenaufnahme in die Storefront-Services-Pipeline**: Nehmen Sie Ihre Katalogdaten direkt in die Katalog-Service-Pipeline für den Storefront-Durchsuchen- und Suchlebenszyklus auf (Produktanzeigeseite, Produktlistenseite, Suchergebnisseite usw.). | <ul><li>Nehmen Sie Katalogdaten direkt in die Service-Pipeline für die Storefront auf, die für Folgendes zuständig ist: Katalog-Service, Produkterkennung (Live-Suche) und Produktempfehlungen. Auf diese Weise können Sie Katalogaktualisierungen im benötigten Umfang für Millionen von SKUs bereitstellen. Dies ermöglicht ein zeitkritisches, umfangreiches Promotion-Management. </li></ul> |
| **Neue Katalogproduktbereiche**: Kanal, Richtlinie und Umfang sind neue Produktbereiche, die von CCDM eingeführt werden. Diese Produktbereiche ersetzen die Bereiche „Website“, „Store“ und „StoreReview“ in der Ebene „Storefront-Services“. [Weitere Informationen](#product-context-management). | <ul><li>Mit den neuen Umfängen ermöglicht CDM die Skalierung für Anwendungsfälle mit mehreren Regionen, Geschäftseinheiten, mehreren Marken und mehreren Sprachen auf einfache Weise mithilfe eines einzigen Basiskatalogs.</li><li>Beseitigen Sie Datenredundanz im Katalog-Management.</li></ul> |
| **Skalierung auf mehrere zehn Millionen SKUs** | Entsperren Sie die Katalogverwaltung in großem Maßstab. Hier können Sie mühelos über 200-MM-SKUs aufnehmen und verwalten. |
| **Unterstützung von Produkttypen** | <ul><li>Einfach, konfigurierbar</li><li>Bundles und Bundles (künftige Roadmap)</li><li>Abonnements und Pläne (künftige Roadmap)</li></ul> |
| **Headless-Commerce** | <ul><li>Vollständige Unterstützung für Headless-Commerce-Implementierungen über Katalog-Service, Produkterkennung (Live-Suche) und Produktempfehlungs-APIs.</li></ul> |
| **Moderne, blitzschnelle Benutzeroberflächenkomponenten** | <ul><li>Vorkonfigurierte UI-Komponentenunterstützung für die Produktsuche und Produktempfehlungen.</li><li>Die Benutzeroberflächenkomponenten sind erweiterbar und flexibel, sodass sie sowohl vom Edge Delivery-Service von Adobe als auch von jeder anderen Storefront-Implementierung verwendet werden können.</li></ul> |

## Welche Art von Händler profitiert am meisten von CCDM?

In der folgenden Tabelle werden häufige Herausforderungen, vor denen Händler stehen, und die Art und Weise, wie sie mit CCDM bewältigt werden, beschrieben.

| Händler-Typ | Anwendungsfall | Probleme gelöst |
|---|---|---|
| Mehrmarkenkonglomerat | <ul><li>Sie verkaufen mehrere Marken</li><li>Sie verkaufen in mehreren Ländern</li><li>Sie verkaufen in verschiedenen Sprachen</li></ul> | Verwenden Sie einen einheitlichen Basiskatalog und erreichen Sie so betriebliche Effizienz bei gleichzeitiger Erweiterung auf mehrere Marken, Regionen und Sprachen. |
| Automobil-/Fertigteilkonglomerat | <ul><li>Verkauft Auto- oder Maschinenteile. Die Produkte sind für alle Kunden gleich.</li><li>Verschiedene Händler verkaufen Teile an Kunden</li><li>Jeder Händler hat seine eigenen Preise, Lager und Versandmethoden</li></ul> | Um unterschiedliche Versandintegrationen zu haben, sollte jeder Händler über eine separate Website verfügen. Separate Websites erzwingen jedoch, dass das typische Katalogdatenmodell die Daten dupliziert. Wenn es also 3000 Händler in den USA gibt, erstellt ein Händler 3000 Katalogkopien, obwohl derselbe Katalog von allen Händlern verwendet wird. Diese Datenduplizierung beeinträchtigt die Leistungsgrenzen. CCDM eliminiert Datenduplizierung. |
| Verpackungs-/Logistikunternehmen | <ul><li>Sie haben mehrere Versandstandorte</li><li>Sie haben für jeden Kunden einen anderen Preis</li><li>Das gleiche Produkt, das an 2 Standorten für 2 Kunden verfügbar ist, hat 4 mögliche Preise</li></ul> | Trotz der Verwendung von Kundengruppen zur Abdeckung der Preise pro Kunde verfügt das typische Katalogdatenmodell nicht über die Möglichkeit, den Preis pro Standort zu verwalten. Darüber hinaus wünschen sich Händler eindeutige Sichtbarkeitsregeln pro Standort/Website. Die Verwaltung solch komplexer Preis- und Sichtbarkeitsregeln kann im großen Maßstab mit CCDM freigeschaltet werden. |

### Wie geht es jetzt weiter?

- Aufnehmen von Daten in CCDM mithilfe [Datenaufnahme-API](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/using-the-api/).
- Verwalten Sie Ihren Katalog und definieren Sie die Kanäle, Richtlinien und Bereiche mithilfe der [Catalog Management API](https://developer-stage.adobe.com/commerce/services/composable-catalog/admin/using-the-api/)
- [Absolvieren Sie ein Tutorial](https://developer-stage.adobe.com/commerce/services/composable-catalog/ccdm-use-case/) in dem gezeigt wird, wie ein Unternehmen mit einem einzigen Basiskatalog die CDM-APIs verwenden kann, um Produktdaten hinzuzufügen, Kataloge mithilfe von Projektionen zu definieren und die Katalogdaten zur Anzeige in einer Headless-Storefront abzurufen.
