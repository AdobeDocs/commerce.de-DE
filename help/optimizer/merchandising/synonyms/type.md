---
title: Synonyme
description: Erfahren Sie mehr über die verschiedenen Arten von Synonymen in [!DNL Adobe Commerce Optimizer].
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 3131cc27a25d1bf958071b973f1d4bf1a68be152
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Typen von Synonymen

Ein- und Zwei-Wege-Synonyme erweitern die Definition von Keywords. Einige sind mit dem Keyword austauschbar, während andere eine Teilmenge des Keywords darstellen.

## wechselseitig

Zwei-Wege-Synonyme haben dieselbe Bedeutung und geben dieselben Suchergebnisse zurück. Im folgenden Beispiel ist das erste fett gedruckte Wort das Schlüsselwort, das im Katalog verwendet wird, gefolgt von Wörtern, die dieselbe Bedeutung wie das ursprüngliche Schlüsselwort haben. Sie können ein einfaches Paar von bidirektionalen Synonymen oder eine Kette mehrerer bidirektionaler Synonyme für dasselbe Keyword erstellen.

**Jacke** ![Zwei-Wege-](../../assets/btn-two-way.png)
**Hose** ![Zweiwegselektor](../../assets/btn-two-way.png) Hose ![Zweiwegselektor](../../assets/btn-two-way.png)

## unidirektional

Ein Einwegsynonym ist eine Teilmenge eines Keywords, jedoch mit einer spezifischeren Bedeutung. Zum Beispiel sind Capris und Shorts Hosen, aber nicht alle Hosen sind Capris oder Shorts. Die Suche nach Hosen umfasst Capris und Shorts. Die Suche nach Shorts gibt jedoch keine Capris zurück.

**Sweatshirt** ![Einwegselektor](../../assets/btn-one-way.png) Kapuzenpullover
**Hose** ![Einwegwähler](../../assets/btn-one-way.png) capris ![Mehrere Einwegwähler](../../assets/btn-multiple-one-way.png) Wadenlängenhose ![Mehrere Einwegwähler](../../assets/btn-multiple-one-way.png) Tretschieber

## Synonymverhalten für mehrere Wörter

Bei Synonymen mit mehreren Wörtern betrachtet [!DNL Adobe Commerce Optimizer] das Synonym als eine Phrase. Wenn Sie beispielsweise ein Zweiwegsynonym erstellen **Esszimmertisch** ![Zweiwegselektor](../../assets/btn-two-way.png) **** Küchentisch![Zweiwegselektor](../../assets/btn-two-way.png)**Esstisch**, dann [!DNL Adobe Commerce Optimizer] alle Felder durchsucht, die auf Durchsuchbar eingestellt sind, um das Auftreten von **Esszimmertisch** oder **Küchentisch** oder **Esstisch**.

Wenn kein Synonym erstellt wird und ein Käufer nach **Küchentabelle** sucht, sucht [!DNL Adobe Commerce Optimizer] in den durchsuchbaren Feldern nach den Begriffen, auch über verschiedene Felder hinweg, z. B. **table** im Namensfeld und **KÜCHE** im Meta-Schlüsselwort.

Nachdem Sie ein Synonym erstellt haben, ändert sich das Suchverhalten, sodass Sie nach der exakten Phrase **Küchentabelle)**. Dadurch kann die Anzahl der Ergebnisse reduziert werden, da nur Produkte mit der exakten Phrase angezeigt werden.

Wenn Sie möchten, dass nach den Begriffen separat gesucht wird, können Sie [ein Support-Ticket erstellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide). Wenn genügend Bedarf besteht, werden [!DNL Adobe Commerce Optimizer] in einer zukünftigen Version erwägen, diese Funktion zum Produkt hinzuzufügen.
