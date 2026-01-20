---
title: Erfassen von Daten
description: Erfahren Sie, wie Ereignisse Daten für  [!DNL Product Recommendations] erfassen.
feature: Services, Recommendations, Eventing
exl-id: 0d5317e3-c049-4fcd-a8e4-228668d89386
source-git-commit: 458f34c45406db871ec61ff408aa624f163b6ee0
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 0%

---

# Erfassen von Daten

Wenn Sie [[!DNL Product Recommendations]](install-configure.md) installieren und konfigurieren, stellt das Modul die Verhaltensdatenerfassung in Ihrer Storefront bereit. Dieser Mechanismus erfasst anonymisierte Verhaltensdaten von Ihren Käufern und unterstützt [!DNL Product Recommendations]. Beispielsweise wird das `view` Ereignis verwendet, um den `Viewed this, viewed that` Empfehlungstyp zu berechnen, und das `place-order` Ereignis wird verwendet, um den `Bought this, bought that` Empfehlungstyp zu berechnen.

Weitere Informationen zu den Verhaltensdaten[&#x200B; die von &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations)-Ereignissen erfasst werden, finden Sie in der [!DNL Product Recommendations]Entwicklerdokumentation“.

>[!NOTE]
>
>Die Datenerhebung zum Zwecke der [!DNL Product Recommendations] umfasst keine personenbezogenen Daten (PII). Alle Benutzerkennungen wie Cookie-IDs und IP-Adressen werden streng anonymisiert. Weitere [&#x200B; (](https://www.adobe.com/privacy/experience-cloud.html).

## Healthcare-Kunden

Wenn Sie Kundschaft im Gesundheitswesen sind und die [Data Services HIPAA-Erweiterung](../data-connection/hipaa-readiness.md#installation) installiert haben, die Teil der [Data Connection](../data-connection/overview.md)-Erweiterung ist, werden von [!DNL Product Recommendations] verwendete Storefront-Ereignisdaten nicht mehr erfasst. Dies liegt daran, dass Storefront-Ereignisdaten Client-seitig generiert werden. Um weiterhin Storefront-Ereignisdaten zu erfassen und zu senden, aktivieren Sie die Ereigniserfassung für [!DNL Product Recommendations] erneut. Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general#data-services)Allgemeine Konfiguration“.

## Datentypen und Ereignisse

Es gibt zwei Arten von Daten, die in Produktempfehlungen verwendet werden:

- **Verhalten** - Daten aus der Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, Artikel, die zum Warenkorb hinzugefügt werden, und Käufe.
- **Katalog** - Produktmetadaten, z. B. Name, Preis, Verfügbarkeit usw.

Bei der Installation des `magento/product-recommendations`-Moduls aggregiert Adobe AI die Verhaltens- und Katalogdaten und erstellt für jeden Empfehlungstyp Produktempfehlungen. Der Produktempfehlungs-Service stellt diese Empfehlungen dann in Form eines Widgets, das das empfohlene Produkt (die empfohlenen _) enthält, in Ihrer Storefront_.

Einige Empfehlungstypen verwenden Verhaltensdaten von Kundinnen und Kunden, um Modelle für maschinelles Lernen zu trainieren, um personalisierte Empfehlungen zu erstellen. Andere Empfehlungstypen verwenden nur Katalogdaten und verwenden keine Verhaltensdaten. Wenn Sie Produktempfehlungen schnell auf Ihrer Site verwenden möchten, können Sie die folgenden, nur für den Katalog geeigneten Empfehlungstypen verwenden:

- `More like this`
- `Visual similarity`

### Kaltstart

Ab wann können Empfehlungstypen verwendet werden, die Verhaltensdaten verwenden? Es kommt darauf an. Dies wird als &quot;_&quot;-_ bezeichnet.

Das _Kaltstart_-Problem bezieht sich auf die Zeit, die ein Modell benötigt, um trainiert und effektiv zu werden. Für Produktempfehlungen bedeutet dies, dass Sie warten müssen, bis Adobe AI genügend Daten gesammelt hat, um seine Modelle für maschinelles Lernen zu trainieren, bevor Sie Empfehlungseinheiten auf Ihrer Site bereitstellen. Je mehr Daten die Modelle haben, desto genauer und nützlicher sind die Empfehlungen. Da die Datenerfassung auf einer Live-Site erfolgt, ist es am besten, diesen Prozess frühzeitig durch die Installation und Einrichtung des `magento/production-recommendations`-Moduls zu starten.

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

Während Daten auf Ihrer Live-Site erfasst werden und die Modelle für maschinelles Lernen trainiert werden, können Sie andere Test- und Konfigurationsaufgaben abschließen, die zum Einrichten von Empfehlungen erforderlich sind. Wenn Sie mit dieser Arbeit fertig sind, verfügen die Modelle über genügend Daten, um nützliche Empfehlungen zu erstellen, sodass Sie sie in Ihrer Storefront bereitstellen können.

Wenn auf Ihrer Site nicht genügend Traffic (Ansichten, Käufe, Trends) für die meisten Produkt-SKUs vorhanden ist, sind möglicherweise nicht genügend Daten vorhanden, um den Lernprozess abzuschließen. Dadurch kann der Bereitschaftsindikator im Admin-Bereich hängen bleiben. Die Bereitschaftsindikatoren sollen Händlern einen weiteren Datenpunkt bei der Auswahl des Recommendations-Typs bieten, der für ihren Store besser ist. Die Zahlen sind Richtwerte und erreichen möglicherweise nie 100 %. [Weitere &#x200B;](create.md#readiness-indicators) zu Bereitschaftsindikatoren.

### Empfehlungen für Backups {#backuprecs}

Wenn die Eingabedaten nicht ausreichen, um alle angeforderten Empfehlungselemente in einer Einheit bereitzustellen, bietet Adobe Commerce Sicherungsempfehlungen zum Ausfüllen von Empfehlungseinheiten. Wenn Sie beispielsweise den `Recommended for you` Empfehlungstyp auf Ihrer Homepage bereitstellen, hat ein Erstkäufer auf Ihrer Site nicht genügend Verhaltensdaten generiert, um personalisierte Produkte korrekt zu empfehlen. In diesem Fall zeigt Adobe Commerce Elemente basierend auf dem `Most viewed` Empfehlungstyp an diesen Käufer an.

Bei unzureichender Erfassung von Eingabedaten greifen die folgenden Empfehlungstypen auf `Most viewed` Empfehlungstyp zurück:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

#### Einschränkungen

- Anzeigenblocker und Datenschutzeinstellungen können verhindern, dass Ereignisse erfasst werden, und können dazu führen, dass die Interaktion und der Umsatz [Metriken](workspace.md#column-descriptions) nicht erfasst werden. Darüber hinaus werden einige Ereignisse möglicherweise nicht gesendet, weil der Käufer die Seite oder das Netzwerk verlassen hat.
- [Headless-Implementierungen](headless.md) müssen das Eventing implementieren, um das Produktempfehlungs-Dashboard zu unterstützen.
- Für konfigurierbare Produkte verwenden Produktempfehlungen das Bild des übergeordneten Produkts in der Empfehlungseinheit. Wenn für das konfigurierbare Produkt kein Bild angegeben ist, ist die Empfehlungseinheit für dieses spezifische Produkt leer.

>[!NOTE]
>
>Wenn [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Adobe Commerce keine Verhaltensdaten, bis der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Einschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
