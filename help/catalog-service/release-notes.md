---
title: '[!DNL Commerce Storefront Catalog Service Release Notes]'
description: Die neuesten Versionsinformationen für  [!DNL Catalog Service]  für Adobe Commerce.
feature: Services, Catalog Service, Release Notes
exl-id: 74f2e46a-5592-4857-a6d7-b95b85d8b4cc
source-git-commit: 7b05da07d185c5495642037c6ef3b7ff5fcaa8e6
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 0%

---

# [!DNL Commerce Storefront Catalog Service] Versionshinweise

In diesen Versionshinweisen werden die neuesten Aktualisierungen des Commerce Catalog Service behandelt, darunter:

- **Versionen des Storefront Catalog Service**

   - Verbesserungen des Catalog Service-API-Schemas für einen verbesserten Datenabruf.
   - Verbesserungen der Sicherheit, Leistung und Zuverlässigkeit für die Catalog Service-API und die zugrunde liegende Infrastruktur.

- **Catalog Service Metapaket-Versionen**

   - Abhängigkeiten wurden aktualisiert, um die Leistung, Stabilität und Kompatibilität mit anderen Adobe Commerce-Komponenten zu verbessern.

Aktualisierungen werden nach Typ kategorisiert:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bug](../assets/bug.svg) Bekannte Probleme

Unterstützung wird für die neueste Version bereitgestellt. Versionshinweise für ältere Versionen sind als Referenz enthalten.

## Storefront Catalog Service

### Version 1.47

_12. Februar 2025_

![Neu](../assets/new.svg) Der API-Service unterstützt jetzt den `CategoryProductView` und ermöglicht erweiterte Ansichten und Abfragen für Produkte nach Kategorie. Diese Aktualisierung ermöglicht es Entwicklerinnen und Entwicklern, Produktdaten basierend auf der Kategorie effizient abzurufen und zu filtern, was die Flexibilität und Leistung für kategoriegesteuerte Anwendungsfälle verbessert. Weitere Informationen finden Sie unter [Implementieren von Kategorien in der Storefront](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/categories-storefront-implementation/). Wird nur bei Commerce-Implementierungen mit dem [zusammensetzbaren Katalogdatenmodell](https://developer.adobe.com/commerce/services/optimizer/) für Headless-Storefronts unterstützt<!--DATA-6949-->

### Version 1.46

_11. Dezember 2025_

![Fix](../assets/fix.svg) Verbesserungen auf Systemebene und Infrastrukturverbesserungen zur Verbesserung von Leistung und Stabilität. <!--DATA-6852, DATA-6864-->

### Version 1.45

_17. November 2025_

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

### Version 1.44

_6. November 2025_

![Fix](../assets/fix.svg) Verbesserungen auf Systemebene und Infrastrukturverbesserungen zur Verbesserung von Leistung und Stabilität. <!--DATA-6852, DATA-6864-->

### Version 1.43

_3. November 2025_

![Neu](../assets/new.svg) **Produktebenen für die mehrdimensionale Produktanpassung** - Es wurde Unterstützung für die kanalspezifische, gebietsschemasensitive Inhaltsbereitstellung für Adobe Commerce Optimizer-Implementierungen hinzugefügt.<!--DATA-6632-->

- Bereitstellen verschiedener Produktinhalte für verschiedene Kundensegmente
- Anwenden von gebietsschemaspezifischen Anpassungen ohne Duplizieren von Basisdaten
- Überschreibungen auf Feldebene mit Ebenenmasken steuern
- Unterstützung für Premium-, Saison- und Mobile-optimierte Inhaltsebenen

  Ebenen werden mit der vorhandenen `products` Abfrage abgerufen, werden Server-seitig aus Anfrage-Headern angewendet und erfordern keine Schemaänderungen. Siehe [Katalogebene](https://experienceleague.adobe.com/de/docs/commerce/optimizer/setup/catalog-layer) im _Adobe Commerce Optimizer-Handbuch_.

![Korrigieren](../assets/fix.svg) Gruppierte Produkte können jetzt abgefragt werden, wenn das übergeordnete Element keine Preise hat. Untergeordnete Produkte geben ihre eigenen Sichtbarkeitsrollen zurück.<!--DATA-6779-->

![Fix](../assets/fix.svg) Verbesserungen auf Systemebene und Infrastrukturverbesserungen zur Verbesserung von Leistung und Stabilität. <!--DATA-6721, DATA-6864-->

### Version 1.42

_8. September 2025_

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

### Version 1.41

_2. September 2025_

![Behebung](../assets/fix.svg) **Verbesserte Fehlerbehandlung bei fehlenden Preisinformationen** - Wenn die Preisdaten noch nicht eingegangen sind, gibt die API `null` für das Preisfeld zurück, anstatt einen Fehler auszulösen, sodass Kunden fehlende Daten ordnungsgemäß verarbeiten können.<!--DATA-6612-->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um die Leistung und Stabilität zu verbessern.<!--DATA-6671-->

### Version 1.40

_30. Juli 2025_

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6619-->

### Version 1.39

_24. Juli 2025_

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

### Version 1.38

_15. Juli 2025_

![Neu](../assets/new.svg) **Produkttypen für Geschenkkarten**-Katalog-Storefront-Service unterstützt jetzt Produktattribute als JSON-Objekte oder Arrays und ermöglicht so eine flexible Verwaltung komplexer Typen wie Geschenkkarten.<!--DATA-6573-->


### Version 1.37

_20. Juni 2025_

![Neu](../assets/new.svg) **Hierarchische Preisbuchkonfiguration** - Präzise Preisbereiche für über- und untergeordnete Preisbücher. Berechnungen berücksichtigen Hierarchie und übernommene Regeln; reduziert Preisfehler, wenn mehrere Preisbücher verknüpft sind. Nur Adobe Commerce Optimizer. Siehe [Preisbücher](https://experienceleague.adobe.com/de/docs/commerce/optimizer/setup/pricebooks).

![Neu](../assets/new.svg) **Schlüssel ohne Unterscheidung von Groß- und Kleinschreibung** - Bei Schlüsselsuchen in Abfragen wird jetzt nicht mehr zwischen Groß- und Kleinschreibung unterschieden, wodurch Fehler durch Schlüsselschreibungen reduziert werden. <!--DATA-6494, DCAT-2495-->

### Version 1.36

_20. Juni 2025_

![Neu](../assets/new.svg) **Öffentliche I/O-Ereignisse für Katalog-Storefront** - Es wurden öffentliche I/O-Ereignisse für die Echtzeit-Integration und -Beobachtbarkeit (CSS und EDS) hinzugefügt.<!--DATA-6329-->

![Neu](../assets/new.svg) **Server-Side Rendering (SSR)** - Architektonische Verbesserungen zur Unterstützung von SSR für bessere Leistung, SEO und UX in großen Katalogen.<!--DATA-6278, DATA-6280-->

![Neu](../assets/new.svg) **Infrastruktur und Sicherheit** - Neue AWS-Rollen, ServiceNow-Integration und CI/CD-Pipelines für den Ereignis-Service.

![Neu](../assets/new.svg) **Ereignisformate und Beobachtbarkeit** - Optimierte Payloads, verbesserte Überwachung, verbesserte Variantenereignisdaten.<!--DATA-6332, DATA-6402, -->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6404, DATA-6410, -->

+++ Frühere Versionen

## Version 1.35

_13. Juni 2025_

![Neu](../assets/new.svg) **Nicht zwischengespeicherte Daten abrufen**-Aktivieren Sie die `Magento-Is-Preview`-Kopfzeile, um nicht zwischengespeicherte Daten vom Katalog-Endpunkt an den Suchdienst zu übergeben.<!--DATA-6345-->

![Neu](../assets/new.svg) **Produktoptionen mit Mehrfachauswahl**-GraphQL-API macht jetzt verfügbar, ob Produktoptionen mehrere Auswahlen zulassen (z. B. Bundle „mehrere Elemente auswählen„).<!--DATA-6487-->

![Neu](../assets/new.svg) Aktualisierte Preisvalidierung bei der Datenaufnahme, um Produkte ohne Preise zu unterstützen.<!--DATA-6098-->

![Behebung](../assets/fix.svg) Verbesserte Fehlerbehandlung für einfache Paketpreise in Adobe Commerce Optimizer.<!--DATA-6541-->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6273, DATA-6485, -->

## Version 1.34

_23. März 2025_

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-5732-->

## Version 1.33

_29. April 2025_

![Behebung](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur. Die Infrastruktur unterstützt jetzt extrem große Kataloge (bis zu ~440 Millionen SKUs), ohne die vorhandene Arbeitslast zu beeinträchtigen.

### Version 1.32

_28. März 2025_

![Beheben](../assets/fix.svg) Attribute ohne Rollen werden für den zusammenstellbaren Katalog nicht mehr standardmäßig indiziert. Dies verbessert die Indizierungszeit und reduziert den Speicher. Altes Verhalten kann über ein Feature Flag wieder aktiviert werden.

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern. <!--DATA-6348, DATA-6440, DATA-6446, DATA-6641-->

### Version 1.31

_18. Februar 2025_

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6389, DATA-6367, DATA-6373-->

### Version 1.30

_9. Dezember 2024_

Hauptversion: [Zusammensetzbares Katalogdatenmodell](https://developer.adobe.com/commerce/services/optimizer/) für Headless-Storefronts, Header-Management und die Handhabung von Produktdaten.

![Neu](../assets/new.svg) **Zusammensetzbares Katalogdatenmodell (CCDM)** - Unterstützt Kunden bei der Verwendung des zusammensetzbaren Katalogs für Headless-Storefronts. Neue Endpunkte akzeptieren Katalogansicht- und Richtlinien-IDs (abwärtskompatibel). Konfigurierbare Produktdetails und Preise mit integrierter Paginierung.<!--DATA-6018, DATA-6288-->

![Neu](../assets/new.svg) **Kopfzeilenverwaltung**-`AC-Locale` für zusammenstellbare Katalog-API-Vorgänge in `AC-Scope-Locale` umbenannt. Kopfzeilenzuordnung und Standardwerte wurden angegeben.<!--DATA-6303, DATA-6078-->

![Neu](../assets/new.svg) **Produktdaten und Preise**-Unterstützung für zusammenstellbares Katalogdatenmodell und verbesserte Preisverwaltung für konfigurierbare Produkte.<!--DATA-6279-->

`CurrencyEnum` wurde aktualisiert, um `NONE` für Produktsuchabfragen zu unterstützen, die an der Verbundlogik ausgerichtet sind.<!--DATA-6285-->

![Behebung](../assets/fix.svg) **Infrastruktur und Upgrades** - Verbesserungen auf Systemebene für Sicherheit, Leistung und Stabilität.

![Fix](../assets/fix.svg) Bundle-Produktoptionen zeigen jetzt nur noch aktivierte Produkte an.<!--DATA-6347-->

### Version 1.29

_9. Dezember 2024_

![Neu](../assets/new.svg) **Bildreihenfolge in Produktabfragen** - Produktbilder im Feld &quot;GraphQL-`images`&quot; folgen jetzt der `sortOrder` für den Katalogexport, um ein konsistentes Verhalten bei Storefronts und APIs zu gewährleisten.<!--DATA-6258-->

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6619-->

### Version 1.28

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6180, DATA-6230, DATA-6254, DATA-6257-->

### Version 1.27

_26. September 2024_

![Beheben](../assets/fix.svg) Verbesserungen auf Systemebene und in der Infrastruktur, um Sicherheit, Leistung und Stabilität zu verbessern.<!--DATA-6243-->

### Version 1.26

_22. Oktober 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Das GraphQL-Schema enthält jetzt `lastModifiedAt` in Produktinformationen für genaue Sitemaps und die Neuindizierung von Suchmaschinen (z. B. Google). <!--DATA-6209-->

### Version 1.23

_22. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Fix](../assets/fix.svg) Produktinformationen können jetzt ohne Produktüberschreibungsdaten (Preise) abgerufen werden. Zuvor haben diese Abfragen Folgendes zurückgegeben: `The following sku does not have product override data in the DB: <SKU value>. Make sure data is synced.` <!--DATA-6121-->

### Version 1.22

_13. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Unterstützung zum Abrufen aller Varianten nach Produkt-SKU hinzugefügt. Siehe die [Catalog Service API-Referenz](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/). <!--DATA-6067-->

### Version 1.19

_23. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer


![Beheben](../assets/fix.svg) <!--DATA-5033-->Das `InStock` für Optionswerte berücksichtigt jetzt den `enabled` der Produktvariante.

![Fix](../assets/fix.svg) <!--DATA-5888-->Unterstützung für Produktpreise mit bis zu 16 Stellen und 4 Dezimalstellen hinzugefügt. Synchronisieren Sie über das [Data Management-Dashboard](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard) oder [CLI](../landing/catalog-sync.md#command-line-interface) neu, um Aktualisierungen anzuwenden.

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

### Version 1.18

_11. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Es wurde Unterstützung für PHP 8.3 hinzugefügt.

![Neu](../assets/new.svg) Die [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/)- und [`refineProduct`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/)-Abfragen geben jetzt anpassbare Optionsdaten für einfache und komplexe Produkte zurück.<!--DATA-5538-->

### Version 1.17

_22. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html?lang=de) ist jetzt für Datenströme verfügbar (Produktempfehlungen, Live-Suche, Katalog-Service). Erfordert `catalog-service` Metapaket v3.1.0+.

### Version v1.16

_13. Februar 2024_

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

### Version 1.13

_12. Oktober 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Der Katalog-Service unterstützt das `inStock`-Flag für Produktvarianten.
![Neu](../assets/new.svg) Die Felder `urlKey` und `externalId` wurden zum GraphQL-Schema hinzugefügt.
![Neu](../assets/new.svg) Herunterladbare Produkte und Geschenkkarten werden jetzt unterstützt.

### Version 1.12

_19. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Der Katalog-Service verwendet jetzt [SaaS-Preisindizierung](../price-index/price-indexing.md).
![Behebung](../assets/fix.svg) Diese Version enthält Fehlerbehebungen und Verbesserungen auf der Service-Seite.

### Version 1.11

_18. Juli 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Der Katalog-Service unterstützt jetzt die [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) GraphQL-Abfrage für Produktempfehlungen.

### Version 1.10

_27. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die Catalog Service-API unterstützt jetzt `related products`.

### Version v1.7

_12. April 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Der Katalog-Service bereinigt jetzt gelöschte Produktvarianten.
![Behebung](../assets/fix.svg) Infrastrukturskalierbarkeit und Leistungsverbesserungen.

### Version v1.6

_28. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Zur [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) Abfrage wurden Farbfelder hinzugefügt.
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, `entityId` mithilfe von [API Mesh) &#x200B;](mesh.md).

### Version v1.5

_6. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Funktion [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL hinzugefügt.
![Behebung](../assets/fix.svg) Verbesserte Leistung und API-Skalierbarkeit.

### Version v1.4

_7. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Veröffentlichtes Katalog-Service-Metapaket zur Vereinfachung der Installationsschritte.
![Fix](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version 1.3

_17. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Das Onboarding wurde vereinfacht und verbessert.
![Neu](../assets/new.svg) Neue Kunden-Sandbox-Endpunkte sind für Vorproduktionstests verfügbar.
![Neu](../assets/new.svg) Unterstützung für virtuelle Produkte hinzugefügt.
![Fix](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version v1.1

_18. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Der Katalog-Service unterstützt jetzt das Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fix](../assets/fix.svg) Verbesserte API-Skalierbarkeit und Gesamtleistung.

### Version 1.0

_4. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Unterstützung für gebündelte und gruppierte Produkte.
![Neu](../assets/new.svg) Es wurden Überschreibungen der B2B-Sichtbarkeit hinzugefügt. Produkte können jetzt durchsucht und für bestimmte Kundengruppen zum Warenkorb hinzugefügt werden.
![Fix](../assets/fix.svg) Service ist jetzt stabiler und hat die Leistung verbessert.

### Version 0.3 - Beta+

_12. September 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Variantenbilder: Produktbilder werden basierend auf ausgewählten Optionen zurückgegeben.
![Neu](../assets/new.svg) Preisrollen: Nur Mitglieder bestimmter Kundengruppen können Produktpreise sehen.
![Behebung](../assets/fix.svg) Verbesserte Stabilität und Leistung des Service.
![Neu](../assets/new.svg) Aktualisierungen werden empfangen, wenn Produkte aus dem Katalog gelöscht werden.

### Beta-Version

_9. August 2022_

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

- Für lokale Adobe Commerce on Cloud-Standorte empfiehlt Adobe die Verwendung von Composer , um das Metapaket Catalog Service in Ihren Cloud-Umgebungen auf die neueste Version zu aktualisieren.

### Version v3.3.0

_14. Oktober 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) **Data Services-Upgrade** - `magento/data-services` auf ^8.0.0 aktualisiert. Überprüfen Sie vor dem Upgrade die Verwendung der Umgebung und der benutzerdefinierten Data Services-API auf Kompatibilität mit 8.x.
Tee
![Neu](../assets/new.svg) Aktualisierte Version und Metadaten für die Version 3.3.0.

### Version v3.2.0

_12. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Version und Metadaten aktualisiert für 3.2.0. Keine weiteren Abhängigkeitsänderungen.

### Version v3.1.0

_26. Januar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Neue Paketabhängigkeiten hinzugefügt:

- **Category Permission Data Exporter** (`magento/module-category-permission-data-exporter`) zum Exportieren von Kategorieberechtigungsdaten, die vom Katalog-Service verwendet werden.
- **Catalog Sync Admin** `magento/module-catalog-sync-admin` für die Admin-Benutzeroberfläche und Konfiguration im Zusammenhang mit der Katalogsynchronisierung.

![Neu](../assets/new.svg) Aktualisierte Version und Metadaten für die Version 3.1.0.

## Verwandte Dokumentation

- Informationen zu Projekten, die in **Adobe Commerce in der Cloud, lokal oder in Adobe Commerce as a Cloud Service bereitgestellt werden, finden Sie in der folgenden Dokumentation:

   - [Handbuch zum Katalog-Service](overview.md)
   - [Catalog Service GraphQL-API-Referenz](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/)
   - [Adobe Commerce-Administratorhandbuch](https://experienceleague.adobe.com/en/docs/commerce-admin/)
   - [Handbuch zu Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/)
   - Handbuch zu [Adobe Commerce in Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud/)

- Informationen zu Projekten, die **Adobe Commerce Optimizer** oder **Adobe Commerce Optimizer Connector** verwenden, finden Sie in der folgenden Dokumentation:

   - [Merchandising-Services-Entwicklerhandbuch](https://developer.adobe.com/commerce/services/optimizer/)
   - [Merchandising-GraphQL-API-Referenz](https://developer.adobe.com/commerce/services/reference/graphql/)
   - [Handbuch zu Adobe Commerce Optimizer](../optimizer/overview.md)
