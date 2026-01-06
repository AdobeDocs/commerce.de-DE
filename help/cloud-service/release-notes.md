---
title: '[!DNL Adobe Commerce as a Cloud Service] Versionshinweise'
description: Erfahren Sie mehr über die neuesten Funktionen und Verbesserungen in [!DNL Adobe Commerce as a Cloud Service].
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Developer, User, Leader
level: Beginner
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: cf06dec6-8d6b-413e-9977-df88373c188e
source-git-commit: 1ce3b6b6b94b1b4e94c0d34c081dec2884d7f0f8
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Versionshinweise

Die folgenden Versionshinweise enthalten Aktualisierungen zu [!DNL Adobe Commerce as a Cloud Service]. Versionsinformationen für andere Produkte finden Sie unter [Adobe Commerce Optimizer](../optimizer/release-notes.md) oder [Adobe Commerce On-Premise und Adobe Commerce on Cloud](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

[!DNL Adobe Commerce as a Cloud Service] enthält die neuesten Versionen von Merchandising-Services, Zahlungsdiensten und Erweiterbarkeitsversionen. Verwenden Sie die folgenden Links, um die jeweiligen Versionshinweise anzuzeigen:

* Dienste
   * [Katalog-Service](../catalog-service/release-notes.md)
   * [Live Search](../live-search/release-notes.md)
   * [Zahlungsdienste](../payment-services/release-notes.md)
   * [Produkt Recommendations](../product-recommendations/release-notes.md)
   * [SaaS-Datenexport](../data-export/release-notes.md)
* Erweiterbarkeit
   * [Admin-Benutzeroberfläche - SDK](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/release-notes/)
   * [API-Mesh](https://developer.adobe.com/graphql-mesh-gateway/mesh/release)
   * [Ereignisse](https://developer.adobe.com/commerce/extensibility/events/release-notes/)
   * [Webhooks](https://developer.adobe.com/commerce/extensibility/webhooks/release-notes/)

## November 2025

>[!BEGINSHADEBOX]

### Verbesserungen

* [Benutzerverwaltung](./user-management.md) - hat die Rolle **Produktadministrator** in der Admin Console geändert, um den Benutzerzugriff auf den Commerce-Administrator automatisch zu aktualisieren. <!-- CCSAAS-3012 -->

* Amazon Es wurde die Möglichkeit hinzugefügt, verhandelbare Angebotsanhänge sowie Dateien und Bilder, die mit Kunden und Kundenadressen verknüpft sind, mithilfe von vordefinierten URLs in [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/uploads) und [REST3 hochzuladen und ](https://developer.adobe.com/commerce/webapi/rest/modules/s3-uploads) abzurufen. Mit REST können Sie auch Kategoriebilder hochladen. <!-- CCSAAS-3250 -->

* Die Endpunkte `POST /V1/customers` und `PUT /V1/customers/{customerId}` wurden der [REST-API“ hinzugefügt](https://developer.adobe.com/commerce/webapi/rest/reference/) um Kunden zu erstellen und zu aktualisieren. Diese Endpunkte erfordern eine Admin-Autorisierung. <!-- CCSAAS-3112 -->

* Es wurde die [`exchangeOtpForCustomerToken`-Mutation hinzugefügt](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/exchange-otp-customer-token/) für die die E-Mail-Adresse eines Käufers und ein einmaliges Kennwort (One-Time Password, OTP) erforderlich sind und für die im Austausch ein Kunden-Token empfangen wird. Diese Mutation wird normalerweise in Szenarien verwendet, in denen sich ein Kunde mithilfe eines OTP authentifizieren muss, der an seine E-Mail oder sein Telefon gesendet wird.

* Wenn eine im Konfigurationsbildschirm [!UICONTROL **E-Mail-Adressen speichern**] im Admin-Bereich definierte Adresse einen Wert enthält, der auf `example.com` endet, sendet Commerce keine E-Mails an diese Adresse. Stattdessen protokolliert das System, dass die E-Mail nicht gesendet wurde.  <!-- CCSAAS-3533 -->

#### Benutzerdefinierte Bestellattribute

* Admin-Benutzer können jetzt [benutzerdefinierte Bestellattribute](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#custom-order-attributes) direkt in den Bildschirmen „Bestellansicht“, „Bearbeiten“ und „Erstellen“ im Admin-Bedienfeld anzeigen und bearbeiten. Diese Verbesserung verbessert die Verwaltung von benutzerdefinierten Bestelldaten, die über GraphQL erstellt wurden. <!-- CEXT-5044 -->

>[!ENDSHADEBOX]
