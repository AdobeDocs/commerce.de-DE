---
title: AEM Assets-Integration für Commerce
description: Erfahren Sie, wie Sie Adobe Experience Manager Assets mit Ihrer  [!DNL Commerce] -Instanz integrieren können, um die Mediendateien für Ihre Commerce-Storefront zu erstellen und zu verwalten.
feature: CMS, Media, Configuration, Integration
exl-id: f450752a-bef1-419e-ad14-ff8879ab204b
source-git-commit: d46526db56dad08a8f865664c92d1214bbf063d8
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# AEM Assets-Integration für Commerce

Die Nachfrage nach personalisierten Inhalten steigt rapide, während die Marketing-Budgets unter Druck geraten. Einzelhändler und Marken tun sich schwer, mit dem wachsenden Bedarf an Variationen in der Produktdarstellung Schritt zu halten, der durch regionale, saisonale und segmentspezifische Anforderungen bedingt ist.

Nehmen wir einen retailer mit 1.000 Produkten. Noch bevor Attributvarianten berücksichtigt werden, steigt die Anzahl der erforderlichen digitalen Assets erheblich, wenn verschiedene Regionen, Kundensegmente und Personalisierungsbemühungen berücksichtigt werden. Dies kann zu einer überwältigenden Anzahl von Asset-Varianten führen, die bis in die Millionen reichen.

![Übersicht](assets/product-visuals-example.png){width="700" zoomable="yes"}

Die AEM Assets-Integration löst diese Herausforderung durch die Automatisierung von Asset-Management-Workflows. Die Integration stellt sicher, dass digitale Assets, wie Produktbilder und Marketing-Inhalte, basierend auf der SKU oder anderen Schlüsselattributen dynamisch mit den entsprechenden Merchandising-Entitäten verknüpft werden, einschließlich Produkten und Kategorien in Adobe Commerce. Dieser Prozess optimiert den Betrieb und steigert die Effizienz, indem er Folgendes ermöglicht:

* **Nahtlose Installation und Konfiguration** - Merchandising-Teams und -Entwickler können die Integration schnell mit den bekannten Adobe-Tools und -Workflows einrichten.

* **Dynamic Asset Updates** Produktbilder und Marketing-Assets spiegeln automatisch die neuesten Änderungen in AEM Assets wider, sodass Storefronts präzise und relevant bleiben.

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

![check](assets/icon-check.png) **No Additional Cost**-Diese Integration wird für Händler, die die Lizenzanforderungen erfüllen, kostenlos bereitgestellt.

![check](assets/icon-check.png) **Official Adobe Solution** Von Adobe entwickelt, gepflegt und vollständig unterstützt, um Stabilität und Abstimmung mit zukünftigen Plattformverbesserungen sicherzustellen.

![Überprüfen](assets/icon-check.png) **Die Unterstützung und Fehlerbehebung durch das Adobe Managed Support-** werden direkt von Adobe durchgeführt, sodass Sie sich beruhigt auf Ihre Arbeit konzentrieren und Probleme effizient beheben können.

![check](assets/icon-check.png) **Funktionen von Adobe Storefront Builder**-Die DAM-Lösung (Digital Asset Management) ermöglicht die Verwendung von Assets wie Bildern, Videos und anderen Medien in [Storefront Builder](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/storefront-builder/#userlabs-commerce-genai-product-visuals).

>[!ENDSHADEBOX]

In diesem Video erfahren Sie, wie Adobe Commerce und AEM Assets zusammenarbeiten, um Inhalts-Workflows zu optimieren:

>[!VIDEO](https://video.tv.adobe.com/v/3447837)

## Nächste Schritte

Die Aktivierung der Commerce-Integration mit Experience Manager Assets ist ein dreistufiger Prozess:

1. [Konfigurieren Sie Ihr AEM Assets-Projekt zur Unterstützung von Commerce-Metadaten](get-started/configure-aem.md).

1. [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} [Adobe Commerce-Pakete installieren](get-started/configure-commerce.md).

1. [Integration konfigurieren](get-started/setup-synchronization.md).

## Support

Wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden, wenden Sie sich an Ihren AEM Assets Integration-Vertriebsmitarbeiter oder erstellen Sie ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket), um zusätzliche Hilfe zu erhalten.
