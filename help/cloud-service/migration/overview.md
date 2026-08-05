---
title: Migrieren nach [!DNL Adobe Commerce as a Cloud Service]
description: Erfahren Sie, wie Sie zu  [!DNL Adobe Commerce as a Cloud Service].
feature: Cloud
exl-id: 9065c92a-f6b2-4464-8ec0-5c549bf78104
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Developer
level: Intermediate
autotag-review: '2026-06-18T16:12:28.840Z'
TQID: 'https://experienceleague.adobe.com/GmxaQdGKvAIDpZ2jvmlLFSYw0IFQysIMOT0lUnsJBsI'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
  - id: f8ddfd3b-6194-46e8-a176-0e918039be56
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: addc3a3a-2b1c-4fdf-aea4-4b1eb2931ba6
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eb30f47f-d87a-400f-8f78-63ce7979ff56
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: e03840ea9e0e43a005f385914e8599804383e79d
workflow-type: tm+mt
source-wordcount: 3305
ht-degree: 0%

---

# Migrieren nach [!DNL Adobe Commerce as a Cloud Service]

Dieses Handbuch hilft Entwicklerinnen und Entwicklern beim Übergang von [!DNL Adobe Commerce on Cloud] oder On-Premise zu [!DNL Adobe Commerce as a Cloud Service] (SaaS). Dieses SaaS-Modell bietet eine verbesserte Leistung, Skalierbarkeit und Integration mit dem [!DNL Adobe Experience Cloud].

>[!NOTE]
>
>Weitere Informationen zu Migrations-Tools finden Sie unter [Tool für die Massendatenmigration](./bulk-data/migration-tool.md).

## Überblick

Die Migration eines etablierten [!DNL Adobe Commerce] nach [!DNL Adobe Commerce as a Cloud Service] ist mehr als das Verschieben von Daten. Eine echte Migration umfasst die folgenden Bereiche:

- Anwendung - Anpassungen und Erweiterungen, die für [!DNL Adobe Commerce on Cloud] oder On-Premise-Installationen erstellt wurden
- Daten - Kataloge, Bestellungen, Kunden und Konfiguration
- Schaufenster
- Integration mit externen Systemen

[!DNL Adobe Commerce as a Cloud Service] ist eine versionslose SaaS-Plattform, was bedeutet, dass keiner dieser Bereiche migriert werden kann, ohne sie anzupassen. Die Anpassungen werden in [!DNL App Builder] Anwendungen modernisiert, die Storefronts werden auf Edge Delivery Services (EDS) neu aufgebaut, die Daten werden in den neuen [!DNL Adobe Commerce as a Cloud Service]-Mandanten migriert und die Integrationen werden mithilfe von SaaS-Mustern wiederhergestellt.

Anstatt die Migration als ein einzelnes monolithisches Projekt zu betrachten, bietet Adobe einen integrierten Migrations-Workflow, der auf [drei Migrations-Tools](#migration-tools-workflow) basiert.

Dieser freigegebene Workflow konsolidiert die Erkennung, stimmt die Engineering- und Bereitstellungs-Teams ab und bietet einen konsistenten Migrationsplan.

![Migrationsflussdiagramm](../assets/migration-flow.png)

### PaaS- und SaaS-Vergleich

[!DNL Adobe Commerce on Cloud] oder On-Premise (PaaS) und [!DNL Adobe Commerce as a Cloud Service] (SaaS) unterscheiden sich in der Art und Weise, wie sie verwaltet werden und wie Händler mit der Plattform interagieren.

**Die wichtigsten Unterschiede**

- [!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."}
- **[!DNL Adobe Commerce on Cloud Infrastructure]**: Händler verwalten Anwendungs-Code, Upgrades, Patches und Infrastrukturkonfiguration.
- **[!DNL Adobe Commerce]On-Premise**: Händler verwaltet Anwendungs-Code, Upgrades, Patches und Infrastrukturkonfigurationen in der gehosteten Umgebung von Adobe.

  >[!NOTE]
  >
  >[Modell der gemeinsamen Verantwortung](https://experienceleague.adobe.com/de/docs/commerce-operations/security-and-compliance/shared-responsibility) für Dienste (MySQL, Elasticsearch und andere).

- [!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} **SaaS (Neu - [!DNL Adobe Commerce as a Cloud Service])**: Adobe verwaltet die Kernanwendung, -infrastruktur und -aktualisierungen vollständig. Händler konzentrieren sich auf die Anpassung durch Erweiterungspunkte (APIs, App Builder, UI-SDKs). Der Code der Hauptanwendung ist gesperrt.

**Auswirkungen auf die Architektur**

- **Versionslose Plattform**: Kontinuierliche Aktualisierungen bedeuten keine größeren Versionsaktualisierungen mehr für den Kern.
- **Microservices &amp; API-first**: Stärkere Abhängigkeit von APIs für Erweiterbarkeit und Integration.
- **Headless standardmäßig (optional)**: Starke Unterstützung für entkoppelte Storefronts (z. B. Commerce Storefront powered by Edge Delivery Services).
- **Edge Delivery Services**: Auswirkungen auf die Frontend-Leistung und -Bereitstellung.

**Neue Tools und Konzepte**

- [Adobe Developer App Builder](https://developer.adobe.com/app-builder/) und [API Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/)
- [Commerce Optimizer](../../optimizer/overview.md)
- [Edge-Bereitstellungsdienste](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de)
- Self-Service-Bereitstellung mit dem [Commerce Cloud Manager](../getting-started.md#create-an-instance)

### Die Migrations-Journey

Eine Migration durchläuft die folgenden Phasen:

- **Bewerten** - Analysieren Sie die vorhandene Implementierung und berücksichtigen Sie dabei Folgendes: Inventaranpassungen, Integrationen, Storefront-Merkmale und Datenstrukturen. Erstellen Sie nach der Analyse eine Roadmap mit Migrationsempfehlungen, Komplexitätsbewertung und Aufwandsschätzungen.
- **Modernisieren Sie die Anwendung und migrieren Sie Daten** - Erstellen Sie Anpassungen als [!DNL App Builder] Anwendungen neu und migrieren Sie Geschäftsdaten nach [!DNL Adobe Commerce as a Cloud Service].
- **Storefront modernisieren** - Storefront auf Edge Delivery Services (EDS) für Commerce neu erstellen.
- **Überspringen und Betreiben** - Wechseln des Traffics auf [!DNL Adobe Commerce as a Cloud Service], Stilllegung von Legacy-Systemen und Übergang in den laufenden Betrieb.

Die Migration ist in der Regel iterativ und nicht linear. Unternehmen können mehrere Umgebungen bewerten, Empfehlungen validieren, schrittweise modernisieren und Implementierungspläne vor der endgültigen Produktionsumstellung verfeinern.

### Workflow für Migrations-Tools

Jeder der folgenden Workflows verfügt über ein eigenes Tool. Verwenden Sie sie zusammen, um Ihre Migration abzuschließen, wobei die Migrationsbewertung als gängige Blueprint während der gesamten Migration dient.

| Workflow | Tool | Beschreibung |
| --- | --- | --- |
| [Bewertung](#migration-assessment-tool) | **Migrationsbewertungswerkzeug** | KI-gesteuerte Bewertung der vorhandenen Implementierung, die benutzerdefinierte Module, Erweiterungen von Drittanbietern, Integrationen, Storefront-Beobachtungen, Datenbankschema, benutzerdefinierte Tabellen, Migrationsempfehlungen, Komplexitätsbewertung und Schätzungen des Modernisierungsaufwands inventarisiert. |
| [Modernisierung von Anwendungen und Storefronts](#code-and-storefront-migration-commerce-developer-mcp) | **Commerce Developer MCP** | KI-gestützte Modernisierung der Commerce-Anwendung, beschleunigte Migration von Anpassungen auf [!DNL App Builder], Unterstützung der Storefront-Transformation auf Edge Delivery Services (EDS) und Anleitung für Entwicklerinnen und Entwickler durch die umfassendere Journey zur Anwendungsmodernisierung mit einer von Entwicklungsteams geprüften und validierten Implementierung. |
| [Datenmigration](#data-migration-commerce-data-migration-service) | **Commerce Data Migration Service** | Extraktion, Laden und Integritätsprüfung von Katalog-, Kunden- und Bestelldaten in [!DNL Adobe Commerce as a Cloud Service]. |

Diese Tracks sind nicht eigenständig. Wenn Sie sie in der richtigen Reihenfolge gemeinsam verwenden, wird die Nacharbeit minimiert.

- **Bewertung zuerst ausführen** - Beim ersten Ausführen der Bewertung werden nicht unterstützte Anpassungen identifiziert, der Migrationsaufwand geschätzt, Überlegungen zur Datenmigration aufgezeigt und Integrationsabhängigkeiten vor Beginn der Implementierung hervorgehoben. Die Bewertung wird zum Migrationsplan, der sowohl von den Workflows für die Anwendungsmodernisierung als auch für die Datenmigration verwendet wird.
- **Anwendungsmodernisierung** - Das Commerce Developer MCP verwendet die Migrationsbewertung, um zu bestimmen, welche Anpassungen wie modernisiert werden sollen. Anschließend generiert der MCP die entsprechenden [!DNL App Builder] Programme und Storefront-Komponenten.
- **Datenmigration** - Die Umfrage zum Umfang der Datenmigration erfasst den Umfang, die Volumina und die benutzerdefinierten Tabellen, die von der Bewertung angezeigt wurden.
- **Benutzerdefinierte Daten und Drittanbieterdaten** - Daten, die von Drittanbietererweiterungen in benutzerdefinierten Tabellen gespeichert werden, werden bei der Bewertung identifiziert, werden jedoch nicht von der standardmäßigen Datenmigration verarbeitet und erfordern eine [!DNL App Builder] Anpassung.

Die Modernisierung der Storefront ist nicht nur eine Benutzeroberflächenmigration. Neben der Migration von Geschäftsfunktionen müssen Sie auch die Erlebnisarchitektur, die Modernisierung wiederverwendbarer Komponenten, die Leistungsoptimierung und die Übernahme von Edge Delivery Services-Mustern in Betracht ziehen.

Integrationen werden im Rahmen der Migrationsbewertung bewertet, ihre Implementierung variiert jedoch je nach Szenario. Integrationen können [!DNL App Builder]-, [!DNL API Mesh]-, Adobe I/O Events- und [!DNL Adobe Commerce as a Cloud Service]-APIs nutzen.

Diese Migrationstools erweitern und pflegen weiterhin einen einheitlichen Migrationsprozess, der sich auf die Migrationsbewertung konzentriert.

### Nächste Schritte

Wenn Sie bereit für die Migration sind, erstellen Sie zunächst eine Bewertung. In der Migrationsbewertung wird der Plan für den Rest der Migration festgelegt.

Das Migrationsbewertungs-Tool und das Commerce Developer MCP verwenden KI, um Sie bei der Ermittlung, Planung und Implementierung zu unterstützen. Wie bei jedem Engineering-Workflow sollten KI-generierte Empfehlungen und Implementierungen von Ihrem Team im Rahmen der standardmäßigen Architektur-, Test- und Qualitätssicherungsprozesse sorgfältig geprüft und validiert werden.

## Migrationsbewertungswerkzeug

Bevor Sie mit der Entwicklung oder Migration beginnen, müssen Sie die Größe der Migration berücksichtigen und die Elemente ermitteln, die die Entwicklung erfordern. Ein [!DNL Adobe Commerce] Store auf [!DNL Adobe Commerce on Cloud] oder On-Premise verfügt wahrscheinlich über benutzerdefinierte Module, Integrationen, Storefront-Anpassungen und Datenstrukturen, die möglicherweise erst offensichtlich sind, wenn jemand die Implementierung analysiert. Das Migrationsbewertungs-Tool scannt automatisch Ihre Code-Basis, um diese Elemente für die Entwicklung zu identifizieren.

### Bewertungsübersicht

Das Migrationsbewertungs-Tool führt eine KI-Bewertung der vorhandenen Implementierung durch und erstellt eine strukturierte Modernisierungsbewertung und eine [!DNL Adobe Commerce as a Cloud Service] Migrationsplanung. Außerdem wird ein umfassender Überblick über die Migration geboten, indem die Anwendungsanpassungen, Integrationen, Datenstrukturen, Storefront-Merkmale und andere Implementierungsdetails bewertet werden, die sich auf die Modernisierung auswirken. Die Discovery wird in einem schnellen, wiederholbaren Prozess ausgeführt, der es Ihnen ermöglicht, Aufwand, Risiken und Sequenzen zu bewerten, bevor Sie Verpflichtungen eingehen.

Die Bewertung, die das Migrationsbewertungswerkzeug erzeugt, ist nicht nur ein Bericht. Die Bewertung wird zu einem gemeinsam genutzten Migrationsartefakt, das während des gesamten Migrationslebenszyklus Informationen zu Planung, Implementierung und Validierung liefert. Als erste Phase der Journey betreffen die Ergebnisse sowohl die Modernisierung der Anwendung als auch die anschließende Datenmigration.

Weitere Informationen darüber, was in einem Migrationsbewertungsbericht enthalten ist und wie er verwendet wird, finden Sie [Migrationsbewertung](./assessment.md).

### Bewertungsphasen

Eine Bewertung erfolgt anhand der vorhandenen Implementierung und durchläuft eine Reihe automatisierter Phasen:

- **Inventory** - Katalogisiert die Implementierung. Umfasst: benutzerdefinierte Module, Composer-Abhängigkeiten, Drittanbietererweiterungen, Konfiguration, Storefront-Komponenten (falls zutreffend), Dateien, Erweiterungspunkte, Ereignisse, Plug-ins, APIs, Cron-Aufträge, Warteschlangen, Datenbankschema und benutzerdefinierte Datenbanktabellen.
- **Analyze**: Führt eine statische Analyse durch, um Speicheranpassungen, Abweichungen von einer standardmäßigen [!DNL Adobe Commerce]-Installation und die Interaktion dieser Anpassungen im gesamten Programm zu identifizieren.
- **Klassifizieren** - Verwendet KI, um jede Anpassung zu interpretieren, zusammenzufassen, was die Anpassung tut, verwandte Funktionen zu gruppieren, Implementierungsmuster zu identifizieren und kontextbezogene Migrationsempfehlungen bereitzustellen.
- **Zuordnen und empfehlen** - Ordnet jede Funktion ihrer [!DNL Adobe Commerce as a Cloud Service] Entsprechung zu, einschließlich: Standardfunktionen, [!DNL App Builder]-Anwendungen oder Adobe-Services. Im Anschluss daran wird ein Modernisierungspfad empfohlen und die Komplexität, die Abhängigkeiten und der Implementierungsaufwand werden bewertet.
- **Bericht** - Erstellt eine exportierbare Roadmap für die Planung der Migrationsausführung, mit der Sie die Risiken an die Stakeholder kommunizieren können. Es werden auch Prioritäten, Abhängigkeiten, technische Verschuldung und Implementierungsrisiken genannt.

### Bewertungswert

Der Wert einer Bewertung entspricht dem Maß an Vertrauen, das Sie haben können, bevor Sie sich auf Entwicklungsspezifikationen festlegen. Anstatt eine Migration mit regelmäßigen Scoping-Praktiken zu schätzen, bietet die Bewertung ein evidenzbasiertes Verständnis der Implementierung. Dazu gehört, welche Anpassungen einfach zu migrieren sind, welche neu gestaltet werden müssen und welche vollständig eingestellt werden können. Bewertungen kommen routinemäßig zu veralteten oder nicht verwendeten Funktionen, sodass Sie technische Schwierigkeiten reduzieren können.

Jede Empfehlung enthält Belege zusammen mit Zitaten zurück zur zugrunde liegenden Implementierung, die es Architekten und Ingenieuren ermöglichen, während der Planung zu validieren. Da jede Bewertung derselben Methodik folgt, können Sie mehrere Entwicklungsbedürfnisse mithilfe eines konsistenten Bewertungs- und Planungs-Frameworks vergleichen.

Die Bewertung ist nicht nur ein Ausgangspunkt. Das nachgelagerte Migrations-Tool nutzt die Ergebnisse der Bewertung, um die Implementierung zu beschleunigen und die Konsistenz mit dem genehmigten Migrationsplan sicherzustellen. Die Anpassungsanalyse wird zum Blueprint für die Anwendungsmodernisierung, während die Datenbewertung den Datenmigrationsaufwand durch die Analyse der Datenbankgröße, des Entitätsbestands und benutzerdefinierter Tabellen abdeckt.

### Prüfungsumfang

Das Migrationsbewertungs-Tool konzentriert sich auf das Verständnis der gesamten Migrationslandschaft. Es analysiert benutzerdefinierte Module, Plug-ins, Ereignisse, APIs, Cron-Aufträge, Warteschlangen, Integrationen mit externen Systemen, Storefront-Merkmale und das Datenbankschema, von dem diese Anpassungen abhängen. Die Bewertung ordnet die Ergebnisse den verfügbaren [!DNL Adobe Commerce as a Cloud Service]-Funktionen zu und identifiziert, wo Funktionen mithilfe von [!DNL App Builder] modernisiert oder für die SaaS-Architektur neu entwickelt werden sollten.

Die Bewertung ist eher ein Planungs- als ein Ausführungswerkzeug. Er ermittelt, was modernisiert werden sollte, schätzt die Komplexität der Implementierung ein und gibt Empfehlungen. Implementierungsentscheidungen und Architekturvalidierung bleiben gemeinsame Aktivitäten von Adobe, Partnern und Customer-Engineering-Teams.

Daten, die in benutzerdefinierten Tabellen von Erweiterungen von Drittanbietern gespeichert werden, werden als Überlegungen zur Migration angezeigt. Bei der standardmäßigen Datenmigration werden diese Daten nicht automatisch migriert. Zur Unterstützung dieser Szenarien könnten benutzerdefinierte [!DNL App Builder] erforderlich sein. Weitere Informationen finden [&#x200B; im &#x200B;](#data-migration-commerce-data-migration-service) zur Datenmigration .

Die Bewertung bietet Analysen für die Workflows zur Anpassung der Storefront und Datenmigration:

- Migration von Code und Storefront - Die Anwendungsanalyse der Bewertung wird zur Blueprint für das Commerce Developer MCP.
- Datenmigration - Der Entitätsbestand der Bewertung, die Analyse der Datenbankmerkmale und die Analyse benutzerdefinierter Tabellen bilden den Umfang für den Commerce-Datenmigrations-Service.

Sie können Bewertungen auch bei der Weiterentwicklung Ihrer Anwendungen erneut ausführen. Auf diese Weise können Ihre Teams Korrekturarbeiten validieren, den Modernisierungsfortschritt messen und Migrationspläne während des gesamten Projekts kontinuierlich verfeinern.

### Nächste Schritte

Jede [!DNL Adobe Commerce as a Cloud Service] Migration sollte mit einer Bewertung beginnen. Dies ist eine kostengünstige Methode, um den Umfang festzulegen, die Unsicherheit zu reduzieren und einen gemeinsamen Migrationsplan zu erstellen, bevor die Implementierung beginnt.

Weitere Informationen zu den Bewertungs-Tools und zum nachgelagerten Entwickler-Workflow finden Sie unter [Adobe Commerce Developer MCP](https://developer.adobe.com/commerce/extensibility/developer-agent/).

## Migration von Code und Storefront (Commerce Developer MCP)

In [!DNL Adobe Commerce on Cloud] oder On-Premise-Anpassungen können prozessinterne PHP-Module, Plug-ins und Ereignisbeobachter verwenden, die innerhalb der Anwendung ausgeführt werden. [!DNL Adobe Commerce as a Cloud Service] ist eine versionslose SaaS-Plattform, und dieses Modell gilt nicht mehr. Anpassungen werden als prozessexterne [!DNL Adobe Developer App Builder] ausgeführt, die über Ereignisse und APIs in Commerce integriert werden können. Die Modernisierung der Anpassungen eines Stores für diese Architektur ist in der Regel der wichtigste technische Aufwand bei einer [!DNL Adobe Commerce as a Cloud Service].

### Übersicht über die Code-Migration

Ausgehend von der Migrationsbewertung bietet das Commerce Developer MCP ein dialogorientiertes IDE-Erlebnis für die Modernisierung veralteter PHP-Anpassungen in [!DNL App Builder]. Es bietet auch Unterstützung für den Wiederaufbau von Storefronts auf Edge Delivery Services (EDS). Durch die direkte Nutzung der Ergebnisse des Migrationsbewertungswerkzeugs sorgt das Commerce Developer MCP dafür, dass die Implementierung mit dem genehmigten Migrationsfahrplan im Einklang steht, indem es die manuelle Interpretation reduziert, die Rückverfolgbarkeit aufrechterhält und die Konsistenz des gesamten Prozesses sicherstellt.

Während die Migration der Hauptanwendungsfall ist, ist der Commerce Developer MCP als umfassender KI-Entwicklungsagent für [!DNL Adobe Commerce] konzipiert. Das MCP unterstützt Modernisierung, Neuentwicklung, operative Workflows und alle Updates für [!DNL Adobe Commerce as a Cloud Service]. Dank dieser Flexibilität können Teams auch lange nach der Migration Commerce-Anwendungen erstellen und erweitern.

### Commerce Developer MCP

Anhand der Ergebnisse der [Migrationsbewertung](#migration-assessment-tool) wandelt der Commerce Developer MCP identifizierte Anpassungen mithilfe eines iterativen Entwicklungs-Workflows in [!DNL App Builder] Anwendungen um. Beachten Sie bei der Entwicklung mit diesen Tools die folgenden Richtlinien:

- **Mit dem Blueprint beginnen** - Das Commerce Developer MCP nutzt die Migrationsbewertung und verwendet die identifizierten Anpassungen, Empfehlungen und Migrationsprioritäten als Grundlage für die Implementierungsplanung.

- **Jede Anpassung planen** - Für jede Anpassung entwickelt der Commerce Developer MCP eine Spezifikation, die die empfohlene [!DNL Adobe Commerce as a Cloud Service], die erforderlichen Integrationsmuster und alle Neugestaltungen beschreibt, die für die Umstellung auf eine prozessexterne Anwendung erforderlich sind.

- **Gemeinsam erstellen** - Anstatt zunächst Code zu generieren, unterstützt Sie das Commerce Developer MCP während des gesamten Entwicklungslebenszyklus, indem es Implementierungen plant, die Architektur erörtert, Code generiert und verfeinert, empfohlene Muster validiert und Bereitstellungsanleitungen bereitstellt. Entwickler können generierte Implementierungen iterativ durch natürliche Sprache verfeinern, sodass sich die Projektdetails während des gesamten Modernisierungsvorgangs gemeinschaftlich entwickeln können.

  - Die generierten Implementierungen sind so konzipiert, dass sie die Bereitstellung beschleunigen und gleichzeitig von den Engineering-Teams vollständig überprüfbar, testbar und erweiterbar bleiben.

- **Integrieren und Bereitstellen** - Das Commerce Developer MCP verbindet Anwendungen über die entsprechenden Integrationsmuster mit Commerce, unterstützt Bereitstellungs-Workflows und validiert Implementierungen vor der Bereitstellung anhand empfohlener Architekturmuster, was die Konsistenz verbessert und den doppelten Aufwand reduziert.

  - Das Commerce Developer MCP enthält das [!DNL Adobe Commerce App Builder] MCP, das Domain-Kenntnisse, Implementierungsmuster, Architekturanleitungen, kontextuelle Produktexperten und validierte Codierungsverfahren direkt in Ihrem Entwicklungs-Workflow bereitstellt. Dadurch wird sichergestellt, dass die MCP-Empfehlungen weiterhin auf die Best Practices von Adobe abgestimmt sind, unabhängig davon, ob die Entwickler direkt mit dem Commerce Developer MCP oder in Kombination mit anderen Agenten wie Claude, Cursor oder Copilot arbeiten.

### Modernisierung der Storefront

Im Frontend modernisiert der Commerce Developer MCP [Storefronts](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de) auf Edge Delivery Services (EDS) für Commerce mithilfe der Adobe Commerce-Textbausteine, Dropdown-Komponenten und EDS-Blöcke.

Das Commerce Developer MCP lädt vorhandene Storefront-Projekte basierend auf dem Commerce-Textbaustein. Es modernisiert Ihre Storefront durch:

- Erstellen responsiver EDS-Blöcke
- Generieren von Commerce-fähigen Seitendaten (Startseite, PLP, PDP, Warenkorb, Checkout, Konto)
- Erstellen und Erweitern von Dropdown-Komponenten
- Übersetzen von Designs in EDS-Implementierungen
- Konvertieren veralteter monolithischer Storefronts in eine zusammensetzbare EDS-Blockarchitektur

Der MCP unterstützt auch bei:

- Komponentenmodernisierung
- Wiederverwendbare Blockzusammensetzung
- Erlebnisoptimierung
- Abstimmung mit aktuellen Best Practices für Edge Delivery Services

### MCP-Wert für Entwickler

Der Wechsel von PHP-Anpassungen im laufenden Prozess hin zu zusammenstellbaren [!DNL App Builder]-Anwendungen stellt einen bedeutenden Wandel der Architektur dar. Das Commerce Developer MCP schließt diese Lücke, indem es [!DNL Adobe Commerce], [!DNL App Builder] Implementierungsmuster und Best Practices für Produkte direkt in den Entwicklungs-Workflow einbettet.

Die Einbeziehung dieses Kontexts bietet eine verbesserte Konsistenz sowohl bei der Versandgeschwindigkeit als auch bei der technischen Qualität. Teams können Anwendungen schneller modernisieren und gleichzeitig Implementierungen erstellen, die einer konsistenten Architekturanleitung folgen.

Durch die Einbettung empfohlener Implementierungsmuster reduziert das Commerce Developer MCP die Abhängigkeit von individuellem Know-how und hilft Unternehmen, Modernisierungsmaßnahmen in allen Projekten konsistent zu skalieren.

Der Migrationsprozess ist auch eine Möglichkeit, die bestehende Implementierung zu verbessern. Teams können veraltete Anpassungen vereinfachen, veraltete Funktionen einstellen, SaaS-Funktionen übernehmen und die Anwendungsarchitektur modernisieren, anstatt historische technische Schulden voranzutreiben.

Da das Commerce Developer MCP die Migrationsbewertung direkt nutzt, bleibt bei jedem Modernisierungsansatz die Rückverfolgbarkeit bis zur ursprünglichen Bewertung erhalten, sodass die Implementierung weiterhin mit der genehmigten Migrationsplanung übereinstimmt.

Das Commerce Developer MCP fördert auch das Design zusammensetzbarer Anwendungen, indem es modulare [!DNL App Builder]-Anwendungen fördert, die sich unabhängig von den sich ändernden Geschäftsanforderungen entwickeln können.

### MCP-Umfang für Entwickler

Am Backend modernisiert der Commerce Developer MCP die Anpassungs- und Integrationsebene, indem PHP-Module, Plug-ins und Ereignisbeobachter in [!DNL App Builder]-Anwendungen umgewandelt werden, und legt Integrationsmuster fest, um sie mit Adobe Commerce zu verbinden. Außerdem wird die Entwicklung an der Kasse, bei Zahlungen und in der Admin-Benutzeroberfläche beschleunigt.

Im Frontend modernisiert der Commerce Developer MCP [Storefronts von Commerce](#storefront-modernization) auf Edge Delivery Services.

Die Datenmigration wird vom MCP nicht verarbeitet. Geschäftsdaten werden über den [Commerce Data Migration Service](#data-migration-commerce-data-migration-service) migriert. Das MCP unterstützt die [!DNL App Builder] Anwendungen, die erforderlich sind, wenn Geschäftslogik oder benutzerdefinierte Tabellen eine Anwendungsmodernisierung erfordern.

### Nächste Schritte

Die Modernisierung von Code und Storefront beginnt, sobald die Roadmap für das Migrationsbewertungs-Tool den Migrationsbereich und die Prioritäten festgelegt hat.

Weitere Informationen zur Installation und Verwendung des MCP finden Sie in der Dokumentation [Commerce Developer MCP](https://developer.adobe.com/commerce/extensibility/developer-agent/) .

## Datenmigration (Commerce Data Migration Service)

Für die Migration zu [!DNL Adobe Commerce as a Cloud Service] müssen u. U. jahrelange Daten migriert werden, darunter: Kataloge, Bestellungen, Kunden und Konfigurationen.

Der Commerce-Datenmigrations-Service ersetzt eine manuelle Migration durch einen einzigen, wiederholbaren, automatisierten Prozess. Dies macht komplexe Datenbankmigrationen vorhersehbarer und effizienter.

### Commerce Data Migration Service

Bei einer Migration wird ein geführter Workflow verwendet, der von einem Docker-Befehlszeilen-Tool (`./bin/console migration`) gesteuert wird. Ein Systemintegrator oder Benutzer führt diesen Workflow für den Quellspeicher aus.

Die Migration von Kerndaten ist automatisiert, aber die meisten Migrationen umfassen nicht standardmäßige Schemata, Erweiterungen und Edge-Fälle. Daher beginnen alle Migrationen mit einer [Bewertung](#migration-assessment-tool) des Quellspeichers. Nachdem Sie die Anmeldeinformationen und die Konnektivität überprüft, die Migration registriert und eine Überprüfungsgrundlinie eingerichtet haben, können Sie mit der Datenmigration fortfahren.

Das Migrations-Service-Tool führt die folgenden Datenverwaltungsschritte aus:

1. **Extrahieren und Transformieren** - Extrahiert alle relevanten Daten parallel aus der Quelle und gestaltet sie für die [!DNL Adobe Commerce as a Cloud Service] neu. Inkompatible Daten werden herausgefiltert und benutzerdefinierte Attribute und andere Strukturen werden neu zugeordnet.
1. **Load** - Überträgt die extrahierten Daten an den Commerce-Datenmigrations-Service. Der Service lädt die Daten in die [!DNL Adobe Commerce as a Cloud Service], erstellt dann die Indizes neu und nimmt den Katalog auf.
1. **Verify** - Vergleicht Quell- und Zieldaten auf Datenbankebene. Anschließend validiert der Service ein Beispiel für Live-Datensätze über die GraphQL-Storefront- und die Admin-REST-APIs, um die Daten zu überprüfen.
1. **Bericht** - Konsolidiert die Ergebnisse jedes Schritts in einem endgültigen Migrationsbericht.

Diese Datenverschiebungsstufen erfordern ein Wartungsfenster, aber während der Vorbereitungsphase bleibt der Speicher betriebsbereit, wodurch Ausfallzeiten auf ein Minimum beschränkt werden.

### Wert des Migrationsdienstes

Der Commerce-Datenmigrations-Service bewahrt die Datenintegrität mithilfe von Beweisen. Jede Migration wird durch den Vergleich von Quell- und Zieldaten und die Validierung eines Beispiels von Live-Datensätzen über die APIs verifiziert. Daten, die [!DNL Adobe Commerce as a Cloud Service] nicht eindeutig zugeordnet werden können, z. B. benutzerdefinierte Attribute, werden während der Extraktion automatisch gefiltert und neu zugeordnet.

Der Migrationsdienst wurde für Datenbanken im Unternehmensmaßstab entwickelt. Die Datenmigration wird asynchron partitioniert und verarbeitet, sodass große Kataloge und umfangreiche Auftragsverläufe zuverlässig migriert werden können. Wenn die Pipeline wächst, können mehrere Migrationen parallel ausgeführt werden. Wenn eine Migration unterbrochen wird, wird sie von der letzten abgeschlossenen Phase fortgesetzt und angehaltene Aufträge werden automatisch erkannt und erneut versucht.

Ausfallzeiten werden auf folgende Weise minimiert:

- Die meisten Arbeiten werden ausgeführt, während das Geschäft aktiv bleibt, was bedeutet, dass nur die endgültige Umstellung ein Wartungsfenster erfordert.
- Die Datenmigration verwendet hocheffiziente direkte SQL-Lese- und Schreibvorgänge und überspringt Tabellen und Datensätze, die nicht migriert werden müssen.

Da bei Migrationen Produktionsdaten durch die Adobe-Infrastruktur verschoben werden, ist der gesamte Pfad gesichert:

- Alle Uploads werden vor Erreichen des Ziels auf Malware überprüft
- Die Aufnahmeschicht validiert Dateitypen und blockiert unsichere Datenbankvorgänge
- Jede Anfrage wird mithilfe von Adobe IMS und Gateway-Signaturüberprüfung authentifiziert

Der Commerce-Datenmigrations-Service ist weltweit in der Produktionsumgebung verfügbar und hat bereits mehrere Migrationen auf Unternehmensebene durchgeführt.

### Benutzerdefinierte Daten und Daten von Drittanbietern

Der Migrationsdienst unterstützt nur die wichtigsten Commerce-Daten von Erstanbietern. Der Migrationsdienst verarbeitet keine benutzerdefinierten Entitäten von Drittanbietern.

Daten von Drittanbietern können fallweise migriert werden, was eine entsprechende Anpassung an das Docker-Extraktions-Tool erfordert. Nach der Erstellung benutzerdefinierter Tools können die Daten aus der Quelle extrahiert und in die [!DNL App Builder]- oder Drittanbieterdatenbank geschrieben werden.

Da jede Erweiterung ihre Daten unterschiedlich modelliert, kann ein Migrationspfad für Drittanbieterdaten nur entworfen werden, nachdem das Schema und die Speicherorte des Quell- und Zielspeichers bestimmt wurden. Datenmigrationen von Drittanbietern sollten frühzeitig erkannt werden, um Zeit für die Festlegung des Umfangs zu haben.

### Nächste Schritte

Wenn Sie bereit für die Migration sind, füllen Sie den [Fragebogen zur Datenmigration](../assets/data-migration-scoping-questionnaire.xlsx) aus, der die Quelltopologie, den Entitätsbereich, die Volumes, Compliance-Beschränkungen, die Umstellungsmechanik und alle [benutzerdefinierten Tabellen) &#x200B;](#custom-and-third-party-data), die für die Migrationsplanung erforderlich sind. Durch das Ausfüllen dieses Fragebogens kann Adobe Ihre Umgebung bewerten und ein Migrationsfenster planen.

Lesen Sie die [Handbuch zum Tool für die Massendatenmigration](bulk-data/migration-tool.md), um mehr über den Workflow, die unterstützten Daten und die Verifizierung zu erfahren.

Systemintegratoren, die eine Quellumgebung vorbereiten, können auch die standardmäßige [Adobe Commerce Cloud-CLI](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview) und die [Adobe Developer Console](https://developer.adobe.com) für IMS-Anmeldeinformationen verwenden.
