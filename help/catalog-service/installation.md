---
title: Onboarding und Installation
description: Erfahren Sie, wie Sie installieren [!DNL Catalog Service]
exl-id: 3f8492c3-f76d-49b7-a201-35deace36a1d
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: 54fbf7f65ee5e464a4b61a9df95fef7536f1cedb
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 0%

---

# Onboarding und Installation

Installieren Sie den Katalog-Service, um Produktdaten von einer Commerce-Instanz mithilfe der [Catalog Service GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/) anzufordern und zu empfangen. Der Katalog-Service wird als Composer-Metapaket aus dem Repository repo.magento.com bereitgestellt.

>[!NOTE]
>
>Wenn Ihre Commerce-Instanz die Live Search oder Product Recommendations verwendet, wird der Katalog-Service automatisch installiert oder aktualisiert, sobald Sie diese Services integrieren oder aktualisieren. Weitere Informationen finden Sie in den Installationsanweisungen für [Live Search](https://experienceleague.adobe.com/en/docs/commerce/live-search/install) und [Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/getting-started/install-configure).



## Systemanforderungen

**Softwareanforderungen**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3, 8.4
- Komponist: 2.x

**Unterstützte Plattformen**

- Adobe Commerce auf Cloud-Infrastruktur: 2.4.4+
- Adobe Commerce On-Premises: 2.4.4+

## Endpunkte

[!DNL Catalog Service] stehen zwei Endpunkte für das Onboarding zur Verfügung:

- Sandbox (`https://catalog-service-sandbox.adobe.io/graphql`) - wird vor der Live-Schaltung zu Test- und Validierungszwecken verwendet
- Production (`https://catalog-service.adobe.io/graphql`) - wird für Live-Traffic für Commerce-Händler und -Websites verwendet

Alle Commerce-Testinstanzen verwenden den Sandbox-Endpunkt.

Führen Sie alle Belastungstests für den Sandbox-Endpunkt durch. Senden Sie vor Beginn des Auslastungstests ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket), damit das Services-Team den zusätzlichen Server-Traffic antizipieren kann.

## Installation und Konfiguration

Um mit [!DNL Catalog Service] für Adobe Commerce zu beginnen, sind die folgenden Schritte erforderlich:

- Installieren der Catalog Service-Erweiterung (`magento/catalog-service`)
- Konfigurieren des Service und des Datenexports
- Zugriff auf den Service

### Installieren der Catalog Service-Erweiterung

>[!BEGINSHADEBOX]

**Voraussetzung**

- Greifen Sie auf [repo.magento.com](https://repo.magento.com) zu, um die Erweiterung zu installieren. Informationen zum Generieren von Schlüsseln und zum Abrufen der erforderlichen Berechtigungen finden Sie unter [Abrufen Ihrer Authentifizierungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). Informationen zu Cloud-Installationen finden Sie im Handbuch [Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Zugriff auf die Befehlszeile des Adobe Commerce-Anwendungsservers.

>[!ENDSHADEBOX]

Installieren Sie die neueste Version der Catalog Services-Erweiterung (`magento/catalog-service`) auf einer Adobe Commerce-Instanz, auf der Adobe Commerce Version 2.4.4 oder höher ausgeführt wird. Der Katalog-Service wird als Composer-Metapaket aus dem Repository [repo.magento.com](https://repo.magento.com) bereitgestellt.

>[!BEGINTABS]

>[!TAB Cloud-Infrastruktur]

Verwenden Sie diese Methode, um die [!DNL Catalog Service] für eine Commerce Cloud-Instanz zu installieren.

1. Wechseln Sie auf Ihrer lokalen Workstation in das Projektverzeichnis für Ihr Adobe Commerce on Cloud-Infrastrukturprojekt.

   >[!NOTE]
   >
   >Informationen zur lokalen Verwaltung von Commerce-Projektumgebungen finden Sie unter [Verwalten von Verzweigungen mit der CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) im _Benutzerhandbuch für Adobe Commerce auf Cloud-Infrastruktur_.

1. Checken Sie die Umgebungsverzweigung aus, um sie mithilfe der Adobe Commerce Cloud-CLI zu aktualisieren.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Fügen Sie das Modul Katalog-Service hinzu.

   ```bash
   composer require magento/catalog-service --no-update
   ```

1. Paketabhängigkeiten aktualisieren.

   ```bash
   composer update "magento/catalog-service"
   ```

1. Code-Änderungen für `composer.json` und `composer.lock` übertragen und übertragen.

1. Fügen Sie die Code-Änderungen für die `composer.json`- und `composer.lock`-Dateien hinzu, übertragen Sie sie und übertragen Sie sie in die Cloud-Umgebung.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   Durch Pushen der Aktualisierungen in die Cloud-Umgebung wird der [Commerce-Cloud-Bereitstellungsprozess](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) gestartet, um die Änderungen anzuwenden. Überprüfen Sie den Bereitstellungsstatus im [Bereitstellungsprotokoll](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB On-Premises]

Verwenden Sie diese Methode, um die [!DNL Catalog Service] für eine lokale Instanz zu installieren.

1. Verwenden Sie Composer, um das Modul Katalog-Service zu Ihrem Projekt hinzuzufügen:

   ```bash
   composer require magento/catalog-service --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update  "magento/catalog-service"
   ```

1. Adobe Commerce aktualisieren:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >In einigen Fällen, insbesondere bei der Bereitstellung in der Produktion, empfiehlt es sich möglicherweise, kompilierten Code nicht zu löschen, da dies einige Zeit in Anspruch nehmen kann. Stellen Sie sicher, dass Sie Ihr System sichern, bevor Sie Änderungen vornehmen.

>[!ENDTABS]

### Konfigurieren des Service und des Datenexports

Führen Sie nach der Installation des [!DNL Catalog Service] die folgenden Schritte aus, um den Katalog-Service in Ihre Adobe Commerce-Instanz zu integrieren. Diese Integration ermöglicht die Datensynchronisation und Kommunikation zwischen der Commerce-Instanz, dem Katalog-Service und anderen unterstützenden Services. Die Datensynchronisation wird von der [SaaS-Datenexporterweiterung“ ](../data-export/overview.md).

1. Richten Sie den [Commerce Services-Connector ein](https://experienceleague.adobe.com/en/docs/commerce/user-guides/integration-services/saas) indem Sie die API-Schlüssel angeben und einen SaaS-Datenspeicher auswählen.

   Die Einrichtung des Commerce Services-Connectors ist ein einmaliger Prozess, der zur Verwendung von Adobe Commerce-Services wie dem Katalog-Service, der Live-Suche und den Produktempfehlungen erforderlich ist. Wenn Sie den Connector bereits für einen anderen Dienst konfiguriert haben, überspringen Sie diesen Schritt.

1. Führen Sie eine erste Datensynchronisation über das [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) durch.

   Die erste Synchronisierung kann je nach Kataloggröße einige Minuten bis Stunden dauern. Sie können den Synchronisierungsstatus über das Daten-Management-Dashboard überwachen. Nach der ersten Synchronisierung exportiert der Katalog laufend Produktdaten, um die Services auf dem neuesten Stand zu halten.

   >[!NOTE]
   >
   >Sie können die Erstsynchronisierung auch über die Befehlszeile starten, indem Sie die Commerce-CLI verwenden. Siehe [Erstsynchronisierung](../data-export/data-export-cli-commands.md#initial-sync) im _SaaS-Datenexporthandbuch_.

So stellen Sie sicher, dass der Katalogexport ordnungsgemäß ausgeführt wird:

- [Bestätigen Sie, dass Cron-Aufträge ausgeführt werden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Stellen Sie sicher, dass die Indexer vom [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) oder mithilfe des Commerce CLI-`bin/magento indexer:info` ausgeführt werden.
- Stellen Sie sicher, dass die `Catalog Attributes Feed, Product Feed, Product Overrides Feed`- und `Product Variant Feed`-Indexer auf `Update by Schedule` eingestellt sind.

### Überwachen und Fehlerbehebung bei der Datensynchronisation

Vom Commerce-Administrator aus können Sie den Synchronisierungsprozess mithilfe des [Daten-Management-Dashboards“ ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Verwenden Sie die [Commerce-CLI](../data-export/data-export-cli-commands.md#troubleshooting) und Protokolle, um den Prozess zu verwalten und Fehler zu beheben.

### Zugriff auf den Service

Auf die [!DNL Catalog Service] GraphQL-API kann über den ` https://catalog-service.adobe.io/graphql`-Endpunkt mithilfe von POST-Befehlen über HTTPS zugegriffen werden.

In Ihren GraphQL-Abfragen müssen Sie mehrere HTTP-Kopfzeilen angeben, einschließlich des öffentlichen API-Schlüssels, den Sie der Adobe Commerce Services Connector-Konfiguration in Admin hinzugefügt haben. Weitere Informationen finden Sie in der [Storefront Services GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/)-Dokumentation.

### Firewall-Konfiguration

Um [!DNL Catalog Service] durch eine Firewall zuzulassen, fügen Sie `commerce.adobe.io` zur Zulassungsliste hinzu.

## Katalog-Service und API-Mesh

Das [API Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht Entwicklern die Integration von privaten oder Drittanbieter-APIs und anderen Benutzeroberflächen mit Adobe-Produkten mithilfe von Adobe IO.

Informationen zur Installation [[!DNL Catalog Service]  Konfiguration finden Sie ](mesh.md) Thema „und API-Mesh“ .

## Dashboard für das Daten-Management

Weitere Informationen zur [!DNL Catalog Service] Datensynchronisation finden Sie unter [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
