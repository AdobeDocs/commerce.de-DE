---
title: Integrieren  [!DNL Adobe Commerce] mit [!DNL Adobe LLM Optimizer]
description: Verbinden [!DNL Adobe Commerce] mit [!DNL Adobe LLM Optimizer] , um Katalogsignale in LLMs zu überwachen und genehmigte Katalogoptimierungen bereitzustellen.
role: Admin, User, Leader
recommendations: noCatalog
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: 47348a44ff7c5f890c10594f44cae6e771be046f
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Integrieren von [!DNL Adobe Commerce] mit [!DNL Adobe LLM Optimizer]

>[!IMPORTANT]
>
>Der Zugriff auf diese Integration ist eingeschränkt. Weitere Informationen erhalten Sie von Ihrem technischen Kundenbetreuer.

[!DNL Adobe LLM Optimizer] ist eine Unternehmenslösung, mit der Marken überwachen, analysieren und optimieren können, wie ihre Inhalte in Antworten von großen Sprachmodellen (LLMs) und KI-Assistenten angezeigt werden. Da Käufer zunehmend KI-Tools für die Forschung und Produktsuche verwenden, trägt LLM Optimizer dazu bei, dass Ihre Marke und Ihr Katalog korrekt zitiert und im Kontext dargestellt werden.

In diesem Handbuch wird beschrieben, wie **[!DNL Adobe Commerce]** in diesen Workflow passt, wenn Ihr Produktkatalog in Commerce gespeichert wird. Sie erfahren, welche Funktionen verfügbar werden, welche Konfiguration erforderlich ist und wie sich bereitgestellte Optimierungen im Admin-Bereich und über Aufnahmekanäle hinweg verhalten.

>[!NOTE]
>
>[!DNL Adobe LLM Optimizer] ist eine eigenständige Adobe-Lösung. Für zentrale Überwachungs- und Opportunity-Workflows sind keine [!DNL Adobe Experience Manager] (AEM) oder andere Adobe-Programme erforderlich. Commerce-spezifische Bereitstellungsaktionen gelten nur, wenn Ihr Katalog mit LLM Optimizer verbunden ist und Sie genehmigte Änderungen in [!DNL Adobe Commerce] pushen.

## Was die Integration ermöglicht {#what-integration-enables}

Wenn Sie LLM Optimizer mit Ihrem [!DNL Adobe Commerce] verbinden, können Sie von umfangreichen Inhaltseinblicken zu (**)** Empfehlungen wechseln:

- **Identifizieren** Lücken und Inkonsistenzen in Katalogdaten, wie z. B. Titel, Beschreibungen und strukturierte Signale, die sich darauf auswirken, wie LLMs Ihre Produkte interpretieren.
- **Überprüfen** Verbesserungsvorschläge mit unterstützendem Kontext, einschließlich Begründungen und Vorher-Nachher-Vergleichen.
- **Stellen Sie** Optimierungen wie Produktnamen- und Beschreibungsaktualisierungen direkt im Commerce-Katalog bereit, um sicherzustellen, dass Admin-Workflows, Raster und Storefront-orientierte Daten aufeinander abgestimmt bleiben.

Wenn die Katalogquelle [!DNL Adobe Commerce] ist, kann Adobe den vollständigen End-to-End-Workflow unterstützen: das automatische Erkennen von Opportunities, das Vorschlagen von Änderungen und das Anwenden genehmigter Fehlerbehebungen. Für Kataloge, die von außerhalb von Commerce stammen, kann LLM Optimizer weiterhin analysieren und Verbesserungen vorschlagen. Die Anwendung der Änderungen hängt jedoch von Ihrem Integrationsmodell ab (z. B. einem gespiegelten Katalog oder manuellen Aktualisierungen). Siehe [Integrationsbeschränkungen und -grenzen](boundaries-limits.md).

## Für wen ist das? {#who-this-is-for}

- **Digital Marketer und Merchandiser** die möchten, dass Produktdaten in LLM-basierten Antworten korrekt und konsistent sind und eine kontrollierte Möglichkeit zur skalierten Verbesserung der Katalogkopie benötigen.
- **Commerce-Administratoren** die für Katalogintegrität, Admin-Prozesse und Integrationen (API, CSV, PIM) verantwortlich sind, die Produktattribute befüllen.

## Voraussetzungen {#prerequisites}

Die folgenden Voraussetzungen gelten, wenn Sie (**) Zugriff** die Adobe Commerce-Integration mit Adobe LLM Optimizer haben. Weitere Informationen erhalten Sie von Ihrem technischen Kundenbetreuer.

- Ihre Storefront kann durch LLM-orientierte und agentische Bots crawlen werden, wobei diese crawlen-Funktion Teil Ihrer Mess- und Optimierungsstrategie für LLM Optimizer ist (eine allgemeine Voraussetzung für katalogbewusste Einblicke).
- Für Commerce-unterstützte Bereitstellungs-Workflows sind die erforderlichen Commerce-Services und die Katalogkonnektivität aktiviert und in gutem Zustand. Die Einrichtung auf Aufgabenebene wird unter [Adobe Commerce mit LLM Optimizer verbinden](get-started/connect-to-llmo.md) beschrieben.

Sie sollten auch verstehen, wie Daten zwischen Systemen verschoben werden:

### Datenfluss auf hoher Ebene {#high-level-data-flow}

Grundsätzlich folgen Katalogoptimierungen zwei Mustern (Ihr Projekt kann eines oder beide verwenden, je nach Funktion):

| Richtung | Zweck |
| --- | --- |
| **Commerce-Katalog -> LLM Optimizer** | Katalog- und URL-Signale dienen als Feed für Opportunities und Vorschläge in der LLM Optimizer-Benutzeroberfläche. |
| **LLM Optimizer -> Commerce** | Nachdem Sie eine Bereitstellungsaktion genehmigt haben, werden Aktualisierungen am Produktnamen und an der Beschreibung in den Commerce-Hauptkatalog geschrieben, sodass sowohl die Admin- als auch die Storefront die optimierten Werte widerspiegeln. |

### [!DNL Adobe Commerce] im Vergleich zu Katalogen von Drittanbietern {#commerce-vs-third-party}

| Katalogquelle | Typische LLM Optimizer-Abdeckung |
| --- | --- |
| **[!DNL Adobe Commerce]** | Umfassende Unterstützung für Identifikation und Vorschläge sowie Bereitstellung von genehmigten Katalogfeld-Aktualisierungen, die Sie konfigurieren. |
| **Drittanbieter-Commerce** | Identifikation und Vorschläge werden unterstützt. Die automatisierte Bereitstellung im Händlersystem hängt vom Export, von Spiegelung oder Partner-Workflows ab und nicht von direkten Schreibvorgängen im Quellkatalog des Händlers. |

## Catalog Agent, Storefront MCP und LLM Optimizer {#catalog-agent-and-mcp}

Ihr [!DNL Adobe Commerce] **Produktkatalog** ist das „System of Record“ für Produktdaten: Namen, Beschreibungen, Attribute, Preise und Inventar. Um die KI-gestützte Erkennung und Optimierung zu unterstützen, ist **Adobe Commerce Storefront MCP** (Model Context Protocol) eine strukturierte Schnittstelle zwischen Ihren Commerce-Live-Katalogdaten und Adobe AI-Erlebnissen.

**Catalog Agent** befindet sich auf der Storefront MCP. Der Katalogagent ermöglicht es [!DNL Adobe LLM Optimizer], Kataloge und PDP-Kontexte abzufragen, anzureichern und damit zu arbeiten, indem er Lücken erkennt, Verbesserungen vorschlägt und Änderungen bereitstellt, wenn Sie diese genehmigen. Diese Funktionen tauchen in LLM Optimizer-Workflows auf, die unter [Verwenden von LLM Optimizer mit Adobe Commerce](get-started/use-llmo-with-commerce.md) beschrieben werden.

## Verbessern des Katalogagenten für Commerce für LLMs {#catalog-agent-optimizations}

Der Katalogagent behandelt die Auffindbarkeit durch zwei komplementäre Optimierungen: Anreicherung der Produktdetailseite und Anreicherung des Produktkatalogs.

### Anreicherung der Produktdetailseite {#pdp-enrichment-overview}

**Anreicherung von Produktdetailseiten (PDP)** schlägt Verfeinerungen des Inhalts von Produktseiten vor, damit Ihre Ware klarer gelesen wird, wenn Käufer Produkte über KI-Assistenten und ähnliche Tools entdecken. Ziel ist es, Klarheit und Konsistenz zu verbessern, ohne das Layout der Storefront zu ändern, über die Ihr Team bereits verfügt. Sie können Vorschläge in LLM Optimizer überprüfen und bereitstellen, wenn Sie bereit sind.

Überprüfen Sie nach der Bereitstellung die Live-Produktseite, um sicherzustellen, dass das Einkaufserlebnis weiterhin wie erwartet aussieht.

### Anreicherung des Produktkatalogs {#catalog-enrichment-overview}

**Produktkataloganreicherung** schlägt klarere **Produktnamen** und **Produktbeschreibungen) vor** bei denen die Kopie dünn, vage oder inkonsistent ist. Jeder Vorschlag enthält Kontext, damit Ihr Team entscheiden kann, was geändert werden soll. Wenn Sie eine Aktualisierung genehmigen, kann sie auf Ihren [!DNL Adobe Commerce] angewendet werden, sodass Admin, Storefront und andere Erlebnisse, die diese Felder verwenden, denselben Wortlaut widerspiegeln.

Da diese Felder in Commerce vorhanden sind, kann die einmalige Verbesserung eines Namens oder einer Beschreibung jedem Kanal, der diese Produktdaten liest, zugute kommen (je nachdem, wie und wann Ihre Systeme aktualisiert werden).

## Verwandte Themen {#related-topics}

- [Adobe Commerce mit LLM Optimizer verbinden](get-started/connect-to-llmo.md)
- [Verwenden von LLM Optimizer mit Adobe Commerce](get-started/use-llmo-with-commerce.md)
- [Integrationsbeschränkungen und -grenzen](boundaries-limits.md)
