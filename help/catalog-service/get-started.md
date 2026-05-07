---
title: Erste Schritte mit [!DNL Catalog Service]
description: Erfahren Sie, wie Sie auf  [!DNL Catalog Service]  zugreifen und mit Frontend-Anwendungen und Services von Drittanbietern integrieren können.
role: Admin, Developer
exl-id: ee178e67-519d-4283-8de8-2634ae1f347a
source-git-commit: 50d8937c903efb1c56ec86e6bc4b947d2f198d49
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# Erste Schritte mit dem [!DNL Catalog Service]

Nachdem die [!DNL Catalog Service] aktiviert wurde, können Sie auf den Service zugreifen und ihn verwenden, um Katalogdaten wie Produkt- und Kategorieinformationen von Ihrer Adobe Commerce-Instanz abzurufen. Der Service ist als GraphQL-API verfügbar, auf die Sie über Commerce Admin oder ein beliebiges Frontend-Programm zugreifen können, das GraphQL-Abfragen unterstützt.

{{aco-merchandising-services}}

## Zugriff auf den Service

Die [!DNL Catalog Service] ist als GraphQL-API verfügbar, auf die Sie über Commerce Admin oder ein beliebiges Frontend-Programm zugreifen können, das GraphQL-Abfragen unterstützt. Der Service ist sowohl in SaaS- als auch in PaaS-Umgebungen verfügbar.

[!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."}

| Umgebung | Endpunkt |
| ------------ | ----------: |
| **Testen** | `https://catalog-service-sandbox.adobe.io/graphql` |
| **Produktion** | `https://catalog-service.adobe.io/graphql` |

[!BADGE nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."}

| Umgebung | Endpunkt |
| ----------- | --------:|
| Test läuft | `https://na1-sandbox.api.commerce.adobe.com/{{tenant-id}}/graphql` |
| Produktion (noch nicht verfügbar) | `https://na1.api.commerce.adobe.com/{{tenant-id}}/graphql` |

**URL-Struktur für SaaS-Endpunkte**

```text
https://<region>-<environment>.api.commerce.adobe.com/<tenantId>/graphql
```

- `<region>` ist die Cloud-Region, in der Ihre Instanz bereitgestellt wird.
- `<environment>` ist der Umgebungstyp, z. B. `sandbox`. Wenn es sich bei der Umgebung um eine Produktionsumgebung handelt, wird dieser Wert weggelassen.
- `<tenantId>` ist die eindeutige Kennung für die spezifische Instanz Ihres Unternehmens in der Adobe Experience Cloud.

Weitere Informationen zur Verwendung der Catalog Service GraphQL-API finden Sie im [Handbuch zu Catalog Service für Adobe Commerce](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/) in der *Dokumentation für Adobe Commerce*.

## Integration mit einer Headless-Storefront oder Services von Drittanbietern

Zur Integration mit einer Headless-Storefront müssen Sie die Storefront-Konfiguration aktualisieren, um die Kommunikation zwischen der Storefront und dem [!DNL Catalog Service] zum Abrufen von Produkt- und Kategoriedaten zu ermöglichen.

Wenn Sie die Adobe Commerce-Storefront auf Edge Delivery Services verwenden, fügen Sie den Catalog Service-Endpunkt zur Storefront-Konfiguration hinzu. Weitere Informationen finden Sie in der Dokumentation zu [Edge Delivery Services](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/#storefront-configuration).

Für andere Integrationen finden Sie Details zum Konfigurieren von Integrationen zwischen dem Service und Backend-Datenquellen in der Dokumentation zu Projekteinstellungen .

### Firewall-Konfiguration

Um [!DNL Catalog Service] durch eine Firewall zuzulassen, fügen Sie `commerce.adobe.io` zur Zulassungsliste hinzu.

## Katalog-Service und API-Mesh

Das [API Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht Entwicklern die Integration von privaten oder Drittanbieter-APIs und anderen Benutzeroberflächen mit Adobe-Produkten mithilfe von Adobe IO.

Informationen zur Installation [[!DNL Catalog Service]  Konfiguration finden Sie ](mesh.md) Thema „und API-Mesh“ .

## Überwachen und Fehlerbehebung beim Datenexport

Commerce Admin bietet Tools zur Überwachung und Fehlerbehebung beim Datenexport aus Commerce in Connected Services:

- **[Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard)** - Überwachen der Datensynchronisation zwischen dem [!DNL Catalog Service] und Ihrer Adobe Commerce-Instanz. Das Dashboard zeigt den allgemeinen Synchronisierungsstatus an und listet alle synchronisierten Produkte auf.

- **[Seite „Synchronisierungsstatus für Daten-Feeds](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status)** - Verfolgen Sie den Exportstatus aller Daten-Feeds, um die Konsistenz der Daten sicherzustellen. Auf dieser Seite werden Sie über Probleme informiert, die während des Exportvorgangs auftreten, damit Sie sie schnell beheben können. Der Status „Erfolgreich abgeschlossen“ zeigt an, dass Daten exportiert wurden und nach Abschluss des Datensynchronisierungsprozesses in den verbundenen Commerce-Services verfügbar sein werden.

>[!NOTE]
>
>Wenn die Seite Synchronisierungsstatus für Daten-Feeds nicht in der Commerce Admin für Commerce in Cloud- oder lokalen Bereitstellungen verfügbar ist, befolgen Sie die [Installationsanweisungen für Erweiterungen](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status#install-the-extension), um sie zu aktivieren.
