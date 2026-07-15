---
title: Konfigurieren des AEM Assets-Projekts
description: Erfahren Sie, wie Sie Assets zwischen Adobe Commerce und AEM Assets synchronisieren, indem Sie das Asset-Commerce-Paket bereitstellen und Commerce-Metadaten in Ihrem AEM-Projekt konfigurieren.
feature: CMS, Media, Integration
exl-id: a5d2cbab-5ea1-446b-8ab2-2c638128a40c
TQID: https://experienceleague.adobe.com/QPlM-eeRjJ0gwmpGO4SSYR4PLtL97O-NeozWorDWtv0
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: da3860b0-d637-47df-bef0-273751180266
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 0c2e50338cbf286704239b6d1f628180e85a3bef
workflow-type: tm+mt
source-wordcount: 1741
ht-degree: 1%

---

# Konfigurieren des AEM Assets-Projekts

In diesem Abschnitt wird beschrieben, wie Sie Ihr AEM Assets-Projekt so konfigurieren, dass der Commerce-Namespace, das Metadatenschema und [!UICONTROL Commerce] Registerkarte in der Authoring-Umgebung von AEM verfügbar sind. Hintergrundinformationen zu diesen Ressourcen finden Sie unter [Commerce-Metadaten in AEM Assets](../metadata.md).

Sie haben zwei Möglichkeiten, das AEM Assets-Projekt zu konfigurieren:

* [!BADGE Empfohlen]{type=Positive} **Self-Service-Onboarding** - Aktivieren Sie in AEM-Versionen `2026.5.26309` und höher die Integration in Cloud Manager, indem Sie eine Umgebungsvariable festlegen und Dynamic Media mit OpenAPI-Funktionen aktivieren. Es ist kein benutzerdefinierter Code erforderlich. Siehe [Aktivieren der Commerce-Integration (Self-Service)](#enable-aem-commerce-self-service).

* **Manuelle Konfiguration** - Stellen Sie das `assets-commerce`-Paket über eine Cloud Manager-Pipeline bereit. Verwenden Sie diese manuellen Schritte, wenn Sie benutzerdefinierten Paket-Code bereitstellen müssen oder wenn Sie eine AEM-Version vor `2026.5.26309` verwenden. Siehe [Manuelles Installieren des Assets-Commerce-Pakets](#install-the-assets-commerce-package-manually).

>[!TIP]
>
>Sie können die aktuelle AEM-Version über das Menü oben rechts überprüfen: **[!UICONTROL Help]** > **[!UICONTROL About AEM]**.

## Aktivieren der Commerce-Integration (Self-Service) {#enable-aem-commerce-self-service}

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} AEM-Version `2026.5.26309` und höher.

In unterstützten AEM-Versionen aktivieren Sie die Commerce-Integration von Cloud Manager aus, ohne benutzerdefinierten Code bereitzustellen. Der Commerce-Namespace, das Metadatenschema und die Registerkarte **[!UICONTROL Commerce]** werden automatisch bereitgestellt, wenn Sie die Integration im Autoren-Service aktivieren.

### Voraussetzungen für den Self-Service

* [Zugriff auf das AEM Cloud Manager-Programm und Umgebungen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager#access-sysadmin-bo) mit den Rollen „Programm“ und „Bereitstellungs-Manager“

* Ein AEM-Programm ab Version `2026.5.26309`.

* Die **IMS-Org-ID** für Ihre Commerce-Instanz.

  Sowohl Ihre Commerce-Instanz als auch die Authoring-Umgebung von AEM Assets müssen sich in derselben IMS-Organisation befinden.

### Schritt 1: Erstellen des Programms und der Umgebungen

Das Erstellen eines Programms in Cloud Manager ist ein einzelner Assistentenprozess: Das Programm und seine Umgebungen werden in mehreren Schritten konfiguriert und am Ende gemeinsam gespeichert.

1. Wählen Sie in Cloud Manager **[!UICONTROL Add Program]** aus.

1. Klicken Sie auf **[!UICONTROL Set up for production]**, geben Sie einen Programmnamen ein und klicken Sie auf **[!UICONTROL Continue]**.

1. Wählen Sie im **[!UICONTROL Solutions & Add-ons]** Schritt die Lösungen und Add-ons aus, die für Ihr Projekt erforderlich sind, einschließlich **[!UICONTROL Dynamic Media]**, und wählen Sie dann **[!UICONTROL Continue]** aus.

   ![Schritt &quot;Cloud Manager-Lösungen und -Add-ons“ mit ausgewähltem Dynamic Media](../assets/aem-cloud-manager-program-addons.png){width="600" zoomable="yes"}

1. Geben Sie im **[!UICONTROL Add Environment]** Schritt Namen für die Umgebungen **Produktion** und **Staging** ein und wählen Sie dann eine Region aus.

   ![Dialogfeld &quot;Cloud Manager-Umgebung hinzufügen“ mit Produktions- und Staging-Details](../assets/aem-cloud-manager-add-environment.png){width="600" zoomable="yes"}

1. Wählen Sie **[!UICONTROL Save]** aus, um das Programm mit seinen Umgebungen zu erstellen.

### Schritt 2: Commerce-Integrationsvariable aktivieren

Öffnen Sie in Cloud Manager die in Schritt 1 erstellte Umgebung und dann:

1. Wählen Sie die Registerkarte **[!UICONTROL Configuration]** aus.

1. Fügen Sie eine Umgebungsvariable mit den folgenden Werten hinzu und wählen Sie dann **[!UICONTROL Add]** und **[!UICONTROL Save]** aus:

   | Feld | Wert |
   |---|---|
   | Name | `COMMERCE_INTEGRATION_ENABLED` |
   | Wert | `true` |
   | Service angewendet | Autor |
   | Typ | Variable |

   ![Cloud Manager-Umgebungskonfiguration mit der COMMERCE_INTEGRATION_ENABLED-Variable, die auf den Autoren-Service angewendet wird](../assets/aem-cloud-manager-commerce-integration-variable.png){width="600" zoomable="yes"}

   Die Umgebung wird aktualisiert, um die Konfiguration anzuwenden. Warten Sie, bis der Umgebungsstatus zu **[!UICONTROL Running]** zurückkehrt.

### Schritt 3: Aktivieren von Dynamic Media mit OpenAPI-Funktionen

1. Suchen Sie auf der Registerkarte **[!UICONTROL General]** nach **[!UICONTROL Dynamic Media]**.

1. Wählen Sie neben *OpenAPI-Funktionen sind verfügbar* die Option **[!UICONTROL Click to activate]**.

   ![Registerkarte „Umgebung - Allgemein“ mit dem Link zur Dynamic Media OpenAPI-Aktivierung](../assets/aem-cloud-manager-dynamic-media-activate.png){width="600" zoomable="yes"}

   Die Aktivierung erfolgt im Hintergrund. Nach Abschluss des Vorgangs ist die Umgebung für die Commerce-Integration bereit.

   >[!NOTE]
   >
   > Wenn **[!UICONTROL Click to activate]** nicht verfügbar ist, öffnen Sie ein Support-Ticket, um Dynamic Media mit OpenAPI-Funktionen zu aktivieren.

### Schritt 4: Validieren der Konfiguration

Wechseln Sie zur **AEM Assets-Autorenumgebung** und öffnen Sie ein beliebiges Asset. Bearbeiten Sie die Eigenschaften und vergewissern Sie sich, dass das Standard-Metadatenschema die Registerkarte **[!UICONTROL Commerce]** enthält und dass die Felder **[!UICONTROL Product Data]** und **[!UICONTROL Eligible for Commerce]** sichtbar sind.

## Installieren Sie das Paket assets-commerce manuell

>[!NOTE]
>
> Verwenden Sie diese manuelle Methode, um benutzerdefinierten Paket-Code bereitzustellen, oder wenn Sie AEM-Versionen vor `2026.5.26309` verwenden. Verwenden Sie in unterstützten Versionen [Aktivieren der Commerce-Integration (Self-Service)](#enable-aem-commerce-self-service).

### Voraussetzungen

Um den `assets-commerce`-Code in der AEM Assets as a Cloud Service AEM-Umgebung bereitzustellen, benötigen Sie die folgenden Ressourcen und Berechtigungen:

* [Zugriff auf das AEM Assets Cloud Manager-Programm und Umgebungen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager#access-sysadmin-bo) mit den Rollen „Programm“ und „Bereitstellungs-Manager“

* eine [lokale AEM-Entwicklungsumgebung](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview) und die Vertrautheit mit dem lokalen AEM-Entwicklungsprozess.

* Machen Sie sich mit der [AEM](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure)Projektstruktur und der Bereitstellung benutzerdefinierter Inhaltspakete mit Cloud Manager vertraut.

* Die **IMS-Org-ID** für Ihre Commerce-Instanz. Sowohl Ihre Commerce-Instanz als auch die Authoring-Umgebung von AEM Assets müssen sich in derselben IMS-Organisation befinden.

* So aktivieren Sie [Dynamic Media mit OpenAPI-Funktionen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview#enable-dynamic-media-open-apis):

>[!BEGINTABS]

>[!TAB Produktvisualisierung]

[!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} Dynamic Media mit OpenAPI-Funktionen ist ein Self-Service für Produktvisualisierungen mit AEM Assets.

1. Navigieren Sie zu Ihrer Cloud Manager.

1. Wählen Sie die gewünschte Umgebung aus.

1. Aktivieren Sie **Dynamic Media mit OpenAPI-Funktionen**.

   Wenn die Schaltfläche **Dynamic Media mit OpenAPI** Funktionen nicht aktiv ist, öffnen Sie ein Support-Ticket.

>[!TAB AEM Assets]

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} Senden Sie auf AEM as a Cloud Service ein Adobe-Support-Ticket mit diesen Informationen:

* Bezeichnung: Aktivieren der vollständigen Integration von Adobe Commerce mit AEM Assets durch Dynamic Media OpenAPI

   * Inhalt des Support-Tickets:

      * **[!UICONTROL AEM Program ID]**
      * **[!UICONTROL Adobe Commerce URL]**
      * **[!UICONTROL AEM Environment ID]**
      * **[!UICONTROL IMS Org ID]**

Sobald Sie das Support-Ticket gesendet haben, aktiviert Adobe Dynamic Media mit OpenAPI-Funktionen in Ihrer Cloud Services-Umgebung und gibt die Details wie die IMS-Client-ID frei, damit Sie mit der Integration fortfahren können.

>[!ENDTABS]

### Installationsschritte

1. Gehen Sie zur AEM Cloud Manager, wählen Sie ein Programm aus und erstellen [Produktions- und Staging-Umgebungen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/create-environments#creating-environments) die Sie in Adobe Commerce integrieren möchten.

1. [Klonen Sie das in Adobe verwaltete Git](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/administering/site-creation/quick-site/retrieve-access#repo-access)Repository für das ausgewählte Programm.

   ![Cloud Manager-Repository-Anmeldeinformationen und Klonbefehl](../assets/cloud-manager-repository-info.png){width="600" zoomable="yes"}

   Wählen Sie in **Pipelines** die Option **[!UICONTROL Access Repo Info]** aus, um **[!UICONTROL Repository Info]** zu öffnen. Kopieren Sie den **[!UICONTROL URL]**- oder **[!UICONTROL Git command line]**, generieren Sie bei Bedarf ein Zugriffskennwort und klonen Sie es dann lokal mit Ihrem Git-Client.

1. Laden Sie von GitHub den Paket-Code aus dem [AEM Assets Commerce-Repository](https://github.com/ankumalh/assets-commerce) herunter.

1. Kopieren Sie [lokalen AEM-](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview)) den heruntergeladenen Code manuell in das bestehende von Adobe verwaltete Repository.

1. Ersetzen Sie in allen `filter.xml` und `pom.xml` Dateien für Ihr Projekt alle Vorkommen von &lt;my-app> durch Ihren App-Namen.

   >[!NOTE]
   >
   > Alternativ können Sie den benutzerdefinierten Code in Ihrer AEM Assets-Projektkonfiguration als Maven **Paket**.

1. Übertragen Sie die Änderungen und pushen Sie Ihre lokale Entwicklungsverzweigung in das Cloud Manager-Git-Repository.

1. Konfigurieren Sie eine [Bereitstellungs-Pipeline](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/administering/site-creation/quick-site/pipeline-setup#create-front-end-pipeline) oder stellen Sie sicher, dass Ihre Pipeline Änderungen an der ausgewählten Umgebung bereitstellen kann.

   ![Cloud Manager-Pipelines](../assets/cloud-manager-pipelines.png){width="600" zoomable="yes"}

   Wenn die Pipeline vorhanden ist, öffnen Sie das Menü Aktionen (**…**) Informationen zum **[!UICONTROL Run]**, **[!UICONTROL Edit]**, **[!UICONTROL View/Edit variables]** oder anderen Aktionen finden Sie in der oben verlinkten Dokumentation zur Cloud Manager-Pipeline.

1. Aktualisieren Sie in AEM Cloud Manager [die AEM-Umgebung, indem Sie die Pipeline verwenden, um Ihren Code bereitzustellen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code#deploying-code-with-cloud-manager).

1. Gehen Sie zu einem beliebigen Asset und bearbeiten Sie dessen Eigenschaften, um die Änderungen zu validieren:

   * Das Standard-Metadatenschema umfasst die Registerkarte **Commerce** .

   * Produkt-SKUs und die `Eligible for Commerce` Felder sind sichtbar.

### Registerkarte &quot;Commerce&quot; ist in den Eigenschaften nicht sichtbar

Wenn die Registerkarte **Commerce** nicht in den Eigenschaften angezeigt wird, müssen Sie die folgenden Schritte im Metadatenschema-Editor manuell ausführen:

1. Navigieren Sie zum Metadatenschema-Editor.

1. Wählen Sie **Bearbeiten** aus, um das Standard-Metadatenschema-Formular zu ändern.

1. Erstellen Sie eine **Commerce**-Registerkarte und wählen Sie sie aus.

1. Ziehen Sie die Komponente **Produkt** in die Registerkarte **Commerce** und ordnen Sie sie der `commerce:skus` zu.

1. Aktivieren Sie das Kontrollkästchen für **Rollen anzeigen** und **Reihenfolge anzeigen**.

1. Ziehen Sie eine **checkbox**-Komponente per Drag-and-Drop auf die Registerkarte {2 **Commerce} und ordnen Sie sie der `commerce:isCommerce` zu.** Definieren Sie **Ja** und **Nein** als Optionen.

Wenn Sie auf andere Probleme stoßen, erstellen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) oder wenden Sie sich an Ihren AEM Assets Integration-Vertriebsmitarbeiter, um Hilfe zu erhalten.

## Konfigurieren eines Metadatenprofils (optional)

Legen Sie in der AEM Assets-Autorenumgebung Standardwerte für Commerce-Asset-Metadaten fest, indem Sie ein Metadatenprofil erstellen. Um diese Standardwerte automatisch zu verwenden, wenden Sie das neue Profil auf AEM Asset-Ordner an. Diese Konfiguration optimiert die Asset-Verarbeitung durch Reduzierung manueller Schritte.

Beim Konfigurieren des Metadatenprofils müssen Sie nur die folgenden Komponenten konfigurieren:

* Fügen Sie eine Registerkarte Commerce hinzu. Diese Registerkarte ermöglicht Commerce-spezifische Konfigurationseinstellungen, die von der Vorlage hinzugefügt werden.

* Fügen Sie das Feld `Eligible for Commerce` zur Registerkarte Commerce hinzu.

Die Komponente Produktdaten-Benutzeroberfläche wird automatisch auf Grundlage der Vorlage hinzugefügt.

### Definieren des Metadatenprofils

1. Melden Sie sich bei der Adobe Experience Manager-Autorenumgebung an.

1. Navigieren Sie im Adobe Experience Manager-Arbeitsbereich zum Arbeitsbereich für die Inhaltsverwaltung in AEM Assets durch Klicken auf das Adobe Experience Manager-Symbol.

   ![AEM Assets-Authoring](../assets/aem-assets-authoring.png){width="600" zoomable="yes"}

1. Öffnen Sie die Administrator-Tools, indem Sie auf das Hammersymbol klicken.

   ![AEM-Autoren-Admin zur Verwaltung von Metadatenprofilen](../assets/aem-manage-metadata-profiles.png){width="600" zoomable="yes"}

1. Öffnen Sie die Seite Profilkonfiguration , indem Sie auf **[!UICONTROL Metadata Profiles]** klicken.

1. **[!UICONTROL Create]** eines Metadatenprofils für die Commerce-Integration.

   ![AEM-Autoren-Admin fügt Metadatenprofile hinzu](../assets/aem-create-metadata-profile.png){width="600" zoomable="yes"}

1. Fügen Sie eine Registerkarte für Commerce-Metadaten hinzu.

   1. Klicken Sie links auf **[!UICONTROL Settings]**.

   1. Klicken Sie im Abschnitt Registerkarte auf **[!UICONTROL +]** und geben Sie dann die **[!UICONTROL Tab Name]** an, `Commerce`.

1. Fügen Sie das Feld `Eligible for Commerce` zum Formular hinzu.

   ![AEM-Autoren-Admin fügt Metadatenfelder zum Profil hinzu](../assets/aem-edit-metadata-profile-fields.png){width="600" zoomable="yes"}

   * Klicken Sie auf **[!UICONTROL Build form]**.

   * Ziehen Sie das `Single Line text` Feld in das Formular.

   * Fügen Sie den `Eligible for Commerce` Text für die Bezeichnung hinzu, indem Sie auf **[!UICONTROL Field Label]** klicken.

   * Fügen Sie auf der Registerkarte Einstellungen den Titeltext zu **Feldbezeichnung“**.

   * Setzen Sie den Platzhaltertext auf `yes`.

   * Kopieren Sie den folgenden Wert in das Feld **[!UICONTROL Map to Property]** und fügen Sie ihn ein

     ```terminal
     ./jcr:content/metadata/commerce:isCommerce
     ```

1. Optional. Um genehmigte Commerce-Assets beim Hochladen in die AEM Assets-Umgebung automatisch zu synchronisieren, setzen Sie den Standardwert für das _[!UICONTROL Review Status]_&#x200B;auf der Registerkarte `Basic` auf `approved`.

1. Speichern Sie die Aktualisierung.

### Anwenden des Metadatenprofils auf den Commerce Assets-Quellordner

1. Wählen Sie auf der Seite **[!UICONTROL Metadata Profiles]** das Integrationsprofil Commerce aus.

1. Wählen Sie im Menü Aktion die Option **[!UICONTROL Apply Metadata Profiles to Folders]** aus.

1. Wählen Sie den Ordner aus, der Commerce-Assets enthält.

   Erstellen Sie einen Commerce-Ordner, wenn er noch nicht vorhanden ist.

1. Wählen Sie **[!UICONTROL Apply]** aus.

## Nächste Schritte

* [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} [Adobe Commerce-Pakete installieren](configure-commerce.md).

* [!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} [Konfigurieren der Integration über den Administrator](setup-synchronization.md).
