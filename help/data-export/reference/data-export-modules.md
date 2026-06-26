---
title: SaaS-Datenexportmodule
description: Erfahren Sie mehr über die Magento-Modulpakete in  [!DNL SaaS Data Export]  und ihre Rollen bei der Datenerfassung, Umwandlung und Übermittlung an Adobe SaaS-Services.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Developer
feature: Services
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 111
ht-degree: 0%

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
