---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%
---
>[!IMPORTANT]
>
>Die folgende Funktion befindet sich in der [privaten Betaversion](https://experienceleague.adobe.com/en/docs/commerce-operations/release/beta).

Merchandising-Services mit dem zusammensetzbaren Katalogdatenmodell (CCDM) ordnen die Ergebnisse so ein, dass Käufer die relevantesten Produkte zuerst sehen. Der Service steigert Produkte, deren Katalogtext **eng** der Anfrage des Käufers übereinstimmt, bevorzugt dann Übereinstimmungen, bei denen Begriffe gemeinsam vorkommen, und schließlich auch umfassendere Übereinstimmungen.

## Wie Übereinstimmungen priorisiert werden

Die Relevanz beruht auf drei Schichten übereinstimmender Stärke (zusätzlich zu den anderen unten beschriebenen Scoring-Faktoren):

1. **Exakte und Beinahe-Phrasenübereinstimmung** - Die vollständige Suchphrase entspricht Katalogtext oder einer Beinahe-Übereinstimmung nach der Normalisierung wie Stemming (z. B. werden Singular- und Plural-Formulare zu derselben Wurzel aufgelöst). Diese Übereinstimmungen erhalten den höchsten Relevanzschub.

1. **Alle Wörter im selben Feld** - Jedes Abfragewort wird in einem durchsuchbaren Attribut angezeigt (z. B. `red` und `pants` im Produkt **name**). Diese Schicht erhält die nächsthöhere Verstärkung.

1. **Wörter über verschiedene Felder hinweg** - Abfragebegriffe werden in verschiedenen durchsuchbaren Attributen angezeigt (z. B. `red` in **color** und `pants` in **name**). Diese Übereinstimmungsschicht ist die breiteste und erhält die niedrigste Relevanzsteigerung. Es kann auch mit Teilabfragen übereinstimmen, die von der automatischen Vervollständigung verwendet werden, z. B. wenn ein Käufer `red pan` eingibt, bevor er `pants` beendet. Für deutsche Kataloge siehe [Dekompounding](#decompounding-german).

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

Legen Sie **Sprache** auf **Deutsch** auf der Registerkarte [Sprache](../settings.md#language) in [Einstellungen](../settings.md) fest, sodass Zerlegungsregeln gelten. Validieren Sie hochwertige deutsche Abfragen in einer Staging-Storefront, bevor Sie Änderungen in der Produktion aktivieren.

Die Dekomprimierung ist regelbasiert und kann auf dieser Ebene Randfälle hinzufügen. Fehlt ein Unterwort im Wörterbuch, ist die Tokenisierung unvollständig und gibt breitere Übereinstimmungen als erwartet zurück, z. B. **gas** fehlt im **gaszähler** nur **zahl** oder **stat** fehlt im **thermostat**. Die Stemmer können auch unerwartete Wurzeln produzieren (z. B **„schrauber** stemming to **schraub** oder **schelle** to **schell**). Adobe aktualisiert das Wörterbuch und die Abstammungsüberschreibungen für bekannte Fälle, wenn Probleme erkannt werden.

## Was wirkt sich noch auf das Ranking aus?

Die Übereinstimmung der Phrasen allein bestimmt nicht die Relevanz. Mehrere Signale interagieren:

- Verstärken durch **exakte/** Phrasenübereinstimmung
- Verstärken, wenn **alle Abfragebegriffe** im **Feld** werden
- **Intelligentes Ranking** (wenn aktiviert), das textliche Relevanz mit Verhaltenssignalen verbindet - siehe [Funktionsweise der intelligenten Rangfolgenbewertung](../merchandising/rules/add.md#how-intelligent-ranking-scoring-works-search)
- **[Suchgewichtung](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results)** für jedes Attribut und andere textliche Relevanzfaktoren (z. B. wie oft Begriffe im Namen oder in der Beschreibungslänge vorkommen). Konfigurieren Sie *Einstellungen*, welche Attribute an der Keyword-Suche beteiligt sind, und ihre relativen **[Keyword-Suchgewichte](../settings.md)**.
- **[Merchandising-Regeln](../merchandising/rules/overview.md)** z. B. Pin, Boost und Bury

Da Signale interagieren, rangiert eine breite Übereinstimmung manchmal vor einer engeren Phrasenübereinstimmung, wenn **Suchgewichte** oder die Termfrequenz eine schwächere Phrasenübereinstimmung überwiegen.

**Beispiel:** Wenn **rote Hose** in **Beschreibung** mit **search weight = 1**, **red** und **pants** getrennt in **name** und **color** mit **search weight = 10** angezeigt wird, hat die Teilungsübereinstimmung mehr Gewicht als die Phrasenübereinstimmung.

Manuelle **Pin**- und **Bury**-Regeln bleiben stark; **Boost**-Regeln erfordern möglicherweise eine Abstimmung, um neue Phrasen und Verstärkungen im selben Feld zu überwinden. Validieren wichtiger Abfragen nach dem Ändern von Gewichtungen oder Regeln.

### Suchgewichtung 1 und kombinierte Indizierung

Attribute mit **minimaler Suchgewichtung** (Gewichtung **1**) und ohne spezielle Übereinstimmungsmodi werden zu einem einzigen internen Feld (`defaultSearchField`) kombiniert, um den Zuordnungs-Overhead zu reduzieren. Betrachten Sie dies als eine durchsuchbare Oberfläche für **Gleiches Feld**-Abgleich: Token, die nur in diesen kombinierten Feldern mit geringer Gewichtung landen, werden zusammen und nicht als separate Felder pro Attribut ausgewertet. Adobe kann diese Optimierung im Laufe der Zeit verfeinern, wenn sich der Abgleich weiterentwickelt.

## Verwandte Themen

- [Einstellungen](../settings.md)
- [Suchleistung](search-performance.md)
- [Übersicht über Merchandising-Regeln](../merchandising/rules/overview.md)
- [Suchregeln hinzufügen](../merchandising/rules/add.md)
- [Übersicht über Synonyme](../merchandising/synonyms/overview.md)
