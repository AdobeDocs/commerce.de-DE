---
title: '[!DNL Catalog Service] Versionshinweise'
description: Die neuesten Versionsinformationen für  [!DNL Catalog Service]  für Adobe Commerce.
feature: Services, Catalog Service, Release Notes
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---

# [!DNL Catalog Service] Versionshinweise

In diesen Versionshinweisen werden die neuesten Versionen von [!DNL Catalog Service] beschrieben.
Unterstützung wird für die aktuelle Hauptversion bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bug](../assets/bug.svg) Bekannte Probleme

## Aktuelle Hauptversion

### Version 1.26

_22. Oktober 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Das GraphQL-Schema enthält jetzt das Attribut `lastModifiedAt` in den Produktinformationen. Mit diesem präzisen Zeitstempel können Kunden sicherstellen, dass Sitemaps die neuesten Aktualisierungen ihrer Produkte korrekt widerspiegeln. Suchmaschinen wie Google können so auch feststellen, wann eine Neuindizierung erforderlich ist, den Crawling-Prozess optimieren und Probleme im Zusammenhang mit aggressiven Daten der letzten Änderung vermeiden, die verwendet werden, wenn keine präzisen Informationen verfügbar sind. <!--DATA-6209-->

## Frühere Versionen

+++ Frühere Versionen

### Version 1.23

_22. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Fehlerbehebung](../assets/fix.svg) Sie können jetzt Produktinformationen abrufen, ohne dass Produktüberschreibungsdaten (Preise) erforderlich sind. In früheren Versionen gaben diese Abfragen den folgenden Fehler zurück:
`The following sku does not have product override data in the DB: <SKU value>. Make sure data is synced.` <!--DATA-6121-->

### Version 1.22

_13. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung zum Abrufen aller Varianten nach Produkt-SKU hinzugefügt. Siehe die [Catalog Service API-Referenz](https://developer.adobe.com/commerce/services/graphql/catalog-service/). <!--DATA-6067-->

### Version 1.22

_13. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung zum Abrufen aller Varianten nach Produkt-SKU hinzugefügt. Siehe die [Catalog Service API-Referenz](https://developer.adobe.com/commerce/services/graphql/catalog-service/). <!--DATA-6067-->

### Version 1.19

_23. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}


![Beheben](../assets/fix.svg) <!--DATA-5033-->Das `InStock` für Optionswerte berücksichtigt jetzt den `enabled` der Produktvariante.

![Fix](../assets/fix.svg) <!--DATA-5888-->Unterstützung für Produktpreise hinzufügen, die eine große Anzahl (bis zu 16 Stellen) und eine höhere Dezimalgenauigkeit (bis zu 4 Dezimalstellen) erfordern. Um die Preiskonfigurationsaktualisierungen auf Ihren bestehenden Katalog anzuwenden, synchronisieren Sie Katalogdaten über das [Daten-Management-Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) oder mithilfe der [Adobe Commerce-Befehlszeilenschnittstelle](../landing/catalog-sync.md#command-line-interface) neu.

#### Bekannte Einschränkungen

Die folgenden Funktionen werden noch nicht unterstützt:

* Die maximale Größe für die Payload dynamischer Attribute beträgt 9 MB.
* Der Gruppenproduktpreis kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.

Lösen Sie die folgenden Einschränkungen mithilfe von API Mesh und der Core GraphQL-API:

* Mindestpreis
* Preisstufe
* Bundle-Produkte mit Festpreisen

Weitere Informationen und Beispiele finden Sie unter [Katalog-Service und API-Mesh](mesh.md)

### Version 1.18

_11. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Es wurde Unterstützung für PHP 8.3 hinzugefügt.

![Neu](../assets/new.svg) Die [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/)- und [`refineProduct`](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/)-Abfragen geben jetzt anpassbare Optionsdaten für einfache und komplexe Produkte zurück.<!--DATA-5538-->

### Version 1.17

_22. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) ist jetzt verfügbar. Dieses überarbeitete Dashboard bietet Einblicke in Datenströme für [!DNL Product Recommendations], [!DNL Live Search] und [!DNL Catalog Service]. Die Unterstützung für diese Funktion wurde in Version 3.1.0 des `catalog-service`-Metapakets eingeführt.

### Version 1.16

_13. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Produktvideos werden jetzt von der Catalog Service-API unterstützt.
![Beheben](../assets/fix.svg) Nicht vorrätige Optionen werden jetzt im PDP-Widget angezeigt.

#### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Die maximale Größe für die Payload dynamischer Attribute beträgt 9 MB.
* Gruppenproduktpreis. Dieser Wert kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.

Die folgenden Einschränkungen können mithilfe von API Mesh und der Core GraphQL-API behoben werden:

* Mindestpreis
* [Preisstufe](mesh.md)

### Version 1.13

_12. Oktober 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalog-Service unterstützt das `inStock`-Flag für Produktvarianten.
![Neu](../assets/new.svg) Die Felder `urlKey` und `externalId` wurden zum GraphQL-Schema hinzugefügt.
![Neu](../assets/new.svg) Herunterladbare Produkte und Geschenkkarten werden jetzt unterstützt.

### Version 1.12

_19. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalog-Service verwendet jetzt [SaaS-Preisindizierung](../price-index/price-indexing.md).
![Behebung](../assets/fix.svg) Diese Version enthält Fehlerbehebungen und Verbesserungen auf der Service-Seite.

### Version 1.11

_18. Juli 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalog-Service unterstützt jetzt die [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) GraphQL-Abfrage für Produktempfehlungen.

### Version 1.10

_27. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Catalog Service-API unterstützt jetzt `related products`.

### Version 1.7

_12. April 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalog-Service bereinigt jetzt gelöschte Produktvarianten.
![Behebung](../assets/fix.svg) Infrastrukturskalierbarkeit und Leistungsverbesserungen.

### Version 1.6

_28. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Zur [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) Abfrage wurden Farbfelder hinzugefügt.
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, `entityId` mithilfe von [API Mesh) ](mesh.md).

### Version 1.5

_6. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Funktion [`categories`](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) GraphQL hinzugefügt.
![Behebung](../assets/fix.svg) Verbesserte Leistung und API-Skalierbarkeit.

### Version 1.4

_7. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Veröffentlichtes Katalog-Service-Metapaket zur Vereinfachung der Installationsschritte.
![Fix](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version 1.3

_17. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Das Onboarding wurde vereinfacht und verbessert.
![Neu](../assets/new.svg) Neue Kunden-Sandbox-Endpunkte sind für Vorproduktionstests verfügbar.
![Neu](../assets/new.svg) Unterstützung für virtuelle Produkte hinzugefügt.
![Fix](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version v1.1

_18. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalog-Service unterstützt jetzt das Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fix](../assets/fix.svg) Verbesserte API-Skalierbarkeit und Gesamtleistung.

### Version 1.0

_4. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützt jetzt gebündelte und gruppierte Produkte.
![Neu](../assets/new.svg) Es wurden Überschreibungen der B2B-Sichtbarkeit hinzugefügt. Produkte können jetzt durchsucht und für bestimmte Kundengruppen zum Warenkorb hinzugefügt werden.
![Fix](../assets/fix.svg) Service ist jetzt stabiler und hat die Leistung verbessert.

### Version 0.3 - Beta+

_12. September 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung von Bildern für Varianten: Produktbilder werden basierend auf den ausgewählten Optionen zurückgegeben
![Neu](../assets/new.svg) Rollen zur Preisunterstützung: Nur Mitgliedern bestimmter Kundengruppen wird ermöglicht, die Preise von Produkten anzuzeigen.
![Behebung](../assets/fix.svg) Verbesserte Stabilität und Leistung des Service
![Neu](../assets/new.svg) Aktualisierungen werden empfangen, wenn Produkte aus dem Katalog gelöscht werden

### Beta-Version

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die `products`- und `refineProduct`-Abfragen geben die folgenden Daten zurück:

* Vordefinierte (System-)Produktattribute.
* Dynamische Produktattribute und deren Filterung nach Rolle (Produktanzeigeseite/Produktlistenseite).
* Produktoptionen.
* Produktbilder und Filtern nach Rolle (PDP/PLP).
* Ein spezifischer Preis für einfache Produkte und Preisspannen für konfigurierbare Produkte.
* Kundengruppenpreise und Preisspannen. Sie geben einen standardmäßigen Fallback-Preis für Käufer ohne Kundengruppe zurück.
* Produkttypen, die B2B-kundenspezifische Preise verwenden.
