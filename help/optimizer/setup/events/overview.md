---
title: Übersicht über Ereignisse
description: Erfahren Sie mehr über die Ereignisse [!DNL Adobe Commerce Optimizer]  die verwenden, um die Suche und Empfehlungen zu verbessern.
role: Admin, Developer
recommendations: noCatalog
exl-id: c102c558-a680-4622-80f0-6e5c34d497e9
source-git-commit: 15a708db9a9a31798877ea3a400d5a9f6f930bda
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 0%

---

# -Events

Ereignisse sind ein wichtiges Tool zur Verbesserung des Einkaufserlebnisses und zur Steigerung von Konversionen durch die Nutzung von Echtzeit-Dateneinblicken.

[!DNL Adobe Commerce Optimizer] stellt Storefront-Ereignisse automatisch für Ihre Site bereit. Diese Ereignisse erfassen Daten aus den Interaktionen von Käufern auf Ihrer Site. Diese anonymisierten Daten ermöglichen [Empfehlungen](../../manage-results/recommendation-performance.md), [Produkterkennung](../../manage-results/search-performance.md) und [Erfolgsmetriken](../../manage-results/success-metrics.md).

>[!NOTE]
>
>Die Datenerfassung umfasst keine personenbezogenen Daten (PII). Alle Benutzerkennungen wie Cookie-IDs und IP-Adressen werden streng anonymisiert. [Weitere Informationen](https://www.adobe.com/privacy/experience-cloud.html).

Auf **Seite** Ereignisse“ können Sie die erfassten Storefront-Ereignisdaten beobachten. Mit einem Blick auf die Ereignisdatenerfassung können Händler überprüfen, ob sie Storefront-Ereignisse korrekt implementiert haben und ob Ereignisse erfolgreich erfasst werden. Händler können diese Seite verwenden, um potenzielle Probleme zu identifizieren und Schritte zum Beheben von Ereignisproblemen zu unternehmen.

## Anzahl der Ereignisse

Die Registerkarte **Anzahl von Ereignissen** verfolgt Käuferinteraktionen wie Suchen, Klicks und Käufe, um Ihnen bei der Analyse von Trends und der Verbesserung des Einkaufserlebnisses zu helfen.

![Anzahl der Ereignisse](../../assets/event-counts.png){zoomable="yes"}

| Feld | Beschreibung |
|---|---|
| **Datumsbereich** | Im Folgenden können Sie den Datumsbereich angeben, um eine bestimmte Teilmenge von Daten anzuzeigen. |
| **Storefront-Ereignisse pro Stunde** | Zeigt ein Diagramm der Anzahl der Ereignisse an, die auf Ihrer Storefront ausgelöst wurden. |
| **Storefront-Ereignisse insgesamt** | Eine filterbare Tabelle mit Details zu allen Ereignissen, die auf Ihrer Storefront ausgelöst werden. |

## Plausibilitätsprüfung

Die Registerkarte **Integritätsprüfung** bietet Einblicke in den Zustand jedes Verhaltensereignisses, wodurch eine genaue Datenerfassung und Funktionalität sichergestellt sind. &#x200B;

![Vernunftprüfung](../../assets/sanity-check.png){zoomable="yes"}

| Feld | Beschreibung |
|---|---|
| **Datumsbereich** | Im Folgenden können Sie den Datumsbereich angeben, um eine bestimmte Teilmenge von Daten anzuzeigen. |
| **Produkterkennung** | Zeigt die erforderlichen Ereignisse zum Personalisieren der Produktsuchergebnisse an. Die Spalte **Status** gibt an, ob die Ereignisse empfangen wurden. |
| **Recommendations** | Zeigt die erforderlichen Ereignisse zum Personalisieren von Produktempfehlungen an. Die Spalte **Status** gibt an, ob die Ereignisse empfangen wurden. |

In den folgenden Abschnitten werden Ereignisdetails für [Produkterkennung](#product-discovery) und [Empfehlungen](#recommendations) beschrieben.

### Produkterkennung

Die Produkterkennung nutzt Ereignisse, um Suchalgorithmen wie „Am häufigsten angezeigt“ und „Am häufigsten angezeigt, Das angezeigt“ zu unterstützen.

In dieser Tabelle werden die von der Produkterkennung verwendeten Ereignisse [Rangfolgestrategien](../../merchandising/rules/add.md#intelligent-ranking) beschrieben.

| Rangfolgestrategie | -Events | Seite |
| --- | --- | --- |
| Am häufigsten angezeigt | `page-view`<br>`product-view` | Produktdetailseite |
| Am häufigsten gekauft | `page-view`<br>`place-order` | Warenkorb/Checkout |
| Am häufigsten zum Warenkorb hinzugefügt | `page-view`<br>`add-to-cart` | Produktdetailseite<br>Produktlistenseite<br>Warenkorb<br>Wunschliste |
| hat dieses angezeigt, hat Folgendes angezeigt | `page-view`<br>`product-view` | Produktdetailseite |

#### Erforderliche Dashboard-Ereignisse

Einige Ereignisse sind erforderlich, um das Dashboard [Suchleistung“ ](../../manage-results/search-performance.md)

| Dashboard-Bereich | -Events | Feld verbinden |
| ------------------- | ------------- | ---------- |
| Eindeutige Suchvorgänge | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Null Suchergebnisse | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |

### Recommendations

Es gibt zwei Arten von Daten, die in Empfehlungen verwendet werden:

- **Verhalten** - Daten aus der Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, Artikel, die zum Warenkorb hinzugefügt werden, und Käufe.
- **Katalog** - Produktmetadaten, z. B. Name, Preis, Verfügbarkeit usw.

Adobe Sensei aggregiert die Verhaltens- und Katalogdaten und erstellt für jeden Empfehlungstyp Empfehlungen. Der Recommendations-Service stellt diese Recommendations dann in Form eines Widgets, das das empfohlene Produkt (_) enthält, in Ihrer Storefront_.

Einige Empfehlungstypen verwenden Verhaltensdaten von Kundinnen und Kunden, um Modelle für maschinelles Lernen zu trainieren, um personalisierte Empfehlungen zu erstellen. Andere Empfehlungstypen verwenden nur Katalogdaten und verwenden keine Verhaltensdaten. Wenn Sie Recommendations schnell auf Ihrer Site verwenden möchten, können Sie den Empfehlungstyp `More like this` verwenden.

#### Kaltstart

Ab wann können Empfehlungstypen verwendet werden, die Verhaltensdaten verwenden? Es kommt darauf an. Dies wird als &quot;_&quot;-_ bezeichnet.

Das _Kaltstart_-Problem bezieht sich auf die Zeit, die ein Modell benötigt, um trainiert und effektiv zu werden. Für Recommendations bedeutet dies, abzuwarten, bis Adobe Sensei genügend Daten gesammelt hat, um seine Modelle für maschinelles Lernen zu trainieren, bevor Recommendations-Einheiten auf Ihrer Site bereitgestellt werden. Je mehr Daten die Modelle haben, desto genauer und nützlicher sind die Empfehlungen. Da die Datenerfassung auf einer Live-Site erfolgt, ist es am besten, diesen Prozess frühzeitig zu starten.

Die folgende Tabelle enthält einige allgemeine Hinweise dazu, wie lange es dauert, bis für jeden Empfehlungstyp genügend Daten erfasst sind:

| Empfehlungstyp | Trainingszeit | Notizen |
|---|---|---|
| Beliebtheitsbasiert (`Most viewed`, `Most purchased`, `Most added to cart`) | Variiert | Hängt von der Menge der Ereignisse ab - Ansichten sind am häufigsten und lernen daher schneller; fügt dann zum Warenkorb hinzu und kauft |
| `Viewed this, viewed that` | Erfordert mehr Schulung | Das Volumen der Produktansichten ist annehmbar hoch |
| `Viewed this, bought that`, `Bought this, bought that` | Erfordert die meiste Schulung | Kaufereignisse sind die seltensten Ereignisse auf einer Commerce-Site, insbesondere im Vergleich zu Produktansichten |
| `Trending` | Erfordert drei Tage Daten, um eine Popularitätsbasislinie zu erstellen | Der Trend ist ein Maß für die jüngste Dynamik in der Popularität eines Produkts verglichen mit seiner eigenen Popularitätsbasislinie. Der Trend-Score eines Produkts wird anhand eines Vordergrundsatzes (aktuelle Popularität über 24 Stunden) und eines Hintergrundsatzes (Popularitätsbasislinie über 72 Stunden) berechnet. Wenn die Popularität eines Elements innerhalb eines Zeitraums von 24 Stunden im Vergleich zu seiner Grundbeliebtheit signifikant zunimmt, erhält es einen hohen Trend-Score. Jedes Produkt hat diese Bewertung, und die Artikel mit der höchsten Bewertung zu jeder Zeit umfassen die Gruppe der Top-Trend-Produkte. |

Andere Variablen, die sich auf die für das Training benötigte Zeit auswirken können:

- Höheres Traffic-Volumen trägt zu schnellerem Lernen bei
- Einige Empfehlungstypen trainieren schneller als andere
- [!DNL Adobe Commerce Optimizer] berechnet die Verhaltensdaten alle vier Stunden neu. Empfehlungen werden umso genauer, je länger sie auf Ihrer Site verwendet werden.

Auf der Seite „Empfehlung erstellen[ werden Bereitschaftsindikatoren angezeigt, damit Sie den Trainings-Fortschritt ](../../merchandising/recommendations/create.md#readiness-indicators) jeden Empfehlungstyp visualisieren können.

Während Daten auf Ihrer Live-Site erfasst werden und die Modelle für maschinelles Lernen trainiert werden, können Sie andere Test- und Konfigurationsaufgaben abschließen, die zum Einrichten von Empfehlungen erforderlich sind. Wenn Sie mit dieser Arbeit fertig sind, verfügen die Modelle über genügend Daten, um nützliche Empfehlungen zu erstellen, sodass Sie sie in Ihrer Storefront bereitstellen können.

Wenn auf Ihrer Site nicht genügend Traffic (Ansichten, Käufe, Trends) für die meisten Produkt-SKUs vorhanden ist, sind möglicherweise nicht genügend Daten vorhanden, um den Lernprozess abzuschließen. Dadurch kann der Bereitschaftsindikator im Recommendations-Arbeitsbereich hängen bleiben. Die Bereitschaftsindikatoren sollen Händlern einen weiteren Datenpunkt bei der Auswahl des Recommendations-Typs bieten, der für ihren Store besser ist. Die Zahlen sind Richtwerte und erreichen möglicherweise nie 100 %. [Weitere ](../../merchandising/recommendations/create.md#readiness-indicators) zu Bereitschaftsindikatoren.

#### Empfehlungen für Backups

Wenn die Eingabedaten nicht ausreichen, um alle angeforderten Empfehlungselemente in einer Einheit bereitzustellen, bietet [!DNL Adobe Commerce Optimizer] Sicherungsempfehlungen zum Ausfüllen von Empfehlungseinheiten. Wenn Sie beispielsweise den `Recommended for you` Empfehlungstyp auf Ihrer Homepage bereitstellen, hat ein Erstkäufer auf Ihrer Site nicht genügend Verhaltensdaten generiert, um personalisierte Produkte korrekt zu empfehlen. In diesem Fall [!DNL Adobe Commerce Optimizer] Elemente basierend auf dem `Most viewed` Empfehlungstyp an diesen Einkäufer.

Bei unzureichender Erfassung von Eingabedaten greifen die folgenden Empfehlungstypen auf `Most viewed` Empfehlungstyp zurück:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

#### Empfehlungsspezifische Ereignisse

In der folgenden Tabelle sind die Ereignisse aufgeführt, die ausgelöst werden, wenn Käufer mit Empfehlungseinheiten in der Storefront interagieren. Die erfassten Ereignisdaten ermöglichen es den [Metriken](../../manage-results/recommendation-performance.md) zu analysieren, wie gut Ihre Empfehlungen funktionieren.

| Ereignis | Beschreibung |
| --- | --- |
| `impression-render` | Wird gesendet, wenn die Empfehlungseinheit auf der Seite dargestellt wird. Wenn eine Seite zwei Empfehlungseinheiten hat (gekauft, Ansicht), werden zwei `impression-render` gesendet. Dieses Ereignis wird verwendet, um die Metrik für Impressionen zu verfolgen. |
| `rec-add-to-cart-click` | Der Käufer klickt auf die Schaltfläche **Zum Warenkorb hinzufügen** für einen Artikel in der Empfehlungseinheit. |
| `rec-click` | Der Käufer klickt in der Empfehlungseinheit auf ein Produkt. |
| `view` | Wird gesendet, wenn die Empfehlungseinheit zu mindestens 50 % sichtbar wird, z. B. durch Scrollen auf der Seite nach unten. Wenn beispielsweise eine Empfehlungseinheit über zwei Zeilen verfügt, wird ein `view` gesendet, sobald eine Zeile plus ein Pixel der zweiten Zeile für den Erstkäufer sichtbar wird. Wenn der Erstkäufer die Seite mehrmals nach oben und unten scrollt, wird das `view` so oft gesendet, wie der Erstkäufer die gesamte Empfehlungseinheit erneut auf der Seite sieht. |

#### Erforderliche Dashboard-Ereignisse

Die folgenden Ereignisse sind erforderlich, um das [Recommendations-Performance-Dashboard“ ](../../manage-results/recommendation-performance.md)

| Dashboard-Spalte | -Events | Feld verbinden |
| ---------------- | --------- | ----------- |
| Impressionen | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | `unitId` |
| Ansichten | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | `unitId` |
| Klicks | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | `unitId` |
| Einnahmen | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| LT-Umsatz | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |

Die folgenden Ereignisse gelten nicht nur für Recommendations, sondern sind für Adobe Sensei erforderlich, um Kundendaten korrekt zu interpretieren:

- `view`
- `add-to-cart`
- `place-order`

#### Empfehlungstyp

In dieser Tabelle werden die von den einzelnen Empfehlungstypen verwendeten Ereignisse beschrieben.

| Empfehlungstyp | -Events | Seite |
| --- | --- | --- |
| Am häufigsten angezeigt | `page-view`<br>`product-view` | Produktdetailseite |
| Am häufigsten gekauft | `page-view`<br>`place-order` | Warenkorb/Checkout |
| Am häufigsten zum Warenkorb hinzugefügt | `page-view`<br>`add-to-cart` | Produktdetailseite<br>Produktlistenseite<br>Warenkorb<br>Wunschliste |
| hat dieses angezeigt, hat Folgendes angezeigt | `page-view`<br>`product-view` | Produktdetailseite |
| Das hier angesehen, das gekauft | `page-view`<br>`product-view` | Produktdetailseite/<br>/Checkout |
| Das kaufte ich, das kaufte ich | `page-view`<br>`product-view` | Produktdetailseite |
| Trend | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: Zum Kauf anzeigen | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: Zum Kauf anzeigen | `page-view`<br>`place-order` | Warenkorb/Checkout |
| Konversion: In Warenkorb anzeigen | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: In Warenkorb anzeigen | `page-view`<br>`add-to-cart` | Produktdetailseite<br>Produktlistenseite.<br>.<br> |

## Support

Wenn Sie Datendiskrepanzen feststellen oder Empfehlungen und Suchergebnisse nicht erwartungsgemäß funktionieren, [ Sie ein Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).
