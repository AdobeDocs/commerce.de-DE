---
title: Konfiguration für Händler
description: Richten Sie erweiterte Inventory management-Quellen als Händler ein.
role: Admin
level: Experienced
feature: Shipping/Delivery, Inventory, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 0%

---

# Konfiguration von Merchant Stores (Source)

Diese Lösung erweitert die nativen Inventory management-Funktionen durch Erweiterung der Lagerquellen um betriebliche Funktionen für Händler.

- Geografische Koordinaten für den Store-Standort hinzufügen
- Geben Sie die Quelle als [!DNL Store Pickup Location] an und geben Sie die verfügbaren Versandfunktionen an (Versand an Store, Versand aus Store).
- Geben Sie verfügbare Abholoptionen (im Geschäft oder am Straßenrand), benutzerdefinierte Abholanweisungen und andere Informationen an, um den Kunden Abholdetails und Anweisungen mitzuteilen

Die Begriffe _Quelle_ und _Standort des Handels_ werden synonym verwendet. Alle Datensätze sind Inventarquellen, Quellen können jedoch je nach den Konfigurationseinstellungen auch Händler-Speicherorte sein.

Verwalten Sie die Konfiguration von Merchant Stores über den Administrator: **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>Während des Einrichtungsprozesses kann es erforderlich sein, den Cache zu leeren, nachdem Sie Quellen erstellt oder vorhandene Quellen aktualisiert haben.

## **Allgemein**

<table>
<tbody>
<tr>
<th>Feld</th>
<th>Beschreibung</th>
<th>Umfang</th>
<th>Erforderlich</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Breitenkoordinate des Standorts des Handelsgeschäfts. Diese erforderlichen Informationen werden für die Standortsuche und die Platzierung von Karten im Storefront-Erlebnis verwendet. Der Wert muss mit der genauen Adresse des Speichers übereinstimmen, damit die Validierung erfolgreich ist.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Längskoordinate des Standorts des Händlergeschäfts. Diese erforderlichen Informationen werden für die Standortsuche und die Platzierung von Karten im Storefront-Erlebnis verwendet. Der Wert muss mit der genauen Adresse des Speichers übereinstimmen, damit die Validierung erfolgreich ist.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Bestimmen Sie die Quelle als verfügbaren Speicherort für die Store-Abholung. Diese Einstellung bestimmt, ob die Quelle synchronisiert und Besuchern angezeigt wird.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>Konfigurieren Sie die Ship-to-Store-Funktionen auf Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md) <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Breitenkoordinate des Standorts des Handelsgeschäfts. Diese erforderlichen Informationen werden für die Standortsuche und die Platzierung von Karten im Storefront-Erlebnis verwendet. Der Wert muss mit der genauen Adresse des Speichers übereinstimmen, damit die Validierung erfolgreich ist.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Längskoordinate des Standorts des Händlergeschäfts. Diese erforderlichen Informationen werden für die Standortsuche und die Platzierung von Karten im Storefront-Erlebnis verwendet. Der Wert muss mit der genauen Adresse des Speichers übereinstimmen, damit die Validierung erfolgreich ist.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Bestimmen Sie die Quelle als verfügbaren Speicherort für die Store-Abholung. Diese Einstellung bestimmt, ob die Quelle synchronisiert und Besuchern angezeigt wird.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>Konfigurieren Sie die Ship-to-Store-Funktionen auf Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>Konfigurieren Sie die Funktion „Ship-from-Store“ auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
<td>Konfigurieren Sie die Funktion „Ship-from-Store“ auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>



| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | Breitenkoordinate des Standorts des Handelsgeschäfts. Diese erforderlichen Informationen werden für die Standortsuche und die Platzierung von Karten im Storefront-Erlebnis verwendet. Der Wert muss mit der genauen Adresse des Speichers übereinstimmen, damit die Validierung erfolgreich ist. | Global | Ja |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | Längskoordinate des Standorts des Händlergeschäfts. Diese erforderlichen Informationen werden für die Standortsuche und die Platzierung von Karten im Storefront-Erlebnis verwendet. Der Wert muss mit der genauen Adresse des Speichers übereinstimmen, damit die Validierung erfolgreich ist. | Global | Ja |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | Bestimmen Sie die Quelle als verfügbaren Speicherort für die Store-Abholung. Diese Einstellung bestimmt, ob die Quelle synchronisiert und Besuchern angezeigt wird. | Global | Nein |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | Konfigurieren Sie die Ship-to-Store-Funktionen auf Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), **[!UICONTROL Enable Ship To Store]**. | Global | Nein |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | Konfigurieren Sie die Funktion „Ship-from-Store“ auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), [!UICONTROL Enable Ship From Store] | Global | Nein |

{style="table-layout:auto"}

## Konfiguration des Abholstandorts

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | Eine von zwei Abholoptionen. [!DNL In-Store Pickup] bezieht sich auf die Möglichkeit, einem Kunden zu erlauben, den Standort des Händlergeschäfts einzugeben, um seine Bestellung abzurufen. </br></br>Wenn diese Option aktiviert ist, wird sie dem Kunden möglicherweise während des Checkouts angezeigt. </br></br>Diese Option überschreibt auch die globale Konfiguration auf [!UICONTROL Enable In-store Pickup], die auf der [!UICONTROL Delivery Method] für [!UICONTROL In-store Pickup] konfiguriert wurde | Global | Nein |
| **Anleitung zur Abholung im Geschäft**</br>`Extension Attribute: store_pickup_instructions` | Eine anpassbare Nachricht, die dem Kunden in der E **Mail-Benachrichtigung „Bestellung bereit für Abholung im Store** zugestellt wird. | Global | Nein |
| **Am Bordrand zulassen**</br>`Extension Attribute: curbside_enabled` | Eine von zwei Abholoptionen. Die Auslieferung am Bordstein ermöglicht es einem Kunden, sein Fahrzeug an einem bestimmten Ort im Kaufhaus abzustellen. In diesem Szenario wird die Bestellung dem Kunden von einem Verkaufsassistenten zugestellt. </br></br>Wenn diese Option aktiviert ist, kann sie dem Kunden während des Checkouts angezeigt werden. Außerdem kann der Kunde gebeten werden, sein Fahrzeug und seinen Parkplatz während des Check-in-Prozesses zu beschreiben. </br></br>Mit dieser Option wird auch die globale Konfiguration für **Abholung am Bordstein aktivieren** überschrieben, die für die **Bereitstellungsmethode** für **Abholung im Geschäft konfiguriert wurde** | Global | Nein |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | Eine anpassbare Nachricht, die dem Kunden in der [!UICONTROL Order Ready For Pickup in Store] E-Mail-Benachrichtigung zugestellt wird. | Global | Nein |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | Die Anzahl der Minuten, die erforderlich sind, bevor eine Bestellung empfangen, abgeholt und zur Abholung bereit ist. </br></br>Diese Informationen werden verwendet, um Kunden auf der Website geschätzte Zeiten für die Bestellabholung anzuzeigen.</br></br> diese Option aktiviert ist, wird die globale Konfiguration für **Geschätzte Abholzeit** **überschrieben, die für die Versandmethode** in der **Abholung im Geschäft** Konfiguration konfiguriert ist. | Global | Nein |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | Beschriftung, die die Anzahl der Minuten anzeigt, bis eine Bestellung abholbereit ist.</br></br> Beim Anpassen dieser Beschriftung können Sie den Code &quot;%1“ verwenden, um Ihre **Geschätzte Abholzeit“**.</br></br> Festlegen dieser Option überschreibt die globale Konfiguration für [!UICONTROL Estimated Pickup Time Label], die für die [!UICONTROL Delivery Method] im [!UICONTROL In-store Pickup] konfiguriert sind. | Global | Nein |

### **Öffnungszeiten**

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | Die Zeitzone des Standorts des Händlergeschäfts. Legen Sie für jeden Tag die Öffnungs- und Schließzeiten fest.</br></br>Diese Einstellungen werden zur Optimierung der geschätzten Abholzeiten und in Fulfillment-Service-Berichten verwendet. | Global | Ja |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | Die Betriebszeiten für den Standort des Handelsgeschäfts. </br></br>Diese Informationen können zur Optimierung der geschätzten Abholzeiten und in Fulfillment-Service-Berichten verwendet werden. | Global | Ja |

### Konfigurieren der Optionen der Benutzeroberfläche für das Einchecken



| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | Geben Sie an, ob der Standort des Kaufhauses über Parkplätze für die Randabholung verfügt. </br></br>Wenn diese Option aktiviert ist, können Sie verfügbare Parkplätze konfigurieren. | Global | Nein |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | Geben Sie an, ob für Kunden während des Einkaufserlebnisses eine Parkplatzkennung erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde bei der Ankunft aufgefordert, seinen Parkplatz anzugeben. Wenn deaktiviert, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | Die verfügbaren Parkplätze stehen an diesem Einkaufsstandort für die Abholung am Bordstein zur Verfügung. Verwenden Sie die bereitgestellte Schnittstelle, um jeden Punkt zu benennen.</br></br> Sie müssen nicht jeden Parkplatz benennen, sondern nur die für die Bordsteinkante vorgesehenen. Beispielsweise können Sie Parkzeilen A-G zur Verfügung haben, aber nur die ersten 8 Punkte der Reihe A sind für die Aufnahme am Bordstein vorgesehen. In diesem Szenario können Sie acht Punkte definieren, z. B. A1, A2, A3 usw. | Global | Nein |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | Wenn diese Einstellung aktiviert ist, kann der Kunde seinen Parkplatz beim Einchecken beschreiben. | Global | Nein |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | Geben Sie an, ob die Erfassung der Fahrzeugfarbe vom Kunden beim Einchecken unterstützt werden soll. </br></br> Die verfügbaren Auswahlmöglichkeiten für [!UICONTROL Car Color] sind in der Admin-[ (Systemeinstellungen für das Eincheckerlebnis) ](check-in-experience-setup.md). | Global | Nein |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | Geben Sie an, ob beim Check-in eine Fahrzeugidentifizierung für Kunden erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde bei der Ankunft aufgefordert, die Farbe seines Fahrzeugs anzugeben. Wenn deaktiviert, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | Geben Sie an, ob die Abholung von Fahrzeughersteller beim Kunden während des Check-ins unterstützt werden soll.</br></br> Die verfügbaren Auswahlmöglichkeiten für [!UICONTROL Car Make] sind in der Admin-[ (Systemeinstellungen für das Eincheckerlebnis) ](check-in-experience-setup.md). | Global | Nein |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | Geben Sie an, ob beim Check-in eine Identifikation des Fahrzeugherstellers erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde bei der Ankunft aufgefordert, die Marke seines Fahrzeugs anzugeben. Wenn deaktiviert, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | Geben Sie an, ob die Erfassung zusätzlicher Informationen beim Einchecken durch den Kunden unterstützt werden soll. | Global | Nein |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | Geben Sie an, ob beim Einchecken zusätzliche Informationen für Kunden erforderlich sind. </br></br>Wenn diese Option aktiviert ist, wird der Kunde bei der Ankunft aufgefordert, zusätzliche Informationen einzugeben. Wenn deaktiviert, kann der Kunde diese Eingabe überspringen. | Global | Nein |
