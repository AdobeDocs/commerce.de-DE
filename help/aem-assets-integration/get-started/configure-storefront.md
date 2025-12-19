---
title: Konfigurieren der Storefront
description: Erfahren Sie, wie Sie Ihre Edge Delivery Services-Storefront mit Ihrer AEM Assets-Integration verbinden.
feature: CMS, Media, Integration
source-git-commit: d426c7878f7a66fe1047673be7c5bf65ae1949a7
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Konfigurieren der Storefront

Die AEM Assets-Integration zeigt Produktbilder an, die in AEM Assets verwaltet werden, anstatt in Adobe Commerce gehostete Bilder zu verwenden. Die Integration ermöglicht erweiterte Bildverwaltungsfunktionen wie erweiterte Optimierung, Zuschnitt und Bereitstellung über das Content Delivery Network (CDN) von Adobe.

Um die Integration in Commerce-Storefronts mit Edge Delivery Services zu aktivieren, aktualisieren Sie die Storefront-Konfigurationsdatei (`config.json`), um den `"commerce-assets-enabled": true` hinzuzufügen.

```json
{
  "public": {
    "default": {
      "commerce-assets-enabled": true
    }
  }
}
```

Die Commerce-Dropdown-Menüs erkennen automatisch die `commerce-assets-enabled`-Konfiguration und passen die Bildverarbeitung entsprechend an.

Weitere Informationen zur Verwendung von AEM Assets mit der Commerce-Storefront mit Edge Delivery Services finden Sie in der Storefront-Konfiguration, die im Thema [AEM Assets-Integration](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-assets-configuration/) in der Dokumentation zu *Adobe Commerce* Storefront beschrieben wird.
