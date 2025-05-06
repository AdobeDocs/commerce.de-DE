---
title: Commerce Services-Connector
description: Erfahren Sie, wie Sie Ihre Adobe Commerce- oder Magento Open Source-Instanz mithilfe von Produktions- und Sandbox-API-Schlüsseln in Services integrieren.
feature: Services, Saas
role: Admin, User
exl-id: 1aa6ba8b-be39-496e-b83d-a4a7db9f5dd8
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: be1c739f3821a5f1e846b3026088e3a3ff45a60f
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Einige Funktionen von Adobe Commerce und Magento Open Source basieren auf [!DNL Commerce Services] und werden als SaaS (Software as a Service) bereitgestellt. Um diese Services zu verwenden, müssen Sie Ihre [!DNL Commerce] mithilfe von Produktions- und Sandbox-API-Schlüsseln verbinden und den Datenspeicher in der [Konfiguration“ ](#saas-configuration). Sie müssen die Verbindung nur einmal für jede Instanz konfigurieren.

## Verfügbare Services {#availableservices}

Im Folgenden sind die [!DNL Commerce] Funktionen aufgeführt, auf die Sie über die [!DNL Commerce Services Connector] zugreifen können:

| Service | Verfügbarkeit |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) mit Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) mit Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce und Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/intro) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Architektur

Im Großen und Ganzen besteht die [!DNL Commerce Services Connector] aus den folgenden Kernelementen:

![Connector-Architektur für Commerce Services](assets/saas-config-sync-workflow.png)

In den folgenden Abschnitten werden diese Elemente ausführlicher behandelt.

## Anmeldeinformationen {#apikey}

The production and sandbox API keys are generated from the [!DNL Commerce] account of the [license owner](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding). The Commerce account is identified by a unique [!DNL Commerce] ID (MageID). The license owner for the merchant&#39;s organization can generate API keys for services like Product Recommendations or Live Search, as long as the account is in good standing.

The keys can be shared on a &quot;need-to-know&quot; basis with the systems integrator or development team that manages projects and environments on behalf of the license holder. Entwickler, denen vom Lizenzinhaber [!DNL Shared Access] erteilt wurde, können die Schlüssel nicht in ihrem Namen generieren, selbst wenn die Organisation des Händlers in der Dropdown-Liste &quot;[!DNL Switch Accounts]&quot; auf ihrem Konto vorhanden ist.

Darüber hinaus sind Lösungsintegratoren auch berechtigt, [!DNL Commerce Services] zu verwenden. Wenn Sie Lösungsintegrator sind, sollte der Unterzeichner des [!DNL Commerce] die API-Schlüssel generieren.

>[!NOTE]
>Die Schlüsselkennungen *Produktion* und *Sandbox* beziehen sich nicht auf Ihre Umgebung. Sie verwenden dieselben API-Schlüssel für jede Ihrer Umgebungen, z. B. lokale, Entwicklungs-, Staging- oder Produktionsumgebungen.
>
>Der Lizenzinhaber ist in der Regel der Primäre Ansprechpartner im Adobe Commerce-Konto und nicht immer derselbe wie der Projektbesitzer des Adobe Commerce on Cloud Infrastructure-Projekts.

### Erzeugen der Produktions- und Sandbox-API-Schlüssel {#genapikey}

1. Log in to your [!DNL Commerce] account at [https://account.magento.com](https://account.magento.com/customer/account/login){:target="_blank"}.

1. Under the **Magento** tab, select **API Portal** on the sidebar.

1. From the _Environment_ menu, select **Production** or **Sandbox**.

   >[!NOTE]
   >
   >*Produktion* und *Sandbox* beziehen sich auf die Datenspeicherumgebungen, in denen Daten in Adobe SaaS-Backend-Systemen gespeichert werden. It does not refer to commerce environment(s) where you will be using the keys.

1. Geben Sie im Abschnitt _API-Schlüssel_ einen Namen ein und klicken Sie auf **Neu hinzufügen**, um das Dialogfeld zum Herunterladen des neuen Schlüssels zu öffnen.

   ![Privaten Schlüssel herunterladen](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Dieses Dialogfeld bietet die einzige Möglichkeit, dass Sie Ihre Schlüssel kopieren oder herunterladen müssen.

1. Klicken Sie **Herunterladen** und anschließend auf **Abbrechen**.

1. Wiederholen Sie die obigen Schritte für jede Umgebung (Produktion und Sandbox).

   Im Abschnitt **API-Schlüssel** werden nun Ihre API-Schlüssel (öffentliche Schlüssel) angezeigt. Sie benötigen alle vier Schlüssel (Produktions- und Sandbox-Schlüssel, öffentlich+privat), wenn Sie [ein SaaS-Projekt auswählen oder erstellen](#createsaasenv) in einer der Umgebungen oder Installationen ausführen, die mit der Lizenz verbunden sind.

## SaaS-Konfiguration {#saasenv}

[!DNL Commerce] Instanzen müssen mit einem SaaS-Projekt und einem SaaS-Datenraum konfiguriert werden, damit [!DNL Commerce Services] Daten an den richtigen Speicherort senden können. Ein SaaS-Projekt gruppiert alle SaaS-Datenräume. Die SaaS-Datenräume dienen zur Erfassung und Speicherung von Daten, die [!DNL Commerce Services] eine reibungslose Arbeit ermöglichen. Einige dieser Daten werden möglicherweise aus der [!DNL Commerce]-Instanz exportiert und einige werden aus dem Käuferverhalten in der Storefront erfasst. Diese Daten werden dann im sicheren Cloud-Speicher aufbewahrt.

[!DNL Product Recommendations] enthält der SaaS-Datenbereich Katalog- und Verhaltensdaten. Sie können eine [!DNL Commerce]-Instanz auf einen SaaS-Datenbereich verweisen, indem [ sie ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) der [!DNL Commerce]-Konfiguration auswählen.

>[!WARNING]
>
> Use your **production SaaS data space** only on your production [!DNL Commerce] installation to avoid data collisions. Otherwise, you risk polluting your production site data with testing data, which causes deployment delays. For example, your production product data could be mistakenly overwritten from staging data, such as staging URLs.
> If this should happen, [submit a Support request](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview) to request data cleanup.

### SaaS data space provisioning

Alle Adobe Commerce-Händler können pro SaaS-Projekt auf einen Produktionsdatenbereich und zwei Testdatenbereiche zugreifen.

You can use the testing data spaces in any non-production environment as long as you don&#39;t use the same data space in multiple environments at the same time. To use the test data space in a different environment, perform a data cleanup before you select and configure the data space in that environment.

For Adobe Commerce Cloud Pro projects with multiple staging environments, you can request additional testing data spaces for each staging environment by [submitting a Support request](https://experienceleague.adobe.com/home?support-tab=home#support). However, if you only have one staging environment and require additional testing data spaces, you have the following options:
- Wenden Sie sich an das Customer Success-Team oder Ihren Customer Success Manager, um eine zusätzliche Staging-Umgebung anzufordern.
- [Submit a Support request](https://experienceleague.adobe.com/home?support-tab=home#support) to request the additional testing data space and indicate the business justification for the extra dataspace. This request is subject to approval.

Magento Open Source-Kunden, die Adobe Payment Services verwenden, können auch einen zusätzlichen Datenspeicher anfordern. Wenden Sie sich an das Zahlungs-Team, um die zusätzlichen Datenräume zu genehmigen, bevor Sie eine [Support-Anfrage](https://experienceleague.adobe.com/home?support-tab=home#support) einreichen, um den Testdatenraum anzufordern.

Kunden, die mehrere Cloud-Projekte oder lokale (Live-/Produktions-)Installationen besitzen, können auch zusätzliche Produktions- und Testdatenbereiche für jedes Projekt oder jede Instanz anfordern, indem sie [eine Support-Anfrage stellen](https://experienceleague.adobe.com/home?support-tab=home#support).

### SaaS-Projekt auswählen oder erstellen {#createsaasenv}

Um ein SaaS-Projekt auszuwählen oder zu erstellen, fordern Sie den [!DNL Commerce] API-Schlüssel vom [!DNL Commerce] Lizenzinhaber für Ihren Store an:

>[!NOTE]
>
> Wenn der Abschnitt **[!UICONTROL Commerce Services Connector]** in der [!DNL Commerce] nicht angezeigt wird, müssen Sie die [!DNL Commerce] für Ihren gewünschten [[!DNL Commerce] Dienst](#availableservices) installieren.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **System** > Services > **Commerce Services Connector**.

   Wenn der Abschnitt **[!UICONTROL Commerce Services Connector]** in der [!DNL Commerce] nicht angezeigt wird, installieren Sie die [!DNL Commerce] für Ihren gewünschten [[!DNL Commerce] Dienst](#availableservices). Vergewissern Sie sich außerdem, dass das `magento/module-services-id`-Paket installiert ist.

1. Fügen Sie in den Abschnitten _[!UICONTROL Sandbox API Keys]_&#x200B;und&#x200B;_[!UICONTROL Production API Keys]_ Ihre Schlüsselwerte ein.

   - Private Schlüssel müssen `----BEGIN PRIVATE KEY---` am Anfang des Schlüssels und `----END PRIVATE KEY----` am Ende des Schlüssels enthalten.
   - Wenn Sie keine Kopie der tatsächlichen Schlüssel haben, fragen Sie den Kontoinhaber nach diesen Schlüsseln und schließen Sie die Werte an die Konfiguration an.

   >[!WARNING]
   >
   > Wenn Sie Schlüsselwerte hinzufügen, indem Sie eine Datenbanksicherung oder einen Schnappschuss abfragen und die Werte in die Konfiguration einfügen, wird eine zusätzliche Verschlüsselungsschicht angewendet und die Schlüssel funktionieren nicht.

1. Klicken Sie **Speichern**.

Alle SaaS-Projekte, die mit Ihren Schlüsseln verknüpft sind, werden im Feld **Projekt** im Abschnitt **SaaS-Kennung** angezeigt.

1. Wenn keine SaaS-Projekte vorhanden sind, klicken Sie auf **Projekt erstellen**. Geben Sie dann im Feld **Projekt** einen Namen für Ihr SaaS-Projekt ein.

>[!NOTE]
>
>Um Verwirrung zu vermeiden, verwenden Sie keinen bestimmten Commerce-Service als Namen für Ihr Projekt, z. B. *Live Search*, *Product Recommendations* oder *Data Connection*.  Sofern Ihre Lizenz nicht für mehrere SaaS-Projekte bereitgestellt wurde, können Sie dasselbe SaaS-Projekt für mehrere Services verwenden.

1. Wählen Sie **Datenspeicher** aus, der für die aktuelle Konfiguration Ihres [!DNL Commerce] verwendet werden soll.

>[!NOTE]
>
>Wenn Sie über separate Instanzen verfügen, die in Commerce Services integriert werden können, [ Sie ein Support-Ticket ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket), um für jede weitere Instanz ein neues SaaS-Projekt anzufordern. Nachdem das SaaS-Projekt vom Support erstellt wurde, konfigurieren Sie die Commerce Services-Integration für die Instanz mit demselben API-Schlüssel und wählen Sie das neue SaaS-Projekt für den Datenspeicher aus.

>[!WARNING]
>
> Wenn Sie im Abschnitt „API-Portal“ von Mein Konto neue Schlüssel generieren, aktualisieren Sie die API-Schlüssel in der Admin-Konfiguration sofort. Wenn Sie neue Schlüssel generieren und im Admin nicht aktualisieren, funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Um die Namen Ihres SaaS-Projekts oder Datenraums zu ändern, klicken Sie neben einem **auf** Umbenennen. Das Ändern des Namens wirkt sich nicht auf Ihren Service aus, da der Name nur eine Bezeichnung ist, die Ihnen dabei hilft, Projekte und Datenräume zu identifizieren und zwischen ihnen zu unterscheiden.

## IMS-Organisation (optional) {#organizationid}

To connect your Adobe Commerce instance to the Adobe Experience Platform, sign in to your Adobe account using your Adobe ID. Nach der Anmeldung wird in diesem Abschnitt die IMS-Organisation angezeigt, die Ihrem Adobe-Konto zugeordnet ist.

## SaaS data export

When your [!DNL Commerce] instance successfully connects to [!DNL Commerce Services], the SaaS data export process exports Commerce data from your [!DNL Commerce] server to [!DNL Commerce SaaS Services] so it can be synchronized to connected Commerce Services. In the Admin, you can check synchronization status using the [Data Management dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). For details, see the [SaaS Data Export Guide](../data-export/overview.md).
