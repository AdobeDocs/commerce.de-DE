---
title: Installieren von [!DNL Payment Services]
description: Installieren Sie die Erweiterung Zahlungsdienste .
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade, Paas
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%
---
# Installieren von [!DNL Payment Services]

Um mit Payment Services für [!DNL Adobe Commerce] und [!DNL Magento Open Source] zu beginnen, müssen Sie einige Onboarding-Schritte ausführen.

>[!INFO]
>
> Weitere Informationen finden [&#x200B; in  [!DNL Payment Services]  Video „Konfigurieren für &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services)&quot;.

Das Herunterladen und Installieren der [!DNL Payment Services]-Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist ein erforderlicher Schritt für die Verwendung von [!DNL Payment Services].

## Herunterladen der Erweiterung

Sie müssen zuerst die Erweiterung von [Commerce Marketplace herunterladen](https://experienceleague.adobe.com/en/docs/commerce-admin/start/resources/commerce-marketplace) bevor Sie sie installieren können.

1. Navigieren Sie zur [Payment Services-Erweiterung in der Commerce Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. Um die Bearbeitung und Version auszuwählen, schalten Sie **[!UICONTROL Edition]** um und **[!UICONTROL Your store version]** Sie Ihre bevorzugte Auswahl an.
1. Klicken Sie auf **[!UICONTROL Add to Cart]**.
1. Checkout abschließen und auf **[!UICONTROL Place Order]** klicken.
1. Überprüfen Sie die mit Ihrem Marketplace-Download verknüpfte E-Mail, um eine Bestellbestätigung und Details zu erhalten.

>[!NOTE]
>
> Für Adobe Commerce Version 2.4.7 oder höher ist [!DNL Payment Services] vorkonfiguriert verfügbar.

## Installieren der Erweiterung

Sie können die [!DNL Payment Services]-Erweiterung sowohl für [!DNL Adobe Commerce] in der Cloud-Infrastruktur als auch für lokale Instanzen installieren, die mit Ihrem im Anmeldeprozess bereitgestellten Commerce-[&#x200B; (](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information#access-keys)) verknüpft sind.
[!DNL Magento Open Source] Kunden verwenden die lokal installierten Anweisungen.

Composer verwendet diese Schlüssel bei der ersten Installation von [!DNL Adobe Commerce] oder in Situationen, in denen die Composer-Schlüssel zuvor nicht in der `auth.json`-Datei gespeichert wurden.

Weitere [&#x200B; zum Abrufen von Composer-Schlüsseln finden &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) unter „Abrufen von Authentifizierungsschlüsseln“.

Weitere Informationen dazu[&#x200B; was vor dem Herunterladen und Installieren einer Erweiterung zu beachten &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions), finden Sie unter „Installieren einer Erweiterung“.

### [!DNL Adobe Commerce] zur Cloud-Infrastruktur

Diese Methode wird zum Installieren der [!DNL Payment Services]-Erweiterung für eine Commerce Cloud-Instanz verwendet.

1. Aktualisieren Sie Ihre `composer.json`:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie den Befehl `composer update` , um alle Stammabhängigkeiten zu aktualisieren.

1. Übertragen und übertragen Sie Ihre Änderungen.

### On-Premise und andere Konfigurationen

Diese Methode wird für die Installation der [!DNL Payment Services]-Erweiterung für eine lokale Instanz und [!DNL Magento Open Source] Kunden verwendet.

1. Um die Erweiterung zu erhalten, führen Sie die folgenden Befehle aus:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie den Befehl `composer update` , um alle Stammabhängigkeiten zu aktualisieren.

1. Aktualisieren Sie Ihre Instanz:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

1. Änderungen übernehmen.
1. Um sicherzustellen, dass der übergebene Code bereitgestellt wird, aktualisieren Sie Ihre Instanz .

>[!NOTE]
>
> [!DNL Payment Services] 1.6.1 ist kompatibel mit PHP-Versionen 7.x. Es wird jedoch dringend empfohlen, auf die neueste [!DNL Payment Services] Version zu aktualisieren.

## Aktualisieren der Erweiterung

Wenn eine neue Version von [!DNL Payment Services] veröffentlicht wird, können Sie Ihre Erweiterung einfach aktualisieren.

1. So rufen Sie die neueste Version des Pakets ab:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie den Befehl `composer update` , um alle Stammabhängigkeiten zu aktualisieren.

1. Führen Sie nach dem Composer-Update Folgendes aus:

   ```bash
   bin/magento setup:upgrade
   ```

1. Übertragen und übertragen Sie Ihre Änderungen.

## Fehlerbehebung

Beim Versuch, die [!DNL Payment Services]-Erweiterung zu installieren, werden möglicherweise Fehler angezeigt. Verwenden Sie die folgenden Methoden zur Fehlerbehebung, um die Fehler zu beheben.

### Repository-Liste

Stellen Sie sicher, dass `repo.magento.com` in der Liste der Repositorys vorhanden ist.

### Falsche Composer-Schlüssel

Wenn die folgende Fehlermeldung angezeigt wird, die besagt, dass Sie die falschen Composer-Schlüssel haben:

```
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Überprüfen Sie, ob Ihre Composer-Schlüssel gültig sind und Sie Zugriff auf andere Magento-Pakete haben.

So sehen Sie, welche Composer-Schlüssel konfiguriert sind:

1. Suchen Sie den Speicherort der `auth.json`:

   ```bash
   composer config --global home
   ```

1. `auth.json` anzeigen:

   ```bash
   cat /path/to/auth.json
   ```

1. Siehe [Welche Schlüssel sind mit Ihrem Commerce-`MageID`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) verknüpft?

### Nicht genügend Speicher für PHP

Wenn der folgende Fehler darauf hinweist, dass nicht genügend Speicher für PHP vorhanden ist:

```
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Erhöhen Sie die Speicherbegrenzung](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#increase-php-memory-limit) für PHP in Ihrer Umgebung in `php.ini`.

Alternativ können Sie die Speicherbegrenzung mit diesem Befehl angeben: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Beispiel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
