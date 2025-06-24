---
title: Benutzerverwaltung
description: Erfahren Sie, wie Sie in Benutzer verwalten [!DNL Adobe Commerce Optimizer].
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 02758aa5cc14af6d46bfc4bb7865fa37a787d4cb
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Benutzerverwaltung

Um den Zugriff auf [!DNL Adobe Commerce Optimizer] zu aktivieren, fügen Sie Benutzer aus der [Adobe Admin Console ](https://adminconsole.adobe.com){target="_blank"} und stellen Sie sicher, dass sie Zugriff auf das Commerce-Produkt haben.

Sie können Benutzer einer der folgenden Rollen zuweisen:

- **Benutzer** - Benutzer haben Zugriff auf die [!DNL Adobe Commerce Optimizer]-Benutzeroberfläche, um Katalogansichten und Merchandising-Regeln anzuzeigen und zu verwalten und Leistungsmetriken zu verfolgen.

- [**Entwickler**](https://helpx.adobe.com/enterprise/using/manage-developers.html#Adddevelopers){target="_blank"} - Entwicklerinnen und Entwickler haben Benutzerberechtigungen und Zugriff auf die Adobe Developer Console. Das bedeutet, dass sie Projekte erstellen und Anmeldeinformationen konfigurieren können, um Entwickler-Tools wie die [!DNL Adobe Commerce Optimizer]-APIs und -SDKs zusammen mit Adobe-Erweiterbarkeits-Tools wie App Builder und API Mesh zu verwenden.

- **Admin** - Es gibt drei verschiedene Arten von Administratorrollen:
   - [Systemadmins](https://helpx.adobe.com/enterprise/using/admin-roles.html){target="_blank"} - Der Systemadmin hat über die Adobe Admin Console Zugriff auf alle Produkte und Produktprofile in der Organisation.
   - [Produktadministratoren](#add-a-product-admin) - Produktadministratoren können [Benutzer, Rollen und Berechtigungen für das Produkt verwalten](#add-users-and-admins) in der [!DNL Adobe Admin Console].
   - [Produktprofil-Administrierende](#add-users-developers-and-product-profile-admins) - Produktprofil-Administrierende können Benutzende für das Produkt in der [!DNL Adobe Admin Console] verwalten.

## Hinzufügen eines Produktadministrators

1. Navigieren Sie zur [Admin Console](https://adminconsole.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das [!UICONTROL **Adobe Commerce as a Cloud Service - Backend**] Produkt aus.

   ![Produkt auswählen](../cloud-service/assets/backend.png){width="600" zoomable="yes"}

1. Wählen Sie die Registerkarte [!UICONTROL **Administratoren**] aus.

1. Klicken Sie [!UICONTROL **Admin hinzufügen**].

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie als Administratoren hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

## Hinzufügen von Benutzern, Entwicklern und Produktprofil-Administrierenden

>[!BEGINSHADEBOX „Voraussetzungen“]
>
Die folgende Bereitstellung ist für die Benutzerverwaltung erforderlich:

- Für [!DNL Adobe Commerce Optimizer] bereitgestellte IMS-Organisation
- Ein Adobe Experience Cloud-Konto in derselben IMS-Organisation mit der System- oder Produktadministratorrolle

>[!ENDSHADEBOX]

Mit den folgenden Anweisungen können Sie Benutzer und Entwickler zum [!DNL Commerce Cloud Manager] hinzufügen, in dem Sie Ihre Commerce-Instanzen verwalten.

1. Navigieren Sie zu [Adobe Admin Console](https://adminconsole.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das [!UICONTROL **Adobe Commerce as a Cloud Service - Backend**] Produkt aus.

   ![Produkt auswählen](../cloud-service/assets/backend.png){width="600" zoomable="yes"}

1. Klicken Sie auf [!UICONTROL **Produktprofil**] Standard - Cloud Manager&quot;.

1. Wählen Sie die Registerkarte [!UICONTROL **Benutzer**], [!UICONTROL **Entwickler**] oder [!UICONTROL **Administratoren**] und klicken Sie auf [!UICONTROL **Benutzer hinzufügen**] oder [!UICONTROL **Entwickler hinzufügen**] oder [!UICONTROL **Administratoren hinzufügen**].

   Administratoren, die über diesen Bildschirm hinzugefügt werden, werden der Gruppe [Produktprofil-Administratoren](#understanding-roles) zugewiesen.

   ![Auswählen](../cloud-service/assets/tab-select.png){width=600 zoomable="yes"}

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie als Administratoren hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

## Massenbenutzerverwaltung

Sie können mit einer der folgenden Methoden mehrere Benutzer effizienter hinzufügen:

- Verwenden Sie die **Benutzer nach CSV hinzufügen** in der Adobe Admin Console, um einen [CSV-Massen-Upload](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html){target="_blank"} durchzuführen.
- Fügen Sie einer Rolle mehrere Benutzer hinzu, indem Sie eine [Benutzergruppe](https://helpx.adobe.com/enterprise/using/user-groups.html){target="_blank"} erstellen. Fügen Sie dann das Produkt [!UICONTROL **Adobe Commerce as a Cloud Service - Backend**] zur Benutzergruppe hinzu.

