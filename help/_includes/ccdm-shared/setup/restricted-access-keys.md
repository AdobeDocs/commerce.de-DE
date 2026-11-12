---
source-git-commit: b6b737220a6dadf55b03da54e8d74226ed578cd0
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%
---
# Schlüssel mit eingeschränktem Zugriff

Mithilfe von eingeschränkten Zugriffsschlüsseln können autorisierte Client-Anwendungen auf eine [private Katalogansicht](private-catalog-view.md) zugreifen. Nur Anfragen mit einem gültigen signierten Token aus einem zugewiesenen Schlüssel können Katalogdaten abrufen. Alle anderen Anfragen werden abgelehnt, einschließlich Anfragen von Kunden, die keinen expliziten Zugriff auf diese Katalogansicht haben, und Skripte, die die Adobe Commerce Merchandising Services-API prüfen.

Es gibt zwei Möglichkeiten, eingeschränkte Zugriffsschlüssel bereitzustellen:

- **Automatisch für freigegebene B2B-Kataloge** - Das System stellt den Anfangsschlüssel für Katalogansichten bereit, die mit einem freigegebenen B2B-Katalog verknüpft sind, und weist ihn zu. Anschließend verwalten Sie die Schlüssel und die Schlüsselzuweisung über den Commerce-Administrator. Siehe [Authentifizierung der Katalogansicht](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-views-manage) im *Commerce-Administratorhandbuch*. Die automatische Bereitstellung ist in den folgenden Bereitstellungen verfügbar:

  - **Adobe Commerce as a Cloud Service mit CCDM** für Adobe Commerce B2B.
  - **Adobe Commerce in der Cloud oder lokal** über die [!DNL Adobe Commerce Optimizer Connector for B2B] mit Adobe Commerce Optimizer integriert. Die B2B-Erweiterung für den Connector ist erforderlich.

- **Manuell für jede Katalogansicht** - Um eine Katalogansicht selbst zu schützen, z. B. für ein Partnerportal oder eine Vorschau einer Vorabversion, führen Sie die Schritte in diesem Thema aus, beginnend mit [Erstellen eines eingeschränkten Zugriffsschlüssels](#create-a-restricted-access-key).

## Anwendungsfälle für Schlüssel mit eingeschränktem Zugriff

**[!UICONTROL Price Book ID]** bestimmt, welche Preise einer Anfrage angezeigt werden - sie erfasst die Preise und nicht, wer die Anfrage stellen kann. Jeder Kunde, der die ID und Preisbuch-ID einer Katalogansicht kennt, kann diese Daten über die Merchandising Services-API abrufen. Eingeschränkte Zugriffsschlüssel fügen eine separate, ergänzende Kontrolle hinzu: Sie ermöglichen es, überhaupt auf eine Katalogansicht zuzugreifen, unabhängig davon, welches Preisbuch gilt.

Eingeschränkte Zugriffsschlüssel werden häufig für Folgendes verwendet:

- **Vertragsbasierte B2B-Preisfindung** - Schränken Sie eine Katalogansicht ein, die mit einem ausgehandelten Preisbuch verknüpft ist, sodass nur der Käufer, für den es gilt, es abfragen kann. Andere Einkaufsorganisationen und die Öffentlichkeit können das nicht. Bei freigegebenen B2B-Katalogen wird dies automatisch eingerichtet. Siehe [Schlüsselverwaltung und -rotation](#key-management-and-rotation).
- **Partner- und Reseller-**: Beschränken Sie einen Teil des Katalogs auf genehmigte Partner, die direkt in die Merchandising Services-API integriert werden.
- **Vorabversionsvorschauen** - Ein vertrauenswürdiges internes System oder Partnersystem kann bevorstehende Produkte in der Vorschau anzeigen, bevor sie öffentlich sichtbar werden.

## Funktionsweise von eingeschränkten Zugriffsschlüsseln

Ein Schlüssel mit eingeschränktem Zugriff ist die öffentliche Komponente eines RSA-Schlüsselpaars. Ihre Client-Anwendung generiert und verwendet diesen Schlüssel, um zu beweisen, dass sie zum Lesen einer privaten Katalogansicht berechtigt ist. In diesem Zusammenhang bezieht _Client-Anwendung_ sich auf das Backend-System, das Käufer authentifiziert - z. B. benutzerdefinierte Logik auf [!DNL Adobe Commerce] oder einem Backend eines Drittanbieters - niemals das Storefront-Frontend selbst.

Die folgenden Schritte beschreiben, wie ein Schlüsselpaar und ein signiertes Token bei Katalogansichten, die nicht Teil eines B2B-freigegebenen Katalogs sind, von der Erstellung zur Validierung wechseln.

1. Ihre Client-Anwendung generiert ein RSA-Schlüsselpaar und behält den privaten Schlüssel bei.
1. Sie registrieren den **öffentlichen** Schlüssel im System als eingeschränkten Zugriffsschlüssel.
1. Ihre Client-Anwendung signiert ein JSON Web Token (JWT) mit dem privaten Schlüssel und fügt es bei jeder Anfrage in eine private Katalogansicht ein.

   Das System überprüft die Signatur des Tokens anhand des registrierten öffentlichen Schlüssels und gibt, falls gültig, die angeforderten Katalogdaten zurück.

## Zugriff auf den Arbeitsbereich mit eingeschränktem Zugriffsschlüssel

Wie Sie den Arbeitsbereich Schlüssel für eingeschränkten Zugriff öffnen, hängt vom verwendeten Produkt ab:

- **Adobe Commerce Admin** (Adobe Commerce as a Cloud Service) - Wählen Sie *System* > *Datenübertragung* > **Schlüssel mit eingeschränktem Zugriff**.
- **Adobe Commerce Optimizer Studio**—Wählen Sie *Store-Setup* > **Eingeschränkte Zugriffsschlüssel**.

## Erstellen eines eingeschränkten Zugriffsschlüssels

>[!NOTE]
>
>In diesem und den beiden folgenden Abschnitten wird der manuelle Prozess zur Verwaltung von eingeschränkten Zugriffsschlüsseln beschrieben. Verwalten Sie für freigegebene B2B-Kataloge mit automatischer Schlüsselbereitstellung die Schlüssel vom Commerce Admin. Siehe [Schlüssel für eingeschränkten Zugriff](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/catalog-view-sync/restricted-access-keys).

### Zugriffsschlüssel hinzufügen

Wählen Sie die Registerkarte für das Tool aus, das Sie zum Verwalten von Schlüsseln verwenden: Commerce Admin oder Adobe Commerce Optimizer Studio.

>[!BEGINTABS]

>[!TAB Adobe Commerce-Admin]

Kunden, die Adobe Commerce as a Cloud Service mit CCDM verwenden oder Adobe Commerce Optimizer über den Connector mit Adobe Commerce verbunden sind, können RSA-Schlüsselpaare von Commerce Admin generieren. Siehe [Verwalten eingeschränkter Zugriffsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/catalog-view-sync/restricted-access-keys).

>[!TAB Adobe Commerce Optimizer Studio - manuelle Schlüsselverwaltung]

Kunden und Kundinnen, die Adobe Commerce Optimizer Studio verwenden, müssen ihre eigenen RSA-Schlüsselpaare generieren und verwalten und dann den öffentlichen Schlüssel zum System hinzufügen. Dies ist der erforderliche Workflow für Adobe Commerce Optimizer mit einem Backend eines Drittanbieters. Kunden, die den Connector verwenden, können auch diesen Workflow anstelle des Commerce-Administrators verwenden.

**Generieren eines RSA-Schlüsselpaars**

Generieren Sie zum ersten Testen privater Katalogansichten ein Schlüsselpaar mit einem Tool wie [!DNL OpenSSL]. Behalten Sie den privaten Schlüssel geheim. Nur der öffentliche Schlüssel wird als eingeschränkter Zugriffsschlüssel in das System hochgeladen.

```bash
openssl genrsa -out private-key.pem 2048
openssl rsa -in private-key.pem -pubout -out public-key.pem
```

Die Schlüsselgröße muss zwischen 2048 und 8192 Bit liegen. `public-key.pem` enthält den Wert, den Sie in das **[!UICONTROL Public key]** Feld unten einfügen.

**Fügen Sie den öffentlichen Schlüssel zum System hinzu**

1. Klicken Sie im Arbeitsbereich Schlüssel für eingeschränkten Zugriff auf **[!UICONTROL Add Restricted Access Key]**.

   ![Liste der Schlüssel mit eingeschränktem Zugriff, mit der Schaltfläche Schlüssel hinzufügen](/help/assets/ccdm-shared/setup/restricted-access-keys.png){width="70%" zoomable="yes"}

1. Geben Sie die wichtigsten Details ein:

   ![Formular mit eingeschränktem Zugriffsschlüssel hinzufügen, mit Feldern für Titel, Ablaufdatum und öffentlichen Schlüssel](/help/assets/ccdm-shared/setup/restricted-access-keys-add.png){width="70%" zoomable="yes"}

   - **[!UICONTROL Title]** - Eine Beschriftung zur Identifizierung des Schlüssels, die in der Schlüsselliste und der Tastenauswahl für die Katalogansicht angezeigt wird, z. B. `ACME Corp wholesale portal — Tier 1 pricing`.
   - **[!UICONTROL Expiration date]** - Datum und Uhrzeit (UTC), nach der der Schlüssel nicht mehr berücksichtigt wird, auch nicht bei einem Token, das noch nicht abgelaufen ist.
   - **[!UICONTROL Public key]** - Der PEM-kodierte öffentliche RSA-Schlüssel im SPKI-Format (Subject Public Key Info), einschließlich der `-----BEGIN PUBLIC KEY-----`- und `-----END PUBLIC KEY-----`. Muss in der gesamten Umgebung eindeutig sein.

1. Klicken Sie auf **[!UICONTROL Save]**.

>[!ENDTABS]

Schlüssel sind nach der Erstellung unveränderlich. Um einen beliebigen Wert zu ändern, löschen Sie den Schlüssel und erstellen Sie einen neuen. Siehe [Drehen einer Taste](#rotate-a-key), um dies ohne Zugriffsunterbrechung zu tun.

## Zuweisen eines Schlüssels zu einer Katalogansicht

Ein eingeschränkter Zugriffsschlüssel authentifiziert den Zugriff erst, nachdem er einer Katalogansicht mit aktiviertem **[!UICONTROL Catalog Protection]** zugewiesen wurde. Siehe [Schützen einer &#x200B;](private-catalog-view.md#protect-a-catalog-view)) für Einrichtungsschritte.

## Schlüssel löschen

1. Suchen Sie im Arbeitsbereich **[!UICONTROL Restricted access keys]** den Schlüssel, den Sie entfernen möchten, und löschen Sie ihn.

   Wenn der Schlüssel einer oder mehreren Katalogansichten zugewiesen ist, wird in einer Warnung erläutert, dass Client-Anwendungen, die auf diesen Schlüssel angewiesen sind, den Zugriff verlieren. Die Katalogansichten selbst bleiben geschützt - sie werden nicht öffentlich zugänglich.

1. Bestätigen Sie den Löschvorgang.

## Schlüsselverwaltung und -rotation

Für die Verwaltung von eingeschränkten Zugriffsschlüsseln gibt es zwei Möglichkeiten, je nachdem, wie Sie den Katalogschutz verwenden:

- **Automatisch für freigegebene B2B-**: Für Adobe Commerce B2B-Bereitstellungen mit Merchandising Services mit CCDM und für Adobe Commerce Optimizer-Bereitstellungen, die über die [!DNL Adobe Commerce Optimizer Connector for B2B] integriert sind (wofür die B2B-Erweiterung erforderlich ist), generiert der Service automatisch den ersten eingeschränkten Zugriffsschlüssel und weist ihn zu, wenn eine Katalogansicht erstellt wird. Jede Katalogansicht erhält einen eigenen Schlüssel. Danach können Sie jeden Schlüssel über die Seiten Freigegebener Katalog oder Unternehmenskonto verwalten. Sie können Schlüssel auch über die Commerce Admin-Seite **Schlüssel mit eingeschränktem Zugriff** anzeigen und verwalten (**System** > **Datenübertragung**). Siehe [Konfiguration der Katalogansicht verwalten](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-views-manage).

  Jede Kombination aus einem freigegebenen Katalog und einer Shop-Ansicht wird als separate Katalogansicht projiziert. Eine Projektion ist die Katalogansicht, die Richtlinie, die Preisbuchreferenz und die Konfigurationsdaten mit eingeschränktem Zugriff, die für diese Kombination in die Merchandising Services-Datenschicht exportiert werden. Ein freigegebener Katalog, der mehreren Shop-Ansichten zugewiesen wurde, erzeugt mehrere Katalog-Ansichten, jede mit einem eigenen Schlüssel. Bearbeiten oder Drehen einer Taste für eine Katalogansicht, ohne die anderen zu beeinflussen.

  Standardmäßig ist ein langer Gültigkeitszeitraum für Schlüssel festgelegt. Wenn Sie einen Schlüssel drehen müssen, fügen Sie den Ersatz in der Admin hinzu und lassen Sie beide aktiv, bis Sie den alten Schlüssel entfernen.

- **Manuell für jede Katalogansicht** - Wie Sie Schlüssel generieren und verwalten, hängt von Ihrem Produktkontext ab. In beiden Fällen signiert der Backend-Client, der Käufer authentifiziert, die Token.

  - **Commerce Admin (Adobe Commerce as a Cloud Service mit CCDM oder Adobe Commerce Optimizer mit dem Connector)** Generieren Sie RSA-Schlüsselpaare in Commerce Admin und erstellen, zuweisen und löschen Sie Schlüssel auf der Seite **Schlüssel für eingeschränkten Zugriff**. Adobe Commerce dreht die Tasten nicht automatisch. Informationen zum Drehen einer Taste finden Sie [Drehen einer Taste](#rotate-a-key).
  - **Adobe Commerce Optimizer Studio**—Studio generiert keine Schlüssel. Dies ist der erforderliche Workflow für Adobe Commerce Optimizer mit einem Backend eines Drittanbieters, und Connector-Kunden können ihn auch verwenden. Verwenden Sie Ihre Client-Anwendung, um das RSA-Schlüsselpaar zu generieren, den privaten Schlüssel beizubehalten und den öffentlichen Schlüssel als eingeschränkten Zugriffsschlüssel hinzuzufügen. Verwenden Sie die zuvor in diesem Thema beschriebenen Schritte, um Schlüssel zu erstellen, hinzuzufügen und zu löschen. Informationen zum Drehen einer Taste finden Sie [Drehen einer Taste](#rotate-a-key).

### Drehen eines Schlüssels

Um einen Schlüssel ohne Zugriffsunterbrechung zu drehen, können einer Katalogansicht bis zu drei Schlüssel gleichzeitig zugewiesen werden:

Wählen Sie die Registerkarte für das Tool aus, das Sie zum Verwalten von Schlüsseln verwenden: Commerce Admin oder Adobe Commerce Optimizer Studio.

>[!BEGINTABS]

>[!TAB Adobe Commerce-Admin]

Siehe [Auswahl und Drehung von Tasten](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/catalog-view-sync/restricted-access-keys#key-selection-and-rotation). Dies gilt für Adobe Commerce as a Cloud Service mit CCDM und für Adobe Commerce-Projekte, die über den Adobe Commerce Optimizer-Connector in Adobe Commerce Optimizer integriert werden.

>[!TAB Adobe Commerce Optimizer Studio (manuelle Schlüsselverwaltung)]

Dieses Verfahren ist für Adobe Commerce Optimizer mit einem Backend eines Drittanbieters erforderlich. Kunden, die den Connector verwenden, können ihn auch anstelle von Commerce Admin verwenden.

1. Generieren Sie ein neues Schlüsselpaar und fügen Sie den neuen öffentlichen Schlüssel als neuen Schlüssel mit beschränktem Zugriff hinzu.
1. Weisen Sie der Katalogansicht den neuen Schlüssel neben dem vorhandenen Schlüssel zu.
1. Signieren Sie neue Token mit dem neuen privaten Schlüssel, um das Rollover des Schlüssels abzuschließen.
1. Sobald alle Client-Anwendungen mit dem neuen Schlüssel bestätigt wurden, entfernen und löschen Sie den alten Schlüssel.

>[!ENDTABS]

## Beschränkungen

Siehe [Katalogansichten und Richtlinienbeschränkungen](https://experienceleague.adobe.com/en/docs/commerce/optimizer/boundaries-limits).

## Ähnliche Themen

- [Private Katalogansichten](private-catalog-view.md) - Erfahren Sie, wie Sie eine Katalogansicht mit eingeschränkten Zugriffsschlüsseln schützen.
