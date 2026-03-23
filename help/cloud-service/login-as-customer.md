---
title: Melden Sie sich als Kunde mit einmaligen Codes an.
description: Erfahren Sie, wie Sie mit der OTC-Funktion „Als Kunde anmelden“ einmalige Codes für die Kundenauthentifizierung in [!DNL Adobe Commerce as a Cloud Service] generieren können.
role: Admin
level: Intermediate
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 2de1006ad3cee936d114bcf1b9a98b43a54d8c76
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# Als Kunde anmelden

{{accs-sandbox-experimental}}

Mit der Funktion „Als Kunde anmelden“ (OTC, Einmalcode) können Admin-Benutzer einen kurzlebigen Einmalcode für einen Kunden generieren. Dieser Code kann über GraphQL in ein Kunden-Zugriffs-Token umgetauscht werden, wodurch kennwortlose Workflows **Als Kunde anmelden** für verkäuferunterstützte Einkaufsszenarien ermöglicht werden.

Die Anmeldung als Kunde besteht aus den folgenden Komponenten:

* **Admin-**: Auf der Seite „Kundenbearbeitung“ können Administratoren einen einmaligen Code (OTC) anfordern, anstatt sich direkt als Kunde anzumelden.
* **REST API** - Ein programmatischer Endpunkt für die OTC-Generierung, der für Admin-Skripte und Drittanbieter-Integrationen nützlich ist.
* **GraphQL-API** - Mutationen, die ein OTC-Token gegen ein Kunden-Zugriffstoken für Storefront- oder Headless-Commerce-Flüsse eintauschen.

## Einmaligen Code von der Administratorin bzw. dem Administrator erzeugen

Die Schaltfläche Als Kunden-OTC anmelden ersetzt die standardmäßige Schaltfläche Anmelden als Kunde auf der Seite Kundenbearbeitung durch eine Schaltfläche [!UICONTROL **Kunden-OTC abrufen**]. Der generierte Einmalcode kann dann mit der Storefront oder GraphQL für verkäufergestützte Einkäufe verwendet werden.

>[!NOTE]
>
>Die Schaltfläche **Als Kunde anmelden** ist auf den Seiten „Bestellung“, „Rechnung“, „Versand“ und „Gutschrift“ nicht verfügbar.

### Voraussetzungen

Sie müssen die folgenden Anforderungen erfüllen, bevor Sie die Funktion „Als Kunde anmelden“ verwenden:

* **Administratorberechtigung** : Für Admins muss in ihrer Administratorrolle die Berechtigung `Magento_LoginAsCustomer::login` Zugriffskontrollliste (ACL) aktiviert sein, um sich als Kunde anzumelden.

* **Kundenzustimmung** - Für den Kunden muss das `login_as_customer_assistance_allowed`-Erweiterungsattribut auf &quot;**2“**. Dies kann auf der Seite **Kunde bearbeiten** in der Admin Console oder über GraphQL beim Erstellen oder Bearbeiten eines Kunden konfiguriert werden.

  ![Konfiguration des Kundeneinverständniserweiterungs-Attributs auf der Seite „Kunde bearbeiten“](./assets/customer-consent-attribute.png){width="600" zoomable="yes"}

* **Anmeldung als Kundenerweiterung aktiviert** - Die Funktion „Anmeldung als Kunde“ ist nicht verfügbar, wenn die Option „Anmeldung als Kunde“ deaktiviert ist. Um sicherzustellen, dass die Erweiterung aktiviert ist, navigieren Sie [!UICONTROL **Stores**] > [!UICONTROL **Configuration**] > [!UICONTROL **Customers**] > [!UICONTROL **Als Kunde anmelden**] > [!UICONTROL **Erweiterung aktivieren**].

### Einmaligen Code (OTC) anfordern

1. Navigieren Sie zu [!UICONTROL **Kunden**] und wählen Sie einen Kunden aus, um die Seite „Bearbeiten“ zu öffnen.

1. Klicken Sie auf der Seite „Kunde bearbeiten [!UICONTROL **auf „OTC zur Kundenanmeldung**].

   ![Schaltfläche „OTC für Kundenanmeldung abrufen“ auf der Seite „Kunde bearbeiten“](./assets/get-customer-login-otc-button.png){width="600" zoomable="yes"}

1. Geben Sie einen [!UICONTROL **Grund**] (erforderlich) ein und klicken Sie auf [!UICONTROL **Anfordern**].

   ![OTC-Anfrage-Modal mit Feld „Grund“](./assets/otc-reason-modal.png){width="600" zoomable="yes"}

   >[!NOTE]
   >
   >Das **Grund**-Feld ist erforderlich. Sie wird an den OTP-Generierungsfluss übergeben und ist für die Verwendung in kommenden Audit- und Ereignisprotokollierungsfunktionen reserviert.

1. Das generierte OTC wird im Modal angezeigt. Verwenden Sie diesen Code mit der `generateCustomerToken`- oder `exchangeOtpForCustomerToken` GraphQL-Mutation zur Kundenautorisierung.

   ![Generated OTC wird im Modal angezeigt](./assets/otc-generated-code.png){width="300" zoomable="yes"}

>[!IMPORTANT]
>
>Der generierte OTC-Einmalcode ist standardmäßig 30 Sekunden lang gültig und wird nach einer einzigen Verwendung ungültig. Die TTL kann durch Senden eines -Support[Tickets konfiguriert &#x200B;](https://experienceleague.adobe.com/home?support-tab=home#support).

Nachdem der Einmalcode generiert wurde, können Sie ihn verwenden, indem Sie zu Ihrer Storefront navigieren und sich mit den folgenden Anmeldeinformationen anmelden:

* **Email**: Die E-Mail-Adresse des Kunden
* **Kennwort**: Der generierte einmalige Code (OTC)

## Generieren eines einmaligen Codes mithilfe der REST-API

Der Endpunkt POST-`V1/customer/:customerId/otp` bietet eine programmgesteuerte Möglichkeit, ein OTC für einen Kunden zu generieren. Dies ist für Admin-Benutzeroberflächen, Skripte oder Drittanbieterintegrationen nützlich, die eine konsistente Trigger der OTC-Ausgabe erfordern.

### REST-Vertrag

| Element | Wert |
|---|---|
| **Methode** | POST |
| **URL** | `/rest/V1/customer/:customerId/otp` |
| **Authentifizierung** | Admin-Token (Bearer). Erforderliche ACL: `Magento_LoginAsCustomer::login`. |
| **Anfragetext** | JSON mit optionalem `reason`. Wird für Auditing und Protokollierung verwendet. |
| **Erfolgsantwort** | HTTP 200, JSON mit `otp` (32-stellige Hexadezimalzeichenfolge). |
| **Fehlerantworten** | Fehler in der Standard-Web-API (z. B. 401, 403). Wenn die Kundenunterstützung Anmelden für den Kunden deaktiviert ist, wird möglicherweise als 500 oder eine zugeordnete Ausnahme angezeigt. |

### Beispiel für eine Anfrage

```text
POST /rest/V1/customer/:customerId/otp
Content-Type: application/json
```

```json
{"reason": "Support session"}
```

### Beispiel für eine Antwort

```json
{"otp": "a1b2c3d4e5f6789012345678abcdef01"}
```

## Einmaliger Code durch ein Kunden-Token mit GraphQL austauschen

Nachdem Sie ein OTC-Token generiert haben (über die Admin-Benutzeroberfläche oder die REST-API), verwenden Sie eine der folgenden GraphQL-Mutationen, um es gegen ein Kunden-Zugriffstoken einzutauschen.

### `generateCustomerToken` Mutation

Die `generateCustomerToken(email, password)` Mutation gibt ein Kunden-Token zurück. Das `password` Argument wird in der folgenden Reihenfolge ausgewertet:

1. **Kundenkennwort (Standard)** - Das Kontokennwort des Kunden.
1. **Token zum Zurücksetzen des Kennworts durch den Kunden (einmalige Verwendung)** - Ein gültiges Token aus **Kennwort vergessen** (z. B. die `requestPasswordResetEmail`-Mutation). Wird bei der ersten Verwendung verbraucht.
1. **Admin-generierter OTC (Einmalcode)** - Ein Code, der von einem Administrator über die REST-API oder die Admin-Benutzeroberfläche für den Kunden generiert wurde. Einmalige Verwendung, kurzlebig (standardmäßig 30 Sekunden).

**Schema:**

```graphql
type Mutation {
  generateCustomerToken(email: String!, password: String!): CustomerToken
}

type CustomerToken {
  token: String!
}
```

**Beispiel: Anmeldung mit Admin OTC**

```graphql
mutation GenerateCustomerToken($email: String!, $password: String!) {
  generateCustomerToken(email: $email, password: $password) {
    token
  }
}
```

Variablen (verwenden Sie das OTC als `password`):

```json
{
  "email": "customer@example.com",
  "password": "<admin-generated-OTC>"
}
```

**Beispiel: Anmeldung mit Passwort**

```graphql
mutation GenerateCustomerToken($email: String!, $password: String!) {
  generateCustomerToken(email: $email, password: $password) {
    token
  }
}
```

Variablen:

```json
{
  "email": "customer@example.com",
  "password": "CustomerPassword123"
}
```

**Beispiel: Anmeldung mit Token zum Zurücksetzen des Kennworts**

Nachdem der Kunde ein Zurücksetzen des Passworts angefordert hat (z. B. `requestPasswordResetEmail`), kann das über den E-Mail-Link empfangene Zurücksetzen-Token wie `password` in `generateCustomerToken` (einmalige Verwendung) verwendet werden.

```graphql
mutation GenerateCustomerToken($email: String!, $password: String!) {
  generateCustomerToken(email: $email, password: $password) {
    token
  }
}
```

Variablen (verwenden Sie nach `password` das Token „Zurücksetzen„):

```json
{
  "email": "customer@example.com",
  "password": "<reset-password-token-from-email-link>"
}
```

**Beispielantwort:**

```json
{
  "data": {
    "generateCustomerToken": {
      "token": "<customer-access-token>"
    }
  }
}
```

### `exchangeOtpForCustomerToken` Mutation

Die `exchangeOtpForCustomerToken`-Mutation tauscht ein von einem Administrator erstelltes Kennwortzurücksetzungs-Token oder OTP gegen ein Kundenzugriffs-Token aus. Der OTP wird nach erfolgreichem Austausch ungültig (einmalige Verwendung). Dieser Endpunkt berücksichtigt die reCAPTCHA-Konfiguration.

**Schema:**

```graphql
type Mutation {
  exchangeOtpForCustomerToken(
    email: String!
    otp: String!
  ): CustomerToken
}

type CustomerToken {
  token: String!
}
```

**Beispielanfrage:**

```graphql
mutation ExchangeOtpForCustomerToken($email: String!, $otp: String!) {
  exchangeOtpForCustomerToken(email: $email, otp: $otp) {
    token
  }
}
```

Variablen:

```json
{
  "email": "customer@example.com",
  "otp": "<one-time-password>"
}
```

**Beispielantwort:**

```json
{
  "data": {
    "exchangeOtpForCustomerToken": {
      "token": "<customer-access-token>"
    }
  }
}
```

### Zusammenfassung der Mutationen

| Mutation | Anwendungsfall |
|---|---|
| `generateCustomerToken(email, password)` | Einzelner Einstiegspunkt: Kundenkennwort, Token zum Zurücksetzen des Kennworts, OTC-Admin oder OTP (nach dem Kennwort/Zurücksetzen versucht). |
| `exchangeOtpForCustomerToken(email, otp)` | OTP- oder Reset Password Token Exchange. OTP (oder Reset Password Token) wird nach der Verwendung genutzt. |

Sowohl das Kennwortzurücksetzungs-Token als auch die Administrator-OTC werden als `password` an `generateCustomerToken` übergeben. Der Resolver erkennt den Token-Typ und validiert ihn entsprechend.
