---
source-git-commit: 4032a0871d0a9b129ad870c93f62a2a7596ea8b7
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%
---
<!--
SOURCE OF TRUTH: Edit this file in the commerce.en repo:
https://github.com/Adobe-Enterprise-Docs/commerce.de-DE/blob/main/help/_includes/ccdm-shared/merchandising/overview.md

This content is shared by the Adobe Commerce Optimizer Guide (commerce.en) and the
Merchandising Services with CCDM Guide (commerce-admin.en). Changes made in commerce.en
are synced automatically to commerce-admin.en, so do not edit the copy in that repo.
This includes related images in help/assets/ccdm-shared/.
-->

# Adobe Merchandising

Erfahren Sie, wie Sie durch Produkterkennung und Empfehlungen personalisierte Erlebnisse für Ihre Kunden erstellen können.

Diese Adobe Merchandising-Services basieren auf dem zusammensetzbaren Katalogdatenmodell (Composable Catalog Data Model, CCDM), das *Produktdaten* vom *Produktkontext* trennt. Zu den Produktdaten gehören SKUs, Attribute, Metadaten, Assets und Preise. Der Produktkontext definiert, wie diese Daten bereitgestellt werden, einschließlich [Katalogansichten](/help/optimizer/setup/catalog-view.md), [Datenzugriffsrichtlinien](/help/optimizer/setup/policies.md) und [Katalogquellen](/help/optimizer/setup/catalog-sources.md) (Gebietsschemata). Da Katalogansichten und Richtlinien Storefront-Daten steuern, können Sie benutzerdefinierte Kataloge für B2B-, B2C- und D2C-Modelle erstellen und Einkaufserlebnisse anpassen, ohne die Basisdaten zu duplizieren.

- **Product Discovery**: Rüstet Merchandiser mit leistungsstarken Tools aus, um das Einkaufserlebnis zu kuratieren und zu optimieren und sicherzustellen, dass Kunden die richtigen Produkte schnell und zum richtigen Zeitpunkt finden. Durch die Anpassung des Suchverhaltens können Sie die Sichtbarkeit, Relevanz und Konversion des Produkts direkt beeinflussen.

  Mit der Produkterkennung können Sie Käufer durch die Konfiguration zu den relevantesten Produkten mit minimaler Reibung führen:

  - [**Merchandising-Regeln**](rules/overview.md) - Verstärken, Begraben, Anheften oder Filtern von Produkten in Suchergebnissen, Standardproduktlisten und Kategorieseiten.
  - [**Facetten**](facets/overview.md) - Konfigurieren Sie die Filter, die Käufer verwenden, um die Such- und Kategorienergebnisse einzugrenzen.
  - [**Synonyme**](synonyms/overview.md) - Ordnen Sie äquivalente Begriffe zu, damit verschiedene Suchbegriffe dieselben Produkte zurückgeben.

  Die semantische Suche, die standardmäßig in [Einstellungen](../settings.md) aktiviert ist, verbessert die Relevanz für Abfragen, die auf natürlicher Sprache und Absichten basieren. In den Einstellungen können Sie auch Preisfacetten, Katalogsprache und erweiterte semantische und Fuzzy-Suchoptionen konfigurieren.

- [**Recommendations**](recommendations/overview.md) - Verwenden Sie Algorithmen für künstliche Intelligenz und maschinelles Lernen, um das aggregierte Besucherverhalten und Produktinteraktionen in Ihrer Storefront zu analysieren. In Kombination mit Ihrem Katalog liefern diese Daten höchst ansprechende, relevante und personalisierte Erlebnisse. Empfehlungen werden in der Storefront als Einheiten mit Beschriftungen angezeigt, z. B. „Kunden, die dieses Produkt angesehen haben, haben es auch angesehen“. Sie können Recommendations direkt im Recommendations -Arbeitsbereich erstellen, verwalten und bereitstellen und auf der gesamten Journey platzieren, um Werbeziele, Crosssell-Strategien und personalisierte Erlebnisse zu unterstützen.
