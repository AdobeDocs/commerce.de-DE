---
title: Private Katalogansichten
description: Erfahren Sie, wie Sie eine private Katalogansicht erstellen, indem Sie den Katalogschutz aktivieren, sodass nur Anfragen mit einem gültigen signierten Token die Produkt- und Preisdaten abrufen können.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 38fa0734562a631fdcdd7510580571c5d37cb598
workflow-type: tm+mt
source-wordcount: 467
ht-degree: 0%

---

# Private Katalogansichten

Standardmäßig ist eine [Katalogansicht](catalog-view.md) öffentlich. Aktivieren Sie den Katalogschutz für eine Katalogansicht, um den Zugriff auf Anfragen zu beschränken, die ein gültiges signiertes Token enthalten.

Der Katalogschutz gilt nur für die ausgewählte Katalogansicht. Die Richtlinien, Ebenen oder Preisbücher der Ansicht werden dadurch nicht geändert.

Beispiele für [&#x200B; zum Schutz einer Katalogansicht finden Sie &#x200B;](restricted-access-keys.md#restricted-access-key-use-cases) Anwendungsfällen für „Schlüssel mit eingeschränktem Zugriff“.

## Erläuterung der Schutzgrenze

Der Katalogschutz gilt nur für die Katalogansicht, in der er aktiviert ist. Es schützt Katalog- und Suchanfragen, ändert jedoch nicht die Richtlinien oder Preislisten der Ansicht, schützt andere Katalogansichten oder sichert Warenkorb-, Checkout- oder Bestellvorgänge.

Das verbundene Commerce-Backend muss die Kaufberechtigung unabhängig durchsetzen.

## Schützen einer Katalogansicht

Bevor Sie beginnen, [&#x200B; Sie aus dem öffentlichen Schlüssel, den Ihre Client](restricted-access-keys.md)Anwendung generiert, einen Schlüssel mit eingeschränktem Zugriff.

1. Schalten Sie in der Katalogansicht Formular erstellen oder bearbeiten **[!UICONTROL Catalog Protection]** zu **[!UICONTROL Enabled]** um.

1. Wählen Sie unter **[!UICONTROL Restricted Access Keys]** bis zu drei [Schlüssel mit eingeschränktem Zugriff](restricted-access-keys.md) aus, die dieser Katalogansicht zugewiesen werden sollen.

   ![Der Katalogschutz ist im Bearbeitungsformular für die Katalogansicht aktiviert, wobei ein eingeschränkter Zugriffsschlüssel zugewiesen ist](../assets/catalog-view-protected.png){width="70%" zoomable="yes"}

1. Klicken Sie auf **[!UICONTROL Save catalog view]**.

   Die Katalogansicht ist jetzt geschützt. Nur Anfragen, die ein gültiges signiertes Token von einem zugewiesenen Schlüssel enthalten, können dessen Daten abrufen.

   >[!NOTE]
   >
   >Es kann bis zu fünf Minuten dauern, bis Änderungen an der Konfiguration für den Katalogschutz wirksam werden.

## Überprüfen, ob der Zugriff erzwungen wird

Um zu bestätigen, dass eine private Katalogansicht nicht autorisierte Anfragen ablehnt, rufen Sie ihren [GraphQL](../get-started.md#get-instance-details)Endpunkt mit und ohne signiertes Token mithilfe der folgenden Kopfzeilen auf:

| Kopfzeile | Zweck |
| --- | --- |
| `AC-View-ID` | Die abzufragende Katalogansicht. |
| `AC-Price-Book-ID` | Das anzuwendende Preisbuch. |
| `AC-Catalog-View-Access-Token` | Der signierte JWT-Nachweis für die Autorisierung für die Katalogansicht. |

Eine Anfrage ohne gültiges Token gibt anstelle von Katalogdaten einen GraphQL-Fehler zurück, z. B.:

```json
{
  "errors": [
    {
      "message": "Access key validation failed: Missing token",
      "extensions": { "x-commerce-exception": "access-key-invalid" }
    }
  ]
}
```

Eine Anfrage mit einem Token, das von einem zugewiesenen, nicht abgelaufenen Schlüssel signiert wurde, gibt die Katalogdaten erwartungsgemäß zurück. Weitere Informationen zum Signieren eines JWT und zum Aufrufen der Merchandising-API finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/using-the-api#authentication).

## Verwalten eingeschränkter Zugriffsschlüssel

Wenn [!UICONTROL Catalog Protection] aktiviert ist und alle zugewiesenen Schlüssel ablaufen, wird die Katalogansicht unzugänglich - Storefronts, die auf diese Katalogansicht angewiesen sind, können keine Daten aus dieser bereitstellen. Weisen Sie einen neuen, nicht abgelaufenen Schlüssel zu, um den Zugriff wiederherzustellen. Anweisungen finden Sie unter [Drehtasten](restricted-access-keys.md#rotate-a-key).

>[!IMPORTANT]
>
>Die automatische Schlüsselerstellung und -verwaltung über Adobe Commerce und den Adobe Commerce Optimizer-Connector ist noch nicht verfügbar.

## Ähnliche Themen

- [Katalogansichten](catalog-view.md) Erfahren Sie, wie Katalogansichten Ihren Produktkatalog nach Geschäftsstruktur, Richtlinien und Preisen organisieren.
- [Schlüssel mit eingeschränktem Zugriff](restricted-access-keys.md) - Erstellen, zuweisen und drehen Sie die Schlüssel, die zum Signieren von Token für den Katalogschutz verwendet werden.
