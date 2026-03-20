---
title: Geschenkkartenkonto-REST-Endpunkte
description: Erfahren Sie, wie Sie mit den REST-APIs für Geschenkkartenkonten in programmgesteuert Geschenkkartenkonten erstellen, aktualisieren, löschen und abfragen können [!DNL Adobe Commerce as a Cloud Service].
role: Admin, Developer
level: Experienced
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 160180d9d779514f6faee3c7de46531ebf191c7d
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Geschenkkartenkonto-API

{{accs-sandbox-experimental}}

Die REST-Endpunkte für Geschenkkartenkonten bieten eine programmgesteuerte Verwaltung von Geschenkkartenkonten auf Kontoebene, nicht auf Warenkorb- oder Angebotsebene. Verwenden Sie diese API, um Geschenkkartenkonten zu erstellen, abzurufen, zu aktualisieren und zu löschen oder Geschenkkartenkonten stapelweise über den JSON-Importendpunkt bereitzustellen.

Diese Endpunkte wurden für Folgendes entwickelt:

* Administratoren, die Geschenkgutscheinprogramme verwalten
* Integration von Drittanbietern zur Bereitstellung von Geschenkkarten aus externen Systemen wie ERP-, CRM- und Marketing-Plattformen
* Automatisierte Workflows für die Erstellung von Geschenkgutscheinen

## Authentifizierung

Für alle Endpunkte ist ein Admin- oder Integrationsträger-Token erforderlich. Das Token muss einer Rolle zugeordnet sein, die die Ressource `Magento_GiftCardAccount::giftcardaccount` Zugriffskontrollliste (ACL) enthält.

Bei Massenimportvorgängen muss die Rolle auch die `Magento_ImportExport::import_api` ACL-Ressource enthalten.

## Website- und Store-Kontext

Website- und Store-Ansichtswerte werden aus HTTP-Anfrage-Headern aufgelöst, nicht aus dem Anfragetext. Übergeben Sie bei jeder Anfrage eine der folgenden Kopfzeilen:

* `Store: <store_view_code>`
* `Magento-Website-Code: <website_code>`

Die -API löst die Website automatisch aus diesen Kopfzeilen auf. Schließen Sie keine `website_id` in die Payload der REST-Anfrage ein.

>[!NOTE]
>
>Der Massenimportendpunkt ist eine Ausnahme. Da der Import stapelweise erfolgt und möglicherweise auf bestimmte Websites abzielt, erfordert jede Zeile in der Import-Payload einen expliziten `website_id`.

## REST-API-Referenz

Die API stellt die folgenden Vorgänge unter `/V1/giftcardaccounts` bereit, die alle durch die `Magento_GiftCardAccount::giftcardaccount` ACL-Ressource gesichert sind:

| Methode | URL | Beschreibung |
|--------|-----|-------------|
| POST | `/rest/V1/giftcardaccounts` | Erstellen eines Geschenkkartenkontos |
| GET | `/rest/V1/giftcardaccounts` | Konten auflisten (unterstützt searchCriteria) |
| GET | `/rest/V1/giftcardaccounts/:id` | Konto nach ID abrufen |
| GET | `/rest/V1/giftcardaccounts/code/:code` | Konto nach Code abrufen |
| PUT | `/rest/V1/giftcardaccounts/:id` | Konto aktualisieren (Semantik zusammenführen) |
| DELETE | `/rest/V1/giftcardaccounts/:id` | Konto löschen |

### Feldverweis

| Feld | Typ | Gültige Werte | REST erstellen | importieren |
|---|---|---|---|---|
| `code` | Zeichenfolge | Max. 255 Zeichen | Erforderlich | Erforderlich |
| `balance` | floaten | >= 0 | Erforderlich | Erforderlich |
| `status` | int | `0` (deaktiviert), `1` (aktiviert) | Optional, standardmäßig `1` | Optional, standardmäßig `1` |
| `state` | int | `0` (verfügbar), `1` (verwendet), `2` (eingelöst), `3` (abgelaufen) | Optional, standardmäßig `0` | Optional, standardmäßig `0` |
| `is_redeemable` | int | `0` oder `1` | Optional, standardmäßig `1` | Optional, standardmäßig `1` |
| `date_expires` | Zeichenfolge | `YYYY-MM-DD` oder null | optional | optional |
| `date_created` | Zeichenfolge | `YYYY-MM-DD` | Auto-set | Optional, automatische Einstellung, wenn weggelassen |
| `website_id` | int | Gültige Website-ID | Nicht akzeptiert (automatisch aufgelöst aus Kopfzeilen) | Erforderlich |

### Erstellen eines Geschenkkartenkontos

Erstellt ein neues Geschenkkartenkonto mit Erkennung von doppeltem Code.

| Element | Wert |
|---|---|
| **Methode** | `POST` |
| **URL** | `/V1/giftcardaccounts` |

**Anfragetext:**

```json
{
  "giftcardAccount": {
    "code": "GIFT-1234-ABCD",
    "balance": 100.00,
    "status": 1,
    "state": 0,
    "is_redeemable": 1,
    "date_expires": "2027-12-31"
  }
}
```

**Antwort (200):**

```json
{
  "account_id": 42,
  "code": "GIFT-1234-ABCD",
  "balance": 100,
  "status": 1,
  "state": 0,
  "is_redeemable": 1,
  "date_expires": "2027-12-31",
  "date_created": "2026-03-12"
}
```

### Abrufen eines Geschenkkartenkontos nach ID

| Element | Wert |
|---|---|
| **Methode** | `GET` |
| **URL** | `/V1/giftcardaccounts/:id` |

**Antwort (200):**

Gibt ein einzelnes Geschenkkartenkontoobjekt zurück.

### Abrufen eines Geschenkkartenkontos nach Code

| Element | Wert |
|---|---|
| **Methode** | `GET` |
| **URL** | `/V1/giftcardaccounts/code/:code` |

>[!IMPORTANT]
>
>Wenn ein Geschenkkartencode rein numerisch ist (z. B. `12345`), entspricht eine Anfrage an `/V1/giftcardaccounts/12345` der ID-Route, nicht der Code-Route. Verwenden Sie immer `/V1/giftcardaccounts/code/12345` für Code-basierte Suchen, wenn der Code numerisch sein könnte.

**Antwort (200):**

Gibt ein einzelnes Geschenkkartenkontoobjekt zurück.

### Auflisten von Geschenkkartenkonten mit Suchkriterien

| Element | Wert |
|---|---|
| **Methode** | `GET` |
| **URL** | `/V1/giftcardaccounts` |

Übergeben Sie Suchkriterien als Abfrageparameter. Im folgenden Beispiel werden Geschenkgutscheinkonten zurückgegeben, bei denen `status` gleich `1` (aktiviert) ist:

```text
GET /V1/giftcardaccounts?searchCriteria[filterGroups][0][filters][0][field]=status&searchCriteria[filterGroups][0][filters][0][value]=1&searchCriteria[pageSize]=10&searchCriteria[currentPage]=1
```

**Antwort (200):**

```json
{
  "items": [
    {
      "account_id": 42,
      "code": "GIFT-1234-ABCD",
      "balance": 100,
      "status": 1,
      "state": 0,
      "is_redeemable": 1,
      "date_expires": "2027-12-31",
      "date_created": "2026-03-12"
    }
  ],
  "search_criteria": { ... },
  "total_count": 1
}
```

### Aktualisieren eines Geschenkkartenkontos

Aktualisiert ein vorhandenes Geschenkkartenkonto mithilfe der Zusammenführungssemantik. Nur Felder, die nicht null sind, in der Anfrage werden angewendet. Das `code` Feld ist unveränderlich. Die Übergabe eines anderen Codes gibt einen Validierungsfehler zurück.

| Element | Wert |
|---|---|
| **Methode** | `PUT` |
| **URL** | `/V1/giftcardaccounts/:id` |

**Anfragetext:**

```json
{
  "giftcardAccount": {
    "balance": 75.00,
    "status": 1
  }
}
```

**Antwort (200):**

Gibt das aktualisierte Geschenkkartenkontoobjekt zurück.

### Löschen eines Geschenkkartenkontos

| Element | Wert |
|---|---|
| **Methode** | `DELETE` |
| **URL** | `/V1/giftcardaccounts/:id` |

**Antwort (200):**

```json
true
```

## Massenimport über JSON

Geschenkkartenkonten können mithilfe von `POST /V1/import/json` mit dem Entitätstyp `giftcardaccount` stapelweise bereitgestellt werden. Dieser Endpunkt erfordert die Ressource `Magento_ImportJsonApi::import_api` Zugriffssteuerungsliste (ACL) zusätzlich zur Geschenkkartenkonto-ACL.

### Unterstützte Verhaltensweisen

| Verhalten | Beschreibung |
|---|---|
| `append` | Erstellt neue Geschenkkartenkonten. Wenn bereits ein Code vorhanden ist, schlägt diese Zeile fehl und der Import wird mit den verbleibenden Zeilen fortgesetzt. |
| `replace` | Aktualisiert und fügt die Geschenkkartenkonten nach Code ein. Erstellt das Konto, wenn der Code nicht vorhanden ist, und ersetzt ihn, wenn er vorhanden ist. |
| `delete` | Entfernt Geschenkkartenkonten nach Code. |

### Beispiel für eine Anfrage

```json
{
  "source": {
    "entity": "giftcardaccount",
    "behavior": "append",
    "validation_strategy": "validation-stop-on-errors",
    "allowed_error_count": "10",
    "items": [
      {
        "code": "BULK-001",
        "balance": 50.00,
        "website_id": 1,
        "status": 1,
        "state": 0,
        "is_redeemable": 1,
        "date_expires": "2027-06-30"
      },
      {
        "code": "BULK-002",
        "balance": 25.00,
        "website_id": 1
      }
    ]
  }
}
```

### Details zum Importverhalten

* Jede Zeile in der Import-Payload erfordert eine explizite `website_id`, im Gegensatz zu REST-Endpunkten, die die Website aus Anfragekopfzeilen ableiten.
* Jede Zeile wird unabhängig voneinander validiert. Ungültige Zeilen führen zu Fehlern pro Zeile, ohne dass sich dies auf gültige Zeilen im selben Batch auswirkt.
* Doppelte Codes innerhalb desselben Batches werden als Fehler pro Zeile erkannt und gemeldet, anstatt ein Transaktions-Rollback zu verursachen.
* Der Import schreibt aus Leistungsgründen direkt in die Datenbank und umgeht den Speicherlebenszyklus des Anbietermodells. Beim Import werden keine Einträge im Verlauf der Saldenänderung erstellt.
* REST-Erstellungsvorgänge lehnen vergangene Ablaufdaten ab. Der Import akzeptiert standardmäßig frühere Ablaufdaten, um die Migration historischer Daten zu unterstützen.

## Fehlerbehandlung

Die API gibt Standard-HTTP-Status-Codes zurück:

| Status-Code | Bedingung |
|---|---|
| `400` | Validierungsfehler. Fehlende erforderliche Felder, ungültige Werte oder vergangenes Ablaufdatum bei der REST-Erstellung. |
| `401` | Fehlendes oder ungültiges Bearer-Token. |
| `403` | Dem Token fehlt die erforderliche ACL-Ressource. |
| `404` | Geschenkkartenkonto nicht gefunden. |
| `409` | Duplizieren Sie den Geschenkkartencode. |

Die Eingabevalidierung umfasst erforderliche Felder, Wertebereiche (Status muss `0` oder `1` sein, Status muss `0`-`3` sein, Saldo muss nicht negativ sein), das Datumsformat und die Typsicherheit. Nicht numerische Werte für numerische Felder werden abgelehnt.
