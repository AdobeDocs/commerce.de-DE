---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%
---
Katalogquellen stellen autoritative Bereiche von Produkten, Attributen und Kategorien dar. Sie werden normalerweise Sprachgrenzen, Zielgruppen- oder Systemgrenzen zugeordnet und bestimmen das Such-, Filter- und Sortierverhalten.

## Katalogquellen im Vergleich zu verwandten Konzepten

Wenn Sie verstehen, wie Katalogquellen mit anderen Merchandising Services-Konzepten zusammenhängen, können Sie Ihre Daten korrekt modellieren:

* **Katalogquelle** - Der zugrunde liegende Datenkontext, der Produktinformationen bereitstellt. Eine Katalogquelle stellt normalerweise ein Gebietsschema (z. B. `en-US`, `fr-CA`) oder einen Datenkontext dar, der von einem externen System wie einem PIM oder ERP bereitgestellt wird. Produkte, Attributmetadaten und Kategorien sind alle pro Katalogquelle enthalten. Eine Katalogquelle definiert die Herkunft von Rohkatalogdaten und ihre Auswirkungen auf die Produkterkennung (Suchergebnisse, Filterung und Sortierverhalten).

* **[Katalogansicht](/help/optimizer/setup/catalog-view.md)** - Eine konfigurierte Ansicht Ihres Katalogs für eine bestimmte Geschäftsanforderung. Eine Katalogansicht wählt Katalogquellen (oder Gebietsschema) aus, wendet [Richtlinien](/help/optimizer/setup/policies.md) an, um die Sichtbarkeit von Produkten zu filtern, und verknüpft [Preisbücher](/help/optimizer/setup/pricebooks.md) mit der Ansicht. Eine einzelne Katalogquelle kann für viele Katalogansichten verwendet werden (z. B. eine `en-US` mit separaten Katalogansichten für verschiedene Marken oder Regionen). Stellen Sie sich eine Katalogansicht wie *vor* wie Sie diese Daten einer Storefront, einem Kanal oder einer Zielgruppe bereitstellen.

* **[Katalogebene](catalog-layer.md)** - Eine Ebene, die auf die Basiskatalogdaten angewendet wird, um Produktattribute (Name, Beschreibung, Bilder, Metadaten) zu ändern, ohne die Quelldaten zu ändern. Verwenden Sie Katalogebenen, wenn Unterschiede sich nur auf die Storefront-Anzeige auswirken dürfen - nicht auf die Produkterkennung.

## So werden Katalogquellen befüllt

Katalogquellen werden über die Katalogdatenaufnahme befüllt. Wie Sie diese Daten bereitstellen, hängt von Ihrer Implementierung ab:

- **Adobe Commerce as a Cloud Service mit CCDM** - Native Synchronisierung liefert Katalogdaten von Commerce Foundation. Verwalten Sie die zugrunde liegenden Produkte und die Store-View-Konfiguration in Commerce Foundation und überwachen Sie die Synchronisierung im [Datensynchronisierung](data-sync.md)-Arbeitsbereich. Es ist keine separate Datenaufnahme -API-Integration erforderlich.
- **Adobe Commerce Optimizer mit einem Backend eines Drittanbieters** - Ihre Integration liefert Informationen zu Produkten und Katalogquellen über die [Datenaufnahme-API](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/).


## Regeln und Einschränkungen

* Eine Katalogquelle wird erstellt, wenn Katalogdaten für ein neues Gebietsschema oder Quellsystem zum ersten Mal von der Merchandising Services-Datenschicht empfangen werden.
* Die Einzigartigkeit des Produkts wird durch die SKU und die Katalogquelle bestimmt.
* Käufer greifen nicht direkt auf Katalogquellen zu. Katalogdaten werden über (Katalogansichten[ der Storefront ](catalog-view.md).

## Modellierungsanleitung

Beachten Sie bei der Planung Ihrer Katalogstruktur die folgenden Hinweise. Verwalten Sie für Adobe Commerce as a Cloud Service mit CCDM die zugrunde liegende Konfiguration in Commerce Foundation, anstatt Katalogquellen über eine separate Aufnahmeintegration zu erstellen.

* Verwenden Sie für jede Katalogsprache eine separate Katalogquelle.
* Verwenden Sie separate Katalogquellen, wenn Produkt- und Attributunterschiede das Such-, Filter- oder Sortierverhalten beeinflussen müssen, z. B. unterschiedliche Einstellungen für die Durchsuchbarkeit oder Filterbarkeit.
* Verwenden Sie [Katalogebenen](catalog-layer.md) wenn Produkt- und Attributunterschiede die Produktpräsentation beeinflussen müssen, ohne das Such-, Filter- oder Sortierverhalten zu ändern.

>[!MORELIKETHIS]
>
> * [Katalogansichten](catalog-view.md) - Konfigurieren gefilterter, preisgesteuerter Ansichten über einer Katalogquelle
> * [Katalogebenen](catalog-layer.md) - Ändern der Produktpräsentation ohne Änderung der Quelldaten
> * [Richtlinien](policies.md) - Erstellen von attributbasierten Filtern für Katalogansichten
> * [Preisbücher](/help/optimizer/setup/pricebooks.md) - Verwalten von Preisstrukturen für verschiedene Kundensegmente
> * [Eingeschränkte Zugriffsschlüssel](restricted-access-keys.md) - Schützen einer Katalogansicht mit Authentifizierung mit signierten Token
