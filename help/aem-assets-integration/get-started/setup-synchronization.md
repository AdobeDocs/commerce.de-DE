---
title: Integration konfigurieren
description: Erfahren Sie, wie Sie Ihr Adobe Commerce-Projekt mit Experience Manager Assets-Projekten verbinden, um die Synchronisierung von Assets zwischen diesen beiden Systemen zu aktivieren.
feature: CMS, Media
exl-id: 3533d010-926f-4d78-935c-98a9b7040d27
source-git-commit: d59c9d179018318d7a0ab1685d8e9e172eefa3ed
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 0%

---

# Integration konfigurieren

Konfigurieren Sie die Integration, indem Sie Commerce mit der AEM Assets-Instanz verbinden und die entsprechende Strategie für die Synchronisierung von Assets auswählen.

Nachdem Sie das AEM Assets-Projekt identifiziert haben, wählen Sie die Zuordnungsregel für die Synchronisierung von Assets zwischen Adobe Commerce und AEM Assets aus.

* **[!UICONTROL Match by product SKU]** - Standardregel, die die SKU in den Asset-Metadaten mit der [Commerce-Produkt-SKU](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/glossary#sku) abgleicht, um sicherzustellen, dass Assets mit den richtigen Produkten verknüpft sind.

* **[!UICONTROL Custom match]** - Matching-Regel für komplexere Szenarien oder spezifische Geschäftsanforderungen, die eine benutzerdefinierte Matching-Logik erfordern. Für die Implementierung des benutzerdefinierten Abgleichs ist die Entwicklung von benutzerdefiniertem Code in Adobe Developer App Builder erforderlich, um zu definieren, wie Assets mit Produkten abgeglichen werden. Weitere Details folgen in Kürze…

Verwenden Sie für die Ersteinrichtung die Standardregel *Übereinstimmung nach Produkt-SKU*.

## Anforderungen

Stellen Sie vor dem Konfigurieren der AEM Assets-Integration sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Konfigurieren des AEM Assets-Projekts](configure-aem.md)

* [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} [Installieren von Adobe Commerce-](configure-commerce.md), um die Erweiterung hinzuzufügen und die erforderlichen Anmeldeinformationen und Verbindungen zur Verwendung der Erweiterung zu generieren.

### IMS- und Benutzerberechtigungen

Um den Asset-Wähler zu verwenden und eine reibungslosere Einrichtung in Commerce zu ermöglichen, sind die folgenden Berechtigungen erforderlich:

>[!BEGINTABS]

>[!TAB ACCS]

[!BADGE nur SaaS]{type=Positive tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."}

Die IMS-Authentifizierung ist standardmäßig aktiviert. Fügen Sie den Benutzer dem Produktprofil **AEM Assets DM OpenAPI Users - delivery** in der [Adobe Admin Console](https://adminconsole.adobe.com/) hinzu, um Zugriff auf die AEM Assets-Bereitstellungsebene zu gewähren.

![Admin Console-Produktprofil für AEM Assets-Versand](../assets/aem-assets-delivery-product-profile.png){width="600" zoomable="yes"}

>[!TAB PaaS]

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."}

1. [Aktivieren von Adobe IMS für Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/ims/adobe-ims-config.html){target=_blank} indem Sie die Anweisungen im *Commerce-Administratorhandbuch befolgen*.

1. [Öffnen Sie ein Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases), um eine benutzerdefinierte IMS-Client-ID für den Asset-Wähler anzufordern.

1. Fügen Sie den Benutzer dem Produktprofil **AEM Assets DM OpenAPI Users - delivery** in der [Adobe Admin Console](https://adminconsole.adobe.com/) hinzu, um Zugriff auf die AEM Assets-Bereitstellungsebene zu gewähren.

>[!ENDTABS]

## Konfigurieren der Verbindung

1. Öffnen Sie vom Commerce-Administrator aus die AEM Assets-Integrationskonfiguration.

   1. Wechseln Sie zu **[!UICONTROL Store]** > Konfiguration > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

      ![AEM Assets-Integration aktivieren](../assets/aem-assets-view.png){width="600" zoomable="yes"}

>[!INFO]
>
> Die AEM Assets-Integration unterstützt nur Konfigurationen im globalen (Standard-)Umfang. Die Konfiguration auf Website-Ebene wird nicht unterstützt. Wenn Sie versuchen, die Integration auf Website-Ebene zu konfigurieren, ignoriert das System Einstellungen auf Website-Ebene und verwendet stattdessen die globalen Konfigurationswerte.

1. [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} Geben Sie die **[!UICONTROL Asset Selector IMS Client ID]** ein.

   Diese ID ist erforderlich, um den Asset-Wähler zu aktivieren und die Funktion zum automatischen Ausfüllen für die Felder Programm-ID und Umgebungs-ID zu aktivieren. Siehe [IMS- und Benutzerberechtigungen](#ims-and-user-permissions) um diese ID zu erhalten. Weitere Informationen zum Asset-Wähler finden Sie unter [Manuelles Auswählen von Assets](../synchronize/asset-selector-integration.md).

1. Wählen Sie die **[!UICONTROL Program ID]** und **[!UICONTROL Environment ID]** der AEM Assets-Umgebung aus den Dropdown-Menüs aus.

   Die Dropdown-Listen werden basierend auf der IMS-Sitzung des Benutzers automatisch ausgefüllt. Um diese Funktion verwenden zu können, müssen Sie über die richtigen [IMS- und Benutzerberechtigungen](#ims-and-user-permissions) verfügen.

   Wenn die Dropdown-Listen nicht verfügbar sind, können Sie die IDs manuell über die AEM Cloud Manager-URL eingeben: `https://author-p[Program ID]-e[EnvironmentID].adobeaemcloud.com/`

   Bearbeiten Sie die Konfigurationswerte, indem Sie die Auswahl aus der *[!UICONTROL Use system value]* entfernen.

1. [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} Wählen Sie die [[!UICONTROL Commerce integration]](configure-commerce.md#add-the-integration-to-the-commerce-environment) zum Authentifizieren von Anfragen zwischen Commerce und dem Asset Matching-Service aus.

1. Legen Sie **[!UICONTROL Synchronization enabled]** auf `Yes` fest, damit Commerce eingehende Updates von AEM Assets annehmen kann.

   Nach der Aktivierung der Integration stehen zusätzliche Konfigurationsoptionen zur Verfügung, um Kriterien für die Asset-Zuordnung anzugeben.

1. Wählen Sie aus dem Dropdown-Menü &quot;**[!UICONTROL Asset matching rule]**&quot; eine der Asset-Zuordnungsregeln für die Asset-Synchronisierung aus.

   * Wählen Sie **[!UICONTROL Match by SKU]** für [standardmäßige automatische ](../synchronize/default-match.md))
   * Wählen Sie **[!UICONTROL Custom match]** für [benutzerdefinierten automatischen Abgleich](../synchronize/custom-match.md) (erfordert [Adobe Developer App Builder](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder).)

1. Fügen Sie den [AEM Assets-Metadatenfeldnamen](configure-aem.md#configure-metadata) der für Commerce-Produkt-SKUs definiert ist, in das Feld **[!UICONTROL Match by product SKU attribute name]** ein, `commerce:skus` standardmäßig.

1. Wählen Sie **[!UICONTROL Save Config]** aus, um Aktualisierungen anzuwenden und die Synchronisierung von Assets zu starten.

   Durch die Konfigurationsaktualisierung wird der anfängliche Synchronisierungsprozess Trigger, sodass Commerce eingehende Aktualisierungen von AEM Assets annehmen kann. Die für die Synchronisierung erforderliche Zeit hängt vom Volumen der Assets und von bestimmten Konfigurationen ab. Die Integration nutzt automatisierte Prozesse, um die für die Synchronisierung erforderliche Zeit zu minimieren.

### Synchronisierung mit SLA

Die Integration gewährleistet die folgenden Synchronisierungsleistungsstufen:

* `< 5 minutes for 99% of updates`

* `< 30 minutes for 99.9% of updates`

Dadurch wird sichergestellt, dass Produktseiten immer die aktuellsten Bilder anzeigen und so der Inhalt der Storefront korrekt und visuell ansprechend bleibt.

### Visualisierungsbesitzer konfigurieren

Die Einstellung **Visualisierungseigentümer** bestimmt, welches System Produktbilder in der Integration bereitstellt:

* Adobe Commerce - Verwendet in Commerce gehostete Bilder.

* AEM Assets - Verwendet Bilder, die mit AEM synchronisiert wurden.

Der Administrator zeigt die verfügbaren Bilder für diesen Eigentümer an, während der Rest der Bilder ausgegraut ist und mit einer **Beschriftung angezeigt**.

Weitere Informationen [ Verhalten bei der Anzeige von Bildern finden ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/digital-assets/product-image#set-image-details){target=_blank} unter „Festlegen von“.

>[!TIP]
>
> Legen Sie während einer Migration von Commerce zu AEM Assets den **Visualisierungseigentümer** auf Commerce fest, um fehlerhafte Bildverknüpfungen zu vermeiden. Wenn alle Produkte erfolgreich mit AEM Assets synchronisiert wurden, wechseln Sie zum AEM Assets-Eigentümer, um die Umstellung abzuschließen. Dadurch wird eine kontinuierliche Bildverfügbarkeit während des gesamten Prozesses sichergestellt.

1. Navigieren Sie zu **[!UICONTROL Store]** > Konfiguration > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

   Funktion für Verantwortlichen für die Visualisierung der AEM Assets-Integration ![](../assets/visualization-owner-detail.png){width="400" zoomable="yes"}

1. Wählen Sie die **Visualisierungsinhaber** Quelle aus, um die Bilder anzuzeigen.

1. Klicken Sie auf **[!UICONTROL Save Config]** , um Aktualisierungen anzuwenden und die Synchronisierung von Assets zu starten.

### Optional. Konfigurieren der benutzerdefinierten Domain-URL

Wenn das AEM Assets as a Cloud Service-Projekt mit einem [benutzerdefinierten Domain-Namen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name){target=_blank} konfiguriert wurde, müssen Sie den Domain-Namen zur Commerce-Store-Konfiguration hinzufügen, damit die AEM Assets-Integration für Commerce ihn verwenden kann.

1. Navigieren Sie zu **[!UICONTROL Store]** > Konfiguration > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

   ![AEM Assets-Integration aktivieren](../assets/aem-assets-view.png){width="700" zoomable="yes"}

1. Fügen Sie die **benutzerdefinierte Domain-URL** zum Feld **[!UICONTROL Asset Custom Domain]** hinzu.

1. Klicken Sie auf **[!UICONTROL Save Config]** , um Aktualisierungen anzuwenden und die Synchronisierung von Assets zu starten.

## Nächster Schritt

* **Konfigurieren Ihrer Commerce-Storefront** - Um AEM Assets mit der Commerce-Storefront mit Edge Delivery Services zu verwenden, schließen Sie die Storefront-Konfiguration ab, die im Thema [AEM Assets-Integration](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-assets-configuration/) in der *Dokumentation zur Adobe Commerce-Storefront beschrieben*.

* Einrichten von [Abgleichregeln](../synchronize/default-match.md) zwischen Adobe Commerce und der AEM Assets-Integration.

* [Verwalten von Commerce-](../manage-assets.md).
