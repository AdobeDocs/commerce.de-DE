---
title: Lagerverwaltung für Produkte
description: Konfigurieren Sie die für Kunden verfügbaren Merchant Stock-Nachrichten und -Funktionen.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Lagerverwaltung für Produkte

Als Händler können Sie Adobe Commerce [Inventory management](https://experienceleague.adobe.com/de/docs/commerce-admin/inventory/introduction) Stock- und Quelloptionen verwenden. Darüber hinaus können Sie mit der Store Fulfillment-Lösung andere Optionen für die Verfügbarkeit von Inventaren steuern, die mit Ihrem Händlergeschäft verbunden sind.

- Heimlieferoption von Kaufhäusern

- Für Store-Abholung zulassen/verfügbar

- UPC/SKU/Andere eindeutige Produktkennungen

- Schwellenwert für nicht vorrätige Artikel

- Verringern des Lagerbestands von bestimmten Lagerorten auf Bestellung

Konfigurieren Sie die Stock-Optionen für Produkte über den Administrator: **[!UICONTROL Catalog > Products > Select Product]**

## **Produktaktienoptionen**

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Verfügbar für den Versand zu Hause** | <p>Legt die Verfügbarkeit des heimischen Versands (Ship-from-Store) für das Produkt fest. Wenn diese Option aktiviert ist, werden alle zugewiesenen Händlerlagerstandorte mit verfügbarem Inventar für das Produkt als für die Heimlieferung geeignet erachtet. Wenn diese Option deaktiviert ist, ist das Produkt nie für den Heimversand geeignet.</p>Normalerweise reicht es aus, diese Option auf Händlerebene festzulegen. Es kann jedoch Einzelfälle für bestimmte Produkte geben, z. B. solche, die unter Bundesversandbeschränkungen fallen. Diese sollten nicht für die Lieferung nach Hause infrage kommen.</p> | Website | Nein |
| **[!UICONTROL Available for Store Pickup]** | <p>Legen Sie die Verfügbarkeit der Store-Abholung für das Produkt fest. Wenn diese Option aktiviert ist, werden alle zugewiesenen Händlerstandorte mit verfügbarem Inventar für das Produkt als für die Option „Store-Abholung“ geeignet erachtet. Wenn diese Option deaktiviert ist, ist das Produkt nie für die Abholung vom Store geeignet.</p><p>Diese Option kann nützlich sein, um den Händlerbestand im System zu verfolgen, den Sie nicht über Ihren E-Commerce-Kanal verkaufen möchten.</p> | Website | Nein |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Dieses Attribut sollte als Produktattribut vorhanden sein und sich auf die **[!UICONTROL Barcode Source / Barcode Type]**-Einstellung beziehen. Dieses Attribut wird verwendet, um einen scannbaren Barcode für Ihre Produkte zu verfolgen. Dieser Wert wird möglicherweise gesendet, wenn eine Bestellung zur Kommissionierung an Ihre Händlerläden gesendet wird. Store-Associates können den Wert mit der Auswahlliste verwenden, um Produkte im Regal mithilfe eines Barcode-Scanners abzugleichen. | Shop-Ansicht | Nein |

{style="table-layout:auto"}

## Quellen für Inventar auf Produktebene

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | <p>Legen Sie den Lagerschwellenwert für den Artikel innerhalb jeder Quelle fest. Wenn der Bestand unter den Schwellenwert fällt, wird er an der Quelle als nicht vorrätig angesehen.</p><p>Um die globale Store-Konfigurationseinstellung zu verwenden, aktivieren Sie die Option **[!UICONTROL Use Default]** .</p> | Global | Nein |
| **[!UICONTROL Allow Store Pickup]** | <p>Legen Sie explizit fest, ob der Artikel unabhängig vom verfügbaren Inventar oder der Konfiguration des Händlerstandorts für die Abholung im Geschäft verfügbar ist.</p><p>Um die Einstellung auf Produktebene zu verwenden, deaktivieren Sie die Option [!UICONTROL Use Default] und treffen Sie Ihre Auswahl. Andernfalls wird diese Einstellung basierend auf der Konfiguration für **[!UICONTROL Allow In-Store Pickup]** ausgewählt, die für die Stock-Quelle festgelegt wird.</p> | Global | Nein |

{style="table-layout:auto"}

