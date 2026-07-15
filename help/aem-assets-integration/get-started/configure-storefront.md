---
title: Konfigurieren der Storefront
description: Erfahren Sie, wie Sie Ihre Edge Delivery Services-Storefront mit Ihrer AEM Assets-Integration verbinden.
feature: CMS, Media, Integration
TQID: https://experienceleague.adobe.com/gl0Y2UNs3sYkXE9QYwLtAltyX1dxE699y23ey-y0KUU
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2: id: ae62cf09-5996-4921-bda8-fbe67b62e470
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7f901cec90291e264376e3f93e6ebaaccf7c15f0
workflow-type: tm+mt
source-wordcount: 610
ht-degree: 0%

---

# Konfigurieren der Storefront

## Aktivieren der Anzeige von Produktbildern über AEM Assets {#enable-product-images}

Die AEM Assets-Integration zeigt Produktbilder aus AEM Assets anstelle von Adobe Commerce an und ermöglicht so erweiterte Optimierung, Zuschnitt und CDN-Bereitstellung.

Um die Integration in Commerce-Storefronts mit Edge Delivery Services zu aktivieren, fügen Sie den `"commerce-assets-enabled": true`-Parameter zur Konfigurationsdatei für Storefronts hinzu (`config.json`).

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

Weitere Informationen zur Verwendung von AEM Assets mit der Commerce-Storefront mit Edge Delivery Services finden Sie unter [AEM Assets-Integration](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-assets-configuration/) in der Dokumentation zu *Adobe Commerce Storefront*.

>[!TIP]
>
>Informationen zum Durchsuchen und Einfügen von AEM Assets in statische Inhaltsseiten durch Autorinnen und Autoren finden Sie unter [Verbinden von AEM Assets mit Da.live für die statische Inhaltserstellung](#connect-aem-assets-authoring).

## AEM Assets mit Da.live verbinden, um statische Inhalte zu erstellen {#connect-aem-assets-authoring}

>[!NOTE]
>
>Dieses Setup ist nicht mit der AEM Assets-Integrationserweiterung identisch. bereitgestellt von [Da.live](https://da.live){target="_blank"} ermöglicht es Autoren, durch das [!UICONTROL Library]-Bedienfeld und [!UICONTROL Content Advisor] zu navigieren und AEM Assets in statische Inhaltsseiten (z. B. Landingpages oder Inhaltsblöcke) einzufügen. Produktbilder, die über die AEM Assets-Integration synchronisiert werden, werden separat mithilfe der `commerce-assets-enabled` konfiguriert.

Führen Sie die folgenden Schritte aus, um AEM Assets mit einer Storefront für die Dokumenterstellung (Da.live) zu verbinden, sodass Autorinnen und Autoren beim Bearbeiten statischer Inhalte AEM Assets aus der **[!UICONTROL Content Advisor]** durchsuchen und einfügen können.

>[!NOTE]
>
>Detaillierte Setup-Anweisungen finden Sie unter [Einrichten von AEM Assets](https://docs.da.live/administrators/guides/setup-aem-assets){target=_blank} in der Dokumentation zu Da.live und [Integrieren von AEM Assets beim Erstellen von Inhalten für Edge Delivery Services](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/integrate-aem-assets-edge-delivery-services/integrate-aem-assets-edge-delivery-services){target=_blank} in der Dokumentation zu AEM Assets.

### Schritt 1: Öffnen Sie Ihre Site-Konfiguration in Da.live

1. Suchen Sie in [Da.live](https://da.live){target=_blank} Ihre Storefront und öffnen Sie sie.

1. Wählen Sie in der Breadcrumb-Navigation das Symbol **[!UICONTROL Settings]** neben Ihrem Site-Namen aus, um die Tabelle Site-Konfiguration zu öffnen.

### Schritt 2: AEM-Repository-URL kopieren

1. Wechseln Sie in einer neuen Registerkarte zu [experience.adobe.com](https://experience.adobe.com){target=_blank} und navigieren Sie zu **[!UICONTROL Experience Manager]**.

1. Adobe Experience Manager Assets öffnen : Scrollen Sie zum Abschnitt **[!UICONTROL My Authoring]** und wählen Sie dann **[!UICONTROL Assets]** neben Ihrer **[!UICONTROL Production]** aus.

1. Kopieren Sie in der Browser-Adressleiste das Segment, das mit `author` beginnt, bis einschließlich `.com`, z. B. `author-p107634-e1009805.adobeaemcloud.com`.

### Schritt 3: Repository-ID zu Ihrer Konfiguration hinzufügen

1. Um Ihre Site zu konfigurieren, kehren Sie zu Da.live zurück und wählen Sie in Ihrer Site-Konfiguration **[!UICONTROL data]** aus.

1. Füllen Sie die Tabelle wie folgt aus:

   | Zelle | Wert |
   |---|---|
   | A1 | `key` |
   | B1 | `value` |
   | A2 | `aem.repositoryId` |
   | B2 | Die in Schritt 2 kopierte URL |

1. Klicken Sie auf **[!UICONTROL Save]** und dann auf den Rückwärtspfeil neben Ihrem Site-Namen, um zum Site-Stamm zurückzukehren.

   >[!NOTE]
   >
   > Der Host mit dem `author-` Präfix durchsucht Assets aus der Autorenebene. Um Assets stattdessen über Dynamic Media bereitzustellen, verwenden Sie einen Host mit `delivery-` Präfix. Alle `aem.repositoryId` Optionen finden Sie unter [Einrichten von AEM Assets](https://docs.da.live/administrators/guides/setup-aem-assets){target=_blank}.

### Schritt 4: AEM Assets über die Bibliothek verbinden

1. Wählen Sie im Stammverzeichnis der Site den **[!UICONTROL index]** Ordner aus, um ihn zu öffnen.

1. Öffnen Sie im Editor das **[!UICONTROL Library]** und wählen Sie **[!UICONTROL AEM Assets]** aus.

   Das **[!UICONTROL Content Advisor]** Pop-up wird geöffnet und zeigt Ihre AEM Assets-Ordner und -Dateien an.

Ihre Storefront ist jetzt mit AEM Assets verbunden. Sie können Assets direkt aus dem **[!UICONTROL Content Advisor]** durchsuchen und einfügen.

## Verwandte Dokumentation

* [AEM Assets-Integration](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-assets-configuration/){target=_blank} in der Dokumentation zu *Adobe Commerce* Storefront - Storefront-Konfiguration und Bildverarbeitungsverhalten.

* [Integrieren Sie AEM Assets beim Erstellen von Inhalten für Edge Delivery Services](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/integrate-aem-assets-edge-delivery-services/integrate-aem-assets-edge-delivery-services){target=_blank} in der *AEM Assets*-Dokumentation.

* [Einrichten von AEM Assets](https://docs.da.live/administrators/guides/setup-aem-assets){target=_blank} und [Arbeiten mit Medien](https://docs.da.live/authors/guides/adding-media){target=_blank} in der Dokumentation zu Da.live .
