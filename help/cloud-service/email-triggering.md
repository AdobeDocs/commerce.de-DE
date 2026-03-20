---
title: E-Mail-Auslösung durch REST
description: Erfahren Sie, wie Sie mit der REST-API bei Bedarf Transaktions-E-Mails in Trigger nehmen können, indem Sie eine Vorlagen-ID, eine Empfänger-E-Mail und Vorlagenvariablen für angeben [!DNL Adobe Commerce as a Cloud Service].
role: Admin
level: Experienced
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 9661e368f7a0dc85edcd3e52a67ae2a98355d8b5
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Auslösen von E-Mails über die REST-API

Zuvor konnten Sie E-Mails nur senden, wenn Ereignisse ausgelöst wurden, z. B. bei der Kundenregistrierung oder beim Bestellvorgang. In [!DNL Adobe Commerce as a Cloud Service] können Sie E-Mails bei Bedarf über die REST-API senden, indem Sie eine Vorlagen-ID, eine Empfänger-E-Mail und Vorlagenvariablen angeben.

>[!NOTE]
>
>Derzeit können nur neu erstellte, benutzerdefinierte Vorlagen gesendet werden. Vordefinierte Vorlagen und Systemvorlagen werden nicht unterstützt.

Der `V1/custom-email/send`-Endpunkt ermöglicht **Drittanbietersystemen** wie Integrationen und externen Services, E-Mails bei Bedarf zu senden, indem Folgendes angegeben wird:

- **Vorlagen-ID** - E-Mail-Vorlagen-ID.
- **Empfänger-E-**: Die Ziel-E-Mail-Adresse für diese Anfrage.
- **Variablen** - (Optional) Benutzerdefinierte Schlüssel-Wert-Paare, die in die Vorlage eingefügt werden sollen, z. B. `customer_name` oder `order_id`.

>[!NOTE]
>
>Die E-Mail wird synchron unter Verwendung des aktuellen Speicherbereichs und der standardmäßigen E **Mail-Adresse (**) oder der für Vorlagen definierten E-Mail-Adresse gesendet.

## REST-Vertrag

Im folgenden Abschnitt wird erläutert, wie Sie mit der REST-API bei Bedarf Transaktions-E-Mails senden können.

### Endpunkt

- **URL** - `POST /rest/V1/custom-email/send`
- **Autorisierung** - Nur **Service-zu-Service-IMS-Autorisierung** wird unterstützt. Der Aufrufer muss Zugriff auf die Ressource **Benutzerdefinierte E-Mail über API senden** (`Magento_CustomEmailSend::send_custom_email`) haben. Weitere Informationen finden [ unter ](https://developer.adobe.com/commerce/webapi/rest/authentication/)-Authentifizierung .
- **Asynchrone Verwendung** (empfohlen) - Obwohl dieser Endpunkt synchron implementiert ist, empfehlen wir, ihn mit der **asynchronen REST-API** aufzurufen, damit die Anfrage von einem Verbraucher in die Warteschlange gestellt und verarbeitet wird, wodurch langlebige HTTP-Verbindungen vermieden werden. In [!DNL Adobe Commerce as a Cloud Service] können Sie die Route mit `/async` nach `V1` verwenden, z. B.: `POST https://<server>.api.commerce.adobe.com/<tenant-id>/V1/async/custom-email/send`.

  Weitere Informationen finden [ unter „Asynchrone Web-Endpunkte (SaaS](https://developer.adobe.com/commerce/webapi/rest/use-rest/asynchronous-web-endpoints/).

### Anfragetext

- **templateId** (Ganzzahl, erforderlich) - E-Mail-Vorlagen-ID, wie in der Admin unter [!UICONTROL **Marketing**] > [!UICONTROL _Kommunikation_] > [!UICONTROL **E-Mail-Vorlagen**] definiert.

- **recipientEmail** (Zeichenfolge, erforderlich) - Die Ziel-E-Mail-Adresse. Muss ein gültiges E-Mail-Format sein. Fehlende oder leere Werte verursachen Trigger bei der Validierung.
- **variables** (Objekt, optional) - Schlüssel-Wert-Zuordnung, die als `UnstructuredArray` in die Vorlage eingefügt wird.

  Wenn Sie keine Variablen verwenden, übergeben Sie ein leeres -Objekt oder lassen Sie es weg. Verwenden Sie im Textkörper und Betreff der E-Mail-Vorlage die Variablensyntax, um auf eine Variable zu verweisen, z. B. `var order_id`. Der Betreff unterstützt außerdem dieselben benutzerdefinierten Variablen und die Syntax, die unter [Unterstützte Vorlagenszenarien“ beschrieben ](#supported-template-scenarios).

### Erfolgsantwort (HTTP 200)

Die API gibt bei erfolgreichem Versand HTTP 200 zurück.

### Fehlerantworten

- **HTTP 400 - Validierungsfehler**

  Die Integration muss für jede Anfrage eine gültige `templateId` und einen gültigen `recipientEmail` bereitstellen.

   - `"message": "Invalid recipient email format"` - Ungültige oder falsch formatierte Empfängeradresse
   - `"message": "Recipient email is required."` - fehlende oder leere `recipientEmail`
   - `"message": "Template ID must be a positive integer."` - fehlende, null oder ungültige `templateId`

- **HTTP 404 - Vorlage nicht gefunden**

  Beispiel: `"message": "Email template with ID \"999\" does not exist."`

## Unterstützte Vorlagenszenarien

Die folgenden Vorlagenfunktionen werden sowohl im **E-Mail-Textkörper** als auch im **Vorlagenbetreff** unterstützt:

>[!NOTE]
>
>Der Vorlagenbetreff unterstützt auch benutzerdefinierte Variablen. Verwenden Sie `var variableName` und andere Syntax, wie im folgenden Abschnitt beschrieben.

- **Include-Anweisung** - um andere Design-Vorlagen wie eine E-Mail-Kopfzeile einzuschließen.

  ```javascript
  {{template config_path="design/email/header_template"}}
  ```

- **Einfache Variablen** - `var variableName` verwenden, z. B. `var order_id` oder `var g`.

  ```javascript
  {{var order.test}}
  {{var g}}
  {{var order_id}}
  ```

- **Verschachtelte/Punktnotation** - Für verschachtelte Schlüssel, die im Anfrage-`variables` übergeben werden, verwenden Übersetzungen in Dollar-Präfixnamen wie `$order_data.customer_name`, `$order.increment_id` oder `$order_data.frontend_status_label`.

  ```javascript
  {{trans "%name," name=$order_data.customer_name}}
  {{trans "Your order #%increment_id has been updated with a status of **%order_status**." increment_id=$order.increment_id order_status=$order_data.frontend_status_label |raw}}
  ```

- **Übersetzung (trans)** - parametrisierter Text, mehrzeilige Übersetzungen mit mehreren Platzhaltern und HTML-Tags.

  ```javascript
  {{trans "%name," name=$order_data.customer_name}}
  {{trans "Your order #%increment_id has been updated with a status of **%order_status**." increment_id=$order.increment_id order_status=$order_data.frontend_status_label |raw}}
  ```

- **Rohausgabe** - Verwenden Sie den `|raw`, wenn der übersetzte oder variable Inhalt HTML enthält (z. B. `<strong>` oder `<a>`).

  ```javascript
  {{trans "Your order #%increment_id has been updated with a status of **%order_status**." increment_id=$order.increment_id order_status=$order_data.frontend_status_label |raw}}
  ```

- **URL helper** - zum Speichern von URLs in Übersetzungen.

  ```javascript
  {{trans 'You can check the status of your order by [logging into your account](%account_url).' account_url=$this.getUrl($store,'customer/account/',[_nosid:1]) |raw}}
  ```
