---
title: Abgleich und Rangfolge suchen
description: Erfahren Sie [!DNL Live Search]  wie exakte und Beinahe-Übereinstimmungen, Übereinstimmungen mit gleichen Feldern und feldübergreifende Übereinstimmungen priorisiert und wie das Ranking mit Suchgewichten, intelligenten Rangfolgen und Merchandising-Regeln interagiert.
role: Admin, Developer
recommendations: noCatalog
hide: true
source-git-commit: f7ea996f3adcd3beb2a9c064ce57d251f49ae5b3
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%

---

# Abgleich und Rangfolge suchen

>[!IMPORTANT]
>
>Die folgende Funktion befindet sich in der [privaten Betaversion](https://experienceleague.adobe.com/de/docs/commerce-operations/release/beta).

[!DNL Live Search] werden die Ergebnisse so sortiert, dass Käufer die relevantesten Produkte zuerst sehen. Der Service steigert am meisten die Produkte, deren Katalogtext **eng mit dem** Kunden übereinstimmt), bevorzugt dann Übereinstimmungen, bei denen Abfragebegriffe sinnvoll zusammenpassen, und schließlich breitere Übereinstimmungen (einschließlich Verhaltensweisen, die eine automatische Vervollständigung unterstützen).

## Wie Übereinstimmungen priorisiert werden

Auf hoher Ebene verwendet die Relevanz drei Schichten der Übereinstimmungsstärke (zusätzlich zu den anderen unten beschriebenen Scoring-Faktoren):

1. **Exakte und Beinahe-Phrasenübereinstimmung** - Die vollständige Suchphrase entspricht Katalogtext oder einer Beinahe-Übereinstimmung nach der Normalisierung wie Stemming (z. B. werden Singular- und Plural-Formulare zu derselben Wurzel aufgelöst). Diese Übereinstimmungen erhalten den höchsten Relevanzschub.

1. **Alle Wörter im selben Feld** - Jedes Wort in der Abfrage wird in einem durchsuchbaren Attribut angezeigt (z. B. sowohl `red` als auch `pants` im Produkt **name**). Diese Schicht erhält die nächsthöhere Verstärkung.

1. **Wörter über verschiedene Felder hinweg** - Abfragebegriffe werden in verschiedenen durchsuchbaren Attributen angezeigt (z. B. `red` in **color** und `pants` in **name**). Dies ist die breiteste Übereinstimmungsschicht und erhält die niedrigste Relevanzsteigerung. Es kann auch mit Teilabfragen übereinstimmen, die von der automatischen Vervollständigung verwendet werden, z. B. wenn ein Käufer `red pan` eingibt, bevor er `pants` beendet. Für deutsche Kataloge siehe [Dekompounding](#decompounding-german).

### Beispiel

Für eine Abfrage wie `red pants`:

- Produkte mit der exakten Phrase **rote Hose** (oder einer nahen Variante) rangieren **(**.
- Als Nächstes folgen Produkte **bei denen** und **Hose** im **selben Feld** erscheinen (z. B **name**).
- Produkte, bei denen die Begriffe in **verschiedenen Feldern** enthalten sind (z. B **&quot;**&quot; und **name**).

### Dekomprimierung (Deutsch) {#decompounding-german}

Deutsche Kataloge verwenden viele zusammengesetzte Wörter. Zum Beispiel können **spülbecken** und **spül becken** in Token wie **spul** und **beck** (nach dem Stemmen) zerfallen, sodass ein Käufer, der **spul becken** sucht, weiterhin **spülbecken** finden kann. Auf dieser Ebene müssen dekomprimierte Unterwörter aus einem zusammengesetzten Begriff im selben Feld erscheinen. Andere Abfragebegriffe können in verschiedenen Feldern übereinstimmen.

Diese **AND**-Anforderung filtert irrelevante Übereinstimmungen, bei denen nur ein Unterwort vorhanden ist. Beispielsweise gibt eine Suche nach **Brauseschlauch** nicht mehr **Schlauchstück** zurück, wenn nur ein Teil der Verbindung übereinstimmt. Eine Suche nach **flush** becken **kann immer noch übereinstimmen** da das längere Wort alle erwarteten Token enthält.

>[!NOTE]
>
>Exakter und nahezu übereinstimmender Phrasen und Übereinstimmung mit gleichen Feldern verwenden die oben beschriebenen Regeln, ohne die Komposition zu unterbrechen.

#### Beispiel

Für einen Suchbegriff wie `Brauseschlauch chrom`:

- **Exakte und Beinahe-Phrasenübereinstimmung** - Sucht nach der vollständigen Phrase **brauseschlauch chrom** wie eingegeben, ohne zu zerlegen (Stemming gilt weiterhin).
- **Alle Wörter im selben Feld** — Sucht nach **brauseschlauch** und **chrom** im **same** durchsuchbaren Attribut, noch ohne Zerlegung (z. B. beide in **name**).
- **Wörter über verschiedene Felder hinweg** — Zerlegt **Brauseschlauch** in **brause** und **schlauch**. Diese Token müssen im **Feld angezeigt werden** nicht unbedingt als angrenzende Phrase). **chrom** kann in einem Feld **anders** übereinstimmen (z. B. **Brause** und **Schlauch** in **name**, **chrom** in **color**).

Legen Sie **Sprache** im Arbeitsbereich [Einstellungen](settings.md#language) auf **Deutsch** fest, sodass Zerlegungsregeln angewendet werden. Validieren Sie hochwertige deutsche Abfragen in einer Staging-Storefront, bevor Sie Änderungen in der Produktion aktivieren.

Die Dekomprimierung ist regelbasiert und kann auf dieser Ebene Randfälle hinzufügen. Wenn ein Unterwort im Wörterbuch fehlt, kann die Tokenisierung unvollständig sein und breitere Übereinstimmungen zurückgeben, als erwartet - z. B. kann **gas** fehlt im **gaszähler** nur **zahl** oder **stat** fehlt im **thermostat**. Die Stemmer können auch unerwartete Wurzeln produzieren (z. B **„schrauber** stemming to **schraub** oder **schelle** to **schell**). Adobe aktualisiert das Wörterbuch und die Abstammungsüberschreibungen für bekannte Fälle, wenn Probleme erkannt werden.

## Was wirkt sich noch auf das Ranking aus?

Die Relevanz wird nicht allein durch die Übereinstimmung der Phrasen bestimmt. Mehrere Signale interagieren:

- Verstärken durch **exakte/** Phrasenübereinstimmung
- Verstärken, wenn **alle Abfragebegriffe** im **Feld** werden
- **Intelligentes Ranking** (wenn aktiviert), das textliche Relevanz mit Verhaltenssignalen verbindet - siehe [Funktionsweise der intelligenten Rangfolgenbewertung](rules-add.md#how-intelligent-ranking-scoring-works)
- **[Suchgewichtung](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/catalog/search/search-results)** für jedes Attribut und andere textliche Relevanzfaktoren (z. B. wie oft Begriffe vorkommen und Name oder Länge der Beschreibung). Konfigurieren Sie in der [!DNL Adobe Commerce] Admin **In der Suche verwenden** und **Suchgewichtung** für Produktattribute.
- **[Merchandising-Regeln suchen](rules.md)** z. B. Pin, Boost und Bury

Da diese Signale interagieren, kann ein Produkt, das nur auf der breitesten Ebene übereinstimmt, manchmal einen engeren Übereinstimmungsgrad erreichen, z. B. wenn **Suchgewichte** oder die Häufigkeit von Begriffen in einem Feld mit hoher Gewichtung eine schwächere Übereinstimmung der Phrasen an anderer Stelle überwiegen.

**Beispiel:** Wenn **rote Hose** als Phrase in **Beschreibung** mit **Suchgewicht = 1** angezeigt wird, **rot** und **pants** getrennt in **name** und **color** mit **Suchgewicht = 10**, übertrifft die Phrase in **description** möglicherweise nicht die Aufspaltungsübereinstimmung, je nach Gesamtbewertung.

Manuelle **Pin**- und **Bury**-Regeln bleiben stark; **Boost**-Regeln erfordern möglicherweise eine Abstimmung, um neue Phrasen und Verstärkungen im selben Feld zu überwinden. Validieren wichtiger Abfragen nach dem Ändern von Gewichtungen oder Regeln.

### Suchgewichtung 1 und kombinierte Indizierung

Attribute, die mit der **Mindestsuchgewichtung** (Gewichtung **1**) und **Nicht** für spezielle Übereinstimmungsmodi konfiguriert wurden (z. B. Enthält oder Beginnt mit), können im Suchindex zu einem einzigen internen Feld (`defaultSearchField`) kombiniert werden, um den Mehraufwand für die Feldzuordnung zu reduzieren. Betrachten Sie dies als eine durchsuchbare Oberfläche für **Gleiches Feld**-Abgleich: Token, die nur in diesen kombinierten Feldern mit geringer Gewichtung landen, werden zusammen und nicht als separate Felder pro Attribut ausgewertet. Adobe kann diese Optimierung im Laufe der Zeit verfeinern, wenn sich der Abgleich weiterentwickelt.

## Verwandte Themen

- [Indizierung](indexing.md)
- [Best Practices](best-practice.md)
- [Suchregeln hinzufügen](rules-add.md)
- [Synonyme](synonyms.md)
