---
title: Erste Schritte mit [!DNL Adobe Commerce as a Cloud Service]
description: Erfahren Sie mehr über die ersten Schritte mit [!DNL Adobe Commerce as a Cloud Service].
role: Admin, Developer, User
exl-id: 58d98b9e-b41d-44db-9666-c924a5b005b3
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: d8c0cf5f54a8518b033013cdb24b25f8ff363f02
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Erste Schritte

[!DNL Adobe Commerce as a Cloud Service] bietet die meisten vorkonfigurierten Konfigurationen. Nach Abschluss einiger grundlegender Einrichtungsprozesse ist Ihr Store in kürzester Zeit betriebsbereit. Dieses Handbuch führt Sie durch die Erstellung und Arbeit mit einer -Instanz.

Klicken Sie auf die folgenden Registerkarten, um allgemeine Workflow-Übersichten für die folgenden Benutzertypen anzuzeigen:

* Administratoren
* Händler
* Entwickler

>[!BEGINTABS]

>[!TAB Administrator- und Händler-Workflow]

Dieses Diagramm bietet einen allgemeinen Überblick darüber, wie Administratoren und Händler auf [!DNL Adobe Commerce as a Cloud Service]-Instanzen zugreifen und diese verwalten. Weitere Informationen zu Administrator-Workflows finden [ im Handbuch zu Adobe Admin Console ](https://helpx.adobe.com/de/enterprise/admin-guide.html).

![[!DNL Adobe Commerce as a Cloud Service] Handelsflussdiagramm](./assets/merchant-flow.svg){zoomable="yes"}

>[!TAB Entwickler-Workflow]

Dieses Diagramm bietet einen allgemeinen Überblick darüber, wie Entwickler Integrationen für [!DNL Adobe Commerce as a Cloud Service] mit App Builder erstellen. Weitere Informationen finden Sie in [ API](https://developer.adobe.com/commerce/webapi/rest/)Dokumentation.

![[!DNL Adobe Commerce as a Cloud Service] Flussdiagramm für Entwickler](./assets/developer-flow.svg){zoomable="yes"}

>[!ENDTABS]

## Instanz erstellen

>[!NOTE]
>
>Bevor Sie eine Instanz erstellen können, müssen Sie vom Produktadministrator oder Systemadministrator Ihres Unternehmens als Benutzer des [!DNL Adobe Commerce as a Cloud Service] Produkts hinzugefügt werden. Weitere Informationen finden [ unter „Hinzufügen von ](./user-management.md#add-users-and-admins) und Administratoren“.

[!DNL Adobe Commerce as a Cloud Service] Instanzen verwenden ein kreditbasiertes System. Sie können mehrere Instanzen erstellen, aber jede Instanz erfordert eine relative Menge an Credits. Die Höhe des Guthabens hängt zunächst von Ihrem Abonnement ab.

1. Melden Sie sich bei Ihrem [Adobe Experience Cloud](https://experience.adobe.com/)-Konto an.

1. Klicken Sie unter [!UICONTROL Quick access] auf [!UICONTROL **Commerce**], um die [!UICONTROL Commerce Cloud Manager] zu öffnen.

   Die [!UICONTROL Commerce Cloud Manager] zeigt eine Liste der [!DNL Adobe Commerce as a Cloud Service] Instanzen an, die in Ihrer Adobe IMS-Organisation verfügbar sind.

1. Klicken [!UICONTROL **oben rechts**] Bildschirm auf „Instanz hinzufügen“.

   ![Instanz erstellen](./assets/create-instance.png){width="50%" align="center" zoomable="yes"}

1. Wählen Sie [!UICONTROL **Commerce as a Cloud Service**].

1. Geben Sie **Name** und **Beschreibung** für Ihre Instanz ein.

1. Wählen Sie den [!UICONTROL **Umgebungstyp**] für Ihre Instanz aus. Sie können zwischen den folgenden Optionen wählen:

   * [!UICONTROL **Sandbox**] - Ideal für Design- und Testzwecke. Sie sollten Ihren [!DNL Adobe Commerce as a Cloud Service]-Journey mit der Sandbox-Umgebung beginnen.
   * [!UICONTROL **Produktion**] - Für Live-Stores und kundenorientierte Websites.

   >[!NOTE]
   >
   >* Sandbox-Instanzen sind auf die Region Nordamerika beschränkt.
   >* Die Option zum Installieren von Beispieldaten ist derzeit nicht verfügbar.

1. Wählen Sie die Region aus, in der Ihre Instanz gehostet werden soll.

   >[!NOTE]
   >
   >Nachdem Sie Ihre Instanz erstellt haben, können Sie die Region nicht mehr ändern.

1. Klicken Sie [!UICONTROL **Instanz hinzufügen**].

## Zugriff auf eine Instanz

Nachdem Sie eine Instanz erstellt haben, können Sie über die [!UICONTROL Commerce Cloud Manager] darauf zugreifen.

1. Melden Sie sich bei Ihrem [Adobe Experience Cloud](https://experience.adobe.com/)-Konto an.

1. Klicken Sie unter [!UICONTROL Quick access] auf [!UICONTROL **Commerce**], um die [!UICONTROL Commerce Cloud Manager] zu öffnen.

   Die [!UICONTROL Commerce Cloud Manager] zeigt eine Liste der Instanzen an, die in Ihrer Adobe IMS-Organisation verfügbar sind.

1. Um die [!UICONTROL Commerce Admin] für eine Instanz zu öffnen, klicken Sie auf den Instanznamen.

>[!TIP]
>
>Um Informationen zu Ihrer -Instanz, einschließlich der REST- und GraphQL-Endpunkte und der Admin-URL, anzuzeigen, klicken Sie auf das Informationssymbol neben dem Instanznamen.

## Importieren des Katalogs

Standardmäßig enthalten [!DNL Adobe Commerce as a Cloud Service] Instanzen keine Produktdaten. Sie haben die Möglichkeit, beim Erstellen einer Instanz zu Test- und Lernzwecken Beispielproduktdaten einzubeziehen, bevor Sie Ihren eigenen Katalog importieren.

Es gibt zwei Möglichkeiten, Ihren Katalog in [!DNL Adobe Commerce as a Cloud Service] zu importieren:

* [**Commerce Admin**](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/import/data-import) - Eine benutzerfreundliche Oberfläche, über die Sie Ihre Katalogdaten mit wenigen Klicks importieren können.
* [**JSON-API importieren**](https://developer.adobe.com/commerce/webapi/rest/modules/import/#import-json-api) - Eine REST-API, mit der Sie Ihre Katalogdaten programmgesteuert importieren können.

<!-- TODO

- Add guidance about how to choose which method to use
- Add guidance for new vs existing customers (cross-reference OR and _include file for migration content)

-->

## Einrichten der Storefront

Nachdem Sie eine -Instanz erstellt haben, können Sie mit dem [ Ihrer Edge Delivery Services-](storefront.md) für die Commerce-Storefront fortfahren.
