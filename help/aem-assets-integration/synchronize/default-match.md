---
title: Standardmäßige automatische Zuordnung
description: Erfahren Sie, wie die standardmäßige Regel für den automatischen Abgleich eine nahtlose Synchronisierung zwischen Adobe Commerce und der AEM Assets-Integration ermöglicht, um sicherzustellen, dass Assets automatisch mit den richtigen Merchandising-Entitäten verknüpft werden.
feature: CMS, Media, Integration
exl-id: 8a18639b-f508-456e-8d22-18e3e0fdd515
source-git-commit: 6640635fca5c53fe4b06b9bbb3120fffc46cb0b8
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Standardmäßige automatische Zuordnung

Die AEM Assets-Integration für Commerce bietet einen standardmäßigen automatischen Abgleichmechanismus (**[!UICONTROL Match by product SKU]**), der auf der **AEM Assets**-Metadatenkonfiguration basiert. Diese Regel ermöglicht eine nahtlose Synchronisierung zwischen **Adobe Commerce** und **AEM Assets**, um sicherzustellen, dass Assets automatisch mit den richtigen Merchandising-Entitäten verknüpft werden.

## Konfigurieren des automatischen Abgleichmechanismus

1. Navigieren Sie vom Commerce-Administrator aus zu **[!UICONTROL Store]** > Konfiguration > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

1. Geben Sie **[!UICONTROL Match by SKU]** als Übereinstimmungsregel an.

   ![Standardregel für automatisierten Abgleich](../assets/ootb-matching-rule.png){width="600" zoomable="yes"}

1. Geben Sie den Metadatenfeldnamen ein, der zur Asset-Identifizierung in der AEM Assets verwendet wird.

   >[!NOTE]
   >
   > Wenn der standardmäßige Onboarding-Prozess befolgt wurde, sollte dieser Wert auf `commerce:skus` gesetzt werden.

## Funktionsweise des automatischen Abgleichmechanismus

Wenn die Regel zum Abgleichen von **[!UICONTROL Match by product SKU]** in der Commerce Admin konfiguriert ist, werden Commerce-Asset-Dateien automatisch von AEM Assets mit Ihrem Commerce-Projekt synchronisiert, basierend auf den Asset-Metadaten, die für jede Datei konfiguriert wurden. Sie konfigurieren die Metadaten auf der Registerkarte &quot;AEM **Commerce** in der **AEM Assets Author**-Umgebung:

![Beispiel-Metadaten](../assets/example-metadata.png){width="600" zoomable="yes"}

1. Aktualisieren Sie in AEM Assets die Bildmetadaten, um `Commerce=yes` die Adobe Commerce-Verknüpfung hinzuzufügen.

1. Konfigurieren Sie die Metadaten ([!UICONTROL SKU], [!UICONTROL position] und [!UICONTROL role]), die das Asset mit der zugehörigen Produkt-SKU verknüpfen.

   >[!NOTE]
   >
   > Wenn ein Asset für mehrere Produkte verwendet wird, konfigurieren Sie die Metadaten für jede zugehörige SKU.

Dadurch wird sichergestellt, dass digitale Assets ordnungsgemäß verknüpft und in Adobe Commerce angezeigt werden. Außerdem können Merchandiser und Marketing-Experten Rollen und die Asset-Positionierung direkt in AEM Assets verwalten, wodurch ein konsistenter und zentralisierter Mechanismus für die Bildauswahl und -reihenfolge über alle Interaktionskanäle hinweg bereitgestellt wird.
