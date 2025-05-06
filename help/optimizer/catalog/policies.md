---
title: Richtlinien
description: Erfahren Sie, wie Sie mit Richtlinien Daten innerhalb eines Kanals filtern können, um sicherzustellen, dass Daten an das richtige Ziel gesendet werden.
hide: true
recommendations: noCatalog
exl-id: 05bbad1a-d612-41a4-9575-543f507089c3
source-git-commit: a731d978aa180633431b0dd9dde5439c286461a2
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Richtlinien

>[!NOTE]
>
>In dieser Dokumentation wird ein Produkt beschrieben, das sich in der Entwicklung für den frühzeitigen Zugriff befindet und nicht alle für die allgemeine Verfügbarkeit vorgesehenen Funktionen enthält.

Richtlinien sind Datenzugriffsfilter, die in Kanälen enthalten sind, welche die an die einzelnen Kanäle gelieferten Daten weiter verfeinern. Richtlinien stellen sicher, dass der richtige Inhalt an das richtige Ziel gesendet wird. Zum Beispiel physische Ladengeschäfte, Marktplätze, Werbeleitungen (Google, Facebook, Instagram).

Richtlinien basieren auf Produktattributen wie Marke, Modell oder Teilekategorie und werden verwendet, um die Katalogdaten an bestimmte Geschäftsanforderungen anzupassen. &#x200B;

## Filter

Filter sind der Mechanismus innerhalb einer Richtlinie, die die Katalogsegmentierung erzwingen. Mit Filtern können Unternehmen Storefronts und Kanäle an spezifische Produktsätze anpassen, die auf betrieblichen Anforderungen basieren. Sie verwenden Kriterien wie Produktattribute, Operatoren und Werte, um eine Regel oder Bedingung zu definieren, die angibt, welche Produkte in einem Kanal oder einer Storefront enthalten oder ausgeschlossen sind.

### Teile eines Filters

Ein Filter besteht aus den folgenden Teilen:

| Teil | Beschreibung | Beispiel |
|---|---|---|
| **Attribut** | Das für die Filterung verwendete Produktattribut. | `part_category` |
| **Operator** | Die auf das Attribut angewendete Bedingung. | `IN`, `EQUALS`, `CONTAINS` |
| **Wertquelle** | Gibt an, ob die Werte `STATIC` oder `TRIGGER` sind. | `STATIC` [Weitere Informationen](#value-source-types) |
| **Wert** | Die spezifischen Werte, die die Bedingung erfüllen. | `brakes, suspension` |

### Beispiel

Ein Filter mit dem Attribut `part_category`, einem Operator von `IN` und Werten `brakes, suspension` stellt sicher, dass nur Produkte mit einem `part_category` mit dem Wert `brake` oder `suspension` von der Richtlinie gefiltert und angezeigt werden.

### Quelltypen von Werten

Es gibt zwei Arten von Wertquellen: **STATIC** und **TRIGGER**.

Richtlinien mit einer **Wertquelle** von **STATIC** werden als universelle Richtlinien betrachtet. Universelle Richtlinien definieren das Erlebnis einer Website als Ganzes. Das bedeutet, dass der Kanal diese Richtlinie immer ausführt. Mit anderen Worten: Die Ausführung dieser Richtlinie basiert auf keiner Benutzerinteraktion in der Storefront.

Richtlinien mit einer **Wertquelle** von **TRIGGER** werden als exklusive Richtlinien bezeichnet. Das bedeutet, dass der Kanal diese Richtlinie nur dann ausführt, wenn der Trigger in der Kopfzeile des API-Aufrufs angegeben ist. In der Storefront bedeutet dies, dass Informationen basierend auf der Auswahl des Käufers angezeigt werden. Im folgenden Bild gibt es beispielsweise zwei Dropdown-Menüs: **Marke** und **Modell**.

![Trigger-Wertquelle auf Storefront](../assets/policy-trigger.png)

**Marke** und **Modell** sind definierte Trigger:

- `AC-Policy-Brand`
- `AC-Policy-Model`

Wenn der Käufer auf die Dropdown **Marke** klickt, enthält die Kopfzeile des API-Aufrufs `AC-Policy-Brand`, die so konfiguriert ist, dass nur Produkte angezeigt werden, die für die `AC-Policy-Brand`-Richtlinie spezifisch sind.

## Richtlinie erstellen

In diesem Abschnitt erstellen Sie eine neue Richtlinie. Die Richtlinie kann entweder **STATIC** oder **TRIGGER** sein.

### Erstellen einer STATISCHEN Richtlinie

1. Öffnen Sie im linken Menü den Abschnitt **[!UICONTROL Catalog]** und klicken Sie auf **[!UICONTROL Policies]**.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Add Policy]** .

   Eine neue Seite wird geöffnet, auf der Sie die Richtliniendetails ausfüllen können. &#x200B;

1. Geben Sie den Namen der Richtlinie ein, z. B. „Celport Part Categories“.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Add Filter]** .

   Ein Dialogfeld wird geöffnet, in dem Sie Filterdetails hinzufügen können.

1. Fügen Sie die Filterdetails hinzu. Beispiel:

   1. **Attribut** - Geben Sie ein Attribut aus Ihrem Katalog ein. Beispiel: „part_category“. Dieser Name muss genau mit dem Namen des Attributs im Katalog übereinstimmen.
   1. **Operator** - Wählen Sie den Operator. Beispiel: **IN**. &#x200B;
   1. **Wert Source** - Wählen Sie **STATIC**. &#x200B;
   1. **Wert** - Geben Sie die Werte innerhalb des zuvor angegebenen Attributs ein. Beispiel: „Bremsen, Aufhängung“. &#x200B;Diese Namen müssen genau mit den Namen der Werte für das zuvor angegebene Attribut übereinstimmen.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Save]** im Dialogfeld Filterdetails . &#x200B;

1. Klicken Sie auf die Aktionspunkte (…) neben dem erstellten Filter und wählen Sie **Aktivieren**. Von hier aus können Sie **Filter auch**, **Deaktivieren** oder **Löschen**.

   Die Spalte **Status** zeigt ein grünes Symbol und das Wort „Aktiviert“.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Save]** , um die neue Richtlinie zu speichern&#x200B; Wenn die Schaltfläche nicht aktiv ist, stellen Sie sicher, dass der Richtlinienname hinzugefügt wird, indem Sie auf das Stiftsymbol neben &quot;**Richtlinie“**.

1. Um Ihre neue Richtlinie zu überprüfen, gehen Sie zurück zur Liste der Richtlinien, indem Sie auf den Pfeil nach hinten klicken. &#x200B;Ihre neue Richtlinie wird aufgelistet.

### Erstellen einer TRIGGER-Richtlinie

1. Öffnen Sie im linken Menü den Abschnitt **[!UICONTROL Catalog]** und klicken Sie auf **[!UICONTROL Policies]**.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Add Policy]** .

   Eine neue Seite wird geöffnet, auf der Sie die Richtliniendetails ausfüllen können. &#x200B;

1. Geben Sie den Namen der Richtlinie ein, z. B. „Celport Part Categories“.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Add Trigger]** .

   Das Dialogfeld **Trigger** Details wird angezeigt.

1. Geben Sie einen Namen für den Trigger ein, z. B. **AC-Policy-Brand**.

1. Wählen Sie den **Transport-Typ**. **HTTP_HEADER** ist derzeit der einzige unterstützte Typ.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Save]** , um den Trigger zu speichern.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Add Filter]** .

   Ein Dialogfeld wird geöffnet, in dem Sie Filterdetails hinzufügen können.

1. Fügen Sie die Filterdetails hinzu. Beispiel:

   1. **Attribut** - Geben Sie ein Attribut aus Ihrem Katalog ein. Beispiel: „part_category“. Dieser Name muss genau mit dem Namen des Attributs im Katalog übereinstimmen.
   1. **Operator** - Wählen Sie den Operator. Beispiel: **IN**. &#x200B;
   1. **Wert Source** - **TRIGGER**. &#x200B;
   1. **Wert** - Geben Sie den zuvor erstellten Trigger-Namen ein (**AC-Policy-Brand**).

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Save]** im Dialogfeld Filterdetails . &#x200B;

1. Klicken Sie auf die Aktionspunkte (…) neben dem erstellten Filter und wählen Sie **Aktivieren**. Von hier aus können Sie **Filter auch**, **Deaktivieren** oder **Löschen**.

   Die Spalte **Status** zeigt ein grünes Symbol und das Wort „Aktiviert“.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Save]** , um die neue Richtlinie zu speichern&#x200B; Wenn die Schaltfläche nicht aktiv ist, stellen Sie sicher, dass der Richtlinienname hinzugefügt wird, indem Sie auf das Stiftsymbol neben &quot;**Richtlinie“**.

1. Um Ihre neue Richtlinie zu überprüfen, gehen Sie zurück zur Liste der Richtlinien, indem Sie auf den Pfeil nach hinten klicken. &#x200B;Ihre neue Richtlinie wird aufgelistet.

Wenn Sie diese Schritte befolgen, wird die Richtlinie erstellt und kann mit einem Kanal verknüpft werden, um die Sichtbarkeit des Produkts zu steuern.
