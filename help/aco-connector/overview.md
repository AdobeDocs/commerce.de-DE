---
title: Adobe Commerce Optimizer-Connector
description: Erfahren Sie, wie Sie Ihre Daten aus Ihrem Commerce Cloud- oder lokalen Projekt mit Adobe Commerce Optimizer verbinden
feature: Personalization, Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
hidefromtoc: true
hide: true
source-git-commit: 1654aede42cf53b2dffe2965680f122d7c247234
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---


# Adobe Commerce Optimizer Connector für Commerce

Der Adobe Commerce-Connector ist die Integrationsbrücke, die Katalog- und Preisdaten zwischen einer bestehenden Adobe Commerce Cloud in der Cloud oder On-Premise-Bereitstellung und dem zusammensetzbaren Katalogdatenmodell von Adobe Commerce Optimizer synchronisiert. Dies ermöglicht Funktionen wie dynamische KI-Suche, Recommendations, schnell ladende Headless-Storefronts, einschließlich Adobe Commerce-Storefronts auf Edge Delivery Services, und Echtzeit-Leistungsanalysen.

>[!NOTE]
>
>In dieser Dokumentation wird ein Produkt beschrieben, das sich in der Entwicklung für den frühzeitigen Zugriff befindet und nicht alle für die allgemeine Verfügbarkeit vorgesehenen Funktionen enthält.

## Architektur und Erfahrung

Der Adobe Commerce-Connector funktioniert durch die Zuordnung der `website/store/storeview` Kataloghierarchie von Commerce zum Adobe Commerce Optimizer-`channel/policy/source`.

Anstatt Commerce-Services (Live Search und Product Recommendations) über den Commerce-Administrator zu konfigurieren und zu verwalten, verwenden Sie [Adobe Commerce Optimizer Merchandising-Tools](../optimizer/merchandising/overview.md) um die Regelkonfiguration für die Produkterkennung (Live Search) und Recommendations (Product Recommendations) zu verwalten.  Die Adobe Commerce-Instanz wird zur Datenherkunft für Katalog- und Preisdaten. Wenn die Daten in Commerce aktualisiert werden, werden die Aktualisierungen mit der Adobe Commerce Optimizer-Instanz synchronisiert.

## Workflows

Der Connector ermöglicht mehrere wichtige Workflows:

* **Exportieren von Commerce-Katalogdaten nach Adobe Commerce Optimizer** - Preis- und Preisbuchdaten werden auf `website` exportiert. Produkt- und Produktattributdaten werden auf `store view` exportiert. Standardmäßig ist die Synchronisierung von Katalogdaten für alle Commerce-Bereiche (Websites und Store-Ansichten) aktiviert.

  Verwenden Sie zum Aktivieren dieses Workflows Composer, um die `adobe-commerce/commerce-data-export-aco-adapter` PHP-Erweiterung zu installieren, und geben Sie dann die IMS-Anmeldeinformationen zur Authentifizierung der Verbindung zwischen dem Commerce-Projekt an.

* **Ordnen Sie die nach Adobe Commerce Optimizer zu exportierenden Commerce-`website/store/storeview` zu**

  Sie haben die Möglichkeit, die Adobe Commerce Optimizer Exporter-Einstellungen so anzupassen, dass Daten nur für bestimmte Bereiche exportiert werden, indem Sie die Exporter-Konfiguration aus dem Store-Raster in Admin aktualisieren (**[!UICONTROL Stores]** -> [!UICONTROL Settings] -> **[!UICONTROL All Stores]**).

* **Konfiguration und Verwaltung von Merchandising-Regeln**

  Wenn der Connector aktiviert ist, werden Merchandising-Regeln für die Produkterkennung und Empfehlungen über die Adobe Commerce Optimizer-Benutzeroberfläche definiert und verwaltet, nicht über die Seiten [!UICONTROL Live Search] und [!UICONTROL Product Recommendations] in Commerce Admin.

* **Bereitstellen der Commerce-Storefront auf Edge Delivery Services**

  Nach der Einrichtung der Integration mit Adobe Commerce Optimizer können Sie eine Commerce-Storefront für Edge Delivery-Services einrichten und bereitstellen, um mithilfe der zusammenstellbaren, API-gesteuerten Architektur und der modularen Komponenten, die mit Adobe Commerce Optimizer verfügbar sind, ultraschnelle Leistung, Skalierbarkeit, nahtlose Inhaltserstellung, integrierte Personalisierung und reduzierte Betriebskosten zu erzielen.

## Voraussetzungen für die Verwendung der Integration

* Adobe Commerce 2.4.7+

   * PHP 8.2, 8.3 oder 8.4
   * Composer 2.x

* Adobe Commerce Optimizer-Lizenz mit einer bereitgestellten Sandbox-Instanz.

* Zugriff auf [repo.magento.com](https://repo.magento.com), um das Commerce Connector-Metapaket mit Composer herunterzuladen.

* Administratorzugriff auf eine [Adobe Commerce Optimizer Sandbox-Instanz](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-commerce-optimizer/create-first-instance).

Der Adobe Commerce-Benutzer, der die Integration konfiguriert, muss über Folgendes verfügen:

* Administratorzugriff auf den Adobe Commerce Admin.

* [Befehlszeilenzugriff auf den Adobe Commerce-Anwendungsserver](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access).

* Entwicklerzugriff auf die [IMS-Organisation](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations?), in der das Adobe Commerce Optimizer-Projekt bereitgestellt wird.

## Erste Schritte

1. **Einrichten der Integration**

   1. [Installieren Sie das Commerce Connector-Paket](#install-the-commerce-connector-package).

   1. [Abrufen der erforderlichen Werte für die Konfiguration der Commerce Optimizer-Verbindung](#get-required-values-for-configuring-the-commerce-optimizer-connection)

   1. [Aktivieren der Adobe Commerce Optimizer-Integration](#enable-the-adobe-commerce-optimizer-integration).

   1. [Überprüfen Sie, ob die Datensynchronisation funktioniert](#verify-that-the-data-sync-is-working).

   1. [Anpassen der Datenexportkonfiguration](#customize-commerce-data-export-configuration) (optional).

1. **[Konfigurieren von Adobe Commerce Optimizer-Stores](#configure-adobe-commerce-optimizer-stores)**

1. **[Einrichten einer Commerce-Storefront auf Edge Delivery Services](#set-up-a-commerce-storefront-on-edge-delivery-services)**

## Installieren des Commerce Connector-Pakets

Das Adobe Commerce Connector Composer-Metapaket steht allen Commerce-Händlern mit einer aktiven Lizenz für Adobe Commerce Optimizer zur Verfügung.

### Installationsschritte

1. Fügen Sie das Modul `adobe-commerce/commerce-data-export-aco-adapter` mit dem Composer hinzu:

```shell
 composer require adobe-commerce/commerce-data-export-aco-adapter
```

1. Stellen Sie die Änderungen in Ihrer Adobe Commerce-Staging-Umgebung bereit.

Nachdem Sie Ihre Änderungen bereitgestellt haben, ist die Option Commerce Optimizer Optimizer im Commerce Admin-Menü verfügbar.

>[!NOTE]
>
>Detaillierte Installationsanweisungen für Erweiterungen finden Sie in den folgenden Handbüchern:
>
>[Installieren der Erweiterung auf Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/extensions)
>
>[Installieren der Erweiterung Adobe Commerce On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions)

## Erforderliche Werte zum Konfigurieren der Commerce Optimizer-Verbindung abrufen

### API-Anmeldedaten abrufen

>[!NOTE]
>
>Wenn Sie bereits ein Entwicklerprojekt mit der Datenaufnahme-API in der IMS-Organisation haben, in der Ihre Commerce Optimizer-Instanz bereitgestellt ist, können Sie die erforderlichen API-Anmeldeinformationen und die Organisations-ID aus den OAUTH-Server-zu-Server-Anmeldeinformationen in diesem Projekt abrufen.

Erstellen Sie ein neues Entwicklerprojekt in der Adobe Developer-Konsole, um die Anmeldedaten für die Adobe Commerce Optimizer-Aufnahme-API abzurufen und die Integration zwischen Commerce- und Commerce Optimizer-Instanzen zu konfigurieren. Anweisungen finden Sie unter [Abrufen von IMS](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/authentication/#obtain-ims-credentials) im *Merchandising-Entwicklerhandbuch*.

Nachdem Sie das Projekt erstellt haben, speichern Sie die folgenden Werte auf der Seite mit den OAUTH-Server-zu-Server-Anmeldeinformationen :

* **Organisations-ID** (`org_id`)

* **IMS-`client_id` und`client_secret`**

### Adobe Commerce Optimizer-Instanzdetails abrufen

Speichern Sie die folgenden Werte aus Ihren Adobe Commerce Optimizer-Instanzdetails.

* **Instanz-ID - &#x200B;** Die eindeutige Kennung für Ihre Adobe Commerce Optimizer-Instanz. Wird auch als Mandanten-ID bezeichnet.

  Rufen Sie die Instanz-ID von der URL ab, um auf Ihre Adobe Commerce Optimizer-Instanz zuzugreifen. Im URL-`https://na1-sandbox.admin.commerce.adobe.com/1234567890abcdef` ist die Instanz-ID beispielsweise `1234567890abcdef`.

* **Region - &#x200B;** Die Region, in der Ihre Adobe Commerce Optimizer-Sandbox-Instanz gehostet wird.

  Abrufen der Region aus der Adobe Commerce Optimizer-URL. Im URL-`https://na1-sandbox.admin.commerce.adobe.com/1234567890abcdef` ist die Region beispielsweise `na1`.

## Aktivieren der Adobe Commerce Optimizer-Integration

>[!IMPORTANT]
>
>Die Datensynchronisierungsverarbeitung beginnt mit der Ausführung des Konfigurationsbefehls. Standardmäßig ist die Synchronisierung von Katalogdaten für alle Commerce-Bereiche (Websites und Store-Ansichten) aktiviert. Je nach Größe Ihres Katalogs kann der Datensynchronisierungsprozess viele Stunden dauern.

Mithilfe der API-Anmeldeinformationen und Instanzdetails, die Sie in den vorherigen Schritten gesammelt haben, können Sie jetzt die Integration zwischen Ihren Commerce- und Adobe Commerce Optimizer-Instanzen konfigurieren.

1. Wählen Sie in Commerce Admin die Option **[!UICONTROL Adobe Commerce Optimizer]** aus, um die Konfigurationsseite mit Anweisungen anzuzeigen.

   ![Adobe Commerce Optimizer-Konfigurationsseite](../assets/aco-connector-config-page.png)

1. Verwenden Sie in der Befehlszeile [SSH](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/secure-connections), um eine Verbindung zur Commerce-Staging-Umgebung herzustellen.

1. Führen Sie den folgenden Commerce-CLI-Befehl aus, um die Integration zu konfigurieren. Ersetzen Sie dabei die Platzhalterwerte durch die Werte für Ihr Commerce Optimizer-Projekt:

```terminal
bin/magento aco:config:init --org_id=<<your_org_id>> --tenant_id=<<your_tenant_id>> --client_id=<<your_client_id>> --client_secret=<<your_client_secret>> --region=<<na1>> --type=sandbox
```

1. Überprüfen Sie die Verbindung, indem Sie zum Commerce-Administrator zurückkehren und die Option [!UICONTROL Adobe Commerce Optimizer] auswählen.

   Wenn Sie auf die Option klicken, wird die Adobe Commerce Optimizer-Benutzeroberfläche auf einer neuen Registerkarte geöffnet.

## Überprüfen, ob die Datensynchronisation funktioniert

Sie können die Datensynchronisation sowohl von der Commerce Admin als auch von der Commerce Optimizer aus überprüfen.

* Auf **[Seite „Synchronisierungsstatus für Daten-Feeds](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status.md)** wird der Fortschritt der Synchronisierung von Katalogdaten von Commerce zu Adobe Commerce Optimizer angezeigt.

* Auf der **[[!UICONTROL Data Sync]Seite &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/optimizer/setup/data-sync)** in Adobe Commerce Optimizer werden die Katalogdaten angezeigt, die von Ihrer Commerce-Instanz übertragen wurden.

1. Überprüfen Sie, ob Katalogdaten von Commerce an Commerce Optimizer fließen:

   Öffnen Sie in Commerce Admin die Seite [!UICONTROL Data Feed Sync Status] , indem Sie [!UICONTROL System] **&#x200B; > [!UICONTROL Data Transfer] > &#x200B;** [!UICONTROL Data Feed Sync Status]** auswählen.

   ![Seite „Daten-Feed-Synchronisierungsstatus“ mit Reporting zum Feed-Elementstatus](./assets/data-feed-sync-status.png)

   Wenn die Datensynchronisation gestartet wurde, zeigen die Feed-Daten erfolgreich gesendete Datensätze an. Sie können Synchronisierungsprobleme auch anzeigen und beheben, indem Sie die Details für jeden Feed anzeigen.

1. Stellen Sie sicher, dass Adobe Commerce Optimizer die Katalogdaten erhält:

   Wählen Sie im Menü Commerce Optimizer die Option **[!UICONTROL Data Sync]** aus, um die Seite Datensynchronisierung zu öffnen.

   ![Datensynchronisation](./assets/data-sync.png)

### Fehlerbehebung

Wenn die Datensynchronisation nicht gestartet wurde, stellen Sie sicher, dass die Katalogindizes gültig sind. Wenn die Indizes ungültig sind, führen Sie den folgenden Befehl über die Commerce-CLI aus, um die Katalogdaten neu zu indizieren:

```terminal
bin/magento indexer:reindex" catalog indexer re-index CLI command to start PaaS to ACO catalog data synchronization.
```

## Anpassen der Konfiguration für den Commerce-Datenexport

Sie haben die Möglichkeit, die Adobe Commerce Optimizer Exporter-Einstellungen so anzupassen, dass Daten nur für bestimmte Bereiche exportiert werden, indem Sie die Exporter-Konfiguration aus dem Store-Raster in Admin aktualisieren (**[!UICONTROL Stores]** -> [!UICONTROL Settings] -> **[!UICONTROL All Stores]**).

* Wenn Sie auf `website` Ebene die Einstellung Exporter deaktivieren, wird der Export von Preis- und Preisbuchdaten nach Adobe Commerce Optimizer gestoppt.

* Wenn Sie auf `storeview`-Ebene die Exporteinstellung deaktivieren, wird der Export von Produkten und Produktattributen nach Adobe Commerce Optimizer gestoppt.

Wenn die Konfiguration geändert wird, werden die entsprechenden Indizes ungültig gemacht, damit der Trigger die betroffenen Entitäten erneut exportieren kann.

## Konfigurieren von Adobe Commerce Optimizer-Stores

Konfigurieren Sie Adobe Commerce Optimizer-Stores, indem Sie Katalogansichten und Richtlinien erstellen&#x200B; Siehe [Erstellen von Katalogansichten](../optimizer/setup/catalog-view.md) im Adobe Commerce Optimizer-Handbuch.

Beachten Sie, dass Preisverzeichnisse automatisch von Adobe Commerce-Kundengruppen erstellt werden.

## Einrichten einer Commerce-Storefront in Edge Delivery Services

In diesem Abschnitt finden Sie einen allgemeinen Überblick über die Schritte, die zum Einrichten Ihrer Commerce-Storefront erforderlich sind. Detaillierte Informationen finden Sie auf der Dokumentations-Site zur &lbrace;0[ Adobe Commerce Storefront (https://experienceleague.adobe.com/developer/commerce/storefront/).]

1. Klonen und stellen Sie das Adobe Commerce Storefront-Textbaustein mithilfe des [Site Creator-Tools](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator) für EDS bereit.

1. [Einrichten einer lokalen Entwicklungsumgebung](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/#set-up-local-environment).

1. [GraphQL Storefront-Kompatibilitätspaket installieren](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/storefront-compatibility/install/).&#x200B;

1. [Konfigurieren Sie CORS-Header für die Commerce-Instanz in der Cloud-Umgebung](#configure-cors-headers-for-commerce-instance).

1. [Verbinden der Storefront mit Commerce-Datenquellen](#connect-the-storefront-to-commerce-data-sources).

### Konfigurieren von CORS-Headern für die Commerce-Instanz

Damit GraphQL-Anfragen von einer Edge Delivery Services (EDS)-Storefront an Adobe Commerce in einer Cloud- oder On-Premise-Umgebung gesendet werden können, fügen Sie den Adobe Commerce GraphQL-Endpunkten spezifische CORS-Kopfzeilen (Cross-Origin Resource Sharing) hinzu&#x200B; Anweisungen finden Sie unter [CORS-Setup](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/cors-setup/) in der Dokumentation zur *Adobe Commerce*.

### Verbinden der Storefront mit Commerce-Datenquellen

Aktualisieren Sie im GitHub-Repository für den Textbausteincode für die Storefront die Konfigurationsdatei für die Storefront, `config.json` mit den folgenden Parametern:

* `"commerce-core-endpoint": "Commerce cloud instance GraphQL endpoint"`, zum Beispiel `https://{{your store}}/graphql`.

* `"commerce-endpoint": "Commerce Optimizer instance GraphQL endpoint"`, zum Beispiel `https://na1-sandbox.api.commerce.adobe.com/{{instanceId}}/v1/catalog&#x200B;`.

* `"AC-Environment-Id": "Customer organization ID"` - Diesen Wert aus dem [Commerce-Cloud-Projekt abrufen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/overview#project-overview).

* `"AC-View-ID": "Catalog view ID in Commerce Optimizer Admin"` - Diesen Wert erhalten Sie aus der [Katalogansichtsdetails](../optimizer/setup/catalog-view.md#view-details) in Adobe Commerce Optimizer.

* `"AC-Price-Book-ID": "base::b6589fc6ab0dc82cf12099d1c2d40ab994e8410c"` - Diesen Wert erhalten Sie aus der Liste der zugeordneten Preisbücher in der [Katalogansichtsdetails](../optimizer/setup/catalog-view.md#view-details) in Adobe Commerce Optimizer.

* `"AC-Source-Locale": "catalogSource"` - Geben Sie die Quelle an, die mit der Commerce-Storeview verknüpft ist, um eine Verbindung zur Storefront herzustellen. Verfügbare Quellen werden auf der Seite [Datensynchronisierung](../optimizer/setup/data-sync.md) in Adobe Commerce Optimizer angezeigt.

Weitere Informationen finden Sie unter [Storefront-Konfiguration](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/) in der Dokumentation *Adobe Commerce*.


