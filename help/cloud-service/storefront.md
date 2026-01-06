---
title: Einrichten der Storefront
description: Erfahren Sie, wie Sie das Tool für Strukturvorlagen ausführen, um Ihre Storefront  [!DNL Adobe Commerce as a Cloud Service] .
feature: Storefront
role: Developer
level: Beginner
exl-id: 02928dc4-1777-483e-b0ee-b04fc813864d
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 6eda2197fde2e88292e58b2bb4fc4759f24da558
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Einrichten der Storefront

Führen Sie die folgenden Schritte aus, um Ihre [!DNL Adobe Commerce Storefront] mit [!DNL Edge Delivery Services] für [!DNL Adobe Commerce as a Cloud Service] (SaaS) einzurichten.

Eine besser anpassbare und detailliertere Anleitung finden Sie in der [Storefront-Dokumentation](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/).

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

* Weitere Informationen zum Verwalten und Anzeigen von Inhalten und Daten in der Storefront finden Sie unter [Storefront-Inhalte aktualisieren](./use-cases.md#update-storefront-content).
* Weitere Informationen zu Funktionen für kontextuelle Experimente finden Sie unter [Kontextuelle Experimente](./use-cases.md#contextual-experimentation).
* Weitere Informationen zur Verwendung der generativen KI zur Automatisierung der Erstellung hochwertiger Inhalte finden Sie unter [Varianten generieren](./use-cases.md#generate-variations).
* Weitere Informationen zum Aktualisieren von Website-Inhalten und zur Integration mit Commerce-Frontend-Komponenten und Backend-Daten finden Sie in der [[!DNL Adobe Commerce Storefront documentation]](https://experienceleague.adobe.com/developer/commerce/storefront/).
