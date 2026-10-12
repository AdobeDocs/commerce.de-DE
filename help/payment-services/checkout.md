---
title: Checkout in [!DNL Payment Services]
description: Passen Sie [!DNL Payment Services] Checkout an die Bedürfnisse Ihrer Kunden an.
feature: Payments, Checkout, Paas, Saas
exl-id: 47df165f-2145-4e0e-b272-54b8e768cf19
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
source-wordcount: '343'
ht-degree: 0%
---

# Checkout in [!DNL Payment Services]

Sie können den Checkout für Adobe Commerce [!DNL Payment Services] so konfigurieren, dass er Ihren Kundinnen und Kunden am besten entspricht. Funktionen wie [automatische &#x200B;](#order-auto-voided-if-error) bestellen) und [Tresor für Kreditkarten](#credit-card-vaulting) stellen sicher, dass Ihre Kunden ein reibungsloses Benutzererlebnis haben.

## Bei Fehler automatisch storniert bestellen

Tritt während des Checkouts ein Fehler auf, wird die Bestellung automatisch storniert bzw. storniert [!DNL Payment Services].

Auf der Kaufbestätigungsseite wird eine Fehlermeldung für den Käufer angezeigt. Die Meldung kann variieren.

![Fehler beim Überprüfen](assets/user-checkout-error.png "Fehler beim Auschecken"){width="600" zoomable="yes"}

Ein Kommentar zur stornierten Bestellung wird auch im Administrator für eine bestimmte [Bestellung](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/orders?lang=en) angezeigt.

![Stornierter Bestellkommentar in Admin für Bestellung](assets/admin-checkout-error.png "Stornierter Bestellkommentar in Admin für Bestellung"){width="600" zoomable="yes"}

Wenn ein Käufer die Genehmigung für eine Bestellung erhält, die Bestellung jedoch nicht erstellt und in eine `Capture` umgewandelt wurde, wird die Bestellung automatisch storniert. Dadurch wird sichergestellt, dass kein Kredit auf der Kreditkarte des Käufers reserviert wird, und die Gebühr des Zahlungsdienstleisters vermieden, die anfällt, wenn die Autorisierung am Ende der standardmäßigen 29-Tage-Frist ungültig wird.

>[!NOTE]
>
>Die automatische Stornierung einer Bestellung tritt nur auf, wenn der Kunde eine Zahlungsmethode verwendet, die auf den `Authorize`-Modus, nicht auf den `Authorize and Capture`-Modus eingestellt ist.

## Checkout von der Produktseite

Wenn ein Kunde direkt über die Produktseite mit den Schaltflächen PayPal oder [!DNL Pay Later] auscheckt, wird nur der auf der aktuellen Produktseite dargestellte Artikel gekauft. Artikel, die sich bereits im Warenkorb des Kunden befinden, werden nicht zum Checkout-Ablauf hinzugefügt und nicht gekauft.

Mit dieser Funktion kann der Kunde schnell den Artikel kaufen, den er gerade anzeigt, während er zuvor zum Warenkorb hinzugefügte Artikel beibehält.
Wenn der Kunde die Bestellung storniert, wird der Artikel auf der aktuellen Produktseite zum Warenkorb des Kunden hinzugefügt.

Wenn ein Kunde über die Produktseite in den Checkout-Fluss eintritt, wird die Checkout-Seite vereinfacht: Die Ansicht zeigt nur auftragsbezogene Daten und Optionen an.

## Tresor mit Kreditkarte

Käufer können ihre Kreditkarteninformationen für zukünftige Käufe auf der Website-Ebene (jedes Geschäft innerhalb des Kontos desselben Händlers) Vault-nutzen oder „speichern“.

Siehe [Kreditkartenabwicklung](vaulting.md) für weitere Informationen
