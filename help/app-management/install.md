---
title: Installieren und Zugreifen auf [!DNL App Management]
description: Voraussetzungen und Zugriffsanforderungen für die Verwendung von Adobe Commerce [!DNL App Management].
feature: App Builder, Extensibility, Integration
source-git-commit: 86c0945bbb0a562de1b66d420dec2a05d4d81e5f
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Installieren und Zugreifen auf [!DNL App Management]

[!DNL App Management] für geeignete Commerce-Instanzen ist im Commerce-Admin verfügbar. Die Verfügbarkeit hängt von Ihrem Bereitstellungstyp ab.

## Verfügbarkeit

Nachdem Sie die folgenden Anforderungen erfüllt haben, wählen Sie unten die entsprechende Registerkarte für Ihren Bereitstellungstyp aus, um zu sehen, ob [!DNL App Management] eine Installation erfordert oder bereits auf Ihrer Instanz verfügbar ist.

## Voraussetzungen

Bevor Sie eine App verknüpfen, stellen Sie Folgendes sicher:

| Anforderung | Beschreibung |
|-------------|-------------|
| **Administratorzugriff** | Commerce-Admin mit [!DNL App Management] Berechtigungen |
| **Bereitgestellte App** | App Builder-Anwendung, die in Ihrem Unternehmen bereitgestellt wird und eine Verbindung herstellen kann |
| **Organisationszugriff** | Zugriff auf die Adobe-Organisation, in der die App bereitgestellt wird |

>[!BEGINTABS]

>[!TAB Adobe Commerce as a Cloud Service]

[!DNL App Management] ist automatisch auf [!DNL Adobe Commerce as a Cloud Service] verfügbar. Es ist keine Installation erforderlich. [Aktivieren Sie sie in der Admin](#access-app-management) und beginnen Sie mit der Verknüpfung von Apps.

>[!TAB Adobe Commerce on Cloud (PaaS) und On-Premise]

* **Adobe Commerce 2.4.8 und höher** - [!DNL App Management] wird automatisch einbezogen. Es ist keine Installation erforderlich.

* **Adobe Commerce 2.4.5 bis 2.4.7**—Installieren Sie die [!DNL Admin UI SDK] (einschließlich [!DNL App Management]) mit dem Composer:

  ```bash
  composer require "magento/commerce-backend-sdk": ">=3.3"
  ```

  Führen Sie dann aus:

  ```bash
  composer update
  bin/magento setup:upgrade
  bin/magento indexer:reindex
  bin/magento cache:clean
  ```

Weitere Informationen finden [ unter „Installieren oder Aktualisieren der Adobe Commerce Admin](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/installation/){target="_blank"}Benutzeroberfläche - SDK&quot;.

>[!ENDTABS]

## [!DNL App Management]

1. Melden Sie sich beim Commerce Admin an.

1. Navigieren Sie zu **[!UICONTROL Apps]** > **[!UICONTROL App Management]**.

Die [!DNL App Management] wird angezeigt. Hier können Sie App Builder-Programme verknüpfen, konfigurieren und verwalten.

## Installieren von App Builder Apps

Wenn Sie eine App Builder-App von Adobe Exchange installieren müssen (z. B. eine vordefinierte Integration oder eine Marketplace-App), finden Sie unter [Installieren von App Builder-Apps von Adobe Exchange](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/install-app-builder-app){target="_blank"} schrittweise Anweisungen.

Nachdem eine App installiert und bereitgestellt wurde, verwenden Sie [!DNL App Management] , um [sie mit Ihrer Commerce-Instanz zu verknüpfen](manage-app.md#associate-an-app) und ihre Einstellungen zu konfigurieren.

## Commerce Webhooks und Apps

Einige App Builder-Programme verwenden [Adobe Commerce-Webhooks](https://developer.adobe.com/commerce/extensibility/webhooks/) damit Commerce Ihre App über HTTP aufrufen kann, wenn bestimmte Ereignisse eintreten (z. B. nachdem ein Produkt gespeichert wurde). Webhook-Endpunkte und Abonnementlogik werden vom **App-Entwickler** beim Erstellen und Bereitstellen der Anwendung definiert. Store-Administratoren konfigurieren Webhooks nicht separat in App Management.

Nachdem Sie [ App mit ](https://experienceleague.adobe.com/en/docs/commerce/app-management/manage-app/manage-app) Commerce-Instanz verknüpft und alle Einrichtungsanweisungen der App ausgeführt haben, folgt das Webhook-Verhalten der Implementierung der App.

Wenn [!DNL App Management] den Validierungsendpunkt der App nicht mit Triggern versehen können (z. B. wenn die URL nicht erreichbar ist oder die Antwort die Anforderungen nicht erfüllt), wird möglicherweise ein Fehler wie der folgende im [!DNL App Management]-Dashboard angezeigt:

![Webhook-Validierungsfehler](assets/webhook-validation-error.png){width="600" zoomable="yes"}

Arbeiten Sie mit dem **App-Entwickler** zusammen, um die Webhook-Konfiguration oder -Bereitstellung zu korrigieren, damit die Validierung erfolgreich sein kann.

**App-**. Informationen zum Implementieren von Webhook-Abonnements und Handler-Antworten von App Builder [ Sie unter ](https://developer.adobe.com/commerce/extensibility/app-management/installation/webhooks/)Webhooks“ in der Entwicklerdokumentation für die Commerce-Erweiterbarkeit und im [`@adobe/aio-commerce-lib-webhooks`](https://github.com/adobe/aio-commerce-sdk/tree/main/packages/aio-commerce-lib-webhooks) auf GitHub.
