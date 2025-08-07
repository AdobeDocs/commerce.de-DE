---
title: Hinzufügen benutzerdefinierter Attribute zu Profilen
description: Erfahren Sie, wie Sie Kundenprofilen benutzerdefinierte Attribute hinzufügen.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 5489910382edc70eea5d7c0ca94da41c653b577d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Hinzufügen benutzerdefinierter Attribute zu Profilen

Benutzerdefinierte Profilattribute ermöglichen es Ihnen, die Identifizierung von Kundenprofilen in Experience Platform zu verbessern, indem Sie zusätzliche Kennungen verwenden, die über die standardmäßigen `customerId` und `emailId` hinausgehen. Diese zusätzlichen Kennungen ermöglichen einen präziseren Kundenabgleich und eine verbesserte Datenintegration zwischen der Commerce-Plattform und Experience Platform.

>[!NOTE]
>
>Erfahren Sie, wie [ Bestellungen „benutzerdefinierte Attribute ](custom-attributes.md)&quot; können.

## Vorteile

- Verwenden Sie mehrere Kennungen, um den Kundenabgleich zu verbessern.
- Ordnen Sie benutzerdefinierte Felder Identitätsattributen basierend auf Ihren Geschäftsanforderungen zu.
- Reduzierung doppelter Profile und Verbesserung der Genauigkeit von Kundendaten.
- Ermöglichen zielgerichteterer Kundenerlebnisse.

## Voraussetzungen

Bevor Sie benutzerdefinierte Identitätsattribute implementieren, stellen Sie Folgendes sicher:

- [Installieren der Datenverbindungserweiterung](install.md)
- [Verbindung mit Adobe Experience Platform herstellen](connect-data.md)
- [Senden von Kundenprofildaten](connect-data.md#send-customer-profile-data)

## Schritt 1: Konfigurieren des Experience Platform-Schemas

1. Melden Sie sich bei Adobe Experience Platform an und wählen Sie Ihr Commerce-Schema aus.
1. [Hinzufügen benutzerdefinierter Identitätsfelder](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas?lang=en#custom-fields-for-standard-groups) auf der Stammebene:
   - `hashedPID` (Zeichenfolge) - Primärer Identitäts-Hash
   - `hashedSID` (Zeichenfolge) - Sekundärer Identitäts-Hash
   - `primaryID` (Zeichenfolge) - Primärer Identitätsfeldname
   - `secondaryID` (Zeichenfolge) - Sekundärer Identitätsfeldname

![Experience Platform-Schemakonfiguration](./assets/aep-schema-configuration.png)

>[!NOTE]
>
>Sie können die genauen Feldnamen entsprechend Ihren Anforderungen anpassen. Im Beispiel werden `hashedPID` und `hashedSID` als Identitätsfelder verwendet.

## Schritt 2: Prozessorklassen erstellen

Erstellen Sie die folgenden PHP-Prozessorklassen in Ihrem benutzerdefinierten Modul:

### AddressCustomHashedId-Klasse

Dieser Prozessor erstellt Hash-Werte für `parent_id` und `entity_id` für Kundenadressen.

```php
<?php declare(strict_types=1);

namespace Magento\AepCustomerCustomAttributes\Event;
use Magento\AdobeCommerceEventsClient\Event\Event;
use Magento\AdobeCommerceEventsClient\Event\Processor\EventDataProcessorInterface;

class AddressCustomHashedId implements EventDataProcessorInterface
{
    public function process(Event $event, array $eventData): array
    {
        $pid = $eventData['parent_id'] ?? '';
        $sid = $eventData['entity_id'] ?? '';

        $eventData['profileAttributes']['hashedPID'] = hash('sha256', (string)$pid);
        $eventData['profileAttributes']['hashedSID'] = hash('sha256', (string)$sid);
        return $eventData;
    }
}
```

### AddressCustomId-Klasse

Dieser Prozessor legt die primären und sekundären ID-Feldnamen für Adressereignisse fest.

```php
<?php declare(strict_types=1);

namespace Magento\AepCustomerCustomAttributes\Event;
use Magento\AdobeCommerceEventsClient\Event\Event;
use Magento\AdobeCommerceEventsClient\Event\Processor\EventDataProcessorInterface;

class AddressCustomId implements EventDataProcessorInterface
{
    public function process(Event $event, array $eventData): array
    {
        $eventData['profileAttributes']['primaryID'] = 'hashedPID';
        $eventData['profileAttributes']['secondaryID'] = 'hashedSID';

        // Ensure both IDs are present, otherwise, Commerce will default primary to customerId and secondary to emailId
        if (empty($eventData['profileAttributes']['primaryID']) || empty($eventData['profileAttributes']['secondaryID'])) {
            $eventData['profileAttributes']['primaryID'] = $eventData['customerId'] ?? '';
            $eventData['profileAttributes']['secondaryID'] = $eventData['email'] ?? '';
        }

        return $eventData;
    }
}
```

### CustomHashedId-Klasse

Dieser Prozessor erstellt Hash-Werte für `entity_id` und `email` für Kundenprofile.

```php
<?php declare(strict_types=1);

namespace Magento\AepCustomerCustomAttributes\Event;
use Magento\AdobeCommerceEventsClient\Event\Event;
use Magento\AdobeCommerceEventsClient\Event\Processor\EventDataProcessorInterface;

class CustomHashedId implements EventDataProcessorInterface
{
    public function process(Event $event, array $eventData): array
    {
        $pid = $eventData['entity_id'] ?? '';
        $sid = $eventData['email'] ?? '';

        $eventData['profileAttributes']['hashedPID'] = hash('sha256', (string)$pid);
        $eventData['profileAttributes']['hashedSID'] = hash('sha256', (string)$sid);
        return $eventData;
    }
}
```

### CustomId-Klasse

Dieser Prozessor legt die primären und sekundären ID-Feldnamen für Profilereignisse fest.

```php
<?php declare(strict_types=1);

namespace Magento\AepCustomerCustomAttributes\Event;
use Magento\AdobeCommerceEventsClient\Event\Event;
use Magento\AdobeCommerceEventsClient\Event\Processor\EventDataProcessorInterface;

class CustomId implements EventDataProcessorInterface
{
    public function process(Event $event, array $eventData): array
    {
        $eventData['profileAttributes']['primaryID'] = 'hashedPID';
        $eventData['profileAttributes']['secondaryID'] = 'hashedSID';

        // Ensure both IDs are present, otherwise, Commerce will default primary to customerId and secondary to emailId
        if (empty($eventData['profileAttributes']['primaryID']) || empty($eventData['profileAttributes']['secondaryID'])) {
            $eventData['profileAttributes']['primaryID'] = $eventData['customerId'] ?? '';
            $eventData['profileAttributes']['secondaryID'] = $eventData['email'] ?? '';
        }

        return $eventData;
    }
}
```

>[!NOTE]
>Stellen Sie sicher, dass in den Ereignisdaten sowohl `primaryID` als auch `secondaryID` gesendet werden. Wenn eine der beiden fehlt, verwendet Commerce standardmäßig:
>
>- primaryID = customerId
>- secondaryID = emailId

>[!BEGINSHADEBOX]

Nachdem Sie diese beiden Schritte ausgeführt haben:

- Ihr Commerce-Schema in Experience Platform kann benutzerdefinierte Identitäten für Ihre Profilereignisdaten ordnungsgemäß aufnehmen.
- Prozessorklassen in Ihrem Commerce PHP-Code sammeln benutzerdefinierte Identifizierungsinformationen aus Profilereignissen.

Jetzt enthalten alle Profilereignisdaten, die von Commerce gesendet werden, Ihre benutzerdefinierten Identifizierungsinformationen.

>[!ENDSHADEBOX]

## Beispiele für Datenformate

Die folgenden Beispiele zeigen die erwartete JSON-Struktur für benutzerdefinierte Identitätsattribute sowohl in Profilattributen als auch in vollständigen Kundenprofildatenformaten.

### Format der Profilattribute

```json
{
  "profileAttributes": {
    "hashedPID": "d80eae6e96d148b3b2abbbc6760077b66c4ea071f847dab573d507a32c4d99a5",
    "hashedSID": "fa7359e288ce3104bd4317a4fb75f08c4a5feec472de2e415b8260fb3567ebe6",
    "warehousecode": "1256",
    "method": "ina2354",
    "source": "commerce",
    "primaryID": "hashedPID",
    "secondaryID": "hashedSID"
  }
}
```

### Vollständige Kundenprofilstruktur

```json
{
  "id": 137,
  "entity_id": "137",
  "created_at": "2025-02-10 20:10:30",
  "updated_at": "2022-02-10 20:10:31",
  "email": "customer@example.com",
  "firstname": "John",
  "lastname": "Doe",
  "dob": "2007-10-01 00:00:00",
  "profileAttributes": {
    "hashedPID": "d80eae6e96d148b3b2abbbc6760077b66c4ea071f847dab573d507a32c4d99a5",
    "hashedSID": "fa7359e288ce3104bd4317a4fb75f08c4a5feec472de2e415b8260fb3567ebe6",
    "primaryID": "137",
    "secondaryID": "customer@example.com"
  },
  "_metadata": {
    "commerceEdition": "Adobe Commerce",
    "commerceVersion": "2.4.6",
    "eventsClientVersion": "1.9.0",
    "storeId": "1",
    "websiteId": "1",
    "storeGroupId": "1",
    "websiteCode": "base",
    "storeCode": "default",
    "storeViewCode": "main_website_store"
  }
}
```

## Fehlerbehebung

### Primäre oder sekundäre ID fehlt

- **Symptom:** Daten werden standardmäßig auf customerId/emailId statt auf benutzerdefinierte Werte gesetzt.
- **Lösung:** Stellen Sie sicher, dass sowohl `primaryID` als auch `secondaryID` im `profileAttributes` festgelegt sind.

### Ungültige Hash-Werte

- **Problem:** Hash-Werte sind leer oder fehlerhaft.
- **Lösung:** Überprüfen Sie vor dem Hashing, ob die Quellfelder (`parent_id`, `entity_id`, `email`) gültige Daten enthalten.

### Prozessoren werden nicht ausgeführt

- **Problem:** Benutzerdefinierte Attribute werden nicht in den Ereignisdaten angezeigt.
- **Lösung:** Vergewissern Sie sich, dass die Prozessoren in `events.xml` ordnungsgemäß registriert sind und das Modul aktiviert ist.

### Experience Platform-Schema stimmt nicht überein

- **Problem** Daten werden in Experience Platform nicht angezeigt und es treten keine Schemavalidierungsfehler auf.
- **Lösung:** Stellen Sie sicher, dass das Experience Platform-Schema die benutzerdefinierten Identitätsfelder mit den richtigen Datentypen enthält.
