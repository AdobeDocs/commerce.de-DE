---
title: Merchandising-Regeln
description: '[!DNL Adobe Commerce Optimizer] Merchandising-Regeln kombinieren Logik mit Aktionen, um das Einkaufserlebnis zu gestalten.'
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 356b10704c9e7c7329d3e9c0e10baa15d5142ec0
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---

# Merchandising-Regeln

Merchandising-Regeln beziehen sich auf einen Satz von Regeln, die Logik mit Aktionen kombinieren, um das Sucherlebnis eines Käufers in Ihrem Geschäft zu gestalten. Sie können Merchandising-Regeln verwenden, um Produkte zu optimieren, zu vergraben, anzuheften oder auszublenden, um Suchergebnisse in Echtzeit zu kalibrieren und so Ihre Geschäftsziele zu unterstützen.

Jede Regel besteht aus drei Hauptkomponenten:

- Bedingungen : Die Bedingungen, unter denen eine Aktion Trigger wird.
- Ereignisse : Die Aktionen, die ausgeführt werden, wenn die Bedingungen erfüllt sind.
- Details : Der Name der Regel und optionaler Zeitrahmen und Beschreibung.

Sie können mehrere Bedingungen und Aktionen kombinieren und eine Regel so planen, dass sie für einen Zeitraum aktiv ist. Sie können auch eine Standardregel festlegen, die auch dann angewendet wird, wenn kein Suchbegriff festgelegt ist.

## Anforderungen

Eine einfache Suchregel kann eine einzelne Bedingung und ein einzelnes Ereignis enthalten, während eine komplexe Regel bis zu zehn Bedingungen mit Triggern von bis zu 25 Ereignissen enthalten kann.
Regeln können Folgendes enthalten:

- Bis zu zehn Bedingungen
- Bis zu 25 Ereignisse

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

Sie können eine Standardregel festlegen, die angewendet wird, wenn kein Suchbegriff angegeben wird oder keine andere Suchregel angewendet werden kann. Wenn Sie die Standardregel auf „Am häufigsten gekauft“ festlegen, wird für alle Abfragen standardmäßig dieser Rangfolgetyp verwendet, es sei denn, sie werden durch einen spezifischeren Suchbegriff überschrieben. Für die Standardregel kann kein Suchbegriff festgelegt werden.

## Rangfolge mit mehreren Regeln

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
