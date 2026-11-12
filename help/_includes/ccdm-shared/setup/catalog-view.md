---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%
---
<!--This shared include file contains the conceptual and architecture overview of catalog views for Adobe Merchandising Services-->

Eine Katalogansicht definiert die Produkte und Preise, die ein Kunde abrufen kann. Es kombiniert Katalogquellen, Katalogschichten, Richtlinien und Preisbücher, um verschiedene Marken, Regionen, Geschäftseinheiten oder Kanäle zu unterstützen.

## Was sind Katalogansichten?

Katalogansichten definieren, wie Ihr Produktkatalog organisiert und angezeigt wird. Sie dienen als Filter, die Folgendes bestimmen:

- **Welche Produkte sichtbar sind** basierend auf der Unternehmensstruktur (Marken, Regionen, Händler)
- **Welche Preise werden angezeigt** durch verknüpfte Preisbücher
- **Filterung von Produkten** Verwendung von Richtlinien (Attribute wie Marke, Modell, Kategorie)
- **Was [Katalogquelle](/help/optimizer/setup/catalog-sources.md) wird basierend** Attributen wie „locale“ verwendet
- **Wer kann auf die Daten der Ansicht zugreifen** über [Katalogschutz](private-catalog-view.md) und [eingeschränkte Zugriffsschlüssel](restricted-access-keys.md)

Sie können beispielsweise separate Katalogansichten erstellen für:

- Eine Marke oder Geschäftseinheit
- Eine geografische Region
- Ein Händler- oder Partnerkanal
- Ein Kundensegment mit bestimmten Preisen

## Überblick über die Architektur

Katalogansichten sind Teil des Adobe Merchandising Services-Frameworks, das das in Adobe Commerce Foundations verwendete Website-, Store- und Store-Review-Framework durch ein flexibleres Modell ersetzt:

![[!DNL Merchandising Services] Architektur](/help/assets/ccdm-shared/setup/merchandising-svcs-architecture.png)

### Funktionsweise

**1. Datenaufnahme**
Katalogdaten aus einem Adobe Commerce-Backend oder einem anderen Drittanbieter-Backend (z. B. PIM oder ERP) und anderen Systemen werden in die Adobe Merchandising Services-Datenschicht aufgenommen. Jede SKU enthält Gebietsschema-Informationen und Produktattribute, die Katalogansichten, Richtlinien und Gebietsschemata zugeordnet sind. Der Datenerfassungsprozess hängt vom Quellsystem und der Integrationsmethode ab:

- **Adobe Commerce-Backend**: Das System exportiert Commerce-Katalog-Feeds, ordnet sie dem von der Datenaufnahme-REST-API erwarteten Format zu und synchronisiert Feed-Daten mit der Adobe Merchandising Services-Datenschicht. In diesem Modell verwaltet Adobe Commerce die Erstsynchronisierung und nachfolgende Aktualisierungen. Zu den Feeds gehören Produkte, Kategorien, Produktattribute, Preise und Preisverzeichnisse.

- **Backend- oder Quellsystem eines Drittanbieters** - Ein Connector oder Integrations-Service ruft Katalogdaten aus der Quelle ab - über APIs, Ereignisse oder Export-Feeds, ordnet sie dann dem Schema des zusammensetzbaren Katalogdatenmodells (CCDM) zu und validiert sie und synchronisiert die Daten mithilfe der Datenaufnahme-REST-API mit der Adobe Merchandising Services-Ebene. Die Integration ist für das anfängliche Laden und das Senden späterer Änderungen verantwortlich. Ein plattformspezifischer Connector, z. B. der [Salesforce Commerce Connector](https://experienceleague.adobe.com/de/docs/commerce/optimizer/developer/salesforce-connector) von Adobe, kann einen Ausgangspunkt bieten.

**2. Unified Base Catalog**
Die erfassten Daten erstellen einen einheitlichen Basiskatalog in der Katalog-Service-Datenpipeline. Durch diese zentrale Quelle werden Datenduplikate in allen Geschäftsbereichen vermieden.

**3. Katalogansichten**
Mehrere Katalogansichten stellen verschiedene Geschäftseinheiten dar (z. B. „Texas Retail“, „Texas Retail Seasonal„). Gebietsschemata, Richtlinien und Preisverzeichnisse können aus Gründen der Flexibilität über Katalogansichten hinweg gemeinsam genutzt werden.

**4. Multi-Channel-Versand**
Die gefilterten Katalogdaten werden an Ziele wie Edge Delivery Services, Marktplätze, Werbeplattformen und benutzerdefinierte Mikro-Storefronts bereitgestellt. Weitere Informationen zur Bereitstellung von Katalogdaten finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/).

Wenn eine Katalogansicht aktiviert **[!UICONTROL Catalog Protection]**, erfordert der Versand an dieses Ziel ein gültiges signiertes Token von einem zugewiesenen [eingeschränkten Zugriffsschlüssel](restricted-access-keys.md). Nicht autorisierte Anfragen werden abgelehnt, anstatt Katalogdaten zu erhalten.

### Schlüsselkomponenten

| Komponente | Zweck | Beispiel |
|---|---|---|
| **Katalogansicht** | Geschäftseinheit oder Vertriebskanal | Händlernetzwerk, regionaler Store |
| **Richtlinie** | Produktfilter basierend auf Attributen | Marke, Modell, Kategorie |
| **Gebietsschema** | Einstellung für Sprache/Region | en-US, fr-CA, es-MX |
| **Preisbuch** | Preisstruktur | Einzelhandel, Großhandel, Mitarbeiter |
| **Schlüssel für eingeschränkten Zugriff** | Anmeldedaten mit signiertem Token, die Zugriff auf eine geschützte Katalogansicht gewähren | Partner-Portal-Schlüssel, B2B-Preisschlüssel |

### Datenfluss

1. **Aufnehmen** - Katalogdaten aus dem Adobe Commerce-Backend
2. **Prozess** - Anwenden von Katalogansichten, Richtlinien und Preisen
3. **Versand** - Bereitstellung eines gefilterten Katalogs an Storefronts, Marktplätze usw.

## Wichtigste Funktionen

| Funktion | Vorteil |
|---|---|
| **Single Base Catalog** | Eliminierung von Datenduplikaten in allen Geschäftsbereichen |
| **Flexible Preisgestaltung** | Mehrere Preisbücher pro SKU für verschiedene Kundensegmente |
| **skalierbar** | Effiziente Verwaltung von mehr als 200 Millionen SKUs |
| **Multi-Channel** | Kataloge für Storefronts, Marktplätze und Werbeplattformen bereitstellen |
| **Echtzeit-Updates** | Schnelles Aktualisieren von Katalogdaten für Promotions und Kampagnen |
| **Private Katalogansichten** | Katalogansicht mithilfe der Validierung signierter Token auf autorisierte Clients beschränken |

## Anwendungsszenarien

### Mehrmarkenkonglomerat

**Herausforderung**: Verwaltung mehrerer Marken, Länder und Sprachen<br>
**Lösung**: Einzelner Katalog mit Katalogansichten für jede Kombination aus Marke und Region

### Autoteilehändler

**Challenge**: 3.000 Händler mit den gleichen Produkten, aber unterschiedlichen Preisen<br>
**Lösung**: Ein Katalog mit händlerspezifischen Katalogansichten und Preisbüchern

### Retailer mit mehreren Standorten

**Challenge**: Unterschiedliche Preise und Lagerbestände pro Standort<br>
**Lösung**: Standortbasierte Katalogansichten mit regionsspezifischen Richtlinien

>[!NOTE]
>
>Detaillierte Informationen zur Aufnahme und Bereitstellung von Katalogdaten finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/).
