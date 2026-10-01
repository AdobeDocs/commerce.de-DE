---
source-git-commit: a3ade1a31d3c2905b601f71bda118de89c43cf59
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# [!DNL Commerce Optimizer]-Instanzdetails abrufen

Rufen Sie die _Mandanten_ ID) aus dem Feld _[!DNL Instance Id]_auf der [!DNL Commerce Optimizer]-Instanz [[!DNL Instance details] Seite](/help/optimizer/get-started.md#manage-instances) oder aus der URL ab, die für den Zugriff auf die Instanz verwendet wird. Zum Beispiel in `https://experience.adobe.com/#/@<your organization>/in:<tenant>/commerce-optimizer-studio/home`.

1. Wählen Sie in Commerce Admin die Option **[!UICONTROL Adobe Commerce Optimizer]** aus, um die Konfigurationsseite mit Anweisungen anzuzeigen.

   ![[!DNL Commerce Optimizer] Konfigurationsseite](/help/aco-connector/assets/aco-connector-admin-installation.png){width="500" zoomable="yes"}

1. Verwenden Sie in der Befehlszeile [SSH](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/secure-connections), um eine Verbindung zur [!DNL Adobe Commerce] Staging-Umgebung herzustellen.

1. Um die Integration zu konfigurieren, führen Sie den folgenden [!DNL Adobe Commerce] CLI-Befehl aus. Ersetzen Sie dabei die Platzhalterwerte durch die Werte für Ihr [!DNL Commerce Optimizer]:

   ```shell
   bin/magento aco:config:init --org_id=your-org --tenant_id=your-tenant --client_id=your-client-id --client_secret=your-secret
   ```

1. Überprüfen Sie die Verbindung, indem Sie zum Commerce-Administrator zurückkehren und die Option [!UICONTROL Adobe Commerce Optimizer] auswählen.

   Wenn Sie die Option auswählen, wird die [!DNL Commerce Optimizer]-Benutzeroberfläche auf einer neuen Registerkarte geöffnet.
