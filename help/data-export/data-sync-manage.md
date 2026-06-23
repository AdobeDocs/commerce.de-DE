---
title: Synchronisierungsprozess anzeigen und verwalten
description: Erfahren Sie, wie Sie den  [!DNL SaaS Data Export]  mithilfe des Daten-Management-Dashboards und der Seite „Status der Daten-Feed-Synchronisierung“ anzeigen und verwalten können.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: e7d9c056ef8d565b4a143b05ff4e06d607fbfa8e
workflow-type: tm+mt
source-wordcount: 544
ht-degree: 0%

---

# Synchronisierungsprozess anzeigen und verwalten

Die meisten Synchronisierungsaktivitäten werden automatisch mit vollständiger Synchronisierung, teilweiser Synchronisierung oder Wiederholung fehlgeschlagener Elementsynchronisierung verarbeitet. Siehe [Synchronisierungstypen](sync-overview.md#synchronization-types) für Details zum Zeitpunkt der Ausführung der einzelnen Typen. [!DNL SaaS Data Export] bietet außerdem Tools zur Überwachung, Verwaltung und Fehlerbehebung bei diesem Prozess. Sie können den Synchronisierungsstatus anzeigen und den Datensynchronisierungsprozess mithilfe der Dashboards für Ihre Bereitstellung verwalten.

>[!BEGINTABS]

>[!TAB Adobe Commerce]

Bei Adobe Commerce-On-Cloud-, On-Premise- oder Adobe Commerce as a Cloud Service-Bereitstellungen können Sie den Synchronisierungsprozess über diese Commerce-Admin-Ressourcen anzeigen und verwalten:

- **[Seite „Daten-Feed-Synchronisierungsstatus](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status)** - Überprüfen Sie den Feed-Exportstatus für Bereitstellungen, die mit [!DNL Live Search], [!DNL Product Recommendations] oder [!DNL Catalog Service] verbunden sind. Dieses Dashboard zeigt den Status des Feed-Exports für jeden Feed einschließlich aller aufgetretenen Fehler an. In einer Detailansicht wird der Status des Feed-Exports für einzelne Feed-Elemente angezeigt.

- **[Daten-Management-Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard)** - Admin-Benutzer können Daten anzeigen und verfolgen, die erfolgreich exportiert und mit verbundenen Commerce Services synchronisiert wurden. In diesem Dashboard werden die mit Commerce Services synchronisierten Produktdaten angezeigt.

>[!NOTE]
>
>Das Daten-Management-Dashboard und die Seite Status der Daten-Feed-Synchronisierung sind nur verfügbar, wenn [!DNL Live Search], [!DNL Product Recommendations] oder [!DNL Catalog Service] installiert sind.

>[!TAB Adobe Commerce mit Commerce Optimizer]

Bei Commerce-On-Cloud- oder -On-Premise-Bereitstellungen, die in [!DNL Commerce Optimizer] integriert sind, können Sie den Synchronisierungsprozess mithilfe der folgenden Ressourcen anzeigen und verwalten:

- **[Seite „Synchronisierungsstatus für Daten-Feeds](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status)** - Überwachen Sie den Exportstatus des Connector-Feeds über die Commerce-Admin. Auf dieser Seite wird angezeigt, ob Katalogdaten erfolgreich aus [!DNL Adobe Commerce] exportiert wurden, einschließlich Fehlerdetails pro Feed und pro Element.

- **[Datensynchronisierungsseite](../optimizer/setup/data-sync.md)** - Die Datensynchronisierungsseite bietet einen Überblick über den Synchronisierungsstatus für Produktdaten, die von Ihrer Upstream-Katalogquelle in [!DNL Commerce Optimizer] stammen.

Weitere Informationen dazu, wie Sie diese Dashboards verwenden, um zu überprüfen, ob die Datensynchronisierung funktioniert, und um Daten manuell neu zu synchronisieren, finden Sie unter [Synchronisierung verwalten](../aco-connector/data-sync-manage.md) im _Adobe Commerce Optimizer Connector-Handbuch_.

>[!ENDTABS]

## Überprüfen, ob die Datensynchronisation funktioniert {#verify-that-the-data-sync-is-working}


{{$include /help/_includes/data-export/verify-commerce-service-data-sync.md}}

## Daten manuell neu synchronisieren

Wenn Synchronisierungsprobleme durch teilweise Synchronisierung und automatische erneute Versuche nicht behoben werden, können Sie die Synchronisierung von Daten manuell über den Commerce Admin oder mithilfe von Commerce-CLI-Befehlen neu synchronisieren. Die verfügbaren Optionen hängen von Ihrer Bereitstellung ab.

### Verfügbare manuelle Resynchronisierungsoptionen {#manual-resync-options-commerce}

Verwenden Sie die folgenden Optionen, um Feed-Daten manuell neu zu synchronisieren.

| Aufgabe | Option | Notizen |
| --- | --- | --- |
| Ausgewählte fehlgeschlagene oder problematische Feed-Elemente neu synchronisieren | **[!UICONTROL Data Feed Sync Status]Seite** | Überwachen und re-synchronisieren Sie ausgewählte Feed-Elemente über den Commerce Admin. Siehe [Überprüfen, ob die Datensynchronisation funktioniert](#verify-that-the-data-sync-is-working). |
| Vollständige Neusynchronisierung aller Feeds | **[!UICONTROL Data Management Dashboard]** | Führen Sie eine vollständige Neusynchronisierung aller Feeds von Commerce Admin durch. Adobe empfiehlt dies vor allem, wenn Sie zum ersten Mal eine Verbindung zu einem Commerce-Service herstellen. Siehe [Überprüfen, ob die Datensynchronisation funktioniert](#verify-that-the-data-sync-is-working). |
| Gezielte Re-Synchronisation des Feeds mit Betriebssteuerung | **Commerce-CLI** | Verwenden Sie den Befehl `saas:resync` für die Resynchronisation zielgerichteter Feeds. Siehe [Synchronisieren von Feeds mit der Commerce-CLI](data-export-cli-commands.md). |

>[!MORELIKETHIS]
>
> - [Funktionsweise der Synchronisierung](sync-overview.md) - Erfahren Sie mehr über Synchronisierungsmodi, vollständige Synchronisierung, partielle Synchronisierung und Wiederholen fehlgeschlagener Elemente.
> - [Feeds über die Commerce-CLI synchronisieren](data-export-cli-commands.md) - Verwenden Sie den Befehl `saas:resync` für die Resynchronisierung gezielter Feeds.
> - [Überprüfen von Protokollen und Fehlerbehebung](troubleshooting/logging.md) - Diagnostizieren von Datenexport- und SaaS-Exportfehlern.
> - [Synchronisierung mit verwalten [!DNL Commerce Optimizer]](../aco-connector/data-sync-manage.md) - Überprüfen Sie die Synchronisierung von Katalogdaten und synchronisieren Sie Connector-Feeds manuell neu.
