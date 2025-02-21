---
title: Konfiguration des Speicherorts und des Zuordnungssystems
description: Konfigurieren Sie einen Entfernungsanbieter, um die Speicherortzuordnung in der Storefront-Benutzeroberfläche zu unterstützen. Die Store-Fulfillment-Lösungen erfordern einen Fernanbieter, um die Suche im Einzelhandel und andere Zuordnungs- und Planungsfunktionen für den End-to-End-Fulfillment-Workflow zu ermöglichen.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Store-Standort und Zuordnungseinrichtung

Aktivieren Sie den Store-Standort und die Zuordnungsfunktionen für Store Fulfillment, indem Sie einen [Distanzanbieter](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/distance-priority-algorithm) konfigurieren, um nach Einzelhandelsspeicherorten zu suchen.

**Anforderungen**

Während des Konfigurationsprozesses geben Sie einen Google-API-Schlüssel für die Google Maps-Plattform an. Wenn Sie noch keinen haben, [ Sie einen über die Google Maps-Plattform ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/distance-priority-algorithm#configure-google-maps).

So konfigurieren Sie den Entfernungsanbieter:

1. Fügen Sie in der **[!UICONTROL Stores > General]** in der Admin Console die Google Maps-Integration für den Inhaltstyp „Zuordnung“ hinzu.

   - Gehe zu **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Fügen Sie Ihren Google-API-Schlüssel zu **[!UICONTROL Google Maps API Key]** Feld hinzu.

1. Wählen Sie in der **[!UICONTROL Stores > Inventory]** im Admin-Bereich den Entfernungsanbieter für Store Fulfillment aus.

   - Gehe zu **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Erweitern Sie den Abschnitt **[!UICONTROL Distance Provider for Distance Based SSA]** .

   - Legen Sie den **Provider** auf **Google Map** fest.

1. Konfigurieren Sie die Einstellungen für die **[!UICONTROL Google Distance Provider]**.

   - Fügen Sie Ihren **Google-API-Schlüssel hinzu**.

   - **[!UICONTROL Computation Mode]** auf `Driving` und **[!UICONTROL Value]** auf `Distance` setzen
