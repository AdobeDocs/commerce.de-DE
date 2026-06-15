---
title: Katalogquelle
description: Erfahren Sie, was Katalogquellen sind und wie sie den autorisierenden Umfang von Produkten, Attributen und Kategorien für das Such-, Filter- und Sortierverhalten definieren.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
autotag-review: '2026-06-09T19:36:23.516Z'
TQID: 'https://experienceleague.adobe.com/MiLbuYx6Pf95n3jvrgvou05Ery9XHXskx8p6KrN6CYg'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
subfeature_v2:
  - id: ae62cf09-5996-4921-bda8-fbe67b62e470
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: b23e006f-0a29-4f1d-8fd0-77aa56f3d12b
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 69f39a6a62e05c86a0e2897d09079543b3d8830e
workflow-type: tm+mt
source-wordcount: 450
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

* Eine Katalogquelle wird erstellt, indem ein Produkt über die Datenaufnahme-API aufgenommen wird. Weitere Informationen finden [&#x200B; unter &#x200B;](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/) - Datenaufnahme .
* Die Einzigartigkeit des Produkts wird durch die SKU und die Katalogquelle bestimmt.
* Käufer greifen nicht direkt auf Katalogquellen zu. Katalogdaten werden über (Katalogansichten[&#x200B; der Storefront &#x200B;](catalog-view.md).

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

