---
title: Synonyme
description: Erfahren Sie mehr über die verschiedenen Arten von Synonymen in [!DNL Adobe Commerce Optimizer].
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: a74e48ea-e069-4ccc-a67f-2f85be251fb5
TQID: https://experienceleague.adobe.com/23kmFWLruZeFMxIjKZJKbs0y9q10DDtbFG8ioLC5U-o
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 393
ht-degree: 0%

---

# Typen von Synonymen

Ein- und Zwei-Wege-Synonyme erweitern die Definition von Keywords. Einige sind mit dem Keyword austauschbar, während andere eine Teilmenge des Keywords darstellen.

## wechselseitig

Zwei-Wege-Synonyme haben dieselbe Bedeutung und geben dieselben Suchergebnisse zurück. Im folgenden Beispiel ist das erste fett gedruckte Wort das Schlüsselwort, das im Katalog verwendet wird, gefolgt von Wörtern, die dieselbe Bedeutung wie das ursprüngliche Schlüsselwort haben. Sie können ein einfaches Paar von bidirektionalen Synonymen oder eine Kette mehrerer bidirektionaler Synonyme für dasselbe Keyword erstellen.

**Jacke** ![Zwei-Wege-](../../assets/two-way.png)
**Hose** ![Zweiwegselektor](../../assets/two-way.png) Hose ![Zweiwegselektor](../../assets/two-way.png)

## unidirektional

Ein Einwegsynonym ist eine Teilmenge eines Keywords, jedoch mit einer spezifischeren Bedeutung. Zum Beispiel sind Capris und Shorts Hosen, aber nicht alle Hosen sind Capris oder Shorts. Die Suche nach Hosen umfasst Capris und Shorts. Die Suche nach Shorts gibt jedoch keine Capris zurück.

**Sweatshirt** ![Einwegselektor](../../assets/one-way.png) Kapuzenpullover
**Hose** ![Einwegselektor](../../assets/one-way.png) capris ![Einwegselektor](../../assets/one-way.png) Wadenlängenhose ![Einwegselektor](../../assets/one-way.png) Peddlers

## Synonymverhalten für mehrere Wörter

Bei Synonymen mit mehreren Wörtern betrachtet [!DNL Adobe Commerce Optimizer] das Synonym als eine Phrase. Wenn Sie beispielsweise ein Zweiwegsynonym erstellen **Esszimmertisch** ![Zweiwegselektor](../../assets/two-way.png) **&#x200B;**&#x200B;Küchentisch![Zweiwegselektor](../../assets/two-way.png)**Esstisch**, dann [!DNL Adobe Commerce Optimizer] alle Felder durchsucht, die auf Durchsuchbar eingestellt sind, um das Auftreten von **Esszimmertisch** oder **Küchentisch** oder **Esstisch**.

Wenn kein Synonym erstellt wird und ein Käufer nach **Küchentabelle** sucht, sucht [!DNL Adobe Commerce Optimizer] in den durchsuchbaren Feldern nach den Begriffen, auch über verschiedene Felder hinweg, z. B. **table** im Namensfeld und **KÜCHE** im Meta-Schlüsselwort.

Nachdem Sie ein Synonym erstellt haben, ändert sich das Suchverhalten, sodass Sie nach der exakten Phrase **Küchentabelle)**. Dadurch kann die Anzahl der Ergebnisse reduziert werden, da nur Produkte mit der exakten Phrase angezeigt werden.

Wenn Sie möchten, dass nach den Begriffen separat gesucht wird, können Sie [ein Support-Ticket erstellen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide). Wenn genügend Bedarf besteht, werden [!DNL Adobe Commerce Optimizer] in einer zukünftigen Version erwägen, diese Funktion zum Produkt hinzuzufügen.
