---
title: Migrieren nach [!DNL Adobe Commerce as a Cloud Service]
description: Erfahren Sie, wie Sie zu  [!DNL Adobe Commerce as a Cloud Service].
exl-id: 9065c92a-f6b2-4464-8ec0-5c549bf78104
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 34057c1e55ff117ea7aab4407f31548ce826691b
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 0%

---

# Migrieren nach [!DNL Adobe Commerce as a Cloud Service]

{{accs-early-access}}

[!DNL Adobe Commerce as a Cloud Service] bietet die meisten vorkonfigurierten Konfigurationen. Wenn Sie jedoch von einer bestehenden Adobe Commerce in der Cloud oder einer lokalen Instanz migrieren, müssen Sie je nach Ihrer spezifischen Konfiguration verschiedene Migrationsaktionen durchführen.

## Migrationspfade

[!DNL Adobe Commerce as a Cloud Service] unterstützt mehrere Migrationspfade, abhängig von Ihrer Timeline, Storefront und Ihren Anpassungen.

Als Alternative zu einer vollständigen Migration unterstützt [!DNL Adobe Commerce as a Cloud Service] eine stufenweise Migration mithilfe von Commerce Optimizer oder eines inkrementellen Ansatzes.

* **Inkrementelle Migration** Dieser Ansatz umfasst die schrittweise Migration Ihrer Daten, Anpassungen und Integrationen. Dieser Ansatz ist ideal für große Händler mit vielen Anpassungen, die ihre komplexen Anpassungen und Daten schrittweise in ihrem eigenen Tempo auf [!DNL Adobe Commerce as a Cloud Service] umstellen möchten.

![Inkrementelle Migration](./assets/incremental.png){width="600" zoomable="yes"}

* **Commerce Optimizer**: Bei diesem Ansatz können Sie iterativ migrieren, indem Sie Commerce Optimizer als Übergangsphase verwenden, um komplexe Anpassungen und Daten in Ihrem eigenen Tempo in [!DNL Adobe Commerce as a Cloud Service] zu verschieben. Commerce Optimizer bietet Zugriff auf Merchandising-Services, die auf Katalogkanälen und Richtlinien basieren, auf die Commerce-Storefront mit Edge Delivery und auf Produktvisualisierungen mit AEM Assets.

![Iterative Migration](./assets/optimizer.png){width="600" zoomable="yes"}

* **Vollständige Migration** Dieser Ansatz umfasst die Migration aller Daten, Anpassungen und Integrationen auf einmal. Dieser Ansatz ist ideal für kleinere Händler mit wenigen Anpassungen, die schnell auf [!DNL Adobe Commerce as a Cloud Service] umstellen möchten.

Die folgende Tabelle bietet einen Überblick über den Migrationsprozess für verschiedene Storefronts und Konfigurationen:

|                    | LUMA-Storefront | PWA-Storefront | Commerce Storefront powered by Edge Delivery | Headless |
|--------------------|----------------------------------------|----------------------------------------|------------------------------------------------------|----------------------------------------|
| Datenmigration | Erforderlich | Erforderlich | Erforderlich | Erforderlich |
| Schaufenster | Migrieren zur Commerce-Storefront mit Edge Delivery | Migrieren zur Commerce-Storefront mit Edge Delivery oder Wartung | Keine Auswirkung | Keine Auswirkung |
| API-Mesh | Neues Netz erstellen | Neues Netz erstellen oder vorhandenes neu konfigurieren | Neues Netz erstellen oder vorhandenes neu konfigurieren | Neues Netz erstellen oder vorhandenes neu konfigurieren |
| Integrationen | Nutzen des Integrations-Starter-Kits | Nutzen des Integrations-Starter-Kits | Nutzen des Integrations-Starter-Kits | Nutzen des Integrations-Starter-Kits |
| Anpassungen | Zu App Builder und API Mesh wechseln | Zu App Builder und API Mesh wechseln | Zu App Builder und API Mesh wechseln | Zu App Builder und API Mesh wechseln |
| Verwaltung von Assets | Migration erforderlich bei Verwendung von OOTB | Migration erforderlich bei Verwendung von OOTB | Migration erforderlich bei Verwendung von OOTB | Migration erforderlich bei Verwendung von OOTB |
| Erweiterungen | Migrieren nach App Builder | Migrieren nach App Builder | Migrieren nach App Builder | Migrieren nach App Builder |

Wie aus der Tabelle ersichtlich, bestehen die Abhilfemaßnahmen für jede Migration aus:

* **Datenmigration** - Verwenden der bereitgestellten Migrations-Tools, um Daten von Ihrer vorhandenen Instanz zu [!DNL Adobe Commerce as a Cloud Service] zu migrieren.
* **Storefront** - Bestehende EDS- und Headless-Storefronts erfordern keine Abschwächung, aber für LUMA-Storefronts ist eine Migration zu einer Commerce Storefront mit Edge Delivery erforderlich. PWA Studio-Storefronts können zu Commerce Storefronts migriert werden, die von Edge Delivery unterstützt werden oder in ihrem aktuellen Status beibehalten werden. Adobe stellt Accelerators zur Verfügung, die Sie bei der Migration von Storefronts unterstützen.
* **[API-](https://developer.adobe.com/graphql-mesh-gateway)**: Erstellen Sie ein neues Netz oder ändern Sie das vorhandene. Adobe stellt vorkonfigurierte Meshes zur Verfügung, um diesen Prozess zu unterstützen.
* **Integrationen** - Alle Integrationen müssen entweder das [Integrations-Starter-Kit](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/) oder die [[!DNL Adobe Commerce as a Cloud Service] REST-API](https://developer.adobe.com/commerce/services/reference/cloud-service/core-admin/) nutzen.
* **Anpassungen** - Alle Anpassungen müssen auf App Builder und API-Mesh verschoben werden.
* **Assets-**: Die gesamte Asset-Verwaltung erfordert eine Migration. Wenn Sie AEM Assets bereits verwenden, müssen Sie nicht migrieren.
* **Erweiterungen** - Alle prozessinternen Erweiterungen müssen als prozessexterne Erweiterungen neu erstellt werden. Bis Ende 2025 wird Adobe Zugriff auf unsere beliebtesten Erweiterungen bieten, um die Erstellungszeiten zu minimieren.

## Migrationsphasen

Die Migration von Ihrer aktuellen Adobe Commerce-Instanz zu einer neuen [!DNL Adobe Commerce as a Cloud Service] umfasst hauptsächlich die folgenden Phasen:

* **[Bereitschaft](#readiness-phase)** - Ermitteln Sie zunächst, ob Ihre Bereitstellung für den Wechsel zu ACS bereit ist. In dieser Phase sollten Sie sich auch mit den von ACS eingeführten Änderungen vertraut machen&#x200B;
* **[Implementierung](#implementation-phase)** Als Nächstes sollten Sie Code, Storefront, Erweiterungen und Integrationen für die Migration vorbereiten. Um den Übergang zu erleichtern, ermöglicht Adobe sowohl [kurzfristige als auch langfristige iterative Ansätze](#migration-paths). &#x200B;
* **[Go-Live](#go-live-phase)**: Testen und bestätigen Sie, dass alles eingerichtet ist, und führen Sie dann die Datenmigration durch.
* **[Nach der Live-Schaltung](#post-go-live-phase)** - Überwachen Sie in Zusammenarbeit mit Adobe Probleme und verbessern Sie die Leistung nach Abschluss der Migration nach Bedarf.

### Bereitschaftsphase

1. Überprüfen Sie zunächst die [!DNL Adobe Commerce as a Cloud Service] Architektur, das Erweiterbarkeits-Framework und die Storefront-Funktionen:

   * [Architektur von Adobe Commerce in Cloud Services](./overview.md)—Überprüfen Sie die Plattformarchitektur und die Unterschiede zu Ihrer aktuellen Adobe Commerce-Instanz.
   * [Adobe Commerce-Erweiterbarkeits-Framework](https://developer.adobe.com/commerce/extensibility/) - Ermitteln Sie, wie Sie Ihre aktuellen Anpassungen umstellen möchten.
   * [Commerce Storefront powered by Edge Delivery](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de) - Überprüfen Sie die empfohlene Storefront-Lösung.

1. Prüfen Sie Ihre Anpassungskompatibilität:

   * Identifizieren Sie Ihre aktuellen benutzerdefinierten Module und Integrationen von Drittanbietern.
   * Auswerten von Anpassungen, die mithilfe von App Builder erneut implementiert werden müssen.
   * Ordnen Sie Ihre aktuellen Anpassungen ihren App Builder-Erweiterungen-Äquivalenten zu.

1. Bestätigen Sie Ihre Storefront-Anforderungen und stellen Sie sicher, dass sie mit den Adobe Edge-Bereitstellungsfunktionen übereinstimmen.

1. Überprüfen Sie Ihre aktuellen Integrationen von Drittanbietern und bestätigen Sie die API-Kompatibilität mit der [!DNL Adobe Commerce as a Cloud Service].

### Implementierungsphase

Die folgenden Schritte beschreiben den Entwicklungs- und Ausführungsprozess der Migration:

1. Erstellen Sie eine neue [!DNL Adobe Commerce as a Cloud Service] im [Commerce Cloud Manager](./getting-started.md#create-an-instance).

1. Installieren erforderlicher Apps und Anpassungen. [!DNL Adobe Commerce as a Cloud Service] hat Zugriff auf unsere beliebtesten Apps. Wenn Sie zusätzliche Apps oder Anpassungen benötigen, können Sie diese mit App Builder erneut implementieren.

1. Richten Sie eine der folgenden GraphQL-basierten Storefronts ein:

   * [Erstellen einer Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de)
   * [Verwenden Sie PWA Studio, um eine benutzerdefinierte GraphQL-basierte Storefront zu erstellen](https://developer.adobe.com/commerce/pwa-studio/)

1. Migrieren Sie Ihre Daten aus Ihrer vorherigen Commerce-Instanz zu ACS:

   * Migrieren nativer Adobe Commerce-Daten mithilfe von Datenmigrations-Tools.
   * Migrieren von Erweiterungen und Anpassungen von Drittanbietern
   * Migrieren von Konfigurations- und Integrationsdaten:
      * Übertragen Sie API-Mesh-Konfigurationen, Services von Drittanbietern und Systemintegrationen mithilfe des [Adobe Commerce Integration Starter Kit](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/).

### Phase der Live-Schaltung

Validieren und testen Sie Ihre neue [!DNL Adobe Commerce as a Cloud Service]-Instanz mithilfe einer Sandbox-Umgebung, bevor Sie sie starten:

* **Funktionstests** Stellen Sie sicher, dass migrierte Daten, Storefront-Funktionen und Anpassungen nahtlos funktionieren.

* **Leistungstests** Bewerten Sie die Geschwindigkeit und Skalierbarkeit Ihrer Stores, um weltweit eine optimale Leistung sicherzustellen.

* **Sicherheitsaudit** - Überprüfen Sie Sicherheitsmaßnahmen, einschließlich API-Zugriffskontrolle und potenzieller Sicherheitslücken.

Nachdem Sie Ihre neue [!DNL Adobe Commerce as a Cloud Service]-Sandbox-Instanz validiert und getestet haben, können Sie Ihre Produktionsinstanz starten.

### Phase nach der Live-Schaltung

Führen Sie nach der Live-Schaltung die folgenden Aktivitäten nach dem Start aus:

1. Go-Live-Follow-up

   * Leiten Sie den Traffic an die neue Plattform um und überwachen Sie die Leistung.
   * Deaktivieren Sie Ihre alte Adobe Commerce-Instanz.

1. Überwachung nach der Einführung

   * Verwenden Sie Überwachungs-Tools, um einen stabilen Betrieb zu gewährleisten und Probleme nach der Markteinführung zu beheben.
