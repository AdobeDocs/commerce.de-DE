---
source-git-commit: 10a91a91337778648e99078bcbf0c9ef25a49f86
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---
# Commerce Snippets

## Installationshinweis für die Erweiterung „Status der Daten-Feed-Synchronisierung“ {#install-data-sync-feed-status}

>[!NOTE]
>
>Wenn die Seite Synchronisierungsstatus für Daten-Feeds nicht in der Commerce Admin für Commerce in Cloud- oder lokalen Bereitstellungen verfügbar ist, befolgen Sie die [Installationsanweisungen für Erweiterungen](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status#install-the-extension){target="_blank"}, um sie zu aktivieren.


## Ausrichtung der Adobe Commerce Optimizer-Integrationsumgebung {#aco-integration-environment-alignment}

>[!IMPORTANT]
>
>Verbinden Sie Sandbox Optimizer-Instanzen immer mit Nicht-Produktionsumgebungen und Produktionsinstanzen mit Produktionsumgebungen. Nicht übereinstimmende Umgebungen führen zu inkonsistenten Katalogdaten, Suchergebnissen und Empfehlungen.


## Merchandising-Services für Optimizer {#aco-merchandising-services}

>[!NOTE]
>
>Verwenden Sie für Commerce-Lösungen, die Adobe Commerce Optimizer oder den Adobe Commerce Optimizer-Connector verwenden, die [Merchandising Services-GraphQL-API](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/using-the-api/) anstelle der Catalog Service-GraphQL-API.

## Datensynchronisierungsprüfung für Optimizer {#aco-data-sync-verification}

>[!NOTE]
>
>Bei Bereitstellungen, die den [[!DNL Adobe Commerce Optimizer Connector]](../aco-connector/overview.md) zum Exportieren von Katalogdaten nach [!DNL Adobe Commerce Optimizer] verwenden, überprüfen Sie die Synchronisierung von Katalogdaten auf der [Seite „Status der Daten-Feed-](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status)&quot; in der Commerce Admin- und [Datensynchronisierungsseite](../optimizer/setup/data-sync.md) in [!DNL Adobe Commerce Optimizer Studio], nicht im [Daten-Management-Dashboard](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard).

## Adobe Commerce Optimizer-Dropdown-Hinweis für API-Aktualisierungen {#aco-api-updates-and-dropins}

>[!NOTE]
>
>[Dropdown-Komponenten](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/?lang=de) für [!DNL Commerce Storefront on Edge Delivery Services], die die neuesten GraphQL-Änderungen automatisch übernehmen (neue Felder, Einschränkungen und Abfrageverhalten).

## Frühzeitiger Zugriff auf ACCS {#accs-early-access}

>[!NOTE]
>
>In dieser Dokumentation wird ein Produkt beschrieben, das sich in der Entwicklung für den frühzeitigen Zugriff befindet und nicht alle für die allgemeine Verfügbarkeit vorgesehenen Funktionen enthält.

<!--
## Nav hack ACCS {#nav-hack-accs}

>[!BEGINSHADEBOX]

<table style="table-layout:fixed">
  <tr>
    <td style="vertical-align: middle;"><a href="https://developer.adobe.com/commerce/webapi/"><img alt="Developers" src="../assets/icons/developers.svg" /> <strong>Developers</strong></a></td>
    <td style="vertical-align: middle;"><a href="https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de"><img alt="Storefront" src="../assets/icons/storefront.svg" /> <strong>Storefront</strong></a></td>
    <td style="vertical-align: middle;"><a href="../cloud-service/overview.md"><img alt="Merchants" src="../assets/icons/merchants.svg" /> <strong>Merchants</strong></a></td>
    <td style="vertical-align: middle;"><a href="https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/getting-started/commerce-as-a-cloud-service/overview"><img alt="Videos" src="../assets/icons/videos.svg" /> <strong>Videos</strong></a></td>
    <td style="vertical-align: middle;"><a href="https://experienceleague.adobe.com/developer/commerce/storefront/playgrounds/commerce-services/?lang=de"><img alt="Playgrounds" src="../assets/icons/playgrounds.svg" /> <strong>Playgrounds</strong></a></td>
  </tr>
</table>

>[!ENDSHADEBOX]
-->

## Experimentelle Funktion „Nur ACS-Sandbox“ {#accs-sandbox-experimental}

>[!IMPORTANT]
>
>Diese Funktion ist experimentell und nur in Sandbox-Umgebungen von [!DNL Adobe Commerce as a Cloud Service] verfügbar.
>
>Diese Funktion kann ohne Vorankündigung geändert werden.

[!BADGE Sandbox]{type=Caution tooltip="Die aufgelisteten Elemente sind derzeit nur in Sandbox-Umgebungen verfügbar. Adobe stellt neue Versionen zunächst in Sandbox-Umgebungen zur Verfügung, um Zeit zum Testen bevorstehender Änderungen zu haben, bevor die Version in Produktionsumgebungen verfügbar ist."}

## AEM Assets-Instanzzuordnung {#aem-assets-instance-mapping}

>[!NOTE]
>
>Beim Verbinden von [!DNL Adobe Commerce as a Cloud Service] mit [!DNL AEM Assets] wird Ihre [!DNL AEM Assets]-Staging-Instanz Ihrer Sandbox-[!DNL Adobe Commerce as a Cloud Service]-Instanz und allen anderen Nicht-Produktionsumgebungen zugeordnet. Ihre [!DNL AEM Assets] Produktionsinstanz wird Ihrer [!DNL Adobe Commerce as a Cloud Service] Produktionsinstanz zugeordnet.

## IMS-Identität und Single-Sign-on-Informationen {#ims-identity-and-sso-config}

Die Identitätsverwaltung und -authentifizierung von Adobe Commerce wird über Adobe Admin Console vom Adobe Identity Management System (IMS) verwaltet.

Informationen zu den Konfigurationsoptionen für Identitäten, einschließlich Adobe ID, Enterprise ID und Federated ID, und Anweisungen zum Konfigurieren von Single Sign-On (SSO) für einen sicheren Zugriff auf Adobe-Apps finden Sie unter [Einrichten von Identitäten und Single Sign-On](https://helpx.adobe.com/de/enterprise/using/set-up-identity.html) in der Dokumentation *Enterprise Admin Console*.

## ACS Services und Erweiterbarkeit - Versionshinweise {#accs-release}

### Zusätzliche Versionshinweise

[!DNL Adobe Commerce as a Cloud Service] enthält die neuesten Versionen von Merchandising-Services, Zahlungsdiensten und Erweiterbarkeitsversionen. Verwenden Sie die folgenden Links, um die jeweiligen Versionshinweise anzuzeigen:

| Dienste | Erweiterbarkeit | Schaufenster |
| --- | --- | --- |
| <ul><li>[Katalog-Service](../catalog-service/release-notes.md)</li><li>[Live-Suche](../live-search/release-notes.md)</li><li>[Zahlungsdienste](../payment-services/release-notes.md)</li><li>[Produktempfehlungen](../product-recommendations/release-notes.md)</li><li>[SaaS-Datenexport](../data-export/release-notes.md)</li></ul> | <ul><li>[Admin-Benutzeroberfläche - SDK](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/release-notes/)</li><li>[API-Mesh](https://developer.adobe.com/graphql-mesh-gateway/mesh/release)</li><li>[Ereignisse](https://developer.adobe.com/commerce/extensibility/events/release-notes/)</li><li>[Webhooks](https://developer.adobe.com/commerce/extensibility/webhooks/release-notes/)</li></ul> | <ul><li>[Versionsinformationen](https://experienceleague.adobe.com/developer/commerce/storefront/releases/?lang=de)</li><li>[Changelog](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/?lang=de)</li></ul> |

## Versionshinweise zu Adobe Commerce Optimizer Services {#aco-release}

### Zusätzliche Versionshinweise

[!DNL Adobe Commerce Optimizer] funktioniert mit den neuesten Versionen der AEM Assets-Integration, dem Commerce Optimizer-Connector und [!DNL Adobe Commerce Storefront]. Über die folgenden Links können Sie Versionshinweise für jeden Bereich anzeigen:

| Dienste | Schaufenster |
| --- | --- |
| [AEM Assets-Integration](../aem-assets-integration/release-notes.md)<br>[Commerce Optimizer-Connector](../aco-connector/release-notes.md) | [Storefront-Versionsinformationen](https://experienceleague.adobe.com/developer/commerce/storefront/releases/?lang=de)<br>[Storefront-Änderungsprotokoll](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/?lang=de) |
