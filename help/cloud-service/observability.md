---
title: Beobachtbarkeit für [!DNL Adobe Commerce as a Cloud Service]
description: Erfahren Sie mehr über die Observability-Tools und Telemetriefunktionen, die für  [!DNL Adobe Commerce as a Cloud Service] verfügbar sind, einschließlich Metriken, Protokollierung und Verfolgung.
feature: Cloud, Integration
role: Admin, Developer
level: Intermediate
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
autotag-review: '2026-06-09T15:41:54.613Z'
TQID: 'https://experienceleague.adobe.com/jTPNVSy6cP8v-pV-3pyqgJX-PAzFFhOUf9SjQIMeBns'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: ef32511703a96b5f4db32d54229e9a7cbe961f12
workflow-type: tm+mt
source-wordcount: 607
ht-degree: 0%

---

# Beobachtbarkeit

Die Beobachtbarkeit ist ein wichtiger Aspekt der [!DNL Adobe Commerce as a Cloud Service]. Sie umfasst die Erfassung, Verarbeitung und Visualisierung von Telemetriedaten - einschließlich Metriken, Protokollierung und Verfolgung -, sodass Sie den Zustand von Anwendungen überwachen, Leistungsprobleme diagnostizieren und die Zuverlässigkeit Ihrer Commerce-Plattform und ihrer Integrationen optimieren können.

## [!DNL Adobe Commerce as a Cloud Service]

### Übersicht über die Beobachtbarkeit

Observability bietet Ihnen Einblick in den Zustand und die Leistung Ihrer Adobe Commerce-Storefront und aller damit verbundenen App Builder-Anwendungen. Durch die Erfassung von Telemetriedaten in Ihrem Commerce-Ökosystem haben Sie folgende Möglichkeiten:

* **Metriken** z. B. API-Antwortzeiten, Anfrage- und Fehlerquoten sowie Ressourcenauslastung verfolgen, um die Echtzeit-Performance zu überwachen und Trends zu erkennen.
* **Zentralisieren Sie Protokolle** von Ihrer Anwendung, Infrastruktur, dem CDN und Integrationen in einer zentralen Ansicht, um die Fehlerbehebung zu beschleunigen.
* **Trace-Anfragen** End-to-End, während sie vom Frontend über Commerce und verbundene Apps laufen, helfen Ihnen dabei, Engpässe und Fehler zu identifizieren, bevor sie sich auf Kunden auswirken.

Gemeinsam helfen Ihnen diese Funktionen dabei, Probleme schnell zu identifizieren und zu beheben, die Leistung zu optimieren und ein zuverlässiges Kundenerlebnis sicherzustellen. In [Beobachtbarkeitsübersicht](https://developer.adobe.com/commerce/extensibility/observability/) wird erläutert, wie [!DNL Adobe Commerce as a Cloud Service] OpenTelemetry verwendet, um diese Telemetriesammlung für Eventing, Webhooks und App Builder-Anwendungen zu vereinheitlichen.

![Observability Architecture](./assets/observability.png){width="600" zoomable="yes"}

Adobe Commerce unterstützt die folgenden Observability-Tools über OpenTelemetry:

* Elasticsearch
* Grafana
* Jäger
* New Relic
* Prometheus
* Splunk
* Zipkin

### Konfigurieren von Abonnements

[Konfigurieren Sie Beobachtbarkeits](https://developer.adobe.com/commerce/extensibility/observability/configuration/)Abonnements im [!UICONTROL Admin] oder über die REST-API, um Protokolle, Metriken oder Spuren zu einem OpenTelemetry-kompatiblen Endpunkt zu leiten. Jedes Abonnement zielt auf bestimmte Komponenten ab (Webhooks, Ereignisse oder [!UICONTROL Admin UI SDK]).

### Observability REST-API

Die [Observability REST-API](https://developer.adobe.com/commerce/extensibility/observability/api/) stellt Endpunkte bereit, die Observability-Abonnements programmgesteuert erstellen, abrufen, aktualisieren und löschen. Verwenden Sie diese Endpunkte, um die Konfiguration über Instanzen hinweg zu automatisieren.

## Adobe Developer App Builder

### App Builder-Instrumentierung

[Implementieren Sie die Beobachtbarkeit in [!DNL App Builder]](https://developer.adobe.com/commerce/extensibility/observability/app-builder/) um den Ablaufverfolgungskontext aus Commerce in Ihre [!DNL App Builder]-Aktionen zu übertragen, sodass die Protokolle und Ablaufverfolgungen beider Systeme in Ihrer Beobachtbarkeitsplattform übereinstimmen. Behandelt die Instrumentierung für Webhook-basierte und ereignisbasierte Integrationen.

[!DNL App Builder] bietet außerdem integrierte Tools für die [Verwaltung von Anwendungsprotokollen](https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/application_logging/logging) einschließlich CLI- und Developer Console-Zugriff und Protokollweiterleitung an externe Lösungen wie Splunk, Azure und New Relic.

### Fernmessbibliothek

Die [`@adobe/aio-lib-telemetry`](https://github.com/adobe/aio-lib-telemetry/blob/main/docs/usage.md)-Bibliothek wird von App Builder-Aktionen zum Ausgeben von OpenTelemetry-kompatiblen Protokollen und Spuren verwendet. Behandelt Installation, Konfiguration und Export-Setup.

### Lokale Entwicklung und Tests

[Testen Sie die Einrichtung der Beobachtbarkeit lokal](https://developer.adobe.com/commerce/extensibility/observability/local-development/) bevor Sie sie bereitstellen. Verwenden Sie [!DNL Grafana] für die Visualisierung und Tunnelweiterleitung (z. B. [!DNL Ngrok]), um Telemetrie von einer Remote-Commerce-Instanz auf Ihrem Entwicklungsrechner zu erhalten.

## [!DNL API Mesh]

### API-Mesh-Protokollierung

[API Mesh-Protokollierung](https://developer.adobe.com/graphql-mesh-gateway/mesh/advanced/logging/) ermöglicht die Überwachung und Fehlerbehebung von Anfragen, die über Ihr Mesh geleitet werden, mithilfe von Graph-IDs. Protokolle stapelweise exportieren oder zur zentralen Analyse an Plattformen wie [!DNL New Relic] weiterleiten.

## Schaufenster

### CDN- und Real User Monitoring

[Proxy Real User Monitoring (RUM)](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/content-delivery-network/#proxy-rum-through-the-origin-to-avoid-a-tls-handshake) Datenerfassung über Ihre CDN-Herkunft, um einen zusätzlichen TLS-Handshake zu vermeiden und die Frontend-Leistungsmessung zu verbessern.

## Beobachtbarkeits-Videos

Die folgenden Videos bieten einen allgemeinen Überblick über Observability-Angebote in [!DNL Adobe Commerce as a Cloud Service]:

* [App Builder-Beobachtungsvideos](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/observability/overview){target="_blank"}
* [Videos zu API-Mesh](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/extensibility/api-mesh/getting-started-api-mesh){target="_blank"}
