---
title: Typen von Synonymen
description: Ein- und Zwei-Wege [!DNL Live Search] Synonyme erweitern die Definition von Keywords.
exl-id: f5522428-c7cc-4627-a09b-d9148918c127
source-git-commit: 81bde302463a70e41318b494565694929703dff9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Typen von Synonymen

Ein- und Zwei-Wege-Synonyme erweitern die Definition von Keywords. Einige sind mit dem Keyword austauschbar, während andere eine Teilmenge des Keywords darstellen.

## wechselseitig

Zwei-Wege-Synonyme haben dieselbe Bedeutung und geben dieselben Suchergebnisse zurück. Im folgenden Beispiel ist das erste fett gedruckte Wort das Schlüsselwort, das im Katalog verwendet wird, gefolgt von Wörtern, die dieselbe Bedeutung wie das ursprüngliche Schlüsselwort haben. Sie können ein einfaches Paar von bidirektionalen Synonymen oder eine Kette mehrerer bidirektionaler Synonyme für dasselbe Keyword erstellen.

**Jacke** ![Zwei-Wege-](assets/btn-two-way.png)
**Hose** ![Zweiwegselektor](assets/btn-two-way.png) Hose ![Zweiwegselektor](assets/btn-two-way.png)

## unidirektional

Ein Einwegsynonym ist eine Teilmenge eines Keywords, jedoch mit einer spezifischeren Bedeutung. Zum Beispiel sind Capris und Shorts Hosen, aber nicht alle Hosen sind Capris oder Shorts. Die Suche nach Hosen umfasst Capris und Shorts. Die Suche nach Shorts gibt jedoch keine Capris zurück.

**Sweatshirt** ![Einwegselektor](assets/btn-one-way.png) Kapuzenpullover
**Hose** ![Einwegwähler](assets/btn-one-way.png) capris ![Mehrere Einwegwähler](assets/btn-multiple-one-way.png) Wadenlängenhose ![Mehrere Einwegwähler](assets/btn-multiple-one-way.png) Tretschieber

## Best Practices

Beachten Sie die folgenden Best Practices, um [!DNL Live Search] Synonyme optimal zu nutzen.

### „Stoppwörter“ vermeiden

[!DNL Live Search] filtert gängige englische „Stoppwörter“ aus Synonymen heraus, z. B.:

a, an, and, are, as, at, be, but, by, for, if, in, into, is, it, no, not, of, on, or, such, that, the, their, then, there, these, they, this, to, was, will, with

Stoppwörter machen Synonyme nicht bedeutungsvoller, sondern erhöhen die Menge an Daten, die verarbeitet werden müssen.

### Verwendung von Singular und Plural

Es ist nicht notwendig, sowohl die Singular- als auch die Pluralform eines Wortes als Synonym zu definieren. Wenn Sie eine Mischung aus Einzel- und Pluralbegriffen in Ihrem Katalog haben, findet Search den richtigen Satz von Produkten. Wenn Sie beispielsweise das Wort „Hose“ im Produktnamen verwenden und ein Käufer nach „Hose“ sucht, wird der richtige Satz von Produkten zurückgegeben und das einzelne Wort „Hose“ wird als Vorschlag angeboten. Der Begriff „Hose“ wird oft in der Modebranche und manchmal im Einzelhandel verwendet, obwohl die Pluralform „Hose“ in einigen Bereichen häufiger verwendet wird. (Das Wort „Hose“ bezieht sich technisch auf den Teil eines Kleidungsstücks, der ein Bein bedeckt, weshalb Sie eine „Hose“ benötigen, um beide Beine zu bedecken.)

### Konsistenz

Konsistenz mit der Verwendung der Terminologie in Ihrem Katalog Beachten Sie, dass es regionale Unterschiede in der Verwendung und manchmal Unterschiede innerhalb einer Branche geben kann.

## Synonymverhalten für mehrere Wörter

Bei Synonymen mit mehreren Wörtern betrachtet Commerce das Synonym als eine Phrase. Wenn Sie beispielsweise ein Zwei-Wege-Synonym **Esszimmertisch** ![Zwei-Wege-Selektor](assets/btn-two-way.png) **&#x200B;**&#x200B;Küchentisch![Zwei-Wege-Selektor](assets/btn-two-way.png)**Esstisch** erstellen, durchsucht Commerce alle Felder, die auf Durchsuchbar eingestellt sind, nach **Esszimmertisch** oder **Küchentisch** oder **Esstisch**.

Wenn kein Synonym erstellt wird und ein Käufer nach **Küchentabelle** sucht, sucht Commerce in den durchsuchbaren Feldern nach den Begriffen, auch über verschiedene Felder hinweg, z. B. **table** im Namensfeld und **küche** im Meta-Schlüsselwort.

Nachdem Sie ein Synonym erstellt haben, ändert sich das Suchverhalten, sodass Sie nach der exakten Phrase **Küchentabelle)**. Dadurch kann die Anzahl der Ergebnisse reduziert werden, da nur Produkte mit der exakten Phrase angezeigt werden.

Wenn Sie möchten, dass nach den Begriffen separat gesucht wird, können Sie [ein Support-Ticket erstellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide). Wenn genügend Bedarf besteht, wird Commerce in einer zukünftigen Version erwägen, diese Funktion zum Produkt hinzuzufügen.
