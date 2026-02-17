---
title: '[!DNL Catalog Service]'
description: Beschleunigen Sie Ihre Adobe Commerce-Storefront mit  [!DNL Catalog Service]  leistungsstarken GraphQL-API, die die Seitenladezeiten für Produktseiten, Kategorieseiten und Suchergebnisse reduziert.
role: Admin, Developer
recommendations: noCatalog
exl-id: 525e3ff0-efa6-48c7-9111-d0b00f42957a
source-git-commit: 4f3f8accd653dbee6fec45c065f55ff04b17bd2d
workflow-type: tm+mt
source-wordcount: '1353'
ht-degree: 0%

---

# [!DNL Catalog Service] für Adobe Commerce

[!DNL Catalog Service] für Adobe Commerce verbessert die Ladezeiten der Storefront, indem optimierte, schreibgeschützte Katalogdaten über eine dedizierte GraphQL-API bereitgestellt werden. Dieser Service wurde speziell entwickelt, um produktbezogene Seitenerlebnisse zu verbessern, was zu schnelleren Seitenladevorgängen und verbesserten Konversionsraten führt.

Die umfangreichen Ansichtsmodelldaten, die von der [!DNL Catalog Service] bereitgestellt werden, umfassen Produktdetails, Attribute, Bestand und Preise, was ein schnelles Rendern produktbezogener Storefronts ermöglicht, z. B.:

- Produktdetailseiten
- Produktlisten- und Kategorieseiten
- Suchergebnisseiten
- Produktkarussells
- Produktvergleichsseiten
- Alle anderen Seiten, die Produktdaten rendern, wie Warenkorb-, Bestell- und Wunschlistenseiten


## Wichtige Vorteile und Funktionen

- **Schnelleres Seitenladen**: Optimierte Abfragen für bis zu 10-mal schnelleren Abruf von Katalogdaten im Vergleich zum GraphQL-Kernsystem
- **Verbesserte Konversionsraten**: Schnellere Ladezeiten führen zu einem besseren Benutzererlebnis
- **Vereinfachte Produktarten**: Ein einheitliches Schema, das auf einfachen und komplexen Produktarten basiert, reduziert die Komplexität für Entwickler
- **Verbesserte Preisgenauigkeit**: Unterstützung für 16-stellige Werte mit 4 Dezimalstellen
- **Entkoppelte Architektur**: Separates GraphQL-System für Katalogdaten sorgt für hohe Leistung, ohne die zentralen Commerce-Vorgänge zu beeinträchtigen
- **Echtzeit-Datensynchronisation**: Der Katalog-Service wird über die SaaS-Datenexporterweiterung mit der Adobe Commerce-Anwendung synchronisiert, um sicherzustellen, dass Abfragen die aktuellen Katalogdaten zurückgeben
- **Daten-Management-Dashboard**: Überwachen und Verwalten von Datensynchronisierungsvorgängen über die Admin-Benutzeroberfläche von Adobe Commerce
- **API-Mesh-Integration**: Optional Integration mit [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/), um die Adobe Commerce GraphQL-Systeme mit anderen internen APIs und Drittanbieter-APIs zu kombinieren, um das GraphQL-Schema des Katalog-Services zu erweitern und benutzerdefinierte Daten oder Funktionen hinzuzufügen


## Überblick über die Architektur

>[!NOTE]
>
>Wenn Sie Ihren Katalog mithilfe des zusammenstellbaren Katalogs mit Adobe Commerce Optimizer oder Adobe Commerce Optimizer Connector implementieren, lesen Sie das [Adobe Commerce Optimizer-](../optimizer/overview.md#architecture) und Merchandising Services-Entwicklerhandbuch.

Der [!DNL Catalog Service] verwendet [GraphQL](https://graphql.org/), um Katalogdaten, einschließlich Produkte, Produktattribute, Bestand und Preise, anzufordern und zu empfangen. GraphQL ist eine Abfragesprache, die ein Frontend-Client verwendet, um mit der in einem Backend wie Adobe Commerce definierten Anwendungsprogrammierschnittstelle (API) zu kommunizieren. GraphQL ist eine beliebte Kommunikationsmethode, da sie einfach ist und es einem Systemintegrator ermöglicht, den Inhalt und die Reihenfolge jeder Antwort anzugeben.

Adobe Commerce bietet zwei GraphQL-Systeme, die unterschiedlichen Zwecken dienen:

### GraphQL-Kernsystem

- **Zweck**: API mit vollem Funktionsumfang für alle Commerce-Vorgänge
- **Funktionen**: Abfragen (lesen) und Mutationen (schreiben) für Produkte, Kunden, den Warenkorb, den Checkout und mehr
- **Einschränkung**: Produktabfragen sind nicht für die Geschwindigkeit optimiert
- **Anwendungsfall**: Allgemeine Commerce-Vorgänge und Schreibvorgänge

### Catalog Service GraphQL-System

- **Zweck**: Nur leistungsstarke Produktkatalogabfragen
- **Funktionen**: Schreibgeschützte Abfragen für Produkte, Attribute, Inventar und Preise
- **Vorteil**: Deutlich schneller als das Kernsystem für Produktdaten
- **Anwendungsfall**: Storefront-Produkterlebnisse, bei denen Geschwindigkeit entscheidend ist

Die für den Katalog-Service verfügbaren Daten werden von der SaaS-Datenexporterweiterung bereitgestellt. Diese Erweiterung synchronisiert Daten zwischen der Commerce-Anwendung und den verbundenen Commerce Services, um sicherzustellen, dass Abfragen an die GraphQL-API-Endpunkte der Services die aktuellen Katalogdaten zurückgeben. Informationen zur Verwaltung und Fehlerbehebung bei SaaS-Datenexportvorgängen finden Sie im [SaaS-Datenexporthandbuch](../data-export/overview.md).

[!DNL Catalog Service] Kunden können den [SaaS-Preisindexer](../price-index/price-indexing.md) verwenden, der schnellere Preisaktualisierungen und Synchronisierungszeiten ermöglicht.

## Architekturdetails

Das folgende Diagramm veranschaulicht die architektonischen Unterschiede zwischen dem GraphQL-Kernsystem und dem GraphQL-Katalogdienst-System und zeigt, wie sie zusammenarbeiten, um die Leistung der Storefront zu optimieren:

![Katalog-Architekturdiagramm](assets/catalog-service-architecture.png)

### Funktionsweise der Systeme

**Core GraphQL-System (herkömmlicher Ansatz):**
Die Progressive Web App (PWA) sendet Anfragen direkt an die Commerce-Anwendung, die jede Anfrage über mehrere Subsysteme verarbeitet, bevor sie eine Antwort zurückgibt. Dieser mehrstufige Roundtrip kann zu langsamen Seitenladezeiten führen und möglicherweise zu niedrigeren Konversionsraten.

**Katalog-Service (optimierter Ansatz):**
Catalog Service fungiert als Gateway für Storefront-Services, das auf eine dedizierte, optimierte Datenbank mit Produktdetails, Attributen, Varianten, Preisen und Kategorien zugreift. Der Service sorgt für die Synchronisierung mit Adobe Commerce durch automatisierte Indizierung, wobei der herkömmliche Zyklus von Anfrage und Antwort umgangen wird, um die Latenz erheblich zu reduzieren.

Die Kern- und Service-GraphQL-Systeme kommunizieren nicht direkt miteinander. Sie greifen auf jedes System über eine andere URL zu, und Aufrufe erfordern unterschiedliche Kopfzeileninformationen. Die beiden GraphQL-Systeme sind so konzipiert, dass sie gemeinsam verwendet werden können. Das [!DNL Catalog Service] GraphQL-System erweitert das Kernsystem, um ProduktStorefront-Erlebnisse schneller zu machen.

Sie können optional [API Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) implementieren, um die beiden Adobe Commerce GraphQL-Systeme mit privaten und Drittanbieter-APIs und anderen Softwareschnittstellen unter Verwendung von Adobe Developer zu integrieren. Das Netz kann so konfiguriert werden, dass an jeden Endpunkt weitergeleitete Aufrufe die richtigen Autorisierungsinformationen in den -Kopfzeilen enthalten.

## Architektonische Details

In den folgenden Abschnitten werden einige der Unterschiede zwischen den beiden GraphQL-Systemen beschrieben.

### Schema-Management

Da der Katalog-Service als Service funktioniert, müssen sich Integratoren keine Gedanken über die zugrunde liegende Version von Commerce machen. Die Syntax der Abfragen ist für alle Versionen gleich. Darüber hinaus ist das Schema für alle Händler konsistent. Diese Konsistenz erleichtert die Einrichtung von Best Practices und erhöht die Wiederverwendung von Storefront-Widgets erheblich.

### Vereinfachung der Produktarten

Das Schema reduziert die Vielfalt der Produkttypen auf zwei Anwendungsfälle:

- **Einfache Produkte** - Der Katalog-Service ordnet die Adobe Commerce-Produkttypen „Einfach“, „Virtuell“, „Herunterladbar“ und „Geschenkkarte“ `simpleProductViews` zu. Dieser Typ hat:
   - Ein einheitlicher, fester Preis und eine einheitliche Menge
   - Regulärer Preis (vor Rabatten) und Endpreis (nach Rabatten)
   - Unterstützung für Produktattribute wie Farbe, Größe und andere Eigenschaften

- **Komplexe Produkte** - Der Katalog-Service ordnet die konfigurierbaren, gebündelten und gruppierten Adobe Commerce-Produkttypen `complexProductViews` zu. Komplexe Produkte sind Sammlungen mehrerer einfacher Produkte, die konfiguriert oder gebündelt werden können.
   - Jede Komponente eines einfachen Produkts kann einen eigenen Preis haben.
   - Käufer können Mengen für einzelne Komponentenprodukte angeben.
   - Produktoptionen (wie Größe, Farbe, Material) sind vereinheitlicht und funktionieren unabhängig vom Produkttyp auf die gleiche Weise. Jede Optionsauswahl verweist auf ein bestimmtes einfaches Produkt mit eigenen Attributen und einem eigenen Preis. Das Endprodukt bleibt undefiniert, bis der Käufer alle erforderlichen Optionen auswählt.

#### Attribute der Produktansicht

Sowohl einfache als auch komplexe Produkte verfügen über kundendefinierte Attribute, die in der Storefront angezeigt werden können. Diese Attribute werden als &quot;[&quot; zurückgegeben](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/#productviewattribute-type). In Adobe Commerce werden die verfügbaren Attribute definiert, wenn das Produkt erstellt wird. Sie können zusätzliche Attribute aus dem Adobe Commerce-Backend oder programmgesteuert hinzufügen. Siehe [Erweitern und Anpassen von SaaS-Datenexport-Feed-Daten](../data-export/extensibility-and-customizations.md).

>[!TIP]
>
>Anstatt Datentypen zum Commerce-Backend hinzuzufügen, können Sie [API Mesh mit dem Katalog-Service](mesh.md) verwenden, um das GraphQL-Schema des Katalog-Services zu erweitern und Daten hinzuzufügen oder vorhandene Katalogdaten zu konfigurieren, um neue Funktionen zu aktivieren.

### Preise

Einfache Produkte stellen die Basis-Verkaufseinheit dar, die einen Preis hat. [!DNL Catalog Service] berechnet den regulären Preis vor Rabatten sowie den Endpreis nach Rabatten. Preisberechnungen können feste Produktsteuern enthalten. Sie schließen personalisierte Promotions aus.

Ein komplexes Produkt hat keinen festgelegten Preis. Stattdessen gibt der Katalog-Service die Preise für verknüpfte Einfache zurück. Beispielsweise kann ein Händler zunächst allen Varianten eines konfigurierbaren Produkts dieselben Preise zuweisen. Wenn bestimmte Größen oder Farben unbeliebt sind, kann der Händler die Preise dieser Varianten senken. Der Preis des komplexen (konfigurierbaren) Produkts weist also zunächst eine Preisspanne auf, die den Preis sowohl von Standardvarianten als auch von unpopulären Varianten widerspiegelt. Nachdem der Käufer einen Wert für alle verfügbaren Optionen ausgewählt hat, zeigt die Storefront einen einzigen Preis an.

Der Katalog-Service sorgt für genaue Preisaktualisierungen und Berechnungen, indem er Preise mit großen Werten (bis zu 16 Stellen) und hoher Dezimalgenauigkeit (bis zu 4 Dezimalstellen) unterstützt.

>[!NOTE]
>
> Commerce-Kunden mit [!DNL Catalog Service] können mit dem SaaS-Preisindexer [ schnellere Preisänderungen und Synchronisierungszeiten auf ihren Websites ](../price-index/price-indexing.md).

## Implementierung

Der Implementierungsprozess umfasst Folgendes:

1. [!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."} **[Installieren und Konfigurieren des Katalog-Service](installation.md)** - Installieren und konfigurieren Sie die Catalog-Service-Erweiterung und richten Sie die SaaS-Verbindung mithilfe der [!DNL Commerce Services Connector] ein.
2. **Storefront-Code aktualisieren**: Integrieren Sie GraphQL-Abfragen des Katalog-Services in Ihr Frontend.
3. **Routing-Abfragen**: Alle Abfragen des Katalog-Services gehen über das GraphQL-Gateway (die URL wird beim Onboarding angegeben)
4. **Überwachung und Fehlerbehebung bei der Datensynchronisation**: Überprüfen Sie die verbesserte Leistung und überwachen Sie die Ergebnisse.


