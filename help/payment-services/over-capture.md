---
title: Übererfassung
description: Erfahren Sie mehr über die Anforderungen und die Konfiguration der Übererfassung für die Payment Services-Erweiterung.
role: Admin, User
level: Intermediate
feature: Payments, Paas
source-git-commit: d2bcc58f34af50f26d4a4f082e5b3fc30089ab58
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%
---
# Übererfassung

Die Übererfassung ermöglicht es berechtigten Händlern mit einer PayPal-Übererfassung-Vereinbarung, bei der Fakturierung einer Bestellung mehr als den ursprünglich autorisierten Betrag zu erfassen. So kann sich beispielsweise der Endbetrag aufgrund gewichtsbezogener Anpassungen oder aufgrund von Änderungen bei den Materialkosten zwischen Zulassung und Erfüllung erhöhen.

PayPal bestimmt für jedes Händlerkonto das Limit für die Übererfassung. Durch die Aktivierung der Übererfassung in [!DNL Payment Services] wird keine Vereinbarung getroffen oder das von PayPal genehmigte Limit erhöht.

>[!NOTE]
>
>In diesem Thema wird die Übererfassung in der [!DNL Payment Services]-Erweiterung beschrieben. [!DNL Adobe Commerce as a Cloud Service] Informationen zu den separaten Verfügbarkeits- [&#x200B; Aktivierungsanforderungen finden Sie unter „Benutzerdefinierte &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/invoices#custom-capture-amounts)&quot;.

## Voraussetzungen

Vor der Aktivierung der Übererfassung:

* Übererfassung ist nur in [!DNL Payment Services] 2.17.0 oder höher verfügbar.
* Übererfassung steht nur US-Unternehmen zur Verfügung. Die [&#x200B; (Overcapture Requirements, PSD2)](https://www.paypal.com/us/cshelp/article/overcapture-requirements-psd2-help954) gelten auch für Händler in den USA, die im Europäischen Wirtschaftsraum (EWR) an PayPal-Käufer verkaufen.
* Eine Übererfassung ist für alternative Zahlungsmethoden (APMs) nicht verfügbar.
* Holen Sie sich eine Übernahmevereinbarung mit PayPal und bestätigen Sie das für Ihr Händlerkonto genehmigte Limit mit Ihrem PayPal-Account-Manager.
* Legen Sie die **[!UICONTROL Payment Action]** der Zahlungsmethode auf `Authorize` fest. Die Übererfassung gilt für autorisierte Bestellungen, die später bei der Fakturierung erfasst werden, nicht für Bestellungen, die automatisch mit `Authorize and Capture` erfasst werden. Siehe [Als  [!DNL Payment Services]  festlegen](production.md#set-payment-services-as-payment-method).

## Übererfassung aktivieren

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Wählen Sie die zu konfigurierende Website mit der Store-Bereichsauswahl aus.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_&#x200B;den Abschnitt&#x200B;_[!UICONTROL General Configuration]_ .
1. Legen Sie **[!UICONTROL Over Capture Enabled]** auf `Yes` fest.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

## Erfasst eine autorisierte Zahlung

Die Übererfassung erfolgt bei der Rechnungsstellung im Admin. Der angeforderte Erfassungsbetrag muss innerhalb des von PayPal für Ihr Händlerkonto genehmigten Limits liegen. Siehe [Erstellen einer Rechnung](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) für den Standard-Abrechnungs-Workflow.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Öffnen Sie eine Bestellung mit einer autorisierten Zahlung, die noch nicht erfasst wurde.
1. Klicken Sie auf **[!UICONTROL Invoice]**.
1. Geben Sie im Feld Benutzerdefinierter Erfassungsbetrag den zu erfassenden Gesamtbetrag ein. Wenn beispielsweise der autorisierte Betrag USD 100 lautet und die vereinbarte endgültige Gebühr USD 110 ist, geben Sie `110` ein, nicht `10`. Der angeforderte Betrag muss innerhalb Ihres von PayPal genehmigten Limits liegen.
1. Wählen Sie die Online-Erfassung für die Rechnung aus, um die Zahlung über den Zahlungsanbieter anzufordern.
1. Überprüfen Sie die Rechnung und klicken Sie auf **[!UICONTROL Submit Invoice]**.

### Erfassen mithilfe der Rechnung-API

Verwenden Sie den standardmäßigen Endpunkt [Rechnung erstellen](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-create-invoice):

```http
POST /rest/<store_code>/V1/order/<orderId>/invoice
```

Verwenden Sie den Store-Code für die Bestellung und die interne ID der Bestellung. Mit einem autorisierten Admin- oder Integrations-Token authentifizieren und `Content-Type: application/json`.

Die folgende Beispiel-Payload fordert eine vollständige Rechnung mit Online-Erfassung von USD 110 für eine Bestellung an, die für USD 100 autorisiert ist, sofern der PayPal-Vertrag des Händlers diesen Betrag zulässt:

```json
{
  "capture": true,
  "notify": false,
  "arguments": {
    "extension_attributes": {
      "custom_capture_amount": 110
    }
  }
}
```

In diesem Beispiel:

1. `capture` der Online-Erfassung.
1. `notify` steuert, ob Commerce die Rechnungsbenachrichtigungs-E-Mail sendet.
1. `custom_capture_amount` ist der zu erfassende Endbetrag und nicht die Erhöhung gegenüber dem genehmigten Betrag.

## Fehlerbehebung bei einer zurückgewiesenen Erfassung

Wenn PayPal eine Übererfassungsanfrage ablehnt:

* Vergewissern Sie sich, dass für das für die Zahlung verwendete PayPal-Händlerkonto ein Übernahmevertrag aktiv ist.
* Überprüfen Sie, ob der angeforderte Betrag innerhalb des genehmigten Limits liegt. Wenn er das Limit überschreitet, fordern Sie einen niedrigeren Betrag an oder wenden Sie sich an Ihren PayPal-Kundenbetreuer, um eine Erhöhung zu besprechen.
