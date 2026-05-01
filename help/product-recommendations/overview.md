---
title: Was sind Product Recommendations?
description: Erfahren Sie mehr über Produktempfehlungen in Adobe Commerce. Entdecken Sie KI-gesteuerte Storefront-Einheiten, Datenschutz, Admin- und Storefront-Pfade und die Aufbewahrung wichtiger Daten.
recommendations: noCatalog
exl-id: 72850cfd-555c-4e0e-ac3e-097e6dac2030
source-git-commit: 6bfc2c0ed53b44fb30a142dc87f87dca8a601a33
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Was sind [!DNL Product Recommendations]?

[!DNL Product Recommendations] können Ihnen mithilfe von [Adobe AIpersonalisierte Produktempfehlungen für Adobe Commerce-Storefronts ](https://business.adobe.com/ai.html) und maschinelles Lernen für das aggregierte Käuferverhalten und Ihren Katalog zeigen. Diese Übersicht behandelt Service-Einschränkungen (einschließlich HIPAA), Daten und Datenschutz, wo Empfehlungseinheiten angezeigt werden, Storefront-Implementierungspfade, wie Empfehlungen Produktbeziehungen ergänzen und die Aufbewahrung von Katalogdaten.

>[!IMPORTANT]
>
>**[!DNL Product Recommendations]ist kein HIPAA-fähiger Service.** Aktivieren oder verwenden Sie [!DNL Product Recommendations] in keiner Adobe Commerce-Implementierung, die das HIPAA-fähige Angebot verwendet oder anderweitig geschützte Gesundheitsinformationen (Protected Health Information, PHI) verarbeitet. [!DNL Product Recommendations] gehört zu den Commerce SaaS-Services, die derzeit als nicht HIPAA-fähig eingestuft sind.
>
>Weitere Informationen dazu, welche Adobe Commerce-Funktionen HIPAA-fähig sind und welche Services nicht mit PHI verwendet werden dürfen, finden Sie unter [HIPAA-Bereitschaft für Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) und [Vorgänge](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/operations#adobe-commerce-services).

## Umgang mit Daten und Datenschutz

Die Datenerfassung für [!DNL Product Recommendations] umfasst keine personenbezogenen Daten (PII). Alle Benutzerkennungen wie Cookie-IDs und IP-Adressen werden streng anonymisiert. Weitere Informationen finden Sie in der [Adobe-Datenschutzrichtlinie](https://www.adobe.com/privacy/policy.html).

Weitere Informationen zur Datensynchronisation finden Sie unter [Data Management Dashboard](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html).

## Wo Empfehlungen erscheinen

Empfehlungen werden in der Storefront als Einheiten mit Beschriftungen angezeigt, z. B. „Kunden, die dieses Produkt angesehen haben, haben es auch angesehen“. Sie können Empfehlungen für Ihre Store-Ansichten über den Adobe Commerce-Admin erstellen, verwalten und bereitstellen. Wenn Ihr Commerce-Projekt den [Adobe Commerce Optimizer-Connector](https://experienceleague.adobe.com/en/docs/commerce/aco-optimizer-connector/overview) verwendet, können Sie Empfehlungen über [Adobe Commerce Optimizer erstellen, verwalten und bereitstellen](../optimizer/overview.md).

## Storefront-Implementierungen

Wählen Sie die Dokumentation aus, die Ihrer Storefront entspricht:

- **PWA Studio** - [Dokumentation zu PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/)
- **Benutzerdefinierte Frontends (z. B. React oder Vue.js)** - [Integration [!DNL Product Recommendations]](headless.md) in eine Headless-Storefront
- **Commerce Edge Delivery Services (EDS)** — [Dokumentation zur Adobe Commerce-Storefront für EDS](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/)

>[!NOTE]
>
>Headless- und benutzerdefinierte Setups variieren je nach Stack. In diesem Produktbereich werden ein PWA Studio-Pfad und ein allgemeines Headless-Integrationsmuster dokumentiert. Es werden nicht alle Drittanbieter- oder benutzerdefinierten Szenarien abgedeckt.

## Produktempfehlungen versus Produktbeziehungen

Angesichts der sich ständig verändernden Komplexität von Online-Shopping, ist das, was am besten für Ihre Storefront funktioniert, oft eine Kombination aus mehreren Schlüsseltechnologien. Die Verwendung von [!DNL Product Recommendations]- [Produktbeziehungen](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/product-relationships/product-relationships.html) bietet Ihnen mehr Flexibilität bei der Promotion von Produkten. Sie können [!DNL Product Recommendations] mit Adobe AI nutzen, um Ihre Empfehlungen im benötigten Umfang intelligent zu automatisieren. Anschließend können Sie &quot;[ Produktregeln“ nutzen](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/product-relationships/product-related-rules.html) wenn Sie manuell eingreifen müssen und sicherstellen müssen, dass eine bestimmte Empfehlung an ein Zielkunden-Segment gesendet wird oder wenn bestimmte Geschäftsziele erfüllt werden müssen.

Produktempfehlungen ermöglichen Ihnen Folgendes:

- Wählen Sie aus neun verschiedenen intelligenten Empfehlungstypen, die auf den folgenden Bereichen basieren: Käuferbasiert, Artikelbasiert, Beliebtheit, Trend und Ähnlichkeit
- Verwenden Sie Verhaltensdaten, um Empfehlungen auf der Storefront-Journey des Käufers zu personalisieren
- Messen Sie Schlüsselmetriken, die für jede Empfehlung relevant sind, damit Sie die Auswirkungen Ihrer Empfehlungen besser verstehen können

## Produktempfehlungen - Demo

In diesem Video erfahren Sie mehr über [!DNL Product Recommendations]:

>[!VIDEO](https://video.tv.adobe.com/v/343991?quality=12)

## Richtlinie zur Aufbewahrung von Katalogdaten

Der [!DNL Product Recommendations]-Service ist auf Katalogdaten angewiesen, die mit Ihrer Adobe Commerce-Umgebung synchronisiert bleiben. Inaktive Kataloge oder Umgebungen, die keine Daten mehr abfragen, können in den Ruhezustand übergehen. Dies wirkt sich darauf aus, was der Service bis zur erneuten Aktivierung zurückgibt.

Wenn Sie 90 aufeinander folgende Tage lang keine Abfrage für die Katalogdaten in Ihrer **Test**-Umgebung senden, werden die Katalogdaten auf den Ruhezustand eingestellt und es werden keine Daten für eine Abfrage zurückgegeben. Katalogdaten in Ihrer **Produktions** Umgebung sind von der 90-Tage-Regel nicht betroffen.

Wenn Ihre Umgebung 45 Tage nach **Erstellung einen** Katalog hat, werden die Katalogdaten auf den Ruhezustand eingestellt und es werden keine Daten für eine Abfrage zurückgegeben. Dies gilt sowohl für Produktions- als auch für Testumgebungen.

### Reaktivieren von Katalogdaten

Um Katalogdaten nach dem Ruhezustand wiederherzustellen[ senden Sie eine Support-Anfrage ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#experience-league-start-page) dem Titel &quot;[!DNL Product Recommendations] erneut aktivieren“ und schließen Sie die Umgebungs-IDs ein. Katalogdaten sollten innerhalb weniger Stunden wiederhergestellt werden.
