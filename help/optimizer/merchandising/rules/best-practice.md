---
title: Best Practices für Merchandising-Regeln
description: Erfahren Sie mehr über die Best Practices zur Implementierung von Merchandising-Regeln für Such-, Standard- und Kategorieseiten.
role: Admin, Developer
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: cc8d0879-c253-4ad4-8e7d-e066dff9112d
source-git-commit: 14c4178338859d55a7391139033d51d1aa6f7678
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Best Practices für Merchandising-Regeln

Um Konversionen und Umsätze zu optimieren, implementieren Sie effektive **Suchregeln** eine **(Standardauflistung** und **[Kategorieregeln](add.md#rule-types)** (Beta). Passen Sie Rankings mithilfe von Verkaufsdaten, Lagern, Promotions und [intelligentem Ranking](add.md#intelligent-ranking) an.

Es ist von entscheidender Bedeutung, eine gut durchdachte **Standardregel“**. Ihre [Standardregel](overview.md#default-rule) bestimmt, wie Suchergebnisse zunächst sortiert werden, wenn keine spezifischere Suchregel gilt, was die Erkennung und Kaufwahrscheinlichkeit verbessert. Überprüfen Sie diese regelmäßig, damit sie mit den Anforderungen und Kampagnen der Kunden Schritt hält.

## Tipps zum Optimieren von Suchregeln

- Produkte mit hohen Verkaufsmengen oder kürzlichen Verkaufsaktivitäten heften oder ankurbeln.
- Priorisieren Sie Produkte mit hohen Bewertungen und positiven Bewertungen.
- Stellen Sie sicher, dass Artikel auf Lager höher eingestuft werden.
- Produkte mit höheren Gewinnspannen leicht priorisieren, ohne die Relevanz zu beeinträchtigen.
- Heben Sie Produkte hervor, die zum Verkauf stehen oder Teil von Sonderaktionen sind.
- Legen Sie Suchregeln während der Promotion oder des Verkaufszeitraums automatisch fest, indem Sie den Datumsbereich während des Promotion-Zeitraums verwenden.
- Passen Sie Suchergebnisse mithilfe von „Intelligent Ranking[&#x200B; wie &quot;](add.md#intelligent-ranking) für Sie empfohlen“, „Am häufigsten angezeigt“ usw. an das individuelle Kundenverhalten an.
- Verwenden Sie immer das Bedienfeld „Regel testen“, um eine Vorschau anzuzeigen, wie sich Ihre intelligente Rangfolgestrategie auf die tatsächlichen Suchergebnisse für verschiedene Abfragen auswirkt.

## Tipps für Kategorieregeln

>[!IMPORTANT]
>
>Kategorieregeln befinden sich in der Beta-Phase.

- Verwenden Sie [Kategorieregeln](add.md#rule-types) auf Seiten mit hohem Traffic oder mit hoher Marge **Kategorieseiten** auf denen die kuratierte Reihenfolge ebenso wichtig ist wie die Suche - z. B. saisonale Sammlungen oder vorgestellte Abteilungen.
- Ordnen Sie **intelligentes Ranking** (z. B. Trend, am häufigsten angezeigt) dem zu, wie Käufer diese Kategorie durchsuchen. Kategorieseiten verwenden nicht den Suchabfragetext, wie Suchregeln das tun. Siehe [Intelligente Rangfolge](add.md#intelligent-ranking).
- Wenden Sie **PIN**, **BOOST** und **BURY** konsistent mit Ihrem Kampagnenplan an. Denken Sie daran, dass manuelle Positionen in der Regel nur dann gelten, wenn der Käufer die **Standardsortierung** für den Eintrag verwendet. Siehe [Manuelle Rangfolge](add.md#manual-ranking).
- Vorschau im **Kategorie**-Regelfluss im Editor und Validierung in der Storefront nach der Veröffentlichung, dieselbe Disziplin, die Sie für das Bedienfeld „Regel testen“ bei der Suche verwenden.
