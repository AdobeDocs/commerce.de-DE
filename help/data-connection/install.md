---
title: Installieren [!DNL Data Connection]
description: Erfahren Sie, wie Sie die Erweiterung  [!DNL Data Connection]  Adobe Commerce installieren, aktualisieren und deinstallieren.
role: Admin, Developer
feature: Install
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Installieren von [!DNL Data Connection]

Bevor Sie die Erweiterung installieren, [ Sie die Voraussetzungen ](overview.md#prereqs).

## Installieren der Erweiterung

Die [!DNL Data Connection]-Erweiterung ist über den [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html) verfügbar. Wenn Sie diese Erweiterung über die Befehlszeile des Servers installieren, wird eine Verbindung zu Ihrer Adobe Commerce-Installation als [Service](../landing/saas.md) hergestellt. Wenn der Prozess abgeschlossen ist, werden **[!DNL Data Connection]** und **Commerce Services Connector** im Menü **System** unter **Services** in Commerce _Admin_ angezeigt.

Admin-Ansicht ![[!DNL Data Connection] Erweiterung](assets/epc-adminui.png)

>[!IMPORTANT]
>
>Während der Name der Erweiterung von Experience Platform Connector in [!DNL Data Connection] geändert wurde, bleibt der Paketname `experience-platform-connector`, um die Abwärtskompatibilität zu unterstützen.

1. Um das `experience-platform-connector`-Paket herunterzuladen, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Dieses Metapaket enthält die folgenden Module und Erweiterungen:

   - `magento/orders-connector`
   - `magento/data-services`
   - `magento/customers-connector`
   - `magento/module-experience-connector`
   - `magento/module-experience-connector-admin`
   - `magento/module-experience-connector-admin-graph-ql`
   - `magento/module-experience-connector-aep-integration`

1. (Optional) Um [!DNL Live Search] einzuschließen, die [Suchereignisse](events.md#search-events) umfassen, installieren Sie die [[!DNL Live Search]](../live-search/install.md).

1. (Optional) Um B2B-Daten einzuschließen, die [Anforderungsereignisse](events.md#b2b-events) umfassen, installieren Sie die [B2B-Erweiterung](#install-the-b2b-extension).

1. (Optional) Wenn Sie ein Händler im Gesundheitswesen sind, installieren Sie die [Data Services HIPAA](#install-the-data-services-hipaa-extension)-Erweiterung, damit Ihre [!DNL Commerce] Backoffice-Daten HIPAA-fähig sind.

### Installieren Sie Adobe I/O Events und konfigurieren Sie das Modul „customers-connector“

Nachdem Sie die `experience-platform-connector`-Erweiterung installiert haben, müssen Sie Adobe I/O Events für Adobe Commerce installieren und das `customers-connector` konfigurieren.

Die folgenden Schritte gelten sowohl für Adobe Commerce in der Cloud-Infrastruktur als auch für On-Premise-Installationen.

1. Wenn Sie Commerce 2.4.4 oder 2.4.5 ausführen, verwenden Sie den folgenden Befehl, um die Ereignismodule zu laden:

   ```bash
   composer require magento/commerce-eventing=^1.0 --no-update
   ```

   Commerce 2.4.6 und höher lädt diese Module automatisch.

1. Aktualisieren Sie die Projektabhängigkeiten.

   ```bash
   composer update
   ```

1. Aktivieren Sie die neuen Module:

   ```bash
   bin/magento module:enable Magento_AdobeCommerceEventsClient Magento_AdobeCommerceEventsGenerator Magento_AdobeIoEventsClient Magento_AdobeCommerceOutOfProcessExtensibility
   ```

Die Installation kann je nach Bereitstellungstyp abgeschlossen werden: Adobe Commerce auf Cloud-Infrastruktur oder On-Premise.

#### Über die Cloud-Infrastruktur

Aktivieren Sie in Adobe Commerce auf der Cloud-Infrastruktur die globale Variable `ENABLE_EVENTING` in `.magento.env.yaml`. [Weitere Informationen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html?lang=de#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

Übertragen und Übertragen aktualisierter Dateien in die Cloud-Umgebung. Wenn die Bereitstellung abgeschlossen ist, aktivieren Sie das Senden von Ereignissen mit dem folgenden Befehl:

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### On-Premises

In lokalen Umgebungen müssen Sie die Codegenerierung und Adobe Commerce-Ereignisse manuell aktivieren:

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Installieren der B2B-Erweiterung

Installieren Sie für B2B-Händler die folgende Erweiterung, um Ereignisdaten [Anforderungsliste](events.md#b2b-events) einzuschließen.

Laden Sie die `magento/experience-platform-connector-b2b`-Erweiterung herunter, indem Sie Folgendes über die Befehlszeile ausführen:

```bash
composer require magento/experience-platform-connector-b2b
```

### Installieren der HIPAA-Erweiterung für Data Services

Installieren Sie für Händler im Gesundheitswesen die folgende Erweiterung, um sicherzustellen, dass die Backoffice-Ereignisdaten HIPAA-fähig sind.

Laden Sie die `magento/module-data-services-hipaa`-Erweiterung herunter, indem Sie Folgendes über die Befehlszeile ausführen:

```bash
composer require magento/module-data-services-hipaa
```

## Aktualisieren der [!DNL Data Connection] {#update}

Um die [!DNL Data Connection]-Erweiterung zu aktualisieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Oder für B2B-Händler:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Um auf eine Hauptversion zu aktualisieren, z. B. von 2.0.0 auf 3.0.0, bearbeiten Sie die [!DNL Composer]-`.json` des Projekts wie folgt:

1. Öffnen Sie die `composer.json` und suchen Sie nach `magento/experience-platform-connector`.

1. Aktualisieren Sie im Abschnitt `require` die Versionsnummer wie folgt:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
      ...
    }
   ```

1. **Speichern** `composer.json`. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   Oder für B2B-Händler:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Deinstallieren der [!DNL Data Connection] {#uninstall}

Informationen zum Deinstallieren der [!DNL Data Connection]-Erweiterung finden Sie unter [Module deinstallieren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html?lang=de).
