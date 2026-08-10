---
title: Schlüssel mit eingeschränktem Zugriff
description: Erfahren Sie, wie Sie eingeschränkte Zugriffsschlüssel erstellen, zuweisen und drehen, um Katalogansichten in mit  [!DNL Adobe Commerce Optimizer] -Token-Authentifizierung zu schützen.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
TQID: https://experienceleague.adobe.com/Jmze0Pq3kSNMIXqkkML-hmmlZnv-XKgeEgRB8Q8NZ6s
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
nudge: true
source-git-commit: 688bc6e28a4c5a94b1fe55c84f7c05401dd651bc
workflow-type: tm+mt
source-wordcount: 791
ht-degree: 0%

---

# Schlüssel für eingeschränkten Zugriff

Mithilfe von eingeschränkten Zugriffsschlüsseln können autorisierte Client-Anwendungen auf eine [private Katalogansicht](catalog-view.md) zugreifen. Nur Anfragen mit einem gültigen signierten Token aus einem zugewiesenen Schlüssel können Katalogdaten abrufen. Alle anderen Anfragen werden abgelehnt, einschließlich Anfragen von anonymen Käufern, Käufern, denen kein expliziter Zugriff auf diese Katalogansicht gewährt wurde, und Skripten, die die API untersuchen.

## Anwendungsfälle für Schlüssel mit eingeschränktem Zugriff

[!DNL Adobe Commerce Optimizer] bestimmt **[!UICONTROL Price Book ID]**, welche Preise eine Anfrage sieht - sie umfasst die Preise, nicht, wer die Anfrage stellen kann. Jeder Kunde, der die ID und Preisbuch-ID einer Katalogansicht kennt, kann diese Daten über die Merchandising-API abrufen. Eingeschränkte Zugriffsschlüssel fügen eine separate, ergänzende Kontrolle hinzu: Sie ermöglichen es, überhaupt auf eine Katalogansicht zuzugreifen, unabhängig davon, welches Preisbuch gilt.

Eingeschränkte Zugriffsschlüssel werden häufig für Folgendes verwendet:

- **Vertragsbasierte B2B-Preisfindung** - Schränken Sie eine Katalogansicht ein, die mit einem ausgehandelten Preisbuch verknüpft ist, sodass nur der Käufer, für den es gilt, es abfragen kann. Andere Einkaufsorganisationen und die Öffentlichkeit können das nicht.
- **Partner- und Reseller-**: Beschränken Sie eine Teilmenge des Katalogs auf genehmigte Partner, die direkt in die Merchandising-API integriert werden.
- **Vorabversionsvorschauen** - Ein vertrauenswürdiges internes System oder Partnersystem kann bevorstehende Produkte in der Vorschau anzeigen, bevor sie öffentlich sichtbar werden.

>[!IMPORTANT]
>
>Schlüsselgenerierung, Token-Signierung und Rotation werden derzeit vollständig von der Backend-Client-Anwendung verwaltet, die Käufer authentifiziert. [!DNL Adobe Commerce Optimizer] generiert oder dreht diese Schlüssel nicht in Ihrem Auftrag.

## Funktionsweise von eingeschränkten Zugriffsschlüsseln

Ein Schlüssel mit eingeschränktem Zugriff ist die öffentliche Komponente eines RSA-Schlüsselpaars. Ihre Client-Anwendung generiert und verwendet diesen Schlüssel, um zu beweisen, dass sie zum Lesen einer privaten Katalogansicht berechtigt ist. In diesem Zusammenhang bedeutet „Client-Anwendung“ das Backend-System, das Kunden authentifiziert - z. B. benutzerdefinierte Logik auf [!DNL Adobe Commerce] oder das Backend eines Drittanbieters -, niemals das Storefront-Frontend selbst.

Die folgenden Schritte beschreiben, wie ein Schlüsselpaar und ein signiertes Token von der Erstellung zur Validierung wechseln:

1. Ihre Client-Anwendung generiert ein RSA-Schlüsselpaar und behält den privaten Schlüssel bei.
1. Sie registrieren den **öffentlichen** Schlüssel in [!DNL Commerce Optimizer] als eingeschränkten Zugriffsschlüssel.
1. Ihre Client-Anwendung signiert ein JSON Web Token (JWT) mit dem privaten Schlüssel und fügt es bei jeder Anfrage in eine private Katalogansicht ein.
1. [!DNL Commerce Optimizer] validiert die Signatur des Tokens anhand des registrierten öffentlichen Schlüssels und gibt, falls gültig, die angeforderten Katalogdaten zurück.

## Erstellen eines eingeschränkten Zugriffsschlüssels

Generieren Sie zum ersten Testen privater Katalogansichten ein Schlüsselpaar mit einem Tool wie [!DNL OpenSSL]. Geheimnis des privaten Schlüssels beibehalten - nur der öffentliche Schlüssel wird in [!DNL Commerce Optimizer] hochgeladen.

```bash
openssl genrsa -out private-key.pem 2048
openssl rsa -in private-key.pem -pubout -out public-key.pem
```

Die Schlüsselgröße muss zwischen 2048 und 8192 Bit liegen. `public-key.pem` enthält den Wert, den Sie in das **[!UICONTROL Public key]** Feld unten einfügen.

## Hinzufügen eines eingeschränkten Zugriffsschlüssels zu [!DNL Commerce Optimizer]

1. Gehen Sie im linken Menü in [!DNL Adobe Commerce Optimizer Studio] zu **[!UICONTROL Store setup]** und klicken Sie auf **[!UICONTROL Restricted access keys]**.

   ![Liste der Schlüssel mit eingeschränktem Zugriff, mit der Schaltfläche Schlüssel hinzufügen](../assets/restricted-access-keys.png){width="70%" zoomable="yes"}

1. Klicken Sie auf **[!UICONTROL Add Restricted Access Key]**.

1. Geben Sie die wichtigsten Details ein:

   ![Formular mit eingeschränktem Zugriffsschlüssel hinzufügen, mit Feldern für Titel, Ablaufdatum und öffentlichen Schlüssel](../assets/restricted-access-keys-add.png){width="70%" zoomable="yes"}

   - **[!UICONTROL Title]** - Eine Beschriftung zur Identifizierung des Schlüssels, die in der Schlüsselliste und der Tastenauswahl für die Katalogansicht angezeigt wird, z. B. `ACME Corp wholesale portal — Tier 1 pricing`.
   - **[!UICONTROL Expiration date]** - Datum und Uhrzeit (UTC), nach der der Schlüssel nicht mehr berücksichtigt wird, auch nicht bei einem Token, das noch nicht abgelaufen ist.
   - **[!UICONTROL Public key]** - Der PEM-kodierte öffentliche RSA-Schlüssel im SPKI-Format (Subject Public Key Info), einschließlich der `-----BEGIN PUBLIC KEY-----`- und `-----END PUBLIC KEY-----`. Muss in der gesamten Umgebung eindeutig sein.

1. Klicken Sie auf **[!UICONTROL Save]**.

Schlüssel sind nach der Erstellung unveränderlich. Um einen beliebigen Wert zu ändern, löschen Sie den Schlüssel und erstellen Sie einen neuen. Siehe [Drehen einer Taste](#rotate-a-key), um dies ohne Zugriffsunterbrechung zu tun.

## Zuweisen eines Schlüssels zu einer Katalogansicht

Ein Schlüssel mit eingeschränktem Zugriff schränkt den Zugriff nur ein, nachdem er einer Katalogansicht mit aktiviertem **[!UICONTROL Catalog Protection]** zugewiesen wurde. Siehe [Schützen einer &#x200B;](private-catalog-view.md#protect-a-catalog-view)) für Einrichtungsschritte.

## Schlüssel löschen

1. Suchen Sie auf der Seite **[!UICONTROL Restricted access keys]** den zu entfernenden Schlüssel und klicken Sie auf **[!UICONTROL Delete]**.

   Wenn der Schlüssel einer oder mehreren Katalogansichten zugewiesen ist, wird in einer Warnung erläutert, dass Client-Anwendungen, die auf diesen Schlüssel angewiesen sind, den Zugriff verlieren. Die Katalogansichten selbst bleiben geschützt - sie werden nicht öffentlich zugänglich.

1. Bestätigen Sie den Löschvorgang.

## Drehen eines Schlüssels

Um einen Schlüssel ohne Zugriffsunterbrechung zu drehen, können einer Katalogansicht bis zu drei Schlüssel gleichzeitig zugewiesen werden:

1. Generieren Sie ein neues Schlüsselpaar und fügen Sie den neuen öffentlichen Schlüssel als neuen Schlüssel mit beschränktem Zugriff hinzu.
1. Weisen Sie der Katalogansicht den neuen Schlüssel neben dem vorhandenen Schlüssel zu.
1. Signieren Sie neue Token mit dem neuen privaten Schlüssel, um das Rollover des Schlüssels abzuschließen.
1. Sobald alle Client-Anwendungen mit dem neuen Schlüssel bestätigt wurden, entfernen und löschen Sie den alten Schlüssel.

## Beschränkungen

Siehe [Katalogansichten und Richtlinienbeschränkungen](../boundaries-limits.md#catalog-views-and-policies).

## Ähnliche Themen

- [Private Katalogansichten](private-catalog-view.md) - Erfahren Sie, wie Sie eine Katalogansicht mit eingeschränkten Zugriffsschlüsseln schützen.

