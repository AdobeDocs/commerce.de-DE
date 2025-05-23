---
title: Instanz verbinden
description: Verbinden Sie Ihre Commerce-Instanz mit einem API-Schlüssel und einem privaten Schlüssel und geben Sie den Datenspeicher in der Konfiguration an.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Paas
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: 0f2e9c3a7d990a46bafc5f3b8a083436d42643b5
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---


# Instanz verbinden

Sie verbinden Ihre Commerce-Instanz mithilfe eines API-Schlüssels und eines privaten Schlüssels und geben den Datenspeicher in der Konfiguration mithilfe des [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html?lang=de) an. **Sie richten diese Verbindung nur einmal ein.**

>[!VIDEO](https://video.tv.adobe.com/v/3448026?captions=ger)

>[!INFO]
>
> Weitere Informationen finden Sie in unserem [[!DNL Adobe Commerce] Services](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=de)Connector)-Video.

* Wenn Sie *bereits mit Ihrer Instanz verbunden* Ihre API-Anmeldeinformationen abgerufen und verwendet und Commerce Services konfiguriert haben, können Sie mit dem Schritt &quot;[ Ihrer Test-Sandbox einrichten“ ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html?lang=de).
* Wenn Sie weiterhin *Ihre Instanz verbinden müssen* finden Sie weitere Informationen in diesem Thema zum [ von API-Anmeldeinformationen ](#obtain-api-credentials) zum [ von Commerce Services](#configure-commerce-services).
* Wenn Sie sich nicht sicher *, ob Ihre Instanz verbunden ist*, navigieren Sie zu **System** > Services > **Commerce Services Connector** und zeigen Sie die öffentlichen und privaten API-Schlüsselwerte in den Abschnitten [!UICONTROL Sandbox Keys] und [!UICONTROL Production Keys] sowie die Felder *Projekt* und *Datenraum* im Abschnitt [!UICONTROL SaaS Identifier] an. Wenn diese Werte vorhanden sind, ist Ihre Instanz verbunden.

>[!NOTE]
>
>Alle für Payment Services berechtigten Händler können einen Produktionsdatenbereich und zwei Testdatenbereiche nutzen.

## Abrufen von API-Anmeldeinformationen

Um einen Commerce SaaS-Service zu nutzen, müssen Sie die API-Schlüssel Ihrer Instanz (den öffentlichen Commerce-API-Schlüssel und einen privaten Schlüssel) sowohl für die Sandbox als auch für die Produktion verwenden, die in Ihrem [Mein Konto-Dashboard“ erstellt und verwaltet ](https://account.magento.com/customer/account/login). [Das Schlüsselpaar](https://experienceleague.adobe.com/de/docs/commerce-admin/config/services/saas) kann für ein Commerce-Konto erstellt werden - eines für eine Sandbox und eines für die Produktion - obwohl jeweils nur ein Paar aktiv verwendet werden kann.

>[!NOTE]
>
>Benötigen Sie Hilfe beim Zugriff auf Ihr [!UICONTROL My Account]-Dashboard? Siehe [Erstellen eines Commerce-](https://experienceleague.adobe.com/de/docs/commerce-admin/start/commerce-account/commerce-account-create).

Nach der Erstellung ist ein öffentlicher API-Schlüssel immer in Ihrem My Account Dashboard verfügbar. Sie kann bei Bedarf kopiert oder gelöscht werden. Der private API-Schlüssel wird sichtbar, wenn Sie einen öffentlichen API-Schlüssel für die Sandbox oder die Produktion erstellen. Er steht nur zum Kopieren oder Speichern im daraufhin angezeigten Dialogfeld zur Verfügung und kann später nicht mehr aufgerufen werden.

Ein bestimmtes API-Schlüsselpaar gilt für alle Commerce-Services in einer Umgebung. Wenn Sie also bereits Commerce-Services für Ihre Instanz konfiguriert haben, ist Ihr API-Schlüsselpaar bereits im Commerce Services Connector vorhanden.

Wenn Ihr API-Schlüssel verloren geht, muss ein neues API-Schlüsselpaar [ (generiert](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html?lang=de#generate-an-api-key-and-private-key) und [angewendet](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html?lang=de#configure-saas-project) auf die Commerce Services Connector-Konfiguration in der Admin Console angewendet werden. Wenn die falschen Schlüssel konfiguriert sind oder keine in der Konfiguration vorhanden sind, wird in Payment Services ein Fehlerdialogfeld angezeigt, das Sie darüber informiert, dass das Konto nicht verifiziert wurde.

Siehe eine [Liste der verfügbaren Commerce-Services, die die -API verwenden](https://experienceleague.adobe.com/de/docs/commerce-merchant-services/user-guides/integration-services/saas#availableservices).

Informationen zum Generieren eines API-Schlüssels für Sandbox- oder Produktionsumgebungen finden Sie unter [Anmeldeinformationen](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html?lang=de#apikey).

>[!IMPORTANT]
>
>Es wird empfohlen, kein API-Schlüsselpaar neu zu generieren *und* die SaaS-Kennung und/oder den Datenspeicher in einer aktiven Produktionsinstanz zu ändern. Sie verlieren Daten für Ihre Instanz, wenn sie geändert werden.

## Konfigurieren von Commerce Services

Derselbe API-Schlüssel kann instanzenübergreifend verwendet werden, aber jede Instanz muss über einen eigenen [SaaS-Datenspeicher](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html?lang=de#saasenv) verfügen.

>[!NOTE]
>
>Händler müssen für ihre Zahlungsansprüche dieselben Schlüssel verwenden, die für die MageID generiert wurden.

Nachdem Sie Ihre Anmeldedaten erhalten haben, können Sie Ihr SaaS-Projekt und Ihren SaaS-Datenspeicher konfigurieren.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Klicken Sie auf **[!UICONTROL Configure Commerce Services]**.

   Diese Option ist sichtbar, wenn Sie Commerce Services noch nicht für Ihr Konto konfiguriert haben.

   Sie werden zum Konfigurationsbereich im Admin-Bereich, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**&#x200B;weitergeleitet, um Ihren Commerce Services-Connector zu konfigurieren.

1. Gehen Sie zur Konfiguration Ihrer Commerce-Services wie unter [SaaS-Konfiguration“ ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=de#saasenv).

   >[!INFO]
   >
   > Weitere Informationen finden Sie in unserem [[!DNL Adobe Commerce] Services](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=de#configuration-faqs)Connector)-Video.

## Endpunkt

[!DNL Payment Services] verwendet den [Commerce Services-Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html?lang=de) um eine Verbindung zu Commerce Services herzustellen und als SaaS bereitzustellen. Diese [!DNL Commerce Services Connector] kommuniziert über den Endpunkt unter:

* `commerce-beta.adobe.io` für Sandbox-Umgebungen.
* `commerce.adobe.io for` für Live-Umgebungen.
