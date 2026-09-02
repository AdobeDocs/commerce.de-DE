---
title: Erfassen von Daten
description: Erfahren Sie, wie Ereignisse Daten für  [!DNL Product Recommendations] erfassen.
feature: Services, Recommendations, Eventing
exl-id: 0d5317e3-c049-4fcd-a8e4-228668d89386
TQID: https://experienceleague.adobe.com/efHRMj3u3w-xvUgMnEYDpX0D-BDCUyjhhrkMaa3n-xg
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eb30f47f-d87a-400f-8f78-63ce7979ff56
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 88a0b1a238090dec85e0f79082d264b720999fee
workflow-type: tm+mt
source-wordcount: 937
ht-degree: 0%

---

# Erfassen von Daten

Wenn Sie [[!DNL Product Recommendations]](install-configure.md) installieren und konfigurieren, stellt das Modul die Verhaltensdatenerfassung in Ihrer Storefront bereit. Dieser Mechanismus erfasst anonymisierte Verhaltensdaten von Ihren Käufern und unterstützt [!DNL Product Recommendations]. Beispielsweise wird das `view` Ereignis verwendet, um den `Viewed this, viewed that` Empfehlungstyp zu berechnen, und das `place-order` Ereignis wird verwendet, um den `Bought this, bought that` Empfehlungstyp zu berechnen.

Weitere Informationen zu den Verhaltensdaten, die von den [!DNL Product Recommendations]-Ereignissen erfasst werden, finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations).

>[!NOTE]
>
>Die Datenerhebung zum Zwecke der [!DNL Product Recommendations] umfasst keine personenbezogenen Daten (PII). Alle Benutzerkennungen wie Cookie-IDs und IP-Adressen werden streng anonymisiert. Weitere [&#x200B; (](https://www.adobe.com/privacy/experience-cloud.html).

## Healthcare-Kunden

Wenn Sie Kundschaft im Gesundheitswesen sind und die [Data Services HIPAA-Erweiterung](../data-connection/hipaa-readiness.md#installation) installiert haben, die in der [Data Connection](../data-connection/overview.md)-Erweiterung enthalten ist, erfasst [!DNL Product Recommendations] keine Storefront-Ereignisdaten mehr, da sie Client-seitig generiert werden.

Um mit dem Erfassen und Senden von Storefront-Ereignisdaten fortzufahren, aktivieren Sie die Ereigniserfassung für [!DNL Product Recommendations] erneut. Weitere Informationen finden Sie unter [Allgemeine Konfiguration](https://experienceleague.adobe.com/de/docs/commerce-admin/config/general/general#data-services).

## Datentypen und Ereignisse

Es gibt zwei Arten von Daten, die in Produktempfehlungen verwendet werden:

- **Verhalten** - Daten aus der Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, Artikel, die zum Warenkorb hinzugefügt werden, und Käufe.
- **Katalog** - Produktmetadaten, z. B. Name, Preis, Verfügbarkeit usw.

Bei der Installation des `magento/product-recommendations` aggregiert Adobe AI die Verhaltens- und Katalogdaten und erstellt für jeden Empfehlungstyp Produktempfehlungen. Der Produktempfehlungs-Service stellt diese Empfehlungen dann in Form eines Widgets, das das empfohlene Produkt (die empfohlenen _) enthält, in Ihrer Storefront_.

Einige Empfehlungstypen verwenden die Verhaltensdaten von Käufern, um Modelle für maschinelles Lernen zu trainieren und personalisierte Empfehlungen zu generieren. Andere verwenden nur Katalogdaten. Um schnell mit der Verwendung von Produktempfehlungen zu beginnen, wählen Sie aus den folgenden Empfehlungstypen auf Katalogbasis:

- `More like this`
- `Visual similarity`

### Kaltstart

Ab wann können Empfehlungstypen verwendet werden, die Verhaltensdaten verwenden? Es kommt darauf an. Diese Situation wird als &quot;_-Problem_ bezeichnet.

Das _Kaltstart_-Problem ist die Zeit, die ein Modell für maschinelles Lernen benötigt, um zu trainieren, bevor es effektive Empfehlungen produzieren kann. Für Produktempfehlungen muss Adobe AI genügend Daten erfassen, um seine Modelle zu trainieren, bevor Sie Empfehlungseinheiten bereitstellen. Mehr Daten verbessern im Allgemeinen die Genauigkeit und Nützlichkeit von Empfehlungen. Da die Datenerfassung auf Ihrer Live-Site erfolgt, starten Sie diesen Prozess frühzeitig, indem Sie das `magento/product-recommendations`-Modul installieren und konfigurieren.

Die folgende Tabelle enthält einige allgemeine Hinweise dazu, wie lange es dauert, bis für jeden Empfehlungstyp genügend Daten erfasst sind:

| Empfehlungstyp | Trainingszeit | Notizen |
|---|---|---|
| Beliebtheitsbasiert (`Most viewed`, `Most purchased`, `Most added to cart`) | Variiert | Hängt von der Menge der Ereignisse ab - Ansichten sind am häufigsten und lernen daher schneller; fügt dann zum Warenkorb hinzu und kauft |
| `Viewed this, viewed that` | Erfordert mehr Schulung | Das Volumen der Produktansichten ist annehmbar hoch |
| `Viewed this, bought that`, `Bought this, bought that` | Erfordert die meiste Schulung | Kaufereignisse sind die seltensten Ereignisse auf einer Commerce-Site, insbesondere im Vergleich zu Produktansichten |
| `Trending` | Erfordert drei Tage Daten, um eine Popularitätsbasislinie zu erstellen | Der Trend ist ein Maß für die jüngste Dynamik in der Popularität eines Produkts verglichen mit seiner eigenen Popularitätsbasislinie. Der Trend-Score eines Produkts wird anhand eines Vordergrundsatzes (aktuelle Popularität über 24 Stunden) und eines Hintergrundsatzes (Popularitätsbasislinie über 72 Stunden) berechnet. Wenn die Popularität eines Elements innerhalb eines Zeitraums von 24 Stunden im Vergleich zu seiner Grundbeliebtheit signifikant zunimmt, erhält es einen hohen Trend-Score. Jedes Produkt hat diese Bewertung, und die Artikel mit der höchsten Bewertung zu jeder Zeit umfassen die Gruppe der Top-Trend-Produkte. |

Andere Variablen, die sich auf die für das Training benötigte Zeit auswirken können:

- Höheres Traffic-Volumen trägt zu schnellerem Lernen bei
- Einige Empfehlungstypen trainieren schneller als andere
- Adobe Commerce berechnet die Verhaltensdaten alle vier Stunden neu. Empfehlungen werden umso genauer, je länger sie auf Ihrer Site verwendet werden.

Auf der Seite „Empfehlung erstellen[&#x200B; werden Bereitschaftsindikatoren angezeigt, damit Sie den Trainings-Fortschritt &#x200B;](create.md#readiness-indicators) jeden Empfehlungstyp visualisieren können.

Während Ihre Live-Site Daten erfasst und die Modelle für maschinelles Lernen trainiert, führen Sie die verbleibenden Test- und Konfigurationsaufgaben aus. Sobald die Modelle über genügend Daten verfügen, um nützliche Empfehlungen zu generieren, stellen Sie die Empfehlungseinheiten in Ihrer Storefront bereit.

Wenn Ihre Site für die meisten Produkt-SKUs nicht ausreichend Traffic (Ansichten, Käufe oder Trends) erhält, wird der Lernprozess möglicherweise nicht abgeschlossen, sodass die Bereitschaftsindikatoren im Admin hängen bleiben. Bereitschaftsindikatoren helfen Händlern, den besten Empfehlungstyp für ihren Store auszuwählen, aber sie sind nur ein Leitfaden und erreichen möglicherweise nie 100 %. Weitere Informationen zu Bereitschaftsindikatoren. [Weitere &#x200B;](create.md#readiness-indicators) zu Bereitschaftsindikatoren.

### Empfehlungen für Backups {#backuprecs}

Wenn unzureichende Eingabedaten eine Empfehlungseinheit daran hindern, alle angeforderten Elemente zurückzugeben, füllt Adobe Commerce sie mit Sicherungsempfehlungen. Wenn Sie beispielsweise den `Recommended for you` Empfehlungstyp auf der Homepage bereitgestellt haben, hat ein Erstkäufer möglicherweise nicht genügend Verhaltensdaten für personalisierte Empfehlungen generiert. In diesem Fall zeigt Adobe Commerce Elemente basierend auf dem `Most viewed `Empfehlungstyp“ an.

Wenn die Erfassung der Eingabedaten nicht ausreicht, greifen die folgenden Empfehlungstypen auf `Most viewed` Empfehlungstyp zurück:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

#### Einschränkungen

- Anzeigenblocker und Datenschutzeinstellungen können verhindern, dass Ereignisse erfasst werden, und können dazu führen, dass die Interaktion und der Umsatz [Metriken](workspace.md#column-descriptions) nicht erfasst werden. Darüber hinaus werden einige Ereignisse nicht gesendet, da der Käufer die Seite oder das Netzwerk verlassen hat.
- [Headless-Implementierungen](headless.md) müssen das Eventing implementieren, um das Produktempfehlungs-Dashboard zu unterstützen.
- Für konfigurierbare Produkte verwenden Produktempfehlungen das Bild des übergeordneten Produkts. Wenn das übergeordnete Produkt kein Bild hat, wird dieses Produkt nicht in der Empfehlungseinheit angezeigt.

>[!NOTE]
>
>Wenn [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/de/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) aktiviert ist, erfasst Adobe Commerce keine Verhaltensdaten, bis der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Einschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
