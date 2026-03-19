---
title: Erste Schritte mit dem Adobe Commerce Optimizer-Connector
description: Erfahren Sie, wie Sie den Connector installieren und konfigurieren, die Exportkonfiguration anpassen, eine Verbindung zu Adobe Commerce Optimizer herstellen und den Datensynchronisierungsstatus überwachen.
feature: Personalization, Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: f302efcb6c08d5a3c695a47ae16fdac790a8bc24
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 0%

---


# Erste Schritte

Installieren und konfigurieren Sie den Commerce Optimizer-Connector, um Ihre Adobe Commerce-Katalogdaten mit [!DNL Adobe Commerce Optimizer] zu synchronisieren, und überwachen Sie dann den Datensynchronisierungsstatus, um sicherzustellen, dass Ihre Storefront auf dem neuesten Stand ist.

## Voraussetzungen für die Verwendung der Integration

* Adobe Commerce 2.4.7+

   * PHP 8.2, 8.3 oder 8.4
   * Composer 2.x

* [!DNL Adobe Commerce Optimizer] Lizenz mit einer bereitgestellten Sandbox-Instanz.

* Zugriff auf [repo.magento.com](https://repo.magento.com), um das Commerce Connector-Metapaket mit Composer herunterzuladen.

* Administratorzugriff auf eine [Adobe Commerce Optimizer Sandbox-Instanz](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-commerce-optimizer/create-first-instance).

Der Adobe Commerce-Benutzer, der die Integration konfiguriert, muss über Folgendes verfügen:

* Administratorzugriff auf den Adobe Commerce Admin.

* [Befehlszeilenzugriff auf den Adobe Commerce-Anwendungsserver](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access).

* Entwicklerzugriff auf die [IMS-Organisation](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations?), in der das [!DNL Adobe Commerce Optimizer] bereitgestellt wird.

>[!BEGINSHADEBOX]

## Voraussetzungen

Wenn Sie eine der folgenden Erweiterungen installiert haben, deinstallieren Sie diese, bevor Sie den Commerce Optimizer-Connector installieren:

* Adobe Commerce Live Search (`magento/live-search`)
* Adobe Commerce Product Recommendations (`magento/product-recommendations`)
* Adobe Commerce Catalog Service (`magento/catalog-service`, `magento/catalog-service-installer`)
* Data Management Dashboard (`magento-catalog-sync-admin`)

Daten, die mit diesen Erweiterungen verknüpft sind, sind weiterhin in der Commerce-Datenbank verfügbar. Er wird jedoch nicht nach [!DNL Adobe Commerce Optimizer] exportiert, wenn der Connector aktiviert ist. Um die Such- und Merchandising-Funktionen zu implementieren, die diese Erweiterungen nach der Aktivierung des Connectors bieten, konfigurieren Sie sie über die [[!DNL Adobe Commerce Optimizer] Admin-Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/commerce/optimizer/overview#quick-tour).

>[!ENDSHADEBOX]

## Konfigurationsschritte

Führen Sie die folgenden Schritte aus, um den Connector zu aktivieren und mit der Synchronisierung von Daten aus Commerce mit Ihrer Adobe Commerce Optimizer-Instanz zu beginnen.

1. **[Installieren Sie das Commerce Optimizer Connector-Paket](#install-the-commerce-connector-package)** verwenden Sie Composer, um Ihre Commerce-Instanz mit [!DNL Adobe Commerce Optimizer] zu verbinden.

1. **[Überprüfen und passen Sie die Datenexportkonfiguration](#customize-commerce-data-export-configuration)** Admin an.

1. **[Zum Herstellen der Verbindung zwischen Commerce und Commerce Optimizer sind API-Anmeldeinformationen erforderlich](#get-required-values-for-configuring-the-commerce-optimizer-connection)**.

1. **[Aktivieren Sie die  [!DNL Adobe Commerce Optimizer] -Integration](#enable-the-adobe-commerce-optimizer-integration)**.

1. **[Überprüfen Sie, ob die Datensynchronisation funktioniert](#verify-that-the-data-sync-is-working)**.


## Installieren des Commerce Optimizer Connector-Pakets

Der Adobe Commerce Optimizer-Connector wird als Composer-Metapaket bereitgestellt, das für alle Commerce-Händler mit einer aktiven Lizenz für [!DNL Adobe Commerce Optimizer] verfügbar ist.

### Installationsschritte

1. Fügen Sie das Modul `adobe-commerce/commerce-data-export-aco-adapter` mit dem Composer hinzu:

   ```shell
   composer require adobe-commerce/commerce-data-export-aco-adapter
   ```

1. Stellen Sie die Änderungen in Ihrer Adobe Commerce-Staging-Umgebung bereit.

Nach Abschluss der Bereitstellung ist die Option Commerce Optimizer im Menü Commerce Admin verfügbar. Klicken Sie auf **[!UICONTROL Commerce Optimizer]** , um Ihre Commerce Optimizer-Instanz direkt über den Commerce-Administrator zu öffnen.

>[!NOTE]
>
>Detaillierte Installationsanweisungen für Erweiterungen finden Sie in den folgenden Handbüchern:
>
>[Installieren der Erweiterung auf Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/extensions)
>
>[Installieren der Erweiterung auf Adobe Commerce On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions)

### Erforderliche Verbindungsdetails abrufen

Erstellen Sie in der Adobe Developer Console ein Entwicklerprojekt, das für den [!DNL Adobe Commerce Optimizer]-Aufnahme-Service aktiviert ist, und generieren Sie OAuth-Server-zu-Server-Anmeldeinformationen. Detaillierte Anweisungen finden Sie unter [Abrufen von IMS](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/authentication/#obtain-ims-credentials) im *Merchandising-Entwicklerhandbuch*.

>[!TIP]
>
>Wenn Sie bereits ein Entwicklerprojekt mit der Datenaufnahme-API in derselben IMS-Organisation wie Ihre Commerce Optimizer-Instanz konfiguriert haben, können Sie die vorhandenen OAuth-Server-zu-Server-Anmeldedaten wiederverwenden.

Speichern Sie die folgenden Werte auf der Seite mit den Anmeldedaten:

* **Organisations-ID** (`org_id`)
* **Client-ID** (`client_id`)
* **Client-Geheimnis** (`client_secret`)

### [!DNL Adobe Commerce Optimizer]-Instanzdetails abrufen

Speichern Sie die Instanz-ID (auch als Mandanten-ID bezeichnet) aus Ihrer [!DNL Adobe Commerce Optimizer]. Sie finden sie in der URL, die für den Zugriff auf die Instanz verwendet wird. In `https://experience.adobe.com/#/@<project-id>/in:TToyu73daQRn66KAYaq8YZ/commerce-optimizer-studio/home` ist die Instanz-ID beispielsweise `TToyu73daQRn66KAYaq8YZ`.

## Anpassen der Konfiguration für den Commerce-Datenexport

Standardmäßig ist die Synchronisierung von Katalogdaten für alle Commerce-Bereiche (Websites und Store-Ansichten) aktiviert. Sie können die Exporteinstellungen so anpassen, dass Daten nur für bestimmte Bereiche entsprechend Ihren Geschäftsanforderungen synchronisiert werden. Wenn Sie beispielsweise mehrere Store-Ansichten haben, aber nur Daten für eine dieser Ansichten exportieren möchten, können Sie für die anderen Store-Ansichten den Exporter deaktivieren.

>[!IMPORTANT]
>
>Durch Ändern der Exporteinstellungen wird eine vollständige Neuindizierung Trigger, die je nach Kataloggröße längere Zeit in Anspruch nehmen kann. Planen Sie diese Änderungen in Zeiten geringen Traffics, um Leistungseinbußen zu minimieren.

### Datenexport nach Umfang

In der folgenden Tabelle wird beschrieben, welche Daten auf jeder Bereichsebene exportiert werden:

| Umfang | Daten exportiert | Notizen |
| ------- | --------------- | ------- |
| Website | Preise und Preisbücher | Jede Preisgruppe wird als „Preisbuch[&#x200B; exportiert, wobei &#x200B;](../optimizer/setup/pricebooks.md) Namenskonvention `website::customergroupcode` verwendet wird. Alle Kundengruppen für die Website sind enthalten. |
| Shop-Ansicht | Produkte und Produktattribute | Jede Store-Ansicht erstellt eine separate Katalogquelle in [!DNL Adobe Commerce Optimizer]. |

### Aktivieren und Deaktivieren des Verhaltens

| Aktion | Ergebnis |
| -------- | -------- |
| Shop-Ansicht deaktivieren | Die Katalogquelle bleibt in [!DNL Adobe Commerce Optimizer], aber alle Daten werden entfernt. |
| Deaktivieren und reaktivieren Sie eine Store-Ansicht | Dieselbe Katalogquelle wird erneut mit einer vollständigen Datensynchronisation aufgefüllt. |

### Aktualisieren der Exportkonfiguration

Nach der Installation des Connector-Pakets zeigt das Speichergitter in Admin jetzt die Exportkonfigurationseinstellungen für Commerce Optimizer an.

![Raster mit Commerce Optimizer-Synchronisierungseinstellungen speichern](./assets/aco-connector-sync-config.png){width="600" zoomable="yes"}

**So ändern Sie die Einstellungen für eine Website- oder Store-Ansicht:**

1. Navigieren Sie im Commerce Admin zu **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL All Stores]**.

1. Wählen Sie die Website- oder Store-Ansicht aus, die Sie konfigurieren möchten.

1. Aktivieren Sie in den **[!DNL Adobe Commerce Optimizer]-** das Kontrollkästchen, um die Datensynchronisierung nach Bedarf zu aktivieren oder zu deaktivieren.

   ![Aktualisieren der Datensynchronisierungskonfiguration](./assets/aco-connector-store-website-export-settings.png){width="500" zoomable="yes"}

1. Speichern Sie Ihre Änderungen.

## [!DNL Adobe Commerce Optimizer] aktivieren

>[!IMPORTANT]
>
>Die Datensynchronisierungsverarbeitung beginnt, sobald Sie den Konfigurationsbefehl ausführen. Standardmäßig ist die Synchronisierung von Katalogdaten für alle Commerce-Bereiche (Websites und Store-Ansichten) aktiviert. Je nach Größe Ihres Katalogs kann der Datensynchronisierungsprozess einige Minuten bis mehrere Stunden dauern.

Mithilfe der API-Anmeldeinformationen und Instanzdetails, die Sie in den vorherigen Schritten gesammelt haben, können Sie jetzt die Integration zwischen Ihrer Commerce- und [!DNL Adobe Commerce Optimizer]-Instanz konfigurieren.

1. Wählen Sie in Commerce Admin die Option **[!UICONTROL Adobe Commerce Optimizer]** aus, um die Konfigurationsseite mit Anweisungen anzuzeigen.

   ![[!DNL Adobe Commerce Optimizer] Konfigurationsseite](/help/aco-connector/assets/aco-connector-admin-installation.png){width="500" zoomable="yes"}

1. Verwenden Sie in der Befehlszeile [SSH](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/secure-connections), um eine Verbindung zur Commerce-Staging-Umgebung herzustellen.

1. Führen Sie den folgenden Commerce-CLI-Befehl aus, um die Integration zu konfigurieren. Ersetzen Sie dabei die Platzhalterwerte durch die Werte für Ihr Commerce Optimizer-Projekt:

```terminal
bin/magento aco:config:init --org_id=your-org --tenant_id=your-tenant --client_id=your-client-id --client_secret=your-secret
```

1. Überprüfen Sie die Verbindung, indem Sie zum Commerce-Administrator zurückkehren und die Option [!UICONTROL Adobe Commerce Optimizer] auswählen.

   Wenn Sie auf die Option klicken, wird die [!DNL Adobe Commerce Optimizer]-Benutzeroberfläche auf einer neuen Registerkarte geöffnet.

## Überprüfen, ob die Datensynchronisation funktioniert

Nach Aktivierung der Integration beginnt die Datensynchronisation automatisch. Je nach Kataloggröße kann die erste Synchronisierung einige Minuten bis mehrere Stunden dauern.

1. **Überprüfen Sie den Synchronisierungsstatus im Commerce Admin-**:

   Navigieren Sie zu **[!UICONTROL System]** > [!UICONTROL Data Transfer] > **[!UICONTROL Data Feed Sync Status]**.

   ![Seite „Daten-Feed-Synchronisierungsstatus“ mit Reporting zum Feed-Elementstatus](./assets/data-feed-sync-status.png){width="500" zoomable="yes"}

   Wenn die Synchronisierung ausgeführt wird, zeigen die Feed-Daten erfolgreich gesendete Datensätze an. Feed auswählen, um Details anzuzeigen oder Synchronisierungsprobleme zu beheben.

1. **Bestätigen Sie, dass Daten in Commerce Optimizer eingegangen sind:**

   Wählen Sie im [!DNL Adobe Commerce Optimizer] Menü **[!UICONTROL Data Sync]** aus.

   ![Datensynchronisation](./assets/data-sync.png){width="500" zoomable="yes"}

   Überprüfen Sie, ob die erwarteten Produkte, Preise und Attribute angezeigt werden.

>[!TIP]
>
>Wenn Sie Probleme mit der Datensynchronisation haben, lesen Sie den Abschnitt [Fehlerbehebung](/help/data-export/troubleshooting-logging.md) in der Dokumentation zum *SaaS-*.

## Nächste Schritte

1. **[Konfigurieren [!DNL Adobe Commerce Optimizer] Katalogansichten und -richtlinien](#configure-adobe-commerce-optimizer-stores)**

   Erstellen Sie Katalogansichten und Richtlinien im [!DNL Adobe Commerce Optimizer]. Beachten Sie, dass Preisverzeichnisse automatisch von Adobe Commerce-Kundengruppen erstellt werden.

1. **[Einrichten einer Commerce-Storefront auf Edge Delivery Services](#set-up-a-commerce-storefront-on-edge-delivery-services)**

   Befolgen Sie die [Dokumentation zur Einrichtung von Storefronts](https://experienceleague.adobe.com/developer/commerce/storefront/setup/), um Ihre Storefront mit der [!DNL Adobe Commerce Optimizer]-Instanz zu verbinden und mit der Bereitstellung personalisierter Commerce-Erlebnisse zu beginnen.


