---
title: Verhaltensereignisse
description: Erfahren Sie, welche Daten jedes Verhaltensereignis erfasst.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bcabccc9-8a2e-4045-9306-1d999bb75624
TQID: https://experienceleague.adobe.com/YS3jKQ3jmy76aeaqAp1PR8cGpD0euagdhoqL6CoMAnQ
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 467
ht-degree: 0%

---

# [!DNL Data Connection] Verhaltensereignisse

Im Folgenden sind die Commerce-Verhaltensereignisse aufgeführt, die bei der Installation der [!DNL Data Connection] verfügbar sind. Die von diesen Ereignissen erfassten Daten werden an die Adobe Experience Platform gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) erstellen, um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt werden.

Zusätzlich zu den Daten, die die folgenden Ereignisse erfassen, erhalten Sie auch [andere Daten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html?lang=de) bereitgestellt von der Adobe Experience Platform Web SDK.

Die Verhaltensereignisse erfassen anonymisierte Verhaltensdaten von Ihren Kundinnen und Kunden, während sie Ihre Website durchsuchen. Sie können die von diesen Ereignissen erfassten Daten verwenden, um Werbeaktionen und Kampagnen für eine bestimmte Gruppe von Käufern zu erstellen.

>[!NOTE]
>
>Alle Verhaltensereignisse umfassen das Feld [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html?lang=de) , das die E-Mail-Adresse des Käufers (sofern verfügbar) und die ECID enthält.

## Storefront-Ereignisse

Storefront-Ereignisse erfassen Daten aus den Interaktionen von Käufern auf der Website und umfassen Ereignisse wie `addToCart`, `pageView`, `createAccount`, `editAccount`, `startCheckout`, `completeCheckout`, `signIn`, `signOut` usw. Storefront-Ereignisse gelten nur für einfache und konfigurierbare Produkte.

Weitere Informationen zu Storefront[Ereignissen finden Sie &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#data-connection) der Entwicklerdokumentation .

## Kundenprofil-Ereignisse

Profilereignisse, die von der Storefront erfasst werden, enthalten Kontoinformationen wie `signIn`, `signOut`, `createAccount` und `editAccount`. Diese Daten werden verwendet, um wichtige Kundendetails auszufüllen, die erforderlich sind, um Segmente besser zu definieren oder Marketing-Kampagnen auszuführen, z. B. Sende-Anmelde-Rabattangebote, Kontoänderungsbestätigungen usw.

Weitere Informationen zu Kundenprofilereignissen finden [&#x200B; in der &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#data-connection) für Entwickler .

## Ereignisse suchen

Die Suchereignisse liefern Daten, die für die Absicht des Erstkäufers relevant sind. Die Absicht eines Käufers zu insight hilft Händlern zu erkennen, wie Käufer nach Artikeln suchen, worauf sie klicken und schließlich kaufen oder verlassen. Ein Beispiel für die Verwendung dieser Daten ist, wenn Sie bestehende Kunden ansprechen möchten, die nach Ihrem Top-Produkt suchen, das Produkt jedoch nie kaufen. Sie müssen die [[!DNL Live Search]](../live-search/install.md)-Erweiterung installieren, um auf diese Ereignisse zugreifen zu können.

Verwenden Sie die Felder `searchRequest.id` und `searchResponse.id`, die sowohl in den `searchRequestSent`- als auch in den `searchResponseReceived`-Ereignissen zu finden sind, um einen Querverweis zwischen einer Suchanfrage und der entsprechenden Suchantwort durchzuführen.

Weitere Informationen zu Suchereignissen finden [&#x200B; in &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#data-connection) Entwicklerdokumentation .

## B2B-Ereignisse

![B2B für Adobe Commerce](../assets/b2b.svg) Für B2B-Händler müssen [&#x200B; die `experience-platform-connector-b2b`-Erweiterung &#x200B;](install.md#install-the-b2b-extension)installieren“, um auf diese Ereignisse zugreifen zu können.

Die B2B-Ereignisse enthalten [Anforderungsliste](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html?lang=de) Informationen, z. B. ob eine Anforderungsliste erstellt, hinzugefügt oder gelöscht wurde. Durch die Verfolgung von für Anforderungslisten spezifischen Ereignissen können Sie sehen, welche Produkte Ihre Kunden häufig kaufen, und auf dieser Grundlage Kampagnen erstellen.

Weitere Informationen zu B2B[Ereignissen finden &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#data-connection) in der Entwicklerdokumentation .
