---
title: Einführung in [!DNL Product Recommendations]
description: '[!DNL Product Recommendations] sind ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, Umsätze steigern und die Kundenbindung stimulieren können.'
recommendations: noCatalog
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Einführung in [!DNL Product Recommendations]

Produktempfehlungen sind ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, Umsätze steigern und die Kundenbindung stimulieren können. Adobe Commerce-Produktempfehlungen basieren auf [Adobe Sensei](https://www.adobe.com/sensei.html), das Algorithmen für künstliche Intelligenz und maschinelles Lernen verwendet, um eine gründliche Analyse aggregierter Besucherdaten durchzuführen. Wenn diese Daten mit Ihrem Adobe Commerce-Katalog kombiniert werden, können Sie ein ansprechendes, relevantes und personalisiertes Erlebnis erhalten.

Produktempfehlungen werden in der Storefront als Einheiten mit Beschriftungen angezeigt, z. B. „Kunden, die dieses Produkt angesehen haben, haben es auch angesehen“. Sie können Recommendations für Ihre Store-Ansichten direkt von der Adobe Commerce-Administratorin bzw. dem -Administrator erstellen, verwalten und bereitstellen.

Wenn Ihre Storefront mit PWA Studio implementiert wird, lesen Sie den Abschnitt [Dokumentation zu PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie, wie Sie [!DNL Product Recommendations] in [ Headless-Storefront ](headless.md) (integrieren) können.

>[!NOTE]
>
>Es gibt viele Möglichkeiten, eine Headless- oder benutzerdefinierte Implementierung zu entwickeln. In diesem Handbuch wird eine Möglichkeit beschrieben, dies mithilfe von PWA Studio zu tun. Sie deckt nicht alle Szenarien oder Eventualitäten ab.

## DATENSCHUTZ

Die Datenerhebung zum Zwecke der [!DNL Product Recommendations] umfasst keine personenbezogenen Daten (PII). Außerdem werden alle Benutzerkennungen wie Cookie-IDs und IP-Adressen streng anonymisiert. Weitere Informationen finden Sie in der [Adobe-Datenschutzrichtlinie](https://www.adobe.com/privacy/policy.html).

[!DNL Product Recommendations] Benutzer können weitere Daten zur Datensynchronisierung [ das ](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html?lang=de)Daten-Management-Dashboard“ aufrufen.

## Produktempfehlungen versus Produktbeziehungen

Angesichts der sich ständig verändernden Komplexität von Online-Shopping, ist das, was am besten für Ihre Storefront funktioniert, oft eine Kombination aus mehreren Schlüsseltechnologien. Die Verwendung von [!DNL Product Recommendations]- [Produktbeziehungen](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/product-relationships/product-relationships.html?lang=de) bietet Ihnen mehr Flexibilität bei der Promotion von Produkten. Sie können [!DNL Product Recommendations] mit Adobe Sensei nutzen, um Ihre Empfehlungen im benötigten Umfang intelligent zu automatisieren. Anschließend können Sie &quot;[ Produktregeln“ nutzen](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/product-relationships/product-related-rules.html?lang=de) wenn Sie manuell eingreifen müssen und sicherstellen müssen, dass eine bestimmte Empfehlung an ein Zielkunden-Segment gesendet wird oder wenn bestimmte Geschäftsziele erfüllt werden müssen.

Produktempfehlungen ermöglichen Ihnen Folgendes:

- Wählen Sie aus neun verschiedenen intelligenten Empfehlungstypen, die auf den folgenden Bereichen basieren: Käuferbasiert, Artikelbasiert, Beliebtheit, Trend und Ähnlichkeit
- Verwenden Sie Verhaltensdaten, um Empfehlungen auf der Storefront-Journey des Käufers zu personalisieren
- Messen Sie Schlüsselmetriken, die für jede Empfehlung relevant sind, damit Sie die Auswirkungen Ihrer Empfehlungen besser verstehen können

## [!DNL Product Recommendations] Demo

In diesem Video erfahren Sie mehr über [!DNL Product Recommendations]:

>[!VIDEO](https://video.tv.adobe.com/v/343991?quality=12)

## Richtlinie zur Aufbewahrung von Katalogdaten

Wenn Sie in Ihrer Testumgebung an 90 aufeinander folgenden Tagen keine Abfrage für die Katalogdaten senden, werden die Katalogdaten auf den Ruhezustand eingestellt und es werden keine Daten für eine Abfrage zurückgegeben. Katalogdaten in Ihrer Produktionsumgebung sind von dieser Richtlinie nicht betroffen.

Um die Katalogdaten in Ihrer Testumgebung erneut zu aktivieren, [ Sie „eine Support-Anfrage ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#experience-league-start-page)&quot; mit dem Titel &quot;[!DNL Product Recommendations] erneut aktivieren“ und fügen Sie die Umgebungs-IDs hinzu. Die Katalogdaten in Ihrer Testumgebung sollten innerhalb weniger Stunden wiederhergestellt werden.
