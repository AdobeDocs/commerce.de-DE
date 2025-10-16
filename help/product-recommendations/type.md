---
title: Empfehlungstypen
description: Erfahren Sie mehr über die Recommendations, die Sie auf verschiedenen Seiten auf Ihrer Site bereitstellen können.
exl-id: bbb290b0-b50b-43d9-bf71-1813298d5f39
source-git-commit: 67d0b98f3a9317c0db944a176fd99375091a3970
workflow-type: tm+mt
source-wordcount: '1991'
ht-degree: 0%

---

# Empfehlungstypen

Adobe Commerce bietet eine Vielzahl von Empfehlungen, die Sie auf verschiedenen Seiten Ihrer Site bereitstellen können. Alle Empfehlungstypen sind datengesteuert. Sie basieren auf Verhaltensdaten, Produktattributdaten und Metriken. Zur Vereinfachung werden die Empfehlungstypen wie folgt gruppiert:

- [Personalisiert](#personalized)
- [Crosssell und Up-Sells](#crossup)
- [Beliebtheit](#popularity)
- [leistungsstark](#highperf)

Als Best Practice empfiehlt Adobe bei der Verwendung von Recommendations die folgenden Richtlinien:

- Diversifizieren Sie Ihre Empfehlungstypen. Kunden ignorieren die Empfehlungen, wenn sie immer wieder dieselben Produkte vorschlagen.

- Stellen Sie nicht dieselben Empfehlungen auf Ihrer Warenkorbseite und Bestellbestätigungsseite bereit. Erwägen Sie, `Most Added to Cart` für die Warenkorbseite und `Bought This, Bought That` für die Bestellbestätigungsseite zu verwenden.

- Halten Sie Ihre Website aufgeräumt. Stellen Sie nicht mehr als drei Empfehlungseinheiten auf derselben Seite bereit.

- Wenn Ihr Geschäft Kleidung verkauft, kann die `More like this` Empfehlung geschlechtsspezifische Produkte vorschlagen, die nicht mit dem Geschlecht des angezeigten Produkts übereinstimmen. Erwägen, diesen Empfehlungstyp nur für Nicht-Bekleidungskategorien zu verwenden.

>[!NOTE]
>
>Weitere Informationen zu den in diesem Artikel beschriebenen Ereignissen finden Sie unter [Storefront-Ereignisse](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations) in der Entwicklerdokumentation.

## Datenanforderungen und -verhalten

Product Recommendations ist ein datengesteuertes System, das auf Verhaltensdaten beruht, die in Ihrer Storefront erfasst werden. Qualität und Quantität der Empfehlungen hängen von der Menge der verfügbaren Ereignisdaten ab.

>[!IMPORTANT]
>
>Die meisten Empfehlungstypen erfordern ausreichende Verhaltensdaten (z. B. Produktansichten, Warenkorbaktionen und Käufe), um aussagekräftige Ergebnisse zu generieren. Das System benötigt in der Regel mehrere Tage aktiver Käuferaktivität, um genaue Empfehlungen zu erstellen. Unter [Bereitschaftsindikatoren](create.md#readiness-indicators) erfahren Sie, wie der Website-Traffic dabei hilft, die verschiedenen Empfehlungstypen auszufüllen.

### Was passiert bei unzureichenden Daten?

Wenn nicht genügend Ereignisdaten vorhanden sind, um Empfehlungen zu generieren, kann das System:

- Leere Ergebnisse für die Empfehlungseinheit zurückgeben.
- Trigger [Sicherungsempfehlungen](events.md#backup-recommendations), z. B. Anzeige `Most viewed` Produkte, wenn noch keine personalisierten Empfehlungen verfügbar sind.
- Zeigt weniger Produkte als [konfiguriert](create.md) in der Empfehlungseinheit an.

## Personalisiert {#personalized}

Diese Empfehlungstypen empfehlen Produkte basierend auf dem Verhaltensverlauf des jeweiligen Käufers auf Ihrer Site. Wenn ein Käufer beispielsweise zuvor auf Ihrer Site nach einer Jacke gesucht oder eine Jacke gekauft hat, greifen diese Empfehlungen im Wesentlichen dort auf, wo er aufgehört hat, und empfehlen andere Jacken oder ähnliche Produkte.

>[!NOTE]
>
>Personalisierte Empfehlungen erfordern, dass die Käufer über eine etablierte Verhaltensgeschichte verfügen. Neuen Besuchern oder Käufern ohne ausreichenden Interaktionsverlauf werden [Sicherungsempfehlungen](events.md#backup-recommendations) wie Am häufigsten angezeigte Produkte angezeigt, bis sie genügend Verhaltenssignale auf Ihrer Site generieren.

| Typ | Beschreibung |
|---|---|
| Empfohlen | empfiehlt Produkte basierend auf dem aktuellen und vorherigen Onsite-Verhalten jedes Käufers. Zeigt hochrelevante Empfehlungen basierend auf dem Browser- und Kaufverlauf des Käufers an. Dieser Empfehlungstyp ist auf der Startseite wirksam, auf der die meisten Kunden ihren Journey auf einer Website beginnen. Für Erstkäufer auf Ihrer Site, die kein Signal zur Personalisierung ihres Erlebnisses generiert haben, zeigt Adobe Commerce Produkte basierend auf dem am häufigsten angezeigten Empfehlungstyp an. Wenn der Käufer jedoch mit den Produkten auf der Website interagiert, passen sich empfohlene Produkte in Echtzeit an sein Verhalten an.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie <br/><br/>**Empfohlene Beschriftungen:**<br/> - Nur für Sie<br/>- Für Sie empfohlen<br/>- Inspiriert von Ihren Shopping-Trends |
| Zuletzt angesehen | Zeigt Produkte an, die der Einkäufer je nach Browser-Verlauf zuletzt angesehen hat. Alle gelöschten Produkte werden von der Empfehlungseinheit entfernt. Die Empfehlungseinheit wird nicht angezeigt, wenn kein Browser-Verlauf vorhanden ist, oder nicht genügend Verlauf, wenn Filterregeln angewendet werden. Wenn die Ergebnisse weniger Produkte enthalten als konfiguriert sind, zeigt die Empfehlungseinheit nur die zurückgegebenen Produkte an.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Vorgeschlagene Beschriftungen:**<br/>- Kürzlich angezeigt<br/>- Werfen Sie einen weiteren Blick |

## Crosssell und Up-Sells {#crossup}

Diese Empfehlungstypen sind sozial abgesichert, um Käufern zu helfen, das zu finden, was anderen gefiel, oder produktgesteuert, um ihnen dabei zu helfen, andere ähnliche Produkte zu finden. Die empfohlenen Produkte ergänzen häufig das ausgewählte Produkt.

>[!NOTE]
>
>Die Empfehlungstypen „hat dies angezeigt, gesehen,“ hat dies angezeigt, gekauft, und „hat dies gekauft, hat das gekauft“ verwenden keine Metrik für einfache Vorfälle, sondern einen komplexeren Algorithmus für die kollaborative Filterung, der nach *interessanten Ähnlichkeiten“ sucht* die nicht auf beliebte Produkte ausgerichtet sind. Die für diese Empfehlungstypen verwendeten Daten basieren auf dem aggregierten Verhalten des Käufers, das aus mehreren Sitzungen auf Ihrer Site abgeleitet wurde. Die Daten basieren nicht auf dem Käuferverhalten, das aus einem einzelnen Sitzungsereignis auf Ihrer Site abgeleitet wurde. Diese Empfehlungstypen helfen Käufern dabei, die benachbarten Produkte zu finden, deren Kombination mit dem aktuell angezeigten Produkt möglicherweise nicht offensichtlich ist.
>
>Diese Empfehlungstypen erfordern erhebliche produktübergreifende Interaktionsdaten, um aussagekräftige Korrelationen zu identifizieren. Stores mit begrenzter Produktkatalogvielfalt oder geringem Traffic erhalten möglicherweise weniger Empfehlungen, bis ausreichende Verhaltensmuster erkennbar werden.

| Typ | Beschreibung |
|---|---|
| hat dieses angezeigt, hat Folgendes angezeigt | empfiehlt Produkte, die Käufer überproportional häufig mit dem aktuell angezeigten Produkt sehen.<br/><br/>**Wo verwendet:**<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/>- Kunden, die dieses Produkt angesehen haben, haben auch angezeigt (PDP) |
| Das hier angesehen, das gekauft | empfiehlt Produkte, die Käufer tendenziell unverhältnismäßig häufiger kaufen, nachdem sie das aktuelle Produkt angesehen haben. Dieser Typ hilft Kundinnen und Kunden, Produkte zu entdecken, die sie andernfalls möglicherweise nicht bemerkt hätten.<br/><br/>**Wo verwendet:**<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Vorgeschlagene Beschriftungen:**<br/>- Kunden, die dieses Ultimate angesehen haben<br/>- Kunden haben schließlich gekauft<br/>- Was kaufen andere, nachdem sie dieses Produkt angesehen haben? |
| Das kaufte ich, das kaufte ich | empfiehlt Produkte, die Käufer überproportional häufiger mit dem aktuell angezeigten Produkt kaufen. Dieser Typ zeigt hochrelevante Produkte an, die Kunden in den Warenkorb legen können, indem sie aggregieren, was andere Kunden mit dem aktuellen Produkt gekauft haben.<br/><br/>**Wo verwendet:**<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/>- Erhalten Sie alles, was Sie benötigen<br/>- Vergessen Sie diese nicht<br/>- Häufig zusammen gekauft |
| Ähnliche Themen | empfiehlt Produkte, die auf ähnlichen Metadaten wie Name, Beschreibung, Kategoriezuweisung und Attributen basieren. Durch die Auswertung der Attribute für die angezeigten Produkte empfiehlt dieser Typ ähnliche Produkte in derselben Kategorie. Wenn ein Käufer beispielsweise Yogamatten durchsucht, werden andere Produkte der Kategorie Ausrüstung empfohlen. Da dieser Empfehlungstyp keine Geschlechter unterscheidet, wird er nicht für Bekleidung, Mode oder andere geschlechtsspezifische vertikale Bereiche empfohlen.<br/><br/>**Wo verwendet:**<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/> - Weitere Produkte wie diese<br/>- Ähnlich wie diese |
| [Visuelle Ähnlichkeit](#visualsim) | empfiehlt, Produkte, die dem angezeigten Produkt ähnlich sehen. Dieser Empfehlungstyp ist am nützlichsten, wenn Bilder und die visuellen Aspekte von Produkten für das Einkaufserlebnis wichtig sind. |

## Beliebtheit {#popularity}

Diese Empfehlungstypen empfehlen Produkte, die in den letzten sieben Tagen am beliebtesten oder beliebtesten waren.

>[!NOTE]
>
>Beliebtheitsbasierte Empfehlungen erfordern ausreichende Ereignisdaten aus Ihrer Storefront. Wenn Ihr Store neu ist oder nur geringen Traffic hat, können diese Empfehlungstypen eingeschränkte Ergebnisse oder keine Ergebnisse zurückgeben, bis ausreichende Verhaltensdaten erfasst wurden. Überwachen Sie Ihre [Data Readiness Indicator](workspace.md), um eine optimale Leistung zu gewährleisten.

| Typ | Beschreibung |
|---|---|
| Am häufigsten angezeigt | empfiehlt Produkte, die am häufigsten angezeigt wurden, indem die Anzahl der Sitzungen gezählt wird, bei denen in den letzten sieben Tagen eine Ansichtsaktion stattgefunden hat.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/>- Am beliebtesten<br/>- Trend<br/>- Beliebt<br/>- Kürzlich beliebt<br/>- Beliebte Produkte inspiriert durch dieses Produkt (PDP)<br/>- Topverkäufe |
| Am häufigsten gekauft | empfiehlt Produkte, die von Käufern in den letzten sieben Tagen am häufigsten gekauft wurden.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/> - Am beliebtesten<br/>- Trend<br/>- Beliebt<br/>- Kürzlich beliebt<br/>- Beliebte Produkte inspiriert durch dieses Produkt (PDP)<br/>- Topverkäufe |
| Am häufigsten zum Warenkorb hinzugefügt | empfiehlt Produkte, die von Käufern in den letzten sieben Tagen am häufigsten in den Warenkorb gelegt wurden. Dieser Empfehlungstyp kann auf allen Seiten verwendet werden.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/> - Am beliebtesten<br/>- Trend<br/>- Beliebt<br/>- Kürzlich beliebt<br/>- Beliebte Produkte inspiriert durch dieses Produkt (PDP)<br/>- Topverkäufe |
| Trend | empfiehlt Produkte basierend auf der jüngsten Popularitätsdynamik eines Produkts auf Ihrer Site.<br/><br/>Adobe Sensei aggregiert Such- und Kaufdaten auf Ihrer Site, um zu ermitteln und zu bewerten, welche Produkte bei Ihren Kundinnen und Kunden am beliebtesten sind. Da Trending die jüngste Produktimpulse analysiert, ist es ein effektiver Empfehlungstyp für Kataloge mit hohem Umsatz. Wenn Ihr Katalog statischer ist, ist er möglicherweise nur dann so nützlich, wenn die Einkaufsmuster Ihrer Zielgruppe sehr variabel sind.<br/><br/>Bei Verwendung auf der Startseite empfiehlt Trend Produkte, die kürzlich auf der gesamten Site beliebt waren. Im Trend-Bereich werden nicht Produkte angezeigt, die durchgängig beliebt sind, sondern solche, die erst kürzlich beliebt wurden. Wenn Sie beispielsweise eine E-Mail-Marketing-Kampagne haben, die bestimmte Produkte bewirbt, erhöht die durch die E-Mail generierte Popularitätssteigerung die Wahrscheinlichkeit, dass die beworbenen Produkte als Trend klassifiziert werden.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/>- Trending<br/>- Jetzt <br/>- Kürzlich trendend<br/>- Hot products<br/>- Trending Related Products (PDP) |

## Hochleistungsfähig {#highperf}

Diese Empfehlungstypen empfehlen, Produkte basierend auf Erfolgskriterien wie Hinzufügen zum Warenkorb oder Konversionsraten am besten zu entwickeln.

>[!NOTE]
>
>Leistungsstarke Empfehlungstypen basieren auf Konversionsdaten (Käufe und Aktionen vom Typ „In den Warenkorb legen„). Neue Stores oder Stores mit niedrigen Konversionsvolumina müssen möglicherweise Daten über 7-14 Tage sammeln, bevor diese Empfehlungen in Kraft treten.

| Typ | Beschreibung |
|---|---|
| Konvertierung für Kauf anzeigen | empfiehlt Produkte mit der höchsten Konversionsrate von Ansicht zu Kauf. Wie hoch ist der Anteil aller Shopper-Sitzungen, in denen eine Produktansicht registriert wurde, an der es letztendlich zu einem Kauf durch den Shopper kam.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/> -Topverkäufe<br/>- Beliebte Produkte<br/>- Sie könnten Interesse haben an |
| Konvertierung von Ansicht in Warenkorb | empfiehlt Produkte mit der höchsten Konversionsrate von Warenkorb zu Ansicht. Wie hoch ist der Anteil aller Shopper-Sitzungen, in denen eine Produktansicht registriert wurde, die von dem Shopper schließlich registriert und in den Warenkorb gelegt wurde.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/> - Topverkäufe<br/>- Beliebte Produkte<br/>- Interessieren Sie sich vielleicht für |
| Am häufigsten gekauft | Dieser Empfehlungstyp wird häufig als „Topverkäufe“ bezeichnet und zählt die Anzahl der Sitzungen, in denen in den letzten sieben Tagen eine Aktion „Bestellung aufgeben“ stattgefunden hat. Dieser Empfehlungstyp kann auf allen Seiten verwendet werden.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/> - Am beliebtesten<br/>- Trend<br/>- Beliebt<br/>- Kürzlich beliebt<br/>- Beliebte Produkte inspiriert durch dieses Produkt (PDP)<br/>- Topverkäufe |
| Am häufigsten zum Warenkorb hinzugefügt | empfiehlt Produkte, die von Käufern in den letzten sieben Tagen am häufigsten in den Warenkorb gelegt wurden. Dieser Empfehlungstyp kann auf allen Seiten verwendet werden.<br/><br/>**Wo verwendet:**<br/>- Startseite<br/>- Kategorie<br/>- Produktdetails<br/>- Warenkorb<br/>- Bestätigung <br/><br/>**Empfohlene Beschriftungen:**<br/> - Am beliebtesten<br/>- Trend<br/>- Beliebt<br/>- Kürzlich beliebt<br/>- Beliebte Produkte inspiriert durch dieses Produkt (PDP)<br/>- Topverkäufe |

## Visuelle Ähnlichkeit {#visualsim}

Der Empfehlungstyp _Visuelle Ähnlichkeit_ empfiehlt, Produkte so auszusehen, wie sie dem angezeigten Produkt ähnlich sind. Dieser Empfehlungstyp ist am nützlichsten, wenn Bilder und visuelle Aspekte der Produkte wichtige Teile des Einkaufserlebnisses sind.

### Funktionsweise

Der Empfehlungstyp _Visuelle Ähnlichkeit_ bietet Empfehlungen für andere Produkte in Ihrem Katalog, die der aktuell angezeigten Abbildung optisch ähnlich sind. Visuelle Ähnlichkeit umfasst Aspekte wie:

- Farbe
- Form
- Größe
- Textur
- Material
- Stil

Adobe Sensei verwendet KI, um die Bilder in Ihrem Katalog zu verarbeiten und zu analysieren und Attribute zu erstellen, die verwendet werden, um visuelle Ähnlichkeiten zu ermitteln.

>[!NOTE]
>
> Wenn Sie diesen Empfehlungstyp in einer Nicht-Produktionsumgebung testen, stellen Sie sicher, dass Ihre Bild-URLs öffentlich zugänglich sind.

>[!NOTE]
>
> Derzeit müssen Produktbilder 10 MB oder weniger groß sein.

Da dieser Empfehlungstyp für die meisten Kataloge nicht anwendbar ist, ist er nicht standardmäßig aktiviert. Sie müssen diesen Empfehlungstyp explizit aktivieren.

### Empfehlungstyp für visuelle Ähnlichkeit aktivieren

>[!NOTE]
>
> Der Empfehlungstyp _Visuelle Ähnlichkeit_ ist verfügbar, wenn Sie [ als optionales ](install-configure.md) installieren.

1. Wechseln Sie in der _Admin_-Seitenleiste zu **Marketing** > _Promotions_ > **Product Recommendations**, um das _Product Recommendations_ Dashboard anzuzeigen.

1. Klicken Sie **Einstellungen** (Zahnradsymbol), um die Seite _Einstellungen_ anzuzeigen.

1. Wählen Sie im Abschnitt _Visuelle Empfehlungen_ die Option aus, um **Visuelle Empfehlungen aktivieren**.

1. Klicken Sie **Abschluss auf**&#x200B;Änderungen speichern“.

   Die Seite [Neue Empfehlung erstellen](create.md) wird jetzt **Visuelle Ähnlichkeit** als auswählbarer Empfehlungstyp angezeigt, wenn der Seitentyp &quot;**&quot;**.

Nachdem Sie die visuellen Empfehlungen aktiviert haben, startet Adobe Sensei die Bildverarbeitung. Wie lange es dauert, hängt von der Größe Ihres Katalogs ab.

### Wo verwendet

- Produktdetails

### Empfohlene Storefront-Kennzeichnungen

- Vielleicht gefällt Ihnen auch Folgendes
- Wir haben weitere Produkte gefunden, die Ihnen gefallen könnten
- Inspiriert von diesem Stil

### Beispiel

Die folgende Abbildung zeigt die Produktdetailseite für die _Clamber Watch_:

![Klammeruhr](assets/visual-sim-pdp.png)

Nachfolgend ist die Empfehlungseinheit _Visuelle Ähnlichkeit_ für _Clamber Watch_ dargestellt:

![Visuelle Ähnlichkeitseinheit](assets/visual-sim-unit.png)
