---
title: Produktvisualisierung mit AEM Assets
description: Erfahren Sie, wie Sie AEM Assets für Produktbilder in  [!DNL Adobe Commerce Optimizer].
feature: CMS, Media, Configuration, Integration
role: Admin, Developer
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: bf1d88ef7daec25872678bb27bce0bb7c97fd296
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---


# Produktvisualisierung mit AEM Assets

Mit Product Visuals können [!DNL Adobe Commerce Optimizer] Produktbilder über Adobe Experience Manager (AEM) Assets verwalten. Diese Integration bietet einen nahtlosen Workflow zum Synchronisieren von hochwertigen Produktbildern aus AEM Assets mit Ihrem [!DNL Commerce Optimizer] mithilfe von Katalogschichten.

## Die wichtigsten Vorteile

* **Zentralisiertes Asset** Management: Verwalten Sie alle Produkt-Images in AEM Assets, der Digital Asset Management-Lösung der Unternehmensklasse.
* **Automatische Synchronisierung**: Produktbilder werden automatisch synchronisiert, wenn Assets in AEM Assets genehmigt oder aktualisiert werden.
* **Bereitstellung von Dynamic Media**: Nutzen Sie Dynamic Media mit OpenAPI-Funktionen für eine optimierte Bildbereitstellung.
* **Katalogebenen**: Produktbilder werden als Katalogebene angewendet, sodass Sie AEM Assets-Bilder in Ihrem Basiskatalog überlagern können.

## Funktionsweise

Die Integration umfasst zwei Hauptflüsse:

* **Von AEM Assets**: Wenn ein Asset genehmigt, abgelehnt oder entfernt wird, fließt das Ereignis über die Adobe-Pipeline zum Assets Integration Service. Der Service ordnet Assets Produkten mithilfe einer `match-by-SKU` oder einer benutzerdefinierten Zuordnungsstrategie zu und sendet dann die `product-asset` Zuordnungen an die [!DNL Commerce Optimizer], wo sie als Produktebenen gespeichert werden.

* **Von ACO**: Wenn ein Produkt im [!DNL Commerce Optimizer] aktualisiert wird, fließt das Ereignis über die Adobe-Pipeline zum Assets Integration Service. Der Service synchronisiert alle übereinstimmenden Asset-Zuordnungen zurück mit ACO.

Die aktualisierten Bilder sind über Storefront-APIs (Katalog-Service, Live-Suche, Produktempfehlungen) verfügbar.

### Source- und Ebenenkonfiguration

Bilder von AEM Assets werden als Katalogschicht mit der folgenden Quellkonfiguration aufgenommen:

> Beispiel für eine Quellkonfiguration

```json
{
  "source": {
    "locale": "en-US",
    "layer": "AEM-Assets"
  }
}
```

Durch diese Konfiguration wird sichergestellt, dass AEM Assets-Bilder als Überlagerung auf Ihrem Basisproduktkatalog angewendet werden.

## Voraussetzungen

Stellen Sie vor der Aktivierung von Produktbildern sicher, dass Sie die [Voraussetzungen für Commerce Optimizer](../../aem-assets-integration/get-started/configure-aco.md#prerequisites) erfüllen.

## Setup

Um die Integration zu aktivieren[ erstellen Sie ein Support-Ticket ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) Ihren [!DNL Commerce Optimizer]- und AEM Assets-Details. Der Adobe-Support konfiguriert die Integration und registriert Ihren Mandanten beim Assets Integration Service.

Weitere [ finden Sie unter „Konfigurieren von AEM Assets ](../../aem-assets-integration/get-started/configure-aco.md) Commerce Optimizer&quot;.

### Konfigurieren von AEM Assets-Metadaten

Um den automatischen Produktabgleich zu aktivieren, konfigurieren Sie Ihre Assets in AEM Assets mit Commerce-Metadaten.

Unter [Konfigurieren von AEM Assets](../../aem-assets-integration/get-started/configure-aco.md#configure-aem-assets) finden Sie die erforderlichen Metadatenfelder und Schritte.

## Verwenden von Produktbildern

Nachdem die Integration konfiguriert ist, verwalten Sie Ihre Produktbilder über AEM Assets.

### Hinzufügen von Bildern zu Produkten

1. Laden Sie Bilder in Ihr AEM Assets-Repository hoch.

1. Fügen Sie dem Asset Commerce-Metadaten hinzu. Siehe [Anwenden von Metadaten auf Assets](../../aem-assets-integration/get-started/configure-aco.md#step-3-apply-metadata-to-assets).

1. Genehmigen Sie das Asset für die Bereitstellung. Das Asset muss sich im Status **Genehmigt** für die Synchronisierung mit dem Trigger befinden.

1. Das Bild wird automatisch mit [!DNL Commerce Optimizer] synchronisiert.

### Anwenden der AEM-Assets-Ebene

Um AEM Assets-Bilder auf Ihrer Storefront anzuzeigen[ weisen Sie die `AEM-Assets` Ihrer Katalogansicht zu](catalog-layer.md#assign-the-aem-assets-layer-to-a-catalog-view).

## Ähnliche Themen

* [Katalogebenen](catalog-layer.md)
* [Katalogansichten](catalog-view.md)
* [AEM Assets-Integrationshandbuch](../../aem-assets-integration/overview.md)
