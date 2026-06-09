---
title: Katalogquelle
description: Erfahren Sie, was Katalogquellen sind und wie sie den autorisierenden Umfang von Produkten, Attributen und Kategorien für das Such-, Filter- und Sortierverhalten definieren.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: dc50e4d7bcd118b2b9a800779c600ade5560e0bf
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---


# Katalogquelle

Eine Katalogquelle stellt einen zulässigen Umfang von Produkten, Attributen und Kategorien dar. Katalogquellen werden in der Regel Sprach-, Zielgruppen- oder Ursprungsgrenzen zugeordnet und bestimmen das Such-, Filter- und Sortierverhalten.

## Katalogquelle und verwandte Konzepte im Vergleich

Wenn Sie verstehen, wie eine Katalogquelle mit anderen [!DNL Adobe Commerce Optimizer] Konzepten in Beziehung steht, können Sie Ihre Daten korrekt modellieren:

* **Katalogquelle** - Der zugrunde liegende Datenkontext, der Produktinformationen bereitstellt. Eine Katalogquelle ist normalerweise ein Gebietsschema (z. B. `en-US`, `fr-CA`) oder ein externes System wie ein PIM oder ERP. Produkte, Attribute, Metadaten und Kategorien sind alle pro Katalogquelle enthalten. Stellen Sie sich eine Katalogquelle vor *aus* die Rohkatalogdaten stammen und *wie* sie sich auf die Produkterkennung auswirken (Suchergebnisse, Filterung und Sortierverhalten).

* **[Katalogansicht](catalog-view.md)** - Eine konfigurierte Ansicht Ihres Katalogs für eine bestimmte Geschäftsanforderung. Wenn Sie eine Katalogansicht erstellen, wählen Sie die zu verwendende Katalogquelle (oder das zu verwendende Gebietsschema) aus und fügen dann [Richtlinien](policies.md) hinzu, um zu filtern, welche Produkte sichtbar sind, und verknüpfen [Preislisten](pricebooks.md) um die Preise zu steuern. Eine einzelne Katalogquelle kann für viele Katalogansichten verwendet werden (z. B. eine `en-US` mit separaten Katalogansichten für verschiedene Marken oder Regionen). Stellen Sie sich eine Katalogansicht wie *vor* wie Sie diese Daten einer Storefront, einem Kanal oder einer Zielgruppe bereitstellen.

* **[Katalogebene](catalog-layer.md)** - Eine Ebene, die auf die Basiskatalogdaten angewendet wird, um Produktattribute (Name, Beschreibung, Bilder, Metadaten) zu ändern, ohne die Quelldaten zu ändern. Verwenden Sie Katalogebenen, wenn Unterschiede sich nur auf die Storefront-Anzeige auswirken dürfen - nicht auf die Produkterkennung.

## Regeln und Einschränkungen

* Eine Katalogquelle wird erstellt, indem ein Produkt über die Datenaufnahme-API aufgenommen wird. Weitere Informationen finden [ unter ](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/) - Datenaufnahme .
* Die Einzigartigkeit des Produkts wird durch die SKU und die Katalogquelle bestimmt.
* Käufer greifen nicht direkt auf Katalogquellen zu. Katalogdaten werden über (Katalogansichten[ der Storefront ](catalog-view.md).

## Modellierungsanleitung

Verwenden Sie die folgenden Anleitungen, wenn Sie entscheiden, wie Sie Ihre Katalogquellen strukturieren möchten:

* Erstellen Sie eine separate Katalogquelle für eine andere Katalogsprache.
* Verwenden Sie separate Katalogquellen, wenn Produkt- und Attributunterschiede das Such-, Filter- oder Sortierverhalten beeinflussen müssen (z. B. unterschiedliche Durchsuchbarkeit, Filterbarkeit oder Facettenkonfiguration für dasselbe Attribut).
* Verwenden Sie [Katalogebenen](catalog-layer.md) wenn Produkt- und Attributunterschiede nur die Anzeige in der Storefront betreffen sollen, nicht die Produkterkennung.

>[!MORELIKETHIS]
>
> * [Katalogansichten](catalog-view.md) - Konfigurieren gefilterter, preisgesteuerter Ansichten über einer Katalogquelle
> * [Katalogebenen](catalog-layer.md) - Ändern der Produktpräsentation ohne Änderung der Quelldaten
> * [Richtlinien](policies.md) - Erstellen von attributbasierten Filtern für Katalogansichten
> * [Preisbücher](pricebooks.md) - Verwalten von Preisstrukturen für verschiedene Kundensegmente
