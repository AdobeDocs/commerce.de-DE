---
title: Benutzer und Identity Management
description: Erfahren Sie, wie Sie Benutzer erstellen und verwalten und Benutzerrollen für [!DNL Adobe Commerce Optimizer] zuweisen.
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 9ab2118d-b7e3-4e2e-adac-8f3950fe1824
source-git-commit: b88406169191cb9d4f0d2b5ef113703f5afcd589
workflow-type: tm+mt
source-wordcount: '704'
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

>[!BEGINTABS]

>[!NOTE]
>
>Weisen Sie Produktadministratoren die Rolle &quot;[&quot; zu](#add-users) bevor Sie sie als Produktadministratoren hinzufügen. Die Benutzerrolle ist für grundlegende Commerce-Berechtigungen erforderlich.

>[!TAB GA (bereitgestellt nach dem 13. Oktober 2025)]

1. Navigieren Sie zu <https://adminconsole.adobe.com> und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie die [!UICONTROL **Benutzer**] aus.

1. Wählen Sie die Registerkarte [!UICONTROL **Administratoren**] aus.

1. Klicken Sie [!UICONTROL **Admin hinzufügen**].

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie als Admins hinzufügen möchten, und klicken Sie auf [!UICONTROL **Weiter**].

1. Wählen Sie die [!UICONTROL **Produktprofil-Administrator**]-Rolle aus.

1. Klicken Sie auf **+**, um Produkte hinzuzufügen.

1. Wählen Sie die bestehende Commerce Optimizer-Instanz aus, der der Administrator hinzugefügt werden soll. Commerce Optimizer-Instanzen verwenden das folgende Format: `Adobe Commerce - <instance-name> - ACO - <environment-type> - <tenant-id>`.

1. Wählen Sie das Produktprofil aus.

1. Klicken Sie [!UICONTROL **Apply**].

1. Klicken Sie [!UICONTROL **Speichern**].

>[!TAB Early access (bereitgestellt vor dem 13. Oktober 2025)]

1. Navigieren Sie zu <https://adminconsole.adobe.com> und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das Produkt [!UICONTROL **Adobe Commerce - Commerce Cloud**].

   ![Produkt auswählen](/help/cloud-service/assets/backend.png){width="600" zoomable="yes"}

1. Wählen Sie die Registerkarte [!UICONTROL **Administratoren**] aus.

1. Klicken Sie [!UICONTROL **Admin hinzufügen**].

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie als Administratoren hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

>[!ENDTABS]

## Benutzer hinzufügen

Mit den folgenden Anweisungen können Sie erfahren, wie Sie Benutzende zum [!DNL Commerce Cloud Manager] und Commerce Optimizer hinzufügen. Über die [!DNL Commerce Cloud Manager] können Sie Ihre Commerce Optimizer-Instanzen erstellen und verwalten. Dieser Prozess ist für alle Benutzer erforderlich, einschließlich Entwickler und Administratoren.

>[!NOTE]
>
>Nur Produkt- und Systemadministratoren können Benutzer und Entwickler zum Adobe Commerce Optimizer-Produkt hinzufügen.

>[!BEGINTABS]

>[!TAB GA (bereitgestellt nach dem 13. Oktober 2025)]

1. Navigieren Sie zu <https://adminconsole.adobe.com> und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie die Registerkarte [!UICONTROL **Produkte**] aus.

1. Wählen Sie das [!UICONTROL **Adobe Commerce**]-Produkt aus.

1. Wählen Sie das Commerce Cloud Manager-Produkt aus, wenn Sie den Anwender zur Benutzeroberfläche von Cloud Manager hinzufügen möchten, wo er Commerce Optimizer-Instanzen erstellen und verwalten kann, oder wählen Sie die vorhandene Commerce Optimizer-Instanz aus, um den Anwender hinzuzufügen. Commerce Optimizer-Instanzen verwenden das folgende Format: `Adobe Commerce - <instance-name> - ACO - <environment-type> - <tenant-id>`.

1. Wählen Sie die Registerkarte [!UICONTROL **Benutzer**] und klicken Sie auf [!UICONTROL **Benutzer hinzufügen**].

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

1. Wählen Sie das gewünschte Produktprofil aus.

1. Klicken Sie [!UICONTROL **Apply**].

1. Klicken Sie [!UICONTROL **Speichern**].

>[!TAB Early access (bereitgestellt vor dem 13. Oktober 2025)]

1. Navigieren Sie zu <https://adminconsole.adobe.com> und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das Produkt [!UICONTROL **Adobe Commerce - Commerce Cloud**].

   ![Produkt auswählen](/help/cloud-service//assets/backend.png){width="600" zoomable="yes"}

1. Klicken Sie auf [!UICONTROL **Produktprofil**] Standard - Cloud Manager&quot;.

1. Wählen Sie die Registerkarte [!UICONTROL **Benutzer**] und klicken Sie auf [!UICONTROL **Benutzer hinzufügen**].

   ![Auswählen](/help/cloud-service/assets/tab-select.png){width=600 zoomable="yes"}

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

>[!ENDTABS]

### Hinzufügen von Entwicklern und Produktprofil-Administrierenden

Um Entwickler und Produktprofil-Administrierende hinzuzufügen, wiederholen Sie den [Benutzer hinzufügen](#add-users), wählen Sie jedoch die Registerkarte [!UICONTROL ****] oder [!UICONTROL **Administratoren**] anstelle der Registerkarte [!UICONTROL **Benutzer**] aus.

>[!NOTE]
>
>Weisen Sie Entwicklern die Benutzerrolle zu, bevor Sie sie als Entwickler hinzufügen. Die Benutzerrolle ist für grundlegende Commerce-Berechtigungen erforderlich.

![Auswählen](/help//cloud-service/assets/tab-select.png){width=600 zoomable="yes"}

## Massenbenutzerverwaltung

Sie können mit einer der folgenden Methoden mehrere Benutzer effizienter hinzufügen:

- Verwenden Sie die **Benutzer nach CSV hinzufügen** in der Adobe Admin Console, um einen [CSV-Massen-Upload](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html){target="_blank"} durchzuführen.
- Fügen Sie einer Rolle mehrere Benutzer hinzu, indem Sie eine [Benutzergruppe](https://helpx.adobe.com/enterprise/using/user-groups.html){target="_blank"} erstellen. Fügen Sie dann das Produkt [!UICONTROL **Adobe Commerce - Commerce Cloud Manager**] zur Benutzergruppe hinzu.

## Identitätsverwaltung und Single-Sign-on-Konfiguration

{{ims-identity-and-sso-config}}
