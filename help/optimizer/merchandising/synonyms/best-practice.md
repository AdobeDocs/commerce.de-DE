---
title: Best Practices für Synonyme
description: Erfahren Sie mehr über die Best Practices zur Implementierung von Synonymen in Ihrem Store.
role: Admin, Developer
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 54b300ed89f830c2fe5258ec889302a59decd59f
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Best Practices für Synonyme

Im Folgenden finden Sie eine Liste mit Best Practices zum Erstellen von Synonymen.

- [!DNL Adobe Commerce Optimizer] verwaltet Rechtschreibfehler standardmäßig. Sie können Synonyme einrichten, um Wörter einzuschließen, die Käufer möglicherweise verwenden, die sich von den in Ihrem Katalog angegebenen Wörtern unterscheiden. Sie wollen keinen Verkauf verlieren, weil jemand ein „Sofa“ sucht, während Ihr Produkt als „Couch“ aufgeführt ist. Sie können eine breite Palette von Suchbegriffen erfassen, indem Sie alle möglichen Wörter eingeben, die Kunden verwenden könnten, um Ihre Produkte zu finden. Sie können [Synonyme auf eine oder zwei Arten festlegen](add.md#step-2-define-the-synonym-by-type) um die Ergebnisse zu verbessern.

- Ordnen Sie nun alle Markenbezeichnungen und Abkürzungen ihren vollständigen Namen zu, z. B. „HP“ für „Hewlett-Packard“ und die gebräuchlichen Produktspitznamen, z. B. &quot;iPhone&quot; für &quot;Apple iPhone&quot;.

- Geben Sie branchenspezifischen Jargon und Begriffe an, die Käufer möglicherweise austauschbar verwenden, z. B. „Sneaker“ und „Laufschuhe“.

- Aktualisieren Sie die Synonym-Liste regelmäßig auf der Grundlage neuer Suchtrends, Produktzusätze und des Käuferverhaltens.

- Testen Sie die Effektivität von Synonym-Zuordnungen durch die Analyse von Suchergebnissen und Kunden-Feedback. Verfeinern Sie Zuordnungen, um die Genauigkeit und Relevanz zu verbessern.

- Vermeiden Sie die Verwendung von Stoppwörtern, da sie Synonyme nicht bedeutungsvoller machen, sondern die Menge an Daten, die verarbeitet werden müssen, erhöhen. [!DNL Adobe Commerce Optimizer] filtert gängige englische „Stoppwörter“ aus Synonymen heraus, z. B.:

  a, an, and, are, as, at, be, but, by, for, if, in, into, is, it, no, not, of, on, or, such, that, the, their, then, there, these, they, this, to, was, will, with

- Es ist nicht notwendig, sowohl die Singular- als auch die Pluralform eines Wortes als Synonym zu definieren. Wenn Sie eine Mischung aus Einzel- und Pluralbegriffen in Ihrem Katalog haben, findet Search den richtigen Satz von Produkten. Wenn Sie beispielsweise das Wort „Hose“ im Produktnamen verwenden und ein Käufer nach „Hose“ sucht, wird der richtige Satz von Produkten zurückgegeben und das einzelne Wort „Hose“ wird als Vorschlag angeboten. Der Begriff „Hose“ wird oft in der Modebranche und manchmal im Einzelhandel verwendet, obwohl die Pluralform „Hose“ in einigen Bereichen häufiger verwendet wird. (Das Wort „Hose“ bezieht sich technisch auf den Teil eines Kleidungsstücks, der ein Bein bedeckt, weshalb Sie eine „Hose“ benötigen, um beide Beine zu bedecken.)

- Konsistenz mit der Verwendung der Terminologie in Ihrem Katalog Beachten Sie, dass es regionale Unterschiede in der Verwendung und manchmal Unterschiede innerhalb einer Branche geben kann.
