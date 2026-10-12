---
title: Verfügbare Daten
description: Finanzberichterstattungsdaten verwenden, um die Berichterstellung mit Nicht-Commerce-Systemen abzustimmen.
role: User
level: Intermediate
exl-id: dbf41ce9-01f9-45d0-b651-e4c499e83822
feature: Payments, Checkout, Data Import/Export, Paas, Saas
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%
---
# Verfügbare Daten

Einige Auftrags- und Auszahlungsdaten stehen Ihnen zur Verfügung, damit Sie die Finanzberichterstattung von Adobe Commerce über externe Systeme hinweg koordinieren können.

## Mit ERP-System abstimmen

Sie können Adobe Commerce Financial Reporting mit Ihrem Nicht-Adobe Enterprise Resource Planning (ERP)-System abstimmen, indem Sie die Inkrement-ID verwenden, die mit einer bestimmten Bestellung verknüpft ist.

Wenn Payment Services die Commerce-Bestellung an PayPal sendet, wird die Inkrement-ID als `custom_id` _und_ in die `invoice_id` aufgenommen (die auch eine zufällige Zeichenfolge nach dem `increment_id` enthält).

Die IDs sind sowohl im Detail der Händleraktivität für eine Auszahlung als auch im PayPal-Webhook leicht zugänglich.

Die `invoice_id` und `custom_id` werden unten in den Details zur Händleraktivität für eine Auszahlung angezeigt:

![`custom_id` Details zur Aktivität Händler](assets/merchant-activity-ids.png){width="600" zoomable="yes"}

`custom_id` und `invoice_id` in den Details im Webhook von PayPal:

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

Weitere Informationen finden Sie in der Dokumentation zu den REST-APIs von PayPal:

* [`purchase_unit`, in dem sich `custom_id` und `invoice_id` befinden](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit)
* [Bestelldetails anzeigen](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
