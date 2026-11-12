---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%
---
Ein- und Zwei-Wege-Synonyme erweitern die Definition von Keywords. Einige sind mit dem Keyword austauschbar, während andere eine Teilmenge des Keywords darstellen.

## wechselseitig

Zwei-Wege-Synonyme haben dieselbe Bedeutung und geben dieselben Suchergebnisse zurück. Im folgenden Beispiel ist das erste fett gedruckte Wort das Schlüsselwort, das im Katalog verwendet wird, gefolgt von Wörtern, die dieselbe Bedeutung wie das ursprüngliche Schlüsselwort haben. Sie können ein einfaches Paar von bidirektionalen Synonymen oder eine Kette mehrerer bidirektionaler Synonyme für dasselbe Keyword erstellen.

**Jacke** ![Zwei-Wege-](/help/assets/ccdm-shared/synonyms/two-way.png)
**Hose** ![Zweiwegselektor](/help/assets/ccdm-shared/synonyms/two-way.png) Hose ![Zweiwegselektor](/help/assets/ccdm-shared/synonyms/two-way.png)

## unidirektional

Ein Einwegsynonym ist eine Teilmenge eines Keywords, jedoch mit einer spezifischeren Bedeutung. Zum Beispiel sind Capris und Shorts Hosen, aber nicht alle Hosen sind Capris oder Shorts. Die Suche nach Hosen umfasst Capris und Shorts. Die Suche nach Shorts gibt jedoch keine Capris zurück.

**Sweatshirt** ![Einwegselektor](/help/assets/ccdm-shared/synonyms/one-way.png) Kapuzenpullover
**Hose** ![Einwegselektor](/help/assets/ccdm-shared/synonyms/one-way.png) capris ![Einwegselektor](/help/assets/ccdm-shared/synonyms/one-way.png) Wadenlängenhose ![Einwegselektor](/help/assets/ccdm-shared/synonyms/one-way.png) Peddlers

## Synonymverhalten für mehrere Wörter

Bei Synonymen mit mehreren Wörtern betrachtet das System das Synonym als eine Phrase. Wenn Sie beispielsweise ein Zwei-Wege-Synonym **Esszimmertisch** ![Zwei-Wege-Selektor](/help/assets/ccdm-shared/synonyms/two-way.png) **&#x200B;**&#x200B;Küchentisch![Zwei-Wege-Selektor](/help/assets/ccdm-shared/synonyms/two-way.png)**Esstisch** erstellen, durchsucht das System alle Felder, die auf Durchsuchbar eingestellt sind, nach **Esszimmertisch** oder **Küchentisch** oder **Esstisch**.

Wenn kein Synonym erstellt wird und ein Käufer nach **Küchentabelle** sucht, sucht das System überall in den durchsuchbaren Feldern nach den Begriffen, auch über verschiedene Felder hinweg, z. B. **table** im Namensfeld und **küche** im Meta-Schlüsselwort.

Nachdem Sie ein Synonym erstellt haben, ändert sich das Suchverhalten, sodass Sie nach der exakten Phrase **Küchentabelle)**. Dadurch kann die Anzahl der Ergebnisse reduziert werden, da nur Produkte mit der exakten Phrase angezeigt werden.

Wenn Sie möchten, dass nach den Begriffen separat gesucht wird, können Sie [ein Support-Ticket erstellen](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).
