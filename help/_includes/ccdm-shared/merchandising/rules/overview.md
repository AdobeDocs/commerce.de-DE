---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%
---
Merchandising-Regeln kombinieren Logik mit Aktionen, um die Darstellung von Produkten **Suchergebnissen** in **Standardproduktlisten** durch die **Standardsuchregel** und auf **Kategorieseiten**. Sie können Produkte ankurbeln, vergraben, anheften oder ausblenden und **intelligentes Ranking** anwenden, sodass die Listeneinträge Ihre Geschäftsziele widerspiegeln.

Jede **Suchregel** besteht aus drei Hauptkomponenten:

- **Bedingungen** - Abfragebasierte Anforderungen, bei denen eine Aktion durch einen Trigger ausgelöst wird, wenn die Suche des Käufers übereinstimmt.
- **Ereignisse** - Aktionen, die stattfinden, wenn die Bedingungen erfüllt sind (manuelle Rangfolge und zugehörige Ereignisse).
- **Details** - Der Name der Regel sowie optionaler Zeitrahmen und Beschreibung.

**Kategorieregeln** Verwenden Sie **Kategorieauswahl** anstelle von Suchabfragebedingungen; intelligentes Ranking und manuelles Ranking funktionieren auf die gleiche Weise wie für die Suche, wobei die Unterschiede in „Regeln erstellen [ verwalten“ ](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add).

Sie können mehrere Bedingungen und Aktionen für Suchregeln kombinieren und jede Regel so planen, dass sie für einen Zeitraum aktiv ist. Sie können auch eine **Standard-Suchregel“ festlegen** die gilt, wenn keine spezifischere Such- oder Kategorieregel gilt.

## Kategorieregeln {#category-rules}

**Kategorieregeln** Steuern der Produktreihenfolge auf **Kategorieseiten**. Sie wählen eine oder mehrere Kategorien aus und wenden dann intelligentes Ranking (z. B. am häufigsten angezeigt, Trend) und manuelle Aktionen wie Pin, Boost und Bury an. Sie verwenden keine Suchabfragebedingungen. Informationen zu Einrichtungsschritten, Regeltypen und der Art und Weise, wie die Rangfolge für Kategorie und Suche gilt, finden Sie unter [Regeln erstellen und verwalten](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add).

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

Sie können eine **Standard-Suchregel** festlegen, die angewendet wird, wenn kein Suchbegriff angegeben wird oder keine andere Suchregel angewendet werden kann. Wenn Sie die Standardregel auf „Am häufigsten gekauft“ setzen, wird für Abfragen standardmäßig dieser Rangfolgetyp verwendet, es sei denn, sie werden durch einen spezifischeren Suchbegriff ersetzt. Für die Standardregel kann kein Suchbegriff festgelegt werden. **Kategorieregeln** sind separat: Sie gelten nur für die von Ihnen ausgewählten Kategorien und ersetzen nicht die standardmäßige Auflistungsregel.

## Rangfolge mit mehreren Regeln

Folgendes gilt für **Suchregeln** und ihre Interaktion für eine bestimmte Suche. **Kategorieregeln** gelten pro Kategorie. Siehe [Erstellen und Verwalten von Regeln](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/rules/add), wie sie mit Such- und Standardregeln übereinstimmen.

Auf einen Suchbegriff wird immer nur eine Suchregel angewendet.
Wenn mehrere Regeln für einen Suchbegriff gefunden werden, werden alle diese Regeln angewendet. Wenn es zu einer Kollision zwischen zwei Regeln kommt - `rule 1`, die SKU1 erhöht, aber `rule 2` dieselbe SKU ausblendet - hat die zuletzt angewendete Regel (`rule 2`) Vorrang.

- Regeln werden nach dem Zeitstempel „Zuletzt geändert“ sortiert. Die zuletzt geänderte Regel wird zuerst und danach die älteren Regeln in der Zeitstempelreihenfolge angewendet.
- Die `query is` Bedingung hat Vorrang vor anderen Bedingungen. Wenn eine neuere Regel eine `query contains` enthält, eine ältere Regel jedoch eine `query is` Bedingung hat, wird die `query is` angewendet.

### Storefront-Anfragen

Wenn eine aktive Regel, die eine `query is` enthält, mit dem Suchbegriff übereinstimmt, wird sie angewendet. Wenn mehrere übereinstimmende Regeln mit einer `query is` Bedingung vorhanden sind, wird die zuletzt aktualisierte aktive Regel angewendet.
Andernfalls wird die zuletzt aktualisierte aktive Regel angewendet.

### Anfragen in der Vorschau anzeigen

In der Vorschau ausgeführte Anfragen funktionieren etwas anders. Bei der Vorschau werden alle Regeln angewendet, einschließlich der abgelaufenen und geplanten.

- Wenn die Regel, die in der Vorschau angezeigt wird, eine `query is` Bedingung aufweist, wird sie angewendet.
- Wenn die in der Vorschau angezeigte Regel keine `query is` aufweist und eine nachfolgende aktive, übereinstimmende Regel mit einer `query is` Bedingung gefunden wird, wird die `query is` Regel angewendet.
- Wenn die in der Vorschau angezeigte Regel keine `query is` aufweist und keine andere Regel mit einer `query is` Bedingung gefunden wird, wird die in der Vorschau angezeigte Regel angewendet.
