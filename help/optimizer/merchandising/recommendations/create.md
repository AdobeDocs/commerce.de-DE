---
title: Empfehlungen erstellen und verwalten
description: Erfahren Sie, wie Sie Empfehlungen erstellen und verwalten.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 7cee0a37-4d43-4ee9-889d-9a0ab9684bb8
source-git-commit: 3d748e83e07a16e58c0c55f12a6c0ad40bbfdead
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 0%

---

# Empfehlungen erstellen und verwalten

Wenn Sie eine Empfehlung erstellen, erstellen Sie eine _Empfehlungseinheit_ oder ein Widget, das das empfohlene Produkt (_)_.

![Empfehlungseinheit](../../assets/unit.png)
_Empfehlungseinheit_

Wenn Sie die Empfehlungseinheit aktivieren, beginnt Adobe Commerce mit der [Datenerfassung](../../manage-results/recommendation-performance.md) um Impressionen, Ansichten, Klicks usw. zu messen. Die Tabelle Recommendations zeigt die Metriken für jede Empfehlungseinheit an, die Ihnen bei fundierten Geschäftsentscheidungen hilft.

1. Wechseln Sie in der _[!DNL Adobe Commerce Optimizer]_&#x200B;Seitenleiste zu_ Merchandising _>**Recommendations**, um den_ Recommendations _-Arbeitsbereich anzuzeigen.

1. Wählen **im Feld** Katalogansicht“ die Katalogansicht aus, in der die Empfehlung verfügbar sein soll. Weitere Informationen über [Verwenden von Katalogansichten für Recommendations](../../manage-results/recommendation-performance.md#select-catalog-view).

   >[!IMPORTANT]
   >
   >Diese Funktion befindet sich derzeit in der Betaphase.

1. Klicken Sie **Empfehlung erstellen**.

   Die erstellte Empfehlung ist in der zuvor ausgewählten Katalogansicht verfügbar.

1. Geben _im Abschnitt &quot;_ benennen“ einen beschreibenden Namen für die interne Referenz ein, z. B. `Home page most popular`.

1. Geben Sie im Abschnitt _Empfehlungstyp auswählen_ den [Empfehlungstyp) an](types.md) den Sie basierend auf Ihrer Strategie verwenden möchten.

1. Geben Sie im Abschnitt _Storefront_ Anzeigebezeichnung) den [Titel](best-practice.md#recommendation-labels) ein, der für Ihre Einkäufer sichtbar ist, z. B. „Topverkäufe“.

1. Stellen Sie im Bereich _Anzahl der Produkte auswählen_ mit dem Schieberegler ein, wie viele Produkte Sie in der Empfehlungseinheit anzeigen möchten.

   Der Standardwert ist `5` mit einem Maximum von `20`.

1. (Optional) Im Abschnitt _Filter_ können Sie [Filter anwenden](filters.md) um zu steuern, welche Produkte in der Empfehlungseinheit angezeigt werden.

1. Verwenden Sie das Bedienfeld _Empfohlene Produktvorschau_, um besser zu verstehen, wie Filter beeinflussen, welche Produkte in der Empfehlungseinheit angezeigt werden. Erfahren Sie mehr über das [Vorschau von Recommendations](#preview-recommendations).

1. Klicken Sie abschließend auf eine der folgenden Optionen:

   - **Als Entwurf speichern**, um die Empfehlungseinheit später zu bearbeiten. Sie können den Empfehlungstyp für eine Empfehlungseinheit im Entwurfsstatus nicht ändern.

   - **Aktivieren**, um die Empfehlungseinheit in Ihrer Storefront zu aktivieren.

   Ihre Empfehlung wird im Arbeitsbereich Recommendations angezeigt. Um Ihre Empfehlung in Ihrer Storefront zu verwenden, müssen Sie die „Recommendations[ID“ &#x200B;](#get-recommendation-id).

>[!NOTE]
>
>Sie können bis zu 50 aktive Empfehlungseinheiten erstellen. Weitere Informationen finden [&#x200B; unter &#x200B;](../../boundaries-limits.md) und Grenzen .

>[!IMPORTANT]
>
>Einige Browser blockieren möglicherweise wichtige Skripte, die verhindern, dass Recommendations erwartungsgemäß funktioniert.

## Recommendations in der Vorschau anzeigen

Das Bedienfeld _Empfohlene Produktvorschau_ ist immer verfügbar mit einer Auswahl von Produkten, die in der Empfehlungseinheit angezeigt werden können, wenn sie in der Storefront bereitgestellt werden.

![Recommendations-Vorschau](../../assets/rec-preview.png)

Um eine Empfehlung beim Arbeiten in einer Nicht-Produktionsumgebung zu testen, können Sie Empfehlungsdaten aus einer anderen Quelle abrufen. Händler können so mit Regeln experimentieren und eine Vorschau der Recommendations anzeigen, bevor sie sie in der Produktion bereitstellen.

| Feld | Beschreibung |
|---|---|
| Katalogansicht |
| -Name | Der Name des Produkts. |
| SKU | Die dem Produkt zugewiesene Lagerhaltungseinheit |
| Preis | Der Preis des Produkts. |
| Ergebnistyp | Primär - Gibt an, dass genügend Schulungsdaten gesammelt wurden, um eine Empfehlung anzuzeigen.<br />Backup - Gibt an, dass nicht genügend Schulungsdaten erfasst wurden und daher eine Sicherungsempfehlung für das Füllen des Slots verwendet wird. Unter [Verhaltensdaten](../../setup/events/overview.md) erfahren Sie mehr über Modelle für maschinelles Lernen und Empfehlungen für Backups. |

Experimentieren Sie beim Erstellen Ihrer Empfehlungseinheit mit dem Empfehlungstyp und den Filtern, um sofortiges Echtzeit-Feedback zu den einzuschließenden Produkten zu erhalten. Sobald Sie verstehen, welche Produkte angezeigt werden, können Sie die Empfehlungseinheit an Ihre Geschäftsanforderungen anpassen.

[!DNL Adobe Commerce Optimizer] [Filter](filters.md) Empfehlungen, um die Anzeige doppelter Produkte zu vermeiden, wenn mehrere Empfehlungseinheiten auf einer Seite bereitgestellt werden. Daher können sich die Produkte, die im Vorschaubereich angezeigt werden, von denen unterscheiden, die in der Storefront angezeigt werden.

Bei Setups mit mehreren Storefronts, mehreren Sprachen oder mehreren Marken können Sie konfigurieren, ob jede Empfehlung für alle Katalogansichten (global) oder für eine einzelne [Katalogansicht) &#x200B;](../../setup/catalog-view.md). Erfahren Sie mehr darüber, wie [die Katalogansicht festlegen](../../manage-results/recommendation-performance.md#select-catalog-view) wenn Sie mit Recommendations arbeiten.

## Recommendations-ID abrufen

Nachdem Sie eine Empfehlung erstellt haben, müssen Sie deren ID abrufen, um die Empfehlungseinheit auf Ihrer Storefront zu implementieren.

1. Wählen Sie auf **Seite** die Empfehlung aus.

1. Klicken Sie auf das Informationssymbol (![Infosymbol](../../assets/info-icon.png)) neben dem Namen der Empfehlung.

   Die **„Details der Empfehlungseinheit** wird angezeigt.

   ![Empfehlungs-ID abrufen](../../assets/get-rec-id.png)

1. Kopieren Sie **Abschnitt** Recommendations-ID“ die ID.

1. Verwenden Sie diese ID, um das [Empfehlungs-Dropdown-Menü](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/blocks/product-recommendations/) in Ihrer Edge Delivery Services-Storefront zu konfigurieren.

## Verwalten vorhandener Empfehlungen

Sie können eine vorhandene Empfehlung bearbeiten, deaktivieren oder löschen.

1. Navigieren Sie in der _[!DNL Adobe Commerce Optimizer]_&#x200B;Seitenleiste zu_ Merchandising _>**Recommendations**.

1. Wählen Sie die Empfehlung aus, die Sie ändern möchten.

1. Klicken Sie auf den (![Mehr-Selektor](../../assets/btn-more.png)) mehr-Selektor.

1. Im Menü können Sie **Empfehlung**, **Löschen** oder **Bearbeiten**. Wenn Sie **Bearbeiten** auswählen, können Sie die folgenden Einstellungen nach Bedarf anpassen:

   - Name der Empfehlung
   - Storefront-Bezeichnung
   - Anzahl der Produkte
   - Produkte filtern

   Sie können den Empfehlungstyp oder die Katalogansicht nicht ändern. Die Katalogansicht wird beim Erstellen der Empfehlung festgelegt. Weitere Informationen finden Sie unter [Katalogansicht auswählen](../../manage-results/recommendation-performance.md#select-catalog-view).

1. Klicken Sie abschließend auf **Änderungen speichern**.

## Bereitschaftsindikatoren

Bereitschaftsindikatoren zeigen, welche Empfehlungstypen basierend auf den verfügbaren Katalog- und Verhaltensdaten am besten abschneiden. Sie können Ihnen auch dabei helfen, potenzielle Probleme mit der [Ereigniserfassung“ zu identifizieren &#x200B;](../../setup/events/overview.md) festzustellen, ob ein Empfehlungstyp nicht genügend Traffic erhält, um Ergebnisse zu generieren.

Bereitschaftsindikatoren werden entweder in [statisch-basiert](#static-based) oder [dynamisch-](#dynamic-based) kategorisiert. Verwenden Sie nur statische Katalogdaten, während dynamische Verhaltensdaten von Ihren Kunden verwendet werden. Diese Verhaltensdaten werden verwendet, um [Modelle für maschinelles Lernen](../../setup/events/overview.md) zu trainieren, um personalisierte Empfehlungen zu erstellen und ihren Bereitschaftswert zu berechnen.

### Berechnen der Bereitschaftsindikatoren

Die Bereitschaftsindikatoren geben an, wie viel das Modell trainiert wird. Die Indikatoren hängen von den erfassten Ereignistypen, der Breite der mit ihnen interagierten Produkte und der Größe des Katalogs ab.

Der Bereitschaftsindikator-Prozentsatz wird aus einer Berechnung abgeleitet, die angibt, wie viele Produkte je nach Empfehlungstyp empfohlen werden können. Statistiken werden auf Produkte angewendet, die auf der Gesamtgröße des Katalogs, dem Volumen der Interaktionen (wie Ansichten, Klicks, Warenkorb-Aufnahmen) und dem Prozentsatz der SKUs basieren, die diese Ereignisse innerhalb eines bestimmten Zeitfensters registrieren. So können die Bereitschaftsindikatoren beispielsweise während der Traffic-Zeit an Feiertagen höhere Werte anzeigen als zu Zeiten normalen Volumens.

Aufgrund dieser Variablen kann der Bereitschaftsindikator in Prozent schwanken. Diese Fluktuation erklärt, warum Sie möglicherweise sehen, dass Empfehlungstypen immer häufiger „bereit zur Bereitstellung“ sind.

Die Bereitschaftsindikatoren werden auf der Grundlage mehrerer Faktoren berechnet:

- Ausreichende Größe des Ergebnissatzes: Werden in den meisten Szenarien genügend Ergebnisse zurückgegeben, um die Verwendung von [Backup-Empfehlungen](../../setup/events/overview.md#backuprecs) zu vermeiden?
- Ausreichende Vielfalt der Ergebnismengen: Stellen die zurückgegebenen Produkte eine Vielzahl von Produkten aus Ihrem Katalog dar? Das Ziel bei diesem Faktor ist zu vermeiden, dass eine Minderheit von Produkten die einzigen empfohlenen Elemente auf der Website ist.

Auf der Grundlage der oben genannten Faktoren wird ein Bereitschaftswert wie folgt berechnet und angezeigt:

- 75 % oder mehr bedeutet, dass die für diesen Empfehlungstyp vorgeschlagenen Empfehlungen sehr relevant sind.
- Mindestens 50 % bedeutet, dass die für diesen Empfehlungstyp vorgeschlagenen Empfehlungen weniger relevant sind.
- Weniger als 50 % bedeutet, dass die für diesen Empfehlungstyp vorgeschlagenen Empfehlungen möglicherweise nicht relevant sind. In diesem Fall werden [Sicherungsempfehlungen](../../setup/events/overview.md#backuprecs) verwendet.

Erfahren Sie mehr [warum Bereitschaftsindikatoren möglicherweise niedrig sind](#what-to-do-if-the-readiness-indicator-percent-is-low).

### Statisch

Die folgenden Empfehlungstypen sind statisch, da sie nur Katalogdaten benötigen. Es werden keine Verhaltensdaten verwendet.

- _Ähnliche Themen_

### Dynamisch basiert

Die folgenden Empfehlungstypen sind dynamisch, da sie Storefront-Verhaltensdaten verwenden.

Verhaltensdaten der Storefront für die letzten sechs Monate:

- _hat dies angezeigt, hat dies angezeigt_
- _Das hier angesehen, das gekauft_
- _Habe das gekauft, hat das gekauft_
- _Empfohlen für Sie_

Verhaltensdaten der Storefront für die letzten sieben Tage:

- _Am häufigsten angezeigt_
- _Am häufigsten gekauft_
- _Am häufigsten zum Warenkorb hinzugefügt_
- _Trend_
- _Ansichts-/Kaufkonvertierung_
- _Zum Warenkorb konvertieren_

Aktuelle Verhaltensdaten der Käufer (nur Ansichten):

- _Kürzlich angesehen_

### Fortschritt visualisieren

Der Schulungsfortschritt jedes Empfehlungstyps lässt sich im Abschnitt _Empfehlungstyp auswählen_ im Folgenden für jeden Empfehlungstyp visuell darstellen.

![Empfehlungstyp](../../assets/create-recommendation-select-type.png)
_Empfehlungstyp_

>[!NOTE]
>
>Die Indikatoren werden möglicherweise nie 100 % erreichen.

Der Bereitschaftsindikator für Empfehlungstypen, die von Katalogdaten abhängen, ändert sich nicht sehr, da sich der Katalog des Händlers nur selten ändert. Der Bereitschaftsindikator für Empfehlungstypen, die auf Verhaltensdaten von Käufern basieren, kann sich jedoch je nach täglicher Käuferaktivität häufig ändern.

#### Was zu tun ist, wenn die Bereitschaft niedrig ist

Ein niedriger Bereitschaftsprozentsatz zeigt an, dass nicht viele Produkte aus Ihrem Katalog für die Aufnahme in Empfehlungen für diesen Empfehlungstyp geeignet sind. Das bedeutet, dass eine hohe Wahrscheinlichkeit besteht, dass [Sicherungsempfehlungen](../../setup/events/overview.md#backuprecs) zurückgegeben werden, wenn Sie diesen Empfehlungstyp ohnehin bereitstellen.

>[!IMPORTANT]
>
>_Bundle_, _grouped_ und benutzerdefinierte Produkttypen werden nicht unterstützt. Wenn Ihr Katalog eine große Anzahl dieser Produktarten enthält, können Sie mit einer niedrigen Bereitschaft rechnen. Darüber hinaus können alle SKUs mit Leerzeichen die Relevanz der Empfehlungen reduzieren und sollten vermieden werden.

Im Folgenden sind mögliche Gründe und Lösungen für häufige Bewertungen der geringen Bereitschaft aufgeführt:

- **Statisch-basiert** - Niedrige Prozentsätze für diese Indikatoren können durch fehlende Katalogdaten für die anzeigbaren Produkte verursacht werden. Wenn sie niedriger sind als erwartet, kann dieses Problem durch eine vollständige Synchronisierung behoben werden.
- **Dynamisch-basiert** - Niedrige Prozentsätze für dynamisch-basierte Indikatoren können durch Folgendes verursacht werden:

   - Fehlende Felder in den erforderlichen [Storefront-Ereignissen](../../setup/events/overview.md) für die entsprechenden Empfehlungstypen (requestId, Produktkontext usw.)
   - Geringer Traffic zum Store, sodass nur ein geringes Volumen von empfangenen Verhaltensereignissen vorliegt.
   - Die Vielfalt der Verhaltensereignisse der Storefront in verschiedenen Produkten in Ihrem Store ist gering. Wenn beispielsweise nur zehn Prozent Ihrer Produkte die meiste Zeit angesehen oder gekauft werden, sind die entsprechenden Bereitschaftsindikatoren niedrig.
