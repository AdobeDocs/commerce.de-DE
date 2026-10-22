---
title: AEM Assets-Integration für Commerce
description: Erfahren Sie, wie Sie AEM Assets mit Adobe Commerce, Adobe Commerce as a Cloud Service und Adobe Commerce Optimizer integrieren können, um Produktbilder und Medien zentral zu verwalten.
role: Admin, Developer, Leader
feature: Storefront, Integration
recommendations: noCatalog
autotag-review: '2026-10-20T01:34:13.564Z'
TQID: 'https://experienceleague.adobe.com/v15DE37DoqpstrsWqnwd6DYpa5moT-BhQ80zDq2KP6I'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: ef0c45ae-6bee-4821-a65e-e1e118e8a01c
    internal-label: Commerce Optimizer
feature_v2:
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
source-git-commit: ca6bb3543583c865c42b8f4d84f01e27a04f9223
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 4%
---

# AEM Assets-Integration für Commerce

Die AEM Assets-Integration ermöglicht Produktvisualisierungsfunktionen in Adobe Commerce, sodass Sie Produktbilder, Videos und andere Medien zentral in AEM Assets verwalten können. Es handelt sich dabei um ein optionales Add-on, das mit jeder Commerce-Architekturoption verwendet werden kann, nicht um eine separate Commerce-Plattform.

## Integrationspfade nach Architektur

Es gibt zwei Integrationspfade. Der Pfad hängt von Ihrer Commerce-Architektur ab.

| Commerce-Architektur | AEM Assets-Integrationspfad | Weitere Informationen |
| --- | --- | --- |
| [!DNL Adobe Commerce] in der Cloud oder vor Ort | [!DNL AEM Assets] Integration für Commerce. Verwendet das Commerce-Integrationspaket zum Synchronisieren und Verwalten von Produktbildern, Videos und anderen Medien zwischen [!DNL Adobe Commerce] und [!DNL AEM Assets]. | [AEM Assets-Integration für Commerce](/help/aem-assets-integration/overview.md) |
| [!DNL Adobe Commerce as a Cloud Service] | [!DNL Product Visuals] mit [!DNL AEM Assets] | Setup für die [AEM Assets-Integration](/help/aem-assets-integration/overview.md#next-steps) |
| Eigenständige [!DNL Adobe Commerce Optimizer] | [!DNL Product Visuals] mit [!DNL AEM Assets]. Basiskatalog- und Preisdaten werden über die [Optimizer-Datenaufnahme-API](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/) geliefert. | [Produktvisualisierung mit AEM Assets](/help/optimizer/setup/product-visuals.md) |
| [!DNL Adobe Commerce] mit dem [!DNL Adobe Commerce Optimizer Connector] | [!DNL Product Visuals] mit [!DNL AEM Assets]. Katalog- und Preisdaten werden vom Connector aus [!DNL Adobe Commerce]. | [Commerce Optimizer-Integrationen](/help/optimizer/integrations/integrations-overview.md) |

[!DNL Product Visuals] ist der Integrationspfad für Adobe Commerce as a Cloud Service und Adobe Commerce Optimizer. Es synchronisiert von AEM verwaltete Produktbilder mit der Commerce-Katalogschicht und stellt sie über Storefront-APIs für Storefront-Erlebnisse bereit.

## Vor der Auswahl

- Die Anforderungen für Setup und Lizenzierung unterscheiden sich zwischen dem Commerce On-Cloud- oder On-Premise-Pfad und dem Commerce as a Cloud Service- oder Adobe Optimizer-[!DNL Product Visuals]. Überprüfen Sie zunächst die bereitstellungsspezifischen Anforderungen.
- [!DNL AEM Assets] verwaltet digitale Assets. Es ersetzt nicht den Commerce-Katalog, die Preisgestaltung, den Warenkorb, den Checkout oder das Bestellsystem.
- Produkt-Assets werden mithilfe der SKU oder anderer dokumentierter übereinstimmender Metadaten mit Commerce-Produkten abgeglichen.
- Wenn Marketing- und Merchandising-Teams zentralisierte Produktbilder und Asset-Workflows benötigen, wählen Sie den Pfad aus, der Ihrer Commerce-Architektur entspricht.

## Verwandte Informationen

- [Dokumentation zu Adobe Experience Manager Assets](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/overview)
- [Überblick über die Architektur](../architecture-options/overview.md)
- [APIs](../apis/commerce-apis.md)
