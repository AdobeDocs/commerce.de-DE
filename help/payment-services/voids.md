---
title: Hohlräume
description: Leerstellen ermöglichen es Ihnen, das Geld auf einem Kredit- oder Debitkartenkonto freizugeben, das durch eine Autorisierung für den Betrag eines Kaufs gesperrt oder beiseite gehalten wird.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout, Paas, Saas
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%
---
# Hohlräume

[!DNL Payment Services] unterstützt die bestehende Funktionalität von Commerce zur Annullierung von Transaktionen. Eine Stornierung gibt Geld auf einem Kredit- oder Debitkartenkonto frei, das von einer Autorisierung für den Kaufbetrag gehalten wird. Transaktionen können nur storniert werden, wenn die Zahlung noch nicht erfasst wurde.

* Wenn Ihr Store [konfiguriert](https://experienceleague.adobe.com/de/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} nur Mittel am Point-of-Sale zu autorisieren (nicht zu erfassen), führt ein Kauf in Ihrem Store zu einer Bestellung mit einem `Processing` in der Commerce-Admin.

* Sie können auch [Bestellung stornieren](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order){target="_blank"} die nicht fakturiert wurde. Nicht erfasste Berechtigungen werden im Rahmen dieses Abbruchs ebenfalls ungültig gemacht.

>[!NOTE]
>
>Die Stornierung einer Bestellung führt auch zur Stornierung, aber die Stornierung einer Bestellung führt nicht zu einem Trigger der Stornierung.

Weitere Informationen zu den grundlegenden Schritten, die eine Bestellung durchläuft, finden Sie unter [Workflow bestellen](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/order-processing){target="_blank"} im Benutzerhandbuch zu Core.

Weitere Informationen zur Void-Funktion und zum Annullieren einer Bestelltransaktion finden Sie unter [Verarbeitung einer Bestellung](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/order-processing#process-an-order){target="_blank"} im Benutzerhandbuch zu Core.
