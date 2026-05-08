---
title: Sicherheitsübersicht
description: Erfahren Sie mehr über die Sicherheitsfunktionen für Adobe Commerce as a Cloud Service.
role: Admin, Developer, Leader
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: feb48068137c6a63e6594167fe969c3aa4b044c4
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Sicherheitsübersicht

[!DNL Adobe Commerce as a Cloud Service] basiert auf Sicherheit und bietet eine moderne, SaaS-native Commerce-Plattform, die Schutz auf Unternehmensniveau, Betriebsstabilität und Sicherheit für Unternehmen jeder Größe bietet.

Im Gegensatz zu herkömmlichen PaaS-Modellen entfällt mit dem SaaS-Modell die Belastung durch manuelles Patchen, Wartung der Infrastruktur und Upgrade-Zyklen. Die Sicherheit ist in jede Ebene der Plattform eingebettet - von Adobe verwalteter Infrastruktur und automatisierten Bereitstellungs-Pipelines bis hin zur Identitäts- und Zugriffsverwaltung durch [!DNL Adobe IMS].

[!DNL Adobe Commerce as a Cloud Service] nutzt das globale Sicherheits- und Compliance-Framework von Adobe und stellt so die Abstimmung mit Branchenstandards wie ISO 27001, SOC 2 und DSGVO sicher. Kunden profitieren von einem [Modell der gemeinsamen Verantwortung](./shared-responsibility.md) das die Rolle von Adobe bei der Sicherung der Plattform und die Rolle des Kunden bei der Verwaltung von Daten und Zugriff klar definiert.

Mit integrierten Schutzfunktionen wie Web Application Firewall (WAF), DDoS-Abschwächung, sicherer Bereitstellung und kontinuierlicher Suche nach Schwachstellen ermöglicht [!DNL Adobe Commerce as a Cloud Service] Unternehmen schnellere Innovationen, ohne die Sicherheit zu beeinträchtigen.

In diesem Dokument werden die Sicherheitsarchitektur, die betrieblichen Sicherheitsmaßnahmen und der Compliance-Status von [!DNL Adobe Commerce as a Cloud Service] erläutert, sodass Kunden fundierte Entscheidungen treffen und ihren digitalen Commerce-Betrieb sicher skalieren können.

## Content Delivery Network (CDN) und Firewall für Web-Anwendungen (WAF)

### Storefront CDN

Händler können sich dafür entscheiden, ein von Adobe verwaltetes CDN bereitzustellen oder eine eigene CDN-Lösung zum Schutz ihrer Commerce-gestützten Storefront zu erwerben.

>[!IMPORTANT]
>
>Wenn Kundinnen und Kunden sich für die Bereitstellung des von Adobe verwalteten CDN entscheiden, können sie keine CDN-Regeln konfigurieren. Benutzerdefinierte Caching-Regeln oder WAF-Regeln können von den Kundinnen und Kunden konfiguriert werden, wenn sie ihr eigenes CDN zum Schutz ihrer Storefronts einsetzen.

### [!DNL API Mesh for Adobe Developer App Builder] CDN

Die CDN-Ebene von [!DNL API Mesh] beendet TLS, führt das GraphQL-Gateway als Workers aus, stellt globales Edge-Caching und automatisches DDoS/WAF bereit und stellt `edge‑graph.adobe.io`/`edge‑sandbox‑graph.adobe.io` als öffentliche Mesh-Endpunkte bereit. Kunden können ihr eigenes CDN vorne hinzufügen, aber das CDN von [!DNL API Mesh] wird von Adobe festgelegt und verwaltet und Kunden können ihre eigenen WAF-Regeln nicht konfigurieren.

Weitere Informationen zu den Sicherheitsfunktionen von [!DNL API Mesh] finden Sie in der [API Mesh-Dokumentation](https://developer.adobe.com/graphql-mesh-gateway/mesh/security/){target="_blank"}.

### Backend-CDN

Ein integriertes CDN schützt [!DNL Adobe Commerce as a Cloud Service].

Aufgrund der [!DNL Adobe Commerce as a Cloud Service] Architektur werden bei der Bereitstellung einer -Instanz in einer zusammengesetzten Zelle durch einen Händler, z. B. `na1`, `eu1`, `au1` oder andere geografische Regionen, drei öffentliche Oberflächen offen gelegt:

| Oberfläche | Beispiel für URL-Muster |
| --- | --- |
| Admin-Benutzeroberfläche | `https://<region>.admin.commerce.adobe.com/<tenant-id>/admin/` |
| REST-API | `https://<region>.api.commerce.adobe.com/<tenant-id>/<endpoint>` |
| GraphQL-API | `https://na1.api.commerce.adobe.com/<tenant_id>/graphql/` |

[!DNL Adobe Commerce as a Cloud Service] verwendet eine Kombination aus WAF und CDN:

- **WAF** - Firewall-Schutz für Web-Anwendungen für alle öffentlichen [!DNL Adobe Commerce as a Cloud Service].
- **CDN** - Edge-Caching für statische Assets und zwischenspeicherbare GraphQL-Antworten.

WAF und CDN werden von der [!DNL Adobe Commerce as a Cloud Service] verwaltet und können von den Kunden nicht konfiguriert werden.

### DDoS-Schutz

Das integrierte CDN und WAF bieten sowohl DDoS-Schutz auf Netzwerkebene als auch auf HTTP-Ebene. [!DNL Adobe Commerce as a Cloud Service] stellt diese WAF- oder DDoS-Protokolle nicht direkt für Händler bereit.

## Datenspeicherung und -verschlüsselung

Wenn Daten in [!DNL App Builder] gespeichert werden, kann ein Händler auf die [!DNL App Builder]Speicheroptionen[ verweisen](https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/storage/). [!DNL App Builder] erzwingt die Isolierung von Mandanten, und der Zugriff auf Daten, die in diesen Services gespeichert sind, ist auf den Laufzeitnamespace beschränkt, in dem die Aktion ausgeführt wird. Es gibt keine Verschlüsselung von Daten im Speicher.

Bei Verwendung von [!DNL API Mesh] sollten geheime Daten in der `secrets.yaml`-Datei in der Netzkonfiguration gespeichert werden. [!DNL API Mesh] verschlüsselt diese geheimen Daten mit AES-256-Verschlüsselung ([https://developer.adobe.com/graphql-mesh-gateway/mesh/advanced/secrets/](https://developer.adobe.com/graphql-mesh-gateway/mesh/advanced/secrets/)).

Alle in [!DNL Adobe Commerce as a Cloud Service] gespeicherten Daten werden im Ruhezustand mit AES-256-Bit-Verschlüsselung verschlüsselt, und alle Daten werden während der Übertragung über HTTPS mit TLS 1.2 oder höher verschlüsselt.
