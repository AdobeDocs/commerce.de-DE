---
title: Einrichten der Storefront
description: Erfahren Sie, wie Sie das Tool für Strukturvorlagen ausführen, um Ihre Storefront  [!DNL Adobe Commerce as a Cloud Service] .
role: Developer
exl-id: 02928dc4-1777-483e-b0ee-b04fc813864d
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 408f28bdc20708022c8eca0fbfea4adb17014bf7
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Einrichten der Storefront

Gehen Sie wie folgt vor, um Ihre Adobe Commerce-Storefront mit Edge Delivery Services für Adobe Commerce as a Cloud Service (SaaS) einzurichten.

Informationen zu einer anpassbareren und detaillierteren Anleitung finden Sie in der [Storefront-Dokumentation](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de).

1. Öffnen Sie das [Tool Site Creator](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator).

1. Wählen **Neue Site erstellen (Code und Inhalt)** aus.

1. Geben Sie die **GitHub-Organisation/den Benutzernamen** ein, in der Sie das Code-Repository für die Storefront erstellen möchten.

1. Geben Sie einen **Site-Namen** ein.

1. Geben Sie im Feld **Commerce GraphQL-Endpunkt (optional)** Ihren Adobe Commerce as a Cloud Service (SaaS) GraphQL-Endpunkt ein, auf den Sie im Commerce Cloud Manager zugreifen können, nachdem Sie [Ihre Instanz erstellt haben](./getting-started.md#create-an-instance).

   Wenn Sie „API Mesh[&#x200B; verwenden, geben &#x200B;](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic) alternativ Ihren API Mesh-GraphQL-Endpunkt in das Feld **Commerce GraphQL-Endpunkt (optional)** ein. Weitere [&#x200B; finden Sie unter &#x200B;](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic/create-mesh) erstellen .

1. Klicken Sie **Site erstellen**. Befolgen Sie die Anweisungen auf dem Bildschirm, um den Zugriff auf Ihr GitHub-Repository zu autorisieren.

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
* Weitere Informationen zum Aktualisieren von Website-Inhalten und zur Integration mit Commerce-Frontend-Komponenten und Backend-Daten finden Sie in der [Dokumentation zur Adobe Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de).
