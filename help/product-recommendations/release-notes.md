---
title: '[!DNL Product Recommendations] Versionshinweise'
description: Die neuesten Versionsinformationen für  [!DNL Product Recommendations]  von Adobe Commerce.
feature: Services, Recommendations, Release Notes
exl-id: 37404605-5b62-4c71-90d1-4f09e6105c4b
source-git-commit: 0d69d893d616a5e75ee264ebc652f3793a359486
workflow-type: tm+mt
source-wordcount: '1703'
ht-degree: 0%

---

# [!DNL Product Recommendations] Versionshinweise

Die Versionshinweise enthalten Aktualisierungen zu den folgenden [!DNL Product Recommendations]:

* [!DNL Product Recommendations]-Metapaket: `magento/product-recommendations`
* Page Builder-Unterstützung im [!DNL Product Recommendations]-Modul (optional): `magento/module-page-builder-product-recommendations`
* Unterstützung des Empfehlungstyps für visuelle Ähnlichkeit für [!DNL Product Recommendations] (optionales) Modul: `magento/module-visual-product-recommendations`

Unterstützung wird für die aktuelle Hauptversion bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Die Versionshinweise umfassen Folgendes:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bug](../assets/bug.svg) Bekannte Probleme

Informationen zum Produkt-[ finden Sie in der Entwicklerdokumentation ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Gehostete Service-Aktualisierungen

In diesen Hinweisen werden Aktualisierungen oder bekannte Probleme beschrieben, die außerhalb einer versionierten Version oder Verbesserungen am gehosteten Service veröffentlicht oder erkannt wurden.

_31. Januar 2025_

![Neu](../assets/new.svg) Es gibt eine neue Richtlinie zur Datenaufbewahrung für nicht abgefragte Katalogdaten in Ihrer Testumgebung. [Weitere Informationen](overview.md#catalog-data-retention-policy).

_28. Juni 2024_

![Bug](../assets/bug.svg) Produkte, die aus einer [!DNL Product Recommendations] auf der Warenkorbseite zum Warenkorb hinzugefügt wurden, werden beim Neuladen der Warenkorbseite nicht aus der Liste der empfohlenen Produkte entfernt.
![Fehler](../assets/bug.svg) Produkte, die aus dem Warenkorb entfernt wurden, bleiben so lange im `cartSkus`-Array erhalten, bis die Warenkorbseite neu geladen wird.

_18. Juli 2023_

![Neu](../assets/new.svg) [!DNL Product Recommendations] verfügt jetzt über eine GraphQL [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/)-Abfrage.

_25. April 2023_

![Neu](../assets/new.svg) [!DNL Product Recommendations] Kunden können jetzt die Vorteile der [SaaS-Preisindizierung](../price-index/price-indexing.md) nutzen.

## Aktuelle Hauptversion

### 6.2.1 von Magento/Product-Recommendations

_14. Juli 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Korrektur](../assets/fix.svg) Es wurden Verbesserungen am Bedienfeld [Recommendations-Vorschau](./create.md#preview-recommendations) vorgenommen.

### Frühere Versionen

### 6.2.0 von Magento/Product-Recommendations

_4. April 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die CDN-URLs für den `recommendations-admin-ui` zur `adobe.io`-Domain wurden aktualisiert.

### 6.1.0 von Magento/Product-Recommendations

_11. März 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) PHP 8.4-Unterstützung wurde hinzugefügt.

### 6.0.3 von Magento/Product-Recommendations

_6. November 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Korrigieren](../assets/fix.svg) Es wurde ein Problem behoben, bei dem [Kategoriefilter](filters.md#category) Kategorien enthielt, die nicht zur aktuellen Storeview gehörten.
![Beheben](../assets/fix.svg) Es wurde ein Abhängigkeitsproblem im `magento/product-recommendations`-Metapaket behoben.

### 6.0.2 von Magento/Product-Recommendations

_9. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem durch Klicken auf die Schaltfläche **[!DNL Add to Cart]** auf einem einfachen Produkt in einer Produktempfehlungseinheit der Einkäufer zur Startseite weitergeleitet wurde, anstatt auf der aktuellen Seite zu bleiben.
![Fehler](../assets/bug.svg) Es gibt einen Validierungsfehler, der durch das `referenceBlock` in der `ProductRecommendations Layout` XML-Datei verursacht wird.

### 6.0.1 von Magento/Product-Recommendations

_19. März 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) PHP 8.3-Unterstützung wurde hinzugefügt.

### 6.0.0 von Magento/Product-Recommendations

_22. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Die [!DNL Catalog Sync Dashboard] ist jetzt die [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Dieses überarbeitete Dashboard bietet Einblicke in Datenströme für [!DNL Product Recommendations], [!DNL Live Search] und [!DNL Catalog Service].
![Beheben](../assets/fix.svg) Es wurde ein Problem behoben, das zu Checkout-Fehlern für [!DNL Product Recommendations] führte.

+++5.0.0 und älter

### 5.0.1 von Magento/Product-Recommendations

_15. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Neue Module zur Unterstützung des [Saas Price Indexer](../price-index/price-indexing.md) hinzugefügt.
![Neu](../assets/new.svg) Es wurden neue Datenexportmodule hinzugefügt, die den Export weiterer Produktarten, einschließlich gebündelter Produkte und Geschenkgutscheine, unterstützen.
![Fix](../assets/fix.svg) Die Tabellengröße der Produkte und der Preis-Feeds wurde stark reduziert. Bei den Tabellen `catalog_data_exporter_products` und `catalog_data_exporter_product_prices` sollte eine erhebliche Größenreduzierung zu verzeichnen sein.

#### Bekannte Einschränkungen

* Der `websiteCode` wird fälschlicherweise zurückgegeben, wenn er einen Unterstrich (_) enthält.

### 5.0.0 von Magento/Product-Recommendations

_20. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Aktualisierte [!DNL Product Recommendations] zur Unterstützung von Adobe Commerce 2.4.6.
![Neu](../assets/new.svg) Dies ist eine Hauptversion. [Bearbeiten](install-configure.md#update) Sie die `composer.json` für Ihr Projekt.
![Neu](../assets/new.svg) [!DNL Product Recommendations] unterstützt jetzt vollständige [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction)-Funktionen in Commerce (ehemals Multi-Source Inventory oder MSI). Um die vollständige Unterstützung zu aktivieren[ müssen Sie ](install-configure.md#update) Abhängigkeitsmodul-`commerce-data-export` auf Version 102.2.0 oder höher aktualisieren.

### 4.0.1 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Korrigieren](../assets/fix.svg) Zuvor zeigte [!DNL Product Recommendations] einen Fehler an, wenn die Anzeigewährung auf eine nicht standardmäßige Währung umgeschaltet wurde. Der Wechsel zwischen Währungen funktioniert jetzt ordnungsgemäß.

### 4.0.0 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.4 und neuer

![Neu](../assets/new.svg) Es wurden [Bereitschaftsindikatoren](create.md) hinzugefügt, mit denen Sie den Schulungsfortschritt der einzelnen Empfehlungstypen visualisieren können.
![Neu](../assets/new.svg) Dies ist eine Hauptversion. [Bearbeiten](install-configure.md#update) Sie die `composer.json` für Ihr Projekt. In dieser Version müssen Sie auch zwei API-Schlüssel bei der Installation und Konfiguration von [!DNL Product Recommendations] angeben[ einen Produktionsschlüssel und einen Sandbox-Schlüssel](../landing/saas.md).

#### Bekannte Einschränkungen

* Der `websiteCode` wird fälschlicherweise zurückgegeben, wenn er einen Unterstrich (_) enthält.

### 3.3.7 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) PHP 8.1-Unterstützung wurde hinzugefügt
![Neu](../assets/new.svg) Die Bildgröße wurde verbessert, sodass die Bildgröße in der Referenzanzeigevorlage konsistenter gehandhabt wird

### 3.3.6 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Optimiertes [!DNL Product Recommendations]-Metapaket durch explizites Auflisten der Abhängigkeiten

### 3.3.5 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) [B2B-Unterstützung](onboarding.md#b2bsupport) in [!DNL Product Recommendations] hinzugefügt
![Neu](../assets/new.svg) Es wurden neue Feeds zum [Synchronisieren von Katalogdaten](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) zu Commerce Services über die Befehlszeile hinzugefügt

### 3.3.3 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Hinzugefügte [Empfehlungstypen](type.md): Konversion (Ansicht zum Warenkorb), Konversion (Ansicht zum Kauf) und Kürzlich angezeigt. Diese neuen Empfehlungstypen sind ab Version 3.2.2 des `magento/product-recommendations`-Moduls verfügbar.
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Fastly&#39;s Web Application Firewall (WAF) fälschlicherweise ein Cookie blockierte
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Produkte, die der nicht standardmäßigen Store-Ansicht zugewiesen waren, beim Erstellen einer Empfehlung für diese _Store-Ansicht_ Bedienfeld „Recommendations-Produktvorschau“ angezeigt wurden
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem bestimmte Namen von Empfehlungseinheiten in Page Builder die Anzeige der Empfehlungseinheit in der Storefront verhinderten

### 3.3.2 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Beheben](../assets/fix.svg) Fehlende Abhängigkeit für die B2B-Unterstützung behoben

### 3.3.1 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Es wurde Unterstützung für Preise für B2B-Kundengruppen hinzugefügt. Wenn Sie einen [Preisfilter](filters.md) für eine Empfehlungseinheit festlegen, sehen B2B-Kunden, die angemeldet sind, den Preissatz der Kundengruppe für die angezeigten Produkte.

### 3.3.0 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Es wurde Unterstützung für die Adobe Client-Datenschicht hinzugefügt, um die Erfassung von Verhaltensdaten über Adobe Commerce-Funktionen und -Services hinweg zu standardisieren. Weitere Informationen finden [ in der ](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md).

### 3.2.6 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Beheben](../assets/fix.svg) Es wurde ein JavaScript-Modalfehler behoben
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Fastly&#39;s Web Application Firewall (WAF) fälschlicherweise ein Cookie blockierte

### 3.2.5 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Umbenannte Magento Services in [Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/integration-services/saas) und verbesserte Benutzerfreundlichkeit in Admin

### 3.2.4 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Beheben](../assets/fix.svg) Der Fehler „Konfigurierbare Produktoptionendaten können nicht abgerufen werden“ bei der Indizierung von Produktattributen wurde behoben

### 3.2.3 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Beheben](../assets/fix.svg) Der Fehler „Daten zu konfigurierbaren Produktoptionen können nicht abgerufen werden“ während der Katalogsynchronisierung wurde behoben
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem der Store-Code nicht korrekt festgelegt wurde, als Sie die Konfiguration „Store-Code zur URL hinzufügen“ aktiviert hatten
![Korrektur](../assets/fix.svg) Die Erkennung von Änderungen an der Admin Panel-Konfiguration wurde verbessert, um sicherzustellen, dass diese Änderungen in die Katalogsynchronisierungsdaten übernommen werden

### 3.2.2 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, [Empfehlungsergebnisse in der Vorschau anzuzeigen](create.md) zur Erstellungszeit. Dies kann erfordern, dass Sie Ihr Modul auf die neueste Version aktualisieren.
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt[ den Katalogsynchronisierungsprozess ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) Admin zu überwachen und zu verwalten.
![Neu](../assets/new.svg) Es wurden [Filter](filters.md) hinzugefügt, um zu steuern, welche Produkte in Recommendations angezeigt werden.
![Neu](../assets/new.svg) Der Empfehlungstyp [Visuelle ](type.md#visualsim)&quot; wurde hinzugefügt.

### 1.2.1 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Es wurde Unterstützung für die Version 3.2.0 und höher des `magento/product-recommendations` hinzugefügt

### 3.1.0 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt[ Ihren Katalog über ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) Befehlszeile erneut mit SaaS-Services zu synchronisieren.
![Neu](../assets/new.svg) Unterstützung für Datenbanktabellen-Präfixe wurde hinzugefügt
![Fix](../assets/fix.svg) PHP 7.1-Unterstützung entfernt

### 3.0.8 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Ereignisse zur Datenerfassung gesendet wurden, bevor das Modul konfiguriert wurde, was zu ungültigem Traffic führte

### 3.0.6 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) **(Beta)** Umfasst Unterstützung für den neuen Empfehlungstyp [Visuelle Ähnlichkeit](type.md#visualsim).

### 1.0.0 von magento/module-visual-product-recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) **(Beta)** [Visuelle Ähnlichkeit](type.md#visualsim). Mit dem Empfehlungstyp _Visuelle Ähnlichkeit_ können Sie eine Empfehlungseinheit auf Ihrer Produktdetailseite bereitstellen, die Produkte anzeigt, die dem angezeigten Produkt visuell ähnlich sind.

### 3.0.5 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Beheben](../assets/fix.svg) Der Fehler „Daten zu Produktoptionen können nicht abgerufen werden“, der beim Katalogexport auftreten konnte, wurde behoben.
![Korrigieren](../assets/fix.svg) Das Währungssymbol in der Spalte _Umsatz_ im _[!DNL Product Recommendations]_-Dashboard spiegelt nun die konfigurierte Basiswährung korrekt wider.

### 3.0.4 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Fehlerbehebung](../assets/fix.svg) Es wurde Unterstützung für Adobe Commerce 2.4.0 hinzugefügt

### 3.0.3 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Korrigieren](../assets/fix.svg) Verbesserte Symbolimplementierung in der Storefront-Vorlage

### 1.0.4 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Beim Bearbeiten des Inhaltstyps von Page Builder wurde ein Produktempfehlungsname hinzugefügt

### 3.0.2 Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Bei der Auswahl von Empfehlungseinheiten in Page Builder wurde eine Statusspalte im Raster hinzugefügt.
![Beheben](../assets/fix.svg) Es wurde ein Problem mit falschen HTTP/HTTPS-Protokollen in Produkt- und Bild-URLs behoben

### 3.0.1 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

Dies ist eine Hauptversion. [Bearbeiten](install-configure.md#update) Sie die Datei „composer.json“ im Stammverzeichnis Ihres Projekts.

![Neu](../assets/new.svg) Abrufen von [!DNL Product Recommendations] aus alternativen SaaS-Datenräumen. Auf diese Weise können Sie in Ihrer Produktumgebung berechnete [!DNL Product Recommendations] in anderen, produktionsfremden Umgebungen verwenden. [Switching SaaS Data Spaces](settings.md) beschreibt diese Funktion näher.

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, durch das der Checkout für Käufer, die uBlock Origin verwenden, gesperrt war
![Beheben](../assets/fix.svg) Es wurde ein Problem beim Senden von externen „Zum Warenkorb hinzufügen“-Ereignissen behoben

### 1.0.3 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Page Builder-Unterstützung. Mit der Page Builder-Integration können Sie Empfehlungseinheiten präzise und detailliert an einer beliebigen Stelle in von Page Builder erstellten Inhalten platzieren. Sie können die Überschriften und Empfehlungseinheiten auch selbst gestalten. Weitere Informationen finden [ unter ](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations)Page Builder“.

### 2.0.0 von Magento/Product-Recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.x und neuer

![Neu](../assets/new.svg) Allgemeine Verfügbarkeitsversion!

+++

## Dokumentation

Weitere Informationen zur [!DNL Product Recommendations]- und [!DNL Product Recommendations]:

* [Benutzerhandbuch](overview.md)
* [Entwicklerdokumentation](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/developer/development-overview)
