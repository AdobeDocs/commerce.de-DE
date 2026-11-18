---
source-git-commit: e3be9274ca8db80d3559b24a5c8be36f5d61b2ba
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 0%
---
<!--
SOURCE OF TRUTH: Edit this file in the commerce.en repo:
https://github.com/Adobe-Enterprise-Docs/commerce.en/blob/main/help/_includes/ccdm-shared/merchandising/rules/best-practice.md

This content is shared by the Adobe Commerce Optimizer Guide (commerce.en) and the
Merchandising Services with CCDM Guide (commerce-admin.en). Changes made in commerce.en
are synced automatically to commerce-admin.en, so do not edit the copy in that repo.
This includes related images in help/assets/ccdm-shared/.
-->

# Best Practices für Merchandising-Regeln

Um Konversionen und Umsätze zu optimieren, implementieren Sie effektive **Suchregeln**, eine **Standardauflistungsregel** und **[Kategorieregeln](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#rule-types)**. Passen Sie Rankings mithilfe von Verkaufsdaten, Lagern, Promotions und [intelligentem Ranking](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#intelligent-ranking) an.

Verwenden Sie [Unterdrückungsregeln für Suchen](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/overview#search-suppression-rules) nur, wenn übereinstimmende Kundenabfragen null Produkte zurückgeben müssen - nicht, wenn Produkte ein anderes Ranking benötigen.

Es ist von entscheidender Bedeutung, eine gut durchdachte **Standardregel“**. Ihre [Standardregel](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/overview#default-rule) bestimmt, wie Suchergebnisse zunächst sortiert werden, wenn keine spezifischere Suchregel gilt, was die Erkennung und Kaufwahrscheinlichkeit verbessert. Überprüfen Sie diese regelmäßig, damit sie mit den Anforderungen und Kampagnen der Kunden Schritt hält.

## Tipps zum Optimieren von Suchregeln

- Produkte mit hohen Verkaufsmengen oder kürzlichen Verkaufsaktivitäten heften oder ankurbeln.
- Priorisieren Sie Produkte mit hohen Bewertungen und positiven Bewertungen.
- Stellen Sie sicher, dass Artikel auf Lager höher eingestuft werden.
- Produkte mit höheren Gewinnspannen leicht priorisieren, ohne die Relevanz zu beeinträchtigen.
- Heben Sie Produkte hervor, die zum Verkauf stehen oder Teil von Sonderaktionen sind.
- Legen Sie Suchregeln während der Promotion oder des Verkaufszeitraums automatisch fest, indem Sie den Datumsbereich während des Promotion-Zeitraums verwenden.
- Passen Sie Suchergebnisse mithilfe von „Intelligent Ranking[ wie &quot;](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#intelligent-ranking) für Sie empfohlen“, „Am häufigsten angezeigt“ usw. an das individuelle Kundenverhalten an.
- Wenn eine andere intelligente Strategie als **Keine** ausgewählt ist, stimmen Sie **[Intelligente Rangverstärkung](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#intelligent-ranking-boost)** pro Regel ab und validieren Sie **Testen Sie Ihre Regel** vor der Veröffentlichung.
- Verwenden Sie immer das Bedienfeld „Regel testen“, um eine Vorschau anzuzeigen, wie sich Ihre intelligente Rangfolgestrategie auf die tatsächlichen Suchergebnisse für verschiedene Abfragen auswirkt.

## Tipps für Kategorieregeln

- Verwenden Sie [Kategorieregeln](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#rule-types) auf Seiten mit hohem Traffic oder mit hoher Marge **Kategorieseiten** auf denen die kuratierte Reihenfolge ebenso wichtig ist wie die Suche - z. B. saisonale Sammlungen oder vorgestellte Abteilungen.
- Ordnen Sie **intelligentes Ranking** (z. B. Trend, am häufigsten angezeigt) dem zu, wie Käufer diese Kategorie durchsuchen. Kategorieseiten verwenden nicht den Suchabfragetext, wie Suchregeln das tun. Siehe [Intelligente Rangfolge](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#intelligent-ranking). Verwenden Sie für andere intelligente **als &quot;**&quot; **[Intelligente Rangverstärkung](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#intelligent-ranking-boost)** und die Kategorievorschau, um die Verhaltensstärke für diese Kategorieregel anzupassen.
- Wenden Sie **PIN**, **BOOST** und **BURY** konsistent mit Ihrem Kampagnenplan an. Denken Sie daran, dass manuelle Positionen in der Regel nur dann gelten, wenn der Käufer die **Standardsortierung** für den Eintrag verwendet. Siehe [Manuelle Rangfolge](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#manual-ranking).
- Vorschau im **Kategorie**-Regelfluss im Editor und Validierung in der Storefront nach der Veröffentlichung, dieselbe Disziplin, die Sie für das Bedienfeld „Regel testen“ bei der Suche verwenden.

## Best Practices und Anwendungsfälle für die Suchunterdrückung {#search-suppression-best-practices}

Eine Suchunterdrückungsregel blockiert Ergebnisse für Abfragen, die ihren Bedingungen entsprechen, sodass die Storefront eine Suchergebnisseite mit null Produkten anzeigt. Der Regeleditor stellt keine Vorschau für Unterdrückungsregeln bereit. Verwenden Sie die engste Bedingung, die die Einschränkung erfüllt, und befolgen Sie dann [Regeln für die Suchunterdrückung erstellen und verwalten](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add#search-suppression-rules). Nachdem die Regel aktiviert wurde, überprüfen Sie übereinstimmende und nicht übereinstimmende Suchen in der Storefront. Überprüfen Sie die tatsächliche ergebnislose Präsentation der Storefront.

| Anwendungsfall | Empfohlene Konfiguration | Was zu überprüfen ist |
| --- | --- | --- |
| Einhaltung gesetzlicher Vorschriften für die Suche | Ordnen Sie die Regel der betroffenen Katalogansicht zu und stimmen Sie mit den eingeschränkten Suchbegriffen überein. | Bestätigen Sie die Bedingungen mit Ihrem Compliance-Team. Die Suchunterdrückung allein verhindert nicht den Zugriff über Kategoriennavigation, Merchandising-Seiten, Empfehlungen oder direkte Produkt-URLs. |
| Branding-Beschränkungen | Verwenden Sie **Abfrage enthält** wenn ein eingeschränkter Markenname in längeren Abfragen blockiert werden muss. | Nachdem die Regel aktiv geworden ist, überprüfen Sie nicht verwandte Storefront-Abfragen, die ähnlichen Text enthalten, um die Unterdrückung legitimer Suchen zu vermeiden. |
| Verhindern, dass ein bestimmter Suchbegriff Ergebnisse zurückgibt | Verwenden **Abfrage ist** für eine exakte Phrase, die keine Produkte zurückgeben sollte. | Verwandte Phrasen separat überprüfen. Eine Bedingung mit exakter Übereinstimmung blockiert nicht jede Abfrage, die diese Phrase enthält. |
| Einschränkungen bei Abfragepräfixen oder -suffixen | Verwenden Sie **Abfrage beginnt mit** oder **Abfrage endet mit** wenn die Position des eingeschränkten Texts wichtig ist. | Nachdem die Regel aktiv geworden ist, überprüfen Sie Storefront-Abfragen mit dem Text am Anfang, in der Mitte und am Ende, um den beabsichtigten Umfang zu bestätigen. |
| Temporäre Sucheinschränkungen | Legen Sie ein Start- und Enddatum für eine zeitlich begrenzte Einschränkung fest. | Bestätigen Sie den Zeitplan und den aktivierten Status und überprüfen Sie, ob die Regel nach Ablauf der Einschränkung weiterhin benötigt wird. |

- Geben Sie jeder Regel einen beschreibenden Namen und notieren Sie den Grund für die Einschränkung in der Beschreibung.
- Überprüfen Sie Abfragebedingungen vor dem Veröffentlichen von Änderungen. Nachdem die Regel aktiviert wurde, überprüfen Sie Storefront-Abfragen, die blockiert werden sollen, und Abfragen, die weiterhin Produkte zurückgeben sollen. Die Aktualisierung zwischengespeicherter Abfrageergebnisse kann bis zu 15 Minuten dauern.
- Überprüfen Sie den Status „Keine Ergebnisse“ der Storefront und stellen Sie sicher, dass Käufer eine nützliche Möglichkeit haben, weiter zu browsen, z. B. indem sie die Abfrage überarbeiten oder zu einer Kategorie navigieren, wo dies von der Storefront unterstützt wird.
- Verwenden Sie die Abfrageunterdrückung nicht als Ersatz für Ausschlüsse auf Produktebene. Um Produkte über Suchergebnisse, Suchvorschläge und die automatische Vervollständigung hinweg auszuschließen, verwenden Sie manuelle Ausschlüsse oder **Attribut-basierte Merchandising** Ereignisse mit einer **Ausblenden** -Aktion in der **Standard-Suchregel**.
- Überprüfen Sie die aktiven Unterdrückungsregeln regelmäßig. Deaktivieren Sie nicht mehr benötigte Regeln oder bearbeiten und veröffentlichen Sie sie, wenn sich die Einschränkungen ändern.
