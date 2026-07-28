---
title: Überprüfen des Zugriffs auf den Migrationsdienst
description: Erfahren Sie, wie Sie den End-to-End-Zugriff auf die Commerce Data Migration Service-API überprüfen und so die Erreichbarkeit des Netzwerks, die IMS-Authentifizierung und die Mandantenautorisierung bestätigen.
feature: Cloud
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Developer
level: Intermediate
autotag-review: '2026-07-22T19:18:53.554Z'
TQID: 'https://experienceleague.adobe.com/csDq2Bbha2IieqxsDDG0iS1IHhAJ02fD-cwd8KFIsSk'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
subfeature_v2:
  - id: f8ddfd3b-6194-46e8-a176-0e918039be56
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 670b6214b28be93a16130552a226a8cadb487324
workflow-type: tm+mt
source-wordcount: 452
ht-degree: 1%

---

# Überprüfen des Zugriffs auf den Migrationsdienst

{{bulk-data-early-access}}

Verwenden Sie dieses Handbuch, um den End-to-End-Zugriff auf die Commerce Data Migration Service (CDMS)-API von Ihrer Umgebung aus zu überprüfen. Bei einem erfolgreichen Aufruf wird gleichzeitig die Erreichbarkeit des Netzwerks anhand Ihrer Ausgangs-IPs (IP-Zulassungsauflistung), der IMS-Authentifizierung und der Mandantenautorisierung überprüft.

Füllen Sie dieses Handbuch aus, nachdem Sie alle Elemente in der [Checkliste zur Kundenbereitschaft](readiness-checklist.md) abgeschlossen haben und bevor Sie die im [Migrationshandbuch](migration-guide.md) beschriebene Migration ausführen.

## Voraussetzungen

- Eine OAuth 2.0-Server-zu-Server-Anmeldedaten (Client-ID und Client-Geheimnis), die in der [Adobe Developer Console erstellt &#x200B;](https://developer.adobe.com/console/).
- Ihre IMS-Organisations-ID im Format `<org>@AdobeOrg`. Die Organisation muss Eigentümer des Ziel-Mandanten sein.
- Die Ziel-`tenantId`, eine 22-stellige alphanumerische IMS-Mandanten-ID.
- Ausgehende Ausgangs-IP-Adressen, die an Adobe für das CDMS-Gateway gesendet und von diesem auf die Zulassungsliste gesetzt werden. Stimmen Sie sich mit dem Adobe-Team ab, wenn Sie sich bezüglich der IP-Adressen oder ihres Status nicht sicher sind.
- Der regionsspezifische Service-Host aus der Tabelle [Service-Hosts nach Umgebung und Region](#service-hosts-by-environment-and-region).

## Generieren eines IMS-Zugriffstoken

Erstellen Sie mit der `client_credentials`-Berechtigung ein Zugriffs-Token mit Ihren OAuth 2.0 Server-zu-Server-Anmeldeinformationen. Der IMS-Host in diesem Schritt ist für alle Datenregionen gleich. Nur der CDMS-Host ändert sich pro Region.

```bash
curl -X POST "https://ims-na1.adobelogin.com/ims/token/v3" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "x-org-id:<your-org-id>@AdobeOrg" \
  -d "grant_type=client_credentials" \
  -d "client_id=<your-ims-client-id>" \
  -d "client_secret=<your-ims-client-secret>" \
  -d "scope=AdobeID,openid,read_organizations,additional_info.projectedProductContext,additional_info.roles,adobeio_api,read_client_secret,manage_client_secrets"
```

## Aufrufen der List Migrations-API

Die folgende Anfrage ruft die Liste der Migrationen für den Mandanten ab und erfordert das Zugriffstoken aus dem vorherigen Schritt. Wählen Sie den Host für Ihre Region aus der Tabelle [Service-Hosts nach Umgebung und Region](#service-hosts-by-environment-and-region) aus. Mit der `-i`-Markierung werden die HTTP-Statuszeile und die Antwort-Header gedruckt, damit Sie das Ergebnis bestätigen können.

```bash
curl -i "https://<host>/<tenantId>/v1/migrations" \
  -H "Authorization: Bearer <your IMS access token>"
```

## Interpretieren der Antwort

| HTTP-Code | Bedeutung | Beispiel-Antworttext |
| --- | --- | --- |
| 200 | Erfolgreich. Konnektivität, Authentifizierung und Mandantenautorisierung wurden weitergeleitet. Der Antworttext enthält die Liste der Migrationen für den Mandanten. | `{"migrations":[...]}` |
| 401 | Fehlendes oder ungültiges Bearer-Token, vor Erreichen des Service abgelehnt. [Erneutes Generieren des Tokens](#generate-an-ims-access-token). | Variiert (Gateway-generiert) |
| 403 | Der authentifizierte Benutzer verfügt nicht über Migrationsberechtigungen für diesen Mandanten. | `{"error":"access_denied","message":"You do not have permission to access this tenant"}` |
| 500 | Interner Server-Fehler. | `{"error":{"message":"Internal Server Error","status":500}}` |

>[!NOTE]
>
>Wenn die Anfrage eine Zeitüberschreitung aufweist oder die Verbindung abgelehnt wird und kein HTTP-Status zurückgegeben wird, wird Ihre Ausgangs-IP wahrscheinlich nicht auf die Zulassungsliste gesetzt oder Sie verwenden einen falschen Host. Bestätigen Sie den Host für die Region in der folgenden Tabelle und Ihre auf die Zulassungsliste gesetzt IPs.

## Service-Hosts nach Umgebung und Region

| Region oder Umgebung | Host |
| --- | --- |
| Sandbox für die Vorproduktion | `https://na1-sandbox.api.commerce.adobe.com` |
| Nordamerika | `https://na1.api.commerce.adobe.com` |
| Europa | `https://eu1.api.commerce.adobe.com` |
| Indien | `https://in1.api.commerce.adobe.com` |
| UK | `https://uk1.api.commerce.adobe.com` |
| Australien und Neuseeland | `https://au1.api.commerce.adobe.com` |

## Nächste Schritte

Nachdem Sie den Zugriff bestätigt haben, fahren Sie mit dem [Migrationshandbuch](migration-guide.md) fort, um mit der Umgebungskonfiguration und der Ausführung der Migration zu beginnen.
