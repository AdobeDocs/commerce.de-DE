---
title: Zusammensetzbares Katalogdatenmodell und Merchandising-Services
description: Erfahren Sie, wie das zusammenstellbare Katalogdatenmodell die Katalogbereitstellung in [!DNL Adobe Commerce as a Cloud Service] ändert und was Händler und Storefront-Teams wissen müssen.
feature: Catalog Management, Personalization, Saas
role: Leader
level: Beginner
autotag-review: '2026-11-09T05:07:21.124Z'
TQID: 'https://experienceleague.adobe.com/5Aaumfx9-lOBMDOg59rr-MMl-0sgFLSVUzngkdzfyR0'
product_v2:
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4273989f-0bf2-5361-a17a-6909488d18ab
    internal-label: Catalog Service
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
    internal-label: Order Management System
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dec06508-d41f-555a-87e8-29e8bcdfa95a
    internal-label: Recommendations
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
    internal-label: Reporting
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: c67e36c5a607fa1112a3a34b71c89de1b0162b10
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 0%
---

# Merchandising-Services

Adobe Commerce as a Cloud Service unterstützt jetzt das Composable Catalog Data Model (CCDM) über Merchandising Services. Adobe Commerce Optimizer führte dieses Datenmodell ein, und CCDM bietet beiden Produkten eine gemeinsame Grundlage für die Bereitstellung von Funktionen zum Durchsuchen des Storefront-Katalogs und für Merchandising, während Commerce Foundation weiterhin Produkte, Preise und Transaktionen verwaltet.

In diesem Thema wird erläutert, was sich mit CCDM ändert, welche Funktionen weiterhin verwendet werden und was die Änderung für Händler, Partner und Entwickler von Storefronts bedeutet.

## Welche Änderungen führt CCDM ein?

Das ursprüngliche Katalogmodell verwendet den Katalog-Service, um Produktdaten an Storefronts bereitzustellen, wobei Live Search und Product Recommendations Such-, Merchandising- und Empfehlungsfunktionen bieten. In diesem Modell synchronisiert Commerce mithilfe des [SaaS-Datenexports](https://experienceleague.adobe.com/en/docs/commerce/saas-data-export/overview).

Beim CCDM basieren diese Funktionen auf derselben Katalogbasis, die auch Adobe Commerce Optimizer unterstützt. [Katalogansichten](../optimizer/setup/catalog-view.md) und [Richtlinien](../optimizer/setup/policies.md) definieren den Katalogkontext, der für eine Storefront verfügbar ist. Richtlinien bestimmen das Produktsortiment, und Merchandising-Regeln können für alle Katalogansichten gelten oder auf eine bestimmte Ansicht zugeschnitten sein.

Dies ändert die Art und Weise, wie der Katalog konfiguriert, aufgerufen und vermarktet wird. CDM baut auf den Such-, Recommendations- und Merchandising-Funktionen des ursprünglichen Commerce-Katalogs auf und führt gleichzeitig Steuerelemente auf Katalogansichtsebene ein. Im Folgenden werden zusätzliche Management- und Reporting-Funktionen beschrieben.

Commerce Foundation bleibt die kanonische Quelle für Produkte und Preise. Produkt- und Preisdaten werden über eine native Adobe Commerce as a Cloud Service-Integration auf eine Weise mit dem CDM synchronisiert. Die Konfiguration von Websites, Stores und Store-Ansichten bleibt neben den bestehenden Workflows für Warenkorb, Checkout und Bestellverwaltung in Commerce.

## Lizenzierung und Bereitstellung

Merchandising-Services sind in der bestehenden Adobe Commerce as a Cloud Service-SKU enthalten. Es handelt sich nicht um ein zweites Produkt oder Abonnement, und es ist kein separater Kauf, keine Berechtigung oder kein separater Mandant für Adobe Commerce Optimizer erforderlich.

## Überblick über die Architektur

Die [!DNL Commerce Foundation] bleibt der wichtigste Datensatz für Produkte und Preise und verwaltet weiterhin Transaktionen. Die native Integration synchronisiert Produkt- und Preisdaten von [!DNL Commerce] bis CCDM. Für diese Synchronisierung wird weder ein separater Connector noch eine [!DNL App Builder] App installiert.

Storefronts verwenden CDM-gestützte Merchandising-Services zum Abrufen von Katalogdaten und -kontext für Browsen, Suchen, Recommendations und Merchandising. Anfragen verwenden den Katalogkontext, um Produkte und Preise für die vorgesehene Zielgruppe abzurufen. Sie weiterhin die Konfiguration von Websites, Stores und Store-Ansichten in [!DNL Commerce] verwalten.

Die folgende Abbildung zeigt die Position von Merchandising Services in der umfassenderen Adobe Commerce as a Cloud Service-Architektur.

![Commerce-Architektur, die den Katalogdatenfluss in die Merchandising-Services anzeigt](./assets/data-flow-ccdm.png){zoomable="yes"}

## Was gibt es Neues für Händler?

Mit dem neuen Modell können Sie bestehende Merchandising-Regeln auf alle Katalogansichten oder auf eine bestimmte Ansicht beschränken. Auf diese Weise können Sie Merchandising auf jede Storefront-Zielgruppe anwenden. Erfahren Sie, wie [eine Merchandising-Regel auf Katalogansichten &#x200B;](../optimizer/merchandising/rules/add.md#create-a-rule).

Im Admin-Bereich können Sie den Katalogkontext mit [!UICONTROL Catalog Views] und [!UICONTROL Policies] konfigurieren. Sie können [!UICONTROL Success Metrics] auch verwenden, um Umsatz, Konversion, Interaktion, Akquise und Absprungrate zu überprüfen. Siehe [Erfolgsmetriken](../optimizer/manage-results/success-metrics.md) für Details.

## Überlegungen vor der Einführung

Überprüfen Sie, wie sich das CDM-Modell auf Ihre Lizenzierungs-, Katalog-Integrationen-, Storefront- und Admin-Workflows auswirkt, bevor Sie Merchandising-Services übernehmen.

### Katalogverwaltung und Integrationen

Produkte und Preise weiterhin in [!DNL Commerce Foundation] verwalten. Die native Integration synchronisiert sie mit dem CDM. Erstellen Sie keinen zweiten Produktkatalog für Merchandising-Services.

### Storefront-Implementierung

Wie Ihre Storefront Katalogdaten abruft, hängt von Ihrer Implementierung ab:

- **[!DNL Adobe Commerce Storefront]**-Dropins - Die Dropins handhaben die Transition. Code-Änderungen sind nicht erforderlich. Siehe die [Storefront-Setup-Dokumentation](https://experienceleague.adobe.com/en/tools/commerce-storefront/).
- **Benutzerdefinierte oder andere Storefronts** - Aktualisieren Sie die Kopfzeilen Ihrer Kataloganfragen, wie in der [Kopfzeilen-Konfigurationsreferenz](https://experienceleague.adobe.com/en/tools/commerce-storefront/setup/configuration/commerce-configuration/#headers) beschrieben.

Überprüfen Sie Ihre Katalogabfragen und Anfragekopfzeilen für das CDM-basierte Modell. Gehen Sie nicht davon aus, dass vorhandene Abfragen oder Kopfzeilen unverändert bleiben. Die Merchandising-GraphQL-Abfragen unterscheiden sich von den Abfragen, die im ursprünglichen Katalog-Service-Modell verwendet wurden. Zusätzliche Abfragen unterstützen CDM. Verwenden Sie die [Merchandising-GraphQL-API](https://developer.adobe.com/commerce/services/reference/graphql/)Referenz und überprüfen Sie den erforderlichen Katalogkontext mit der [Storefront-Kopfzeilenreferenz](https://experienceleague.adobe.com/en/tools/commerce-storefront/setup/configuration/commerce-configuration/#headers).

### Programme und Erweiterungen von Drittanbietern

Überprüfen Sie Apps und Erweiterungen von Drittanbietern, die Katalogdaten lesen oder Katalogereignisse mit ihrem Anbieter nutzen. Die Kompatibilität hängt davon ab, wie jede App oder Erweiterung diese Schnittstellen verwendet.

### Admin-Erfahrung

Adobe Commerce as a Cloud Service mit CCDM verwendet [[!DNL Adobe Unified Experience]](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin-unified-experience) (Unified Shell). Adobe hat Unified Shell getrennt von CCDM veröffentlicht. Vorhandene Instanzen im ursprünglichen Katalog-Service-Modell behalten den Zugriff auf Classic und Unified Shell.

### Beschränkungen

Das CCDM-Modell ändert keine Adobe Commerce as a Cloud Service-Beschränkungen. Die Freigabe einer Kataloggrundlage mit Optimizer bedeutet nicht, dass Commerce die Kapazität oder die Beschränkungen von Optimizer erbt.

## Verfügbarkeit und Migration

Organisationen, die nach dieser Version mit Adobe Commerce as a Cloud Service beginnen, erhalten standardmäßig Merchandising-Services. Wenn Ihr Unternehmen das ursprüngliche Katalogdatenmodell benötigt, wenden Sie sich an Ihr Adobe-Accountteam, um zu besprechen, ob eine Ausnahme verfügbar ist.

Organisationen, die Adobe Commerce as a Cloud Service vor dieser Version verwendet haben, können bei der Bereitstellung [&#x200B; neuen Instanz entweder das Katalogmodell &#x200B;](./getting-started.md#create-an-instance). Standardmäßig ist der [!UICONTROL Enable CCDM] deaktiviert. Sobald CDM aktiviert ist, können Sie es nicht mehr deaktivieren.

Vorhandene Instanzen ändern sich nicht automatisch. Bei allgemeiner Verfügbarkeit (General Availability, GA) können Sie keine vorhandene ursprüngliche Catalog-Services-Instanz zu Merchandising-Services migrieren.
