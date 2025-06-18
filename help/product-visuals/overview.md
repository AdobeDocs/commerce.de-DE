---
title: Produktvisualisierung
description: Erfahren Sie, wie Sie Adobe Experience Manager Assets mit Ihrer  [!DNL Commerce] -Instanz integrieren können, um die Mediendateien für Ihre Commerce-Storefront zu erstellen und zu verwalten.
feature: CMS, Media, Configuration, Integration
source-git-commit: 3afe05d4d0cfe94668bf821a09de4909dcb63a84
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---


# Produktvisualisierung mit AEM Assets-Integration für Commerce

Die Nachfrage nach personalisierten Inhalten steigt rapide, während die Marketing-Budgets unter Druck geraten. Einzelhändler und Marken tun sich schwer, mit dem wachsenden Bedarf an Variationen in der Produktdarstellung Schritt zu halten, der durch regionale, saisonale und segmentspezifische Anforderungen bedingt ist.

Nehmen wir einen retailer mit 1.000 Produkten. Noch bevor Attributvarianten berücksichtigt werden, steigt die Anzahl der erforderlichen digitalen Assets erheblich, wenn verschiedene Regionen, Kundensegmente und Personalisierungsbemühungen berücksichtigt werden. Dies kann zu einer überwältigenden Anzahl von Asset-Varianten führen, die bis in die Millionen reichen.

![Überprüfen](assets/product-visuals-example.png)

Die Integration von Adobe Commerce und Product Visuals löst diese Herausforderung durch die Automatisierung von Asset-Management-Workflows. Die Integration stellt sicher, dass digitale Assets, wie Produktbilder und Marketing-Inhalte, basierend auf der SKU oder anderen Schlüsselattributen dynamisch mit den entsprechenden Merchandising-Entitäten verknüpft werden, einschließlich Produkten und Kategorien in Adobe Commerce. Dieser Prozess optimiert den Betrieb und steigert die Effizienz, indem er Folgendes ermöglicht:

* **Nahtlose Installation und Konfiguration** - Merchandising-Teams und -Entwickler können die Integration schnell mit den bekannten Adobe-Tools und -Workflows einrichten.

* **Dynamic Asset Updates** Produktbilder und Marketing-Assets spiegeln automatisch die neuesten Änderungen in AEM Assets wider, sodass Storefronts präzise und relevant bleiben.

* **Optimiertes Katalogmanagement** Automatisiert die Aktualisierung und Bereinigung von Assets, minimiert den manuellen Aufwand und stellt einen konsistenten, gepflegten Produktkatalog sicher.

## Voraussetzungen für die Verwendung der Integration

Um diese Integration nutzen zu können, müssen Unternehmen die folgenden Anforderungen erfüllen:

* Aktive Lizenzen für Adobe Commerce, Adobe Experience Manager Assets und [AEM Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/dynamic/administering-dynamic-media).

* Adobe Commerce 2.4.5+

   * PHP 8.1, 8.2, 8.3 und 8.4

   * Composer 2.x

* Adobe Experience Manager ist mit [Adobe Experience Manager Assets as a Cloud Service bereitgestellt](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/overview)

* Der Adobe Commerce-Benutzer, der die Integration konfiguriert, muss Zugriff auf die [IMS-Organisation](https://experienceleague.adobe.com/de/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255) haben, in der das AEM Assets-Projekt bereitgestellt wird.

>[!BEGINSHADEBOX]

## Die wichtigsten geschäftlichen Vorteile

![check](assets/icon-check.png) **No Additional Cost**-Diese Integration wird für Händler, die die Lizenzanforderungen erfüllen, kostenlos bereitgestellt.

![check](assets/icon-check.png) **Official Adobe Solution** Von Adobe entwickelt, gepflegt und vollständig unterstützt, um Stabilität und Abstimmung mit zukünftigen Plattformverbesserungen sicherzustellen.

![Überprüfen](assets/icon-check.png) **Die Unterstützung und Fehlerbehebung durch das Adobe Managed Support-** werden direkt von Adobe durchgeführt, sodass Sie sich beruhigt auf Ihre Arbeit konzentrieren und Probleme effizient beheben können.

>[!ENDSHADEBOX]

In diesem Video erfahren Sie, wie Adobe Commerce und AEM Assets zusammenarbeiten, um Inhalts-Workflows zu optimieren:

>[!VIDEO](https://video.tv.adobe.com/v/3447837)

## Nächste Schritte

Die Aktivierung der Commerce-Integration mit Experience Manager Assets ist ein dreistufiger Prozess:

1. [Konfigurieren Sie Ihr AEM Assets-Projekt zur Unterstützung von Commerce-Metadaten](get-started/configure-aem.md).

1. [!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."} [Adobe Commerce-Pakete installieren](get-started/configure-commerce.md).

1. [Integration konfigurieren](get-started/setup-synchronization.md).

## Support

Wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden, wenden Sie sich an Ihren AEM Assets Integration-Vertriebsmitarbeiter oder erstellen Sie ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=de#submit-ticket), um zusätzliche Hilfe zu erhalten.
