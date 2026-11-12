---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%
---
Die semantische Suche verwendet KI, um zu verstehen, was Käufer meinen, und nicht nur die genauen Wörter, die sie eingeben. Abfragen wie „Kleid für eine Strandhochzeit“ oder „bequeme Schuhe für den ganzen Tag stehen“ können relevante Produkte zurückgeben, auch wenn Ihr Katalog nicht genau diese Phrasen verwendet.

Das Produkterkennungssystem kombiniert Keyword-Matching und semantischen Matching in einem Sucherlebnis. Sie verwalten keine separaten Modi für Keywords und Semantik in der Storefront.

## Konfigurieren der semantischen Suche

Die semantische Suche ist **standardmäßig aktiviert** für geeignete englische Kataloge. Sie können diese auf der Registerkarte **[!UICONTROL Advanced search]** des Arbeitsbereichs [Einstellungen](../settings.md#advanced-search) verwalten, wo Sie die Einstellung bestätigen oder ändern und optional die semantische Verstärkung, den Ähnlichkeitsschwellenwert und die Fuzzy-Suche einstellen können. Informationen [ Öffnen des ](../settings.md#access-the-settings-workspace) finden Sie unter „Einstellungen“.

Sie müssen nach dem Speichern keine separate Konfiguration veröffentlichen oder die Storefront-Einstellungen ändern.

## Vorteile

- **Weniger leere Suchseiten** - Käufer finden Produkte, wenn deren Wortlaut nicht genau mit dem Katalogtext übereinstimmt.
- **Besserer Absichtsabgleich** - Natürliche, beschreibende Abfragen liefern nützliche Ergebnisse.
- **Weniger Synonym-Wartung** - Häufige Wortvarianten (z. B. Couch und Sofa) werden oft ohne manuelle Synonym-Listen behandelt.
- **Keine Storefront oder Entwicklerarbeit** - Die semantische Suche ist standardmäßig aktiviert und erfordert keinen Design-Code, keine Dropdown-Liste oder API-Änderungen.

## Funktionsweise

Wenn die semantische Suche aktiviert ist, verwendet das System vordefinierte Katalogattribute (wie Produktname und Beschreibung), um die Bedeutung der Abfrage neben der herkömmlichen Keyword-Suche zu interpretieren. Attribute in den Einstellungen werden nicht ausgewählt oder priorisiert.

Beispiel:

- Bei der Suche nach „Ledercouch“ können Produkte mit der Bezeichnung „Ledersofa“ zurückgegeben werden.
- „Frühlingskleid“ kann saisonale Kleider auch dann darstellen, wenn „Frühling“ nicht im Produktnamen enthalten ist.
- „Trailrunning-Schuhe“ können Produkte abgleichen, die als Gelände- oder Wanderschuhe bezeichnet werden.

## Was passiert, wenn Sie die semantische Suche aktivieren?

Die semantische Suche funktioniert parallel zu Ihrer vorhandenen Suchkonfiguration. Sie ersetzen keine Keyword-Suche und konfigurieren die Storefront nicht neu.

Wenn die semantische Suche aktiv ist:

- Ihre vorhandenen [Merchandising](../merchandising/rules/overview.md), [Synonyme](../merchandising/synonyms/overview.md), [Facetten](../merchandising/facets/overview.md), Boosts und Filter gelten weiterhin.
- Die semantische Suche bietet ein KI-gestütztes Verständnis der Kundenabsicht, um die Ergebnisrelevanz neben dem Keyword-Matching zu verbessern.
- Vordefinierte Katalogattribute werden automatisch indiziert. Sie wählen keine Attribute aus und veröffentlichen keine separate Konfiguration.

## Nach der Aktivierung validieren

Nachdem die semantische Suche aktiv ist und die Indizierung abgeschlossen ist, empfiehlt Adobe, die Suchleistung zu validieren. Verwenden Sie die Seite [Suchleistung](../manage-results/search-performance.md), um Metriken zu überprüfen und Abfragen zu testen, die für Ihr Unternehmen wichtig sind.

1. Überprüfen Sie Ihre am häufigsten gesuchten Begriffe im Bericht **Eindeutige**&quot;.
1. Testen Sie historische Abfragen mit null Ergebnissen aus dem Bericht **Null Ergebnisse** in der Storefront.
1. Suchergebnisse für dieselben Abfragen vor und nach der Aktivierung vergleichen.
1. Überwachen Sie Konversions- und Interaktionsmetriken für die Suche, einschließlich Clickthrough-Rate, Konversionsrate und Nullergebnisrate.

## Best Practices

- Verwenden Sie klare, beschreibende Produktnamen und Beschreibungen (idealerweise 50-100 Wörter), damit sowohl Keyword- als auch semantische Übereinstimmungen mit starkem Katalogtext arbeiten können.
- Beginnen Sie mit der **[!UICONTROL Enable semantic search]** Standardeinstellung und passen Sie **[!UICONTROL Semantic boost]** oder **[!UICONTROL Similarity threshold]** nur an, wenn die Ergebnisse zu breit oder zu schmal sind.
- Halten Sie markenspezifische oder hochtechnische [Synonyme) bei, ](../merchandising/synonyms/overview.md) die semantische Suche möglicherweise keine Fachbegriffe abdeckt.

## Fehlerbehebung

| Problem | Vorgehensweise |
| --- | --- |
| Keine Änderung an der Storefront direkt nach dem Speichern | Warten Sie, bis die Indizierung abgeschlossen ist. Große Kataloge können länger dauern. |
| Ergebnisse fühlen sich zu breit an | **[!UICONTROL Similarity threshold]** Heben Sie die **[!UICONTROL Semantic boost]** auf der Registerkarte **[!UICONTROL Advanced search]** an oder erhöhen Sie sie. |
| Ergebnisse fühlen sich zu eng an | **[!UICONTROL Similarity threshold]** senken oder **[!UICONTROL Semantic boost]** erhöhen. |
| Semantische Suche ist nicht verfügbar | Bestätigen Sie, dass **[!UICONTROL Language]** auf **Englisch** eingestellt ist. |

## Einschränkungen {#semantic-search-limitations}

- **Katalogsprache:** Die semantische Suche ist nur für **Kataloge in** verfügbar.

## Weitere Hilfe zu diesem Thema

- [Erweiterte Suche](../settings.md#advanced-search)
- [Synonyme](../merchandising/synonyms/overview.md)
- [Suchleistung](../manage-results/search-performance.md)
