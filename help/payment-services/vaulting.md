---
title: Kreditkartenabrechnung
description: Käufer können ihre Kreditkartendetails für zukünftige Käufe Vault-fähig machen (speichern).
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout, Paas, Saas
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Kreditkartenabrechnung

Konvertieren Sie einmalige Kunden mithilfe von Kreditkartenabrechnungen in treue Kunden. Angemeldete Kunden können ihre Kreditkartendaten speichern (oder in einen Tresor umwandeln), um sie in einem späteren Kauf für dasselbe oder ein anderes Geschäft im selben Händlerkonto zu verwenden.

## Vaulting aktivieren

Händler können in den [!DNL Payment Services]Einstellungen[&#x200B; Kreditkartenabrechnungen für ihre Geschäfte &#x200B;](configure-admin.md#card-vaulting).

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

1. Klicken Sie auf **[!UICONTROL Settings]**.

1. Schalten Sie die **[!UICONTROL Vault enabled]** ein. Weitere Informationen finden [&#x200B; unter  [!DNL Payment Services]](configure-admin.md#enable-payment-services)Aktivieren“.

## Vaulting ohne Kauf

Angemeldete Kunden können eine Zahlungsmethode im Dashboard „Mein Konto **wie folgt**:

1. Melden Sie sich bei ihrem **Mein Konto** auf der Storefront an.

1. Navigieren Sie im linken Navigationsbereich zu **[!UICONTROL Stored Payment Methods]** , um alle darin gespeicherten Zahlungsmethoden anzuzeigen.

   Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/payments/stored-payment-methods) Zahlungsmethoden.

1. Der Kunde klickt auf **[!UICONTROL Add New Card]**, um eine neue Karte zu speichern.

   ![Neue Karte hinzufügen](assets/add-new-card.png){width="400" zoomable="yes"}

   Der Kunde muss alle erforderlichen Details wie Karten- und Rechnungsinformationen angeben, um die Zahlungsmethode zu tresoren.
Alle Vault-Zahlungsmethoden verwenden die Rechnungsadresse, die beim Vault der Karte festgelegt wurde und auf dem PayPal-Konto des Käufers gespeichert wird. Der Kunde sieht möglicherweise eine andere Rechnungsadresse als die in Commerce angezeigte.

1. **[!UICONTROL Save New Card]** klicken

   ![Gespeicherte Zahlungsmethoden in meinem Konto](assets/stored-payment-methods.png){width="400" zoomable="yes"}

Gespeicherte Karten können bei der Bestellung verwendet werden:

![Verwendung gespeicherter Anmeldedaten für zukünftige Käufe](assets/use-stored-card.png){width="400" zoomable="yes"}

### Löschen einer gespeicherten Zahlungsmethode

Kunden können Tresor-Kreditkarten einfach aus den **gespeicherten Zahlungsmethoden** im **Mein Konto** löschen, indem sie für eine bestimmte Karte auf **Löschen** klicken.

## Vaulting einer Zahlungsmethode beim Checkout

Angemeldete Kunden können eine Kreditkarte während des Checkouts für spätere Käufe im aktuellen Geschäft oder anderen Geschäften innerhalb desselben Händlerkontos tresoren:

![Die Kreditkarte für die spätere Verwendung aufheben](assets/save-card-for-later.png){width="400" zoomable="yes"}

Commerce speichert ein Token, mit dem Kunden durch Abrufen ihrer gespeicherten Kreditkarteninformationen zukünftige Checkouts abschließen können. Eine Karte vom Kundenkonto oder während des Checkouts zu entfernen, führt zu unterschiedlichen Zahlungs-Token.

>[!WARNING]
>
> PayPal kann derzeit maximal fünf Tresorkarten speichern.

## Vaulting in der Admin-Instanz verwenden

Wenn ein Kunde über eine zuvor gedeckte Kreditkarte verfügt, kann ein Händler mit einer dieser gedeckten Zahlungsmethoden eine Folgebestellung für diesen Kunden in der Admin erstellen.

Sie können in Admin nur dann Vault-Karten verwenden, wenn der Kunde sowohl über ein bestehendes Konto als auch über ein gültiges Token verfügt, das von einer zuvor abgeschlossenen Zahlung im System gespeichert wurde.

So erstellen Sie in der Admin eine Bestellung für einen Kunden mit seiner Tresor-Kreditkarte:

1. [Bestellung erstellen und Produkte hinzufügen](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=de).
1. Wählen Sie _[!UICONTROL Payment & Shipping Information]_&#x200B;**[!UICONTROL Stored Cards]**&#x200B;als Zahlungsmethode aus.
1. Wählen Sie die gewünschte Zahlungsmethode mit Vault-Kreditkarte aus.
1. Nachdem Sie alle anderen erforderlichen Schritte für die Bestellung ausgeführt haben, [&#x200B; Sie sie &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=de#step-3%3A-submit-the-order).

   ![Verwenden Sie eine Vault-Kreditkarte in Admin für den Kunden](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## Sicherheit

Minimale Kreditkarteninformationen werden mit dem Käufer geteilt; er sieht nur die letzten vier Ziffern, das Ablaufdatum und die Marke seiner Vault-Kreditkarte. Kreditkartenangaben werden beim Zahlungsdienstleister gespeichert, um die [PCI](security.md#PCI-compliance)-Compliance zu erfüllen.
