---
title: Konfigurieren des AEM Assets-Projekts zur Unterstützung von Commerce-Metadaten
description: Aktivieren Sie die nahtlose Synchronisierung von Assets zwischen Adobe Commerce und AEM Assets, indem Sie die erforderlichen Metadaten für die Integration hinzufügen.
feature: CMS, Media, Integration
exl-id: a5d2cbab-5ea1-446b-8ab2-2c638128a40c
source-git-commit: d426c7878f7a66fe1047673be7c5bf65ae1949a7
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 0%

---

# Konfigurieren des AEM Assets-Projekts zur Unterstützung von Commerce-Metadaten

Wenn Sie AEM Assets als DAM (Digital Asset Management System) für Commerce verwenden, können Sie nach der Installation des `assets-commerce`-Pakets Bilder und Videos für Commerce-Produkte aus der AEM-Autorenumgebung verwalten.

Führen Sie die folgenden Schritte aus, um das AEM Assets-Projekt mit dem erforderlichen Paket-Code und den erforderlichen Metadaten für die Verwaltung von Commerce-Assets aus der AEM-Autorenumgebung zu konfigurieren:

1. [Weitere Informationen zu &#x200B;](#aem-commerce-assets-commerce-package-contents)

1. [Führen Sie die Installationsschritte aus, um das AEM Assets-Projekt zur Unterstützung von Commerce-Metadaten zu konfigurieren](#step-1-install-the-assets-commerce-package)

## Paketinhalte **AEM Commerce** assets-commerce

Adobe bietet eine AEM Commerce Package-Code-`assets-commerce` zum Hinzufügen von Commerce-Namespace- und Metadatenschema-Ressourcen zur Experience Manager Assets as a Cloud Service-Umgebungskonfiguration.

Dieser Paket-Code fügt die folgenden Ressourcen zur Authoring-Umgebung von AEM Assets hinzu:

* Ein [benutzerdefinierter Namespace](https://github.com/ankumalh/assets-commerce/blob/main/ui.config/jcr_root/apps/commerce/config/org.apache.sling.jcr.repoinit.RepositoryInitializer~commerce-namespaces.cfg.json), der zur Identifizierung von Commerce-bezogenen Eigenschaften `Commerce`.

   * Ein benutzerdefinierter Metadatentyp `commerce:isCommerce` mit der Bezeichnung `Eligible for Commerce`, um mit einem Adobe Commerce-Projekt verknüpfte Commerce-Assets zu taggen.

   * Ein benutzerdefinierter Metadatentyp `commerce:skus` und eine entsprechende UI-Komponente, um eine **[!UICONTROL Product Data]** Eigenschaft hinzuzufügen. Produktdaten enthalten die Metadateneigenschaften zum Verknüpfen eines Commerce-Assets mit Produkt-SKUs.

     ![Benutzerdefiniertes Produktdaten-Benutzeroberflächen-Steuerelement](../assets/aem-commerce-sku-metadata-fields-from-template.png){width="600" zoomable="yes"}

   * Ein benutzerdefinierter Metadatentyp `commerce:roles` und `commerce:positions` Attribute, die zeigen, wie das Asset in Commerce visualisiert wird.

* Ein Metadatenschema-Formular mit einer Registerkarte &quot;Commerce&quot;, das die `Eligible for Commerce`- und `Product Data` für das Tagging von Commerce-Assets enthält. Das Formular bietet außerdem Optionen zum Ein- oder Ausblenden der `roles`- und `position` in der AEM Assets-Benutzeroberfläche.

  Registerkarte ![Commerce für das Metadatenschema-Formular von AEM Assets](../assets/assets-configure-metadata-schema-form-editor.png){width="600" zoomable="yes"}

* Ein [Beispiel für getaggte und genehmigte Commerce](https://github.com/ankumalh/assets-commerce/blob/main/ui.content/src/main/content/jcr_root/content/dam/wknd/en/activities/hiking/equipment_6.jpg/.content.xml)Assets`equipment_6.jpg` zur Unterstützung der anfänglichen Asset-Synchronisierung. Nur genehmigte Commerce-Assets können von AEM Assets mit Adobe Commerce synchronisiert werden.

>[!NOTE]
>
> Weitere Informationen zum {[}AEM Commerce](https://github.com/ankumalh/assets-commerce)Package-Code finden Sie auf der Seite „Readme **.**

## Voraussetzungen

Sie benötigen die folgenden Ressourcen und Berechtigungen, um den `assets-commerce`-Code in der AEM Assets as a Cloud Service AEM-Umgebung bereitzustellen:

* [Zugriff auf das AEM Assets Cloud Manager-Programm und Umgebungen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager#access-sysadmin-bo) mit den Rollen „Programm“ und „Bereitstellungs-Manager“

* eine [lokale AEM-Entwicklungsumgebung](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview) und die Vertrautheit mit dem lokalen AEM-Entwicklungsprozess.

* Machen Sie sich mit der [AEM](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure)Projektstruktur und der Bereitstellung benutzerdefinierter Inhaltspakete mit Cloud Manager vertraut.

* Die **IMS-Organisations** ID), die für Ihre Commerce-Instanz konfiguriert wurde.

## Schritt 1: Installieren des Pakets **assets-commerce**

1. Gehen Sie zur AEM Cloud Manager, wählen Sie ein Programm aus und erstellen [Produktions- und Staging-Umgebungen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/create-environments#creating-environments) die Sie in Adobe Commerce integrieren möchten.

1. Konfigurieren Sie eine [Bereitstellungs-Pipeline](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/administering/site-creation/quick-site/pipeline-setup#create-front-end-pipeline) oder stellen Sie sicher, dass Ihre Pipeline Änderungen an der ausgewählten Umgebung bereitstellen kann.

1. [Klonen Sie das in Adobe verwaltete Git](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/administering/site-creation/quick-site/retrieve-access#repo-access)Repository für das ausgewählte Programm.

1. Laden Sie von GitHub den Paket-Code aus dem [AEM Assets Commerce-Repository](https://github.com/ankumalh/assets-commerce) herunter.

1. Kopieren Sie [lokalen AEM-](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview)) den heruntergeladenen Code manuell in das bestehende von Adobe verwaltete Repository.

1. Ersetzen Sie in allen `filter.xml` und `pom.xml files` für Ihr Projekt alle Vorkommen von `<my-app>` durch Ihren App-Namen.

>[!NOTE]
>
> Alternativ können Sie den benutzerdefinierten Code in Ihrer AEM Assets-Projektkonfiguration als Maven **Paket**.

1. Übertragen Sie die Änderungen und pushen Sie Ihre lokale Entwicklungsverzweigung in das Cloud Manager-Git-Repository.

1. Aktualisieren Sie in AEM Cloud Manager [die AEM-Umgebung, indem Sie die Pipeline verwenden, um Ihren Code bereitzustellen](https://experienceleague.dobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code#deploying-code-with-cloud-manager).

1. Gehen Sie zu einem beliebigen Asset und bearbeiten Sie dessen Eigenschaften, um die Änderungen zu validieren:

   * Das Standard-Metadatenschema umfasst die Registerkarte **Commerce** .

   * Produkt-SKUs und die `Eligible for Commerce` Felder sind sichtbar.

### Registerkarte **Commerce** ist in den Eigenschaften nicht sichtbar

Wenn die Registerkarte **Commerce** nicht in den Eigenschaften angezeigt wird, müssen Sie eine im Metadatenschema-Editor manuell erstellen.

1. Navigieren Sie zum Metadatenschema-Editor.

1. Klicken Sie **Bearbeiten**, um das Standard-Metadatenschema-Formular zu ändern.

1. Erstellen Sie eine **Commerce**-Registerkarte und wählen Sie sie aus.

1. Ziehen Sie die Komponente **Produkt** in die Registerkarte **Commerce** und ordnen Sie sie der `commerce:skus` zu.

1. Aktivieren Sie das Kontrollkästchen für **Rollen anzeigen** und **Reihenfolge anzeigen**.

1. Ziehen Sie eine **checkbox**-Komponente per Drag-and-Drop auf die Registerkarte {2 **Commerce} und ordnen Sie sie der** zu. `commerce:isCommerce` Definieren Sie **Ja** und **Nein** als Optionen.

Wenn Sie auf andere Probleme stoßen, erstellen Sie ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=de#submit-ticket) oder wenden Sie sich an Ihren AEM Assets Integration-Vertriebsmitarbeiter, um Hilfe zu erhalten.

## Schritt 2: Optional. Konfigurieren eines Metadatenprofils

Legen Sie in der AEM Assets-Autorenumgebung Standardwerte für Commerce-Asset-Metadaten fest, indem Sie ein Metadatenprofil erstellen. Wenden Sie dann das neue Profil auf AEM Asset-Ordner an, um diese Standardwerte automatisch zu verwenden. Diese Konfiguration optimiert die Asset-Verarbeitung durch Reduzierung manueller Schritte.

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

1. Wählen Sie auf [!UICONTROL &#x200B; Metadata Profiles] Seite das Integrationsprofil Commerce aus.

1. Wählen Sie im Menü Aktion die Option **[!UICONTROL Apply Metadata Profiles to Folders]** aus.

1. Wählen Sie den Ordner aus, der Commerce-Assets enthält.

   Erstellen Sie einen Commerce-Ordner, wenn er noch nicht vorhanden ist.

1. Klicken Sie auf **[!UICONTROL Apply]**.

## Nächste Schritte

* [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} [Adobe Commerce-Pakete installieren](configure-commerce.md).

* [!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} [Konfigurieren der Integration über den Commerce Admin](setup-synchronization.md).
