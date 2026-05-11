---
title: Konfigurieren der Storefront
description: Erfahren Sie, wie Sie Ihre Edge Delivery Services-Storefront mit Ihrer AEM Assets-Integration verbinden.
feature: CMS, Media, Integration
TQID: https://experienceleague.adobe.com/gl0Y2UNs3sYkXE9QYwLtAltyX1dxE699y23ey-y0KUU
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: ae62cf09-5996-4921-bda8-fbe67b62e470
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 137
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
