---
title: Einrichten des Connectors für B2B-Commerce
description: Erfahren Sie, wie Sie den B2B-Connector installieren, Commerce-Bereiche auswählen, freigegebene Katalogdaten synchronisieren, Katalogansichten überprüfen und den Projektionsstatus überwachen.
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: e126554b-28f9-4290-b58c-10b888b88174
    internal-label: IMS integration
  - id: a40ebd6b-b542-4432-a730-1803ef74518d
    internal-label: Data Transfer
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
    internal-label: Data integration
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
last-update: 2026-10-01
source-git-commit: 9ed3a09bc4e26e2ef787909700f51e25de0a18fa
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%
---

# Einrichten des Connectors für B2B-Commerce

Händler, die [!DNL Adobe Commerce] freigegebene B2B-Kataloge verwenden, können die [!DNL Adobe Commerce Optimizer Connector for B2B] verwenden, um benutzerdefinierte freigegebene Katalogdaten und -konfigurationen mit [!DNL Adobe Commerce Optimizer] zu synchronisieren.

{{aco-integration-environment-alignment}}

## Voraussetzungen für die Verwendung der Integration {#requirements-to-use-the-integration}

* Adobe Commerce 2.4.8+ mit [installierter und aktivierter Commerce B2B-Version 1.5.3+](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/install).

* Lizenz mit bereitgestellter Sandbox-Instanz [!DNL Commerce Optimizer].

* [Authentifizierungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) zum Herunterladen des Connector-Metapakets mit Composer.

* Administratorzugriff auf eine [[!DNL Commerce Optimizer] Sandbox-Instanz](../optimizer/get-started.md).

Der [!DNL Adobe Commerce] Benutzer, der die Integration konfiguriert, muss über Folgendes verfügen:

* Administratorzugriff auf den Commerce Admin.

* [Befehlszeilenzugriff auf den  [!DNL Adobe Commerce] -Server](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access).

* Entwicklerzugriff auf die [IMS-Organisation](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations?), in der das [!DNL Commerce Optimizer] bereitgestellt wird.

### Anwendungsanforderungen

* Commerce Cron und Indexer funktionieren normal.
* Die erforderlichen Websites und Speicheransichten, die für den Export identifiziert wurden.
* Freigegebene Kataloge, Unternehmenszuweisungen, Sortimente und B2B-Preise, die in Adobe Commerce konfiguriert oder konfiguriert werden können.

>[!BEGINSHADEBOX]

## Konfliktende Erweiterungen entfernen {#remove-conflicting-extensions}

{{$include /help/_includes/aco-connector/remove-conflicting-extensions.md}}

>[!ENDSHADEBOX]

## Konfigurationsschritte {#configuration-steps}

Gehen Sie wie folgt vor, um die [!DNL Adobe Commerce Optimizer Connector for B2B] zu aktivieren und mit der Synchronisierung der benutzerdefinierten Konfiguration für einen freigegebenen Katalog von [!DNL Adobe Commerce] mit Ihrer [!DNL Commerce Optimizer] zu beginnen.

1. **[Installieren Sie das  [!DNL Adobe Commerce Optimizer Connector for B2B] -Paket](#install-the-adobe-commerce-optimizer-connector-for-B2B-package)** mithilfe von Composer, um Ihre [!DNL Adobe Commerce]-Instanz mit [!DNL Commerce Optimizer] zu verbinden.

1. **[Anpassen der Exportkonfiguration für Commerce-Bereiche](#data-export-and-scope-mapping)** vom Administrator.

1. **[Aktivieren Sie die  [!DNL Commerce Optimizer] -Integration](#enable-the-adobe-commerce-optimizer-integration)**.

1. **[Überprüfen Sie, ob die Datensynchronisation funktioniert](#verify-that-the-data-sync-is-working)**.

## Installieren des [!DNL Adobe Commerce Optimizer Connector for B2B] {#install-the-adobe-commerce-optimizer-connector-for-B2B-package}

Das [!DNL Adobe Commerce Optimizer Connector for B2B] wird als Composer-Metapaket bereitgestellt, das für alle Commerce-Händler mit einer aktiven Lizenz für [!DNL Commerce Optimizer] verfügbar ist.

### Installationsschritte

1. Fügen Sie das Modul `adobe-commerce/commerce-data-export-aco-adapter-b2b` mit dem Composer hinzu:

   ```shell
   composer require adobe-commerce/commerce-data-export-aco-adapter-b2b
   ```

1. Stellen Sie die Änderungen in Ihrer [!DNL Adobe Commerce] Staging-Umgebung bereit.

   Nach Abschluss der Bereitstellung ist die Option [!DNL Commerce Optimizer] im Commerce Admin-Menü verfügbar. Wählen Sie **[!UICONTROL Commerce Optimizer]** aus, um Ihre [!DNL Commerce Optimizer]-Instanz direkt über die Commerce-Admin zu öffnen.

{{install-extension-links}}

### Datenexport und Bereichszuordnung

Wählen Sie die zu synchronisierenden Websites und Store-Ansichten aus und überprüfen Sie dann die anfänglichen Feeds. Für B2B verwendet der Connector die aktivierten Bereiche, wenn er freigegebene Katalogdaten in [!DNL Commerce Optimizer] projiziert.

* **Store-Ansicht** → Katalogquelle mit lokalisierten Produktinhalten
* **Website und Kundengruppe** → Preisbuch für Website- und Kundengruppenpreise
* **Freigegebener Katalog** → geschützte Ansicht des privaten Katalogs und erzwungene Richtlinie

Der freigegebene Katalog definiert das Produktsortiment, und jede aktivierte Store-Ansicht liefert die lokalisierte Katalogquelle. Die Website und die Kundengruppe bestimmen das jeweilige Preisbuch. Der Connector projiziert jeden benutzerdefinierten freigegebenen Katalog für jede aktivierte Store-Ansicht, sodass Sie keine separate Bereichseinstellung für die B2B-Projektion benötigen.

Ein benutzerdefinierter freigegebener Katalog kann mehrere geschützte private Katalogansichten generieren, eine für jede aktivierte Store-Ansicht. Der standardmäßige öffentliche freigegebene Katalog wird nicht als private B2B-Katalogansicht dargestellt. Eine ausführliche Beschreibung der Objektzuordnung und des Laufzeitautorisierungsflusses finden Sie unter [B2B-Shared-Catalog-Projektion](b2b-shared-catalog-projection.md).

>[!IMPORTANT]
>
>Durch Ändern der Exporteinstellungen wird eine vollständige Neuindizierung Trigger. Dieser Vorgang kann je nach Kataloggröße längere Zeit in Anspruch nehmen. Konfigurieren Sie die Commerce-Bereiche, bevor Sie die Integration aktivieren und die anfängliche Datensynchronisierung starten.

### So ändern Sie die Exporteinstellungen für Bereiche

1. Wechseln Sie in Commerce Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**.

1. Wählen Sie die Website- oder Store-Ansicht aus, die Sie konfigurieren möchten.

1. Aktivieren Sie in den **[!DNL Commerce Optimizer]-** das Kontrollkästchen, um die Datensynchronisierung nach Bedarf zu aktivieren oder zu deaktivieren.

   ![Aktualisieren der Datensynchronisierungskonfiguration](./assets/aco-connector-b2b-storeview-list.png){width="500" zoomable="yes"}

1. Speichern Sie Ihre Änderungen.

### Aktivieren und Deaktivieren des Verhaltens

| Aktion | Ergebnis |
| -------- | -------- |
| Shop-Ansicht deaktivieren | **Durch Deaktivieren der Synchronisierung werden Katalogdaten aus Ihrer B2B-Storefront entfernt.** Die Katalogquelle bleibt in [!DNL Adobe Commerce Optimizer], aber alle synchronisierten Daten werden bei der nächsten Cron-Ausführung entfernt. |
| Deaktivieren und reaktivieren Sie eine Store-Ansicht | Dieselbe Katalogquelle wird erneut mit einer vollständigen Datensynchronisation aufgefüllt. |

### Änderungen des freigegebenen B2B-Katalogs überwachen

Der Connector überwacht Änderungen an freigegebenen Katalogen und Unternehmenszuweisungen. Wenn Sie einen freigegebenen Katalog im Commerce Admin-Bereich entfernen, entfernt der Connector nach einer konfigurierbaren Übergangsphase den Zugriff auf die private Katalogansicht.

>[!NOTE]
>
>Die Übergangsphase für die Löschung beträgt standardmäßig sieben Tage. Sie können dies ändern, indem Sie die Konfiguration der Synchronisierungseinstellungen der Katalogansicht aktualisieren. Siehe [Konfiguration der Katalogansicht mit Synchronisierungsstatus](catalog-view-sync-status.md#configure-aco-catalog-view-sync-settings).

## [!DNL Commerce Optimizer] aktivieren {#enable-the-adobe-commerce-optimizer-integration}

Sie aktivieren die Integration und initiieren die Datensynchronisation, indem Sie den `aco:config:init` CLI-Befehl ausführen. Dieser Befehl führt die folgenden Schritte aus:

1. Ruft ein IMS-Zugriffstoken mit den als Befehlszeilenargumente bereitgestellten Anmeldeinformationen ab.
1. Ruft den Commerce Cloud Manager-Service (CCM) unter `https://ccm.api.commerce.adobe.com/api/v1/tenants/{tenantId}/owner/{orgId}` auf, um den Mandanten zu validieren und die Aufnahme-URL und die [!DNL Commerce Optimizer] Studio-URL zu extrahieren.
1. Speichert alle Konfigurationen (Client-Geheimnis verschlüsselt) in `core_config_data`.
1. Plant die anfängliche vollständige Synchronisierung durch Invalidierung aller [!DNL Commerce Optimizer]-Indexer.

{{aco-data-sync-processing-note}}

## Erforderliche Verbindungsdetails abrufen

{{$include /help/_includes/aco-connector/connection-details.md}}

### [!DNL Commerce Optimizer]-Instanzdetails abrufen

{{$include /help/_includes/aco-connector/configure-connection.md}}

## Überprüfen, ob die Datensynchronisation funktioniert {#verify-that-the-data-sync-is-working}

{{$include /help/_includes/aco-connector/verify-optimizer-data-sync.md}}

## Nächste Schritte

1. **Überwachen der Projektion der B2B-Katalogansicht**

Verwenden Sie nach der ersten Feed[Synchronisierung mit &quot;](catalog-view-sync-status.md) der Katalogansicht“, um projizierte private Katalogansichten, Richtlinien, Preisbuchreferenzen und die Konfiguration des eingeschränkten Zugriffsschlüssels zu überprüfen. Informationen zum Projektionsmodell und zum Laufzeitautorisierungsfluss finden Sie unter [B2B-Shared-Catalog-Projektion](b2b-shared-catalog-projection.md).

1. **Einrichten einer Commerce-Storefront auf[!DNL Edge Delivery Services]**

   Um Ihre Storefront mit der [!DNL Commerce Optimizer]-Instanz zu verbinden und personalisierte Commerce-Erlebnisse bereitzustellen, folgen Sie der [Storefront-Setup-Dokumentation](https://experienceleague.adobe.com/en/tools/commerce-storefront/setup/){target="_blank"}.
