---
title: Erstattungen
description: Erstellen Sie Rückerstattungen  [!DNL Payment Services]  Bestellungen im Admin-Bereich im Rahmen des Gutschriftvorgangs.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Erstattungen

Rückerstattungen für [!DNL Payment Services] Bestellungen werden im Rahmen des Gutschriftenprozesses im Admin-Bereich erstellt. Eine Gutschrift ist ein Dokument, das den dem Kunden geschuldeten Betrag für eine vollständige oder teilweise Rückerstattung anzeigt, der auf einen Kauf angerechnet oder dem Kunden direkt zurückerstattet werden kann. Gutschriften können nur für Aufträge ausgestellt werden, die [fakturiert](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"}.

Weitere [&#x200B; und Informationen zum Ausstellen und Ausdrucken &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos){target="_blank"} Gutschriften finden Sie in unserem Core-Benutzerhandbuch unter „Gutschriften“.

Bei Bestellungen, die mit PayPal oder einer Kreditkarte bearbeitet werden, können Sie:

* Den gesamten Betrag der Bestellung zurückerstatten
* Rückerstattung eines Teilbetrags einer Bestellung (oder mehrerer Teilbeträge)
* Einen Betrag zurückerstatten, der kleiner ist als der Wert eines bestimmten Bestellartikels

Weitere Informationen [&#x200B; Sie im &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create){target="_blank"}-Benutzerhandbuch unter „Gutschrift ausstellen“.

>[!NOTE]
>
>Bei PayPal- oder Kreditkartenbestellungen tritt ein Fehler auf, wenn Sie versuchen, eine Bestellung teilweise für mehr als den verbleibenden Bestellbetrag zurückzuerstatten (ursprünglicher Betrag abzüglich der Summe der bestehenden Rückerstattungen) oder wenn Sie eine Rückerstattung für einen Betrag leisten, der größer als der gesamte Bestellbetrag ist.

Die [!UICONTROL Payment Action] in Ihrer [!UICONTROL Payment Settings]-Konfiguration - entweder `Authorize` oder `Authorize and Capture` - bestimmt den [Standard-Rückerstattungs-Workflow](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos#refund-workflow){target="_blank"} für Bestellungen.

Weitere Informationen finden Sie [&#x200B; Abschnitt &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create#payment-action-setting){target="_blank"}Zahlungsaktionseinstellung“ von _Ausstellen_ Gutschrift.
