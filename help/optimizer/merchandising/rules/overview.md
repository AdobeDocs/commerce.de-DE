---
title: Merchandising-Regeln
description: '[!DNL Adobe Commerce Optimizer] Merchandising-Regeln kombinieren Logik mit Aktionen, um Suchergebnisse, Standardproduktlisten und Kategorieseiten zu gestalten.'
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: f2a9b5e8-d23d-4855-b424-ca6b40e057df
source-git-commit: 14c4178338859d55a7391139033d51d1aa6f7678
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Merchandising-Regeln

Merchandising-Regeln kombinieren Logik mit Aktionen, um das Erscheinungsbild von Produkten **Suchergebnisse** auf **Standardproduktlisten** (**Alle Produktlisten**) und auf **Kategorieseiten** ([Kategorienregeln](#category-rules) befinden sich in der Beta-Phase) zu gestalten. Sie können Produkte ankurbeln, vergraben, anheften oder ausblenden und **intelligentes Ranking** anwenden, sodass die Listeneinträge Ihre Geschäftsziele widerspiegeln.

Jede **Suchregel** besteht aus drei Hauptkomponenten:

- **Bedingungen** - Abfragebasierte Anforderungen, bei denen eine Aktion durch einen Trigger ausgelöst wird, wenn die Suche des Käufers übereinstimmt.
- **Ereignisse** - Aktionen, die stattfinden, wenn die Bedingungen erfüllt sind (manuelle Rangfolge und zugehörige Ereignisse).
- **Details** - Der Name der Regel sowie optionaler Zeitrahmen und Beschreibung.

**Kategorieregeln** Verwenden Sie **Kategorieauswahl** anstelle von Suchabfragebedingungen; intelligentes Ranking und manuelles Ranking funktionieren auf die gleiche Weise wie für die Suche, wobei die Unterschiede in „Regeln erstellen [&#x200B; verwalten“ &#x200B;](add.md).

Sie können mehrere Bedingungen und Aktionen für Suchregeln kombinieren und jede Regel so planen, dass sie für einen Zeitraum aktiv ist. Sie können auch eine **Standardregel** festlegen (**Alle Produktlisten**), die gilt, wenn keine spezifischere Such- oder Kategorieregel gilt.

## Kategorieregeln {#category-rules}

>[!IMPORTANT]
>
>Kategorieregeln befinden sich in der Beta-Phase.

**Kategorieregeln** Steuern der Produktreihenfolge auf **Kategorieseiten**. Sie wählen eine oder mehrere Kategorien aus und wenden dann intelligentes Ranking (z. B. am häufigsten angezeigt, Trend) und manuelle Aktionen wie Pin, Boost und Bury an. Sie verwenden keine Suchabfragebedingungen. Informationen zu Einrichtungsschritten, Regeltypen und der Art und Weise, wie die Rangfolge für Kategorie und Suche gilt, finden Sie unter [Regeln erstellen und verwalten](add.md).

## Anforderungen

Eine einfache **Suchregel** kann eine einzelne Bedingung und ein einzelnes Ereignis enthalten, während eine komplexe Regel bis zu zehn Bedingungen mit Triggern von bis zu 25 Ereignissen enthalten kann. **Kategorieregeln** folgen denselben Ereignisbeschränkungen für die manuelle Rangfolge; sie verwenden keine Abfragebedingungen.

Regeln können Folgendes enthalten:

- Bis zu zehn **Bedingungen** (nur Suchregeln)
- Bis zu 25 **Events**

Abfragetext kann Folgendes enthalten:

- Alphanumerische Zeichen (Buchstaben und Zahlen)
- Großbuchstaben oder Kleinbuchstaben. Groß-/Kleinschreibung wird ignoriert.

## Logische Operatoren

Die logischen Operatoren `AND` und `OR` zwei Bedingungen verbinden und unterschiedliche Ergebnisse zurückgeben. Alle logischen Operatoren, die in einer Regel mit mehreren Bedingungen verwendet werden, sind identisch. Es ist nicht möglich, sowohl `AND` als auch `OR` in derselben Regel zu verwenden.

### Operatoren abgleichen

Die Übereinstimmungsoperatoren `All` und `Any` bestimmen den logischen Operator, der zum Verbinden mehrerer Bedingungen in der Regel verwendet wird, und können verwendet werden, um den vorhandenen Operator zu ändern.

- `All` - Verwendet den `AND` logischen Operator zum Verbinden mehrerer Bedingungen. Eine Regel, die den Operator `All` verwendet, kann nur eine `Search query is` aufweisen.
- `Any` - Verwendet den `OR` logischen Operator zum Verbinden mehrerer Bedingungen.

Beim Erstellen einer komplexen Regel kann es hilfreich sein, sie mit Einzügen auszuschreiben, um die Bedingungen, zugehörigen Ereignisse und Produktnamen oder SKUs zu beschreiben, die zum Zurückgeben der gewünschten Ergebnisse erforderlich sind. Erstellen Sie dann die Regel und testen Sie das Ergebnis.

## Standardregel

Sie können eine Standardregel (**Alle Produktlisten) festlegen** die gilt, wenn kein Suchbegriff angegeben wird oder keine andere Suchregel angewendet werden kann. Wenn Sie die Standardregel auf „Am häufigsten gekauft“ setzen, wird für Abfragen standardmäßig dieser Rangfolgetyp verwendet, es sei denn, sie werden durch einen spezifischeren Suchbegriff ersetzt. Für die Standardregel kann kein Suchbegriff festgelegt werden. **Kategorieregeln** sind separat: Sie gelten nur für die von Ihnen ausgewählten Kategorien und ersetzen nicht die standardmäßige Auflistungsregel.

## Rangfolge mit mehreren Regeln

Folgendes gilt für **Suchregeln** und ihre Interaktion für eine bestimmte Suche. **Kategorieregeln** gelten pro Kategorie. Siehe [Erstellen und Verwalten von Regeln](add.md), wie sie mit Such- und Standardregeln übereinstimmen.

Auf einen Suchbegriff wird immer nur eine Suchregel angewendet.
Wenn mehrere Regeln für einen Suchbegriff gefunden werden, werden alle diese Regeln angewendet. Wenn es zu einer Kollision zwischen zwei Regeln kommt - `rule 1`, die SKU1 erhöht, aber `rule 2` dieselbe SKU ausblendet - hat die zuletzt angewendete Regel (`rule 2`) Vorrang.

- Regeln werden nach dem Zeitstempel „Zuletzt geändert“ sortiert. Die zuletzt geänderte Regel wird zuerst und danach die älteren Regeln in der Zeitstempelreihenfolge angewendet.
- Die `query is` Bedingung hat Vorrang vor anderen Bedingungen. Wenn eine neuere Regel eine `query contains` enthält, eine ältere Regel jedoch eine `query is` Bedingung hat, wird die `query is` angewendet.

### Storefront-Anfragen

Wenn eine aktive Regel, die eine `query is` enthält, mit dem Suchbegriff übereinstimmt, wird sie angewendet. Wenn mehrere übereinstimmende Regeln mit einer `query is` Bedingung vorhanden sind, wird die zuletzt aktualisierte aktive Regel angewendet.
Andernfalls wird die zuletzt aktualisierte aktive Regel angewendet.

### Anfragen in der Vorschau anzeigen

In [!DNL Adobe Commerce Optimizer] gestellte Anfragen funktionieren etwas anders. Bei der Vorschau von [!DNL Adobe Commerce Optimizer] werden alle Regeln angewendet, einschließlich der abgelaufenen und geplanten.

- Wenn die Regel, die in der Vorschau angezeigt wird, eine `query is` Bedingung aufweist, wird sie angewendet.
- Wenn die in der Vorschau angezeigte Regel keine `query is` aufweist und eine nachfolgende aktive, übereinstimmende Regel mit einer `query is` Bedingung gefunden wird, wird die `query is` Regel angewendet.
- Wenn die in der Vorschau angezeigte Regel keine `query is` aufweist und keine andere Regel mit einer `query is` Bedingung gefunden wird, wird die in der Vorschau angezeigte Regel angewendet.
