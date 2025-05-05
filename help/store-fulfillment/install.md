---
title: Installation
description: Installieren Sie  [!DNL Store Fulfillment solution]  für eine Adobe Commerce-Storefront mit Composer für PHP.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Installation

Die Erstinstallation der [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]-Erweiterung in einer Nicht-Produktionsumgebung wird abgeschlossen, wobei der Warteschlangen-Manager ausgeführt und die Zwischenspeicherung konfiguriert wird, um die Ausnahmebehandlung zu ermöglichen. Stellen Sie sicher, dass Ihre Entwicklungsumgebung Entwicklungs-Tools enthält, um Best Practices für den Betrieb und die Wartung Ihrer Adobe Commerce-Instanz sicherzustellen.

>[!TIP]
>
>Aktualisieren Sie die Store Fulfillment-Erweiterung für Adobe Commerce On-Premise, indem Sie die [Upgrade-Anweisungen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html?lang=de) im _Adobe Commerce Upgrade Guide_ befolgen. Informationen zu Adobe Commerce in Cloud-Infrastrukturen finden Sie [Upgrade einer Erweiterung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=de#upgrade-an-extension) im Handbuch zu Commerce in Cloud-Infrastrukturen *.*

## Voraussetzungen

Lesen Sie die [Anforderungen](solution-requirements.md) für die Store Fulfillment-Lösung und sammeln Sie die erforderlichen Informationen, bevor Sie die [!DNL Store Fulfillment] für Adobe Commerce installieren oder aktualisieren.

Wenn Sie eine Vorabversion oder Betaversion der Erweiterung Store Fulfillment for Adobe Commerce installiert haben, verwenden Sie den folgenden Befehl, um sie zu entfernen, bevor Sie die aktuelle Version installieren.

```bash
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Installationsanforderungen

- **Zugriff auf das Software-Archiv für Store Fulfillment von Walmart Commerce Technologies (.zip-Datei)** - Während des Onboarding- und Aktivierungsprozesses wenden Sie sich an Ihren Account Manager, um Zugriff auf die Installationsdatei für die Store Fulfillment-Erweiterung zu erhalten.

- **Adobe Commerce-Kontoinformationen** Für die Installation der [!DNL Store Fulfillment] ist ein [[!DNL Commerce] Konto](https://experienceleague.adobe.com/de/docs/commerce-admin/start/commerce-account/commerce-account-create){target="_blank"} erforderlich. Sie benötigen eine Konto-ID und Anmeldeinformationen mit Eigentümer- oder Administratorzugriff auf das [!DNL Adobe Commerce].

- Für [!DNL Adobe Commerce] an Cloud-Infrastrukturprojekten müssen Softwareinstallationsprogramme Administratorzugriff auf das Cloud-Projekt haben. Siehe [Benutzerzugriff verwalten](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/project/user-access).

- **Erfahrung mit der Verwendung von Composer und der[!DNL Commerce CLI]** - Siehe [Allgemeine CLI-Installation](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/extensions){target="_blank"} für Informationen zur Verwendung dieser Tools zur Installation und Verwaltung von Erweiterungen auf der [!DNL Adobe Commerce].

- **Installieren von Erweiterungen von Drittanbietern auf Adobe Commerce** - Weitere Informationen finden Sie in der Dokumentation zu Adobe Commerce.

   - [Installieren Sie eine Erweiterung für eine Adobe Commerce auf einer Cloud-Infrastrukturinstanz](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension).

   - [Installieren Sie eine Erweiterung für eine lokale Adobe Commerce-Instanz](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/extensions).

### Schritt 1: Erweiterungspaket herunterladen

Befolgen Sie die Anweisungen Ihrer Kundenbetreuer, um die Archivdatei mit den Composer-Paketen für die Installation der Store Fulfillment Services-Erweiterung herunterzuladen.

### Schritt 2: Extrahieren von Erweiterungsartefakten in die Anwendung

Extrahieren Sie die Archivdatei, die das Integrationspaket enthält, um die Store Fulfillment Services-Erweiterung zu installieren.

1. Erstellen Sie ein Zielverzeichnis für die extrahierten Dateien.

   - Wechseln Sie in der Befehlszeile zum Stammverzeichnis des Webserverdokuments.

   - Erstellen Sie ein `artifacts`.

1. Extrahieren Sie die Archivdatei in das neue Verzeichnis.

1. Überprüfen Sie, ob die Dateien erfolgreich extrahiert wurden, indem Sie die Dateiliste lesen.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Schritt 3: Mobile App mit Composer konfigurieren

Verwenden Sie Composer, um den Quellordner für die Installation zu konfigurieren und die Store Fulfillment Services-Erweiterung zu installieren.

1. Konfigurieren Sie das Quell-Repository für die Composer-Installation.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Fügen Sie die Erweiterung Store Fulfillment Services zu `composer.json` hinzu.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Um eine bessere Leistung auf lokalen Adobe Commerce-Instanzen zu erzielen, können Sie [die AutoLoad-Konfiguration aktualisieren](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html?lang=de#update-the-autoloader): `composer dump-autoload --optimize`

### Schritt 4: Datenbankschema und Daten aktualisieren

Schließen Sie die Installation ab, indem Sie die `bin/magento setup:upgrade` verwenden, um das Datenbankschema und die Daten mit den Änderungen zu aktualisieren, die die Store Fulfillment-Lösung unterstützen.

>[!NOTE]
>
>Für Adobe Commerce in Cloud-Infrastrukturprojekten müssen Sie die Erweiterung nicht registrieren. Bestätigen Sie stattdessen die Code-Änderungen aus dem vorherigen Schritt und übertragen Sie sie in Ihre Umgebungsverzweigung. Die Befehle zum Aktualisieren des Datenbankschemas und der Daten werden während des Cloud-Build- und -Bereitstellungsprozesses automatisch ausgeführt.

### Schritt 5: Installation abschließen

1. Registrieren Sie die Erweiterung für Adobe Commerce mithilfe des `setup:upgrade` Magento-CLI-Befehls.

   ```bash
   bin/magento setup:upgrade
   ```

1. Kompilieren Sie das [!DNL Commerce]-Projekt erneut, wenn Sie dazu aufgefordert werden.

   ```bash
   bin/magento setup:di:compile
   ```

1. Reinigen Sie den Cache.

   ```bash
   bin/magento cache:clean
   ```

1. Deaktivieren Sie den Wartungsmodus.

   ```bash
   bin/magento maintenance:disable
   ```

### Schritt 6: Installation überprüfen

Stellen Sie vom Adobe Commerce-Server aus sicher, dass die Module für die Store Fulfillment Services-Erweiterung installiert und aktiviert sind.

1. Melden Sie sich beim -Server an.

   Für Installationen auf Adobe Commerce in der Cloud-Infrastruktur [verwenden Sie SSH, um sich bei der Remote-Umgebung anzumelden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).

1. Stellen Sie sicher, dass die Store Fulfillment Services-Module aktiviert sind.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   Die Ausgabe sollte die folgenden Module enthalten:

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### Zusätzliche Schritte

Verwenden Sie bei Bedarf den [setup:static-content:deploy](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/cli-reference/commerce-on-premises){target="_blank"} CLI-Befehl, um statische Ansichtsdateien in Ihrer Produktionsumgebung bereitzustellen.

```bash
php bin/magento setup:static-content:deploy -f
```

Die Option &quot;`-f`&quot; ist erforderlich, wenn Sie ein leeres Design verwenden.

>[!NOTE]
>
>Weitere Informationen finden Sie im Artikel [Best Practices für die Bereitstellung statischer Inhalte in Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html?lang=de) im Adobe Commerce-Hilfezentrum.


