---
title: Integration konfigurieren
description: Erfahren Sie, wie Sie Ihr Adobe Commerce-Projekt mit Experience Manager Assets-Projekten verbinden, um die Synchronisierung von Assets zwischen diesen beiden Systemen zu aktivieren.
feature: CMS, Media
exl-id: 3533d010-926f-4d78-935c-98a9b7040d27
TQID: 'https://experienceleague.adobe.com/MM-neGrH-N8xBcCwLgnsaIrIjhbX6uYL5kS41QdV79I'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
subfeature_v2:
  - id: ae62cf09-5996-4921-bda8-fbe67b62e470
    internal-label: Storefront configuration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 5e9c42e5c93ac81604aa38bf3e55c5df729650a0
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 1%
---
# Integration konfigurieren

Konfigurieren Sie die Integration, indem Sie Commerce mit der AEM Assets-Instanz verbinden und die entsprechende Strategie für die Synchronisierung von Assets auswählen.

Nachdem Sie das AEM Assets-Projekt identifiziert haben, wählen Sie die Zuordnungsregel für die Synchronisierung von Assets zwischen Adobe Commerce und AEM Assets aus.

* **[!UICONTROL Match by product SKU]** - Standardregel, die die SKU in den Asset-Metadaten mit der [Commerce-Produkt-SKU](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/glossary#sku) abgleicht, um sicherzustellen, dass Assets mit den richtigen Produkten verknüpft sind.

* **[!UICONTROL Custom match]** - Matching-Regel für komplexere Szenarien oder spezifische Geschäftsanforderungen, die eine benutzerdefinierte Matching-Logik erfordern. Für die Implementierung des benutzerdefinierten Abgleichs ist die Entwicklung von benutzerdefiniertem Code in Adobe Developer App Builder erforderlich, um zu definieren, wie Assets mit Produkten abgeglichen werden. Siehe [Benutzerdefinierte automatische Zuordnung](../synchronize/custom-match.md).

Verwenden Sie für die Ersteinrichtung die **[!UICONTROL Match by product SKU]**.

## Anforderungen

Stellen Sie vor dem Konfigurieren der AEM Assets-Integration sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Konfigurieren des AEM Assets-Projekts](configure-aem.md)

* [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} [Installieren von Adobe Commerce-](configure-commerce.md), um die Erweiterung hinzuzufügen und die erforderlichen Anmeldeinformationen und Verbindungen zur Verwendung der Erweiterung zu generieren.

* [Benutzerberechtigungen und IMS](permissions.md) - Konfigurieren Sie die erforderlichen Berechtigungen für den Asset-Wähler, die AEM-Umgebungsauswahl und die Domain-Zuordnung.

## Konfigurieren der Verbindung

![Konfiguration der AEM Assets-Integration mit Beispielwerten für Umgebung und Domain](../assets/aem-assets-view.png){width="900" zoomable="yes"}

1. Navigieren Sie vom Commerce-Administrator aus zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

>[!INFO]
>
> Die AEM Assets-Integration unterstützt nur Konfigurationen im globalen (Standard-)Umfang. Die Konfiguration auf Website-Ebene wird nicht unterstützt. Wenn Sie versuchen, die Integration auf Website-Ebene zu konfigurieren, ignoriert das System Einstellungen auf Website-Ebene und verwendet stattdessen die globalen Konfigurationswerte.

1. [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} Geben Sie die **[!UICONTROL Asset Selector IMS Client ID]** ein.

   Diese ID ist erforderlich, um den Asset-Wähler zu aktivieren. Siehe [Benutzerberechtigungen und IMS](permissions.md) um diese ID zu erhalten. Weitere Informationen zum Asset-Wähler finden Sie unter [Manuelles Auswählen von Assets](../synchronize/asset-selector-integration.md).

1. Wählen Sie **[!UICONTROL AEM Environment]** die in konfigurierte Umgebung aus [Konfigurieren des AEM Assets-Projekts](configure-aem.md).

   Die Liste enthält AEM-Umgebungen, für die Ihre Benutzerin bzw. Ihr Benutzer über ein Autoren- oder Versandproduktprofil verfügt. Wenn die erwartete Umgebung fehlt, überprüfen Sie [Benutzerberechtigungen und IMS](permissions.md).

   Wenn in Ihrer Konfiguration stattdessen separate **[!UICONTROL Program ID]**- und **[!UICONTROL Environment ID]** angezeigt werden, geben Sie die Kennungen für diese Umgebung an. Kopieren Sie sie zur manuellen Eingabe aus AEM Cloud Manager oder leiten Sie sie von Ihrer Autoren-URL ab: `https://author-p<ProgramID>-e<EnvironmentID>.adobeaemcloud.com/`. Geben Sie nur die numerischen Kennungen ein, ohne die Präfixe `p` und `e`.

   Deaktivieren Sie bei Feldern mit einem **[!UICONTROL Use system value]** das Kontrollkästchen, bevor Sie den Standardwert überschreiben.

1. Überprüfen Sie **[!UICONTROL AEM Domain Mapping]**. Verfügbare Domains werden basierend auf der ausgewählten AEM-Umgebung automatisch geladen. Wenn Ihr Projekt eine benutzerdefinierte Domain für die Asset-Bereitstellung verwendet, befolgen Sie [Konfigurieren der benutzerdefinierten Domain-URL](#optional-configure-the-custom-domain-url).

1. [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} Wählen Sie die [[!UICONTROL Commerce integration]](configure-commerce.md#add-the-integration-to-the-commerce-environment) zum Authentifizieren von Anfragen zwischen Commerce und dem Asset Matching-Service aus.

1. Legen Sie **[!UICONTROL Synchronization enabled]** auf `Yes` fest, damit Commerce eingehende Updates von AEM Assets annehmen kann.

   Nach der Aktivierung der Integration stehen zusätzliche Konfigurationsoptionen zur Verfügung, um Kriterien für die Asset-Zuordnung anzugeben.

1. Wählen Sie aus dem Dropdown-Menü &quot;**[!UICONTROL Asset matching rule]**&quot; eine der Asset-Zuordnungsregeln für die Asset-Synchronisierung aus.

   * Wählen Sie **[!UICONTROL Match by product SKU]** für [standardmäßige automatische Zuordnung](../synchronize/default-match.md).
   * Wählen Sie **[!UICONTROL Custom match]** für [benutzerdefinierte automatische Zuordnung](../synchronize/custom-match.md). Diese Option erfordert [Adobe Developer App Builder](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/extensibility/adobe-developer-app-builder/introduction-to-app-builder).

1. Geben Sie **[!UICONTROL Match by product SKU]** im Feld **[!UICONTROL Match by product SKU attribute name]** den Eigenschaftsnamen der [AEM Assets](../metadata.md)Metadaten ein. Der Standardwert lautet `commerce:skus`.

   Geben Sie den Eigenschaftsnamen ein, keinen Produkt-SKU-Wert. Fügen Sie den **[!UICONTROL Product Data]**-Metadaten jedes Assets in AEM Assets die eigentlichen Produkt-SKUs hinzu, wie unter [Standardmäßige automatische Zuordnung](../synchronize/default-match.md) beschrieben.

1. Überprüfen Sie die Einstellung [Visualisierungseigentümer](#configure-the-visualization-owner). Behalten Sie während der Migration die Verantwortung für **Adobe Commerce** bis zum Abschluss der Asset-Synchronisierung bei.

1. Wählen Sie **[!UICONTROL Save Config]** aus, um Aktualisierungen anzuwenden und die Synchronisierung von Assets zu starten.

   Durch die Konfigurationsaktualisierung wird der anfängliche Synchronisierungsprozess Trigger, sodass Commerce eingehende Aktualisierungen von AEM Assets annehmen kann. Die für die Synchronisierung erforderliche Zeit hängt vom Volumen der Assets und von bestimmten Konfigurationen ab. Die Integration nutzt automatisierte Prozesse, um die für die Synchronisierung erforderliche Zeit zu minimieren.

### Synchronisierung mit SLA

Der service level agreement (SLA) für die Integration garantiert die folgenden Synchronisierungsleistungsstufen:

* `< 5 minutes for 99% of updates`

* `< 30 minutes for 99.9% of updates`

Mit diesem Service wird sichergestellt, dass Produktseiten stets die aktuellsten Bilder anzeigen und so der Inhalt der Storefront präzise und visuell ansprechend bleibt.

## Synchronisieren von lokalisiertem Alternativtext

Der lokalisierte Alternativtext verwendet den vorhandenen Asset-Synchronisierungsprozess. Sie benötigen keinen neuen Ereignistyp oder eine separate Synchronisierungskonfiguration.

1. Fügen Sie auf der Registerkarte **[!UICONTROL Commerce]** des AEM-Assets mindestens eine Alternativtextzeile für die Store-Ansicht hinzu.

1. Verknüpfen Sie das Asset mit der Commerce-Produkt-SKU.

1. Genehmigen Sie das Asset in AEM Assets.

1. Warten Sie, bis das Asset-Ereignis und der Synchronisierungsprozess abgeschlossen sind.

1. Überprüfen Sie den lokalisierten Wert in der Commerce Admin und in der Storefront-Antwort.

Die Feldnamen, Validierungsregeln und das Commerce-Ergebnis finden Sie unter [Commerce-Metadaten in AEM Assets](../metadata.md).

## Visualisierungsbesitzer konfigurieren

Die Einstellung **Visualisierungseigentümer** bestimmt, welches System Produktbilder in der Integration bereitstellt:

* Adobe Commerce - Verwendet in Commerce gehostete Bilder.

* AEM Assets - Verwendet Bilder, die mit AEM synchronisiert wurden.

Der Administrator zeigt die verfügbaren Bilder für diesen Eigentümer an, während der Rest der Bilder ausgegraut ist und mit einer **Beschriftung angezeigt**.

Weitere Informationen [ Verhalten bei der Anzeige von Bildern finden ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/digital-assets/product-image#set-image-details){target=_blank} unter „Festlegen von“.

>[!TIP]
>
> Legen Sie während einer Migration von Commerce zu AEM Assets den **Visualisierungseigentümer** auf Commerce fest, um fehlerhafte Bildverknüpfungen zu vermeiden. Wenn alle Produkte erfolgreich mit AEM Assets synchronisiert wurden, wechseln Sie zum AEM Assets-Eigentümer, um die Umstellung abzuschließen. Dadurch wird eine kontinuierliche Bildverfügbarkeit während des gesamten Prozesses sichergestellt.

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

   ![Visualization Owner auf AEM Assets festgelegt](../assets/visualization-owner-detail.png){width="700" zoomable="yes"}

1. Wählen Sie die **Visualisierungsinhaber** Quelle aus, um die Bilder anzuzeigen.

1. Klicken Sie auf **[!UICONTROL Save Config]** , um Aktualisierungen anzuwenden.

   Bevor Sie zu **AEM Assets** wechseln[ überprüfen Sie, ob die Assets mit den erwarteten Produkten verknüpft sind](#verify-the-integration). Konfigurieren [ dann Ihre Storefront, ](configure-storefront.md) AEM Assets-Produktbilder anzuzeigen.

## Optional. Konfigurieren der benutzerdefinierten Domain-URL

Wenn das AEM Assets as a Cloud Service-Projekt mit einem [benutzerdefinierten Domain-Namen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name){target=_blank} konfiguriert wurde, müssen Sie den Domain-Namen zur Commerce-Store-Konfiguration hinzufügen, damit die AEM Assets-Integration für Commerce ihn verwenden kann.

Rufen Sie die konfigurierte URL der benutzerdefinierten Domain für die Asset-Bereitstellung von Ihrem AEM-Administrator ab. Diese Einstellung ersetzt die AEM-Bereitstellungs-URL. Es ist nicht die AEM-Autoren-URL, die zum Identifizieren der Programm-ID und der Umgebungs-ID verwendet wird. Wenn Ihr Projekt keine benutzerdefinierte Domain verwendet, lassen Sie die Domain-Zuordnung unverändert.

>[!NOTE]
>
>Beim Konfigurieren einer benutzerdefinierten Domain-URL werden die URLs zuvor synchronisierter Assets nicht aktualisiert. Diese Assets behalten ihre vorherigen URLs bei, bis sie [in AEM Assets erneut verarbeitet](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/reprocessing){target=_blank} werden. Nachdem Sie die benutzerdefinierte Domain-Konfiguration gespeichert haben, verarbeiten Sie diese Assets erneut, um ihre URLs zu aktualisieren und die benutzerdefinierte Domain zu verwenden.

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]**.

1. Bestätigen Sie die ausgewählten **[!UICONTROL AEM Environment]** und wählen Sie dann die konfigurierte benutzerdefinierte Domain aus **[!UICONTROL AEM Domain Mapping]**. Verfügbare Domains werden für die ausgewählte Umgebung automatisch geladen.

![AEM-Umgebung und Domain-Selektoren mit Beispielwerten](../assets/aem-assets-environment-domain.png){width="700" zoomable="yes"}

    Bei Konfigurationen, die stattdessen ein Textfeld **[!UICONTROL Asset Custom Domain]** anzeigen, geben Sie die benutzerdefinierte Domain-URL in dieses Feld ein.

1. Klicken Sie auf **[!UICONTROL Save Config]** , um Aktualisierungen anzuwenden.

## Überprüfen der Integration

>[!NOTE]
>
>Synchronisierungsstatus ist für Adobe Commerce Optimizer nicht verfügbar. Befolgen Sie den [Commerce Optimizer](configure-aco.md#match-by-sku-workflow-example)Verifizierungs-Workflow anstelle der unten aufgeführten Commerce-Admin-Prüfungen.

1. Wählen Sie ein bestehendes Commerce-Produkt aus und notieren Sie sich dessen SKU.

1. Markieren Sie in AEM Assets ein Test-Asset als **[!UICONTROL Eligible for Commerce]**, verknüpfen Sie es mit dieser Produkt-SKU und legen Sie dessen Rolle und Position fest. Genehmigen Sie das Asset. Siehe [Standardmäßiger automatischer Abgleich](../synchronize/default-match.md) oder verwenden Sie Ihre konfigurierte [benutzerdefinierte Abgleichregel](../synchronize/custom-match.md).

1. Öffnen Sie nach Abschluss der Synchronisierung das Produkt in Commerce Admin und überprüfen Sie den **[!UICONTROL Images And Videos]** Abschnitt des Produkts auf die zugehörigen Assets, Rollen und Positionen. Siehe [Verwalten von ](../manage-assets.md).

1. Überprüfen Sie [Synchronisierungsstatus](sync-status.md) auf das Synchronisierungsergebnis des Assets. Wenn die Synchronisierung fehlschlägt, überprüfen Sie die Spalte **[!UICONTROL Error]** .

1. Nachdem Sie **AEM Assets** als Verantwortlichen für die Visualisierung ausgewählt und die [Storefront-Konfiguration](configure-storefront.md) abgeschlossen haben, öffnen Sie das Produkt in der Storefront und bestätigen Sie, dass das erwartete Bild angezeigt wird.

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} Weitere Informationen zur Fehlerbehebung bei der Synchronisierung finden Sie unter [Integrationsprotokolle](logs.md).

## Nächster Schritt

* [Konfigurieren Sie Ihre Commerce-Storefront](configure-storefront.md), um Produktbilder von AEM Assets mit Edge Delivery Services anzuzeigen.

* Einrichten von [Abgleichregeln](../synchronize/default-match.md) zwischen Adobe Commerce und der AEM Assets-Integration.

* [Verwalten von Commerce-](../manage-assets.md).
