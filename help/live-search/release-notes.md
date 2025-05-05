---
title: '[!DNL Live Search] Versionshinweise'
description: Die neuesten Versionsinformationen für  [!DNL Live Search]  von Adobe Commerce.
feature: Services, Search, Release Notes
exl-id: 099cf79c-968c-4381-b66d-7f6141ad2db3
source-git-commit: bf36d522b45218a10bde7a383feca99bdba62aa6
workflow-type: tm+mt
source-wordcount: '2460'
ht-degree: 0%

---

# [!DNL Live Search] Versionshinweise

In diesen Versionshinweisen werden die neuesten Versionen von [!DNL Live Search] beschrieben.
Unterstützung wird für die aktuelle Hauptversion bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bug](../assets/bug.svg) Bekannte Probleme

## Gehostete Service-Aktualisierungen

Diese Hinweise beschreiben Aktualisierungen, die außerhalb einer versionierten Version veröffentlicht wurden, oder Verbesserungen am gehosteten Service.

_29. April 2025_

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei **der Bericht „In CSV**&quot; auf der Registerkarte [**Leistung**](./performance.md) nicht alle im Datumsbereich angegebenen Daten enthielt.
![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Sie eine [Merchandising-Regel“ nicht speichern konnten](./rules.md) wenn der Suchabfragefilter verwendet wurde.
![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei [angeheftete Produkte](./facets-manage.md#pinunpin-facet) oben auf der Ergebnisseite nicht aufgeführt wurden.

_21. April 2025_

![Korrigieren](../assets/fix.svg) Es wurde ein Problem mit dem Bereichsfilter für Preise behoben, sodass Produkte, die gleich dem oberen Bereich sind, nicht in den Ergebnissen enthalten sind. Diese Änderung entspricht der Definition der Preisbereiche für Facetten.

_3. April 2025_

![Behebung](../assets/fix.svg) Die SaaS-Datenexporterweiterung wurde aktualisiert, um die Einschränkung „Produkte müssen der Stammkategorie zugewiesen werden“ [Einschränkung](boundaries-limits.md#b2b-and-category-permissions) für B2B-Händler zu entfernen. Unter [Verwalten der Datenexporterweiterung](../data-export/manage-extension.md) erfahren Sie, wie Sie die SaaS-Datenexporterweiterung auf Version 103.4.0 oder höher aktualisieren.

_20. Februar 2025_

![Neu](../assets/new.svg) Commerce unterstützt Synonyme mit mehreren Wörtern. [Weitere Informationen](synonyms-type.md#multi-word-synonym-behavior). Unterstützung für Synonyme mit mehreren Wörtern ist erst nach dem Veröffentlichungsdatum des 20. Februar verfügbar. Alle vorhandenen Synonyme mit mehreren Wörtern benötigen eine vollständige Neuindizierung, die Sie anfordern können, indem Sie [ein Support-Ticket erstellen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).

_31. Januar 2025_

![Neu](../assets/new.svg) Es gibt eine neue Richtlinie zur Datenaufbewahrung für nicht abgefragte Katalogdaten in Ihrer Testumgebung. [Weitere Informationen](overview.md#catalog-data-retention-policy).

_19. September 2024_

![Neu](../assets/new.svg) Eine Beta-Version, die drei neue Suchfunktionen unterstützt: geschichtet, beginnt mit und enthält. [Weitere Informationen](install.md#install-the-live-search-beta).

_4. September 2024_

![Korrigieren](../assets/fix.svg) Die maximale Anzahl der Buckets, die (innerhalb einer Facette[ zurückgegeben werden können, wurde ](boundaries-limits.md#facets) 100 erhöht.

_7. August 2024_

![Fix](../assets/fix.svg) Der maximale Intervallwert oder die Preisspanne für [Preisfacettierung“ wurde ](settings.md#price-faceting) 10.000 auf 40.000.000 erhöht.

_13. Februar 2024_

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt das Festlegen einer Standardregel für [Search-Merchandising](rules.md).

_12. Oktober 2023_

![Neu](../assets/new.svg) Commerce-Admins können jetzt die Sprache des Index für die [!DNL Live Search] angeben. Siehe [Einstellungen](settings.md).
![Fehlerbehebung](../assets/fix.svg) Die Registerkarte „Suchregeln“ wurde in „Merchandising suchen“ umbenannt.

_13. Juni 2023_

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem einige Zeichen wie Anführungszeichen oder Apostrophe Ranking-Probleme verursachten. Die Neuindizierung löst diese Probleme.

_25. April 2023_

![Neu](../assets/new.svg) [!DNL Live Search] Kunden können jetzt den neuen [SaaS-Preisindexer](../price-index/price-indexing.md) nutzen.

### PLP-Widget

_31. Mai 2024_

![Neu](../assets/new.svg) Version 2.0.0 des PLP-Widgets veröffentlicht, das Unterstützung für die folgenden Funktionen hinzufügt:

- Schaltflächen zum Warenkorb hinzufügen - Nur für einfache Produkte verfügbar.
- Mehrere Bilder pro Produkt - Das Bild kann sich ändern, wenn für ein konfigurierbares Produkt eine andere Farbe ausgewählt wird.

_27. Oktober 2023_

![Neu](../assets/new.svg) Das [!DNL Live Search] PLP-Widget unterstützt jetzt Farbfelder.

## [!DNL Live Search] 4.3.0

_11. März 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Fix](../assets/fix.svg) [!DNL Live Search] unterstützt jetzt PHP 8.4 für Installationen mit Adobe Commerce 2.4.8-beta2.
![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem der Suchadapter nicht mit `psr/http-message:2.0` kompatibel war.

## [!DNL Live Search] 4.2.3

_13. Februar 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem auf der Seite mit den Bestelldetails die Bestellnummer, das Datum und die Schaltfläche &quot;**[!UICONTROL Reorder]**&quot; fehlte.

## [!DNL Live Search] 4.2.2

_6. Januar 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, das zu einem Fehler bei der `categoryList` GraphQL-Abfrage in Adobe Commerce Version 2.4.5 und früher führte.

## [!DNL Live Search] 4.2.1

_31. Juli 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, bei dem bestimmte Skripte nicht auf der Kaufbestätigungsseite geladen wurden.
![Beheben](../assets/fix.svg) Es wurde eine Abhängigkeitsversion in der `composer.json`-Datei behoben.

## [!DNL Live Search] 4.2.0

_31. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die Live Search-Erweiterung wurde aktualisiert, um PLP-Widgets der Version 2.0.0 zu verwenden.

## [!DNL Live Search] 4.1.2

_16. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

### Updates

![Korrigieren](../assets/fix.svg) Die [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-by-categories) GraphQL-Abfrage wurde korrigiert, damit sie korrekt nach `categoryPath` und `categoryList` für Kategorien gefiltert wird.

## [!DNL Live Search] 4.1.1

_19. März 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

### Neue Funktionen

![Neu](../assets/new.svg) Sprachunterstützung für Polnisch hinzugefügt.
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt PHP 8.3 für Installationen mit Adobe Commerce 2.4.4.

## [!DNL Live Search] 4.1.0

_22. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

### Neue Funktionen

![Neu](../assets/new.svg) Die [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-dashboard) ist jetzt verfügbar. Dieses überarbeitete Dashboard bietet Einblicke in Datenströme für [!DNL Product Recommendations], [!DNL Live Search] und [!DNL Catalog Service].

### Updates

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, das einen Fehler verursachte, wenn Gastbenutzer in nicht standardmäßigen Store-Ansichten Produkte zu einem Warenkorb hinzugefügt haben.
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, das dazu führte, dass das Such-Pop-up unabhängig von den Gebietsschemaeinstellungen immer das Währungssymbol vor dem Preiswert anzeigte.
![Beheben](../assets/fix.svg) Entfernte unnötige Typdefinitionen für deaktivierte Kern-Plug-ins, um Kompatibilitätsprobleme bei der Installation zu beheben.

## [!DNL Live Search] 4.0.0

_13. November 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

### Neue Funktionen

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt Farbfelder im PLP-Widget.
![Neu](../assets/new.svg) zeigt [!DNL Live Search] jetzt den Kategorienamen anstelle der Kategorie-ID an.
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt Durchstreichpreise im PLP-Widget.
![Neu](../assets/new.svg) Die Schaltfläche „Filter ausblenden“ wurde eingeführt, um das Bedienfeld „Filter“ auszublenden.


### Updates

![Beheben](../assets/fix.svg) Das [!DNL Live Search] PLP-Widget ist jetzt standardmäßig für Neuinstallationen aktiviert.
![Beheben](../assets/fix.svg) Der Suchadapter wird nicht mehr unterstützt. Ab nun wird der Suchadapter nur noch aktualisiert, um Sicherheitsprobleme zu beheben.
![Korrigieren](../assets/fix.svg) Neukonfigurierte CSS-Stile, um Widget-Klassen besser zu isolieren.
![Behebung](../assets/fix.svg) Kleinere Fehlerbehebungen

Aktivieren Sie nach der Installation von Version 3.1.1 oder höher die neuen Indexer:

- Produktpreise Futtermittel
- Umfang des Website-Daten-Feeds
- Umfänge des Kundengruppen-Daten-Feeds

Testen Sie nach dem Upgrade die aktualisierte Konfiguration in QA oder Staging, bevor Sie die Änderungen an die Produktion pushen.

+++3.1.1 und älter

### [!DNL Live Search] 3.1.1

_15. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die Registerkarte „Merchandising für neue Kategorien“ wurde hinzugefügt. Benutzer können jetzt intelligente und manuelle Rankings (Pin, Boost, Bury, Hide) pro Kategorie hinzufügen
![Neu](../assets/new.svg) Benutzer können eine einzelne Kategorieregel mit intelligenter oder manueller Rangfolge hinzufügen
![Neu](../assets/new.svg) Benutzende können jetzt intelligente Ranking-Regeln zu Unterkategorien hinzufügen
![Neu](../assets/new.svg) Beim Löschen von Unterkategorien mit intelligentem Ranking werden detaillierte Informationen bereitgestellt.
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, Regeln für geerbte Rangfolgestrategien zu löschen
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, Regeln für eine einzelne Kategorie zu löschen
![Neu](../assets/new.svg) Benutzer können jetzt nach Kategorienamen suchen, wenn sie eine Regel hinzufügen
![Neu](../assets/new.svg) Mit der Kategoriestruktansicht können Benutzer jetzt anzeigen, auf welche Kategorie Regeln angewendet wurden.
![Neu](../assets/new.svg) Die Kategorievorschau zeigt nur die ausgewählte Kategorie an.
![Neu](../assets/new.svg) Die Komponenten [Popover-Widget](https://github.com/adobe/aem-cif-guides-venia/pull/319) und [PLP-Widget](https://github.com/adobe/aem-cif-guides-venia/pull/320) von AEM CIF ermöglichen es AEM Sites, [!DNL Live Search] zu nutzen.

#### Updates

![Fix](../assets/fix.svg) Die Tabellengröße der Produkte und der Preis-Feeds wurde stark reduziert. Bei den Tabellen `catalog_data_exporter_products` und `catalog_data_exporter_product_prices` sollte eine erhebliche Größenreduzierung zu verzeichnen sein.
![Korrigieren](../assets/fix.svg) Die Registerkarte „Regeln“ wird in „Suchregeln“ umbenannt
![Beheben](../assets/fix.svg) Bei der Rangfolge nach „Trend“ können Sie jetzt zwischen folgenden Optionen wählen:
- 3 Tage (Standard)
- 14 Tage
- 30 Tage
![Beheben](../assets/fix.svg) „Ereignisse“ (Boost/Pin/Bury/Hide) wurde in „Manuelles Ranking“ umbenannt
![Behebung](../assets/fix.svg) „Ranking-Typ“ wurde in „Intelligentes Ranking“ umbenannt
![Behebung](../assets/fix.svg) Kleinere Fehlerbehebungen

### [!DNL Live Search] 3.1.0

_1. September 2023_

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

#### Updates

![Fehlerbehebung](../assets/fix.svg) Das Widget „Produktauflistung“ wurde aktualisiert, um die [Catalog Service-API“ ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) verwenden.

### [!DNL Live Search] 3.0.2

_7. August 2023_

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

#### Neue Funktionen

![Neu](../assets/new.svg) Die folgenden Werte wurden zum `storeDetails` hinzugefügt:

- „Alle Produkte pro Seite zulassen“
- Wechselkurs
- „Produkte pro Seite auf dem Raster: Zulässige Werte“
- „Produkte pro Seite im Raster - Standardwert“
- Sprache speichern

#### Updates

![Fix](../assets/fix.svg) Catalog Service-Module wurden dem Metapaket hinzugefügt, um den erweiterten Datenabruf zu unterstützen.
![Beheben](../assets/fix.svg) Die Seitennavigation **Mein Konto** wird bei Verwendung des Widgets Produktauflistungsseite nicht mehr ausgeblendet.

Händler müssen die [!DNL Live Search] Erweiterungsversion >= 3.0.2 aktualisieren, um auf diese Funktionen zugreifen zu können.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie zur Produktion pushen. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten nach der Überprüfung der Ergebnisse ihrer Testumgebung upzugraden.

#### Einschränkungen

Die Verwendung des Widgets Live Search Product Listing Page führt dazu, dass Google Tag Manager fehlschlägt. Verwenden Sie den standardmäßigen Suchadapter, wenn Google Tag Manager benötigt wird.

### [!DNL Live Search] 3.0.1

_14. März 2023_

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

#### Neue Funktionen

![Neu](../assets/new.svg) Produktartikelkarte in der Regelvorschau
![Neu](../assets/new.svg) [Widget „Produktauflistungsseite“](https://experienceleague.adobe.com/de/docs/commerce/live-search/live-search-storefront/plp-styling)
![Neu](../assets/new.svg) [Filteroptionen für Kategorien](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, Pin-Ereignisse per Drag-and-Drop zu erstellen
![Neu](../assets/new.svg) Neue Pin-Aktionen:
- An Punkt anheften - Schaltfläche „Anheften“ zum Erstellen eines Pin-Ereignisses mit einem Klick
- Nach oben stecken - Platziert das Produkt an der ersten Position
- An den Boden anheften - Platziert das Produkt am unteren Rand der Ergebnisse
- Ereignis mit einem Klick lösen
![Neu](../assets/new.svg) [Intelligente Rangfolge für Regeln](https://experienceleague.adobe.com/de/docs/commerce/live-search/live-search-admin/rules/rules-add)
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt vollständige [Inventory management](https://experienceleague.adobe.com/de/docs/commerce-admin/inventory/introduction)-Funktionen in Commerce (ehemals Multi-Source Inventory oder MSI). Um die vollständige Unterstützung zu aktivieren[ müssen Sie ](install.md#update) Abhängigkeitsmodul-`commerce-data-export` auf Version 102.2.0 oder höher aktualisieren.

#### Updates

![Korrigieren](../assets/fix.svg) Regeln konfigurieren sortiert nun automatisch Positionen eindeutig
![Beheben](../assets/fix.svg) Durch Löschen eines vorhandenen Ereignisses wird jetzt die Vorschau aktualisiert
![Beheben](../assets/fix.svg) Regeln ohne Ereignisse können gespeichert werden
![Korrigieren](../assets/fix.svg) Auswahl „Facettenart auswählen“ entfernen
![Korrigieren](../assets/fix.svg) Neuer Status „Bearbeiten“ für nicht gespeicherte Regeln hinzugefügt

#### Fehlerkorrekturen

![Beheben](../assets/fix.svg) Es wurde ein Server-Fehler behoben, bei dem ein nicht abgeschlossenes Ereignis beim Speichern auftrat
![Korrektur](../assets/fix.svg) Das Löschen eines bestimmten Ereignisses bei mehreren Ereignissen wurde korrekt behoben
![Korrigieren](../assets/fix.svg) Es wurde ein vorhandenes Regelereignis behoben, das nicht aktualisiert wird, wenn ein neues Ereignis hinzugefügt wurde.
![Beheben](../assets/fix.svg) Es wurde ein zweiter „Bearbeiten“-Klick aus Details behoben, für [!DNL Live Search] die Seite neu geladen werden musste.
![Korrigieren](../assets/fix.svg) Synonyme: Es wurde ein Problem behoben, bei dem Benutzende, die auf eine Eingabe geklickt hatten, den Fokus nicht auf das Feld zurücksetzen konnten
![Behebung](../assets/fix.svg) Weitere kleinere Fehlerbehebungen und Leistungsaktualisierungen
![Bug](../assets/bug.svg) - Die Rangfolge nach „Empfohlen für Sie“ wird nur innerhalb der Live-Such-Widgets unterstützt. Sie wird von der standardmäßigen Suchfunktion für Luma und PWA nicht unterstützt.
![Bug](../assets/bug.svg) - Benutzerdefinierte Preisattribut-Facetten werden in Luma nicht korrekt gerendert, aber die API filtert ordnungsgemäß darauf.

Händler müssen die [!DNL Live Search] Erweiterungsversion >= 3.0.1 aktualisieren, um auf diese Funktionen zugreifen zu können.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie zur Produktion pushen. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten nach der Überprüfung der Ergebnisse ihrer Testumgebung upzugraden.

### [!DNL Live Search] 2.0.5

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Beheben](../assets/fix.svg) - Die Live Search würde einen Fehler auslösen, wenn SDK-Ressourcen aufgrund von Netzwerkproblemen nicht verfügbar waren. Dieser Fehler wurde behoben.

Händler müssen ein Upgrade der Live Search-Erweiterung auf Version >= 2.0.5 durchführen, um auf diese Funktionen zugreifen zu können.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie zur Produktion pushen. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten nach der Überprüfung der Ergebnisse ihrer Testumgebung upzugraden.

### [!DNL Live Search] 2.0.4

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die Live-Suche unterstützt jetzt die Filterung nach der Einstellung „Nicht vorrätige Produkte anzeigen“ in der Admin-Liste. Wenn „Nicht vorrätige Produkte anzeigen“ auf „false“ gesetzt ist, wird `inStock = true` zum Filter hinzugefügt.
![Korrigieren](../assets/fix.svg) Um die Leistung zu verbessern, wurde der Block „Vorschläge“ aus dem Live Search-Popup entfernt. Die Daten werden weiterhin über GraphQL weitergeleitet, falls Sie die Funktion ersetzen möchten.
![Beheben](../assets/fix.svg) `categories` und `categoryPath` haben `categoryIds` für die Kategoriefilterung ersetzt. Weitere Informationen finden Sie unter [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/).
![Beheben](../assets/fix.svg) Zuvor erhielt ein Benutzer, der an eine B2B-Firma gebunden war, bei Suchvorgängen einen falschen Kundengruppen-Code. Die Live Search gibt jetzt den richtigen Wert zurück.
![Beheben](../assets/fix.svg) Zuvor gab die Live-Suche bei der Suche nach einem Begriff, der nicht vorhanden ist, einen Fehler zurück. Dieser Fehler wurde jetzt behoben.

Händler müssen die [!DNL Live Search] Erweiterungsversion >= 2.0.4 aktualisieren, um auf diese Funktionen zugreifen zu können.

Benutzern wird empfohlen, ein Upgrade durchzuführen und Tests durchzuführen, bevor sie zur Produktion wechseln. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten nach der Überprüfung der Ergebnisse ihrer Testumgebung upzugraden.

### [!DNL Live Search] 2.0.3

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die Live Search unterstützt jetzt B2B-Funktionen, indem Kategorieberechtigungen, freigegebene Kataloge und kundengruppenspezifische Preise berücksichtigt werden.

Händler müssen die [!DNL Live Search] Erweiterungsversion >= 2.0.3 aktualisieren, um auf diese Funktionen zugreifen zu können.

Benutzern wird empfohlen, ein Upgrade durchzuführen und Tests durchzuführen, bevor sie zur Produktion wechseln. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten nach der Überprüfung der Ergebnisse ihrer Testumgebung upzugraden.

### [!DNL Live Search] 2.0

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

Vorhandene [!DNL Live Search] müssen auf [!DNL Live Search] 2.0.0 aktualisiert werden, um die folgenden neuen Funktionen, Fehlerbehebungen und Verbesserungen nutzen zu können:

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt PHP 8.1 für Installationen mit Adobe Commerce 2.4.4.
![Neu](../assets/new.svg) Das `Magento_ElasticsearchCatalogPermissionsGraphQl` wird der Liste der Module hinzugefügt, die während der Installation deaktiviert sind.
![Neu](../assets/new.svg) Die Anzahl der verfügbaren Zeilen im [[!DNL storefront popover]](overview.md) kann über den *Admin* konfiguriert werden.
![Neu](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) wird für [!DNL Live Search] unterstützt.
![Neu](../assets/new.svg) Der [!DNL Live Search] wird mit erweiterten Prozessänderungen aktualisiert.
![Behebung](../assets/fix.svg) [Erweiterte Suche](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/catalog/search/search) Link wurde aus der Storefront-Fußzeile entfernt.
![Bug](../assets/bug.svg) Die folgenden Produktattribute werden von der [Commerce GraphQL-API nicht unterstützt](https://developer.adobe.com/commerce/services/graphql/live-search/) wenn sie in Bezug auf die Beta-Version von PWA verwendet werden: `description`, `name`, `short_description`
![Bug](../assets/bug.svg) Die Beta-Version von PWA für [!DNL Live Search] unterstützt nicht [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Beheben](../assets/fix.svg) [Benutzerdefiniertes Preisattribut](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/attributes-input-types) gibt keinen Fehler mehr zurück, wenn es als „Facette[ konfiguriert ](facets-add.md).
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, das dazu führte, dass ein Fehler auftrat, wenn [Währungssymbol](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration#step-5-customize-currency-symbols-optional) (`data-currency-symbol`) verfügbar war.
![Fix](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) zeigt jetzt den [Sonderpreis](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/products/pricing/product-price-special) (Mindestendpreis) an, sofern verfügbar.

### [!DNL Live Search] 1.3.0

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![ Reporting](../assets/new.svg)Dashboard [Neu](performance.md)Performance) bietet Einblicke in Suchbegriffe, die Kundinnen und Kunden verwenden.
![Neu](../assets/new.svg) [!DNL Live Search] [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) bietet Zugriff auf eine gemeinsame Datenschicht mit Services zur Ereignisveröffentlichung und -abonnement sowie Metriken.
![Beheben](../assets/fix.svg) Der [[!DNL Storefront popover]](storefront-popover.md) verfügt über eine neue `active` für den `.search-autocomplete`-Container, der die Sichtbarkeit steuert.
![Fix](../assets/fix.svg) In der Storefront wird der [Suchbegriffe](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/catalog/search/search-terms) Fußzeilen-Link entfernt und sein Cache für [!DNL Live Search] Installationen deaktiviert.
![Bug](../assets/bug.svg) Patch for Search Adapter verarbeitet doppelte Produkte.
![Bug](../assets/bug.svg) [!DNL Live Search] unterstützt [Single-Source](https://experienceleague.adobe.com/de/docs/commerce-admin/inventory/sources/sources-manage) (physische) Lagerplätze mit mehreren (virtuellen) [Stocks](https://experienceleague.adobe.com/de/docs/commerce-admin/inventory/stocks/stocks-manage). Mehrere Inventarquellen werden jetzt nicht unterstützt.

### [!DNL Live Search] 1.2.0

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) zeigt [[!DNL Storefront popover]](storefront-popover.md) vorgeschlagene Produkte und Miniaturbilder der besten Suchergebnisse an, wenn Käufer Abfragen in das Suchfeld eingeben.
![Neu](../assets/new.svg) Commerce *Admin*-Sitzung bleibt während längerer Zeiträume ohne Tastaturaktivität geöffnet
![Neu](../assets/new.svg) [!DNL Live Search] wird nach der Einführung automatisch aktiviert
![Fehlerbehebung](../assets/fix.svg) Die anfängliche Indizierungszeit beträgt weniger als eine Stunde
![Beheben](../assets/fix.svg) Inkrementelle Produktaktualisierungen nahezu in Echtzeit (nach Installation und Einrichtung)
![Korrigieren](../assets/fix.svg) Sortierbare Spalten im Synonym-Editor
![Beheben](../assets/fix.svg) [!DNL Live Search] gibt keinen Fehler mehr aus, wenn Suchkriterien einen leeren Sortierreihenfolgenwert enthalten
![Korrigieren](../assets/fix.svg) Die Bereichsfilterung funktioniert nicht mehr, wenn Attributcodes die Zeichenfolgen „to“ oder „from“ enthalten.

### [!DNL Live Search] 1.1.0

[!BADGE Unterstützt]{type="Informative" tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Bug](../assets/bug.svg) Der [!DNL Live Search]-Service unterstützt nur die [Basiswährung](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) der Adobe Commerce-Installation.
![Bug](../assets/bug.svg) Beim Hinzufügen einer Facette wird der Feed „Produktattribute“ nicht korrekt aktualisiert, wenn auf &quot;`Update on Save`&quot; gesetzt ist. Um dieses Problem zu vermeiden, navigieren Sie zu [Indexverwaltung](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/index-management) und setzen Sie den Feed „Produktattribute“ auf `Update by Schedule`.
![Bug](../assets/bug.svg) [!DNL Live Search] Synonyme werden pro Store-Ansicht definiert, werden aber derzeit pro Website gespeichert und mit einer Kombination aus `environmentId` und `storeViewCode` identifiziert. Daher verwenden alle Websites und Speicheransichten innerhalb der Adobe Commerce-Installation dieselben Synonyme. Der zuletzt erstellte Satz von Synonymen für die Store-Ansicht hat Vorrang.
![Bug](../assets/bug.svg) Wenn ein Synonym-Begriff mehrere Wörter enthält, wird jedes Wort als separates Synonym behandelt. Wenn Sie beispielsweise „Uhr“ als Synonym für „Uhr“ definieren, werden sowohl „Zeit“ als auch „Stück“ als Synonyme von Uhr behandelt.

+++

## Dokumentation

Weitere Informationen:

- [Entwicklerdokumentation für Adobe Commerce](https://developer.adobe.com/commerce/docs)
- [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/de/docs/commerce)
- [[!DNL Live Search] auf Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
