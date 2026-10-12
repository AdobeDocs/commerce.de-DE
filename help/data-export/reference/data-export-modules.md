---
title: SaaS-Datenexportmodule
description: Erfahren Sie mehr über die Magento-Modulpakete in [!DNL SaaS Data Export] und ihre Rollen bei der Datenerfassung, -umwandlung und Übermittlung an Adobe SaaS-Services.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Developer
feature: Services
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 8%
---

# SaaS-Datenexportmodule

[!DNL SaaS Data Export] besteht aus zwei Modulgruppen: der ersten für Datenerfassung und Indizierung und der zweiten für HTTP-Übertragung und -Übermittlung.

Diese Module behandeln die Erkennung von Entitätsänderungen, die Feed-Indizierung, die Datenextraktion und die Schemadefinition.
Die folgende Tabelle enthält nur Module auf Framework-Ebene. Die vollständige Liste der verfügbaren Module hängt von den installierten Paketen ab.

| Modul | Zweck | Schlüsselklassen |
| --- | --- |--- |
| `DataExporter` | Core-Framework: Indexer, Feed-Tabelle, Hash, Wiederholen, Sperren | `FeedIndexer`, `FeedIndexMetadata`, `FeedMetadataPool`, `FeedLockManager` |
| `QueryXml` | XML-basierte Abfrage-DSL für die Datenerfassung | `QueryFactory`, `QueryProcessor`, `SelectBuilder` |
| `SaaSCommon` | Freigegebener HTTP-Transport, erneuter Versuch, CLI (`saas:resync`), Resynchronisation | `ExportFeed`, `SubmitFeed`, `ResyncManager`, `ResyncManagerPool`, `ProgressBarManager` |

Informationen zur Zusammenarbeit dieser Module während der Synchronisierung finden Sie unter [SaaS-Datenexport-Pipeline](../sync-overview.md).

>[!MORELIKETHIS]
>
>- [Funktionsweise der Synchronisierung](../sync-overview.md)
>- [Feed-Tabellenschema](feed-table-reference.md)
>- [Verwalten der SaaS-Datenexporterweiterung](../manage-extension.md)
