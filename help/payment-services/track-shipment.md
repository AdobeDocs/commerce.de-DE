---
title: Verfolgen von Sendungen in [!DNL Payment Services]
description: Passen Sie [!DNL Payment Services] Sendungen und Tracking-Informationen an, die im PayPal-Händler-Dashboard angezeigt werden.
feature: Payments, Paas, Saas
exl-id: 17aede1f-56ae-441a-b723-3193e865e469
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
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
source-wordcount: '228'
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
