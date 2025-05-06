---
title: '[!DNL Catalog Service]'
description: '[!DNL Catalog Service] für Adobe Commerce bietet eine Möglichkeit, den Inhalt von Produktanzeigeseiten und Produktlistenseiten viel schneller abzurufen als die nativen Adobe Commerce GraphQL-Abfragen.'
role: Admin, Developer
recommendations: noCatalog
exl-id: 525e3ff0-efa6-48c7-9111-d0b00f42957a
source-git-commit: be1c739f3821a5f1e846b3026088e3a3ff45a60f
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---

# [!DNL Catalog Service] für Adobe Commerce

Die [!DNL Catalog Service] für Adobe Commerce-Erweiterung bietet umfangreiche, (schreibgeschützte) Ansichtsmodell-Katalogdaten, um produktbezogene Storefront-Erlebnisse schnell und vollständig wiederzugeben, darunter:

* Produktdetailseiten
* Produktlisten- und Kategorieseiten
* Suchergebnisseiten
* Produktkarussells
* Produktvergleichsseiten
* Alle anderen Seiten, die Produktdaten rendern, wie Warenkorb-, Bestell- und Wunschlistenseiten

Der [!DNL Catalog Service] verwendet [GraphQL](https://graphql.org/), um Katalogdaten, einschließlich Produkte, Produktattribute, Bestand und Preise, anzufordern und zu empfangen. GraphQL ist eine Abfragesprache, die ein Frontend-Client verwendet, um mit der in einem Backend wie Adobe Commerce definierten Anwendungsprogrammierschnittstelle (API) zu kommunizieren. GraphQL ist eine beliebte Kommunikationsmethode, da sie einfach ist und es einem Systemintegrator ermöglicht, den Inhalt und die Reihenfolge jeder Antwort anzugeben.

Adobe Commerce verfügt über zwei GraphQL-Systeme. Das GraphQL-Kernsystem bietet eine breite Palette von Abfragen (Lesevorgänge) und Mutationen (Schreibvorgänge), mit denen ein Käufer mit vielen Seitentypen interagieren kann, darunter Produkt, Kundenkonto, Warenkorb, Checkout und mehr. Die Abfragen, die Produktinformationen zurückgeben, sind jedoch nicht für die Geschwindigkeit optimiert. Das GraphQL-Service-System kann nur Abfragen zu Produkten und zugehörigen Informationen durchführen. Diese Abfragen sind leistungsstärker als ähnliche Kernabfragen.

Die für den Katalog-Service verfügbaren Daten werden von der SaaS-Datenexporterweiterung bereitgestellt. Diese Erweiterung synchronisiert Daten zwischen der Commerce-Anwendung und den verbundenen Commerce Services, um sicherzustellen, dass Abfragen an die GraphQL-API-Endpunkte der Services die aktuellen Katalogdaten zurückgeben. Informationen zur Verwaltung und Fehlerbehebung bei SaaS-Datenexportvorgängen finden Sie im [SaaS-Datenexporthandbuch](../data-export/overview.md).

[!DNL Catalog Service] Kunden können den [SaaS-Preisindexer](../price-index/price-indexing.md) verwenden, der schnellere Preisaktualisierungen und Synchronisierungszeiten ermöglicht.

## Architektur

Die folgende Abbildung zeigt die beiden GraphQL-Systeme:

![Katalog-Architekturdiagramm](assets/catalog-service-architecture.png)

Im GraphQL-Kernsystem sendet der PWA eine Anfrage an die Commerce-Anwendung, die jede Anfrage erhält, verarbeitet, möglicherweise über mehrere Subsysteme sendet und dann eine Antwort an die Storefront zurückgibt. Dieser Roundtrip kann zu langsamen Seitenladezeiten führen, was möglicherweise zu niedrigeren Konversionsraten führt.

[!DNL Catalog Service] ist ein Storefront Services-Gateway. Der Service greift auf eine separate Datenbank zu, die Produktdetails und zugehörige Informationen wie Produktattribute, Varianten, Preise und Kategorien enthält. Der Service hält die Datenbank durch Indizierung mit der Adobe Commerce synchronisiert.
Da der Service die direkte Kommunikation mit der Anwendung umgeht, kann er die Latenz des Anfrage- und Antwortzyklus verringern.

Die Kern- und Service-GraphQL-Systeme kommunizieren nicht direkt miteinander. Sie greifen auf jedes System über eine andere URL zu, und Aufrufe erfordern unterschiedliche Kopfzeileninformationen. Die beiden GraphQL-Systeme sind so konzipiert, dass sie gemeinsam verwendet werden können. Das [!DNL Catalog Service] GraphQL-System erweitert das Kernsystem, um ProduktStorefront-Erlebnisse schneller zu machen.

Sie können optional [API Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) implementieren, um die beiden Adobe Commerce GraphQL-Systeme mit privaten und Drittanbieter-APIs und anderen Softwareschnittstellen unter Verwendung von Adobe Developer zu integrieren. Das Netz kann so konfiguriert werden, dass an jeden Endpunkt weitergeleitete Aufrufe die richtigen Autorisierungsinformationen in den -Kopfzeilen enthalten.

## Architektonische Details

In den folgenden Abschnitten werden einige der Unterschiede zwischen den beiden GraphQL-Systemen beschrieben.

### Schema-Management

Da der Katalog-Service als Service funktioniert, müssen sich Integratoren keine Gedanken über die zugrunde liegende Version von Commerce machen. Die Syntax der Abfragen ist für alle Versionen gleich. Darüber hinaus ist das Schema für alle Händler konsistent. Diese Konsistenz erleichtert die Einrichtung von Best Practices und erhöht die Wiederverwendung von Storefront-Widgets erheblich.

### Vereinfachung der Produktarten

Das Schema reduziert die Vielfalt der Produkttypen auf zwei Anwendungsfälle:

* Einfache Produkte sind Produkte, die mit einem einzigen Preis und einer einzigen Menge definiert werden. Catalog Service ordnet die Produkttypen „Einfach“, „Virtuell“, „Herunterladbar“ und „Geschenkkarte“ `simpleProductViews` zu.

* Komplexe Produkte bestehen aus mehreren einfachen Produkten. Die Komponente Einfache Produkte können unterschiedliche Preise haben. Es kann auch ein komplexes Produkt definiert werden, sodass der Käufer die Menge der einfachen Komponentenprodukte angeben kann. Catalog Service ordnet die konfigurierbaren, Bundle- und gruppierten Produkttypen `complexProductViews` zu.

Komplexe Produktoptionen werden durch ihr Verhalten vereinheitlicht und unterschieden, nicht durch ihren Typ. Jeder Optionswert stellt ein einfaches Produkt dar. Dieser Optionswert hat Zugriff auf die einfachen Produktattribute, einschließlich des Preises. Wenn der Käufer alle Optionen für ein komplexes Produkt auswählt, verweist die Kombination der ausgewählten Optionen auf ein bestimmtes einfaches Produkt. Das einfache Produkt bleibt mehrdeutig, bis der Käufer einen Wert für alle verfügbaren Optionen auswählt.

#### Attribute der Produktansicht

Sowohl einfache als auch komplexe Produkte verfügen über kundendefinierte Attribute, die in der Storefront angezeigt werden können. Diese Attribute werden als &quot;[&quot; zurückgegeben](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#productviewattribute-type). In Adobe Commerce werden die verfügbaren Attribute definiert, wenn das Produkt erstellt wird. Sie können zusätzliche Attribute aus dem Adobe Commerce-Backend oder programmgesteuert hinzufügen. Siehe [Erweitern und Anpassen von SaaS-Datenexport-Feed-Daten](../data-export/extensibility-and-customizations.md).

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

[!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."}

Für den Installationsprozess ist die Konfiguration des [Commerce Services-Connectors](../landing/saas.md) erforderlich. Sobald dies erreicht ist, besteht der nächste Schritt darin, dass ein Systemintegrator den Code der Storefront aktualisiert, um die [!DNL Catalog Service] Abfragen zu integrieren. Alle [!DNL Catalog Service] werden an das GraphQL-Gateway weitergeleitet. Die URL wird während des Onboarding-Prozesses bereitgestellt.
