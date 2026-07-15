---
title: AEM Assets-Integration für Commerce
description: Erfahren Sie, wie Sie Adobe Experience Manager Assets mit Ihrer  [!DNL Commerce] -Instanz integrieren können, um die Mediendateien für Ihre Commerce-Storefront zu erstellen und zu verwalten.
feature: CMS, Media, Configuration, Integration
exl-id: f450752a-bef1-419e-ad14-ff8879ab204b
TQID: https://experienceleague.adobe.com/CTDmM7Ox2rQ-55F1BVTg-C8DPBEuEpzFxXGtWpnjXKs
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: da3860b0-d637-47df-bef0-273751180266
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 0c2e50338cbf286704239b6d1f628180e85a3bef
workflow-type: tm+mt
source-wordcount: 1081
ht-degree: 1%

---

# AEM Assets-Integration für Commerce

Die Nachfrage nach personalisierten Inhalten steigt rapide, während die Marketing-Budgets unter Druck geraten. Einzelhändler und Marken tun sich schwer, mit dem wachsenden Bedarf an Variationen in der Produktdarstellung Schritt zu halten, der durch regionale, saisonale und segmentspezifische Anforderungen bedingt ist.

Nehmen wir einen retailer mit 1.000 Produkten. Die Anzahl der erforderlichen digitalen Assets nimmt erheblich zu, wenn verschiedene Regionen, Kundensegmente und Personalisierungsinitiativen berücksichtigt werden. Diese Situation kann zu einer überwältigenden Anzahl von Asset-Variationen führen, die bis in die Millionen reichen.

![Übersicht](assets/product-visuals-example.png){width="700" zoomable="yes"}

Die AEM Assets-Integration löst diese Herausforderung durch die Automatisierung von Asset-Management-Workflows. Die Integration verknüpft digitale Assets dynamisch mit den entsprechenden Adobe Commerce-Produkten und -Kategorien und basiert auf der SKU oder anderen Schlüsselattributen. Dieser Prozess optimiert den Betrieb und steigert die Effizienz, indem er Folgendes ermöglicht:

* **Nahtlose Installation und Konfiguration** - Merchandising-Teams und -Entwickler können die Integration schnell mit den bekannten Adobe-Tools und -Workflows einrichten.

* **Dynamic Asset Updates** - Produktbilder und Marketing-Assets spiegeln automatisch die neuesten Änderungen in AEM Assets wider, sodass Storefronts präzise und relevant bleiben.

* **Optimiertes Katalogmanagement** Automatisiert die Aktualisierung und Bereinigung von Assets, minimiert den manuellen Aufwand und stellt einen konsistenten, gepflegten Produktkatalog sicher.

## Voraussetzungen für die Verwendung der Integration

Um diese Integration entweder mit [Product Visuals oder AEM Assets](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview#product-visuals-powered-by-aem-assets) nutzen zu können, müssen Unternehmen die folgenden Anforderungen erfüllen:

>[!BEGINTABS]

>[!TAB Produktvisualisierung]

[!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} Active-Lizenzen für Adobe Commerce, Product Visuals powered by AEM Assets und [AEM Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/administering-dynamic-media) (diese Lizenzen sind standardmäßig mit [!DNL Adobe Commerce as a Cloud Service] und [!DNL Adobe Commerce Optimizer] verfügbar).

>[!TAB AEM Assets]

[!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} Aktive Lizenzen für Adobe Commerce, Adobe Experience Manager Assets und [AEM Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/administering-dynamic-media).

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} Adobe Commerce 2.4.5+

* PHP 8.1, 8.2, 8.3 und 8.4

* Composer 2.x

[!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} Adobe Experience Manager wird mit [Adobe Experience Manager Assets as a Cloud Service bereitgestellt](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/overview)

>[!ENDTABS]

Der Adobe Commerce-Benutzer, der die Integration konfiguriert, muss Zugriff auf die [IMS-Organisation](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255) haben, in der das AEM Assets-Projekt bereitgestellt wird.

>[!BEGINSHADEBOX]

## Die wichtigsten geschäftlichen Vorteile

![check](assets/icon-check.png) **No Additional Cost** - Diese Integration wird für Händler, die die Lizenzanforderungen erfüllen, kostenlos bereitgestellt.

![check](assets/icon-check.png) **Official Adobe Solution** - Von Adobe entwickelt, gepflegt und vollständig unterstützt, um Stabilität und Abstimmung mit zukünftigen Plattformverbesserungen sicherzustellen.

![Überprüfen](assets/icon-check.png) **Adobe Managed Support Model** - Adobe übernimmt die direkte Unterstützung und Fehlerbehebung, bietet zuverlässigen Support und optimierte Problembehebung.

![check](assets/icon-check.png) **Funktionen von Adobe Storefront Builder** - Die DAM-Lösung (Digital Asset Management) ermöglicht die Verwendung von Assets wie Bildern, Videos und anderen Medien in [Storefront Builder](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/storefront-builder/#userlabs-commerce-genai-product-visuals).

>[!ENDSHADEBOX]

## Tutorial

Sehen Sie sich diese Videos an, um zu erfahren, wie Sie die AEM Assets-Integration mit Adobe Commerce einrichten und verwenden.

>[!BEGINTABS]

>[!TAB Tutorial zu Adobe Commerce in der Cloud oder vor Ort]

In diesem Video erfahren Sie, wie Adobe Commerce und AEM Assets zusammenarbeiten, um Inhalts-Workflows zu optimieren:

>[!VIDEO](https://video.tv.adobe.com/v/3447837)

>[!TAB Tutorial zu Adobe Commerce as a Cloud Service]

Erfahren Sie, wie Sie Adobe Commerce as a Cloud Service mit der AEM Assets-Integration verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/3478140?quality=12&learn=on)

>[!ENDTABS]

## Nächste Schritte

Der Prozess zum Installieren und Konfigurieren der AEM Assets-Integration hängt von Ihrer Adobe Commerce-Bereitstellung ab. In allen Fällen müssen Sie zunächst AEM Assets konfigurieren und dann Commerce damit verbinden.

Um den Namespace, das Metadatenschema und **[!UICONTROL Commerce]** Registerkarte zu verstehen, die die Integration in Ihrer AEM Assets-Umgebung hinzufügt, lesen Sie [Commerce-Metadaten in AEM Assets](metadata.md) bevor Sie beginnen.

Wählen Sie Ihre Bereitstellung aus, um die erforderlichen Schritte in der richtigen Reihenfolge auszuführen:

>[!BEGINTABS]

>[!TAB Adobe Commerce as a Cloud Service]

[!BADGE nur SaaS]{type=Positive tooltip="Gilt nur für Adobe Commerce as a Cloud Service-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."}

1. Um Commerce-Metadaten zu unterstützen, [&#x200B; Sie das AEM Assets-Projekt &#x200B;](get-started/configure-aem.md). Verwenden Sie ab AEM-Version `2026.5.26309` das [Self-Service-Onboarding](get-started/configure-aem.md#enable-aem-commerce-self-service); installieren Sie das `assets-commerce`-Paket in früheren Versionen manuell.

1. [Konfigurieren Sie die IMS](get-started/permissions.md)Benutzerberechtigungen, damit der Asset-Wähler und die automatisch ausgefüllten **[!UICONTROL Program ID]** und **[!UICONTROL Environment ID]** Felder verfügbar sind.

1. [Konfigurieren der Integration im Commerce Admin](get-started/setup-synchronization.md).

1. Optional. [Anzeige von Produktbildern aktivieren](get-started/configure-storefront.md#enable-product-images) sodass eine Storefront mit Edge Delivery Services von AEM verwaltete Produktbilder rendert.

>[!TAB Adobe Commerce on Cloud (PaaS)]

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."}

1. Um Commerce-Metadaten zu unterstützen, [&#x200B; Sie das AEM Assets-Projekt &#x200B;](get-started/configure-aem.md). Verwenden Sie ab AEM-Version `2026.5.26309` das [Self-Service-Onboarding](get-started/configure-aem.md#enable-aem-commerce-self-service); installieren Sie das `assets-commerce`-Paket in früheren Versionen manuell.

1. [Installieren Sie Adobe Commerce-](get-started/configure-commerce.md), um die Erweiterung hinzuzufügen und die erforderlichen Anmeldeinformationen und Verbindungen zu generieren.

1. [Konfigurieren Sie die IMS](get-started/permissions.md)Benutzerberechtigungen, damit der Asset-Wähler und die automatisch ausgefüllten **[!UICONTROL Program ID]** und **[!UICONTROL Environment ID]** Felder verfügbar sind.

1. [Konfigurieren der Integration im Commerce Admin](get-started/setup-synchronization.md).

1. Optional. [Anzeige von Produktbildern aktivieren](get-started/configure-storefront.md#enable-product-images) sodass eine Storefront mit Edge Delivery Services von AEM verwaltete Produktbilder rendert.

>[!TAB Adobe Commerce Optimizer]

[!BADGE nur SaaS]{type=Positive tooltip="Gilt nur für Adobe Commerce Optimizer-Projekte."}

[!DNL Adobe Commerce Optimizer] Es hat keine Benutzeroberfläche für die Admin-Konfiguration. Der Adobe-Support konfiguriert die Integration über Ihr Onboarding-Ticket. Bereiten Sie AEM Assets also zuerst vor.

1. Um Commerce-Metadaten zu unterstützen, [&#x200B; Sie das AEM Assets-Projekt &#x200B;](get-started/configure-aem.md). Verwenden Sie ab AEM-Version `2026.5.26309` das [Self-Service-Onboarding](get-started/configure-aem.md#enable-aem-commerce-self-service); installieren Sie das `assets-commerce`-Paket in früheren Versionen manuell.

1. [Senden Sie das Onboarding-Support](get-started/configure-aco.md#onboarding)Ticket mit Ihrer Mandanten-ID, AEM-Programm-ID, AEM-Umgebungs-ID, übereinstimmender Regel, Ebene und Gebietsschema.

1. [Konfigurieren Sie Ihre &#x200B;](get-started/configure-aco.md#onboarding) mit demselben Gebietsschema und derselben Ebene, die Sie im Ticket registriert haben.

1. Optional. [Anzeige von Produktbildern aktivieren](get-started/configure-storefront.md#enable-product-images) sodass eine Storefront mit Edge Delivery Services von AEM verwaltete Produktbilder rendert.

   Das vollständige Verfahren, die Einschränkungen und die Ebenenanleitung finden Sie unter [Konfigurieren von AEM Assets für Commerce Optimizer](get-started/configure-aco.md).

>[!ENDTABS]

## Support

Wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden, wenden Sie sich an Ihren AEM Assets Integration-Vertriebsmitarbeiter oder erstellen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case), um zusätzliche Hilfe zu erhalten.
