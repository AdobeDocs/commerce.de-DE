---
title: Grenzen und Beschränkungen
description: Erfahren Sie mehr über die Grenzen und Einschränkungen von  [!DNL Product Recommendations] , um sicherzustellen, dass es den Anforderungen Ihres Unternehmens entspricht.
role: Admin, Developer
source-git-commit: 66830c9d950a27269aca1bda0dcc7d0d86f05647
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 0%

---

# Grenzen und Beschränkungen

Überprüfen Sie die folgenden Grenzen und Beschränkungen, um sicherzustellen, dass [!DNL Product Recommendations] die Anforderungen Ihres Unternehmens erfüllt. Wenn Sie diese Einschränkungen verstehen, können Sie die Implementierung planen, Filter konfigurieren und gängige Probleme vermeiden.

## Allgemein

- **Produkttypen** - Unterstützte Produkttypen sind _einfach_, _konfigurierbar_, _virtuell_, _herunterladbar_ und _Geschenkkarte_. _Bundle_, _grouped_ und benutzerdefinierte Produkttypen werden nicht unterstützt. Wenn Ihr Katalog eine große Anzahl nicht unterstützter Produkttypen enthält, können Sie mit einem niedrigen [Bereitschaftswert) &#x200B;](create.md#readiness-indicators). Siehe [Filtern nach Produkttyp](filters.md#type).
- **SKUs mit Leerzeichen** - SKUs, die Leerzeichen enthalten, können die Relevanz von Empfehlungen reduzieren und sollten nach Möglichkeit vermieden werden.
- **Warenkorbseite** - Produktempfehlungen werden auf der Warenkorbseite nicht unterstützt, wenn Ihr Store so konfiguriert ist, dass [die Warenkorbseite sofort nach dem Hinzufügen eines Produkts zum Warenkorb angezeigt &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration). Siehe [Erstellen von Empfehlungen](create.md).
- **Untergeordnete Produkte** - Untergeordnete Produkte eines konfigurierbaren Produkts (Sichtbarkeit _Nicht einzeln sichtbar_) werden nicht in einer Empfehlungseinheit angezeigt. Nur das konfigurierbare (übergeordnete) Produkt kann angezeigt werden. Siehe [Produkte filtern](filters.md#product).
- **Deaktivierte oder nicht sichtbare Produkte** - Produkte, die deaktiviert oder nicht einzeln sichtbar sind, können nie in Empfehlungen angezeigt und nicht in Produktfiltern ausgewählt werden.
- **Sonderpreise** - [Sonderpreise](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) mit Start- und Enddatum werden in Empfehlungseinheiten nicht unterstützt. Ein Produkt mit einem Sonderpreis kann in Recommendations angezeigt werden, aber die Einheit zeigt weder den Sonderpreis noch das Start- oder Enddatum an. Kundinnen und Kunden sehen den regulären Preis (oder andere Preisdaten, die von Ihrem Katalog/Preis-Feed bereitgestellt werden), bis sie die Produktseite öffnen.

## Empfehlungseinheiten

- **Aktive Einheiten pro Seitentyp** - Sie können bis zu 50 aktive Empfehlungseinheiten für jeden Seitentyp (Startseite, Kategorie, Produktdetails, Warenkorb, Bestätigung) erstellen. Der Seitentyp wird im Erstellungsfluss ausgegraut, wenn das Limit erreicht ist.
- **Produkte pro Einheit** - Die Anzahl der in einer Empfehlungseinheit angezeigten Produkte kann von 5 (Standard) auf maximal 20 festgelegt werden.
- **Entwurfsstatus** - Nach dem Speichern einer Empfehlung als Entwurf können Sie den Seitentyp oder Empfehlungstyp für diese Einheit nicht ändern. Andere Einstellungen können vor der Aktivierung bearbeitet werden.

## Filter und Bedingungen

- **Dynamische Bedingungen** - Dynamische Bedingungen (z. B. „Produkte in derselben Kategorie wie das aktuelle Produkt“ oder „relative Preisspanne„) sind auf allen Seitentypen mit Ausnahme der Startseite verfügbar. Sie sind auch nicht auf Seiten verfügbar, auf denen Empfehlungen mit Page Builder platziert werden. Siehe [Bedingungen](filters.md#conditions).

## Vorschau und produktionsfremde Umgebungen

- **Kürzlich angezeigte Vorschau** - Der Empfehlungstyp _Kürzlich angezeigt_ kann nicht in der Admin-Instanz in der Vorschau angezeigt werden, da die Daten auf dem Browser-Verlauf basieren und im Admin-Kontext nicht verfügbar sind. Siehe [Recommendations in der Vorschau](create.md#preview).
- **Empfehlungen aus einem anderen Datenbereich** - Wenn Sie [Empfehlungen aus einem anderen SaaS-Datenbereich abrufen](settings.md) (z. B. Produktion) in einer Nicht-Produktions-Storefront, können Sie die Empfehlungen anzeigen, sich aber nicht zu den Produktseiten durchklicken. Dies ist beabsichtigt für Vorschau und Tests.
- **GraphQL und alternativer Datenspeicher** - Bei der Verwendung von Produktempfehlungen über [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) ist der `alternateEnvironmentId`-Parameter (zum Abrufen von Empfehlungen aus einem anderen Datenspeicher) nicht verfügbar. Verwenden Sie die REST-API oder die Admin-Einstellungen, um die Recommendations-Quelle in produktionsfremden Umgebungen zu wechseln.

## API und Konfiguration

- **API-Schlüssel (4.x und höher)** - Sie müssen öffentliche und private API-Schlüssel für Sandbox- und Produktionsumgebungen bereitstellen. Wenn Sie nicht beide Paare von API-Schlüsseln angeben, können Sie im Admin-Bereich nicht auf die Funktion „Produktempfehlungen“ zugreifen. Die Datenerfassung in Ihrer Storefront und vorhandene Empfehlungen funktionieren weiterhin. Siehe [Installieren und Konfigurieren](install-configure.md).

## Cookie-Einschränkungen

- Wenn [Cookie-Einschränkungsmodus](setting-cookie.md) aktiviert ist und Käufer keine Cookies akzeptiert haben, werden bestimmte Empfehlungstypen, die auf Verhaltensdaten angewiesen sind, möglicherweise nicht angezeigt oder zeigen eingeschränkte Ergebnisse an.
- Empfehlungstypen, die nicht auf Verhaltensdaten angewiesen sind (z. B. _Am häufigsten angezeigt_, _Visuelle Ähnlichkeit_) funktionieren weiterhin, wenn Cookie-Einschränkungen aktiviert sind.
- Wenn Cookie-Einschränkungen aktiviert sind, erfassen oder speichern Product Recommendations Verhaltensdaten erst mit Zustimmung des Käufers in Cookies oder im lokalen Speicher.

## Page Builder

- **Metriken und Store-**: Metriken für Page Builder-Empfehlungseinheiten werden nur in der standardmäßigen Store-Ansicht im Arbeitsbereich „Produktempfehlungen“ angezeigt. Um Page Builder-Empfehlungsmetriken in einer nicht standardmäßigen Store-Ansicht anzuzeigen, müssen Sie die Page Builder[Empfehlungseinheit in dieser Store-Ansicht öffnen und &#x200B;](edit.md)bearbeiten) und speichern. Die Metriken werden dann für diese Store-Ansicht angezeigt. Siehe [Page Builder-Integration](page-builder.md).

## B2B

- Product Recommendations berücksichtigt [Kategorieberechtigungen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/category-permissions.html), [freigegebene Kataloge](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html) und kundengruppenspezifische Preise. Käufer sehen nur Empfehlungen für Produkte, auf die sie entsprechend ihrer Segment- und Katalogzuweisung zugreifen können. Siehe [Onboarding](onboarding.md)

## Daten und Bereitschaft

- **Verhaltensdaten** - Für viele Empfehlungstypen sind ausreichende Verhaltensdaten für Storefronts erforderlich (Ansichten, In den Warenkorb legen, Käufe). Neue Stores oder Stores mit geringem Traffic können für diese Typen eingeschränkte oder keine Ergebnisse sehen, bis ausreichende Daten erfasst werden. Überwachen [Bereitschaftsindikatoren](create.md#readiness-indicators) im Administrator.
- **Staging ohne Produktionsdaten** - In einer Nicht-Produktionsumgebung ohne Verhaltensdaten ist der einzige Empfehlungstyp, den Sie testen können, ohne aus der Produktion abzurufen, _mehr wie dies_, das nur katalogbasierte Ähnlichkeiten verwendet. Siehe [Staging-](staging-environment.md).

## Fehlerbehebung

Suchen Sie in der [Commerce-Wissensdatenbank nach Hilfe bei Katalogsynchronisierung, nicht angezeigten Empfehlungen oder anderen häufigen Problemen &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview) wenden Sie sich an den [Support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).
