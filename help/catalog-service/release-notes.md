---
title: '[!DNL Commerce Storefront Catalog Service Release Notes]'
description: Die neuesten Versionsinformationen für  [!DNL Catalog Service]  für Adobe Commerce.
feature: Services, Catalog Service, Release Notes
exl-id: 74f2e46a-5592-4857-a6d7-b95b85d8b4cc
TQID: https://experienceleague.adobe.com/-yxW4sTuk7LPjGy5YsQ65phtkBLiByg8SmBaQPHMevM
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: c87bcff49f3c17379331e18fb9a0e890a5b9717c
workflow-type: tm+mt
source-wordcount: 2682
ht-degree: 0%

---

# [!DNL Commerce Storefront Catalog Service] Versionshinweise

In diesen Versionshinweisen werden die neuesten Aktualisierungen des Commerce Catalog Service behandelt, darunter:

- **[Versionen des Storefront Catalog Service](#storefront-catalog-service)**

   - Verbesserungen des Catalog Service-API-Schemas für einen verbesserten Datenabruf
   - Verbesserungen der Sicherheit, Leistung und Zuverlässigkeit für die Catalog Service-API und die zugrunde liegende Infrastruktur.

  Weitere [&#x200B; zu diesen APIs finden &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/) in der Commerce Developer-Dokumentation unter „Schema für Storefront-Services“.

- **[Catalog Service Metapaket-Versionen](#catalog-service-metapackage)**

   - Abhängigkeiten wurden aktualisiert, um die Leistung, Stabilität und Kompatibilität mit anderen Adobe Commerce-Komponenten zu verbessern.

- **[Catalog Service-Installationsprogrammversionen](#catalog-service-installer)**

   - Abhängigkeiten wurden aktualisiert, um die Kompatibilität zwischen dem Katalog-Service und Ihrem Commerce-Stack zu gewährleisten.

>[!NOTE]
>
>Wenn Ihr Commerce-Projekt Adobe Commerce Optimizer verwendet, um Katalogdaten für Commerce Edge Delivery Service oder Headless-Storefronts bereitzustellen, finden Sie in den [Adobe Commerce Optimizer](../optimizer/release-notes.md)Versionshinweisen die neuesten API-Aktualisierungen.

Aktualisierungen werden nach Typ kategorisiert:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bug](../assets/bug.svg) Bekannte Probleme

Unterstützung wird für die neueste Version bereitgestellt. Versionshinweise für ältere Versionen sind als Referenz enthalten.

## Storefront Catalog Service

### Mai 2026

**Veröffentlichungsdatum:**. Mai 2026
<!-- v1.55 -->

![Neu](../assets/new.svg) Erzwungenes Limit von maximal 100 SKUs pro Anfrage für Adobe Commerce- und Adobe Commerce as a Cloud Service-Clients gemäß [dokumentierten Limits und Begrenzungen](https://experienceleague.adobe.com/en/docs/commerce/optimizer/boundaries-limits).
<!--DATA-7163-->

**Veröffentlichungsdatum:**. Mai 2026
<!--v1.54-->

![Neu](../assets/new.svg) **Kategoriesortierreihenfolge in GraphQL** - Der `CategoryView` GraphQL-Typ enthält jetzt ein Positionsfeld, sodass Storefronts Kategorien in der Reihenfolge anzeigen können, die Händler in der Kataloghierarchie konfigurieren.
<!--DATA-7166-->

**Veröffentlichungsdatum**: 4. Mai 2026
<!-- v1.53 -->

![Fix](../assets/fix.svg) Die Preise für Storefront-Produkte zeigen jetzt den korrekten Währungscode (z. B. USD) für alle Produkttypen an. Zuvor zeigten einige Produkte `NONE` anstelle der erwarteten Währung, was zu fehlenden Preisen führte. Diese Aktualisierung gewährleistet ein konsistentes und genaues Preis-Rendering in der Storefront.<!--DATA-7115-->

### April 2026

**Veröffentlichungsdatum:**. April 2026
<!--v1.52-->

![Neu](../assets/new.svg) Erzwungenes Limit von maximal 100 SKUs pro Anfrage für Adobe Commerce Optimizer und Adobe Commerce as a Cloud Service
Clients gemäß [dokumentierte Beschränkungen und &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/optimizer/boundaries-limits)<!--DATA-7156-->

**Veröffentlichungsdatum:**. April 2026
<!--v1.51-->

![Neu](../assets/new.svg) Es wurde eine neue `searchCategory` GraphQL-Abfrage hinzugefügt, mit der Kunden Kategorien anhand des Namens mit paginierten Ergebnissen suchen können. Die Abfrage akzeptiert eine erforderliche `searchTerm` (mindestens 3 Zeichen) und optionale `family`-, `pageSize`- und `currentPage`. Zu den Ergebnissen gehören der Abgleich von `CategoryTreeView` mit vollständigen Kategoriemetadaten, ein `totalCount` und `pageInfo` für die Paginierung. <!--COMOPT-1819-->

Diese Abfrage ist nur für Kunden verfügbar, die Adobe Commerce Optimizer Merchandising Services verwenden. Siehe [searchCategory](https://developer.adobe.com/commerce/services/reference/graphql/).

### März 2026

**Veröffentlichungsdatum**: 24. März 2026
<!--v1.49-->

![Neu](../assets/new.svg) Es wurde Unterstützung für die Berechnung und Rückgabe der Preisspanne für dynamische Pakete hinzugefügt.
<!--DATA-7115-->

### Dezember 2025

**Veröffentlichungsdatum:**. Dezember 2025
<!-- v1.46 -->

![Fix](../assets/fix.svg) Verbesserungen auf Systemebene und Infrastrukturverbesserungen zur Verbesserung von Leistung und Stabilität.
<!--DATA-6852, DATA-6864-->

### November 2025

**Veröffentlichungsdatum**: 17. November 2025
<!-- v1.45 -->

![Neu](../assets/new.svg) **Attributfilterung nach Name**-Die `productSearch` GraphQL-Abfrage unterstützt jetzt das Filtern von Produktattributen mit dem `names`. <!--DATA-6831--> Mit diesem Filter können Sie:

- Verringern der Größe der Antwort-Payload durch die Anforderung nur bestimmter Attribute
- Kombination mit dem vorhandenen `roles`, um die Sichtbarkeit nach Rolle und Attributname einzugrenzen
- Beispiele:

  **Nur nach Attributnamen filtern**

  ```graphql
  query {
    products(skus: ["SKU-001"]) {
      attributes(names: ["color", "size", "material"]) {
        name
        label
        value
      }
    }
  }
  ```

  **Filtern Sie nach Rollen und Namen:**

  ```graphql
  query {
    products(skus: ["SKU-001"]) {
      attributes(roles: ["visible in PDP"], names: ["eco_collection", "new"]) {
        name
        label
        value
        roles
      }
    }
  }
  ```

>[!NOTE]
>
>Um alle Attribute ohne Filterung abzurufen, lassen Sie das `names`-Argument weg oder geben Sie ein leeres -Array an.

**Veröffentlichungsdatum:**. November 2025
<!-- v1.44 -->

![Fix](../assets/fix.svg) Verbesserungen auf Systemebene und Infrastrukturverbesserungen zur Verbesserung von Leistung und Stabilität. <!--DATA-6852, DATA-6864-->

![Korrigieren](../assets/fix.svg) Gruppierte Produkte können jetzt abgefragt werden, wenn das übergeordnete Element keine Preise hat. Untergeordnete Produkte geben ihre eigenen Sichtbarkeitsrollen zurück.<!--DATA-6779-->

![Fix](../assets/fix.svg) Verbesserungen auf Systemebene und Infrastrukturverbesserungen zur Verbesserung von Leistung und Stabilität. <!--DATA-6721, DATA-6864-->

### September 2025

**Veröffentlichungsdatum:**. September 2025
<!-- v1.42 -->

![Neu](../assets/new.svg) **Unterstützung für Tier Pricing** um Volumenpreise abzufragen:<!--DATA-6643-->

So rufen Sie die Preisstufe ab:

1. Verwenden der `products` Abfrage mit Ihren gewünschten SKUs
2. Greifen Sie für **SimpleProductView** auf `price.tiers` zu
3. Greifen Sie für **ComplexProductView** auf `priceRange.minimum.tiers` und `priceRange.maximum.tiers` zu.
4. Jede Stufe enthält die ermäßigten `tier`- und `quantity`
5. Mengenschwellenwerte mit `gte` (größer oder gleich) und `lt` (kleiner als) definieren

**Beispiel:**

```graphql
query {
  products(skus: ["SKU-001"]) {
    ... on SimpleProductView {
      price {
        regular { amount { value currency } }
        tiers {
          tier { amount { value currency } }
          quantity {
            ... on ProductViewTierRangeCondition { gte lt }
          }
        }
      }
    }
  }
}
```

![Fixpreis](../assets/fix.svg) **Stufenpreise gefiltert nach Endpreis-**<!--DATA-6643-->

Die API gibt jetzt nur noch Preisstufen zurück, deren ermäßigter Preis **niedriger als** der Mindestendpreis des Produkts ist. Höhere Ebenen werden weggelassen, da stattdessen der Mindestendpreis für die Storefront gelten würde.

Gilt für:

- **Einfache Produkte**: `price.tiers` umfasst nur Ebenen mit `tier.amount.value` &lt; `price.final.amount.value` (Minimum final).
- **Komplexe Produkte**: `priceRange.minimum.tiers` und `priceRange.maximum.tiers` verwenden beim Erstellen der Preisspanne dieselbe Regel.

**Veröffentlichungsdatum:**. September 2025
<!-- v1.41 -->

![Behebung](../assets/fix.svg) **Verbesserte Fehlerbehandlung bei fehlenden Preisinformationen** - Wenn die Preisdaten noch nicht eingegangen sind, gibt die API `null` für das Preisfeld zurück, anstatt einen Fehler auszulösen, sodass Kunden fehlende Daten ordnungsgemäß verarbeiten können.<!--DATA-6612-->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um die Leistung und Stabilität zu verbessern.<!--DATA-6671-->

### Juli 2025

**Veröffentlichungsdatum:**. Juli 2025
<!-- v1.40 -->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6619-->

**Veröffentlichungsdatum**: 24. Juli 2025
<!-- v1.39 -->

![Neu](../assets/new.svg) **Empfehlungseinheiten nach Einheitenkennung abrufen**-Neuer GraphQL-Endpunkt `recommendationsByUnitIds` ruft Empfehlungseinheiten anhand ihrer eindeutigen ID ab, um den Zugriff flexibler und zielgerichteter zu gestalten.

- `unitIds` ist erforderlich (Liste der abzurufenden recIds).
- Kontextparameter (`currentSku`, `cartSkus`, `userViewHistory`, `userPurchaseHistory`, `category`) verhalten sich genauso wie in der vorhandenen Recommendations-Abfrage.

- **Beispiel**

  ```graphql
  query {
    recommendationsByUnitIds(
      unitIds: ["11ee89d1-bfae-4582-a921-2ced44ff6bf7"]
      currentSku: "24-MB01"
      cartSkus: ["24-MB01"]
    ) {
      totalResults
      results {
        unitId
        unitName
        totalProducts
        productsView {
          sku
        }
        pageType
        typeId
        storefrontLabel
        displayOrder
      }
    }
  }
  ```

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6316-->

**Veröffentlichungsdatum**: 15. Juli 2025
<!-- v1.38 -->

![Neu](../assets/new.svg) **Produkttypen für Geschenkkarten**-Katalog-Storefront-Service unterstützt jetzt Produktattribute als JSON-Objekte oder Arrays und ermöglicht so eine flexible Verwaltung komplexer Typen wie Geschenkkarten.<!--DATA-6573-->

+++Frühere Versionen

### Juni 2025

**Veröffentlichungsdatum:**. Juni 2025
<!-- v1.37 -->

![Neu](../assets/new.svg) **Hierarchische Preisbuchkonfiguration** - Präzise Preisbereiche für über- und untergeordnete Preisbücher. Berechnungen berücksichtigen Hierarchie und übernommene Regeln; reduziert Preisfehler, wenn mehrere Preisbücher verknüpft sind. Nur Adobe Commerce Optimizer. Siehe [Preisbücher](https://experienceleague.adobe.com/en/docs/commerce/optimizer/setup/pricebooks).

![Neu](../assets/new.svg) **Schlüssel ohne Unterscheidung von Groß- und Kleinschreibung** - Bei Schlüsselsuchen in Abfragen wird jetzt nicht mehr zwischen Groß- und Kleinschreibung unterschieden, wodurch Fehler durch Schlüsselschreibungen reduziert werden. <!--DATA-6494, DCAT-2495-->

**Veröffentlichungsdatum:**. Juni 2025
<!-- v1.36 -->

![Neu](../assets/new.svg) **Öffentliche I/O-Ereignisse für Katalog-Storefront** - Es wurden öffentliche I/O-Ereignisse für die Echtzeit-Integration und -Beobachtbarkeit (CSS und EDS) hinzugefügt.<!--DATA-6329-->

![Neu](../assets/new.svg) **Server-Side Rendering (SSR)** - Architektonische Verbesserungen zur Unterstützung von SSR für bessere Leistung, SEO und UX in großen Katalogen.<!--DATA-6278, DATA-6280-->

![Neu](../assets/new.svg) **Infrastruktur und Sicherheit** - Neue AWS-Rollen, ServiceNow-Integration und CI/CD-Pipelines für den Ereignis-Service.

![Neu](../assets/new.svg) **Ereignisformate und Beobachtbarkeit** - Optimierte Payloads, verbesserte Überwachung, verbesserte Variantenereignisdaten.<!--DATA-6332, DATA-6402, -->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6404, DATA-6410, -->

**Veröffentlichungsdatum:**. Juni 2025
<!-- v1.35 -->

![Neu](../assets/new.svg) **Nicht zwischengespeicherte Daten abrufen**-Aktivieren Sie die `Magento-Is-Preview`-Kopfzeile, um nicht zwischengespeicherte Daten vom Katalog-Endpunkt an den Suchdienst zu übergeben.<!--DATA-6345-->

![Neu](../assets/new.svg) **Produktoptionen mit Mehrfachauswahl**-GraphQL-API macht jetzt verfügbar, ob Produktoptionen mehrere Auswahlen zulassen (z. B. Bundle „mehrere Elemente auswählen„).<!--DATA-6487-->

![Neu](../assets/new.svg) Aktualisierte Preisvalidierung bei der Datenaufnahme, um Produkte ohne Preise zu unterstützen.<!--DATA-6098-->

![Behebung](../assets/fix.svg) Verbesserte Fehlerbehandlung für einfache Paketpreise in Adobe Commerce Optimizer.<!--DATA-6541-->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6273, DATA-6485, -->

### April 2025

**Veröffentlichungsdatum:**. April 2025
<!-- v1.34 -->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-5732-->

<!-- v1.33 -->
![Fix](../assets/fix.svg) Infrastructure unterstützt jetzt extrem große Kataloge (bis zu ~440 Millionen SKUs), ohne dass sich dies auf die bestehenden Arbeitslasten auswirkt.

### März 2025

**Veröffentlichungsdatum**: 28. März 2025
<!-- v1.32 -->

![Beheben](../assets/fix.svg) Attribute ohne Rollen werden für den zusammenstellbaren Katalog nicht mehr standardmäßig indiziert. Dies verbessert die Indizierungszeit und reduziert den Speicher. Altes Verhalten kann über ein Feature Flag wieder aktiviert werden.

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.
<!--DATA-6348, DATA-6440, DATA-6446, DATA-6641-->

### Februar 2025

**Veröffentlichungsdatum**: 18. Februar 2025
<!-- v1.31 -->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6389, DATA-6367, DATA-6373-->

### Dezember 2024

**Veröffentlichungsdatum:**. Dezember 2024
<!-- v1.30 -->

Hauptversion: [Zusammensetzbares Katalogdatenmodell](https://developer.adobe.com/commerce/services/optimizer/) für Headless-Storefronts, Header-Management und die Handhabung von Produktdaten.

![Neu](../assets/new.svg) **Zusammensetzbares Katalogdatenmodell (CCDM)** - Unterstützt Kunden bei der Verwendung des zusammensetzbaren Katalogs für Headless-Storefronts. Neue Endpunkte akzeptieren Katalogansicht- und Richtlinien-IDs (abwärtskompatibel). Konfigurierbare Produktdetails und Preise mit integrierter Paginierung.<!--DATA-6018, DATA-6288-->

![Neu](../assets/new.svg) **Kopfzeilenverwaltung**-`AC-Locale` für zusammenstellbare Katalog-API-Vorgänge in `AC-Scope-Locale` umbenannt. Kopfzeilenzuordnung und Standardwerte wurden angegeben.<!--DATA-6303, DATA-6078-->

![Neu](../assets/new.svg) **Produktdaten und Preise**-Unterstützung für zusammenstellbares Katalogdatenmodell und verbesserte Preisverwaltung für konfigurierbare Produkte.<!--DATA-6279-->

`CurrencyEnum` wurde aktualisiert, um `NONE` für Produktsuchabfragen zu unterstützen, die an der Verbundlogik ausgerichtet sind.<!--DATA-6285-->

![Behebung](../assets/fix.svg) **Infrastruktur und Upgrades** - Verbesserungen auf Systemebene für Sicherheit, Leistung und Stabilität.

![Fix](../assets/fix.svg) Bundle-Produktoptionen zeigen jetzt nur noch aktivierte Produkte an.<!--DATA-6347-->

**Veröffentlichungsdatum:**. Dezember 2024
<!-- v1.29 -->

![Neu](../assets/new.svg) **Bildreihenfolge in Produktabfragen** - Produktbilder im Feld &quot;GraphQL-`images`&quot; folgen jetzt der `sortOrder` für den Katalogexport, um ein konsistentes Verhalten bei Storefronts und APIs zu gewährleisten.<!--DATA-6258-->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6619-->

**Veröffentlichungsdatum**: Dezember 2024
<!-- v1.28 -->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.
<!--DATA-6180, DATA-6230, DATA-6254, DATA-6257-->

### Oktober 2024

**Veröffentlichungsdatum:**. Oktober 2024
<!-- v1.26 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Das GraphQL-Schema enthält jetzt `lastModifiedAt` in Produktinformationen für genaue Sitemaps und die Neuindizierung von Suchmaschinen (z. B. Google).
<!--DATA-6209-->

### September 2024

**Veröffentlichungsdatum**: 26. September 2024
<!-- v1.27 -->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.
<!--DATA-6243-->

### August 2024

**Veröffentlichungsdatum**: 22. August 2024
<!-- v1.23 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Fix](../assets/fix.svg) Produktinformationen können jetzt ohne Produktüberschreibungsdaten (Preise) abgerufen werden. Zuvor haben diese Abfragen Folgendes zurückgegeben: `The following sku does not have product override data in the DB: <SKU value>. Make sure data is synced.`
<!--DATA-6121-->

**Veröffentlichungsdatum:**. August 2024
<!-- v1.22 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Unterstützung zum Abrufen aller Varianten nach Produkt-SKU hinzugefügt. Siehe die [Catalog Service API-Referenz](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/).
<!--DATA-6067-->

### Mai 2024

**Veröffentlichungsdatum:**. Mai 2024
<!-- v1.19 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer


![Korrigieren](../assets/fix.svg) Das `InStock`-Flag für Optionswerte berücksichtigt jetzt den `enabled` der Produktvariante.

<!--DATA-5033-->

![Fix](../assets/fix.svg) Es wurde Unterstützung für Produktpreise mit bis zu 16 Stellen und 4 Dezimalstellen hinzugefügt. Synchronisieren Sie über das [Data Management-Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard) oder [CLI](../data-export/data-export-cli-commands.md) neu, um Aktualisierungen anzuwenden.
<!--DATA-5033-->

#### Bekannte Einschränkungen

Die folgenden Funktionen werden noch nicht unterstützt:

- Die maximale Größe für die Payload dynamischer Attribute beträgt 9 MB.
- Der Gruppenproduktpreis kann mit einfachen Produktpreisen berechnet werden.
- In einem Bild-Array enthält nur das erste Bild Rollen.

Verwenden Sie API Mesh und die GraphQL-Kern-API für:

- Mindestpreis
- Preisstufe
- Bundle-Produkte mit Festpreisen

Weitere Informationen und Beispiele finden Sie unter [Katalog-Service und API-Mesh](mesh.md).

### April 2024

**Veröffentlichungsdatum:**. April 2024
<!-- v1.18 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Es wurde Unterstützung für PHP 8.3 hinzugefügt.

![Neu](../assets/new.svg) Die [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/)- und [`refineProduct`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/)-Abfragen geben jetzt anpassbare Optionsdaten für einfache und komplexe Produkte zurück.<!--DATA-5538-->

### Februar 2024

**Veröffentlichungsdatum**: 22. Februar 2024
<!-- v1.17 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html) ist jetzt für Datenströme verfügbar (Produktempfehlungen, Live-Suche, Katalog-Service). Erfordert `catalog-service` Metapaket v3.1.0+.

**Veröffentlichungsdatum**: 13. Februar 2024
<!-- v1.16 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Produktvideos werden jetzt von der Catalog Service-API unterstützt.
![Beheben](../assets/fix.svg) Nicht vorrätige Optionen werden jetzt im PDP-Widget angezeigt.

#### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

- Die maximale Größe für die Payload dynamischer Attribute beträgt 9 MB.
- Gruppenproduktpreis. Dieser Wert kann mit einfachen Produktpreisen berechnet werden.
- In einem Bild-Array enthält nur das erste Bild Rollen.

Verwenden Sie API Mesh und die GraphQL-Kern-API für:

- Mindestpreis
- [Preisstufe](mesh.md)

### Oktober 2023

**Veröffentlichungsdatum:**. Oktober 2023
<!-- v1.13 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Der Katalog-Service unterstützt das `inStock`-Flag für Produktvarianten.
![Neu](../assets/new.svg) Die Felder `urlKey` und `externalId` wurden zum GraphQL-Schema hinzugefügt.
![Neu](../assets/new.svg) Herunterladbare Produkte und Geschenkkarten werden jetzt unterstützt.

### September 2023

**Veröffentlichungsdatum:**. September 2023
<!-- v1.12 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Der Katalog-Service verwendet jetzt [SaaS-Preisindizierung](../price-index/price-indexing.md).
![Behebung](../assets/fix.svg) Diese Version enthält Fehlerbehebungen und Verbesserungen auf der Service-Seite.

### Juli 2023

**Veröffentlichungsdatum**: 18. Juli 2023
<!-- v1.11 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Der Katalog-Service unterstützt jetzt die [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) GraphQL-Abfrage für Produktempfehlungen.

### Juni 2023

**Veröffentlichungsdatum**: 27. Juni 2023
<!-- v1.10 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die Catalog Service-API unterstützt jetzt `related products`.

### April 2023

**Veröffentlichungsdatum:**. April 2023
<!-- v1.7 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Der Katalog-Service bereinigt jetzt gelöschte Produktvarianten.
![Behebung](../assets/fix.svg) Infrastrukturskalierbarkeit und Leistungsverbesserungen.

### März 2023

**Veröffentlichungsdatum**: 28. März 2023
<!-- v1.6 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Zur [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) Abfrage wurden Farbfelder hinzugefügt.
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, `entityId` mithilfe von [API Mesh) &#x200B;](mesh.md).

**Veröffentlichungsdatum:**. März 2023
<!-- v1.5 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Funktion [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL hinzugefügt.
![Behebung](../assets/fix.svg) Verbesserte Leistung und API-Skalierbarkeit.

### Februar 2023

**Veröffentlichungsdatum**: 7. Februar 2023
<!-- v1.4 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Veröffentlichtes Katalog-Service-Metapaket zur Vereinfachung der Installationsschritte.
![Fix](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Januar 2023

**Veröffentlichungsdatum**: 17. Januar 2023
<!-- v1.3 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Das Onboarding wurde vereinfacht und verbessert.
![Neu](../assets/new.svg) Neue Kunden-Sandbox-Endpunkte sind für Vorproduktionstests verfügbar.
![Neu](../assets/new.svg) Unterstützung für virtuelle Produkte hinzugefügt.
![Fix](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### November 2022

**Veröffentlichungsdatum**: 18. November 2022
<!-- v1.1 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Der Katalog-Service unterstützt jetzt das Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fix](../assets/fix.svg) Verbesserte API-Skalierbarkeit und Gesamtleistung.

### Oktober 2022

**Veröffentlichungsdatum:**. Oktober 2022
<!-- v1.0 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Unterstützung für gebündelte und gruppierte Produkte.
![Neu](../assets/new.svg) Es wurden Überschreibungen der B2B-Sichtbarkeit hinzugefügt. Produkte können jetzt durchsucht und für bestimmte Kundengruppen zum Warenkorb hinzugefügt werden.
![Fix](../assets/fix.svg) Service ist jetzt stabiler und hat die Leistung verbessert.

### September 2022

**Veröffentlichungsdatum:**. September 2022
<!-- v0.3 -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Variantenbilder: Produktbilder werden basierend auf ausgewählten Optionen zurückgegeben.
![Neu](../assets/new.svg) Preisrollen: Nur Mitglieder bestimmter Kundengruppen können Produktpreise sehen.
![Behebung](../assets/fix.svg) Verbesserte Stabilität und Leistung des Service.
![Neu](../assets/new.svg) Aktualisierungen werden empfangen, wenn Produkte aus dem Katalog gelöscht werden.

### August 2022

**Veröffentlichungsdatum:**. August 2022
<!-- Beta -->

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Die `products`- und `refineProduct`-Abfragen geben die folgenden Daten zurück:

- Vordefinierte (System-)Produktattribute.
- Dynamische Produktattribute und deren Filterung nach Rolle (Produktanzeigeseite/Produktlistenseite).
- Produktoptionen.
- Produktbilder und Filtern nach Rolle (PDP/PLP).
- Ein spezifischer Preis für einfache Produkte und Preisspannen für konfigurierbare Produkte.
- Kundengruppenpreise und Preisspannen. Sie geben einen standardmäßigen Fallback-Preis für Käufer ohne Kundengruppe zurück.
- Produkttypen, die B2B-kundenspezifische Preise verwenden.

+++

## Catalog Service-Metapaket

Aktualisierungen des Katalog-Service PHP-Metapakets (`magento/catalog-service`).

- Für Kunden von Adobe Commerce as a Cloud Service wird die neueste Version in Ihrer Umgebung installiert.

- Für Adobe Commerce in der Cloud oder On-Premise empfiehlt Adobe die Verwendung von Composer , um das Catalog Service-Metapaket in Ihren Cloud-Umgebungen auf die neueste Version zu aktualisieren.

### Version v3.4.0

**Veröffentlichungsdatum:**. Juni 2026

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) **Unterstützung für die Überwachung des Synchronisierungsstatus von Daten-Feeds** - Die Abhängigkeiten des Metapakets für den Katalog-Service wurden aktualisiert und enthalten nun die Data Exporter Status-Erweiterung (`magento/module-data-exporter-status`). Dies ermöglicht [Überwachung des Status der Daten-Feed](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status)Synchronisierung durch den Commerce-Administrator, ohne dass zusätzliche Installations- oder Konfigurationsschritte erforderlich sind

![Neu](../assets/new.svg) Abhängigkeiten wurden aktualisiert, um die Kompatibilität zwischen dem Katalog-Service und Ihrem Commerce-Stack zu gewährleisten.

### Version v3.3.0

**Veröffentlichungsdatum:**. Oktober 2025

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) **Data Services-Upgrade** - `magento/data-services` auf ^8.0.0 aktualisiert. Überprüfen Sie vor dem Upgrade die Verwendung der Umgebung und der benutzerdefinierten Data Services-API auf Kompatibilität mit 8.x.

![Neu](../assets/new.svg) Aktualisierte Version und Metadaten für die Version 3.3.0.

### Version v3.2.0

**Veröffentlichungsdatum:**. April 2024

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Version und Metadaten aktualisiert für 3.2.0. Keine weiteren Abhängigkeitsänderungen.

### Version v3.1.0

**Veröffentlichungsdatum**: 26. Januar 2024

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Neue Paketabhängigkeiten hinzugefügt:

- **Category Permission Data Exporter** (`magento/module-category-permission-data-exporter`) zum Exportieren von Kategorieberechtigungsdaten, die vom Katalog-Service verwendet werden.
- **Catalog Sync Admin** `magento/module-catalog-sync-admin` für die Admin-Benutzeroberfläche und Konfiguration im Zusammenhang mit der Katalogsynchronisierung.

![Neu](../assets/new.svg) Aktualisierte Version und Metadaten für die Version 3.1.0.

## Installationsprogramm für den Katalog-Service

Das Installationsprogramm wird mit der Catalog Service-Erweiterung bereitgestellt und verarbeitet Installations- und Umgebungsprüfungen, damit der Katalog-Service mit Ihrem Commerce-Stack übereinstimmt.

- Für **Kunden von Adobe Commerce** as a Cloud Service) wird die neueste Installationsprogrammversion in Ihrer Umgebung installiert.

- Halten Sie bei **Adobe Commerce in der Cloud** Infrastruktur oder **On-Premise** das Installationsprogramm mit dem Metapaket [Katalog-Service) &#x200B;](#catalog-service-metapackage).

Jedes Mal, wenn Sie Composer zum Aktualisieren des `magento/catalog-service` verwenden, wird das Installationspaket automatisch auf die neueste Version aktualisiert. Sie können Composer auch verwenden, um `magento/catalog-service-installer` separat zu aktualisieren, wenn diese Versionshinweise eine Änderung beschreiben, die Sie benötigen, z. B. Unterstützung für eine neue PHP-Version. Auf diese Weise bleiben Ihre Installations-Tools mit der von Ihnen ausgeführten Version des Katalog-Service kompatibel.

### Version v1.0.6

**Veröffentlichungsdatum**: 25. März 2026

![Neu](../assets/new.svg) **PHP 8.5** - Stellt Kompatibilität sicher, wenn der Catalog Service auf PHP 8.5 läuft.

## Verwandte Dokumentation

- Informationen zu Projekten, die in **Adobe Commerce in der Cloud, lokal oder in Adobe Commerce as a Cloud Service bereitgestellt werden, finden Sie in der folgenden Dokumentation:

   - [Handbuch zum Katalog-Service](overview.md)
   - [Catalog Service GraphQL-API-Referenz](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/)
   - [Adobe Commerce-Administratorhandbuch](https://experienceleague.adobe.com/en/docs/commerce-admin/)
   - [Handbuch zu Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/)
   - [Handbuch zu Adobe Commerce in Cloud Manager](https://experienceleague.adobe.com/en/docs/commerce-cloud/)

- Informationen zu Projekten, die **Adobe Commerce Optimizer** oder **Adobe Commerce Optimizer Connector** verwenden, finden Sie in der folgenden Dokumentation:

   - [Entwicklerhandbuch für Merchandising-Services](https://developer.adobe.com/commerce/services/optimizer/)
   - [Merchandising GraphQL API-Referenz](https://developer.adobe.com/commerce/services/reference/graphql/)
   - [Handbuch zu Adobe Commerce Optimizer](../optimizer/overview.md)
