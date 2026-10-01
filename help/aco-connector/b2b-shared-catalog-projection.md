---
title: B2B-Shared-Catalog-Prognose
description: Erfahren Sie, wie der B2B-Connector freigegebene Adobe Commerce B2B-Kataloge in geschützte Commerce Optimizer-Katalogansichten projiziert und wie Storefronts den Käuferzugriff auflösen und autorisieren.
feature: Integration, Configuration
role: Admin, Developer
level: Intermediate
TQID: 'https://experienceleague.adobe.com/b37PBjcVQXRSLrB6c7nEf3A3U5cuLs1lQzwPUbp9fdA'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: a3ade1a31d3c2905b601f71bda118de89c43cf59
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%
---
# Projektion des freigegebenen B2B-Katalogs

Die [!DNL Adobe Commerce Optimizer Connector for B2B] Projekte [!DNL Adobe Commerce] freigegebene Kataloge und Unternehmenszuweisungen in geschützten [!DNL Adobe Commerce Optimizer] Katalogansichten.

## Basissynchronisierung und B2B-Projektion

Die -[!DNL Adobe Commerce Optimizer Connector] synchronisiert Katalog- und Preis-Feeds, ordnet Store-Ansichten Katalogquellen, Websites Preislisten und Kundengruppen Preislisten zu.

Die [!DNL Adobe Commerce Optimizer Connector for B2B] projiziert das Sortiment und die Preise jedes benutzerdefinierten freigegebenen Katalogs in eine geschützte Ansicht. Adobe Commerce wählt die Ansicht mit der Unternehmenszuweisung des Käufers aus. Der Schlüssel für den eingeschränkten Zugriff überprüft signierte Anfragen, bestimmt jedoch nicht den Katalogzugriff. Adobe Commerce ist das „System of Record“ für von Connectoren verwaltete Katalog-, Preis- und B2B-Projektionsdaten. Verwalten Sie die Produkterkennung und Empfehlungen in der [!DNL Adobe Commerce Optimizer].

## Daten-Mapping

Die B2B-Projektion kombiniert synchronisierten Kataloginhalt und Preise mit dem Sortiment des freigegebenen Katalogs und dem Unternehmenszuweisungskontext.

![Diagrammzuordnung [!DNL Adobe Commerce] Store-Ansichten, Preisen, freigegebenen Katalogen und Unternehmenszuweisungen zu projizierten privaten Katalogansichten in [!DNL Adobe Commerce Optimizer]](./assets/b2b-catalog-projection-mapping.svg){width="800"}

| [!DNL Adobe Commerce] | [!DNL Adobe Commerce Optimizer] | Zweck |
| --- | --- | --- |
| Store- und Produktdaten aktiviert | Katalogquelle | Liefert lokalisierte Produktinhalte. |
| Preise für Websites und Kundengruppen | Preisbuch | Liefert die geltenden Preise, gewährt jedoch keine Zugangsberechtigung |
| Benutzerdefiniertes Sortiment des freigegebenen Katalogs | Richtlinie | Filtert die Katalogansicht nach dem freigegebenen Katalogsortiment. |
| Benutzerdefinierter freigegebener Katalog und aktivierte Store-Ansicht | Private Katalogansicht | Erstellt für jede Kombination eine geschützte Ansicht mit der entsprechenden Katalogquelle, Richtlinie und dem entsprechenden Preisbuch. |
| Unternehmenszuweisung zu einem freigegebenen Katalog | Aufgelöster Käuferkontext | Ermöglicht dem authentifizierten Backend, die mit dem Unternehmen des Käufers verknüpfte Katalogansicht aufzulösen. |
| Schlüssel für eingeschränkten Zugriff, der einer geschützten Ansicht zugewiesen ist | Katalogschutz | Autorisiert Anfragen an die geschützte Katalogansicht, wählt jedoch keine Preise aus. |

Jede private Katalogansicht kann nur auf ein Preisbuch verweisen. Store-Ansichten mit derselben Website und demselben Preiskontext für Kundengruppen können ein Preisbuch gemeinsam nutzen, während verschiedene lokalisierte Katalogquellen verwendet werden. Der Connector erstellt kein Preisbuch pro freigegebenem Katalog.

Der standardmäßig freigegebene Katalog wird nicht als private B2B-Katalogansicht projiziert.

## Laufzeitautorisierung

Nachdem sich ein Käufer angemeldet hat, authentifiziert das Commerce-Backend die Sitzung und verwendet die Unternehmenszuweisung und Store-Ansicht des Käufers, um die entsprechende Katalogansicht und das entsprechende Preisbuch aufzulösen.

Die Storefront sendet bei jeder Merchandising-API-Anfrage die Katalogansichts-ID, die Preisbuch-ID und das signierte Token. [!DNL Adobe Commerce Optimizer] überprüft die RS256-Signatur für das JWT anhand der eingeschränkten Zugriffsschlüssel, die der Katalogansicht zugewiesen sind. Katalogdaten werden nur zurückgegeben, wenn das Token und der Schlüssel gültig und nicht abgelaufen sind.

![Laufzeitautorisierungsfluss für B2B-Kataloganfragen von einem Erstkäufer über eine Storefront und das Commerce-Backend an [!DNL Adobe Commerce Optimizer]](./assets/b2b-catalog-runtime-authorization.svg){width="700"}

Bei Anfragen zum privaten Katalog senden Sie diese Kopfzeilen:

| Kopfzeile | Zweck |
| --- | --- |
| `AC-View-ID` | Identifiziert die Katalogansicht. |
| `AC-Price-Book-ID` | Gibt das zu verwendende Preisbuch an. |
| `AC-Catalog-View-Access-Token` | trägt das signierte JWT, das den Zugriff auf die geschützte Katalogansicht autorisiert. |

Die vollständigen Anforderungen für Anfragen und Token finden Sie unter [Merchandising-API](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/using-the-api#authentication)Authentifizierung und [Überprüfen des Zugriffs auf eine private Katalogansicht](/help/optimizer/setup/private-catalog-view.md#verify-access-is-enforced).

## Schutzgrenze

Der Katalogschutz deckt nur Katalog- und Suchanfragen ab. Es werden keine Warenkorb-, Checkout- oder Bestellvorgänge gesichert. Erzwingen der Kaufeignung in Adobe Commerce oder dem verbundenen Transaktionssystem.

## Projektionseinrichtung und -überwachung

Der B2B-Connector projiziert private Katalogansichten, Richtlinien, Preisbuchreferenzen und die Konfiguration von eingeschränkten Zugriffsschlüsseln aus [!DNL Adobe Commerce]. Diese vom Connector verwalteten Projektionsobjekte müssen nicht manuell erstellt werden. Setup-Anweisungen finden Sie unter [Erste Schritte mit dem B2B-Connector](get-started-b2b-shared-catalogs.md).

Informationen zum Überwachen projizierter Katalogansichten und zum Ausgleichen der Konfigurationsabweichung finden Sie unter [Überwachen der Synchronisierung von Katalogansichten](catalog-view-sync-status.md). Informationen zum Verwalten der zugewiesenen Schlüssel finden Sie unter [Verwalten von eingeschränkten Zugriffsschlüsseln für B2B-freigegebene Kataloge](restricted-access-keys.md).
