---
title: Hinzufügen von Attributen für Steuerklasse, Attributsatz und Bestand
description: Erfahren Sie, wie Sie die Produkt-Feed-Daten erweitern, um Attribute für die Steuerklassifizierung, den Attributsatz und erweiterte Inventareinstellungen einzuschließen.
role: Admin, Developer
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/
source-git-commit: dd8f518028c9f2025606e6620fc20156fceac9ce
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Hinzufügen von Attributen für Steuerklasse, Attributsatz und Bestand

Das Modul Zusätzliche Produktattribute von Adobe Commerce erweitert Produktdaten-Feeds. Sie enthält zusätzliche Produktattribute aus Adobe Commerce-Produktkonfigurationen:

* [Steuerklassifizierung](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/taxes/tax-class)
* [Attribut festgelegt](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-sets)
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

Weitere Informationen finden Sie unter [Überprüfen von Protokollen und Fehlerbehebung](troubleshooting-logging.md).

