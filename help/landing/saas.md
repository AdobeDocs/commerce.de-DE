---
title: Commerce Services-Connector
description: Erfahren Sie, wie Sie Ihre Adobe Commerce- oder Magento Open Source-Instanz mithilfe von Produktions- und Sandbox-API-Schlüsseln in Services integrieren.
feature: Services, Saas
role: Admin, User
exl-id: 1aa6ba8b-be39-496e-b83d-a4a7db9f5dd8
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: ae672ed3f2693e2f14e8c7f379e59ef117a34fc3
workflow-type: tm+mt
source-wordcount: '1486'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Einige Funktionen von Adobe Commerce und Magento Open Source basieren auf [!DNL Commerce Services] und werden als SaaS (Software as a Service) bereitgestellt. Um diese Services zu verwenden, müssen Sie Ihre [!DNL Commerce] mithilfe von Produktions- und Sandbox-API-Schlüsseln verbinden und den Datenspeicher in der [Konfiguration“ &#x200B;](#saas-configuration). Sie müssen die Verbindung nur einmal für jede Instanz konfigurieren.

## Verfügbare Services {#availableservices}

Im Folgenden sind die [!DNL Commerce] Funktionen aufgeführt, auf die Sie über die [!DNL Commerce Services Connector] zugreifen können:

| Service | Verfügbarkeit |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) mit Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) mit Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/guide-overview.md) | Adobe Commerce und Magento Open Source |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Architektur

Im Großen und Ganzen besteht die [!DNL Commerce Services Connector] aus den folgenden Kernelementen:

![Connector-Architektur für Commerce Services](assets/saas-config-sync-workflow.png)

In den folgenden Abschnitten werden diese Elemente ausführlicher behandelt.

## Anmeldeinformationen {#apikey}

Die Produktions- und Sandbox-API-Schlüssel werden aus dem [!DNL Commerce] Konto des [Lizenzinhabers](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding) generiert. Das Commerce-Konto wird durch eine eindeutige [!DNL Commerce]-ID (MageID) identifiziert. Der Lizenzinhaber für die Organisation des Händlers kann API-Schlüssel für Services wie Produktempfehlungen oder Live Search generieren, solange das Konto gut aufgestellt ist.

Die Schlüssel können auf einer „Need-to-know“-Basis mit dem Systemintegrator oder dem Entwicklungsteam geteilt werden, das Projekte und Umgebungen im Namen des Lizenzinhabers verwaltet. Entwickler, denen vom Lizenzinhaber [!DNL Shared Access] erteilt wurde, können die Schlüssel nicht in ihrem Namen generieren, selbst wenn die Organisation des Händlers in der Dropdown-Liste &quot;[!DNL Switch Accounts]&quot; auf ihrem Konto vorhanden ist.

Darüber hinaus sind Lösungsintegratoren auch berechtigt, [!DNL Commerce Services] zu verwenden. Wenn Sie Lösungsintegrator sind, sollte der Unterzeichner des [!DNL Commerce] die API-Schlüssel generieren.

>[!NOTE]
>Die Schlüsselkennungen *Produktion* und *Sandbox* beziehen sich nicht auf Ihre Umgebung. Sie verwenden dieselben API-Schlüssel für jede Ihrer Umgebungen, z. B. lokale, Entwicklungs-, Staging- oder Produktionsumgebungen.
>
>Der Lizenzinhaber ist in der Regel der Primäre Ansprechpartner im Adobe Commerce-Konto und nicht immer derselbe wie der Projektbesitzer des Adobe Commerce on Cloud Infrastructure-Projekts.

### Erzeugen der Produktions- und Sandbox-API-Schlüssel {#genapikey}

1. Melden Sie sich bei Ihrem [!DNL Commerce] Konto unter [https://account.magento.com](https://account.magento.com/customer/account/login){:target="_blank"} an.

1. Wählen Sie auf der Registerkarte **&#x200B;**&#x200B;Magento **in der** die Option „API-Portal“ aus.

1. Wählen Sie im _Umgebung_ die Option **Produktion** oder **Sandbox**.

   >[!NOTE]
   >
   >*Produktion* und *Sandbox* beziehen sich auf die Datenspeicherumgebungen, in denen Daten in Adobe SaaS-Backend-Systemen gespeichert werden. Es bezieht sich nicht auf Commerce-Umgebung(en), in der Sie die Schlüssel verwenden werden.

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

[!DNL Product Recommendations] enthält der SaaS-Datenbereich Katalog- und Verhaltensdaten. Sie können eine [!DNL Commerce]-Instanz auf einen SaaS-Datenbereich verweisen, indem [&#x200B; sie &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) der [!DNL Commerce]-Konfiguration auswählen.

>[!WARNING]
>
> Verwenden Sie Ihren **Produktions-SaaS** Datenspeicher nur in Ihrer Produktions- [!DNL Commerce] -Installation, um Datenkollisionen zu vermeiden. Andernfalls riskieren Sie, die Daten Ihrer Produktions-Website mit Testdaten zu belasten, was zu Bereitstellungsverzögerungen führt. Beispielsweise könnten Ihre Produktionsproduktdaten versehentlich aus Staging-Daten wie Staging-URLs überschrieben werden.
> In diesem Fall können Sie [eine Support-Anfrage senden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview) um eine Datenbereinigung anzufordern.

Wenn Sie LiveSearch-Konfigurationsfelder im Admin Panel nicht finden können, überprüfen Sie, ob Sie den richtigen SaaS-API-Schlüssel eingegeben haben.  Stellen Sie sicher, dass Sie beim Konfigurieren des Produktionsdatenspeichers den Produktions-SaaS-Schlüssel und beim Konfigurieren des Staging-Datenspeichers den Staging-Schlüssel hinzugefügt haben. Wenn Sie den falschen Schlüssel konfigurieren, sind SaaS-Services wie LiveSearch in der Adobe Commerce-Umgebung nicht verfügbar.

### SaaS-Datenspeicherbereitstellung

Alle Adobe Commerce-Händler können pro SaaS-Projekt auf einen Produktionsdatenbereich und zwei Testdatenbereiche zugreifen.

Sie können die Testdatenräume in jeder Nicht-Produktionsumgebung verwenden, solange Sie nicht denselben Datenraum in mehreren Umgebungen gleichzeitig verwenden. Um den Testdatenspeicher in einer anderen Umgebung zu verwenden, führen Sie eine Datenbereinigung durch, bevor Sie den Datenspeicher in dieser Umgebung auswählen und konfigurieren.

Bei Adobe Commerce Cloud Pro-Projekten mit mehreren Staging-Umgebungen können Sie zusätzliche Testdatenbereiche für jede Staging-Umgebung anfordern, indem Sie [eine Support-Anfrage senden](https://experienceleague.adobe.com/home?support-tab=home#support). Wenn Sie jedoch nur über eine Staging-Umgebung verfügen und zusätzliche Testdatenbereiche benötigen, haben Sie die folgenden Optionen:

- Wenden Sie sich an das Customer Success-Team oder Ihren Customer Success Manager, um eine zusätzliche Staging-Umgebung anzufordern.

- [Senden einer Support-Anfrage](https://experienceleague.adobe.com/home?support-tab=home#support) , um den zusätzlichen Testdatenbereich anzufordern und die geschäftliche Begründung für den zusätzlichen Datenbereich anzugeben. Diese Anfrage muss genehmigt werden.

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
>Wenn Sie über separate Instanzen verfügen, die in Commerce Services integriert werden können, [&#x200B; Sie ein Support-Ticket &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket), um für jede weitere Instanz ein neues SaaS-Projekt anzufordern. Nachdem das SaaS-Projekt vom Support erstellt wurde, konfigurieren Sie die Commerce Services-Integration für die Instanz mit demselben API-Schlüssel und wählen Sie das neue SaaS-Projekt für den Datenspeicher aus.

>[!WARNING]
>
> Wenn Sie im Abschnitt „API-Portal“ von Mein Konto neue Schlüssel generieren, aktualisieren Sie die API-Schlüssel in der Admin-Konfiguration sofort. Wenn Sie neue Schlüssel generieren und im Admin nicht aktualisieren, funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Um die Namen Ihres SaaS-Projekts oder Datenraums zu ändern, klicken Sie neben einem **auf** Umbenennen. Das Ändern des Namens wirkt sich nicht auf Ihren Service aus, da der Name nur eine Bezeichnung ist, die Ihnen dabei hilft, Projekte und Datenräume zu identifizieren und zwischen ihnen zu unterscheiden.

## IMS-Organisation (optional) {#organizationid}

Um Ihre Adobe Commerce-Instanz mit der Adobe Experience Platform zu verbinden, melden Sie sich mit Ihrer Adobe ID bei Ihrem Adobe-Konto an. Nach der Anmeldung wird in diesem Abschnitt die IMS-Organisation angezeigt, die Ihrem Adobe-Konto zugeordnet ist.

## SaaS-Datenexport

Wenn Ihre [!DNL Commerce]-Instanz erfolgreich eine Verbindung mit [!DNL Commerce Services] herstellt, exportiert der SaaS-Datenexportprozess Commerce-Daten von Ihrem [!DNL Commerce]-Server nach [!DNL Commerce SaaS Services], damit sie mit verbundenen Commerce-Services synchronisiert werden können. Im Admin-Bereich können Sie den Synchronisierungsstatus mithilfe des [Daten-Management-Dashboards“ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard). Weitere Informationen finden Sie im [SaaS-Datenexporthandbuch](../data-export/overview.md).
