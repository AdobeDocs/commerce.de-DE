---
title: Entwerfen einer Commerce-Plattform für Käufer und KI-Agenten
description: Erfahren Sie, wie Sie eine Commerce-Plattform aufbauen, die menschlichen Käufern und KI-Agenten aus einer einzigen Datenquelle dient, von der Kataloggestaltung und MCP bis zur Telemetrie.
role: Developer, Leader
recommendations: noCatalog
autotag-review: '2026-10-20T20:32:40.424Z'
TQID: 'https://experienceleague.adobe.com/ub4oTxr4IfLGgqqz0S1npY-sn0FZb3mKq-GdjD9eDjI'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
topic_v2:
  - id: b4dd41a7-ccf8-4e9d-918e-acaab534a307
    internal-label: Data quality
  - id: bbbea26f-9621-49eb-9ab8-e06fb3bbce8c
    internal-label: Artificial intelligence
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
    internal-label: Governance
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: f54c816fd23786ec519d5c890bc2664c3dcf8c6f
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 0%
---

# Entwerfen einer Commerce-Plattform für Käufer und KI-Agenten

<table style="table-layout:auto">
<tr style="border: 0;">
   <td valign="middle" style="vertical-align: middle;"><img alt="Porträt von Surya Lamech" src="../../assets/guidance-and-insights/agentic-commerce-author-avatar-slamech.png" width="96"><br><strong>Surya Lamech</strong><br><em>Principal Product Marketing Manager</em></td>
</tr>
</table>

![Hero-Illustration einer agentischen Commerce-Plattform, auf der Menschen und KI-Agenten mit einer einzigen Quelle der Wahrheit interagieren](../../assets/guidance-and-insights/agentic-commerce-hero.png "Die architektonischen Grundlagen einer agentischen Commerce-Plattform")

*Entwicklung einer Commerce-Plattform, auf der Menschen und KI-Agenten mit einer einzigen Quelle der Wahrheit interagieren.*

Commerce befindet sich in einem Strukturwandel. Kunden verlassen sich nicht mehr ausschließlich auf Suchmaschinen oder das Durchsuchen von Storefronts, um ihre Optionen zu erkunden. Stattdessen greifen sie auf LLM-gestützte Schnittstellen, chatbasierte Assistenten und agentische Einkaufstools zurück, um Fragen zu stellen, Produkte über Einzelhändler hinweg zu vergleichen und die Entscheidungsfindung in der Frühphase zu beschleunigen.

Diese Schnittstellen sind leistungsstarke Motoren für Entdeckung, Ausbildung und Vergleich. Sie helfen Kunden, Anforderungen zu klären, Kompromisse einzuschätzen und Auswahlmöglichkeiten schneller einzugrenzen als herkömmliches Browsen.

Doch wenn es Zeit ist, einen Kauf abzuschließen, bevorzugen die Kunden immer noch überwiegend vertrauenswürdige Storefronts und markeneigene Websites, auf denen Zahlungssicherheit, Auftragstransparenz und Post-Purchase-Service gut verstanden werden. Die Konversion bleibt in Umgebungen verankert, in denen bereits Vertrauen aufgebaut wurde.

Wichtig ist, dass KI in dieser Phase nicht verschwindet. Wenn Kundinnen und Kunden in die Storefront einer Marke gelangen, kann die agentische KI das Erlebnis verbessern, indem sie die Produktauswahl führt, Empfehlungen in Echtzeit personalisiert, Einwände beantwortet, ergänzende Elemente bündelt und den Checkout optimiert. In diesen vertrauenswürdigen Umgebungen wird KI zu einem Konversionsbeschleuniger, was die Abschlussraten verbessert und den durchschnittlichen Bestellwert erhöht.

Um in dieser neuen Landschaft wettbewerbsfähig zu bleiben, benötigen Unternehmen eine Commerce-**, die strukturiert, verwaltet und für den menschlichen und Agentenkonsum optimiert**. Adobe Commerce ist für diesen Wandel konzipiert und die folgenden Grundsätze beschreiben, was erforderlich ist, um wirklich bereit für den Agenten zu sein.

## Eine Commerce-Architektur, die für zwei Zielgruppen erstellt wurde

![Abbildung mit Storefronts und Apps für Menschen auf der linken Seite und Chat-Assistenten und autonomen Agenten auf der rechten Seite, die beide aus einem zentralen Commerce-Kern von Produkten, Preisen, Inventar, Werbeaktionen, Warenkorb und Checkout stammen, der über APIs und MCP verfügbar gemacht wird](../../assets/guidance-and-insights/agentic-commerce-foundational-model.png){width="800" zoomable="yes"}

*Was Kunden sehen und was Agenten konsumieren, bleibt konsistent, präzise und markenintern.*

Der moderne Commerce-Stack muss jetzt zwei gleichermaßen wichtige Zielgruppen bedienen: Personen und KI-Agenten. Menschlich orientierte Erlebnisse wie Storefronts und Apps bleiben für die Interaktion, den Markenausdruck und die Kundenloyalität unverzichtbar. Daneben gibt es jedoch eine sich schnell ausbreitende Oberfläche, die auf die Agenten zugeschnitten ist: maschinenlesbare Endpunkte, die LLMs und autonome Agenten mit strukturierten Fakten, verwalteten Inhalten und Transaktionsfunktionen versorgen.

Agenten erzielen die beste Leistung bei der Arbeit mit sauberen, strukturierten Daten, die über vorhersehbare APIs bereitgestellt werden, anstatt zu versuchen, JavaScript zu interpretieren oder Geschäftsregeln aus Präsentationsebenen abzuleiten. Das bedeutet, dass Produktspezifikationen, Preise, Verfügbarkeit und Werbelogik als adressierbare Ressourcen vorhanden sein müssen, die über APIs und standardisierte Schnittstellen wie MCP-Server bereitgestellt werden. Wenn sowohl für Menschen als auch für Agenten bestimmte Oberflächen aus derselben zugrunde liegenden Wahrheitsquelle schöpfen, stellen Marken sicher, dass das, was Kunden sehen und was Agenten konsistent, genau und markenintern konsumieren.

Diese Architektur mit zwei Oberflächen bildet die Grundlage für den agentischen Handel.

## Ein Katalog für maschinelles Argumentieren

![Diagramm mit strukturierten Produktentitäten (SKUs, Attribute, Varianten, Bundles, Preise und Verfügbarkeit), die von Katalogebenen und Richtlinien geformt und dann über Katalogansichten an eine MarkenStorefront, einen Marktplatz, einen Partner-Feed, eine Mobile App und eine KI- oder Agentenoberfläche bereitgestellt werden](../../assets/guidance-and-insights/agentic-commerce-agent-interaction.png){width="800" zoomable="yes"}

*Eine kontrollierte Quelle der Wahrheit, geformt pro Kanal, ohne jemals die Produktdaten zu verzerren.*

Der Katalog bildet den Kern des agenten Handels. Sie muss für Maschinen strukturiert, auf Konformität ausgelegt und flexibel genug sein, um die gesamte Bandbreite an menschlichen und agenten Interaktionen zu unterstützen. Das Katalogmodell von Adobe Commerce, das auf Katalogansichten, Richtlinien, Ebenen und strukturierten Produktentitäten basiert, ist für diese Zukunft konzipiert.

Katalogansichten definieren, wo und wie Produktdaten bereitgestellt werden, sei es für eine Storefront, einen Marktplatz, einen Partner-Feed oder eine KI-Oberfläche. Jede Ansicht kann ihre eigenen Regeln für Produktverfügbarkeit, Preise und Attributsichtbarkeit aufweisen, um sicherzustellen, dass die richtigen Informationen den richtigen Verbraucher oder Agenten erreichen. Katalogebenen ermöglichen es Ihnen, Produktdaten für bestimmte Kanäle anzureichern, ohne die Quellproduktdaten zu ändern. Richtlinien regeln die Kundenberechtigung, die Inventarlogik, die Preisgestaltung und die Einhaltung von Vorschriften. Kombiniert haben Unternehmen eine genaue Kontrolle darüber, auf welche Katalogdaten ein Agent zugreifen oder darauf reagieren kann.

## MCPs als gemeinsame Sprache für Agenten

![Abbildung mit Shopping-Assistenten, Support-Mitarbeitern und Entwickler-Tools, die Anfragen über das Model Context Protocol (das auch das Commerce MCP und das Developer MCP beinhaltet) an Adobe Commerce-Funktionen wie Warenkorberstellung, Checkout, Zahlungen, Inventar sowie Promotions und Rücksendungen senden](../../assets/guidance-and-insights/agentic-commerce-reference-stack.png){width="800" zoomable="yes"}

*MCP standardisiert, wie Agenten Aktionen in natürlicher Absicht anfordern, und Adobe Commerce führt sie als gesteuerte, deterministische Aktionen aus.*

Damit Agent Commerce End-to-End funktioniert, müssen E-Commerce-Plattformen standardisierte Protokolle unterstützen, die es Agenten ermöglichen, Aktionen sicher auszuführen, wie z. B. Warenkorberstellung, Checkout-Initiierung, Zahlungsorchestrierung, Inventarvalidierung, Promotions und Rücksendungen.

Durch native Unterstützung des Model Context Protocol (MCP) strukturiert und stellt Adobe Commerce-Funktionen auf eine Weise bereit, die LLMs konsistent interpretieren können. MCP standardisiert, wie Produktdaten, Geschäftsregeln und Transaktionskontext LLMs präsentiert werden, um sicherzustellen, dass Agenten zuverlässig über sie reden können, während Unternehmen Governance und Kontrolle behalten. Mit dem Commerce MCP können Unternehmen benutzerdefinierte agentische Erlebnisse wie Einkaufsassistenten, die Erstellung von Agentenkörben, Support-Agenten und vieles mehr erstellen.

Das Entwickler-MCP bietet KI-gestützte Entwicklungsfunktionen, die es Teams ermöglichen, die Plattformfunktionalität schnell zu erweitern und zusammensetzbare Storefront-Komponenten bereitzustellen. Durch die direkte Einbettung von Adobe-Wissensquellen, -Dokumentation und Best Practices für die -Plattform in den Entwicklungs-Workflow unterstützt das Entwickler-MCP neue Entwickler dabei, schneller einzusteigen und vom ersten Sprint an produktiv zu werden. Es generiert Code, der bewährten Architekturmustern folgt, leicht zu pflegen ist und die Qualitätsstandards erfüllt, die Enterprise Commerce fordert. Das Ergebnis ist ein beschleunigter Weg von der Idee zur Produktion, der Unternehmen die Geschwindigkeit gibt, mit der sie experimentieren, iterieren und Commerce-Funktionen vor Wettbewerbern ausliefern können.

Adobe unterstützt auch agentische Commerce-Protokolle wie das Agentic Commerce Protocol (ACP) und das Universal Commerce Protocol (UCP), um die Produkterkennung und sichere, standardbasierte Transaktionsinteraktionen zwischen Agenten und Ihrer Storefront zu ermöglichen.

Durch die Verwendung offener Protokolle anstelle von Punktintegrationen stellt Adobe sicher, dass Commerce-Interaktionen gesteuert, deterministisch und sicher sind, und ermöglicht gleichzeitig ein neues Modell der Interaktion zwischen Agenten und Händlern, bei dem vertrauenswürdige Agenten unter klar definierten Richtlinien direkt handeln können.

## Telemetrie und kontinuierliche Optimierung

In einem KI-vermittelten Ökosystem wird die Telemetrie zum strategischen Vorteil. Unternehmen benötigen Einblicke in die Darstellung ihrer Marke über LLMs hinweg, in die Genauigkeit der Darstellung ihrer Inhalte durch Agenten, in die Konversion von agentenbezogenem Traffic und in die Bereiche, in denen Governance- oder Compliance-Probleme auftreten. Sie benötigen außerdem operative Telemetrie, mit der die Ausführung von Agenten und die Anomalieerkennung über Agenteninteraktionen hinweg verfolgt werden.

Adobe bietet Ihnen Einblicke in die Darstellung Ihrer Produkte in LLMs, verbessert Produktdaten mit KI und erhöht die Lesbarkeit Ihrer Daten durch LLMs. Durch das Hinzufügen eines aussagekräftigen Kontexts zu Ihrem Katalog hilft LLMs nicht nur, Ihre Produkte genau zu entdecken, sondern auch zu verstehen, was sie sind, für wen sie sind und warum sie für Kunden wichtig sind.

Darüber hinaus können Ihre Produktdetailseiten, die für den menschlichen Verzehr optimiert wurden, häufig Daten enthalten, die für Agenten unsichtbar sind. Diese Daten könnten hinter Modalen, Konfiguratoren und verknüpften Seiten verborgen sein. Support-Mitarbeiter verstehen Produktkategorien, Bundles und Varianten möglicherweise nicht vollständig. Adobe kann diese kritischen fehlenden Informationen identifizieren und als JSON-LD am Edge bereitstellen, damit Agenten alle relevanten Produktdaten erhalten.

Durch diese konstante Telemetrie und Optimierung können Marken maximale Sichtbarkeit sicherstellen und über LLMs hinweg wettbewerbsfähig bleiben.

## Warum das wichtig ist

E-Commerce ist nicht mehr auf Storefronts und Suchergebnisse beschränkt. LLMs und autonome Agenten vermitteln zunehmend Discovery, Evaluation und Transaktionen. Dieser Wandel verändert die Mechanik der Sichtbarkeit, die Dynamik der Kontrolle und die Grundlagen des Vertrauens. Die Marken, die gewinnen, werden für eine KI-native Stiftung architektonisch arbeiten.

## Ergänzende Leitlinien

* [Katalogansichten](/help/optimizer/setup/catalog-view.md)
* [Katalogebenen](/help/optimizer/setup/catalog-layer.md)
* [Richtlinien](/help/optimizer/setup/policies.md)
* [Entwickler-Tools für KI-Codierung für Adobe Commerce App Builder](/help/cloud-service/migration/coding-tools.md)
* [Commerce-APIs](../../apis/commerce-apis.md)
* [Commerce Developer Agent-Wiedergabeliste](https://experienceleague.adobe.com/de/playlists/commerce-developer-agent) - Sehen Sie sich technische Videos zum Einrichten und Verwenden des Commerce Developer Agent an.
