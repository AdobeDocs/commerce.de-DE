---
title: Empfehlungsfilter
description: Erfahren Sie, wie Sie mit Filtern steuern können, welche Produkte in  [!DNL Adobe Commerce Optimizer]  Recommendations angezeigt werden.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: f6100538-23c0-4e90-9834-a895d4707282
source-git-commit: ba445bf33ec9334c853245fce125af12cd244367
workflow-type: tm+mt
source-wordcount: '998'
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

Jeder Filtertyp bezieht sich auf einen anderen Aspekt des Katalogs, z. B. Produkt und Preis, sodass Sie eingrenzen oder erweitern können, welche Produkte für eine Einheit infrage kommen. Wählen Sie die Typen aus, die Ihren Merchandising-Zielen entsprechen, und kombinieren Sie dann die Ein- und Ausschlussbedingungen nach Bedarf. In den folgenden Unterabschnitten wird beschrieben, wie sich jeder Typ verhält und wie [!DNL Adobe Commerce Optimizer] ihn anwendet.

>[!NOTE]
>
>Es können nur Produkte empfohlen werden **die Ihren** Einschluss“ entsprechen. Alle Produkte, die mit einem Filter **Ausschluss** übereinstimmen, werden entfernt.

### Preis

>[!IMPORTANT]
>
>Die folgende Funktion befindet sich in der Betaphase.

Die Preisfilterung nutzt den **endgültigen berechneten Preis** für das &quot;**&quot; des jeweiligen Produkts** jenes, das der Storefront zugewiesen ist, in der die Empfehlungseinheit gerendert wird. Dieser Wert spiegelt Rabatte, Angebote und Sonderpreise wider, die in diesem Preisbuch definiert sind, nicht nur im Listenpreis. Bei der Auswertung wird nur das Preisbuch dieser Storefront verwendet. Andere Storefronts oder Preisbücher gelten nicht. Die Zuordnung von Preisbüchern zu einer Storefront wird mit Ihrem Katalog und der Einrichtung von [Preisbüchern](../../setup/pricebooks.md) konfiguriert.

#### Einschließen und Ausschließen von Regeln und Preis

- **Einschlussregeln** - Nur Produkte, deren Endpreis **allen** Einschlussbedingungen entspricht, bleiben förderfähig. Dazu gehören alle aktivierten Einschlussfilter (z. B. Ihre Preisspanne plus alle anderen Einschlussregeln).
- **Ausschlussregeln** - Produkte, deren Endpreis **einer** definierten Ausschlussbedingung entspricht, werden aus den Empfehlungen entfernt.

**Angezeigter Preis** - Der auf Produkten innerhalb der Empfehlungseinheit angezeigte Preis ist derselbe **Endpreis** aus dem Preisbuch dieser Storefront, sodass das, was die Käufer sehen, mit dem Wert übereinstimmt, der zum Filtern verwendet wird.

#### Preisfilter einrichten

1. Beim [Erstellen oder Bearbeiten](create.md) einer Empfehlungseinheit öffnen Sie **[!UICONTROL Filter products]** (oder gehen Sie zum Schritt _Filter_ im Einheitenworkflow).
1. Wählen Sie die Registerkarte **[!UICONTROL Inclusions]** oder **[!UICONTROL Exclusions]** aus, je nachdem, ob Sie nur Produkte in einer Preisspanne zulassen oder Produkte in einer Preisspanne blockieren möchten. Das Badge auf jeder Registerkarte zeigt an, wie viele Filter dieses Typs aktiviert sind.
1. Wählen Sie in der Liste auf der linken Seite **[!UICONTROL Price]**.
1. Schalten Sie **[!UICONTROL Enable filter]** ein.

   Die Preiswerte verwenden die **Basiswährung der Website**, wie auf der Seite angegeben.

1. Öffnen Sie **[!UICONTROL Include products based on]** (auf der Registerkarte **[!UICONTROL Inclusions]**) oder das entsprechende Steuerelement auf der Registerkarte **[!UICONTROL Exclusions]** und wählen Sie **[!UICONTROL Set price range]** aus.
1. Legen Sie eine optionale **[!UICONTROL Min price]** und/oder **[!UICONTROL Max price]** mithilfe der Felder neben dem Währungssymbol fest. Sie können Beträge eingeben oder die Steuerelemente **-** und **+** verwenden, um Werte anzupassen. Lassen Sie eine Bindung leer, wenn Sie keine Mindest- oder Höchstwerte benötigen. Die Bandbreite wird mit dem endgültigen berechneten Preis jedes Produkts für das aktive Preisbuch der Storefront verglichen.
1. Stellen Sie die Konfiguration der Empfehlungseinheit fertig und speichern oder veröffentlichen Sie wie gewohnt, damit der Filter wirksam wird.

![Preisfilter](../../assets/filter-price.png)

### Produkt

Produktfilter zielen auf einzelne Katalogelemente nach **SKU** ab. Sie können eine oder mehrere SKUs hinzufügen, um entweder nur diese Produkte zuzulassen (**Einschlüsse**) oder sie zu blockieren (**Ausschlüsse**), indem Sie dieselbe **[!UICONTROL Filter products]** wie [Preisfilter](#price). Sie können keine deaktivierten Produkte oder Produkte anzeigen, die nicht einzeln in einer Empfehlungseinheit sichtbar sind; diese Produkte werden unabhängig von Filtern nie in der Storefront angezeigt.

#### Einrichten eines Produktfilters

1. Beim [Erstellen oder Bearbeiten](create.md) einer Empfehlungseinheit öffnen Sie **[!UICONTROL Filter products]** (oder gehen Sie zum Schritt _Filter_ im Einheitenworkflow).
1. Wählen Sie die Registerkarte **[!UICONTROL Inclusions]** oder **[!UICONTROL Exclusions]** aus. Das Badge auf jeder Registerkarte zeigt an, wie viele Filter dieses Typs aktiviert sind.
1. Wählen Sie in der Liste auf der linken Seite **[!UICONTROL Product]**.
1. Schalten Sie **[!UICONTROL Enable filter]** ein.

   Die Überschrift des rechten Bedienfelds spiegelt die Registerkarte wider, z. B. **[!UICONTROL Product inclusions]** oder das Äquivalent für Ausschlüsse.

1. Geben Sie **[!UICONTROL Product SKU]** eine SKU ein und klicken Sie auf **[!UICONTROL Add]**. Wiederholen Sie diesen Schritt, um weitere SKUs hinzuzufügen.

   Unter **[!UICONTROL Product SKUs]** wird jede SKU als entfernbares Tag angezeigt. Klicken Sie **X** auf ein Tag, um diese SKU zu entfernen, oder klicken Sie auf **[!UICONTROL Clear All]**, um alle SKUs aus der Liste zu entfernen.

1. Stellen Sie die Konfiguration der Empfehlungseinheit fertig und speichern oder veröffentlichen Sie wie gewohnt, damit der Filter wirksam wird.

Für **Einschlüsse** können nur Produkte empfohlen werden, deren SKUs aufgelistet sind (und die mit Ihren anderen aktivierten Einschlussfiltern übereinstimmen). Für **Ausschlüsse** wird kein Produkt empfohlen, dessen SKU aufgelistet ist, selbst wenn es ansonsten qualifiziert wäre.

![Produktfilter](../../assets/filter-product.png)

>[!NOTE]
>
>Untergeordnete Produkte eines konfigurierbaren Produkts werden nicht in einer Empfehlungseinheit angezeigt, da diese untergeordneten Produkte die Sichtbarkeit &quot;_einzeln sichtbar“_.

<!--
### Attribute

You can filter products based on attribute criteria, including attribute values. Selected values use OR logic to either include or exclude products when any of the specified values are found.
-->
