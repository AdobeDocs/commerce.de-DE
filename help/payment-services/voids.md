---
title: Hohlräume
description: Leerstellen ermöglichen es Ihnen, das Geld auf einem Kredit- oder Debitkartenkonto freizugeben, das durch eine Autorisierung für den Betrag eines Kaufs gesperrt oder beiseite gehalten wird.
feature: Payments, Checkout
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Hohlräume

Mit [!DNL Payment Services] können Sie bestehende Commerce-Funktionen verwenden, um Transaktionen zu stornieren. Leerstellen ermöglichen es Ihnen, das Geld auf einem Kredit- oder Debitkartenkonto freizugeben, das durch eine Autorisierung für den Betrag eines Kaufs gesperrt oder beiseite gehalten wird.

>[!NOTE]
>
>Sie können eine Transaktion nur stornieren, wenn die Zahlung noch nicht erfasst wurde.

Wenn Ihr Store [konfiguriert](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} nur Mittel am Point-of-Sale zu autorisieren (nicht zu erfassen), führt ein Kauf in Ihrem Store zu einer Bestellung mit einem `Processing` in der Commerce-Admin.

Sie können auch [Bestellung stornieren](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order){target="_blank"} die nicht fakturiert wurde. Nicht erfasste Berechtigungen werden im Rahmen dieses Abbruchs ebenfalls ungültig gemacht.

>[!NOTE]
>
>Die Stornierung einer Bestellung führt auch zur Stornierung, aber die Stornierung einer Bestellung führt nicht zu einem Trigger der Stornierung.

Weitere Informationen zu den grundlegenden Schritten, die eine Bestellung durchläuft, finden Sie unter [Workflow bestellen](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing){target="_blank"} im Benutzerhandbuch zu Core.

Weitere Informationen zur Void-Funktion und zum Annullieren einer Bestelltransaktion finden Sie unter [Verarbeitung einer Bestellung](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#process-an-order){target="_blank"} im Benutzerhandbuch zu Core.
