---
title: Übersicht über [!DNL Adobe Commerce as a Cloud Service]
description: Erfahren Sie mehr über die wichtigsten Funktionen und Vorteile von [!DNL Adobe Commerce as a Cloud Service].
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Developer, User, Leader
exl-id: 1b7e2731-4a10-4c2b-9bfc-8945729ed523
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: d46526db56dad08a8f865664c92d1214bbf063d8
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---


# Übersicht über [!DNL Adobe Commerce as a Cloud Service]

[!DNL Adobe Commerce as a Cloud Service] bietet Flexibilität, Skalierbarkeit und Effizienz, da Unternehmen digitale Abläufe bereitstellen und schnell skalieren und Innovationen beschleunigen können. Die Cloud-native Infrastruktur von Adobe passt Ressourcen automatisch an Spitzenanforderungen an Traffic, Bestellungen und Katalogmanagement an.

In der folgenden Tabelle sind die Produkte aufgeführt, die [!DNL Adobe Commerce as a Cloud Service] unterstützen:

<table style="table-layout:auto">
  <tr>
    <td align="left">
      <img src="../assets/icon-checkmark-circle-outline.svg" alt="checkmark" align="center"> <strong>Commerce-Storefront</strong>
    </td>
    <td align="left">
      Kundenorientierte Benutzeroberfläche, über die Käufer Produkte suchen und kaufen
    </td>
  </tr>
  <tr>
    <td align="left">
      <img src="../assets/icon-checkmark-circle-outline.svg" alt="checkmark" align="center"> <strong>Merchandising-Services</strong>
    </td>
    <td align="left">
      Backend-Services zur Verwaltung von Produktkatalogen, Preisen und Beständen
    </td>
  </tr>
  <tr>
    <td align="left">
      <img src="../assets/icon-checkmark-circle-outline.svg" alt="checkmark" align="center"> <strong>Produktvisualisierung</strong>
    </td>
    <td align="left">
      Digital Asset Management für Produktbilder und Medien
    </td>
  </tr>
  <tr>
    <td align="left">
      <img src="../assets/icon-checkmark-circle-outline.svg" alt="checkmark" align="center"> <strong>Entwicklerplattform</strong>
    </td>
    <td align="left">
      Zentrale Entwicklungstools und APIs zum Erstellen benutzerdefinierter Funktionen
    </td>
  </tr>
</table>

## Architektur

Im folgenden Video finden Sie eine kurze Einführung in die [!DNL Adobe Commerce as a Cloud Service]. Diagramme, die die Architektur veranschaulichen, werden unter dem Video bereitgestellt.

>[!VIDEO](https://video.tv.adobe.com/v/3443232?learn=on)

Dieses Diagramm zeigt den Datenfluss zwischen [!DNL Adobe Commerce as a Cloud Service] und allen Adobe Experience Cloud-Lösungen.

![[!DNL Adobe Commerce as a Cloud Service] Architekturdiagramm](./assets/data-flow.svg){zoomable="yes"}

## Commerce-Storefront

Verwenden Sie die [Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront?lang=de) von Adobe, die von Edge Delivery Services unterstützt wird, um in Minutenschnelle umfassende Erlebnisse mit einfacher dokumentbasierter Bearbeitung oder visueller Bearbeitung mit Storefront Builder zu erstellen.

Die Commerce-Storefront ist vollständig Headless mit einer entkoppelten Architektur, die alle Merchandising-Services und -Daten über eine GraphQL-API-Ebene bereitstellt. Diese Architektur ermöglicht es Teams, ihre Frontends unabhängig von der Commerce Foundation zu entwickeln, und bietet die Agilität, neue Touchpoints mit neuen Technologien zu erstellen und zu testen.

>[!NOTE]
>
>[!DNL Adobe Commerce as a Cloud Service] unterstützt keine Luma-Storefronts. Wenn Sie von Adobe Commerce in der Cloud oder lokal migrieren, finden Sie unter [Vorhandene Storefronts](https://experienceleague.adobe.com/developer/commerce/storefront/discovery/?lang=de#existing-storefronts) Anleitungen zum Übergang.

## Merchandising- und Zahlungsdienste

Adobe bietet eine breite Palette intelligenter, zusammenstellbarer Merchandising-Services, mit denen Sie Ihre wichtigsten Geschäftsziele unterstützen können. Diese Services bieten auch APIs, die für die skalierte Leistungsoptimierung von entscheidender Bedeutung sind.

- [Live-Suche](../live-search/overview.md) - Mit diesem KI-gestützten Suchwerkzeug können Sie Käufern intelligentere, schnellere und relevante Ergebnisse liefern.
- [Produktempfehlungen](../optimizer/merchandising/recommendations/overview.md) - Fügen Sie KI-gestützte Empfehlungen hinzu, die auf dem Kundenverhalten, beliebten Trends, Produktähnlichkeiten und mehr basieren.
- [Catalog Service](../catalog-service/guide-overview.md): Bieten Sie Ihren Kunden ein optimiertes Produkterlebnis und steigern Sie gleichzeitig die Leistung, die Skalierbarkeit und die Konversionen.
- [Payment Services](../payment-services/guide-overview.md) - Steigern Sie die Kundenzufriedenheit, indem Sie verschiedene Zahlungsmethoden anbieten, einschließlich zinsfreier Zahlungsraten und einer einzigen Ansicht der Zahlungsabwicklung, Bestellungen und Rechnungen.

## Produktvisualisierungen mit AEM Assets

Product Visuals vereinfacht das Asset-Management mithilfe eines Digital-Asset-Management-Systems (DAM), das zum Verwalten von Rich-Media-Inhalten mit Adobe Experience Manager integriert werden kann.

Die Integration stellt sicher, dass digitale Assets, wie Produktbilder oder Marketing-Inhalte, basierend auf der SKU oder anderen Schlüsselattributen dynamisch mit den entsprechenden Merchandising-Entitäten verknüpft werden, einschließlich Produkten und Kategorien in Adobe Commerce.

Product Visuals ist im Lieferumfang von [!DNL Adobe Commerce as a Cloud Service] enthalten und bietet einige der Funktionen von AEM Assets.

Alternativ bieten die nativen Funktionen in [!DNL Adobe Commerce as a Cloud Service] grundlegende Asset-Management-Tools zum Speichern und Verwalten digitaler Assets.

Lesen Sie das Handbuch zur Integration von [AEM Assets](../aem-assets-integration/overview.md) um mehr darüber zu erfahren, wie Sie Produktvisualisierungen mit AEM Assets in [!DNL Adobe Commerce as a Cloud Service] integrieren.

### Produktvisualisierungen für AEM Assets

Der folgende Vergleich hilft Ihnen bei der Auswahl der besten Option für Ihre Inhalte, die supply chain benötigt:

<table>
  <tr>
    <td align="left">
      <strong>Produktvisualisierungen mit AEM Assets</strong>
      <ul>
        <li>Integrierter, automatisierter Digital Asset Manager (DAM) für Produktbilder und Videos</li>
        <li>Ändern der Größe, Zuschneiden und Konvertieren von Bildern</li>
        <li>Schnelle Bild- und Videobereitstellung</li>
        <li>Optimierung von Bildformaten, -größen und -qualität auf der Grundlage der Client-Browser-Funktionen</li>
        <li>Zugriff auf Adobe Express und Adobe Firefly</li>
        <li>Nutzungsbeschränkungen für die Kapazität der Bild-/Videobereitstellung und den Benutzerzugriff</li>
        <li>Integrierter Asset-Wähler</li>
      </ul>
    </td>
    <td align="center">
      <br><br><br><br><br><br><br><br><br><br><br>
      <img src="../assets/icon-double-chevron-right.svg" alt="Chevron" width="100">
    </td>
    <td align="left">
      <strong>AEM Assets</strong>
      <ul>
        <li>Alle Funktionen von Product Visuals</li>
        <li>Full Marketing Digital Asset Manager (DAM)</li>
        <li>Unbegrenzte Anzahl von Benutzern (Zahlung pro Benutzer)</li>
        <li>Unbegrenzte Bild- und Videobereitstellung</li>
        <li>Erweiterte Asset-Management-Funktionen:</li>
        <ul>
          <li>360-Grad-Rotationssets und interaktive Viewer</li>
          <li>3D-Modellunterstützung und immersive Inhalte</li>
          <li>PDF-Support</li>
          <li>KI-gestütztes smartes Zuschneiden</li>
          <li>Dynamische Bildvorlagen</li>
          <li>Smart-Tagging</li>
          <li>Tracking und Analysen der Asset-Leistung</li>
        </ul>
      </ul>
    </td>
  </tr>
    <tr>
    <td align="center" colspan="3">
      Die Integration von <strong>Adobe ist für eine einfache Migration zwischen Angeboten verfügbar.</strong>
    </td>
  </tr>
</table>

## Entwicklerplattform

Adobe bietet Entwicklern umfassende Erweiterungspunkte und Tools, um Programme zu erstellen, die die Commerce Foundation-Funktionen erweitern und mit Drittanbietersystemen (wie CRMs, ERPS und PIMS) integrieren. Diese Tools senken Ihre Gesamtbetriebskosten der Plattform wie folgt:

- **Skalierbarkeit** - Anwendungen können getrennt von der Kernsoftware skaliert werden, was eine höhere Effizienz und vereinfachte Upgrades ermöglicht.
- **Isolation**-Eine isolierte Umgebung bedeutet, dass Entwickler ihre Erweiterungen nach eigenem Ermessen aktualisieren oder ändern können, ohne sich auf eine Hauptversion zu verlassen.
- **Technologische Unabhängigkeit**-Entwickler können wählen, welche Technologie-Stacks und Programmiersprachen ihren Bedürfnissen entsprechen.

>[!TIP]
>
>Von Anbietern erstellte Apps sind auch für die Installation auf [Adobe Exchange verfügbar](https://exchange.adobe.com/).

Adobe bietet die folgenden Entwickler-Tools zum Erstellen von Integrationen und Anpassungen:

- [**API Mesh für Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/) - Koordinieren und kombinieren Sie mehrere API-, GraphQL-, REST- und andere Quellen zu einem einzigen, abfragbaren GraphQL-Endpunkt.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/): Erstellen und implementieren Sie sichere und skalierbare Web-Anwendungen, die die Commerce-Funktionalität erweitern und mit Lösungen von Drittanbietern integrieren.
- [**Ereignisse**](https://developer.adobe.com/commerce/extensibility/events/) - Verwenden Sie benutzerdefinierte Ereignis-Trigger, um mit anderen erweiterbaren Entwicklungs-Tools zu interagieren.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) - Verwenden Sie Webhooks, um Trigger zwischen Commerce und Drittanbietersystemen automatisch zu erstellen.
- [**Admin-Benutzeroberfläche SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) - Passen Sie den Commerce-Admin an und erweitern Sie ihn mit neuen Seiten und Funktionen für Ihre Händler.
- [**Integration Starter Kit**](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/) - Beschleunigen Sie Ihre Backoffice-Integrationen mit Referenzintegrationen, Onboarding-Skripten und einer standardisierten Architektur.

## Commerce Foundation

Commerce Foundation bietet eine sichere automatisierte Hosting-Plattform und Self-Service-Funktionen für die Verwaltung Ihrer Commerce-Anwendung in einer Cloud-nativen Umgebung.

Zu den wichtigsten Funktionen gehören:

- Vereinfachtes Onboarding
- Nahtlose Upgrades
- Integrationen von Drittanbietern

### Vereinfachtes Onboarding

Starten Sie Sandbox- und Produktionsinstanzen in Minutenschnelle mit dem [!UICONTROL Commerce Cloud Manager] Self-Service-Bereitstellungsportal. Alles, was Sie benötigen, einschließlich Merchandising Services, einer Headless-Commerce-Instanz und App Builder, wird automatisch konfiguriert und in Ihre Instanzen integriert.

Unter [Erste Schritte](getting-started.md) erfahren Sie, wie Sie Commerce-Instanzen erstellen und verwalten.

### Nahtlose Upgrades

Zugriff auf die neuesten Funktionen und Verbesserungen ohne manuelle Upgrades. Durch die kontinuierliche Bereitstellung neuer Funktionen und Updates ist kein manuelles Patchen mehr erforderlich, sodass Sie stets auf die neuesten Funktionen mit niedrigen Gesamtbetriebskosten zugreifen können.

Der typische Upgrade-Prozess für Adobe Commerce in Cloud umfasste das Erstellen von Backups, das Klonen von Instanzen, das Ausführen von Kompatibilitäts-Tools und das Beheben von Code-Konflikten. Das ist bei [!DNL Adobe Commerce as a Cloud Service] nicht mehr nötig. Adobe sendet Ihnen In-App-Benachrichtigungen, wenn neue Funktionen und Sicherheitsaktualisierungen veröffentlicht wurden. Sie haben einen Zeitraum von 30 Tagen, um die neuen Funktionen in Ihren Sandbox-Instanzen zu bewerten, bevor die Aktualisierungen automatisch auf Ihre Produktionsumgebungen angewendet werden.

>[!NOTE]
>
>Adobe garantiert Abwärtskompatibilität für alle Updates. Das bedeutet, dass Aktualisierungen, die angewendet werden, nicht die vorhandenen Funktionen oder Anpassungen beeinträchtigen, die dem Modell der &quot;[-First-Erweiterbarkeit](https://developer.adobe.com/commerce/extensibility/) entsprechen.

### Integrationen von Drittanbietern

Entwickler können umfassende [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)- und [REST-APIs](https://developer.adobe.com/commerce/webapi/rest/) verwenden, um Commerce Foundation mit Drittanbietersystemen zu integrieren und Commerce-Funktionen zu erweitern.

<!-- ## Experience Cloud integration

[!DNL Adobe Commerce as a Cloud Service] integrates with all Experience Cloud solutions to deliver [personalized commerce experiences at scale](https://experienceleague.adobe.com/de/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Data Connection](../data-connection/overview.md) unlocks insights about your shoppers' buying behavior so that you can create personalized shopping experiences across all channels with other Adobe Digital Experience products. -->

## Vorteile

In den folgenden Abschnitten finden Sie Informationen zu den Vorteilen, die [!DNL Adobe Commerce as a Cloud Service] Unternehmen und IT-Führungskräften bietet.

### Unternehmensführer

- **Umsatz steigern**: Steigern Sie den organischen Traffic mit einer leistungsstarken Storefront, die SEO steigert. Erstellen Sie personalisierte Erlebnisse, die mit umfangreichen Daten die Konversionsrate steigern.
- **Skalierungsvorgänge**: Automatische Skalierungsdienste erfüllen die Spitzenanforderungen Ihres Unternehmens mit einer Verfügbarkeit von 99,9 %. Rollout mehrerer Marken und Regionen und Unterstützung für B2B und B2C von einer einzigen Instanz aus. Unterstützung großer und komplexer Produktkataloge mit flexibler Datenmodellierung.
- **Merchandiser-Produktivität steigern**: Verwenden Sie KI-gestützte Merchandising-Services, um die Konversion zu verbessern. Experimentieren Sie nativ, direkt in der Storefront. Verwalten Sie das Storefront-Erlebnis, um in Minutenschnelle umfassende Erlebnisse mit einfacher dokumentbasierter Bearbeitung oder einem visuellen Editor zu erstellen.
- **Niedrigere Gesamtbetriebskosten (TCO) und schnellere Innovation**: Immer aktuelle Services bieten Ihnen sofort Zugriff auf neue Funktionen. Aktivieren Sie neue Funktionen, indem Sie Apps einfach vom Markt installieren. Freisetzung von Ressourcen aus langwierigen Wartungsarbeiten, um sich auf den Aufbau neuer Funktionen zu konzentrieren.

### Führende Unternehmen im Bereich Informationstechnologie

- **Schnelle Bereitstellung**: Starten Sie schnell mit der Self-Service-Bereitstellung in Minuten. Alle Services sind für eine nahtlose Zusammenarbeit vorkonfiguriert, um schneller loszulegen. Stellen Sie bei Bedarf Sandboxes für Entwicklerexperimente bereit.
- **Niedrige Betriebskosten**: Keine weiteren Upgrades mit stets aktuellen Services. Bleiben Sie sicher und konform mit den neuesten automatisch für Sie angewendeten Sicherheits-Patches. Automatische Skalierung für anspruchsvollste Arbeitslasten.
- **Hochleistungs-Storefront**: Erstellen Sie innerhalb von Minuten umfangreiche Erlebnisse mit einfacher dokumentbasierter Bearbeitung oder einem visuellen Editor. Verwenden Sie KI-gestützte Merchandising-Services, um die Konvertierung zu verbessern. Native Experimente in der Storefront integriert.
- **Schnellere Innovation**: Freisetzen Sie Ressourcen von mühsamen Wartungsarbeiten und konzentrieren Sie sich auf den Aufbau neuer Funktionen, die geschäftlichen Nutzen bieten. Verwenden Sie umfassende Erweiterbarkeit und standardbasierte Technologien (JavaScript, HTML, CSS und Low-Code-Tools), um differenzierte Erlebnisse zu erstellen. Installieren Sie Apps von Drittanbietern mit einem Klick, um Ihrer Commerce-Plattform neue Funktionen hinzuzufügen.
