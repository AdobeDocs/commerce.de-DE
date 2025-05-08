---
title: Hohlräume
description: Leerstellen ermöglichen es Ihnen, das Geld auf einem Kredit- oder Debitkartenkonto freizugeben, das durch eine Autorisierung für den Betrag eines Kaufs gesperrt oder beiseite gehalten wird.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '189'
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
