---
title: Synchronisierungsstatus für AEM Assets anzeigen
description: Überprüfen synchronisierter Assets in einer Asset-orientierten Liste in Commerce Admin.
feature: CMS, Media, Integration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%
---

# Synchronisierungsstatus für AEM Assets anzeigen

Die **[!UICONTROL Sync Status]** bietet eine Asset-orientierte Liste von Assets, die über die AEM Assets-Integration synchronisiert wurden. Verwenden Sie sie, um Assets anhand ihrer eigenen Attribute zu finden, zu überprüfen und zu beheben, anstatt Produkt für Produkt im Katalog zu navigieren.

![AEM Assets-Synchronisierungsstatusansicht](../assets/aem-assets-sync-status-view.png){width="700" zoomable="yes"}

>[!NOTE]
>
> [!UICONTROL Sync Status] ist nicht für [!DNL Adobe Commerce Optimizer] verfügbar.

## Synchronisierungsstatus öffnen

Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL System]** > **[!UICONTROL AEM Assets]** > **[!UICONTROL Sync Status]**.

![AEM Assets-Synchronisationsstatus im Systemmenü](../assets/aem-assets-configuration-admin-menu.png){width="600" zoomable="yes"}

## Zustand der Integrationssynchronisierung

Oben auf der Seite fasst das Banner **AEM-Synchronisierungsstatus** den Pipeline-Status zusammen und gibt an, wie viele Ereignisse verarbeitet werden sollen. Wählen Sie **[!UICONTROL Refresh]** aus, um das Synchronisierungskonsistenzbanner zu aktualisieren.

## Asset-Liste

Das Raster listet Assets auf, die von der AEM Assets-Synchronisierungs-Pipeline verarbeitet wurden, sowie ihren aktuellen Synchronisierungsstatus. Jede Zeile stellt ein Asset und dessen Synchronisierungsstatus in Commerce dar. Es stellt keinen Produktdatensatz dar.

| Spalte | Beschreibung |
|--------|-------------|
| **Asset-ID** | AEM-Asset-Kennung (z. B. `urn:aaid:aem:…`). |
| **Status** | Ergebnis des letzten Synchronisierungsversuchs für das Asset. Mögliche Werte sind **Erfolg**, **Fehlgeschlagen** oder **Warten**. |
| **Verarbeitung** | Beginn der Datums- und Uhrzeitverarbeitung für das Asset. |
| **Dispatched** | Datum und Uhrzeit, zu der das Synchronisierungsereignis gesendet wurde. |
| **Fehler** | Fehlermeldung, wenn **Status** einen Fehler anzeigt; leer, wenn die Synchronisierung erfolgreich war. |

### Filtern von Assets

1. Wählen Sie **[!UICONTROL Filters]** aus, um das Filterbedienfeld zu erweitern.

1. Geben Sie eine **Asset-ID** ein oder wählen Sie einen **Status**-Wert.

1. Wählen Sie **[!UICONTROL Apply Filters]** aus, um das Raster zu aktualisieren, oder **[!UICONTROL Cancel]**, um das Bedienfeld zu schließen, ohne Änderungen vorzunehmen.

Filter werden auf Daten auf Asset-Ebene angewendet, sodass Sie fehlgeschlagene Synchronisationen isolieren oder ein bestimmtes Asset verfolgen können, ohne einzelne Produkte öffnen zu müssen.

## Fehlgeschlagene Synchronisationen

Wenn **Status** einen Fehler anzeigt, überprüfen Sie die Spalte **Fehler** im Raster auf die von der Synchronisierungs-Pipeline zurückgegebene Nachricht.

Überprüfen Sie die vollständige Fehlermeldung und die Details zum letzten Synchronisierungsversuch, um den Fehler zu diagnostizieren.

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} Weitere Informationen zur Fehlerbehebung finden Sie unter [Standardmäßiger automatischer Abgleich](../synchronize/default-match.md). Integrationsprotokolldateien sind unter `/var/log/aem-assets-integration.log` und `/var/log/aem-assets-integration-errors.log` in Ihrer Commerce-Instanz verfügbar.
