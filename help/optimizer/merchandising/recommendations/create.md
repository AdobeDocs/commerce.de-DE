---
title: Empfehlungen erstellen und verwalten
description: Erfahren Sie, wie Sie Empfehlungen erstellen und verwalten.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 7cee0a37-4d43-4ee9-889d-9a0ab9684bb8
source-git-commit: 0b8e0222a1de1c425964f9f54294d7e0435a26d8
workflow-type: tm+mt
source-wordcount: '1360'
ht-degree: 0%

---

# Empfehlungen erstellen und verwalten

Wenn Sie eine Empfehlung erstellen, erstellen Sie eine _Empfehlungseinheit_ oder ein Widget, das das empfohlene Produkt (_)_.

![Empfehlungseinheit](../../assets/unit.png)
_Empfehlungseinheit_

Wenn Sie die Empfehlungseinheit aktivieren, beginnt Adobe Commerce mit der [Datenerfassung](../../manage-results/recommendation-performance.md) um Impressionen, Ansichten, Klicks usw. zu messen. Die Tabelle Recommendations zeigt die Metriken für jede Empfehlungseinheit an, die Ihnen bei fundierten Geschäftsentscheidungen hilft.

1. Adobe Commerce Optimizer Wechseln Sie in der Seitenleiste von __ zu _Merchandising_ > **Recommendations**, um den Arbeitsbereich _Recommendations_ anzuzeigen.

1. Klicken Sie **Empfehlung erstellen**.

1. Geben _im Abschnitt &quot;_ benennen“ einen beschreibenden Namen für die interne Referenz ein, z. B. `Home page most popular`.

1. Geben Sie im Abschnitt _Empfehlungstyp auswählen_ den [Empfehlungstyp) an](types.md) den Sie basierend auf Ihrer Strategie verwenden möchten.

1. Geben Sie im Abschnitt _Storefront_ Anzeigebezeichnung) den [Titel](best-practice.md#recommendation-labels) ein, der für Ihre Einkäufer sichtbar ist, z. B. „Topverkäufe“.

1. Stellen Sie im Bereich _Anzahl der Produkte auswählen_ mit dem Schieberegler ein, wie viele Produkte Sie in der Empfehlungseinheit anzeigen möchten.

   Der Standardwert ist `5` mit einem Maximum von `20`.

1. (Optional) Im Abschnitt _Filter_ können Sie [Filter anwenden](filters.md) um zu steuern, welche Produkte in der Empfehlungseinheit angezeigt werden.

1. Klicken Sie abschließend auf eine der folgenden Optionen:

   - **Als Entwurf speichern**, um die Empfehlungseinheit später zu bearbeiten. Sie können den Empfehlungstyp für eine Empfehlungseinheit im Entwurfsstatus nicht ändern.

   - **Aktivieren**, um die Empfehlungseinheit in Ihrer Storefront zu aktivieren.

1. Wenn Sie dazu aufgefordert werden, kopieren Sie die Recommendations-ID. Verwenden Sie diese ID, um zu ermitteln, welche Empfehlungseinheit in der Dropdown-Liste „Empfehlung“ in Ihrer Edge Delivery Services-Storefront verwendet wird.

>[!IMPORTANT]
>
>Einige Browser blockieren möglicherweise wichtige Skripte, die verhindern, dass Recommendations erwartungsgemäß funktioniert.

## Verwalten vorhandener Empfehlungen

Sie können eine vorhandene Empfehlung bearbeiten, deaktivieren oder löschen.

1. Navigieren Sie in der Seitenleiste _0}Adobe Commerce Optimizer&quot; zu_ Merchandising _>_ Recommendations **.**

1. Wählen Sie die Empfehlung aus, die Sie ändern möchten.

1. Klicken Sie auf den (![Mehr-Selektor](../../assets/btn-more.png)) mehr-Selektor.

1. Im Menü können Sie **Empfehlung**, **Löschen** oder **Bearbeiten**. Wenn Sie **Bearbeiten** auswählen, können Sie die folgenden Einstellungen nach Bedarf anpassen:

   - Name der Empfehlung
   - Storefront-Bezeichnung
   - Anzahl der Produkte
   - Produkte filtern

   Der Empfehlungstyp kann nicht geändert werden.

1. Klicken Sie abschließend auf **Änderungen speichern**.

## Bereitschaftsindikatoren

Bereitschaftsindikatoren zeigen, welche Empfehlungstypen basierend auf den verfügbaren Katalog- und Verhaltensdaten am besten abschneiden. Sie können auch Bereitschaftsindikatoren verwenden, um festzustellen, ob Probleme mit [Ereigniserfassung](../../setup/events/overview.md) vorliegen oder ob nicht genügend Traffic vorhanden ist, um den Empfehlungstyp auszufüllen.

Bereitschaftsindikatoren werden entweder in [statisch-basiert](#static-based) oder [dynamisch-](#dynamic-based) kategorisiert. Verwenden Sie nur statische Katalogdaten, während dynamische Verhaltensdaten von Ihren Kunden verwendet werden. Diese Verhaltensdaten werden verwendet, um [Modelle für maschinelles Lernen](../../setup/events/overview.md) zu trainieren, um personalisierte Empfehlungen zu erstellen und ihren Bereitschaftswert zu berechnen.

### Berechnen der Bereitschaftsindikatoren

Die Bereitschaftsindikatoren geben an, wie viel das Modell trainiert wird. Die Indikatoren hängen von den erfassten Ereignistypen, der Breite der mit ihnen interagierten Produkte und der Größe des Katalogs ab.

Der Bereitschaftsindikator-Prozentsatz wird aus einer Berechnung abgeleitet, die angibt, wie viele Produkte je nach Empfehlungstyp empfohlen werden können. Statistiken werden auf Produkte angewendet, die auf der Gesamtgröße des Katalogs, dem Volumen der Interaktionen (wie Ansichten, Klicks, Warenkorb-Aufnahmen) und dem Prozentsatz der SKUs basieren, die diese Ereignisse innerhalb eines bestimmten Zeitfensters registrieren. So können die Bereitschaftsindikatoren beispielsweise während der Traffic-Zeit an Feiertagen höhere Werte anzeigen als zu Zeiten normalen Volumens.

Aufgrund dieser Variablen kann der Bereitschaftsindikator in Prozent schwanken. Dies erklärt, warum Sie möglicherweise feststellen, dass Empfehlungstypen immer häufiger „bereit zur Bereitstellung“ sind.

Die Bereitschaftsindikatoren werden auf der Grundlage mehrerer Faktoren berechnet:

- Ausreichende Größe des Ergebnissatzes: Werden in den meisten Szenarien genügend Ergebnisse zurückgegeben, um die Verwendung von [Backup-Empfehlungen](../../setup/events/overview.md#backuprecs) zu vermeiden?
- Ausreichende Vielfalt der Ergebnismengen: Stellen die zurückgegebenen Produkte eine Vielzahl von Produkten aus Ihrem Katalog dar? Das Ziel bei diesem Faktor ist zu vermeiden, dass eine Minderheit von Produkten die einzigen empfohlenen Elemente auf der Website ist.

Auf der Grundlage der oben genannten Faktoren wird ein Bereitschaftswert wie folgt berechnet und angezeigt:

- 75 % oder mehr bedeutet, dass die für diesen Empfehlungstyp vorgeschlagenen Empfehlungen von großer Relevanz sein werden.
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

Der Bereitschaftsindikator Prozent für Empfehlungstypen, die von Katalogdaten abhängen, ändert sich nicht sehr stark, da sich der Katalog des Händlers nicht oft ändert. Der Bereitschaftsindikator für Prozentsätze der Empfehlungstypen, die auf den Verhaltensdaten der Käufer basieren, kann sich jedoch je nach täglicher Käuferaktivität häufig ändern.

#### Was zu tun ist, wenn der Bereitschaftsindikator in Prozent niedrig ist

Ein niedriger Bereitschaftsprozentsatz zeigt an, dass nicht viele Produkte aus Ihrem Katalog für die Aufnahme in Empfehlungen für diesen Empfehlungstyp geeignet sind. Das bedeutet, dass eine hohe Wahrscheinlichkeit besteht, dass [Sicherungsempfehlungen](../../setup/events/overview.md#backuprecs) zurückgegeben werden, wenn Sie diesen Empfehlungstyp ohnehin bereitstellen.

>[!IMPORTANT]
>
>_Bundle_, _grouped_ und benutzerdefinierte Produkttypen werden nicht unterstützt. Wenn Ihr Katalog eine große Anzahl dieser Produktarten enthält, können Sie mit einer niedrigen Bereitschaft rechnen. Darüber hinaus können alle SKUs mit Leerzeichen die Relevanz der Empfehlungen reduzieren und sollten vermieden werden.

Im Folgenden sind mögliche Gründe und Lösungen für häufige Bewertungen der geringen Bereitschaft aufgeführt:

- **Statisch-basiert** - Niedrige Prozentsätze für diese Indikatoren können durch fehlende Katalogdaten für die anzeigbaren Produkte verursacht werden. Wenn sie niedriger sind als erwartet, kann dieses Problem durch eine vollständige Synchronisierung behoben werden.
- **Dynamisch-basiert** - Niedrige Prozentsätze für dynamisch-basierte Indikatoren können durch Folgendes verursacht werden:

   - Fehlende Felder in den erforderlichen [Storefront-Ereignissen](../../setup/events/overview.md) für die entsprechenden Empfehlungstypen (requestId, Produktkontext usw.)
   - Geringer Traffic im Store, sodass das Volumen der Verhaltensereignisse, die wir erhalten, gering ist.
   - Die Vielfalt der Verhaltensereignisse der Storefront in verschiedenen Produkten in Ihrem Store ist gering. Wenn beispielsweise nur zehn Prozent Ihrer Produkte die meiste Zeit angesehen oder gekauft werden, sind die entsprechenden Bereitschaftsindikatoren niedrig.

## Recommendations-Vorschau

>[!IMPORTANT]
>
>Diese Funktion ist noch nicht verfügbar.

Das Bedienfeld _Empfohlene Produktvorschau_ ist immer verfügbar mit einer Auswahl von Produkten, die in der Empfehlungseinheit angezeigt werden können, wenn sie in der Storefront bereitgestellt werden.

Um eine Empfehlung beim Arbeiten in einer Nicht-Produktionsumgebung zu testen, können Sie Empfehlungsdaten aus einer anderen Quelle abrufen. Händler können so mit Regeln experimentieren und eine Vorschau der Recommendations anzeigen, bevor sie sie in der Produktion bereitstellen.

| Feld | Beschreibung |
|---|---|
| -Name | Der Name des Produkts. |
| SKU | Die dem Produkt zugewiesene Lagerhaltungseinheit |
| Preis | Der Preis des Produkts. |
| Ergebnistyp | Primär - gibt an, dass genügend Schulungsdaten erfasst wurden, um eine Empfehlung anzuzeigen.<br />Backup - gibt an, dass nicht genügend Schulungsdaten erfasst wurden, sodass eine Backup-Empfehlung zum Ausfüllen des Slots verwendet wird. Unter [Verhaltensdaten](../../setup/events/overview.md) erfahren Sie mehr über Modelle für maschinelles Lernen und Empfehlungen für Backups. |

Experimentieren Sie beim Erstellen Ihrer Empfehlungseinheit mit dem Empfehlungstyp und den Filtern, um sofortiges Echtzeit-Feedback zu den einzuschließenden Produkten zu erhalten. Sobald Sie verstehen, welche Produkte angezeigt werden, können Sie die Empfehlungseinheit an Ihre Geschäftsanforderungen anpassen.

[!DNL Adobe Commerce Optimizer] [Filter](filters.md) Empfehlungen, um die Anzeige doppelter Produkte zu vermeiden, wenn mehrere Empfehlungseinheiten auf einer Seite bereitgestellt werden. Daher können sich die Produkte, die im Vorschaubereich angezeigt werden, von denen unterscheiden, die in der Storefront angezeigt werden.
