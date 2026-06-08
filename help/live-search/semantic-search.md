---
title: Semantische Suche
description: Aktivieren Sie die KI-Semantische Suche nach [!DNL Live Search] aus den Einstellungen. Es sind keine Attributeinstellungen oder Änderungen an der Storefront erforderlich.
role: Admin
recommendations: noCatalog
source-git-commit: 015f88e540fe5bf7acc4469d7c91b4f606709809
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 0%

---

# Semantische Suche

Die semantische Suche verwendet KI, um zu verstehen, was Käufer meinen, und nicht nur die genauen Wörter, die sie eingeben. Abfragen wie „Kleid für eine Strandhochzeit“ oder „bequeme Schuhe für den ganzen Tag stehen“ können relevante Produkte zurückgeben, auch wenn Ihr Katalog nicht genau diese Phrasen verwendet.

[!DNL Live Search] kombiniert Keyword-Matching und semantischen Matching in einem Sucherlebnis. Sie verwalten keine separaten Modi für Keywords und Semantik in der Storefront. [!DNL Live Search] bietet keine erweiterten semantischen Steuerelemente (z. B. Verstärkungs- oder Ähnlichkeitsregler) in Admin. Sie können die semantische Suche aktivieren oder deaktivieren.

## Aktivierung nach Bereitstellung

Die semantische Suche wird über den **Einstellungen** im [!DNL Live Search] Admin verwaltet (**Marketing** > *SEO &amp; Search* > **[!DNL Live Search]**). [!DNL Adobe Commerce as a Cloud Service] verwendet dieselbe [!DNL Live Search] wie PaaS-Händler.

## Vorteile

- **Weniger Null-Ergebnis-Suchen** - Käufer finden Produkte, wenn ihr Wortlaut nicht genau mit dem Katalogtext übereinstimmt.
- **Relevantere Ergebnisse** - Natürliche, beschreibende Abfragen geben nützliche Übereinstimmungen basierend auf Bedeutung und Kontext zurück.
- **Weniger Synonym-Wartung** - Häufige Wortvarianten (z. B. Couch und Sofa) werden oft ohne manuelle Synonym-Listen behandelt.
- **Keine Storefront oder Entwicklerarbeit** - Semantische Suche erfordert keine Design-Code-, Widget- oder API-Änderungen. PaaS-Händler aktivieren es in den Einstellungen; [!DNL Adobe Commerce as a Cloud Service] Kunden erhalten es standardmäßig aktiviert.

## Funktionsweise

Wenn die semantische Suche aktiviert ist, verwendet [!DNL Live Search] vordefinierte Katalogattribute, die vom System ausgewählt wurden (z. B. Produktname und Beschreibung), um die Bedeutung der Abfrage neben der herkömmlichen Keyword-Suche zu interpretieren. Attribute im Admin-Bereich werden nicht ausgewählt oder priorisiert.

Beispiel:

- Bei der Suche nach „Ledercouch“ können Produkte mit der Bezeichnung „Ledersofa“ zurückgegeben werden.
- „Frühlingskleid“ kann saisonale Kleider auch dann darstellen, wenn „Frühling“ nicht im Produktnamen enthalten ist.
- „Trailrunning-Schuhe“ können Produkte abgleichen, die als Gelände- oder Wanderschuhe bezeichnet werden.

## Was passiert, wenn Sie die semantische Suche aktivieren?

Die semantische Suche funktioniert parallel zu Ihrer vorhandenen [!DNL Live Search]. Sie ersetzen keine Keyword-Suche und konfigurieren die Storefront nicht neu.

Wenn die semantische Suche aktiv ist:

- Die vorhandenen [Suchregeln](rules.md), [Synonyme](synonyms.md), [Facetten](facets.md), Boosts und [Kategorie Merchandising](category-merch.md) Einstellungen gelten weiterhin.
- Die semantische Suche bietet ein KI-gestütztes Verständnis der Kundenabsicht, um die Ergebnisrelevanz neben dem Keyword-Matching zu verbessern.
- Vordefinierte Katalogattribute werden automatisch indiziert. Sie wählen keine Attribute aus und veröffentlichen keine separate Konfiguration.

## Verwalten der semantischen Suche in Admin

Wechseln Sie zum Arbeitsbereich [Einstellungen](settings.md#semantic-search), um den **[!UICONTROL Semantic search]**-Umschalter anzuzeigen oder zu ändern.

>[!NOTE]
>
> Die semantische Suche ist nur für Kataloge **Englisch** verfügbar. Wenn Sie **Language** im Arbeitsbereich **Einstellungen“ in einen nicht englischsprachigen Katalog**, wird **[!UICONTROL Semantic search]** automatisch deaktiviert.

### Für PaaS Händler

Händler, die Adobe Commerce in der Cloud und lokal nutzen, müssen die semantische Suche manuell aktivieren:

1. Gehen Sie im Admin zu **Marketing** > *SEO &amp; Search* > **[!DNL Live Search]**.
1. Aktivieren Sie im **Einstellungen** die Option **[!UICONTROL Semantic search]**.

   Wenn diese Option aktiviert ist, ordnet die Suche Produkte basierend auf ihrer Bedeutung und ihrem Kontext zu, was relevantere Ergebnisse, weniger Suchvorgänge ohne Ergebnis und eine verbesserte Konvertierung zur Folge haben kann.

1. Klicken Sie auf **[!UICONTROL Save]**.

   Aktualisierung der Suchergebnisse nach Abschluss der Indizierung. Bei einem mittelgroßen Katalog kann die Indizierung bis zu einer halben Stunde dauern. Bei großen Katalogen mit Millionen von Produkten kann es ein paar Stunden dauern.

### Für ACS-Kunden

[!DNL Adobe Commerce as a Cloud Service] Kunden verwenden denselben Arbeitsbereich **Einstellungen** in der [!DNL Live Search] Admin. Die semantische Suche ist **standardmäßig aktiviert** für geeignete englische Kataloge. Bestätigen Sie, dass **[!UICONTROL Semantic search]** aktiviert ist, oder deaktivieren Sie sie, wenn Sie keine semantischen Übereinstimmungen in der Storefront wünschen.

Nach dem Speichern einer Änderung ist kein separater Veröffentlichungsschritt und keine Storefront-Konfiguration erforderlich.

## Nach der Aktivierung validieren

Nachdem die semantische Suche aktiv ist und die Indizierung abgeschlossen ist, empfiehlt Adobe, die Suchleistung zu validieren. Verwenden Sie den [Performance](performance.md)-Arbeitsbereich, um Metriken zu überprüfen und Abfragen zu testen, die für Ihr Unternehmen wichtig sind. Dies gilt unabhängig davon, ob die semantische Suche standardmäßig aktiviert ist oder manuell aktiviert wurde.

1. Überprüfen Sie Ihre am häufigsten gesuchten Begriffe im Bericht **Eindeutige**&quot;.
1. Testen Sie historische Abfragen mit null Ergebnissen aus dem Bericht **Null Ergebnisse** in der Storefront.
1. Suchergebnisse für dieselben Abfragen vor und nach der Aktivierung vergleichen.
1. Überwachen Sie Konversions- und Interaktionsmetriken für die Suche, einschließlich Clickthrough-Rate, Konversionsrate und Nullergebnisrate.

## Best Practices

- Verwenden Sie klare, beschreibende Produktnamen und Beschreibungen (idealerweise 50-100 Wörter), damit sowohl Keyword- als auch semantische Übereinstimmungen mit starkem Katalogtext arbeiten können.
- Halten Sie markenspezifische oder hochtechnische [Synonyme) bei, &#x200B;](synonyms.md) die semantische Suche möglicherweise keine Fachbegriffe abdeckt.

## Fehlerbehebung

| Problem | Vorgehensweise |
| --- | --- |
| Keine Änderung an der Storefront direkt nach dem Speichern | Warten Sie, bis die Indizierung abgeschlossen ist. Große Kataloge können länger dauern. |
| Die semantische Suche ist nicht verfügbar oder wird automatisch deaktiviert | Bestätigen Sie **dass** Arbeitsbereich **Einstellungen** auf **Englisch** eingestellt ist. |
| Ergebnisse vermissen noch immer allgemeine Begriffe | Fügen Sie [Synonyme](synonyms.md) für Marken- oder Branchenbegriffe hinzu, die die semantische Suche möglicherweise nicht auflöst. |

## Einschränkungen {#semantic-search-limitations}

- **Katalogsprache:** Die semantische Suche ist nur für **Kataloge in** verfügbar.
- **Admin-Steuerelemente:** [!DNL Live Search] stellt nur ein Steuerelement zum Aktivieren/Deaktivieren bereit. Semantische Verstärkungen, Ähnlichkeitsschwellen oder unscharfe Suchen können nicht im Arbeitsbereich **Einstellungen** angepasst werden.

## Weitere Hilfe zu diesem Thema

- [Einstellungen](settings.md#semantic-search)
- [Synonyme](synonyms.md)
- [Leistung](performance.md)
