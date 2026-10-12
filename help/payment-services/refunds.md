---
title: Erstattungen
description: Erstellen Sie Rückerstattungen für [!DNL Payment Services] Bestellungen im Admin-Bereich im Rahmen des Gutschriftvorgangs.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
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
source-wordcount: '305'
ht-degree: 0%
---
# Erstattungen

Rückerstattungen für [!DNL Payment Services] Bestellungen werden im Rahmen des Gutschriftenprozesses im Admin-Bereich erstellt. Eine Gutschrift ist ein Dokument, das den dem Kunden geschuldeten Betrag für eine vollständige oder teilweise Rückerstattung anzeigt, der auf einen Kauf angerechnet oder dem Kunden direkt zurückerstattet werden kann. Gutschriften können nur für Aufträge ausgestellt werden, die [fakturiert](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"}.

Weitere [ und Informationen zum Ausstellen und Ausdrucken ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos){target="_blank"} Gutschriften finden Sie in unserem Core-Benutzerhandbuch unter „Gutschriften“.

Bei Bestellungen, die mit PayPal oder einer Kreditkarte bearbeitet werden, können Sie:

* Den gesamten Betrag der Bestellung zurückerstatten
* Rückerstattung eines Teilbetrags einer Bestellung (oder mehrerer Teilbeträge)
* Einen Betrag zurückerstatten, der kleiner ist als der Wert eines bestimmten Bestellartikels

Weitere Informationen [ Sie im ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create){target="_blank"}-Benutzerhandbuch unter „Gutschrift ausstellen“.

>[!NOTE]
>
>Bei PayPal- oder Kreditkartenbestellungen tritt ein Fehler auf, wenn Sie versuchen, eine Bestellung teilweise für mehr als den verbleibenden Bestellbetrag zurückzuerstatten (ursprünglicher Betrag abzüglich der Summe der bestehenden Rückerstattungen) oder wenn Sie eine Rückerstattung für einen Betrag leisten, der größer als der gesamte Bestellbetrag ist.

Die [!UICONTROL Payment Action] in Ihrer [!UICONTROL Payment Settings]-Konfiguration - entweder `Authorize` oder `Authorize and Capture` - bestimmt den [Standard-Rückerstattungs-Workflow](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos#refund-workflow){target="_blank"} für Bestellungen.

Weitere Informationen finden Sie [ Abschnitt ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create#payment-action-setting){target="_blank"}Zahlungsaktionseinstellung“ von _Ausstellen_ Gutschrift.
