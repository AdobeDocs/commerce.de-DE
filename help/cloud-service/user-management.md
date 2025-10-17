---
title: Benutzerverwaltung
description: Erfahren Sie, wie Sie in Benutzer verwalten [!DNL Adobe Commerce as a Cloud Service].
exl-id: 9bc80fe6-6dfd-4bb3-8dc5-d5efd8a8d90c
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Admin
source-git-commit: 06db1063d745d83c99459fc82e4ba76fb8935da7
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 0%

---

# Benutzer und Identity Management

Wenn Sie möchten, dass Benutzer auf den Admin in [!DNL Adobe Commerce as a Cloud Service] zugreifen, müssen Sie sie als Benutzer in Ihrer Organisation hinzufügen und sicherstellen, dass sie Zugriff auf das Cloud Service-Produkt in der [Adobe Admin Console haben](https://adminconsole.adobe.com){target="_blank"}.

Für diesen Prozess ist eine IMS-Organisation mit Zugriff auf [!DNL Adobe Commerce as a Cloud Service] erforderlich. Nur ein Systemadministrator oder Produktadministrator für das Unternehmen kann diese Prozesse durchführen.

>[!TIP]
>
>Um mehrere Benutzer gleichzeitig hinzuzufügen, können Sie einen [CSV-Upload](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html){target="_blank"} durchführen.
>
> Sie können einer Rolle auch mehrere Benutzer hinzufügen, indem Sie eine [Benutzergruppe](https://helpx.adobe.com/de/enterprise/using/user-groups.html){target="_blank"} erstellen. Anschließend können Sie das Produkt [!UICONTROL **Adobe Commerce - Commerce Cloud Manager**] zur Benutzergruppe hinzufügen.

## Grundlegendes zu Rollen

Die folgenden Rollen sind für [!DNL Adobe Commerce as a Cloud Service] verfügbar. Um diese Rollen anzuzeigen oder zu bearbeiten, navigieren Sie in der Commerce-Admin zu **System** > **Berechtigungen** > **Benutzerrollen**.

* **Benutzer**: Benutzer haben Administratorzugriff auf Commerce Admin, können jedoch nicht den Zugriff auf Produktebene in Admin Console verwalten. Benutzer können auch Punktzahlen verwenden, um [&#x200B; Instanzen &#x200B;](./getting-started.md#create-an-instance) der [!DNL Commerce Cloud Manager] zu erstellen.

  >[!NOTE]
  >
  >Allen Commerce-Benutzern, einschließlich Entwicklern und Administratoren, muss ebenfalls die Benutzerrolle zugewiesen sein. Sie ist für grundlegende Commerce-Berechtigungen erforderlich.

* [**Entwickler**](https://helpx.adobe.com/de/enterprise/using/manage-developers.html#Adddevelopers){target="_blank"} Entwickler verfügen über Benutzerberechtigungen und werden der Commerce-Instanz als Entwicklerbenutzer hinzugefügt. Das bedeutet, dass sie die [Admin-Benutzeroberfläche SDK](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/){target="_blank"} verwenden [Ereignisse konfigurieren](https://developer.adobe.com/commerce/extensibility/events/){target="_blank"} und [Webhooks erstellen](https://developer.adobe.com/commerce/extensibility/webhooks/){target="_blank"}.

* Administratoren : Es gibt drei verschiedene Arten von Administratoren:
   * [Systemadmins](https://helpx.adobe.com/de/enterprise/using/admin-roles.html){target="_blank"} - Der Systemadmin hat über die Admin Console Zugriff auf alle Produkte und Produktprofile in der Organisation.
   * [Produktadministrierende](#add-a-product-admin) - Produktadministrierende können [Benutzende, Rollen und Berechtigungen für das Produkt verwalten](#add-users) in der [!DNL Adobe Admin Console] und [Benutzende im Commerce Admin verwalten](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/user-accounts/permissions-users-all#create-a-user){target="_blank"}.
   * [Produktprofil-Administrierende](#add-developers-and-product-profile-admins) - Produktprofil-Administrierende haben keinen Zugriff auf den Adobe Commerce-Admin, können jedoch Benutzende für das Produkt im [!DNL Adobe Admin Console] verwalten.

Ausführliche Informationen zu den Berechtigungen, die den einzelnen Rollen in Adobe Commerce gewährt werden, finden Sie unter [Benutzerberechtigungen](#user-permissions).

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

1. Wählen Sie die bestehende Commerce-Instanz aus, der der Administrator hinzugefügt werden soll. Commerce-Instanzen verwenden das folgende Format: `Adobe Commerce - <instance-name> - ACCS - <environment-type> - <tenant-id>`.

1. Wählen Sie das Produktprofil aus.

1. Klicken Sie [!UICONTROL **Apply**].

1. Klicken Sie [!UICONTROL **Speichern**].

>[!TAB Early access (bereitgestellt vor dem 13. Oktober 2025)]

1. Navigieren Sie zu <https://adminconsole.adobe.com> und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das Produkt [!UICONTROL **Adobe Commerce - Commerce Cloud**].

   ![Produkt auswählen](./assets/backend.png){width="600" zoomable="yes"}

1. Wählen Sie die Registerkarte [!UICONTROL **Administratoren**] aus.

1. Klicken Sie [!UICONTROL **Admin hinzufügen**].

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie als Administratoren hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

>[!ENDTABS]

## Benutzer hinzufügen

Die folgenden Anweisungen enthalten Informationen zum Hinzufügen von Benutzern zur [!DNL Commerce Cloud Manager] und zur Commerce Admin. Über die [!DNL Commerce Cloud Manager] können Sie Ihre Commerce-Instanzen erstellen und verwalten. Dieser Prozess ist für alle Benutzer erforderlich, einschließlich Entwickler und Administratoren.

>[!NOTE]
>
>Nur Produkt- und Systemadministratoren können Benutzer und Entwickler zum Adobe Commerce as a Cloud Service-Produkt hinzufügen.

>[!BEGINTABS]

>[!TAB GA (bereitgestellt nach dem 13. Oktober 2025)]

1. Navigieren Sie zu <https://adminconsole.adobe.com> und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie die Registerkarte [!UICONTROL **Produkte**] aus.

1. Wählen Sie das [!UICONTROL **Adobe Commerce**]-Produkt aus.

1. Wählen Sie das Commerce Cloud Manager-Produkt aus, wenn Sie den Anwender zur Benutzeroberfläche von Cloud Manager hinzufügen möchten, wo er Commerce-Instanzen erstellen und verwalten kann, oder wählen Sie die vorhandene Commerce-Instanz aus, um den Anwender hinzuzufügen. Commerce-Instanzen verwenden das folgende Format: `Adobe Commerce - <instance-name> - ACCS - <environment-type> - <tenant-id>`.

1. Wählen Sie die Registerkarte [!UICONTROL **Benutzer**] und klicken Sie auf [!UICONTROL **Benutzer hinzufügen**].

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

1. Wählen Sie das gewünschte Produktprofil aus.

1. Klicken Sie [!UICONTROL **Apply**].

1. Klicken Sie [!UICONTROL **Speichern**].

>[!TAB Early access (bereitgestellt vor dem 13. Oktober 2025)]

1. Navigieren Sie zu <https://adminconsole.adobe.com> und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das Produkt [!UICONTROL **Adobe Commerce - Commerce Cloud**].

   ![Produkt auswählen](./assets/backend.png){width="600" zoomable="yes"}

1. Klicken Sie auf [!UICONTROL **Produktprofil**] Standard - Cloud Manager&quot;.

1. Wählen Sie die Registerkarte [!UICONTROL **Benutzer**] und klicken Sie auf [!UICONTROL **Benutzer hinzufügen**].

   ![Auswählen](./assets/tab-select.png){width=600 zoomable="yes"}

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie hinzufügen möchten, und klicken Sie auf [!UICONTROL **Speichern**].

>[!ENDTABS]

### Hinzufügen von Entwicklern und Produktprofil-Administrierenden

Um Entwickler und Produktprofil-Administrierende hinzuzufügen, wiederholen Sie den [Benutzer hinzufügen](#add-users), wählen Sie jedoch die Registerkarte [!UICONTROL **&#x200B;**] oder [!UICONTROL **Administratoren**] anstelle der Registerkarte [!UICONTROL **Benutzer**] aus.

>[!NOTE]
>
>Produktprofil-Administrierende haben keinen Zugriff auf Commerce Admin. Weitere Informationen finden [&#x200B; unter &#x200B;](#understanding-roles) von Rollen .
>
>Weisen Sie Entwicklern die Benutzerrolle zu, bevor Sie sie als Entwickler hinzufügen. Die Benutzerrolle ist für grundlegende Commerce-Berechtigungen erforderlich.

![Auswählen](./assets/tab-select.png){width=600 zoomable="yes"}

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

## Hinzufügen von Benutzenden zu AEM Assets oder Produktbildern

Die folgende Einrichtung ist für [!DNL Adobe Experience Manager Assets] und [!DNL Product Visuals powered by AEM Assets] Benutzer erforderlich.

Wenn Ihr Konto Zugriff auf [Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service) hat und Sie einem Benutzer den Zugriff auf die erweiterten Funktionen von [AEM Assets](https://experienceleague.adobe.com/de/docs/commerce/aem-assets-integration/overview){target="_blank"} zusammen mit [!DNL Adobe Commerce as a Cloud Service] ermöglichen möchten, verwenden Sie den folgenden Prozess:

>[!NOTE]
>
>Benutzende ohne entsprechende Asset-Berechtigungen können nicht auf erweiterte Funktionen von [!DNL AEM Assets] zugreifen, wie [KI-](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/generative-ai/generative-ai-in-aem){target="_blank"}, [generierte Varianten](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/generative-ai/generate-variations-integrated-editor){target="_blank"} und mehr.

>[!TIP]
>
>Um mehrere Benutzer gleichzeitig hinzuzufügen, können Sie einen [CSV-Upload](https://helpx.adobe.com/de/enterprise/using/bulk-upload-users.html){target="_blank"} durchführen.
>
>Sie können einer Rolle auch mehrere Benutzer hinzufügen, indem Sie eine [Benutzergruppe](https://helpx.adobe.com/de/enterprise/using/user-groups.html){target="_blank"} erstellen. Anschließend können Sie das Produkt [!UICONTROL **Adobe Experience Manager as a Cloud Service - Cloud Manager**] zur Benutzergruppe hinzufügen.

1. Navigieren Sie zu <https://adminconsole.adobe.com> und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie Ihre Organisation aus.

1. Wählen Sie auf [!UICONTROL **Registerkarte**] Produkte [!UICONTROL **unter „Produkte und**]&quot; das Produkt [!UICONTROL **Adobe Experience Manager as a Cloud Service - Cloud Manager**].

   ![Produkt auswählen](./assets/backend-aem.png){width="600" zoomable="yes"}

1. Wählen Sie die [!UICONTROL **Benutzer**] aus.

1. Klicken Sie [!UICONTROL **Benutzer hinzufügen**].

1. Geben Sie den Benutzernamen oder die E-Mail-Adresse der Benutzer ein, die Sie hinzufügen möchten.

1. Klicken Sie [!UICONTROL **Produkt hinzufügen**].

1. Wählen Sie die folgenden Produktprofile aus, die für die Integration von AEM Assets mit Commerce erforderlich sind:

   * Geschäftsinhaber - Erforderlich zum Erstellen und Verwalten von Programmen.
   * Bereitstellungs-Manager - Erforderlich zum Bereitstellen von Code aus Ihren Repositorys für AEM.

   Wenn Sie einen Entwickler hinzufügen, der keinen Zugriff auf die Cloud Manager- oder Experience Manager-Benutzeroberflächen benötigt, können Sie ihm stattdessen die Entwicklerrolle zuweisen.

   >[!NOTE]
   >
   >Weitere Informationen dazu, wie sich diese Berechtigungen auf Ihren Zugriff auf AEM Assets auswirken, finden Sie unter [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/concepts/aem-cs-team-product-profiles#cloud-manager-product-profiles){target="_blank"}.

1. Klicken Sie [!UICONTROL **Apply**].

1. Klicken Sie [!UICONTROL **Speichern**].

Um zu bestätigen, dass der Benutzer Zugriff hat, klicken Sie auf den Namen des Benutzers, um dessen Profilseite zu öffnen. Im Abschnitt [!UICONTROL **Produkte**] sollte es &quot;[!UICONTROL **&quot;**] das Produkt [!UICONTROL **Adobe Experience Manager as a Cloud Service - Cloud Manager**] lauten. Es kann einige Sekunden dauern, nachdem der/die Benutzende hinzugefügt wurde, bis der Status in seinem/ihrem Profil aktualisiert wird. Aktualisieren Sie die Seite, um den aktualisierten Status anzuzeigen.

![Produktzugriff](./assets/product-access.png){width="600" zoomable="yes"}

## Zugriff auf die Experience Manager-Benutzeroberfläche

Nachdem ein(e) Benutzende(r) zu AEM Assets hinzugefügt wurde, kann er/sie auf die [!DNL Experience Manager] zugreifen, indem er/sie zu [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"} navigiert.

1. Klicken Sie im [!UICONTROL **Schnellzugriff**]-Abschnitt auf [!UICONTROL **Experience Manager**] oder klicken Sie auf [!UICONTROL **Alle anzeigen**] wenn [!UICONTROL **Experience Manager nicht angezeigt**]. Klicken Sie dann auf [!UICONTROL **Cloud Manager**] oder navigieren Sie direkt zu [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}.

1. Cloud Manager Klicken Sie auf der Seite [!UICONTROL **&#x200B;**] auf [!UICONTROL **Programm hinzufügen**], um zu beginnen.

1. [Erstellen Sie ein neues Programm](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/create-program){target="_blank"}.

1. [Erstellen einer neuen Umgebung](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/screens-as-cloud-service/onboarding-screens-cloud/creating-an-environment){target="_blank"}.

1. Kehren Sie nach dem Erstellen der Umgebung zur [Admin Console](https://adminconsole.adobe.com){target="_blank"} zurück und wählen Sie [!UICONTROL **Adobe Experience Manager as a Cloud Service**].

1. Es sollten jetzt neue Produktprofile angezeigt werden. Wählen Sie aus, das `- author -` enthält. Beispiel: `<environment-name> - author - <program-id> - <environment-id>`.

1. [Hinzufügen von Benutzern zum Produktprofil](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/users-and-roles){target="_blank"}.

* [Konfigurieren von AEM Assets zur Unterstützung von Commerce-Metadaten](https://experienceleague.adobe.com/de/docs/commerce/aem-assets-integration/get-started/configure-aem)
* [Integrieren von AEM Assets mit Commerce für die Synchronisierung von Assets](https://experienceleague.adobe.com/de/docs/commerce/aem-assets-integration/get-started/setup-synchronization)

## Identitätsverwaltung und Single-Sign-on-Konfiguration

{{ims-identity-and-sso-config}}

