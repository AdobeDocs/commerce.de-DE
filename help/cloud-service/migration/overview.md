---
title: Migrieren nach [!DNL Adobe Commerce as a Cloud Service]
description: Erfahren Sie, wie Sie zu  [!DNL Adobe Commerce as a Cloud Service].
feature: Cloud
exl-id: 9065c92a-f6b2-4464-8ec0-5c549bf78104
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Developer
level: Intermediate
source-git-commit: 458f34c45406db871ec61ff408aa624f163b6ee0
workflow-type: tm+mt
source-wordcount: '3020'
ht-degree: 0%

---

# Migrieren nach [!DNL Adobe Commerce as a Cloud Service]

[!DNL Adobe Commerce as a Cloud Service] bietet eine umfassende Anleitung für Entwicklerinnen und Entwickler, die von einer bestehenden Adobe Commerce PaaS-Implementierung auf das neue Adobe Commerce as a Cloud Service (SaaS)-Angebot umstellen. Adobe Commerce as a Cloud Service stellt einen bedeutenden Wandel hin zu einem vollständig verwalteten, versionslosen SaaS-Modell dar und bietet verbesserte Leistung, Skalierbarkeit, vereinfachten Betrieb und eine engere Integration mit der [!DNL Adobe Experience Cloud].

>[!NOTE]
>
>Weitere Informationen zu Migrations-Tools finden Sie unter [Tool für die Massendatenmigration](./bulk-data.md).

## Die Verschiebung verstehen - PaaS und SaaS vergleichen

**Die wichtigsten Unterschiede**

* [!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."} **PaaS (aktuell)**: Händler verwalten Anwendungs-Code, Upgrades, Patches und Infrastrukturkonfigurationen in der gehosteten Umgebung von Adobe. [Modell der gemeinsamen Verantwortung](https://experienceleague.adobe.com/de/docs/commerce-operations/security-and-compliance/shared-responsibility) für Dienste (MySQL, Elasticsearch und andere).
* [!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} **SaaS (Neu - [!DNL Adobe Commerce as a Cloud Service])**: Adobe verwaltet die Kernanwendung, -infrastruktur und -aktualisierungen vollständig. Händler konzentrieren sich auf die Anpassung über Erweiterungspunkte (APIs, App Builder, UI-SDKs). Der Code der Hauptanwendung ist gesperrt.

**Auswirkungen auf die Architektur**

* **Versionslose Plattform**: Kontinuierliche Aktualisierungen bedeuten keine größeren Versionsaktualisierungen mehr für den Kern.
* **Microservices &amp; API-first**: Stärkere Abhängigkeit von APIs für Erweiterbarkeit und Integration.
* **Headless standardmäßig (optional)**: Starke Unterstützung für entkoppelte Storefronts (z. B. Commerce Storefront powered by Edge Delivery Services).
* **Edge Delivery Services**: Auswirkungen auf die Frontend-Leistung und -Bereitstellung.

**Neue Tools und Konzepte**

* [Adobe Developer App Builder](https://developer.adobe.com/app-builder/) und [API Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway)
* [Commerce Optimizer](../../optimizer/overview.md)
* [Edge Delivery Services](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de)
* Self-Service-Bereitstellung mit dem [Commerce Cloud Manager](../getting-started.md#create-an-instance)

## Migrationspfade

[!DNL Adobe Commerce as a Cloud Service] unterstützt mehrere Migrationspfade, abhängig von Ihrer Timeline, Storefront und Ihren Anpassungen.

Als Alternative zu einer vollständigen Migration unterstützt [!DNL Adobe Commerce as a Cloud Service] eine stufenweise Migration mithilfe von Commerce Optimizer oder eines inkrementellen Ansatzes.

* **Inkrementelle Migration** Dieser Ansatz umfasst die schrittweise Migration Ihrer Daten, Anpassungen und Integrationen. Dieser Ansatz ist ideal für große Händler mit vielen Anpassungen, die ihre komplexen Anpassungen und Daten schrittweise in ihrem eigenen Tempo auf [!DNL Adobe Commerce as a Cloud Service] umstellen möchten.

![Inkrementelle Migration](../assets/incremental.png){width="600" zoomable="yes"}

* **Commerce Optimizer**: Bei diesem Ansatz können Sie iterativ migrieren, indem Sie Commerce Optimizer als Übergangsphase verwenden, um komplexe Anpassungen und Daten in Ihrem eigenen Tempo in [!DNL Adobe Commerce as a Cloud Service] zu verschieben. Commerce Optimizer bietet Zugriff auf Merchandising-Services, die auf Katalogansichten und Richtlinien basieren, auf die Commerce-Storefront mit Edge Delivery und auf [!DNL Product Visuals powered by AEM Assets].

![Iterative Migration](../assets/optimizer.png){width="600" zoomable="yes"}

* **Vollständige Migration** Dieser Ansatz umfasst die Migration aller Daten, Anpassungen und Integrationen auf einmal. Dieser Ansatz ist ideal für kleinere Händler mit wenigen Anpassungen, die schnell auf [!DNL Adobe Commerce as a Cloud Service] umstellen möchten.

Die folgende Tabelle bietet einen Überblick über den Migrationsprozess für verschiedene Storefronts und Konfigurationen:

|                    | LUMA-Storefront | PWA-Storefront | Commerce Storefront powered by Edge Delivery | Headless |
|--------------------|----------------------------------------|----------------------------------------|------------------------------------------------------|----------------------------------------|
| Datenmigration | Erforderlich | Erforderlich | Erforderlich | Erforderlich |
| Schaufenster | Migrieren zur Commerce-Storefront mit Edge Delivery | Migrieren Sie zu einer Commerce Storefront mit Edge Delivery oder verwalten Sie | Keine Auswirkung | Keine Auswirkung |
| API-Mesh | Neues Netz erstellen | Neues Netz erstellen oder vorhandenes neu konfigurieren | Neues Netz erstellen oder vorhandenes neu konfigurieren | Neues Netz erstellen oder vorhandenes neu konfigurieren |
| Integrationen | Nutzen des Integrations-Starter-Kits | Nutzen des Integrations-Starter-Kits | Nutzen des Integrations-Starter-Kits | Nutzen des Integrations-Starter-Kits |
| Anpassungen | Zu App Builder und API Mesh wechseln | Zu App Builder und API Mesh wechseln | Zu App Builder und API Mesh wechseln | Zu App Builder und API Mesh wechseln |
| Verwaltung von Assets | Migration erforderlich bei Verwendung von OOTB | Migration erforderlich bei Verwendung von OOTB | Migration erforderlich bei Verwendung von OOTB | Migration erforderlich bei Verwendung von OOTB |
| Erweiterungen | Migrieren nach App Builder | Migrieren nach App Builder | Migrieren nach App Builder | Migrieren nach App Builder |

Wie aus der Tabelle ersichtlich, bestehen die Abhilfemaßnahmen für jede Migration aus:

* **Datenmigration** - Verwenden der bereitgestellten [Migrations-Tools](./bulk-data.md) um Daten von Ihrer vorhandenen Instanz zu [!DNL Adobe Commerce as a Cloud Service] zu migrieren.
* **Storefront** - Bestehende Commerce-Storefronts mit Edge Delivery und Headless-Storefronts erfordern keine Abschwächung, aber für Luma-Storefronts ist eine Migration zu Commerce Storefronts mit Edge Delivery erforderlich. PWA Studio-Storefronts können zu Commerce Storefronts migriert werden, die von Edge Delivery unterstützt werden oder in ihrem aktuellen Status beibehalten werden. Adobe stellt Accelerators zur Verfügung, die Sie bei der Migration von Storefronts unterstützen.
* **[API-](https://developer.adobe.com/graphql-mesh-gateway)**: Erstellen Sie ein neues Netz oder ändern Sie das vorhandene. Adobe stellt vorkonfigurierte Meshes zur Verfügung, um diesen Prozess zu unterstützen.
* **Integrationen** - Alle Integrationen müssen entweder das [Integrations-Starter-Kit](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/) oder die [[!DNL Adobe Commerce as a Cloud Service] REST-API](https://developer.adobe.com/commerce/webapi/reference/rest/saas/) nutzen.
* **Anpassungen** - Alle Anpassungen müssen auf App Builder und API-Mesh verschoben werden.
* **Assets-**: Die gesamte Asset-Verwaltung erfordert eine Migration. Wenn Sie [!DNL AEM Assets] bereits verwenden, müssen Sie nicht migrieren.
* **Erweiterungen** - Alle prozessinternen Erweiterungen müssen als prozessexterne Erweiterungen neu erstellt werden. Bis Ende 2025 wird Adobe Zugriff auf unsere beliebtesten Erweiterungen bieten, um die Erstellungszeiten zu minimieren.

## Migrationsphasen

In den folgenden Phasen werden die erforderlichen Schritte und Überlegungen für die Migration zu [!DNL Adobe Commerce as a Cloud Service] beschrieben.

### Bewertung und Planung vor der Migration

Diese Phase ist wichtig, um Risiken zu minimieren, einen klaren Migrationspfad festzulegen und Probleme zu identifizieren, bevor sie auftreten.

**Erkennung und Prüfung der aktuellen Umgebung**

**Codebase-Analyse:**

* Identifizieren Sie alle benutzerdefinierten Module, Designs und Überschreibungen.
* Analysieren Sie Änderungen am Kern-Code und ermitteln Sie, welche im Rahmen der Migration umstrukturiert werden müssen.
* Bewerten Sie Erweiterungen von Drittanbietern und ermitteln Sie die Kompatibilität mit [!DNL Adobe Commerce as a Cloud Service]. Gibt es SaaS-kompatible Alternativen oder müssen Sie benutzerdefinierte API-Integrationen oder App Builder-Anwendungen erstellen?
* Identifizieren Sie veralteten Code oder veraltete Funktionen, die nicht migriert werden.

**Datenprüfung:**

* Bewerten Sie die Größe und Komplexität Ihrer Datenbank.
* Identifizieren Sie nicht verwendete Daten oder Tabellen für die Bereinigung.
* Überprüfen Sie vorhandene Datenimport-/Exportprozesse.

**Integrationsüberprüfung:**

* Listen Sie alle externen Systeme auf, die in Adobe Commerce integriert sind (ERP, CRM, PIM, Payment Gateways, Versanddienstleister, OMS und alle anderen Systeme).
* Bewerten Sie Integrationsmethoden (API, benutzerdefinierte Skripte und andere Methoden).
* Bewerten Sie die Kompatibilität mit dem API-First-Ansatz von [!DNL Adobe Commerce as a Cloud Service] und App Builder.

**Leistungs-Benchmarks:**

* Dokumentieren Sie aktuelle Lighthouse-Werte, Seitenladezeiten und wichtige Leistungsindikatoren (KPIs), die eine Grundlinie zur Messung der Verbesserungen nach der Migration bieten.

**Überprüfung der Sicherheitskonfiguration:**

* Bewerten Sie alle benutzerdefinierten WAF-Regeln, IP-Zulassungslisten und anderen Sicherheitskonfigurationen.

**Definieren des Migrationsumfangs und der Migrationsstrategie:**

* **Schrittweise vs. gleichzeitige Migration:** Bewerten Sie die Vor- und Nachteile der einzelnen Ansätze.
* **Identifizieren Sie die wichtigsten Geschäftsprozesse:** Priorisieren Sie Funktionen, die zuerst migriert werden müssen, z. B.:
   * Komplexe Preisregeln
   * Benutzerdefinierte Geschäftsregeln werden angewendet, bevor eine Bestellung offiziell aufgegeben oder verarbeitet wird
   * Komplexe Steuerberechnungen
   * Adressenvalidierungen
   * Benutzerdefinierte Logik, die nach der Bestellung ausgelöst wird
* **Headless vs. monolithische Storefront:** Entscheidungspunkt für die Entwicklung neuer Storefronts oder die Anpassung vorhandener Storefronts.
* **Integrationsstrategie:** bestimmen, wie bestehende Integrationen neu platziert werden (API Mesh, App Builder, Direct API).
* **Datenmigrationsstrategie:** Sie mithilfe vollständiger historischer Daten, partieller Daten oder ohne migrierte Daten, ob Sie migrieren möchten.

**Team-Bereitschaft und -Schulung:**

* Machen Sie sich mit [!DNL Adobe Commerce as a Cloud Service] Konzepten, Entwicklungs-Workflows und neuen Tools vertraut.
* Nehmen Sie an praxisnahen Schulungen mit Adobe App Builder-, Edge Delivery Services- und [!DNL Adobe Commerce as a Cloud Service]-Bereitstellungs-Pipelines teil.

**Einrichtung und Bereitstellung der Umgebung:**

* Bereitstellen Ihrer [!DNL Adobe Commerce as a Cloud Service]-Sandbox- und Entwicklungsumgebungen mit Commerce Cloud Manager.

### Inkrementelle Migrationsphasen

**Strategische Umgestaltung und Externalisierung**

Diese Phase besteht aus dem Kern der Migration, wobei der Schwerpunkt auf der Anpassung Ihrer Code-Basis an das [!DNL Adobe Commerce as a Cloud Service] Cloud-native Paradigma liegt. Dazu müssen neue Adobe-Services strategisch übernommen und benutzerdefinierte Logik aus der Commerce-Kernplattform entfernt werden.

#### &#x200B;1. Migrieren von „In-Process“-Anpassungen und -Erweiterungen zu App Builder

Dies ist eine entscheidende Phase, um einen „gesperrten Kern“ zu erreichen und Ihre Lösung zukunftssicher zu machen, was von zentraler Bedeutung für die [!DNL Adobe Commerce as a Cloud Service] Architekturphilosophie ist.

* **Externalisieren komplexer Logik in App Builder**: Analysieren Sie vorhandene benutzerdefinierte Module und Erweiterungen von Drittanbietern in Ihrer PaaS-Codebasis. Für komplexe Geschäftslogik, maßgeschneiderte Integrationen oder Microservices, die keine direkte, prozessinterne Manipulation des Commerce-Kerndatenmodells erfordern, refaktorieren und replattformen Sie sie als Server-lose Anwendungen innerhalb von Adobe Developer App Builder.
* **API Mesh nutzen**: Implementieren Sie für Szenarien, in denen Daten von mehreren Backend-Systemen (z. B. Ihrem PaaS Commerce-Backend, ERP, CRM und benutzerdefinierten App Builder-Microservices) benötigt werden, eine API-Mesh-Ebene in App Builder. Dadurch werden unterschiedliche APIs zu einem einzigen, leistungsstarken GraphQL-Endpunkt zusammengefasst, der von Ihrer neuen Storefront oder anderen Services genutzt wird, was den komplexen Datenabruf vereinfacht.
* **Ereignisgesteuerte Architektur**: Verwenden Sie Adobe I/O Events, um App Builder-Aktionen auf der Grundlage von Ereignissen in Ihrer PaaS-Instanz (z. B. Produktaktualisierungen, Kundenregistrierungen, Auftragsstatusänderungen) oder anderen verbundenen Systemen in einen Trigger zu bringen. Dies fördert die asynchrone Kommunikation, reduziert die enge Kopplung und erhöht die Systemresilienz.

**Vorteil**: Dieser Schritt verringert die technische Schuld im Zusammenhang mit tief eingebetteten Anpassungen erheblich, beschleunigt den Übergang Ihrer Commerce-Instanz zu [!DNL Adobe Commerce as a Cloud Service] erheblich, verbessert die Skalierbarkeit und unabhängige Bereitstellbarkeit von benutzerdefinierter Logik und beschleunigt die Entwicklungszyklen für Erweiterungen.

#### &#x200B;2. Einführung von SaaS-basierten Adobe Commerce-Merchandising-Services und Integration von Katalogdaten

Dies ist ein wichtiger erster Integrationspunkt mit zwei Optionen für die Katalogdaten-Verwaltung:

>[!BEGINTABS]

>[!TAB Option 1: Vorhandener Katalog-SaaS-Service]

**Nutzen Sie den vorhandenen Katalog-SaaS-Service, der mit dem PaaS-Backend integriert ist**

Diese Option dient als Übergangsschritt, der auf einer vorhandenen Integration aufbaut, bei der Ihr PaaS-Backend eine vorhandene Instanz des Adobe Commerce SaaS-Service mit Daten aus dem [Katalog-Service](../../catalog-service/guide-overview.md), der [Live-Suche](../../live-search/overview.md) und [Produktempfehlungen](../../product-recommendations/overview.md).

* **Synchronisierung von Katalogdaten**: Stellen Sie sicher, dass Ihre Adobe Commerce PaaS-Instanz weiterhin Produkt- und Katalogdaten mit Ihrem bestehenden Adobe Commerce Catalog SaaS-Service synchronisiert. Dies beruht in der Regel auf etablierten Connectoren oder Modulen innerhalb Ihrer PaaS-Instanz. Der Katalog-SaaS-Service bleibt die maßgebliche Quelle für Such- und Merchandising-Funktionen und leitet seine Daten aus Ihrem PaaS-Backend ab.
* **API Mesh für die**: Während die Headless-Storefront (auf Edge Delivery Services) und andere Services Daten direkt aus dem Katalog-SaaS-Service nutzen können, empfiehlt Adobe dringend die Verwendung von API Mesh (innerhalb von App Builder). API Mesh kann APIs aus dem Katalog-SaaS-Service mit anderen erforderlichen APIs aus Ihrem PaaS-Backend (z. B. Echtzeit-Inventarprüfungen aus der Transaktionsdatenbank oder benutzerdefinierte Produktattribute, die nicht vollständig auf den Katalog-SaaS-Service repliziert wurden) zu einem einzigen, leistungsstarken GraphQL-Endpunkt vereinheitlichen. Dies ermöglicht auch eine zentralisierte Zwischenspeicherung, Authentifizierung und Antwortumwandlung.
* **Live-Suche und Produktempfehlungen integrieren**: Konfigurieren Sie Live-Suche und Produktempfehlungen mit SaaS-Services, um [Katalogdaten aufzunehmen](https://experienceleague.adobe.com/de/docs/commerce/live-search/install#configure-the-data) direkt aus Ihrem bestehenden Adobe Commerce Catalog SaaS-Service, der wiederum von Ihrem PaaS-Backend gefüllt wird.

**Vorteil**: Dies bietet einen schnelleren Weg zu einer Headless-Storefront und erweiterten SaaS-Merchandising-Funktionen, indem ein vorhandener und betrieblicher Katalog-SaaS-Service und dessen Integrations-Pipeline mit Ihrem PaaS-Backend genutzt werden. Es behält jedoch die Abhängigkeit vom PaaS-Backend für die primäre Katalogdatenquelle bei und bietet nicht die Aggregationsfunktionen für mehrere Quellen, die dem neuen zusammensetzbaren Katalogdatenmodell inhärent sind. Diese Option ist ein gültiger Schritt auf dem Weg zu einer umfassenderen zusammensetzbaren Architektur.

>[!TAB Option 2: Zusammensetzbares Katalogdatenmodell]

**Übernehmen des neuen zusammensetzbaren Katalogdatenmodells (CCDM)**

Dies ist der strategische, zukunftssichere Ansatz zur Nutzung von Adobe Commerce Optimizer. CCDM bietet einen flexiblen, skalierbaren und einheitlichen Katalog-Service, der für die Datenaggregation aus mehreren Quellen und dynamisches Merchandising entwickelt wurde.

* **Datenaufnahme und -vereinheitlichung**
   * Nehmen Sie zunächst Produkt- und Katalogdaten aus Ihrer bestehenden Adobe Commerce PaaS-Instanz (und/oder anderen PIM/ERP-Systemen) in das neue zusammensetzbare Katalogdatenmodell (CCDM) auf.
   * Ordnen Sie vorhandene Produktattribute dem flexiblen Schema des CDM zu. Priorisieren Sie kritische Produktdaten für die erste Aufnahme.
   * Erstellen Sie robuste Datenpipelines für die kontinuierliche Synchronisierung. Dies kann Folgendes beinhalten:
      * **Ereignisgesteuert** (über App Builder): Verwenden Sie Adobe I/O Events von Ihrer PaaS-Instanz aus, um öffentlich verfügbare oder benutzerdefinierte Adobe App Builder-Programme im Trigger zu halten. Diese Programme transformieren und übertragen Datenänderungen (Erstellen, Aktualisieren und Löschen) über die APIs in das CDM.
      * **Batch-Aufnahme**: Verwenden Sie für große anfängliche Lasten oder periodische Massenaktualisierungen sichere Dateiübertragungen (z. B. CSV oder JSON) in einen Staging-Bereich, die von Adobe Experience Platform (AEP)-Aufnahme-Services in CDM verarbeitet werden.
      * **Direkte API-Integration** (mit App Builder-Orchestrierung): Bei komplexeren Szenarien kann App Builder als Orchestrierungsschicht fungieren, indem es direkte API-Aufrufe an Ihr PaaS-Backend sendet, die Daten transformiert und an das CDM sendet.
* **Katalogansicht und Richtliniendefinition**: Konfigurieren Sie Katalogansichten (logische Gruppierungen für die eindeutige Katalogdarstellung, wie Shop-Ansichten, Regionen und B2B/B2C-Segmente) und definieren Sie Richtlinien (Regelsätze für die Produktdarstellung, Filterung und Merchandising) im CDM. Dies ermöglicht die dynamische Steuerung von Produktsortimenten und die Anzeigelogik pro Katalogansicht.
* **Live-Suche und Produktempfehlungen integrieren**: Sobald Katalogdaten im CCDM vorhanden sind, integrieren Sie die SaaS-basierte Live-Suche und die Produktempfehlungs-Services von Adobe. Diese nutzen KI-Modelle und Modelle für maschinelles Lernen von Adobe, um überlegene Suchrelevanz und personalisierte Empfehlungen zu erzielen, wobei Daten direkt aus dem CDM genutzt werden.

**Vorteil**: Durch die Abstrahierung des Katalogmanagements und der Erkennung in CDM- und zugehörigen SaaS-Services erzielen Sie eine verbesserte Leistung, erhalten KI-gesteuerte Merchandising-Funktionen, entlasten Lesevorgänge erheblich von Ihrem alten Backend und ermöglichen ein robustes „Abziehen“ des Top-of-funnel-Erlebnisses.

>[!ENDTABS]

#### &#x200B;3. Erstellen Sie Ihre Storefront auf Edge Delivery Services

Nachdem Merchandising-Daten-Pipelines eingerichtet und Anpassungen externalisiert wurden, verlagert sich der Fokus auf den Aufbau Ihres leistungsstarken Frontends.

* **Ersteinrichtung**: Richten Sie Ihr Projekt mit dem Textbaustein der Adobe Commerce-Storefront für Edge Delivery Services ein. Dies bietet ein grundlegendes Headless-Frontend, das auf modernen Web-Technologien basiert.
* **Verbindung zu Katalog-Services und API-Mesh herstellen**: Ihre Commerce-Storefront nutzt Daten hauptsächlich über GraphQL-APIs:
   * **Option 1**: Vom vorhandenen Katalog-SaaS-Service (über API-Mesh) für Produktinformationen und Merchandising-Regeln.
   * **Option 2**: Vom CCDM für Produktinformationen und Merchandising-Regeln.
   * Aus API Mesh für alle orchestrierten Daten aus Ihrem alten Backend (PaaS-Instanz) oder benutzerdefinierten App Builder-Services (z. B. Echtzeit-Inventar, benutzerdefinierte Produktattribute und Treuepunkte).
* **Inhaltsmigration (AEM Services)**: Migrieren Sie Ihre vorhandenen statischen Inhalte (z. B. „Über uns“-Seiten, Blog-Posts und Marketing-Banner) in AEM Services, die die Commerce-Storefront unterstützen. Nutzen Sie die Inhaltserstellungsfunktionen von AEM und stellen Sie sicher, dass Assets für Edge Delivery Services optimiert sind.
* **Entwickeln von UI-Kernkomponenten**: Erstellen Sie wichtige Komponenten der Benutzeroberfläche für Produktdetailseiten (PDPs), Produktlistenseiten (PLPs) und allgemeine Inhaltsseiten mithilfe von Edge Delivery Services-Dropdown-Komponenten und benutzerdefinierten React-/Vue-Komponenten. Priorisieren Sie die wichtigsten Commerce-Flüsse.
* **Integration mit vorhandenem Warenkorb/Checkout**: Zunächst koordiniert die Edge Delivery Services-Storefront eine Übergabe an Ihre bestehenden Adobe Commerce PaaS (oder eine andere Drittanbieterplattform) für die Warenkorbverwaltung und den Checkout. Dazu gehören in der Regel:
   * **Umleitung**: Umleitung des Benutzers zu den nativen Warenkorb- und Checkout-URLs der alten Plattform, Übergabe der erforderlichen Sitzungs- und Warenkorbkennungen.
   * **Direkte API-** (mit App Builder-Orchestrierung): Erstellen benutzerdefinierter Warenkorb- und Checkout-UI-Komponenten in Edge Delivery Services, die direkt mit dem Warenkorb und den Checkout-APIs Ihres PaaS-Backends interagieren. Dazu gehört oft App Builder as a Backend-for-Frontend (BFF), um Aufrufe an mehrere Backend-Services zu orchestrieren (z. B. PaaS-Warenkorb, Zahlungs-Gateways und Versandrechner).

**Vorteil**: Bietet ein unglaublich schnelles, SEO-optimiertes und hochflexibles Storefront-Erlebnis. Diese Phase trägt direkt zu einem überlegenen Kundenerlebnis bei und schafft die Grundlage für zukünftige Frontend-Innovationen.

#### &#x200B;4. Datenmigration (stufenweiser Prozess)

Datenmigration ist ein kritischer und facettenreicher Prozess, der gleichzeitig mit der Umgestaltung und Storefront-Entwicklung ausgeführt wird, um die Konsistenz und Integrität der Daten sicherzustellen.

* **Bereinigen und Optimieren vorhandener Daten**: Führen Sie vor einer groß angelegten Migration umfassende Datenbereinigung, Deduplizierung und Validierung in Ihrer bestehenden PaaS-Datenbank durch. Dieser proaktive Schritt ist wichtig, um die Übertragung von Altdatenproblemen zu minimieren und die Qualität der Daten in der neuen Umgebung sicherzustellen.

**Massendatenmigrationen**

Bei der Massendatenmigration müssen Sie einen vollständigen Daten-Dump aus Ihrer Adobe Commerce PaaS-Instanz erstellen, diesen gesamten Datensatz transformieren und ihn gleichzeitig in Adobe Commerce as a Cloud Service importieren. Diese Methode wird normalerweise für die anfängliche Datenpopulation verwendet.

* **Toolingverfügbarkeit**: Dedizierte [Tools für die Massendatenmigration](./bulk-data.md) zur Verwendung durch Kunden für Massendatenmigrationen von First-Party-Commerce werden auf Anfrage ab Mitte Juli 2025 verfügbar sein. Wenn Kundinnen und Kunden vorab Hilfe bei der Massendatenmigration benötigen, kann Adobe die Datenübertragung in ihrem Namen auf Anfrage erleichtern.

* **Prozess**:
   * **Vollständiger Datenexport**: Extrahieren Sie einen vollständigen Datensatz aus Ihrer Adobe Commerce PaaS-Instanz (z. B. Produkte, Kategorien, Kundenkonten, historische Bestelldaten, statische Blöcke und Seiteninhalte).
   * **Datenumwandlung**: Wenden Sie die erforderlichen Umwandlungen an, um die extrahierten Daten an die Schemaanforderungen der neuen Adobe Commerce as a Cloud Service-Komponenten anzupassen, einschließlich des Composable Catalog Data Model (CCDM), falls aktiviert, und aller anderen relevanten Adobe-Services oder -Datenbanken. Dies kann benutzerdefinierte Skripte oder spezielle Datenzuordnungs-Tools umfassen.
   * **Erstimport**: Importieren Sie den umgewandelten vollständigen Datensatz in die entsprechenden Komponenten von Adobe Commerce as a Cloud Service. Für Produkt- und Kategoriedaten wird der ausgewählte Katalog-Service (CDM oder vorhandene Katalog-SaaS) ausgefüllt. Für Kunden- und Bestelldaten werden dadurch das Transaktions-Backend oder die zugehörigen Services ausgefüllt.
   * **Validierung**: Strenge Validierung der importierten Daten, um Vollständigkeit, Genauigkeit und Konsistenz in allen neuen Systemen sicherzustellen.

**Iterative Datenmigrationen**

Iterative Datenmigrationen konzentrieren sich auf die Synchronisierung inkrementeller Änderungen und Deltas von der Quell-PaaS-Instanz mit den neuen Cloud Service-Komponenten, um die Datenaktualität vor und nach der Umstellung sicherzustellen.

* **Tooling-Verfügbarkeit**: Tools, die speziell für iterative Datenmigrationen entwickelt wurden, werden in der zweiten Jahreshälfte 2025 verfügbar sein.

* **Prozess**:
   * **Delta-Identifizierung**: Richten Sie Mechanismen ein, um Änderungen (Erstellen, Aktualisieren und Löschen) in wichtigen Datensätzen in Ihrer PaaS-Umgebung seit der letzten Synchronisierung zu identifizieren. Dies kann Änderungsdatenerfassung (CDC), Zeitstempelvergleiche oder ereignisbasierte Trigger umfassen.
   * **Fortlaufende Synchronisierung** Implementieren Sie robuste Mechanismen für die kontinuierliche, inkrementelle Datensynchronisierung von Ihrer PaaS-Umgebung zu den neuen Cloud Service-Komponenten (z. B. CCDM und Transaktions-Backend). Dies ist für die Aufrechterhaltung der Datenfrische und die Minimierung von Ausfallzeiten während der Umstellung von entscheidender Bedeutung.
   * **Nutzen von Ereignissen**: Nutzen Sie nach Möglichkeit Adobe I/O Events, um App Builder-Aktionen für Echtzeit- oder nahezu Echtzeit-Updates von Ihrer PaaS-Instanz auf die neuen Services Trigger. Beispielsweise könnte bei einer Produktaktualisierung in PaaS ein Ereignis Trigger werden, das den entsprechenden Eintrag in CCDM aktualisiert.
   * **API-gesteuerte Updates**: Verwenden Sie für Daten, die nicht ereignisgesteuert sind, geplante API-Aufrufe (über App Builder oder andere Integrationsplattformen), um Änderungen von PaaS abzurufen und sie auf die neuen Systeme zu übertragen.
   * **Fehlerbehandlung und -überwachung** Implementieren Sie eine robuste Fehlerbehandlung, -protokollierung und -überwachung für alle iterativen Datenpipelines, um sicherzustellen, dass die Datenintegrität während des gesamten Prozesses erhalten bleibt.

### Nach der Migration und laufender Betrieb

**DNS-Umstellung und Live-Schaltung:**

* Planen Sie die DNS-Umstellung sorgfältig mit minimalen Ausfallzeiten.
* Überwachen Sie den Zustand und die Leistung der Site sofort nach dem Start.

**Vorgänge nach der Markteinführung:**

**Stilllegung der PaaS-Umgebung:**

* Sicheres Archivieren oder Löschen alter PaaS-Instanzen und -Daten nach dem Validierungszeitraum.

**Workflow für die laufende Entwicklung:**

* Nutzen Sie den versionslosen Charakter von [!DNL Adobe Commerce as a Cloud Service], der statt umfangreicher Upgrades kontinuierlich kleine Bereitstellungen umfasst.
* Verwenden Sie Cloud Manager für die Verwaltung von Umgebungen und Bereitstellungen.
* Nutzen Sie App Builder, um die Funktionalität zu erweitern, ohne den Kern zu beeinträchtigen.

**Überwachung, Leistung und Sicherheit:**

* Überwachen Sie kontinuierlich die Leistung, Fehler und Sicherheitsprotokolle der Site.
* Nutzen Sie die integrierten Sicherheitsfunktionen von Adobe und halten Sie sich an Best Practices.

**Schulung und Dokumentation:**

* Trainieren Sie neue Entwickler und Geschäftsbenutzer für die [!DNL Adobe Commerce as a Cloud Service] Plattform und Workflows.
* Pflegen Sie die aktuelle interne Dokumentation für benutzerdefinierte Integrationen und Prozesse.
