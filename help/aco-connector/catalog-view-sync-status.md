---
title: Überwachen der Synchronisierung von Katalogansichten für freigegebene B2B-Kataloge
last-update: 2026-09-03
description: Verwenden Sie die Seite „Synchronisierungsstatus für Katalogansicht“, um die Katalogansicht, die Richtlinie, die Preisbuchreferenz und die wichtigsten mit Adobe Commerce Optimizer synchronisierten Konfigurationsdaten zu überwachen und abzustimmen.
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: a40ebd6b-b542-4432-a730-1803ef74518d
    internal-label: Data Transfer
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
    internal-label: Data integration
source-git-commit: 1fd5e3d84d5249ce96014cae46e045528d2790d0
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 0%
---

# Überwachen der Synchronisierung von Katalogansichten für freigegebene B2B-Kataloge

Tracking der Synchronisation der B2B-Katalogansicht von [!DNL Adobe Commerce] nach [!DNL Adobe Commerce Optimizer] mithilfe des [!UICONTROL Catalog View Sync Status]-Dashboards in Commerce Admin.

[!UICONTROL Catalog View Sync Status] überprüft, ob die Katalogansicht, die Richtlinie, die Preisbuchreferenz und die Konfigurationen mit eingeschränktem Zugriff für jeden freigegebenen B2B-Katalog in [!DNL Adobe Commerce Optimizer] vorhanden sind und mit Ihrer [!DNL Adobe Commerce] übereinstimmen. Informationen zum Nachverfolgen der Synchronisierung von Produkt-, Preis- und Kategorie-Feeds finden Sie stattdessen unter [Verwalten der Datensynchronisierung](data-sync-status.md#verify-that-the-data-sync-is-working).

## Aufrufen der Synchronisierungsstatus-Seite {#access-the-sync-status-page}

Navigieren Sie vom Commerce-Administrator aus zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Catalog View Sync Status]**.

![Seite „Synchronisierungsstatus der Katalogansicht“, um den Synchronisierungsstatus der Katalogansicht, Richtlinie, Preisliste und Zugriffsschlüsselkonfigurationen in Adobe Commerce Optimizer zu überwachen](assets/catalog-view-sync-status.png){width="600" zoomable="yes"}

Die Seite verfügt über drei Registerkarten: [!UICONTROL Catalog Views], [!UICONTROL Orphaned in ACO] und [!UICONTROL Deleted].

## Interpretieren des Synchronisationsstatus für Ihre freigegebenen Kataloge {#interpret-sync-status}

Auf der Registerkarte [!UICONTROL Catalog View] stellt jede Zeile eine benutzerdefinierte freigegebene Katalogansicht dar, die aus einer Kombination aus freigegebener Katalog- und Store-Ansicht projiziert wird. Die Projektion umfasst die Katalogansicht, die Richtlinie, die Preisbuchreferenz und die Konfigurationsdaten für den eingeschränkten Zugriff, die [!DNL Commerce Optimizer Connector] für den freigegebenen Katalog nach [!DNL Adobe Commerce Optimizer] exportiert. Verwenden Sie die Statusinformationen, um festzustellen, ob die an die Storefront des Unternehmens gelieferten Daten vollständig und korrekt sind. In der folgenden Tabelle sind die häufigsten Statuswerte und ihre Bedeutung für Ihren freigegebenen Katalog zusammengefasst:

| Status | Was dies für Ihren freigegebenen Katalog bedeutet |
| --- | --- |
| **Degraded** | Etwas wurde direkt in [!DNL Adobe Commerce Optimizer] geändert, z. B. die Police oder das verknüpfte Preisbuch. Das Unternehmen sieht möglicherweise das falsche Sortiment oder die falsche Preisangabe, bis Sie das Problem behoben haben. Dies kann auch vorkommen, wenn der Zugriffsschlüssel, der Ansichtsname oder die Quelle in Commerce Optimizer geändert wird. |
| **fehlgeschlagen** | Die Katalogansicht ist in [!DNL Adobe Commerce Optimizer] nicht vorhanden oder wenn die Übergangsphase abläuft, bevor die erste Projektion durchgeführt wird. (Siehe [Konfigurieren der Synchronisierungseinstellungen für die ACO-Katalogansicht](#configure-aco-catalog-view-sync-settings)). Wenn der Synchronisierungsstatus eines Katalogs `Failed` ist, kann das Unternehmen nicht auf das Storefront-Erlebnis dieses freigegebenen Katalogs zugreifen. |
| **Einstellung** | Sie haben den freigegebenen Katalog in [!DNL Adobe Commerce] gelöscht. Die Katalogansicht ist weiterhin verfügbar, bis die Übergangsphase für die Löschung abläuft. Die standardmäßige Übergangsphase beträgt sieben Tage. Sie können die Standardeinstellung ändern, indem Sie die [Einstellungen für die Katalogansicht - Synchronisierung](#configure-aco-catalog-view-sync-settings) aktualisieren. |
| **Verwaist** | Die Katalogansicht bzw. der -Schlüssel wurde direkt in [!DNL Adobe Commerce Optimizer] Studio und nicht vom Connector erstellt. Siehe [Überprüfen verwaister und gelöschter Einträge](#review-orphaned-and-deleted-entries). |

[!UICONTROL Healthy], [!UICONTROL Pending] und [!UICONTROL Deleted] sind Informationszustände, die keine Maßnahmen erfordern. Siehe [Statuswerte synchronisieren](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/catalog-view-sync/catalog-view-sync-status#sync-status-values){target="_blank"} im *Commerce Admin Guide* um die vollständige Liste zu erhalten.

### Konfigurieren der Synchronisierungseinstellungen für die ACO-Katalogansicht {#configure-aco-catalog-view-sync-settings}

Wechseln Sie vom [!DNL Adobe Commerce] Admin (nicht [!DNL Adobe Commerce Optimizer] Studio) zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL ACO Catalog View Sync]** , um zu steuern, wie der Connector mit Löschungen und Erstellungen umgeht und ob er Drift automatisch repariert.

![Die Seite „ACO-Katalogansicht - Synchronisierungskonfiguration“ mit den Abschnitten „Löschen“, „Erstellen“ und „Drift-Abstimmung“](assets/aco-catalog-view-sync-configuration.png){width="600" zoomable="yes"}

- **[!UICONTROL Deletion Grace Period (days)]** - Anzahl der Tage, die die Katalogansicht, Richtlinie und Metadaten eines gelöschten freigegebenen Katalogs in [!DNL Adobe Commerce Optimizer] aufbewahrt werden, bevor sie entfernt werden. Die Standardeinstellung ist sieben Tage. Wenn Sie auf `0` setzen, wird die Projektion sofort ohne Übergangsphase entfernt.

- **[!UICONTROL Creation Grace Period (days)]** - Anzahl der Tage, die eine neu registrierte Katalogansicht warten kann, bis ihre erste Projektion [!DNL Adobe Commerce Optimizer], während sie als [!UICONTROL Pending] gemeldet wird. Wenn die Übergangsphase ohne Prognose abläuft, wird der Status zu [!UICONTROL Failed]. Die Standardeinstellung ist 1.

- **[!UICONTROL Enabled]** (Drift-Abstimmer) - Führt den geplanten Drift-Abstimmer aus, der [!DNL Adobe Commerce Optimizer] mit dem [!DNL Adobe Commerce] Projektionsstatus vergleicht und Abweichungen repariert oder meldet.

- **[!UICONTROL Automatically Repair Drift]** - Bei Festlegung auf **[!UICONTROL Yes]** konvergiert der geplante Durchlauf [!DNL Adobe Commerce Optimizer] zurück zu [!DNL Adobe Commerce], um eine reparierbare Drift zu erzielen. Bei Festlegung auf **[!UICONTROL No]** werden bei der geplanten Ausführung nur Abweichungen erkannt und protokolliert. Verwaiste Einträge werden immer gemeldet und nie automatisch entfernt. Diese Einstellung wirkt sich nur auf den geplanten Abstimmer aus. Die **[!UICONTROL Reconcile & Repair]** Aktion auf dieser Seite repariert Drift immer. Siehe [Überwachung oder Reparatur wählen](#choose-monitoring-or-repair).

Siehe [ACO Catalog View Sync Configuration](https://experienceleague.adobe.com/en/docs/commerce-admin/configuration-reference/services/aco-catalog-view-sync.md) im *[!DNL Commerce Admin]Guide* für Details zu den einzelnen Einstellungen.

## Überwachung oder Reparatur auswählen {#choose-monitoring-or-repair}

[!DNL Adobe Commerce] ist immer die richtige Quelle für die Katalogansicht, die Richtlinie, das Preisbuch und die wichtigsten Konfigurationen für B2B-freigegebene Kataloge. Wenn Sie oder ein anderer Administrator eine Richtlinie, ein Preisbuch oder eine Schlüsselkonfigurationseinstellung direkt in [!DNL Adobe Commerce Optimizer] Studio geändert haben, meldet die Abstimmung die Konfigurationsunterschiede als Abweichung.

- Wählen Sie **[!UICONTROL Reconcile]** aus, um auf Drift zu prüfen, ohne etwas zu ändern, damit Sie Unterschiede überprüfen können, bevor Sie handeln.
- Wählen Sie **[!UICONTROL Reconcile & Repair]** aus, um die erwartete Konfiguration für jede reparierbare Drift wiederherzustellen.

Um zu überprüfen, was sich geändert hat und warum, öffnen Sie die Detailseite einer Katalogansicht und überprüfen Sie ihren Drift-Verlauf.

## Verwaiste und gelöschte Einträge überprüfen {#review-orphaned-and-deleted-entries}

Die Registerkarten **[!UICONTROL Orphaned in ACO]** und **[!UICONTROL Deleted]** decken zwei Fälle ab, in denen der Connector nicht automatisch repariert werden kann, da es keinen [!DNL Adobe Commerce] freigegebenen Katalog gibt, mit dem abgeglichen werden kann:

- **[!UICONTROL Orphaned in ACO]** - Der Connector meldet verwaiste Entitäten im Synchronisierungsstatus und während der Drift-Abstimmung. Sie werden nicht übernommen oder automatisch gelöscht, selbst wenn die Abstimmung mit aktivierter Reparatur ausgeführt wird.

  Eine Entität wird verwaist, wenn sie in [!DNL Adobe Commerce Optimizer] vorhanden ist, der Connector sie jedoch nicht verfolgt oder mit einer verfolgten Katalogansicht verknüpft. Dies kann vorkommen, wenn eine Entität manuell, durch eine andere Integration oder nach einem unterbrochenen Connector-Vorgang erstellt wird.

  - **Katalogansichten** - Der Connector verfolgt die Ansicht nicht. Wählen Sie den Link Katalogansicht aus, um die Detailseite Katalogansicht in [!DNL Adobe Commerce Optimizer] Studio zu öffnen. Wenn die Katalogansicht nicht mehr benötigt wird, entfernen Sie sie.

  - **Schlüssel mit eingeschränktem Zugriff** - Keine Live-Katalogansicht verweist auf den Schlüssel. Wählen Sie den Link Katalogansicht aus, um die Detailseite Katalogansicht in [!DNL Adobe Commerce Optimizer] Studio zu öffnen. Überprüfen Sie den konfigurierten Zugriffsschlüssel und entfernen Sie ihn, wenn er nicht mehr benötigt wird.

  - **Richtlinien** - Der Connector verfolgt die Richtlinie nicht und keine Live-Katalogansicht verweist darauf. Wählen Sie den Richtlinien-Link aus, um ihn in [!DNL Adobe Commerce Optimizer] Studio zu öffnen.  Überprüfen Sie sie und entfernen Sie sie, wenn sie nicht mehr benötigt wird.

- **[!UICONTROL Deleted]** - Sie haben einen freigegebenen Katalog in [!DNL Adobe Commerce] gelöscht, und seine Katalogansichtsprojektion wurde anschließend entfernt. Diese Zeilen werden 90 Tage lang aufbewahrt, um aufzuzeichnen, was entfernt wurde.

>[!MORELIKETHIS]
>
> - [Überwachung des Synchronisierungsstatus der Katalogansicht](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/catalog-view-sync-status.md){target="_blank"} — Vollständige Dokumentationsreferenz zur Seite „Synchronisierungsstatus der Katalogansicht“ im *Commerce Admin Guide* —>
> - [Datensynchronisierung verwalten](data-sync-status.md) — Überprüfen der Synchronisierung von Produkt, Preis und Kategorie-Feeds
> - [Private Katalogansichten](/help/optimizer/setup/private-catalog-view.md) - Erfahren Sie, was eine von einem Connector verwaltete private Katalogansicht ist
> - [Eingeschränkte Zugriffsschlüssel](/help/optimizer/setup/restricted-access-keys.md) - Erfahren Sie, wie Connector-verwaltete Schlüssel funktionieren
> - [Änderungen am freigegebenen B2B-Katalog überwachen](get-started-b2b-shared-catalogs.md#monitor-b2b-shared-catalog-changes) - Erfahren Sie, was der Connector für freigegebene B2B-Kataloge automatisiert
