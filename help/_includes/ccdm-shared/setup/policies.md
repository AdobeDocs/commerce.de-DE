---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%
---
Richtlinien definieren Filter, die auf Produkte in einer Katalogansicht angewendet werden. Sie helfen bei der Anpassung des Produktsortiments, das an eine Storefront oder einen Kanal zurückgegeben wird. Dadurch wird sichergestellt, dass die richtigen Inhalte am richtigen Ziel bereitgestellt werden. Zum Beispiel Ladengeschäfte, Marktplätze und Werbekanäle wie Google, Facebook und Instagram.

Richtlinien verwenden Produktattribute wie Marke, Modell oder Teilekategorie, um Katalogdaten an Geschäftsanforderungen anzupassen. &#x200B;

## Zugriff auf den Arbeitsbereich Richtlinien

Wie Sie den Arbeitsbereich *Richtlinien* öffnen, hängt vom verwendeten Produkt ab:

- **Adobe Commerce Admin** (Adobe Commerce as a Cloud Service) - Wählen Sie *Katalog* > **Richtlinien**.
- **Adobe Commerce Optimizer Studio**—Wählen Sie *Store-Setup* > **Richtlinien**.

## Filter

Filter definieren attributbasierte Bedingungen, die bestimmen, welche Produkte mit einer Richtlinie übereinstimmen. Wenn eine Richtlinie mit einer Katalogansicht verknüpft ist, hilft sie dabei, die für diese Ansicht zurückgegebenen Produkte anzupassen. Verwenden Sie Produktattribute, Operatoren und Werte, um die entsprechenden Bedingungen zu definieren.

### Teile eines Filters

Ein Filter besteht aus den folgenden Teilen:

| Teil | Beschreibung | Beispiel |
|---|---|---|
| **Attribut** | Das für die Filterung verwendete Produktattribut. | `part_category` |
| **Operator** | Die auf das Attribut angewendete Bedingung. | `IN`, `EQUALS`, `CONTAINS` |
| **Wertquelle** | Gibt an, ob die Werte `STATIC` oder `TRIGGER` sind. | `STATIC` [Weitere Informationen](#value-source-types) |
| **Wert** | Die spezifischen Werte, die die Bedingung erfüllen. | `brakes, suspension` |

### Beispiel

Ein Filter für `part_category`, der den `IN`-Operator mit den Werten `brakes` und `suspension` verwendet, stimmt mit Produkten überein, deren `part_category` Wert ist.

### Quelltypen von Werten

Es gibt zwei Arten von Wertquellen: **STATIC** und **TRIGGER**.

Richtlinien mit einer **Wertquelle** von **STATIC** werden als universelle Richtlinien betrachtet. Universelle Richtlinien definieren das Erlebnis einer Website als Ganzes. Das bedeutet, dass diese Richtlinie immer von der Katalogansicht ausgeführt wird. Die Ausführung der Richtlinie hängt nicht von der Benutzerinteraktion in der Storefront ab.

Richtlinien mit einer **Wertquelle** von **TRIGGER** werden als exklusive Richtlinien bezeichnet. Das bedeutet, dass die Katalogansicht diese Richtlinie nur ausführt, wenn der Trigger in der Kopfzeile des API-Aufrufs angegeben ist. In der Storefront bedeutet dies, dass Informationen basierend auf der Auswahl des Käufers angezeigt werden. Im folgenden Bild gibt es beispielsweise zwei Dropdown-Menüs: **Marke** und **Modell**.

![Trigger-Wertquelle auf Storefront](/help/assets/ccdm-shared/setup/policy-trigger.png)

**Marke** und **Modell** sind definierte Trigger:

- `AC-Policy-Brand`
- `AC-Policy-Model`

Wenn der Käufer auf die Dropdown-Liste Modell klickt, enthält die Kopfzeile des API-Aufrufs `AC-Policy-Model`, die so konfiguriert ist, dass nur Produkte angezeigt werden, die für die `AC-Policy-Model` spezifisch sind.

### HTTP-Header-Trigger mit mehreren Werten {#multi-value-http-header-triggers}

Eine Trigger-Richtlinie, die den `HTTP_HEADER` Transport-Typ verwendet, kann mehrere Werte in einer Kopfzeile empfangen. Die Werte müssen durch Kommas getrennt werden und der Filteroperator muss `IN` sein. Jeder Wert wird als zulässige Übereinstimmung behandelt. Die Werte werden mit `OR` Semantik ausgewertet.

Beispiel: ein Richtlinienfilter, der `IN` mit der folgenden Kopfzeile verwendet:

```
AC-Policy-Vehicle: UNIVERSAL,veh-bolt-mammoth-limited-2025
```

Sucht Produkte, deren `vehicle` entweder `UNIVERSAL` oder `veh-bolt-mammoth-limited-2025` ist.

Ein Filteroperator von `EQUALS`, `GREATER_THAN_EQUAL` oder `LESS_THAN_EQUAL` wird hingegen mit einem Validierungsfehler zurückgewiesen.

#### Hinweise zur Syntax

- Der Kopfzeilenname entspricht dem von Ihnen konfigurierten Trigger-Namen, z. B. `AC-Policy-Vehicle`.
- Kommas trennen einzelne Werte in der Kopfzeile. Wenn derselbe `AC-Policy-_Name_`-Header mehrmals angezeigt wird, werden seine Werte zu einem einzelnen, durch Kommas getrennten Header-Wert kombiniert
- Der Filteroperator ist `IN`.
- Ein Richtlinienfilter mit **Wertquelle** auf `TRIGGER` gesetzt.
- Ein Trigger, dessen **Transport-Typ** `HTTP_HEADER` ist.

## Richtlinie erstellen

In diesem Abschnitt erstellen Sie eine neue Richtlinie. Die Richtlinie kann entweder **STATIC** oder **TRIGGER** sein.

### Erstellen einer STATISCHEN Richtlinie

1. Klicken Sie im Arbeitsbereich **[!UICONTROL Policies]** auf die Schaltfläche **[!UICONTROL Add Policy]** .

   Eine neue Seite wird geöffnet, auf der Sie die Richtliniendetails ausfüllen können. &#x200B;

1. Geben Sie den Namen der Richtlinie ein, z. B. „Celport Part Categories“.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Add Filter]** .

   Ein Dialogfeld wird geöffnet, in dem Sie Filterdetails hinzufügen können.

1. Fügen Sie die Filterdetails hinzu. Beispiel:

   1. **Attribut** - Geben Sie ein Attribut aus Ihrem Katalog ein. Beispiel: „part_category“. Dieser Name muss genau mit dem Namen des Attributs im Katalog übereinstimmen.
   1. **Operator** - Wählen Sie den Operator. Beispiel: **IN**. &#x200B;
   1. **Wert Source** - Wählen Sie **STATIC** aus. &#x200B;
   1. **Wert** - Geben Sie einen Wert aus der zuvor angegebenen Attributdefinition ein. Geben Sie beispielsweise „Bremsen“ ein, um einen Filter für Bremsenteile zu erstellen.
   1. Drücken Sie die Eingabetaste, um **Wert zu**.

      Wenn die Richtlinie nach mehreren Werten filtern soll, geben Sie jeden Wert separat ein.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Save]** im Dialogfeld Filterdetails . &#x200B;

1. Klicken Sie auf das Menüsymbol (…) Klicken Sie neben dem erstellten Filter auf **Aktivieren**. Von hier aus können Sie **Filter auch**, **Deaktivieren** oder **Löschen**.

   Die Spalte **Status** zeigt ein grünes Symbol und das Wort „Aktiviert“.

1. Klicken Sie auf die Schaltfläche &quot;**[!UICONTROL Save]**&quot;, um die neue Richtlinie zu speichern&#x200B; Wenn die Schaltfläche nicht aktiv ist, stellen Sie sicher, dass der Richtlinienname hinzugefügt wird, indem Sie auf das Stiftsymbol neben &quot;**Richtlinie“**.

1. Um Ihre neue Richtlinie zu überprüfen, klicken Sie auf den Rückwärtspfeil, um zum Arbeitsbereich **[!UICONTROL Policies]** zurückzukehren.

### Erstellen einer TRIGGER-Richtlinie

1. Klicken Sie im Arbeitsbereich **[!UICONTROL Policies]** auf die Schaltfläche **[!UICONTROL Add Policy]** .

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

   Zum Zeitpunkt der Konfiguration verweist der Filter auf den konfigurierten Trigger. Zur Laufzeit liefert die Kopfzeile der API-Anfrage den Wert bzw. die Werte, die von diesem Filter ausgewertet werden.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Save]** im Dialogfeld Filterdetails . &#x200B;

1. Klicken Sie auf das Menüsymbol (…) Klicken Sie neben dem erstellten Filter auf **Aktivieren**. Von hier aus können Sie **Filter auch**, **Deaktivieren** oder **Löschen**.

   Die Spalte **Status** zeigt ein grünes Symbol und das Wort „Aktiviert“.

1. Klicken Sie auf die Schaltfläche &quot;**[!UICONTROL Save]**&quot;, um die neue Richtlinie zu speichern&#x200B; Wenn die Schaltfläche nicht aktiv ist, stellen Sie sicher, dass der Richtlinienname hinzugefügt wird, indem Sie auf das Stiftsymbol neben &quot;**Richtlinie“**.

1. Um Ihre neue Richtlinie zu überprüfen, klicken Sie auf den Rückwärtspfeil, um zum Arbeitsbereich **[!UICONTROL Policies]** zurückzukehren.

Mit diesen Schritten wird die Richtlinie erstellt, die dann mit einer Katalogansicht verknüpft werden kann, um die Produktsichtbarkeit zu steuern.
