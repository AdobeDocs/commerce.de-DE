---
title: Integrationsbeschränkungen und -grenzen
description: Erfahren Sie mehr über die Beschränkungen des Umfangs von Katalogen von Drittanbietern, die Abdeckung durch automatische Fehlerbehebung, crawlen Voraussetzungen, Überlegungen zur Unternehmensskalierung und eingeschränkte Beta-Zugriffsbeschränkungen für LLM Optimizer mit Commerce.
role: Admin, User, Leader
recommendations: noCatalog
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: 47348a44ff7c5f890c10594f44cae6e771be046f
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Integrationsbeschränkungen und -grenzen

>[!IMPORTANT]
>
>Der Zugriff auf diese Integration ist eingeschränkt. Weitere Informationen erhalten Sie von Ihrem technischen Kundenbetreuer.

Verwenden Sie dieses Thema, um Erwartungen zu definieren, was die [!DNL Adobe Commerce]- und [!DNL Adobe LLM Optimizer]-Integration automatisieren kann, wo Sie verantwortlich bleiben und welche Beschränkungen sich noch in der Entwicklung befinden.

## Einschränkungen beim Drittanbieterkatalog {#third-party-catalog}

Wenn der Katalog **nicht** in [!DNL Adobe Commerce] vorhanden ist:

- LLM Optimizer kann je nach Einrichtung weiterhin Probleme identifizieren und mithilfe gespiegelter oder importierter Katalogdaten Verbesserungen vorschlagen.
- **Direkte automatische Fehlerbehebung** in die Commerce-Plattform des Händlers ist nicht dasselbe wie das Schreiben in den Quellkatalog des Händlers. Möglicherweise benötigen Sie einen Spiegelkatalog, Export/Import oder Partnerautomatisierung, um Änderungen anzuwenden.

Bei Katalogen, die in Commerce gehostet werden, werden genehmigte Name- und Beschreibungsaktualisierungen im Datensatzsystem von Commerce aufgeführt. Siehe [Verwenden von LLM Optimizer mit Adobe Commerce](get-started/use-llmo-with-commerce.md).

## Maßstab und technische Grenzen {#scale-limits}

Große Kataloge und eine hohe URL-Anzahl können die crawlen-, Analyse- und Edge-Bereitstellungsmuster belasten.

## Crawlen- und Bot-Lesbarkeit {#crawling}

Aussagekräftige Katalog- und PDP-Einblicke gehen davon aus, dass LLM-relevante **Bots auf** gewünschten URLs zugreifen können und dass die Seiten so strukturiert sind, dass die automatisierte Analyse zuverlässig ist. Roboterregeln, Authentifizierung, Geoblocking und umfassende Personalisierung können die Abdeckung verringern.

## Verwandte Themen

- [Übersicht über die Integration](overview.md)
- [Adobe Commerce mit LLM Optimizer verbinden](get-started/connect-to-llmo.md)
- [Verwenden von LLM Optimizer mit Adobe Commerce](get-started/use-llmo-with-commerce.md)
