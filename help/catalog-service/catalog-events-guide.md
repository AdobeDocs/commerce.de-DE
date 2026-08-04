---
title: Handbuch zur Integration von Katalogereignissen und Adobe I/O Events
description: Erfahren Sie, wie Sie Katalogdaten überprüfen [!DNL Adobe I/O Events]  für Adobe Commerce konfigurieren, Katalogereignistypen abonnieren und den Versand für Verbraucher validieren können.
level: Intermediate
recommendations: noCatalog
role: Admin, Developer
feature: Services, Catalog Service
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: c32adafa-ed01-4b31-997e-2413013911b0
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 15aaeadde61b9d70ec107db2ed4c118d1f8ee731
workflow-type: tm+mt
source-wordcount: 1567
ht-degree: 0%

---

# Handbuch zur Integration von Katalogereignissen und [!DNL Adobe I/O Events]

Katalogereignisse sind maschinengenerierte Benachrichtigungen, die unterstützte Katalogänderungen beschreiben, die über [!DNL Catalog Service] bereitgestellt werden. Sie ermöglichen ereignisgesteuerte Workflows, wie etwa:

* Externe Caches oder Dienste mit Katalogaktualisierungen synchronisieren.
* Auslösen nachgelagerter Prozesse, wenn sich Produkte, Varianten, Preise oder Kategorien ändern.
* Anwendungsfälle für Experience Edge und [!DNL Edge Delivery Services], die nahezu in Echtzeit Katalogaktualisierungen erfordern.

Den End-to-End-Pfad von [!DNL Adobe Commerce] zu Ihren Ereigniskonsumenten finden Sie unter [Ereignisbereitstellung bis [!DNL Adobe I/O Events]](#event-delivery-through-adobe-io-events).

## Unterstützte Ereignistypen {#supported-event-types}

Katalogereignisse konzentrieren sich auf Storefront-relevante Änderungen, die über [!DNL Adobe Developer Console] verfügbar gemacht werden. Die folgenden Abonnements werden derzeit unterstützt.

| Abonnement | Ereignisse |
| --- | --- |
| Produktaktualisierung | Produktänderungen für Produkte, die über [!DNL Catalog Service] verfügbar sind, erstellen, aktualisieren und löschen |
| Preisaktualisierung | Preisänderungen erstellen, aktualisieren und löschen, die sich auf die Katalogdaten der Storefront auswirken |

Zu jedem Ereignis gehören:

* Eine Ereigniskennung, die den Änderungstyp beschreibt.
* Entitäts- und Umgebungskontext, z. B. Instanz-ID und SKU
* Eine Payload, die die geänderte Entität und relevante Bereichsinformationen beschreibt.


## Beispiel für Ereignis-Payloads

**ProductUpdated-Ereignis**

```json
{
  "imsOrgId": "aaa-0",
  "instanceId": "instance-9",
  "eventCode": "productUpdated",
  "sku": "1234",
  "links": [
    {"type":  "variantOf", "sku": "5678"}
   ],
  "scope": [
    { "storeViewCode": "US-us" },
    { "storeViewCode": "FR-fr" },
    { "storeViewCode": "DE-de" }
  ]
}
```

**PriceUpdated-Ereignis**

```json
{
  "imsOrgId": "aaa-0",
  "instanceId": "instance-9",
  "eventCode": "priceUpdated",
  "sku": "1234",
  "scope": [
    {
      "websiteCode": "website1",
      "customerGroupCode": "customer-group-code1"
    },
    {
      "websiteCode": "website2",
      "customerGroupCode": "customer-group-code2"
    }
  ]
}
```

## Versand von Ereignissen über [!DNL Adobe I/O Events] {#event-delivery-through-adobe-io-events}

[!DNL Adobe I/O Events] stellt Katalogereignisse für Ihre Integrationen bereit. Das folgende Diagramm zeigt den allgemeinen Fluss von Katalogänderungen von [!DNL Adobe Commerce] über [!DNL Catalog Service] und [!DNL Adobe I/O Events] zu abonnierten Verbrauchern:

![Allgemeiner Fluss von Katalogereignissen aus Adobe Commerce über den Katalog-Service und Adobe I/O Events an abonnierte Kunden](assets/catalog-service-event-pipeline.png)

In den folgenden Schritten wird jede Übergabe detaillierter erläutert:

1. **Adobe Commerce → Catalog Service**

[!DNL Adobe Commerce] exportiert Katalogdaten mithilfe der unterstützten SaaS-Datenexporterweiterungen in [!DNL Catalog Service].

1. **Catalog Service-Verarbeitung**

   * [!DNL Catalog Service] verarbeitet unterstützte Katalogänderungen und bereitet sie für die Ereignisbereitstellung vor.

1. **Katalog-Service → Adobe I/O Events**

* Katalogereignisse werden in [!DNL Adobe I/O Events] veröffentlicht.
* Nutzerinnen und Nutzer melden sich mit Journaling, Webhooks, [!DNL Adobe I/O Runtime], Amazon EventBridge oder anderen unterstützten Versandmechanismen an.

[!DNL Adobe I/O Events] bietet:

* *Mindestens einmaliger Versand* pro Abonnent (doppelte Ereignisse sind möglich).
* Keine Bestellgarantien für alle Sendungen.

Ihre Kunden müssen mit doppelten Ereignissen und nicht ordnungsgemäßer Bereitstellung umgehen. Siehe [Idempotenz](#idempotency) für Implementierungsanleitungen.

## Anwendungsszenarien {#use-cases}

Sie können Katalogereignisse in mehreren Szenarien verwenden.

### Statische Site- und Edge-Bereitstellung

* Generieren oder Invalidieren von Katalogseiten und Storefront-Fragmenten, wenn sich Katalogdaten ändern.
* Vermeiden Sie häufiges Abrufen [!DNL Catalog Service] APIs.

### Suchindizierung und Caching

* Inkrementelle Aktualisierungen des Triggers in nachgelagerten Suchindizes.
* Aktualisieren Sie Cache-Ebenen oder externe Ansichten des Katalogs, wenn sich Produkt- oder Kategoriedaten ändern.

### Integration mit externen Systemen

* Weiterleiten von Katalogänderungen an externe Systeme wie PIM, Preisfindungs-Engines oder andere Branchensysteme.
* Synchronisierung nachgelagerter Anwendungen ohne direkten Datenbankzugriff.

### Überwachung und Beobachtbarkeit

Kombinieren Sie Katalogereignisse mit vorhandener Überwachung (z. B. [!DNL Grafana] und [!DNL Prometheus]), um:

* Überwachen des Ereignisdurchsatzes.
* Erkennen von Anomalien im Katalogaktualisierungsvolumen.

## Katalogereignisse aktivieren {#enable-catalog-events}

Gehen Sie wie folgt vor, um Katalogereignisse End-to-End zu aktivieren.

>[!PREREQUISITES]
>
>Stellen Sie vor dem Aktivieren von Katalogereignissen Folgendes sicher:
>
>* Eine unterstützte Adobe Commerce-Umgebung mit aktiviertem [!DNL Catalog Service].
>* [Die  [!DNL Adobe I/O]  ist für Adobe Commerce konfiguriert](https://developer.adobe.com/commerce/extensibility/events/configure-commerce).
>* Zugriff auf [!DNL Adobe Developer Console] in derselben IMS-Organisation, in der die Commerce-Umgebung bereitgestellt wurde.
>* Um die Synchronisierung mit Commerce SaaS-Services zu überprüfen, verwenden Sie die **[!UICONTROL Data Management Dashboard]** in der Admin Console.
>* Product Recommendations v6.0, [!DNL Live Search] v4.1.0+ oder [!DNL Catalog Service] v1.17+ ist für die Dashboard-Überprüfung erforderlich. Adobe empfiehlt, Ihr Commerce-Projekt auf die neuesten unterstützten Versionen dieser Services zu aktualisieren. Verwenden Sie für frühere Service-Versionen [Katalogsynchronisierung](https://experienceleague.adobe.com/de/docs/commerce/user-guides/data-services/catalog-sync) für die Synchronisierungsüberprüfung.


>[!NOTE]
>
>Um Katalogereignisse zu verwenden, konfigurieren Sie zunächst die Commerce-Umgebung für [!DNL Adobe I/O Events] und registrieren Sie dann in [!DNL Adobe Developer Console] ein Ereignisabonnement.
>
>Wenn Ihre Umgebung nach der Konfiguration nicht in [!DNL Adobe Developer Console] angezeigt wird, stellen Sie sicher, dass Sie bei der richtigen IMS-Organisation angemeldet sind und dass Ihr Konto über den erforderlichen Zugriff verfügt. Wenn die Umgebung weiterhin nicht angezeigt wird, wenden Sie sich an den Adobe-Support.

### Überprüfen von Katalogdaten {#verify-catalog-data}

Stellen Sie vor der Konfiguration sicher, dass [!DNL Catalog Service] über aktuelle Katalogdaten aus Ihrer [!DNL Commerce] verfügt. Katalogereignisse hängen davon ab, [!DNL SaaS Data Export] zwei Schritte ausgeführt werden. Bestätigen Sie **beide**:

1. Bestätigen Sie **erfolgreichen Feed-Export aus Commerce**.

   Öffnen Sie von der [!DNL Adobe Commerce] Admin aus die Seite [Daten-Feed](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status)Synchronisierungsstatus) (**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Data Feed Sync Status]**) und bestätigen Sie, dass der letzte Exportstatus für jeden [!DNL Catalog Service]-Feed erfolgreich ist.

1. Bestätigen Sie über **Admin die erfolgreiche Synchronisierung mit** verbundenen Commerce-Services[!DNL Adobe Commerce].

   Öffnen Sie vom [!DNL Adobe Commerce] Admin aus das [Daten-Management-Dashboard](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard) (**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Data Management Dashboard]**) und überprüfen Sie, ob die synchronisierten Produktdaten die erwarteten Produkte enthalten.

### Registrieren und [!DNL Adobe I/O Events] abonnieren {#register-events}

Legen Sie fest, welche Commerce-Ereignisse abonniert werden sollen, und registrieren Sie sie dann im Projekt.

Wenn sich Ihre Instanz nicht in der Auswahlliste befindet, ist sie nicht mit [!DNL Adobe I/O] verbunden. Anweisungen zum Beheben des Problems finden Sie unter [Konfigurieren der  [!DNL Adobe I/O] -Verbindung](https://developer.adobe.com/commerce/extensibility/events/configure-commerce#configure-the-adobe-io-connection) in der *Adobe Commerce Developer* Dokumentation.

1. Melden Sie sich von der [!DNL Adobe Developer Console] aus bei derselben IMS-Organisation an, die für das Commerce-Projekt verwendet wurde.

1. Erstellen Sie ein Projekt für Commerce-Katalogereignisse oder fügen Sie die Ereignis-API einem vorhandenen Projekt hinzu.

   * Wählen Sie **[!UICONTROL APIs and services]** in der oberen Navigationsleiste aus.

   * Wählen Sie auf der Seite **[!UICONTROL Browse APIs and services]** die Registerkarte **[!UICONTROL Events]** aus.

   * Schnelles Auffinden der APIs für Commerce-Katalogereignisse. Geben Sie _Katalog_ in das Suchfeld ein oder filtern Sie nach dem **[!UICONTROL Commerce]**.

   * Wählen Sie auf der **[!UICONTROL Commerce Catalog Events]** Karte **[!UICONTROL Project]** aus.

   ![Commerce-Anbieter für Katalogereignisse, der auf der Seite „APIs und Services durchsuchen“ ausgewählt ist](assets/catalog-event-select-provider.png){width="600" zoomable="yes"}

1. Konfigurieren der Ereignisregistrierung.

   Wählen Sie die Commerce-Instanz aus, von der Ereignisbenachrichtigungen empfangen werden sollen. Wählen Sie dann **[!UICONTROL Next]** aus.

   ![Commerce-Instanz im Bildschirm zur Ereignisregistrierung ausgewählt](assets/catalog-event-registration.png){width="600" zoomable="yes"}

1. Wählen Sie die Ereignisse aus, die abonniert werden sollen.

   Wählen Sie die unterstützten Ereignisabonnements aus, die Sie erhalten möchten, z. B. **[!UICONTROL Product Update]** oder **[!UICONTROL Price Update]**. Wählen Sie dann **[!UICONTROL Next]** aus.

   ![Ereigniskategorien, die im Registrierungsbildschirm für das Abonnement ausgewählt wurden](assets/catalog-event-subscription.png){width="600" zoomable="yes"}

1. OAuth-Server-zu-Server-Anmeldedaten hinzufügen.

   Geben Sie einen **[!UICONTROL Credential name]** ein. Wählen Sie dann **[!UICONTROL Next]** aus.

1. Geben Sie einen **[!UICONTROL Event registration name]** und einen **[!UICONTROL Event registration description]** ein. Wählen Sie dann **[!UICONTROL Next]** aus.

1. Akzeptieren Sie auf dem letzten Registrierungsbildschirm den Standardverbraucher, die Journal-API.

   Mit der standardmäßigen Journal-API für Privatkunden können Sie die Ereignisregistrierung testen und bestätigen, dass Ereignisse bereitgestellt werden. Wenn Sie bereits einen Webhook oder [!DNL Adobe I/O Runtime] Aktionsbenutzer konfiguriert haben, wählen Sie ihn hier aus. Andernfalls müssen Sie die Ereignisregistrierung später bearbeiten, wenn der Kunde bereit ist.

   ![Journal-API: Verbraucher-Standardeinstellung ist im Bildschirm zum Abschluss der Ereignisregistrierung ausgewählt](assets/catalog-event-consumer.png){width="600" zoomable="yes"}

1. Wählen Sie **[!UICONTROL Complete registration]** aus.

### Konfigurieren des Ereignisverbrauchers {#configure-consumer}

1. Konfigurieren Sie einen Verbraucher, z. B.:

   * Ein Webhook-Endpunkt
   * Eine [!DNL Adobe I/O Runtime] Aktion
   * Ein weiteres unterstütztes Ziel

1. Wenn Sie bei der Registrierung keinen Verbraucher ausgewählt haben, bearbeiten Sie die Ereignisregistrierung, um die Verbraucherdetails hinzuzufügen.

   * Bearbeiten Sie in der [!DNL Adobe Developer Console] Ihr Projekt. Wählen Sie dann die von Ihnen erstellte Ereignisregistrierung aus.

   * Wählen Sie auf der Seite Details zur Ereignisregistrierung **[!UICONTROL Edit Events Registration]** aus.

   * Wählen Sie **[!UICONTROL Next]** aus, bis der Bildschirm Verbraucherauswahl angezeigt wird. Wählen Sie dann den konfigurierten Verbraucher aus.

   * Aktualisieren Sie den -Verbraucher auf Ihr konfiguriertes Ziel. Wählen Sie dann **[!UICONTROL Save configured events]** aus.

### Validieren des Ereignisflusses {#validate-event-flow}

Katalogereignisse sind für Ihre Umgebung aktiviert. Wenn sich Katalogdaten in [!DNL Commerce] ändern, fließen Aktualisierungen über [!DNL Catalog Service] zu [!DNL Adobe I/O Events], und Ihr abonnierter Benutzer erhält das entsprechende Katalogereignis. Lesen Sie [Beschränkungen und Best Practices](#limits-and-best-practices) bevor Sie Produktionsintegrationen erstellen.
1. Nehmen Sie eine einfache unterstützte Katalogänderung vor, z. B. die Aktualisierung eines Produktnamens oder die Änderung eines Preises.

1. Bestätigen Sie die folgenden Ergebnisse:

   * Die Änderung ist über [!DNL Catalog Service] APIs sichtbar.
   * Ihr [!DNL Adobe I/O Events] Verbraucher erhält das entsprechende Produkt- oder Preisereignis.


## Beschränkungen und Best Practices {#limits-and-best-practices}

Befolgen Sie beim Aufbauen auf Katalogereignissen die folgenden Best Practices.

### Idempotenz {#idempotency}

[!DNL Adobe I/O Events] können dasselbe Katalogereignis mehrmals bereitstellen, und Ereignisse für ein einzelnes Produkt können nicht in der richtigen Reihenfolge eingehen. Gestalten Sie Verbraucher als idempotent durch:

* Verwenden von Entitäts-IDs mit einem Feld für Version oder Zeitstempel.
* Doppelte Benachrichtigungen für dieselbe Änderung werden ignoriert.

### Durchsatz und Gegendruck

Große Kataloge mit hohen Aktualisierungsraten können ein signifikantes Ereignisvolumen erzeugen. Stellen Sie sicher, dass:

* Verbraucher können Ereignisse bei maximalem Durchsatz verarbeiten.
* Bei Bedarf können Sie Puffer- oder Batch-Vorgänge oder Warteschlangen verwenden.

### Sicherheit und Isolation

* [!DNL Adobe I/O Events] erzwingt *Mandantenisolation*.
* Ihr Unternehmen erhält Ereignisse nur für seine eigenen Umgebungen und Berechtigungen.

### Schemaentwicklung

Payloads von Katalogereignissen folgen demselben konzeptionellen Modell wie [!DNL Catalog Service]-APIs. So bleiben Sie vorwärtskompatibel:

* Vermeiden Sie nach Möglichkeit eine strikte Schemadurchsetzung.
* Unbekannte Felder ignorieren, anstatt fehlzuschlagen.

## Fehlerbehebung bei Katalogereignissen {#troubleshoot-catalog-events}

Wenn Katalogereignisse fehlen oder sich verzögern, führen Sie die folgenden Schritte aus.

1. **Überprüfen Sie die Daten des Katalog-Service**

   [Verwenden Sie die  [!DNL Catalog Service] -](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/), um zu bestätigen, dass die Katalogänderung erfolgreich gespeichert wurde.

1. **Überprüfen von[!DNL SaaS Data Export]**

   Katalogereignisse erfordern aktuelle Daten in [!DNL Catalog Service]. Bestätigen Sie beide Schritte des Exportpfads:

   * **Feed-Export aus Commerce** - Bestätigen Sie auf der Seite [Status der &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status) des Daten-Feeds) oder in `var/log/saas-export.log`, dass [!DNL Catalog Service] Feeds erfolgreich aus [!DNL Commerce] exportiert wurden.

   * **Mit verbundenen Commerce SaaS-Services synchronisieren** - Bestätigen Sie im [Data Management Dashboard](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard), [Catalog Sync](https://experienceleague.adobe.com/de/docs/commerce/user-guides/data-services/catalog-sync) oder in den Exportprotokollen, dass die Daten erfolgreich mit [!DNL Catalog Service] synchronisiert wurden.

   Informationen zur Fehlerbehebung bei Export- und Synchronisierungsaufträgen finden Sie unter [Synchronisieren von Daten mit dem SaaS](../data-export/data-sync-manage.md)Datenexport und [Protokollierung und Fehlerbehebung](../data-export/troubleshooting/logging.md).

1. **Validieren [!DNL Adobe I/O Events] Konfiguration**

   Bestätigen Sie Folgendes:

   * Sie sind bei der richtigen IMS-Organisation in [!DNL Adobe Developer Console] angemeldet.
   * Der **[!UICONTROL Commerce Catalog Events]** ist aktiviert.
   * Der erwartete **[!UICONTROL Commerce Catalog Events]** und die Umgebung sind sichtbar.
   * Das Abonnement ist aktiv.
   * Ihr Endpunkt, Ihre Aktion oder Ihr Journal-Verbraucher kann Testereignisse empfangen und verarbeiten.

1. **Adobe-Support kontaktieren**

   Wählen Sie beim Öffnen eines Support-Tickets den Problemgrund aus, der der **Adobe Commerce-** entspricht, und geben Sie die folgenden Informationen ein:

   * Details zum Katalog-Service (Umgebung, Region).
   * [!DNL Adobe I/O Events] Abonnementdetails.
   * Ungefähre Zeit und Beschreibung fehlender Ereignisse.

   Weitere Hilfe finden Sie unter [Support-Tickets](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case).

>[!MORELIKETHIS]
>
>
>* [Onboarding und Installation](installation.md)
>* [Erste Schritte mit dem Katalog-Service](get-started.md)
>* [Synchronisieren von Daten mit dem SaaS-Datenexport](../data-export/data-sync-manage.md)
>* [Abrufen von Katalogdaten mit der GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/){target="_blank"}
>* [[!DNL Catalog Service] und API-Mesh](mesh.md)
>* [Konfigurieren der  [!DNL Adobe I/O] -Verbindung](https://developer.adobe.com/commerce/extensibility/events/configure-commerce#configure-the-adobe-io-connection){target="_blank"}
>* [[!DNL Adobe I/O Events]](https://developer.adobe.com/events/docs/guides/){target="_blank"}
