---
title: Produkte filtern
description: Bedingungen definieren, die Produkte entweder einschließen oder von der Verwendung als Empfehlungen ausschließen.
exl-id: 140bf047-4f6a-48da-b536-d96e78ae3d17
source-git-commit: 1b10163c39d9f309afd24aa2e808a57e069258f8
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---

# Produkte filtern

Adobe Commerce wendet nicht konfigurierbare Standardfilter automatisch auf Empfehlungseinheiten an. Wenn mehrere Empfehlungseinheiten auf einer Seite bereitgestellt werden, filtert Adobe Commerce alle Produkte heraus, die in den Einheiten wiederholt werden. Es wird nur der erste Hinweis auf ein wiederholtes Produkt verwendet, um Platz für andere zu empfehlende Produkte zu schaffen. Adobe Commerce filtert auch alle zuvor erworbenen Produkte und diejenigen aus dem Warenkorb heraus.

Wenn Sie [Empfehlungseinheit erstellen](create.md) können Sie Filter definieren, die steuern, welche Produkte in Recommendations angezeigt werden können. Diese Filter basieren auf einem Satz von Ein- oder Ausschlussbedingungen, die Sie definieren. In den Empfehlungen werden nur Produkte angezeigt, die allen Einschlussbedingungen entsprechen. Produkte, die eine der Ausschlussbedingungen erfüllen, werden nicht empfohlen.

Sie können mehrere Filter konfigurieren und nur die gewünschten aktivieren, indem Sie den Umschalter auf jeder Filterseite auswählen. Auf diese Weise können Sie Entwürfe von Filtern für die zukünftige Verwendung erstellen. Die Anzahl der aktivierten Filter wird auf jeder Registerkarte angezeigt.

## Bedingungen

Bedingungen können statisch oder dynamisch sein.

- Eine statische Bedingung verwendet vorhandene Produktattribute, um zu bestimmen, welche Produkte in der Einheit angezeigt werden können. Sie können beispielsweise angeben, dass nur Lagerprodukte mit einem Preis über 25 USD in der Einheit angezeigt werden. Statische Bedingungen sind für alle Seitentypen verfügbar.

- Eine dynamische Bedingung bestimmt den aktuellen Kontext eines Käufers, z. B. die aktuell angezeigte Kategorie oder das angezeigte Produkt. Wenn Sie beispielsweise eine Produktempfehlung erstellen, die auf Produktdetailseiten bereitgestellt wird, können Sie eine Bedingung erstellen, um nur Produkte zu empfehlen, die innerhalb einer relativen Preisspanne des aktuell angezeigten Produkts liegen. Dynamische Bedingungen sind für jeden Seitentyp mit Ausnahme der Startseite und für Seiten mit Empfehlungen, die in Page Builder platziert werden, verfügbar.

### Logische Operatoren

Die logischen Operatoren `AND` und `OR` werden verwendet, um mehrere Bedingungen miteinander zu verbinden. Wenn Sie sowohl Ein- als auch Ausschlussfilter verwenden, werden die Einschlüsse zunächst ausgewertet, um alle möglichen Produkte zu bestimmen, die empfohlen werden können. Anschließend werden Produkte, die mit Ausschlussfiltern übereinstimmen, aus der Liste entfernt.

- `AND` - Verbindet zwei Einschlussfilterbedingungen
- `OR` - Verbindet zwei Ausschluss-Filterbedingungen

>[!NOTE]
>
> Einschluss- und Ausschlussfilter ersetzen die alten Kategorieausschlüsse in Version 3.2.2 und höher des `magento/product-recommendations`. Weitere Informationen [&#x200B; Adobe Commerce-Versionen finden &#x200B;](release-notes.md) in den Versionshinweisen .

## Filtertypen {#filtertypes}

![Filter](assets/rec-conditions.png)

### Kategorie

Filtert Produkte nach ihrer Kategorie. Der Kategoriefilter verwendet direkte Kategoriezuweisungen und deren Unterkategorien. Wenn Sie beispielsweise eine Ausschlussbedingung für Kategorie `Gear` aktivieren, werden `Gear` zugewiesene Produkte und alle zugehörigen Unterkategorien wie `Gear/Bags` oder `Gear/Fitness Equipment` ausgeschlossen. Dasselbe gilt für einen Einschlussfilter für eine Kategorie. Wenn Sie beispielsweise eine Einschlussbedingung für Kategorie `Gear` aktivieren, werden `Gear` zugewiesene Produkte und alle zugehörigen Unterkategorien wie `Gear/Bags` oder `Gear/Fitness Equipment` einbezogen.

Das Feld Kategorie zeigt Kategorien an, die zur aktuellen Storeview gehören.

>[!NOTE]
>
>Für B2B-Händler entspricht der Kategoriefilter allen [kundenspezifischen Produktkategorien](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html?lang=de) die Sie konfiguriert haben.

Adobe Commerce empfiehlt die Verwendung der folgenden Kategoriefilterkonfiguration, wenn Sie Empfehlungen für Ihre Seitentypen bereitstellen:

| Seite | Filtern nach |
|---|---|
| Startseite | Produkte nicht filtern. |
| Kategorie | Produkte in der jeweiligen Kategorie filtern. |
| Produktdetails | Produkte in denselben Kategorien filtern. |
| Warenkorb | Filtern Sie die Kategorien von Produkten im Warenkorb. |
| Bestellbestätigung | Filtern Sie die Kategorien der gekauften Produkte. |

### Produkt

Produktfilter geben an, welche Produkte für die Anzeige in Recommendations infrage kommen bzw. nicht infrage kommen. Sie können keine Produkte auswählen, die deaktiviert oder nicht einzeln sichtbar sind, da diese Produkte nie in den Empfehlungen angezeigt werden können.

>[!NOTE]
>
>Untergeordnete Produkte eines konfigurierbaren Produkts werden nicht in einer Empfehlungseinheit angezeigt, da diese untergeordneten Produkte die Sichtbarkeit &quot;_einzeln sichtbar“_.

### Typ

Ein Filter, der auf dem Produkttyp basiert, schließt alle Produkte eines bestimmten Typs ein oder aus. Zu den unterstützten Typen _einfach_, _konfigurierbar_, _virtuell_, _herunterladbar_ oder _Geschenkkarte_. _Bundle_, _grouped_ und benutzerdefinierte Produkttypen werden nicht unterstützt.

### Sichtbarkeit

Filtert Produkte nach Sichtbarkeit, z. B. _Katalog_, _Suche_ oder beides.

### Preis

Ein auf dem Produktpreis basierender Filter verwendet den Endpreis, um den Vergleich durchzuführen. Im Endpreis sind alle Rabatte enthalten, die anonymen Käufern gewährt werden. Für B2B-Händler entspricht der angezeigte Preis dem [kundenspezifischen Gruppenpreis](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=de) den Sie konfiguriert haben.

### Bestandsstatus

Die folgenden Ausschlussfilter können verwendet werden, um Produkte anhand des Lagerstatus herauszufiltern:

- Nicht vorrätig - (Nur Ausschluss) Ausgeschlossen sind nicht vorrätige Produkte.
- Niedrig auf Lager - (Nur Ausschlüsse) Ausgeschlossen sind Produkte, die niedrig auf Lager sind. Der niedrige Lagerstatus basiert auf dem Wert _Nur noch x Schwellenwert_ in der [Bestandskonfiguration](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/inventory.html?lang=de).
