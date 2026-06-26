---
source-git-commit: e7d9c056ef8d565b4a143b05ff4e06d607fbfa8e
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---
# Überprüfen der Datensynchronisierung des Commerce-Services

Um sicherzustellen, dass die Datensynchronisierung funktioniert, überprüfen Sie, ob die Daten erfolgreich aus [!DNL Adobe Commerce] exportiert und erfolgreich an den verbundenen Commerce-Service übermittelt wurden. Verwenden Sie die Dashboards für Ihre Bereitstellung, um beide Schritte zu überprüfen.

Mit Export beginnen und dann Versand bestätigen.

1. Überprüfen Sie den Synchronisierungsstatus in der Commerce Admin Console.

   Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Data Feed Sync Status]**.

   ![Seite „Daten-Feed-Synchronisierungsstatus“ mit Reporting zum Feed-Elementstatus](/help/data-export/assets/data-feed-sync-status.png){width="800" zoomable="yes"}

   Wenn die Synchronisierung ausgeführt wird, zeigen die Feed-Daten erfolgreich gesendete Datensätze an. Feed auswählen, um Details anzuzeigen oder Synchronisierungsprobleme zu beheben.

1. Vergewissern Sie sich, dass die Daten an verbundene Commerce Services gesendet wurden.

   Navigieren Sie vom Commerce-Administrator aus zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Data Management Dashboard]**.

   ![Daten-Management-Dashboard mit synchronisierten Katalogdaten in Connected Commerce Services](/help/data-export/assets/data-management-dashboard.png){width="700" zoomable="yes"}

   Überprüfen Sie, ob die erwarteten Produkte, Preise und Attribute angezeigt werden.

>[!TIP]
>
>Wenn Sie zusätzliche Probleme mit der Datensynchronisation haben, lesen Sie [Überprüfen Sie die Protokolle und beheben Sie Fehler](/help/data-export/troubleshooting/logging.md).

