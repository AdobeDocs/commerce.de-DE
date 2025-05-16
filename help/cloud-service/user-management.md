---
title: Benutzerverwaltung
description: Erfahren Sie, wie Sie in Benutzer verwalten [!DNL Adobe Commerce as a Cloud Service].
exl-id: 9bc80fe6-6dfd-4bb3-8dc5-d5efd8a8d90c
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 34057c1e55ff117ea7aab4407f31548ce826691b
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---

# Benutzerverwaltung

{{accs-early-access}}

Wenn Sie möchten, dass Benutzer auf den Admin in [!DNL Adobe Commerce as a Cloud Service] zugreifen, müssen Sie sie als Benutzer in Ihrer Organisation hinzufügen und sicherstellen, dass sie Zugriff auf das Cloud Service-Produkt in der [Adobe Admin Console haben](https://adminconsole.adobe.com){target="_blank"}.

Für diesen Prozess ist eine IMS-Organisation mit Zugriff auf [!DNL Adobe Commerce as a Cloud Service] erforderlich. Nur ein Systemadministrator oder Produktadministrator für das Unternehmen kann diese Prozesse durchführen.

>[!TIP]
>
>Um mehrere Benutzer gleichzeitig hinzuzufügen, können Sie einen [CSV-Upload](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html){target="_blank"} durchführen.
> 
> Sie können einer Rolle auch mehrere Benutzer hinzufügen, indem Sie eine [Benutzergruppe](https://helpx.adobe.com/enterprise/using/user-groups.html){target="_blank"} erstellen. Anschließend können Sie das Produkt [!UICONTROL **Adobe Commerce as a Cloud Service - Backend**] zur Benutzergruppe hinzufügen.

## Grundlegendes zu Rollen

Die folgenden Rollen sind für [!DNL Adobe Commerce as a Cloud Service] verfügbar. Um diese Rollen anzuzeigen oder zu bearbeiten, navigieren Sie in der Commerce-Admin zu **System** > **Berechtigungen** > **Benutzerrollen**.

* **Benutzer**: Benutzer haben Administratorzugriff auf Commerce Admin, können jedoch nicht den Zugriff auf Produktebene in Admin Console verwalten. Benutzer können auch Punktzahlen verwenden, um [ Instanzen ](./getting-started.md#create-an-instance) der [!DNL Commerce Cloud Manager] zu erstellen.

* [**Entwickler**](https://helpx.adobe.com/enterprise/using/manage-developers.html#Adddevelopers){target="_blank"} Entwickler verfügen über Benutzerberechtigungen und werden der Commerce-Instanz als Entwicklerbenutzer hinzugefügt. Das bedeutet, dass sie die [Admin-Benutzeroberfläche SDK](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/){target="_blank"} verwenden [Ereignisse konfigurieren](https://developer.adobe.com/commerce/extensibility/events/){target="_blank"} und [Webhooks erstellen](https://developer.adobe.com/commerce/extensibility/webhooks/){target="_blank"}.

* Administratoren : Es gibt drei verschiedene Arten von Administratoren:
   * [Systemadmins](https://helpx.adobe.com/enterprise/using/admin-roles.html){target="_blank"} - Der Systemadmin hat über die Admin Console Zugriff auf alle Produkte und Produktprofile in der Organisation.
   * [Produktadministrierende](#add-a-product-admin) - Produktadministrierende können [Benutzende, Rollen und Berechtigungen für das Produkt verwalten](#add-users-and-admins) in der [!DNL Adobe Admin Console] und [Benutzende im Commerce Admin verwalten](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-users-all#create-a-user){target="_blank"}.
   * [Produktprofil-Administrierende](#add-users-developers-and-product-profile-admins) - Produktprofil-Administrierende haben keinen Zugriff auf den Adobe Commerce-Admin, können jedoch Benutzende für das Produkt im [!DNL Adobe Admin Console] verwalten.

Ausführliche Informationen zu den Berechtigungen, die den einzelnen Rollen in Adobe Commerce gewährt werden, finden Sie unter [Benutzerberechtigungen](#user-permissions).

## Hinzufügen eines Produktadministrators

1. Navigieren Sie zu https://adminconsole.adobe.com und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das [!UICONTROL **Adobe Commerce as a Cloud Service - Backend**] Produkt aus.

   ![Produkt auswählen](./assets/backend.png){width="600" zoomable="yes"}

1. Wählen Sie die Registerkarte [!UICONTROL **Administratoren**] aus.

1. Klicken Sie [!UICONTROL **Admin hinzufügen**].

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie als Administratoren hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

## Hinzufügen von Benutzern, Entwicklern und Produktprofil-Administrierenden

Die folgenden Anweisungen enthalten Informationen zum Hinzufügen von Benutzern und Entwicklern zur [!DNL Commerce Cloud Manager] und zur Commerce-Admin. Über die [!DNL Commerce Cloud Manager] können Sie Ihre Commerce-Instanzen erstellen und verwalten.

>[!NOTE]
>
>Nur Produkt- und Systemadministratoren können Benutzer und Entwickler zum Adobe Commerce as a Cloud Service-Produkt hinzufügen.

1. Navigieren Sie zu https://adminconsole.adobe.com und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das [!UICONTROL **Adobe Commerce as a Cloud Service - Backend**] Produkt aus.

   ![Produkt auswählen](./assets/backend.png){width="600" zoomable="yes"}

1. Klicken Sie auf [!UICONTROL **Produktprofil**] Standard - Cloud Manager&quot;.

1. Wählen Sie die Registerkarte [!UICONTROL **Benutzer**], [!UICONTROL **Entwickler**] oder [!UICONTROL **Administratoren**] und klicken Sie auf [!UICONTROL **Benutzer hinzufügen**] oder [!UICONTROL **Entwickler hinzufügen**] oder [!UICONTROL **Administratoren hinzufügen**].

   >[!NOTE]
   >
   >Administratoren, die über diesen Bildschirm hinzugefügt werden[ sind Produktprofiladministratoren](#understanding-roles) und haben keinen Zugriff auf Commerce Admin.

   ![Auswählen](./assets/tab-select.png){width=600 zoomable="yes"}

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie als Administratoren hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

## Rollenressourcen

In der folgenden Liste werden die Ressourcen beschrieben, für die Standardrollen über die Berechtigung zum Zugriff innerhalb von Adobe Commerce Admin verfügen. Um die Standardberechtigungen für die einzelnen Rollen zu bearbeiten, navigieren Sie zu **System** > **Berechtigungen** > **Benutzerrollen** in Commerce Admin.

**Benutzer**

* Katalog
   * Inventar
      * PRODUCT
         * Produktpreis lesen

**Entwickler**

* Katalog
   * Inventar
      * PRODUCT
         * Produktpreis lesen
* System
   * Datenübertragung
      * Importverlauf
* Adobe IO-Ereigniskonfiguration
   * Konfigurationsprüfung
   * Ereignisanbieter erstellen
   * Konfigurationsaktualisierung
   * Ereignisse synchronisieren
   * Ereignisanbieterliste abrufen
* Eventing Framework
   * Ereignisliste
   * Eventing-Verbindung testen
   * Ereignis abonnieren
   * Abo von einem Ereignis kündigen
   * Ereignisstatus
   * API zum Abrufen von Ereignisabonnements
   * Admin-Benutzeroberfläche für Ereignisabonnements anzeigen
   * Admin-Benutzeroberfläche für Ereignisabonnements erstellen
   * Neue Ereignis-Admin-Benutzeroberfläche anfordern
* Webhooks
   * Webhooks für digitale Signatur
      * Webhooks - Einstellungen für digitale Signaturen
      * Webhooks - Generieren von Schlüsseln mit digitalen Signaturen
   * Webhooks-Verwaltung
      * Webhooks-Raster
      * Webhooks bearbeiten
      * Webhooks testen
      * Webhook-API abonnieren
      * API-Abo von Webhook kündigen
      * Webhooks-Liste
      * Neuen Webhook anfordern
      * Webhooks-Protokolle
      * Liste der Webhooks abrufen

**Administratoren**

Administratoren haben Zugriff auf alle Berechtigungen.
