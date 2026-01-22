---
title: Einrichten der Storefront
description: Erfahren Sie, wie Sie das Tool für Strukturvorlagen ausführen, um Ihre Storefront  [!DNL Adobe Commerce as a Cloud Service] .
feature: Storefront
role: Developer
level: Beginner
exl-id: 02928dc4-1777-483e-b0ee-b04fc813864d
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 0cd9749574460374a8fe875f1eff54f2a4a8d614
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Einrichten der Storefront

Führen Sie die folgenden Schritte aus, um Ihre [!DNL Adobe Commerce Storefront] mit [!DNL Edge Delivery Services] für [!DNL Adobe Commerce as a Cloud Service] (SaaS) einzurichten.

Eine besser anpassbare und detailliertere Anleitung finden Sie in der [Storefront-Dokumentation](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de).

1. Öffnen Sie das [Tool Site Creator](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator).

1. Wählen Sie **[!UICONTROL Create New Site (Code & Content)]** aus.

1. Geben Sie die **[!UICONTROL Github Organization/Username]** ein, in der Sie das Code-Repository für die Storefront erstellen möchten.

1. Geben Sie einen **[!UICONTROL Site Name]** ein.

1. Geben Sie im Feld **[!UICONTROL Commerce GraphQL Endpoint (optional)]** Ihren [!DNL Adobe Commerce as a Cloud Service] (SaaS) GraphQL-Endpunkt ein, auf den Sie im Commerce Cloud Manager zugreifen können, nachdem Sie [&#x200B; Instanz erstellt &#x200B;](./getting-started.md#create-an-instance).

   Wenn Sie [[!DNL API Mesh]](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic) verwenden, geben Sie alternativ Ihren [!DNL API Mesh] GraphQL-Endpunkt in das Feld **[!UICONTROL Commerce GraphQL Endpoint (optional)]** ein. Weitere [&#x200B; finden Sie unter &#x200B;](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic/create-mesh) erstellen .

1. Klicken Sie auf **[!UICONTROL Create Site]**. Befolgen Sie die Anweisungen auf dem Bildschirm, um den Zugriff auf Ihr GitHub-Repository zu autorisieren.

Sobald der Prozess abgeschlossen ist, können Sie Ihre Storefront mit den folgenden Methoden anpassen:

* Code anpassen: `https://github.com/<username or org>/<repo name>`
* Inhalt bearbeiten: `https://da.live/#/<username or org>/<repo name>`
* Konfiguration verwalten: `https://da.live/sheet#/<username or org>/<repo name>/configs-stage`
* Vorschau der Storefront: `https://main--<repo name>--<username or org>.aem.page/`

## Nächste Schritte

Weitere Informationen finden Sie in den folgenden Artikeln:

* [Storefront-Inhalt aktualisieren](./use-cases.md#update-storefront-content) - Verwalten und Anzeigen von Inhalten und Daten in der Storefront.
* [Kontextuelles Experimentieren](./use-cases.md#contextual-experimentation) - Erstellen und verwalten Sie Experimente in Ihrer Storefront.
* [Varianten generieren](./use-cases.md#generate-variations) - Verwenden Sie generative KI, um die Erstellung hochwertiger Inhalte zu automatisieren.
* [Dokumentation zur Adobe Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de)—Hier erhalten Sie detaillierte Informationen zum Aktualisieren von Website-Inhalten und zur Integration mit Commerce-Frontend-Komponenten und Backend-Daten.
* [Konfigurations-Service](https://www.aem.live/docs/config-service-setup) - Erfahren Sie mehr über die Migration Ihrer Storefront-Konfiguration von `config.json` zur Verwendung des Konfigurations-Service, der erweiterte Anwendungsfälle wie die Konfiguration ohne Antwort und Überlagerungen unterstützt.
