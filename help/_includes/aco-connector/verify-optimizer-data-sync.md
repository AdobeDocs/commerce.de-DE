---
source-git-commit: 3d05a7307e58ea2758ac4b6f2b70d24b8ea7a5ac
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# Überprüfen der Datensynchronisation mit Optimizer

Vergewissern Sie sich, dass die Daten erfolgreich von Commerce Admin exportiert und erfolgreich an [!DNL Commerce Optimizer] übermittelt wurden. Beginnen Sie im Commerce-Admin mit dem Export und bestätigen Sie dann den Versand in [!DNL Commerce Optimizer].

1. **Überprüfen Sie den Synchronisierungsstatus im Commerce Admin-**:

   Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Data Feed Sync Status]**.

   ![Seite „Daten-Feed-Synchronisierungsstatus“ mit Reporting zum Feed-Elementstatus](/help/aco-connector/assets/data-feed-sync-status.png){width="700" zoomable="yes"}

   Wenn die Synchronisierung ausgeführt wird, zeigen die Feed-Daten erfolgreich gesendete Datensätze an. Feed auswählen, um Details anzuzeigen oder Synchronisierungsprobleme zu beheben.

1. **Bestätigen Sie, dass Daten an [!DNL Commerce Optimizer] gesendet wurden:**

   Wählen Sie im [!DNL Commerce Optimizer] Menü **[!UICONTROL Data Sync]** aus.

   ![Datensynchronisierungsseite in Adobe Commerce Optimizer mit synchronisierten Katalogdaten](/help/aco-connector/assets/data-sync.png){width="700" zoomable="yes"}

   Überprüfen Sie, ob die erwarteten Produkte, Preise und Attribute angezeigt werden.

Wenn die Synchronisierung erwartungsgemäß funktioniert:

- **[!UICONTROL Data Feed Sync Status]** zeigt erfolgreich gesendete Datensätze für Connector-Feeds ohne nicht behobene Fehler auf Elementebene an.
- **[!UICONTROL Data Sync]** in [!DNL Commerce Optimizer] listet die erwarteten Katalogquellen, Produkte, Preise und Attribute auf.

>[!TIP]
>
>Wenn Sie Probleme mit der Datensynchronisation haben, lesen Sie das Handbuch [Fehlerbehebung](/help/aco-connector/troubleshooting.md).
