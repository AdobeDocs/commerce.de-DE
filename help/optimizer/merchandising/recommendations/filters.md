---
title: Empfehlungsfilter
description: Erfahren Sie, wie Sie mit Filtern steuern können, welche Produkte in  [!DNL Adobe Commerce Optimizer]  Recommendations angezeigt werden.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 746c016f149fb49b9c483968a8a5f40196b163ed
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Produkte filtern

[!DNL Adobe Commerce Optimizer] wendet nicht konfigurierbare Standardfilter automatisch auf Empfehlungseinheiten an. Wenn mehrere Empfehlungseinheiten auf einer Seite bereitgestellt werden, filtert [!DNL Adobe Commerce Optimizer] alle Produkte heraus, die in den Einheiten wiederholt werden. Es wird nur der erste Hinweis auf ein wiederholtes Produkt verwendet, um Platz für andere zu empfehlende Produkte zu schaffen. [!DNL Adobe Commerce Optimizer] filtert auch alle zuvor gekauften Produkte und diejenigen aus, die sich im Warenkorb befinden.

Wenn Sie [Empfehlungseinheit erstellen](create.md) können Sie Filter definieren, die steuern, welche Produkte in Recommendations angezeigt werden können. Diese Filter basieren auf einem Satz von Ein- oder Ausschlussbedingungen, die Sie definieren. In den Empfehlungen werden nur Produkte angezeigt, die allen Einschlussbedingungen entsprechen. Produkte, die eine der Ausschlussbedingungen erfüllen, werden nicht empfohlen.

Sie können mehrere Filter konfigurieren und nur die gewünschten aktivieren, indem Sie den Umschalter auf jeder Filterseite auswählen. Auf diese Weise können Sie Entwürfe von Filtern für die zukünftige Verwendung erstellen. Die Anzahl der aktivierten Filter wird auf jeder Registerkarte angezeigt.

## Bedingungen

Bedingungen können statisch oder dynamisch sein.

- Eine statische Bedingung verwendet vorhandene Produktattribute, um zu bestimmen, welche Produkte in der Einheit angezeigt werden können. Sie können beispielsweise angeben, dass nur Lagerprodukte mit einem Preis über 25 USD in der Einheit angezeigt werden.

- Eine dynamische Bedingung bestimmt den aktuellen Kontext eines Käufers, z. B. die aktuell angezeigte Kategorie oder das angezeigte Produkt. Wenn Sie beispielsweise eine Produktempfehlung erstellen, die auf Produktdetailseiten bereitgestellt wird, können Sie eine Bedingung erstellen, um nur Produkte zu empfehlen, die innerhalb einer relativen Preisspanne des aktuell angezeigten Produkts liegen.

### Logische Operatoren

Die logischen Operatoren `AND` und `OR` werden verwendet, um mehrere Bedingungen miteinander zu verbinden. Wenn Sie sowohl Ein- als auch Ausschlussfilter verwenden, werden die Einschlüsse zunächst ausgewertet, um alle möglichen Produkte zu bestimmen, die empfohlen werden können. Anschließend werden Produkte, die mit Ausschlussfiltern übereinstimmen, aus der Liste entfernt.

- `AND` - Verbindet zwei Einschlussfilterbedingungen
- `OR` - Verbindet zwei Ausschluss-Filterbedingungen

## Filtertypen

![Filter](../../assets/rec-conditions.png)

### Produkt

Produktfilter geben an, welche Produkte für die Anzeige in Recommendations infrage kommen bzw. nicht infrage kommen. Sie können keine Produkte auswählen, die deaktiviert oder nicht einzeln sichtbar sind, da diese Produkte nie in den Empfehlungen angezeigt werden können.

>[!NOTE]
>
>Untergeordnete Produkte eines konfigurierbaren Produkts werden nicht in einer Empfehlungseinheit angezeigt, da diese untergeordneten Produkte die Sichtbarkeit &quot;_einzeln sichtbar“_.

### Preis

Ein auf dem Produktpreis basierender Filter verwendet den Endpreis, um den Vergleich durchzuführen. Der Endpreis beinhaltet alle Rabatte oder Sonderpreise, die anonymen Käufern zur Verfügung stehen.

<!--### Attribute

You can filter products based on attribute criteria, including attribute values. Selected values use OR logic to either include or exclude products when any of the specified values are found.-->
