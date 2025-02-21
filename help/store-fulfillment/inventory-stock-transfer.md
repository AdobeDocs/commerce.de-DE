---
title: Inventory management Source-Übertragung
description: Konfigurieren Sie Stocks für  [!DNL Store Fulfillment solution]  mit Adobe Commerce Inventory management. Richten Sie ein neues Lager ein und transferieren Sie Inventar aus dem Standardlager, sodass Sie es Quellen zuweisen können, die so konfiguriert sind, dass sie die von der Store Fulfillment-Lösung benötigten Funktionen für die Store-Abholung aktivieren.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Inventory management Source-Übertragung

Die [!DNL Store Fulfillment] Lösung verwendet native Adobe Commerce Inventory management. Standardmäßig weist die [!DNL Commerce]-Konfiguration den gesamten Web-Bestand dem Standard-Lager zu, dem keine zusätzlichen Quellen zugewiesen werden können. Da einer Website nur ein einziger Bestand zugewiesen werden kann, muss ein Händler einen neuen Bestand konfigurieren und optional seinen standardmäßigen Quellbestand an eine Quelle übertragen, die dem entsprechenden Umfang zugewiesen ist. Anschließend kann die Quelle dem neuen Lager zugewiesen werden.

>[!IMPORTANT]
>
>Händler müssen die Standardquelle für alle Produkte beibehalten, die in Gruppen- und Bundle-Produktarten enthalten sind. Diese Produkte benötigen eine Lagermenge, die den Mindestmengenschwellenwert für Lagerartikel erfüllt und einen Lagerstatus von [!UICONTROL In Stock] aufweist.

Mit diesen Konfigurationsänderungen können Sie drei Dinge erreichen:

1. [Lager an Quelle übertragen](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/inventory-transfer), um das Lager aus dem Standardlager/der Standardquelle in das neue Lager/die neue Quelle zu verschieben.

1. [Massenzuweisung von ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/bulk-assignment)), um die neuen Quellen für alle Ihre Produkte hinzuzufügen.

1. [Massenaktualisierungen für Produktattribute abschließen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update) um die `Allow Store Pickup`- und `Allow Home Delivery` zu vorhandenen Produkten hinzuzufügen. Wenn die Lösung installiert ist, haben die Attribute die optimalen *Standard*-Werte. Diese Attribute werden jedoch erst dann auf vorhandene Produkte angewendet, wenn Sie den Massenaktualisierungsprozess abgeschlossen haben.

Der Lagerbestand wird von der ausgewählten Quelle abgezogen (Einzelhandelsspeicherort oder E-Commerce-Warehouse). Quellen, die als E-Commerce-Warehouses verwendet werden, müssen demselben Lager wie der Abholort des Geschäfts zugeordnet werden und vor den Einzelhandelsstandorten priorisiert werden. Weitere Informationen finden Sie unter [Priorisieren von Quellen für einen Bestand](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-prioritize-sources).

Weitere Informationen zum Verwalten von Bestand, Lagern und Quellen finden Sie in der Adobe Commerce-Benutzerdokumentation:

- [Verwalten von Inventar](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction)

- [Lagermengen verwalten](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/quantities-manage)

- [Verwalten von Lagern](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage)

- [Verwalten von Quellen](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage)

- [Priorisieren von Quellen für einen Bestand](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-prioritize-sources)

- [Massenaktualisierungen für Produktattribute](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update)


>[!IMPORTANT]
>
>Änderungen an der Konfiguration von Bestands- und Lagerbestandsquellen können sich auch auf nachgelagerte Systeme auswirken. Stellen Sie sicher, dass Sie verstehen, wie sich die Änderungen an der Bestandskonfiguration auf diese Systeme auswirken.
