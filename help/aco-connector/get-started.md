---
title: Erste Schritte mit dem [!DNL Adobe Commerce Optimizer Connector]
description: Erfahren Sie, wie Sie die  [!DNL Adobe Commerce Optimizer Connector] installieren, die Einstellungen für den Bereichsexport konfigurieren, die IMS-Authentifizierung aktivieren und die Katalogsynchronisierung überprüfen.
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T16:55:50.934Z'
TQID: 'https://experienceleague.adobe.com/AcZ6CNyuIdUlfVHXhyQEYuThfLNd4WWqMMY82tjMMCc'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
subfeature_v2:
  - id: e126554b-28f9-4290-b58c-10b888b88174
  - id: a40ebd6b-b542-4432-a730-1803ef74518d
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 7a5ca0f5e76be50481447e6a17fc327562f7c3bf
workflow-type: tm+mt
source-wordcount: 1184
ht-degree: 0%

---


# Erste Schritte

Installieren und konfigurieren Sie die [!DNL Adobe Commerce Optimizer Connector], um Ihre [!DNL Adobe Commerce] mit [!DNL Adobe Commerce Optimizer] zu synchronisieren, und überwachen Sie dann den Datensynchronisierungsstatus, um sicherzustellen, dass Ihre Storefront auf dem neuesten Stand ist.

{{aco-integration-environment-alignment}}

## Voraussetzungen für die Verwendung der Integration {#requirements-to-use-the-integration}

* [!DNL Adobe Commerce] 2.4.7+

   * PHP 8.2, 8.3 oder 8.4
   * Composer 2.x

* [!DNL Adobe Commerce Optimizer] Lizenz mit einer bereitgestellten Sandbox-Instanz.

* [Authentifizierungsschlüssel](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) zum Herunterladen des Connector-Metapakets mit Composer.

* Administratorzugriff auf eine [[!DNL Adobe Commerce Optimizer] Sandbox-Instanz](../optimizer/get-started.md).

Der [!DNL Adobe Commerce] Benutzer, der die Integration konfiguriert, muss über Folgendes verfügen:

* Administratorzugriff auf den Commerce Admin.

* [Befehlszeilenzugriff auf den  [!DNL Adobe Commerce] -Server](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/project/user-access).

* Entwicklerzugriff auf die [IMS-Organisation](https://experienceleague.adobe.com/de/docs/core-services/interface/administration/organizations?), in der das [!DNL Adobe Commerce Optimizer] bereitgestellt wird.

>[!BEGINSHADEBOX]

## Voraussetzungen

Wenn Sie eine der folgenden Erweiterungen installiert haben, deinstallieren Sie diese, bevor Sie die [!DNL Adobe Commerce Optimizer Connector] installieren:

* [!DNL Adobe Commerce Live Search] (`magento/live-search`)
* [!DNL Adobe Commerce Product Recommendations] (`magento/product-recommendations`)
* [!DNL Adobe Commerce Catalog Service] (`magento/catalog-service`, `magento/catalog-service-installer`)
* Data Management Dashboard (`magento-catalog-sync-admin`)

Daten, die mit diesen Erweiterungen verknüpft sind, sind weiterhin in der Commerce-Datenbank verfügbar. Er wird jedoch nicht nach [!DNL Adobe Commerce Optimizer] exportiert, wenn der Connector aktiviert ist. Um die Such- und Merchandising-Funktionen zu implementieren, die diese Erweiterungen nach der Aktivierung des Connectors bieten, konfigurieren Sie sie über die [[!DNL Adobe Commerce Optimizer] Admin-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/commerce/optimizer/overview#quick-tour).

>[!IMPORTANT]
>
>Wenn diese Erweiterungen vor dem Aktivieren des Connectors nicht entfernt werden, werden möglicherweise fehlerhafte Konfigurationsbildschirme, doppelte Daten in [!DNL Adobe Commerce Optimizer] angezeigt, da dieselben Daten sowohl aus dem Connector als auch aus den vorhandenen Erweiterungen exportiert werden, und 401- oder 403-Fehler in den Protokollen aufgrund von Konflikten bei der Authentifizierung der Erweiterungen und des Connectors bei den verbundenen Services.

>[!ENDSHADEBOX]

## Konfigurationsschritte

Führen Sie die folgenden Schritte aus, um die [!DNL Commerce Optimizer Connector] zu aktivieren und mit der Synchronisierung von Daten aus [!DNL Adobe Commerce] mit Ihrer [!DNL Commerce Optimizer]-Instanz zu beginnen.

1. **[Installieren Sie das  [!DNL Commerce Optimizer Connector] -Paket](#install-the-adobe-commerce-optimizer-connector-package)** mithilfe von Composer, um Ihre [!DNL Adobe Commerce]-Instanz mit [!DNL Adobe Commerce Optimizer] zu verbinden.

1. **[Anpassen der Datenexportkonfiguration](#customize-the-commerce-scopes-export-configuration)** vom Administrator.

1. **[Aktivieren Sie die  [!DNL Adobe Commerce Optimizer] -Integration](#enable-the-adobe-commerce-optimizer-integration)**.

1. **[Überprüfen Sie, ob die Datensynchronisation funktioniert](#verify-that-the-data-sync-is-working)**.

## Installieren des [!DNL Commerce Optimizer Connector] {#install-the-adobe-commerce-optimizer-connector-package}

Das [!DNL Commerce Optimizer Connector] wird als Composer-Metapaket bereitgestellt, das für alle Commerce-Händler mit einer aktiven Lizenz für [!DNL Adobe Commerce Optimizer] verfügbar ist.

### Installationsschritte

1. Fügen Sie das Modul `adobe-commerce/commerce-data-export-aco-adapter` mit dem Composer hinzu:

   ```shell
   composer require adobe-commerce/commerce-data-export-aco-adapter
   ```

1. Stellen Sie die Änderungen in Ihrer [!DNL Adobe Commerce] Staging-Umgebung bereit.

   Nach Abschluss der Bereitstellung ist die Option [!DNL Commerce Optimizer] im Commerce Admin-Menü verfügbar. Wählen Sie **[!UICONTROL Commerce Optimizer]** aus, um Ihre [!DNL Adobe Commerce Optimizer]-Instanz direkt über die Commerce-Admin zu öffnen.

>[!NOTE]
>
>Detaillierte Installationsanweisungen für Erweiterungen finden Sie in den folgenden Handbüchern:
>
>[Installieren der Erweiterung in  [!DNL Adobe Commerce]  Cloud-Infrastruktur](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure-store/extensions)
>
>[Installieren einer Erweiterung  [!DNL Adobe Commerce]  On-Premise](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/extensions)

## Anpassen der Exportkonfiguration für Commerce-Bereiche {#customize-the-commerce-scopes-export-configuration}

Standardmäßig ist die Synchronisierung von Katalogdaten für alle Commerce-Bereiche (Websites, Kundengruppen und Store-Ansichten) aktiviert. Sie können die Exporteinstellungen so anpassen, dass Daten nur für bestimmte Bereiche entsprechend Ihren Geschäftsanforderungen synchronisiert werden. Wenn Sie beispielsweise über mehrere Store-Ansichten verfügen, die dieselbe Sprache verwenden, können Sie Daten für nur eine der Store-Ansichten exportieren und als [Katalogquelle](../optimizer/setup/catalog-source.md) für mehrere Catalog-Ansichten in [!DNL Adobe Commerce Optimizer] verwenden.

>[!IMPORTANT]
>
>Durch Ändern der Exporteinstellungen wird eine vollständige Neuindizierung Trigger, die je nach Kataloggröße längere Zeit in Anspruch nehmen kann. Adobe empfiehlt, die Commerce-Bereiche so zu konfigurieren, dass sie mit [!DNL Adobe Commerce Optimizer] synchronisiert werden, bevor die Integration aktiviert und die anfängliche Datensynchronisierung gestartet wird.

In der folgenden Tabelle wird beschrieben, welche Daten auf jeder Bereichsebene exportiert werden:

| Umfang | Daten exportiert | Notizen |
| ----- | ------------- | ----- |
| Website und Kundengruppe | Preise und Preisbücher | Jede Preisgruppe wird als „Preisbuch[&#x200B; exportiert, wobei &#x200B;](../optimizer/setup/pricebooks.md) Namenskonvention `<website>::<SHA1 of customer group ID>` verwendet wird. Alle Kundengruppen für die Website sind enthalten. |
| Shop-Ansicht | Produkte und Produktattribute | Jede Shop-Ansicht erstellt eine separate [Katalogquelle](../optimizer/setup/catalog-source.md) in [!DNL Adobe Commerce Optimizer]. |

![Raster mit Commerce Optimizer-Synchronisierungseinstellungen speichern](./assets/aco-connector-storeviews-list.png){width="600" zoomable="yes"}

**So ändern Sie die Einstellungen für eine Website- oder Store-Ansicht:**

1. Navigieren Sie im Commerce Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**.

1. Wählen Sie die Website- oder Store-Ansicht aus, die Sie konfigurieren möchten.

1. Aktivieren Sie in den **[!DNL Adobe Commerce Optimizer]-** das Kontrollkästchen, um die Datensynchronisierung nach Bedarf zu aktivieren oder zu deaktivieren.

   ![Aktualisieren der Datensynchronisierungskonfiguration](./assets/aco-connector-storeview-export-settings.png){width="500" zoomable="yes"}

1. Speichern Sie Ihre Änderungen.

### Aktivieren und Deaktivieren des Verhaltens

| Aktion | Ergebnis |
| -------- | -------- |
| Shop-Ansicht deaktivieren | Die Katalogquelle bleibt in [!DNL Adobe Commerce Optimizer], aber alle Daten werden entfernt. |
| Deaktivieren und reaktivieren Sie eine Store-Ansicht | Dieselbe Katalogquelle wird erneut mit einer vollständigen Datensynchronisation aufgefüllt. |

## [!DNL Adobe Commerce Optimizer] aktivieren

Sie aktivieren die Integration und initiieren die Datensynchronisation, indem Sie den `aco:config:init` CLI-Befehl ausführen. Dieser Befehl führt die folgenden Schritte aus:

1. Ruft ein IMS-Zugriffstoken mit den als Befehlszeilenargumente bereitgestellten Anmeldeinformationen ab.
1. Ruft den Commerce Cloud Manager-Service (CCM) unter `https://ccm.api.commerce.adobe.com/api/v1/tenants/{tenantId}/owner/{orgId}` auf, um den Mandanten zu validieren und die Aufnahme-URL und die [!DNL Adobe Commerce Optimizer] Studio-URL zu extrahieren.
1. Speichert alle Konfigurationen (Client-Geheimnis verschlüsselt) in `core_config_data`.
1. Plant die anfängliche vollständige Synchronisierung durch Invalidierung aller [!DNL Commerce Optimizer]-Indexer.

>[!IMPORTANT]
>
>Die Datensynchronisierungsverarbeitung beginnt im Hintergrund, sobald die Konfiguration abgeschlossen ist. Je nach Größe Ihres Katalogs kann der Datensynchronisierungsprozess einige Minuten bis mehrere Stunden dauern.

### Erforderliche Verbindungsdetails abrufen

Erstellen Sie in der [Adobe Developer Console](https://developer.adobe.com/console) ein neues Projekt, das für den [!DNL Adobe Commerce Optimizer]-Aufnahme-Service aktiviert ist, und generieren Sie OAuth-Server-zu-Server-Anmeldeinformationen. Detaillierte Anweisungen finden Sie unter [Abrufen von IMS](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/authentication/#obtain-ims-credentials) im *Merchandising-Entwicklerhandbuch*.

Speichern Sie die folgenden Werte auf der Seite mit den Anmeldedaten:

* **Organisations-ID** (`org_id`)
* **Client-ID** (`client_id`)
* **Client-Geheimnis** (`client_secret`)

![Abrufen von Anmeldeinformationen von der Adobe Developer Console-Projektseite](./assets/developer-console-project-credentials.png){width="500" zoomable="yes"}

### [!DNL Adobe Commerce Optimizer]-Instanzdetails abrufen

Rufen Sie die _Mandanten_ ID) aus dem Feld _[!DNL Instance Id]_&#x200B;auf der [!DNL Adobe Commerce Optimizer]-Instanz [[!DNL Instance details] Seite](../optimizer/get-started.md#manage-instances) oder aus der URL ab, die für den Zugriff auf die Instanz verwendet wird. Zum Beispiel in `https://experience.adobe.com/#/@<your organization>/in:<tenant ID>/commerce-optimizer-studio/home`.

1. Wählen Sie in Commerce Admin die Option **[!UICONTROL Adobe Commerce Optimizer]** aus, um die Konfigurationsseite mit Anweisungen anzuzeigen.

   ![[!DNL Adobe Commerce Optimizer] Konfigurationsseite](./assets/aco-connector-admin-installation.png){width="500" zoomable="yes"}

1. Verwenden Sie in der Befehlszeile [SSH](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/secure-connections), um eine Verbindung zur [!DNL Adobe Commerce] Staging-Umgebung herzustellen.

1. Führen Sie den folgenden [!DNL Adobe Commerce] CLI-Befehl aus, um die Integration zu konfigurieren. Ersetzen Sie dabei die Platzhalterwerte durch die Werte für Ihr [!DNL Commerce Optimizer]:

   ```terminal
   bin/magento aco:config:init --org_id=your-org --tenant_id=your-tenant --client_id=your-client-id --client_secret=your-secret
   ```

1. Überprüfen Sie die Verbindung, indem Sie zum Commerce-Administrator zurückkehren und die Option [!UICONTROL Adobe Commerce Optimizer] auswählen.

   Wenn Sie die Option auswählen, wird die [!DNL Adobe Commerce Optimizer]-Benutzeroberfläche auf einer neuen Registerkarte geöffnet.

## Überprüfen, ob die Datensynchronisation funktioniert

Sie können über die Seite [[!UICONTROL Data Feed Sync Status]](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status) in Admin überwachen und überprüfen, ob die Synchronisierung funktioniert.

1. **Überprüfen Sie den Synchronisierungsstatus im Commerce Admin-**:

   Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Data Feed Sync Status]**.

   ![Seite „Daten-Feed-Synchronisierungsstatus“ mit Reporting zum Feed-Elementstatus](./assets/data-feed-sync-status.png){width="500" zoomable="yes"}

   Wenn die Synchronisierung ausgeführt wird, zeigen die Feed-Daten erfolgreich gesendete Datensätze an. Feed auswählen, um Details anzuzeigen oder Synchronisierungsprobleme zu beheben.

1. **Bestätigen Sie, dass Daten in [!DNL Commerce Optimizer]:** eingegangen sind.

   Wählen Sie im [!DNL Adobe Commerce Optimizer] Menü **[!UICONTROL Data Sync]** aus.

   ![Datensynchronisierungsseite in Adobe Commerce Optimizer mit synchronisierten Katalogdaten](./assets/data-sync.png){width="500" zoomable="yes"}

   Überprüfen Sie, ob die erwarteten Produkte, Preise und Attribute angezeigt werden.

>[!TIP]
>
>Wenn Sie Probleme mit der Datensynchronisation haben, lesen Sie das Handbuch [Fehlerbehebung](troubleshooting.md).

## Nächste Schritte

1. **Konfigurieren [!DNL Adobe Commerce Optimizer] Katalogansichten und Richtlinien**

   Erstellen Sie Katalogansichten und Richtlinien in der [!DNL Adobe Commerce Optimizer]-Benutzeroberfläche. Beachten Sie, dass Preislisten automatisch aus [!DNL Adobe Commerce] Kundengruppen erstellt werden. Anweisungen finden Sie in der [Katalogansichten](../optimizer/setup/catalog-view.md) und [Richtlinien](../optimizer/setup/policies.md) im *[!DNL Adobe Commerce Optimizer]-Benutzerhandbuch*.

1. **Einrichten einer Commerce-Storefront auf[!DNL Edge Delivery Services]**

   Befolgen Sie die [Dokumentation zur Einrichtung von Storefronts](https://experienceleague.adobe.com/developer/commerce/storefront/setup/?lang=de){target="_blank"}, um Ihre Storefront mit der [!DNL Adobe Commerce Optimizer]-Instanz zu verbinden und mit der Bereitstellung personalisierter Commerce-Erlebnisse zu beginnen.
