---
title: Neue Empfehlung erstellen
description: Erfahren Sie, wie Sie eine Produktempfehlungseinheit erstellen.
exl-id: 1d5f83c4-1613-4236-9d98-d455f45a47da
TQID: https://experienceleague.adobe.com/K3cKFg-m22bUzlupyhsHgDVxaJka7xhOvFnOt8wDdII
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
    internal-label: Behavioral data
  - id: eb30f47f-d87a-400f-8f78-63ce7979ff56
    internal-label: Machine learning
source-git-commit: b8dd0e31a1deac03b03bfeb90a09761b637e0a40
workflow-type: tm+mt
source-wordcount: '1463'
ht-degree: 0%
---
# Neue Empfehlung erstellen

Wenn Sie eine Empfehlung erstellen, erstellen Sie eine _Empfehlungseinheit_ oder ein Widget, das das empfohlene Produkt (_)_.

![Empfehlungseinheit](assets/unit.png)
_Empfehlungseinheit_

Wenn Sie die Empfehlungseinheit aktivieren, beginnt Adobe Commerce mit der [Datenerfassung](workspace.md) um Impressionen, Ansichten, Klicks usw. zu messen. In der [!DNL Product Recommendations] Tabelle werden die Metriken für jede Empfehlungseinheit angezeigt, damit Sie fundierte Geschäftsentscheidungen treffen können.

>[!NOTE]
>
>Metriken für Produktempfehlungen sind für Luma-Storefronts optimiert. Wenn Ihre Storefront nicht auf Luma basiert, hängt die Art und Weise, wie die Metriken Daten verfolgen, davon ab, wie Sie [die Ereigniserfassung implementieren](events.md).

1. Wechseln Sie in der _Admin_-Seitenleiste zu **Marketing** > _Promotions_ > **Produktempfehlungen**, um den _Produktempfehlungen_ anzuzeigen.

1. Geben Sie [&#x200B; „Store-](https://experienceleague.adobe.com/en/docs/commerce-admin/start/setup/websites-stores-views)&quot; an, in der die Empfehlungen angezeigt werden sollen.

   >[!NOTE]
   >
   > Empfehlungseinheiten von Page Builder müssen in der standardmäßigen Store-Ansicht erstellt werden, können dann aber überall verwendet werden. Weitere Informationen zum Erstellen von Produktempfehlungen mit Page Builder finden Sie unter [Inhalt hinzufügen - Produktempfehlungen](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations).

1. Klicken Sie **Empfehlung erstellen**.

1. Geben _im Abschnitt &quot;_ benennen“ einen beschreibenden Namen für die interne Referenz ein, z. B. `Home page most popular`.

1. Wählen _im Abschnitt &quot;_ auswählen“ aus den folgenden Optionen die Seite aus, auf der die Empfehlung angezeigt werden soll:

   >[!NOTE]
   >
   > Produktempfehlungen werden auf der Warenkorbseite nicht unterstützt, wenn Ihr Store so konfiguriert ist, dass [die Warenkorbseite sofort nach dem Hinzufügen eines Produkts zum Warenkorb angezeigt wird](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration).

   * Startseite
   * Kategorie
   * Produktdetails
   * Warenkorb
   * Bestätigung
   * [Page Builder](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations)

   Sie können für jeden Seitentyp bis zu 50 aktive Empfehlungseinheiten erstellen. Der Seitentyp wird ausgegraut, wenn das Limit erreicht ist.

   ![Empfehlungsname und -seite](assets/create-recommendation.png)
   _Empfehlungsname und Seitenplatzierung_

1. Geben _im Abschnitt „Empfehlungstyp auswählen_ den [Empfehlungstyp“ an](type.md) den Sie auf der ausgewählten Seite anzeigen möchten. Bei einigen Seiten ist [Platzierung](placement.md) von Empfehlungen auf bestimmte Typen beschränkt.

1. Geben Sie im Abschnitt _Storefront_ Anzeigebezeichnung) den [Titel](placement.md#recommendation-labels) ein, der für Ihre Einkäufer sichtbar ist, z. B. „Topverkäufe“.

1. Stellen Sie im Bereich _Anzahl der Produkte auswählen_ mit dem Schieberegler ein, wie viele Produkte Sie in der Empfehlungseinheit anzeigen möchten.

   Der Standardwert ist `5` mit einem Maximum von `20`.

1. Geben _im Abschnitt „Platzierung auswählen_ den Ort an, an dem die Empfehlungseinheit auf der Seite angezeigt werden soll.

   * Am Ende des Hauptinhalts
   * Am Anfang des Hauptinhalts

1. (Optional) Um die Reihenfolge der Empfehlungen zu ändern, wählen Sie die Zeilen in der Tabelle _Position auswählen“ aus und verschieben_ sie.

   Im _Position wählen_ werden alle Empfehlungen angezeigt, die für den ausgewählten Seitentyp erstellt wurden (falls vorhanden).

   ![Reihenfolge der Empfehlungen](assets/create-recommendation-select-placement.png)
   _Empfehlungsreihenfolge auf Seite_

1. (Optional) Um zu steuern, welche Produkte in der Empfehlungseinheit angezeigt werden, [&#x200B; Sie &#x200B;](filters.md) Abschnitt _Filter_ Filter.

   ![Empfehlungsfilter](assets/create-recommendation-filter-products.png)
   _Recommendations-Produktfilter_

1. Klicken Sie abschließend auf eine der folgenden Optionen:

   * **Als Entwurf speichern**, um die Empfehlungseinheit später zu bearbeiten. Sie können den Seitentyp oder Empfehlungstyp für eine Empfehlungseinheit in einem Entwurfsstatus nicht ändern.

   * **Aktivieren**, um die Empfehlungseinheit in Ihrer Storefront zu aktivieren.

>[!IMPORTANT]
>
>Einige Browser blockieren möglicherweise wichtige Skripte, die verhindern, dass Produktempfehlungen erwartungsgemäß funktionieren.

## Bereitschaftsindikatoren

Bereitschaftsindikatoren zeigen, welche Empfehlungstypen mit Ihren verfügbaren Katalog- und Verhaltensdaten am besten abschneiden. Verwenden Sie sie, um Ereignisprobleme oder unzureichenden Traffic zu identifizieren, um einen Empfehlungstyp auszufüllen.

Bereitschaftsindikatoren werden in zwei Kategorien unterteilt: [statisch](#static-based) und [dynamisch](#dynamic-based). Statische Empfehlungen verwenden nur Katalogdaten. Dynamische Empfehlungen verwenden die Verhaltensdaten der Käufer, um Modelle für maschinelles Lernen zu trainieren, personalisierte Empfehlungen zu generieren und den Bereitschaftswert jeder Empfehlung zu berechnen.

### Berechnen der Bereitschaftsindikatoren

Die Bereitschaftsindikatoren geben an, wie viel das Modell trainiert wird. Die Indikatoren hängen von den erfassten Ereignistypen, der Breite der mit ihnen interagierten Produkte und der Größe des Katalogs ab.

Der Bereitschaftsindikator-Prozentsatz schätzt den Anteil der Produkte, die für einen bestimmten Empfehlungstyp empfohlen werden könnten. Er wird anhand der Kataloggröße, des Interaktionsvolumens und des Prozentsatzes der SKUs berechnet, die die relevanten Ereignisse innerhalb eines definierten Zeitfensters aufzeichnen. Beispielsweise können Bereitschaftsindikatoren während des Traffics an Feiertagen höher sein als während normaler Traffic-Zeiten.

Aufgrund dieser Variablen kann der Bereitschaftsindikator in Prozent schwanken. Dies erklärt, warum Empfehlungstypen zwischen der „Bereitstellungs-Bereitschaft“ schwanken.

Die Bereitschaftsindikatoren werden anhand von zwei Faktoren berechnet:

* Ausreichende Größe des Ergebnissatzes: Werden in den meisten Szenarien genügend Ergebnisse zurückgegeben, um die Verwendung von [Backup-Empfehlungen](events.md#backuprecs) zu vermeiden?

* Stellen die zurückgesandten Produkte eine Vielzahl von Produkten aus Ihrem Katalog dar? Dadurch wird sichergestellt, dass die Empfehlungen auf Ihrer Site nicht auf eine kleine Untergruppe von Produkten beschränkt sind.

Auf der Grundlage der oben genannten Faktoren wird ein Bereitschaftswert wie folgt berechnet und angezeigt:

* 75 % oder mehr bedeutet, dass die für diesen Empfehlungstyp vorgeschlagenen Empfehlungen von großer Relevanz sein werden.
* Mindestens 50 % bedeutet, dass die für diesen Empfehlungstyp vorgeschlagenen Empfehlungen weniger relevant sind.
* Weniger als 50 % bedeutet, dass die für diesen Empfehlungstyp vorgeschlagenen Empfehlungen möglicherweise nicht relevant sind. In diesem Fall werden [Sicherungsempfehlungen](events.md#backuprecs) verwendet.

Erfahren Sie mehr [warum Bereitschaftsindikatoren möglicherweise niedrig sind](#what-to-do-if-the-readiness-indicator-percent-is-low).

### Statisch

Die folgenden Empfehlungstypen sind statisch, da sie nur Katalogdaten benötigen. Es werden keine Verhaltensdaten verwendet.

* _Ähnliche Themen_
* _Visuelle Ähnlichkeit_

### Dynamisch basiert

Die folgenden Empfehlungstypen sind dynamisch, da sie Storefront-Verhaltensdaten verwenden.

Verhaltensdaten der Storefront für die letzten sechs Monate:

* _hat dies angezeigt, hat dies angezeigt_
* _Das hier angesehen, das gekauft_
* _Habe das gekauft, hat das gekauft_
* _Empfohlen für Sie_

Verhaltensdaten der Storefront für die letzten sieben Tage:

* _Am häufigsten angezeigt_
* _Am häufigsten gekauft_
* _Am häufigsten zum Warenkorb hinzugefügt_
* _Trend_
* _Ansichts-/Kaufkonvertierung_
* _Zum Warenkorb konvertieren_

Aktuelle Verhaltensdaten der Käufer (nur Ansichten):

* _Kürzlich angesehen_

### Fortschritt visualisieren

Der Schulungsfortschritt jedes Empfehlungstyps lässt sich im Abschnitt _Empfehlungstyp auswählen_ im Folgenden für jeden Empfehlungstyp visuell darstellen.

![Empfehlungstyp](assets/create-recommendation-select-type.png)
_Empfehlungstyp_

>[!NOTE]
>
>Die Indikatoren werden möglicherweise nie 100 % erreichen.

Der Bereitschaftsprozentsatz für katalogbasierte Empfehlungstypen ändert sich in der Regel nur wenig, da Kataloge relativ stabil sind. Im Gegensatz dazu kann sich der Bereitschaftsprozentsatz für Empfehlungstypen, die auf Käuferverhaltensdaten basieren, häufig mit der täglichen Käuferaktivität ändern.

#### Was zu tun ist, wenn der Bereitschaftsindikator in Prozent niedrig ist

Ein niedriger Bereitschaftsprozentsatz zeigt an, dass nicht viele Produkte aus Ihrem Katalog für die Aufnahme in Empfehlungen für diesen Empfehlungstyp geeignet sind. Das bedeutet, dass eine hohe Wahrscheinlichkeit besteht, dass [Sicherungsempfehlungen](events.md#backup-recommendations) zurückgegeben werden, wenn Sie diesen Empfehlungstyp ohnehin bereitstellen.

>[!IMPORTANT]
>
>Alle SKUs mit Leerzeichen können die Relevanz der Empfehlung reduzieren und sollten vermieden werden.

Im Folgenden sind mögliche Gründe und Lösungen für häufige Bewertungen der geringen Bereitschaft aufgeführt:

* **Statisch-basiert** - Fehlende Katalogdaten für die anzeigbaren Produkte führen zu niedrigen Prozentsätzen für diese Indikatoren. Wenn sie niedriger sind als erwartet, kann dieses Problem durch eine vollständige Synchronisierung behoben werden.
* **Dynamisch-basiert** - Die folgenden Faktoren führen bei dynamischen Indikatoren zu niedrigen Prozentsätzen:

  * Fehlende Felder in den erforderlichen [Storefront-Ereignissen](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations) für die entsprechenden Empfehlungstypen (requestId, Produktkontext usw.)
  * Geringer Traffic im Store, sodass das Volumen der Verhaltensereignisse, die wir erhalten, gering ist.
  * Die Vielfalt der Verhaltensereignisse der Storefront in verschiedenen Produkten in Ihrem Store ist gering. Wenn beispielsweise nur zehn Prozent Ihrer Produkte die meiste Zeit angesehen oder gekauft werden, sind die entsprechenden Bereitschaftsindikatoren niedrig.

## Recommendations-Vorschau {#preview}

Das Bedienfeld _Empfohlene Produktvorschau_ ist immer mit einer Auswahl von Beispielprodukten verfügbar, die in der Empfehlungseinheit angezeigt werden, wenn sie in der Storefront bereitgestellt werden.

Um eine Empfehlung zu testen, wenn Sie in einer Nicht-Produktionsumgebung arbeiten, können Sie Empfehlungsdaten aus einer ([&#x200B; Quelle) &#x200B;](settings.md). Händler können so mit Regeln experimentieren und eine Vorschau der Recommendations anzeigen, bevor sie sie in der Produktion bereitstellen.

| Feld | Beschreibung |
|---|---|
| Name | Der Name des Produkts. |
| SKU | Die dem Produkt zugewiesene Lagerhaltungseinheit |
| Preis | Der Preis des Produkts. |
| Ergebnistyp | Primär - gibt an, dass genügend Schulungsdaten erfasst wurden, um eine Empfehlung anzuzeigen.<br />Backup - gibt an, dass nicht genügend Schulungsdaten erfasst wurden, sodass eine Backup-Empfehlung zum Ausfüllen des Slots verwendet wird. Unter [Verhaltensdaten](events.md) erfahren Sie mehr über Modelle für maschinelles Lernen und Empfehlungen für Backups. |

Um anzuzeigen, welche Produkte eine Empfehlungseinheit in Echtzeit enthält, experimentieren Sie beim Erstellen mit dem Seitentyp, dem Empfehlungstyp und den Filtern. Konfigurieren Sie dann das Gerät je nach den zurückgegebenen Produkten entsprechend Ihren Geschäftsanforderungen.

Wenn mehrere Empfehlungseinheiten auf derselben Seite bereitgestellt werden, verwendet Adobe Commerce [Filter](#filters.md), um doppelte Produkte aus den angezeigten Empfehlungen zu entfernen. Daher kann das Vorschaufenster einen anderen Satz von Produkten anzeigen als die Storefront.

>[!NOTE]
>
> Sie können keine Vorschau des `Recently viewed` Empfehlungstyps anzeigen, da die Daten nicht in der Admin-Instanz verfügbar sind.
