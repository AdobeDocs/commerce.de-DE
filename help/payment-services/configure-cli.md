---
title: Befehlszeilenkonfiguration
description: Nach der Installation können Sie  [!DNL Payment Services]  über die Befehlszeilenschnittstelle (CLI) konfigurieren.
role: Admin, Developer
level: Intermediate
feature: Payments, Checkout, Configuration, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# Befehlszeilenkonfiguration

Nach der Installation von [!DNL Payment Services] können Sie diese einfach über [die Startseite](payments-home.md) oder die Befehlszeilenschnittstelle (CLI) konfigurieren.

## Konfigurieren des Datenexports

[!DNL Payment Services] kombiniert aus [!DNL Magento Open Source] und [!DNL Adobe Commerce] exportierte Auftragsdaten mit aggregierten Zahlungsdaten von Zahlungsdienstleistern, um nützliche Berichte zu erstellen. Die [!DNL Payment Services]-Erweiterung verwendet Indexer, um alle erforderlichen Daten für die Berichte effizient zu erfassen.

Informationen zu den in [!DNL Payment Services] Berichten verwendeten Daten finden Sie unter [Bericht zum Zahlungsstatus von Bestellungen](order-payment-status.md#data-used-in-the-report).

### Konfigurieren von Cron auf [!DNL Magento Open Source]

Wenn Sie einen `BY SCHEDULE` Indexmodus für [!DNL Magento Open Source] verwenden möchten, müssen Sie Cron konfigurieren. Siehe [Konfigurieren und Ausführen von cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs).

### Festlegen von Indexern

Bestelldaten werden exportiert und im Zahlungsdienst gespeichert, wobei einer von zwei Indexmodi verwendet wird: `ON SAVE` (Standard) oder `BY SCHEDULE` (empfohlen).

Die folgenden Indizes sind für [!DNL Payment Services]:

| Code | -Name | Beschreibung |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Kundenauftrags-Feed | Erstellt einen Index der Bestelldaten |
| `sales_order_status_data_exporter` | Feed für Auftragsstatus | Erstellt einen Index der Auftragsstatusdaten |
| `store_data_exporter` | Speichert Feed | Erstellt einen Index der Speicherdaten |

Um den Indexmodus für alle drei Indexer zu ändern, führen Sie Folgendes aus:

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Wenn Sie in Ihrem Befehl keine Indexer angeben, werden alle Indexer auf denselben Wert aktualisiert. Wenn Sie einen bestimmten Indexer ändern möchten, müssen Sie ihn in Ihrem Befehl auflisten.

Weitere Informationen zum manuellen Ändern des Modus eines Indexers finden Sie unter [Konfigurieren von Indexern](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers){target="_blank"} in der Entwicklerdokumentation. Informationen zum Ändern im Admin-Bereich finden Sie unter [Indexverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode){target="_blank"} im Benutzerhandbuch zu Core.

### Daten manuell neu indizieren

Sie können Daten manuell neu indizieren, anstatt darauf zu warten, dass sie automatisch auftreten. Weitere Informationen finden [ unter ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#reindex){target="_blank"} in [Verwalten ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers){target="_blank"} Indexer“.

Wenn `BY SCHEDULE` Modus festgelegt ist, verfolgt das System geänderte Entitäten und der Cron-Auftrag aktualisiert den Index für sie basierend auf einem festgelegten Zeitplan. Unter [Ausführen von cron über die Befehlszeile](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs#config-cli-cron-group-run) in [Konfigurieren und Ausführen von cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)) erfahren Sie, wie Sie die Trigger-Indizierung mithilfe von Cron-Aufträgen manuell durchführen.

### Senden von neu indizierten Daten an den Zahlungsdienst

Nachdem die Daten indiziert wurden, werden sie automatisch an [!DNL Payment Services] gesendet. Mit diesem Befehl können Sie auch den Prozess des Versands indizierter Daten manuell als Trigger festlegen:

```bash
bin/magento saas:resync --feed [feedName]
```

Verwenden Sie die folgenden Befehlsoptionen:

| Befehl | Beschreibung |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | Führt eine Neuindizierung des angegebenen Feeds durch und sendet sie an den entsprechenden Service |
| `bin/magento saas:resync --no-reindex` | Überspringt die Indizierung und sendet nicht synchronisierte Daten aus den Indizes |

Mit dem `--feed` können Sie angeben, welchen Feed Sie senden möchten:

| Futter | Beschreibung |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Auftrags-Feed im Produktionsmodus |
| `paymentServicesOrdersSandbox` | Auftrags-Feed im Sandbox-Modus |
| `paymentServicesOrderStatusesProduction` | Auftragsstatus im Produktionsmodus |
| `paymentServicesOrderStatusesSandbox` | Bestellstatus im Sandbox-Modus |
| `paymentServicesStoresProduction` | Stores im Produktionsmodus |
| `paymentServicesStoresSandbox` | Speichert im Sandbox-Modus |

Alle für die Berichte erforderlichen Daten werden automatisch an [!DNL Payment Services] gesendet, wenn cron konfiguriert und installiert ist. Sie können den Prozess des Sendens von Cron-Daten an [!DNL Payment Services] auch manuell mit einem Trigger versehen.

```bash
bin/magento cron:run --group payment_services_data_export
```

Weitere Informationen zur Neuindizierung und Indizierung finden Sie unter [Verwalten der ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)&quot; in der Entwicklerdokumentation.

## Konfigurieren der L2/L3-Verarbeitung

[!DNL Payment Services] können Daten der Ebenen 2 und 3 aus Kartenzahlungstransaktionen verarbeiten, um zusätzliche Informationen für Händler bereitzustellen.

>[!WARNING]
>
> Die Integration mit Level 2 und Level 3 Verarbeitung mit PayPal ist nur für US Händler verfügbar. Weitere Informationen finden [ in der ](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank}-Dokumentation für PayPal-Entwickler unter „Zahlungsabwicklung“.

Wenn Sie L2/L3-Verarbeitungsdaten für [!DNL Payment Services] verwenden möchten oder Fragen haben, wenden Sie sich bitte an Ihren [!DNL Payment Services] Account Manager.

Weitere Informationen zur in [!DNL Payment Services] verwendeten L2- und L3-Verarbeitung finden Sie unter [Verarbeitung der Ebenen 2 und 3](levels-card-payment-transactions.md).
