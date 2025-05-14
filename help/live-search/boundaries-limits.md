---
title: Grenzen und Beschränkungen
description: Erfahren Sie mehr über die Grenzen und Einschränkungen von  [!DNL Live Search] , um sicherzustellen, dass es den Anforderungen Ihres Unternehmens entspricht.
role: Admin, Developer
exl-id: 28b8d98f-0784-4c4d-b382-81c01838e0de
source-git-commit: 29374c45f57e923666e255bfefadd9a1e736cfef
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 0%

---

# Grenzen und Beschränkungen

Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Überprüfen Sie die folgenden Grenzen und Beschränkungen, um sicherzustellen, dass [!DNL Live Search] und [!DNL Catalog Service] den Anforderungen Ihres Unternehmens entsprechen. Wenn Sie erweiterte Suchfunktionen wie Inhaltssuche, BYOA (bring-your-own-algorithm) oder attributbasiertes Merchandising benötigen, sollten Sie eine Suchlösung eines Drittanbieters in Betracht ziehen.

## Allgemein

- Das [Erweiterte Suche](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/catalog/search/search)-Modul ist deaktiviert, wenn [!DNL Live Search] installiert ist, und der Link für die erweiterte Suche in der Storefront-Fußzeile wird entfernt.
- [Preisstufe](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/products/pricing/product-price-tier) wird im [!DNL Live Search] Feld und im Widget „Produktlistenseite“ nicht unterstützt.
- Die Produktpreise enthalten die Mehrwertsteuer (MwSt.), aber [!DNL Live Search] können die MwSt. nicht als separaten Wert anzeigen.
- Die Inhaltssuche (CMS-Seiten und -Blöcke) wird nicht unterstützt.
- Die maximale Anzahl von Ergebnissen, die paginiert werden können, beträgt 10.000. Um sicherzustellen, dass Käufer keine tiefe Paginierung verwenden müssen, wenn eine Kategorie oder ein Suchergebnis eine große Anzahl von Produkten enthält, bieten Sie aussagekräftige Möglichkeiten, Produkte zu filtern.
- Es gibt eine feste Grenze von 1 MB pro Attribut, einschließlich Beschreibung und benutzerdefinierten Attributen.
- Der Suchadapter unterstützt keine Produktattribute, die mit einem benutzerdefinierten Quellmodell erstellt und als Facetten verwendet werden. Um diese Funktion zu unterstützen, müssen Sie das Widget [Produktlistenseite“ ](plp-styling.md).
- Benutzerdefinierte Produkttypen werden nicht unterstützt.
- Benutzerdefinierte Attribute, die programmgesteuert mit `"is_user_defined": false` erstellt wurden, werden nicht unterstützt.
- Sie können Ergebnisse mithilfe der Bedingungen „Beginnt mit“ oder „Enthält“ mit einigen Einschränkungen filtern, wie [hier](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#limitations) beschrieben.
- Sie können Leistungsmetriken nur innerhalb des letzten Jahres verfolgen.
- Wenn eine Suchabfrage mehrere Wörter enthält, werden diese aufgrund des Leerzeichens zwischen den Wörtern als separate Suchbegriffe behandelt. Verwenden Sie [Synonyme](./synonyms.md) wenn Sie mehrwortige Suchabfragen berücksichtigen möchten.

## Indizierung

- [!DNL Live Search] [indizes](indexing.md) bis zu insgesamt 450 Produktattribute pro Shop-Ansicht. Diese sind wie folgt verteilt:
   - 50 sortierbare Attribute
   - 200 filterbare Attribute
   - 200 durchsuchbare Attribute
- [!DNL Live Search] indiziert nur Produkte aus der Adobe Commerce-Datenbank.
- CMS-Seiten sind nicht indiziert.
- Attribute für SKU, Name und Kategorie sind standardmäßig durchsuchbar und können nicht von der Suche ausgeschlossen werden. Heben Sie die Zuweisung der Produkte zu den Kategorien auf, wenn sie nicht zu diesen Kategorien gehören sollen.

## Facetten

- Es können maximal 100 Attribute aus den 200 filterbaren Attributen, die indiziert werden können, als Facetten konfiguriert werden.
- Innerhalb einer Facette können maximal 100 Buckets zurückgegeben werden. Wenn Sie mehr als 100 Behälter zurückgeben müssen, erstellen [ein Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide), damit Adobe die Leistungsauswirkungen analysieren und ermitteln kann, ob es möglich ist, diesen Grenzwert für Ihre Umgebung zu erhöhen.
- Dynamische Facetten können Leistungsprobleme bei großen Indizes und Indizes mit hoher Ordinalität verursachen. Wenn Sie dynamische Facetten erstellt haben und eine Leistungsbeeinträchtigung oder das Laden einer Seite mit Zeitüberschreitungsfehlern bemerken, versuchen Sie, Ihre Facetten zu ändern und anzuheften, um festzustellen, ob dies Ihr Leistungsproblem behebt.
- Lagerstatus (`quantity_and_stock_status`) wird nicht als Facette unterstützt. Sie können `inStock: 'true'` verwenden, um nicht vorrätige Produkte zu filtern. Dies wird im `LiveSearchAdapter`-Modul standardmäßig unterstützt, wenn „Nicht vorrätige Produkte anzeigen“ im [!DNL Commerce] Admin auf „True“ eingestellt ist.
- Datentypattribute werden nicht als Facette unterstützt.
- Änderungen, die an den Attributmetadaten vorgenommen werden, nachdem dieses Attribut als Facette hinzugefügt wurde, werden in der Facette nicht widergespiegelt.

## Abfrage

- [!DNL Live Search] verwendet einen eindeutigen [GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/)Endpunkt für Abfragen zur Unterstützung von Funktionen wie dynamisches Facettieren und Suche nach eigener Eingabe. Obwohl es der [GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/) ähnelt, gibt es einige Unterschiede, und einige Felder sind möglicherweise nicht vollständig kompatibel.
- Die maximale Anzahl von Ergebnissen, die in einer Suchanfrage zurückgegeben werden können, beträgt 10.000.
- Die maximale Anzahl von Ergebnissen pro Seite beträgt 500.
- Es ist nicht möglich, Ergebnisse mithilfe eines Attributs vom Typ Datum zu filtern.

## Merchandising suchen

- Die maximale Anzahl von Merchandising-[ (Regeln](rules.md) pro Store-Ansicht ist 50.
- Die maximale Anzahl von Bedingungen pro Regel ist 10.
- Die maximale Anzahl von Ereignissen pro Regel ist 25.
- Regeln und manuell sortierte Produkte werden auf die Suchergebnisse angewendet, wenn die standardmäßige Sortierreihenfolge „Sortieren nach: Am relevantesten“ ausgewählt ist. Wenn ein Käufer die Sortierreihenfolge ändert, sodass sie etwa nach Name oder Preis sortiert wird, sind Regeln und manuelle Rankings nicht mehr wirksam.
- Um unvorhersehbare Ergebnisse in paginierten Antworten zu vermeiden, sollte die Anzahl der angehefteten Produkte die angeforderte Seitengröße nicht überschreiten.

## Synonyme

- [!DNL Live Search] können bis zu 200 [Synonyme](synonyms.md) pro Shop-Ansicht verwalten.

## Kategorie-Merchandising

- Sie können für jede Shop-Ansicht eine Regel pro Kategorie erstellen.
- Die maximale Anzahl von Bedingungen pro Regel ist 10.
- Die maximale Anzahl von Ereignissen pro Regel ist 25.
- Regeln werden angewendet, wenn eine bestimmte Kategorie in der Storefront geöffnet wird und eine Regel für diese Kategorie vorhanden ist. Für Kategorie-Merchandising-Regeln lautet die standardmäßige Sortierreihenfolge „Sortieren nach: Position“. Wenn ein Käufer die Sortierreihenfolge ändert, werden alle ausgeblendeten, angehefteten und vergrabenen Produkte nicht mehr sortiert.

## B2B- und Kategorieberechtigungen

- Produkte werden nicht angezeigt, wenn sie nicht zu einem freigegebenen Standardkatalog hinzugefügt werden.
- So beschränken Sie Kundengruppen mithilfe von [Kategorieberechtigungen](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/categories/category-permissions):
   - Produkte müssen der Stammkategorie zugewiesen werden. (**Hinweis:** Sie können diese Einschränkung entfernen, indem Sie die SaaS-Datenexporterweiterung auf Version 103.4.0 oder höher aktualisieren. Siehe [Verwalten der Datenexporterweiterung](../data-export/manage-extension.md).
   - Die Kundengruppe „Nicht angemeldet“ muss über „Erlauben“-Browserberechtigungen verfügen.
   - Um Produkte auf die Kundengruppe „Nicht angemeldet“ zu beschränken, gehen Sie zu jeder Kategorie und legen Sie die Berechtigungen für jede [Kundengruppe“ ](https://experienceleague.adobe.com/de/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- Vorkonfigurierte Unterstützung für B2B mit dem PLP-Widget auf PWA Studio wird derzeit nicht unterstützt. Sie können jedoch [die API verwenden](install.md#pwa-support) um diese Funktion zu implementieren.
- Kategoriefacetten in [!DNL Live Search] zeigen möglicherweise Kategorien an, die für eine bestimmte [ (Kundengruppe) nicht ](https://experienceleague.adobe.com/de/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) werden können.
- [!DNL Live Search] können bis zu 1.000 Kundengruppen unterstützen.

## [!DNL Storefront popover]

- Die [[!DNL popover]](storefront-popover.md) ist nur für Stores verfügbar, die das Design *Luma* verwenden, oder für ein benutzerdefiniertes Design, das auf &quot;*&quot;*. Breadcrumbs auf der Suchergebnisseite haben keinen *Luma*-Stil.
- Das [!DNL popover] unterstützt das Design &quot;*&quot;*.
- Die [!DNL popover] wird im Schnellbestellungsformular nicht unterstützt.
- Wunschlisten und Produktvergleiche werden nicht unterstützt.
- Das Währungssymbol für den Peruanischen Sol (PEN) wird nicht unterstützt.

## Fehlerbehebung

Hilfe bei der Fehlerbehebung bei einigen häufigen Problemen in [!DNL Live Search] finden Sie in den folgenden Knowledgebase-Artikeln:

- [[!DNL Live Search] Katalog nicht synchronisiert](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync)
- [[!DNL Live Search] Das Dashboard und die Suchergebnis-Rangfolge sind falsch](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-dashboard-ranking-incorrect)
- [[!DNL Live Search] zeigt nicht vorrätige Produkte unabhängig von den Lagerstatuseinstellungen in Admin an](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-displays-out-of-stock-products)
- [[!DNL Live Search] Facetten sind nicht alphabetisch sortiert](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-facets-not-sorted)

Wenn Sie zusätzliche Hilfe benötigen, wenden Sie sich an [Support](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).
