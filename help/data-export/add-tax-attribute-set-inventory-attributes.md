---
title: Hinzufügen von Attributen für Steuerklasse, Attributsatz und Bestand
description: Erfahren Sie, wie Sie die Produkt-Feed-Daten erweitern, um Attribute für die Steuerklassifizierung, den Attributsatz und erweiterte Inventareinstellungen einzuschließen.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/
TQID: https://experienceleague.adobe.com/AWc-yAn-TyiBXQONoF2ZG9SFjj2u92CKbKvAY8mEVEE
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: c1256247-af4b-46d8-9dca-0c654ecfa157id: c18ed297-2187-4aec-affb-9d9654eca6fcid: dac87252-6066-4d6e-a9d2-f6d84c323de7id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: c1579802-ddd4-4214-8a91-97b2066abe11id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 822
ht-degree: 0%

---

# Hinzufügen von Attributen für Steuerklasse, Attributsatz und Bestand

Das Modul Zusätzliche Produktattribute von Adobe Commerce erweitert Produktdaten-Feeds. Sie enthält zusätzliche Produktattribute aus Adobe Commerce-Produktkonfigurationen:

* [Steuerklassifizierung](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/taxes/tax-class)
* [Attributsatz](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-sets)
* [Inventar](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/product-options#advanced-product-options)

Nach der Installation funktioniert das Modul automatisch. Die zusätzlichen Attribute werden während der Produktsynchronisierung erfasst und exportiert. Es ist keine zusätzliche Konfiguration erforderlich.

## Die wichtigsten Vorteile

* **Automatische Verbesserung**: Reichert Produkt-Feeds mit Attributen der Steuerklasse, des Attributsatzes und des Bestands an
* **Nahtlose Integration**: Bietet einen grundlegenden Kontext für externe Systeme und Services
* **Konfiguration Null**: Funktioniert sofort nach der Installation
* **Echtzeit-Updates**: Wird automatisch mit Produktänderungen synchronisiert

## Funktionen und exportierte Attribute

Das Modul fügt Ihren vorhandenen Produktdaten-Feeds drei zusätzliche Attribute hinzu:

* `ac_tax_class`
* `ac_attribute_set`
* `ac_inventory`

### &#x200B;1. Steuerklasseninformationen (`ac_tax_class`)

**Zweck**: Stellt Informationen zur Steuerklassifizierung für jedes Produkt bereit

**Datenformat**: Zeichenfolgenwert, der den Namen der Steuerklasse enthält

**Beispielausgabe**:

```json
{
  "attributes": [
    {
      "code": "ac_tax_class",
      "values": ["Taxable Goods"]
    }
  ]
}
```

**Anwendungsfälle**:

Wenn Sie Steuerklassendaten in Commerce Catalog Services exportieren, werden diese Daten für Anwendungen verfügbar, die Folgendes unterstützen:

* Berichte zur Einhaltung der Steuervorschriften
* Integration mit externen Steuerberechnungs-Services
* Produktkategorisierung für Buchhaltungssysteme

### &#x200B;2. Informationen zu Attributsätzen (`ac_attribute_set`)

**Zweck**: Gibt an, welcher Attributsatz jedem Produkt zugewiesen ist

**Datenformat**: Zeichenfolgenwert, der den Namen des Attributsatzes enthält

**Beispielausgabe**:

```json
{
  "attributes": [
    {
      "code": "ac_attribute_set",
      "values": [
        "Default"
      ]
    }
  ]
}
```

**Anwendungsfälle**:

Wenn Sie Attributsatzdaten in Commerce Catalog Services exportieren, werden erweiterte Produktverwaltungsfunktionen in externen Systemen aktiviert. Zu diesen Funktionen gehören:

* Identifizierung der Produktvorlage
* Katalogverwaltung und -organisation
* Integration von Drittanbietersystemen, für die Attributsatzkontext erforderlich ist

### &#x200B;3. Erweiterte Inventardaten (`ac_inventory`)

**Zweck**: Liefert für jedes Produkt die Bestandsverwaltungseinstellungen

**Datenformat**: JSON-kodierte Zeichenfolge, die die Inventarkonfiguration enthält

**Enthaltene Felder**:

* `manageStock` (Boolesch): Ob die Lagerverwaltung aktiviert ist
* `cartMinQty` (Float): Minimale zulässige Menge im Warenkorb
* `cartMaxQty` (Float): Maximal zulässige Menge im Warenkorb
* `backorders` (Zeichenfolge): Rückstandsrichtlinie. Der Wert ist einer der folgenden:
   * `"no"`: Keine Nachbestellungen zulässig
   * `"allow"`: Menge unter 0 zulassen
   * `"allow_notify"`: Menge unter 0 zulassen und Kunde benachrichtigen
* `enableQtyIncrements` (Boolesch): Ob Mengeninkremente aktiviert sind
* `qtyIncrements` (Gleitkommazahl): Erforderlicher Inkrementwert für die Menge

**Beispielausgabe**:

```json
{
  "attributes": [
    {
      "code": "ac_inventory",
      "values": [
        "{\"manageStock\":true,\"cartMinQty\":2,\"cartMaxQty\":42,\"backorders\":\"no\",\"enableQtyIncrements\":false,\"qtyIncrements\":2}"
      ]
    }
  ]
}
```

**Anwendungsfälle**:

Wenn Sie Inventardaten in Commerce Catalog Services exportieren, werden erweiterte Inventarverwaltungsfunktionen in externen Systemen aktiviert. Zu diesen Funktionen gehören:

* Inventory management-Systemintegration
* Validierungsregeln für Einkaufswagen
* Optimierung des Auftragserfüllungsprozesses
* Anpassung des Kundenerlebnisses

## Verbesserung des Datenexport-Feeds

Das Modul Zusätzliche Produktattribute erweitert die vorhandenen Produkt-Feeds. Die neuen Attributdaten werden automatisch integriert.

* **Produkt-Feed** (`products`): Mit den drei zusätzlichen Attributen erweitert

   * Fügt jedem Produktdatensatz die Attribute `ac_tax_class`, `ac_attribute_set` und `ac_inventory` hinzu
   * Behält die ursprünglichen Produktdaten bei
   * Behält die Abwärtskompatibilität mit vorhandenen Feed-Verbrauchern bei

* **Feed „Produktattribute** (`productAttributes`): Mit Attributmetadaten für die neuen Attribute erweitert

   * registriert automatisch Metadaten für die drei neuen Attribute im `productAttributes`-Feed
   * Enthält Details zur Attributkonfiguration (Datentypen, Sichtbarkeitseinstellungen usw.)
   * Hilft externen Systemen, das neue Attributschema zu verstehen

## Installieren der Erweiterung

**Anforderungen**

* PHP 8.1, 8.2, 8.3 oder 8.4
* Adobe Commerce 2.4.4+
* [Adobe Commerce-Datenexporterweiterung](manage-extension.md#update-a-module-to-a-specific-version), Version 103.4.11 oder höher
* Zugriff auf [repo.magento.com](https://repo.magento.com)

  Informationen zum Generieren von Schlüsseln und Abrufen der erforderlichen Berechtigungen finden Sie unter [Abrufen Ihrer Authentifizierungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). Informationen zu Cloud-Installationen finden Sie im Handbuch zu [Commerce in Cloud-Infrastrukturen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Zugriff auf die Befehlszeile des Adobe Commerce-Anwendungsservers.

### Installationsschritte

Fügen Sie das Modul `adobe-commerce/module-extra-product-attributes` mit dem Composer hinzu:

```shell
composer require adobe-commerce/module-extra-product-attributes
```

Detaillierte Informationen zu den Installationsschritten finden Sie in den folgenden Handbüchern:

* [Installieren der Erweiterung auf Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/extensions)
* [Installieren der Erweiterung Adobe Commerce On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions)

## Produktdaten synchronisieren

Nach der erneuten Bereitstellung exportiert die Adobe Commerce-Instanz die zusätzlichen Daten automatisch während der Produktsynchronisierung. Sie können auch die `resync` CLI-Befehle verwenden, um die Synchronisierung sofort durchzuführen.

```shell
# Resync the products feed (includes the new attributes)
bin/magento saas:resync --feed=products
```

```shell
# Resync the product attributes feed (includes new attribute metadata)
bin/magento saas:resync --feed=productAttributes
```

## Fehlerbehebung

**Produkte ohne zusätzliche Attribute:**

* Stellen Sie sicher, dass das Modul ordnungsgemäß installiert und aktiviert ist
* Führen Sie die Befehle zur Neusynchronisierung aus, um die Produktdaten zu aktualisieren
* Überprüfen, ob Produkte gültige Steuerklassen- und Attributsatzzuweisungen haben

**Inventardaten erscheinen falsch:**

* Überprüfen Sie, ob die Inventareinstellungen in der Admin Console korrekt konfiguriert sind
* Auf Website-spezifische Inventar-Überschreibungen prüfen
* Überprüfen, ob das [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview)Modul ordnungsgemäß funktioniert

Weitere Informationen finden Sie im [Inventory management-Handbuch](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) in der *Adobe Commerce-Händlerdokumentation*.

**Leistungsprobleme:**

* Überwachen der Leistung des Exportprozesses nach der Installation
* Planen Sie die Neusynchronisierung in Zeiten geringen Traffics

### Protokollierung und Debugging

Das Modul protokolliert Exportfehler und -warnungen in das standardmäßige Commerce-Protokollierungssystem. Wenn bei der Produktsynchronisierung Probleme auftreten, überprüfen Sie die Datenexportprotokolle.

>[!MORELIKETHIS]
>
> * [Überprüfen Sie die Protokolle und führen Sie eine Fehlerbehebung durch](troubleshooting/logging.md)
> * [Erweitern und Anpassen von SaaS-Datenexport-Feeds](extensibility-and-customizations.md)
> * [Synchronisieren Sie Feeds mithilfe der Commerce-CLI](data-export-cli-commands.md)

