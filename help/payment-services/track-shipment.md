---
title: Verfolgen Sie Ihre Sendungen in [!DNL Payment Services]
description: ' [!DNL Payment Services]  Sendungen anpassen und Tracking-Informationen im PayPal-Händler-Dashboard angezeigt.'
feature: Payments
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Verfolgen von Sendungen in [!DNL Payment Services]

[!DNL Payment Services] können Händler die Tracking-Informationen für eine Sendung in ihrem PayPal-Händler-Dashboard einsehen.

Weitere [ zum Versandraster für Adobe Commerce finden ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/shipments){target=_blank} unter dem Thema „Sendungen“.

## Funktionsweise der Sendungsverfolgung

Diese Funktionalität hängt davon ab, ob die Bestellung in Rechnung gestellt wurde, da PayPal eine `capture_id` zur Verarbeitung der Tracking-Informationen erhalten muss. Wenn ein Händler seine Produkte vor der Erfassung ausliefert, werden die Tracking-Informationen nicht an PayPal gesendet.

>[!NOTE]
>
> Es wird empfohlen, pro Tracking-Nummer eine Sendung zu erstellen und der Sendung die richtigen Artikel zuzuordnen.

## Tracking-Nummer hinzufügen

Die folgenden Anweisungen führen Sie durch den Prozess zum Erstellen einer Sendung in Adobe Commerce mit [!DNL Payment Services]:

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.

1. Klicken Sie in der Spalte **[!UICONTROL Action]** für die ausgewählte Bestellung auf **[!UICONTROL View]**.

1. Klicken Sie auf **[!UICONTROL Ship]**.

1. Scrollen Sie nach unten zum **[!UICONTROL Payment & Shipping Method]** Block und klicken Sie in **[!UICONTROL Shipping Information]** auf **[!UICONTROL Add Tracking Number]** .

1. Legen Sie die **[!UICONTROL Carrier]** fest.

1. Geben Sie **[!UICONTROL Title]** und **[!UICONTROL Number]** ein, um die Sendung zu verfolgen.

1. Klicken Sie auf **[!UICONTROL Submit Shipment]**.

>[!NOTE]
>
> Alternativ können Sie ein Versandmodul verwenden, um die Tracking-Nummer einzugeben. Vergewissern Sie sich, dass das Versandmodul die Tracking-Nummer im Feld `tracking_number` speichert.

### Kompatibilität mit Dritten

Jede Erweiterung eines Drittanbieters ist mit der Funktionalität kompatibel, wenn eine Versandentität über die [Commerce-API erstellt ](https://developer.adobe.com/commerce/webapi/rest/attributes/#ShipmentRepositoryInterface){target=_blank}.
