---
title: Semantische Suche
description: Aktivieren Sie KI-semantische Suche in [!DNL Adobe Commerce Optimizer] von Einstellungen. Es sind keine Attributeinstellungen oder Änderungen an der Storefront erforderlich.
role: Admin, User
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 015f88e540fe5bf7acc4469d7c91b4f606709809
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Semantische Suche

Die semantische Suche verwendet KI, um zu verstehen, was Käufer meinen, und nicht nur die genauen Wörter, die sie eingeben. Abfragen wie „Kleid für eine Strandhochzeit“ oder „bequeme Schuhe für den ganzen Tag stehen“ können relevante Produkte zurückgeben, auch wenn Ihr Katalog nicht genau diese Phrasen verwendet.

[!DNL Adobe Commerce Optimizer] kombiniert Keyword-Matching und semantischen Matching in einem Sucherlebnis. Sie verwalten keine separaten Modi für Keywords und Semantik in der Storefront. Navigieren Sie in Admin zum Arbeitsbereich [Einstellungen](../settings.md#advanced-search), um die semantische Suche zu verwalten und optional erweiterte Steuerelemente auf der Registerkarte **[!UICONTROL Advanced search]** zu optimieren.

## Vorteile

- **Weniger leere Suchseiten** - Käufer finden Produkte, wenn ihr Wortlaut nicht genau mit dem Katalogtext übereinstimmt.
- **Besserer Absichtsabgleich** - Natürliche, beschreibende Abfragen liefern nützliche Ergebnisse.
- **Weniger Synonym-Wartung** - Häufige Wortvarianten (z. B. Couch und Sofa) werden oft ohne manuelle Synonym-Listen behandelt.
- **Keine Storefront oder Entwicklerarbeit** - Die semantische Suche ist standardmäßig aktiviert und erfordert keinen Design-Code, keine Dropdown-Liste oder API-Änderungen.

## Funktionsweise

Wenn die semantische Suche aktiviert ist, verwendet [!DNL Adobe Commerce Optimizer] vordefinierte Katalogattribute, die vom System ausgewählt wurden (z. B. Produktname und Beschreibung), um die Bedeutung der Abfrage neben der herkömmlichen Keyword-Suche zu interpretieren. Attribute im Admin-Bereich werden nicht ausgewählt oder priorisiert.

Beispiel:

- Bei der Suche nach „Ledercouch“ können Produkte mit der Bezeichnung „Ledersofa“ zurückgegeben werden.
- „Frühlingskleid“ kann saisonale Kleider auch dann darstellen, wenn „Frühling“ nicht im Produktnamen enthalten ist.
- „Trailrunning-Schuhe“ können Produkte abgleichen, die als Gelände- oder Wanderschuhe bezeichnet werden.

## Was passiert, wenn Sie die semantische Suche aktivieren?

Die semantische Suche funktioniert parallel zu Ihrer vorhandenen [!DNL Adobe Commerce Optimizer]. Sie ersetzen keine Keyword-Suche und konfigurieren die Storefront nicht neu.

Wenn die semantische Suche aktiv ist:

- Ihre vorhandenen [Merchandising](../merchandising/rules/overview.md), [Synonyme](../merchandising/synonyms/overview.md), [Facetten](../merchandising/facets/overview.md), Boosts und Filter gelten weiterhin.
- Die semantische Suche bietet ein KI-gestütztes Verständnis der Kundenabsicht, um die Ergebnisrelevanz neben dem Keyword-Matching zu verbessern.
- Vordefinierte Katalogattribute werden automatisch indiziert. Sie wählen keine Attribute aus und veröffentlichen keine separate Konfiguration.

## Verwalten der semantischen Suche in Admin

Die semantische Suche ist **standardmäßig aktiviert** für geeignete englische Kataloge. Wechseln Sie zu **[!UICONTROL Settings]** > **[!UICONTROL Advanced search]** , um die Einstellung zu bestätigen oder zu ändern:

1. Navigieren Sie in der Admin-Liste zu **[!UICONTROL Settings]**.
1. Überprüfen Sie auf der Registerkarte **[!UICONTROL Advanced search]** die **[!UICONTROL Enable semantic search]**.

   Wenn diese Option aktiviert ist, sucht nach Produkten basierend auf ihrer Bedeutung und ihrem Kontext, was relevantere Ergebnisse, weniger leere Suchseiten und eine verbesserte Konvertierung zur Folge haben kann.

1. Klicken Sie auf **[!UICONTROL Save]** , wenn Sie die Umschalt- oder Abstimmsteuerelemente ändern.

   Aktualisierung der Suchergebnisse nach Abschluss der Indizierung. Bei einem mittelgroßen Katalog kann die Indizierung bis zu einer halben Stunde dauern. Bei großen Katalogen mit Millionen von Produkten kann es ein paar Stunden dauern.

>[!NOTE]
>
> Die semantische Suche ist nur für Kataloge **Englisch** verfügbar. Wenn Sie **[!UICONTROL Language]** in einen nicht englischen Katalog ändern, wird **[!UICONTROL Enable semantic search]** automatisch deaktiviert.

Sie müssen nach dem Speichern keine separate Konfiguration veröffentlichen oder die Storefront-Einstellungen ändern.

## Nach der Aktivierung validieren

Nachdem die semantische Suche aktiv ist und die Indizierung abgeschlossen ist, empfiehlt Adobe, die Suchleistung zu validieren. Verwenden Sie die Seite [Suchleistung](../manage-results/search-performance.md), um Metriken zu überprüfen und Abfragen zu testen, die für Ihr Unternehmen wichtig sind.

1. Überprüfen Sie Ihre am häufigsten gesuchten Begriffe im Bericht **Eindeutige**&quot;.
1. Testen Sie historische Abfragen mit null Ergebnissen aus dem Bericht **Null Ergebnisse** in der Storefront.
1. Suchergebnisse für dieselben Abfragen vor und nach der Aktivierung vergleichen.
1. Überwachen Sie Konversions- und Interaktionsmetriken für die Suche, einschließlich Clickthrough-Rate, Konversionsrate und Nullergebnisrate.

## Optionale Optimierung

Auf der Registerkarte **[!UICONTROL Advanced search]** können Sie anpassen, wie sich die Suche verhält, wenn die semantische Suche aktiviert ist:

- **[!UICONTROL Semantic boost]** - Erhöhen oder verringern Sie, wie stark bedeutungsbasierte Übereinstimmungen das Ranking beeinflussen. Nehmen wir beispielsweise an, eine Produktübereinstimmung, die durch die semantische Suche abgerufen wurde, wird am Ende des Ergebnisses angezeigt. Durch das Hinzufügen einer Steigerung steigt die Anzahl im Ergebnis weiter nach oben.
- **[!UICONTROL Similarity threshold]** - Legt fest, wie nahe eine Übereinstimmung sein muss, bevor ein Produkt angezeigt wird. Niedrigere Werte zeigen mehr Ergebnisse, höhere Werte zeigen weniger, engere Übereinstimmungen.
- **[!UICONTROL Fuzzy search]** und **[!UICONTROL Fuzzy search similarity threshold]** - Helfen Sie Käufern bei der Suche nach Produkten, wenn Abfragen kleine Rechtschreibunterschiede enthalten.

Unter [Erweiterte Suche](../settings.md#advanced-search) finden Sie Steuerungsbeschreibungen und schrittweise Anleitungen.

## Best Practices

- Verwenden Sie klare, beschreibende Produktnamen und Beschreibungen (idealerweise 50-100 Wörter), damit sowohl Keyword- als auch semantische Übereinstimmungen mit starkem Katalogtext arbeiten können.
- Beginnen Sie mit der **[!UICONTROL Enable semantic search]** Standardeinstellung und passen Sie **[!UICONTROL Semantic boost]** oder **[!UICONTROL Similarity threshold]** nur an, wenn die Ergebnisse zu breit oder zu schmal sind.
- Halten Sie markenspezifische oder hochtechnische [Synonyme) bei, &#x200B;](../merchandising/synonyms/overview.md) die semantische Suche möglicherweise keine Fachbegriffe abdeckt.

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
