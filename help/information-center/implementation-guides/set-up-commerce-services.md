---
title: Einrichten von Commerce Services
description: Erfahren Sie, wie Sie Adobe Commerce mithilfe des Commerce Services-Connectors mit Merchandising-Services und Magento Open Source mit Payment Services verbinden.
role: Admin, Developer
feature: Integration, Configuration
recommendations: noCatalog
autotag-review: '2026-10-20T11:14:04.410Z'
TQID: 'https://experienceleague.adobe.com/yyUDw1y5CYHxdLlC3bNo0DKK0byamPAKUjK-wwxVEX4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 4273989f-0bf2-5361-a17a-6909488d18ab
    internal-label: Catalog Service
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: dec06508-d41f-555a-87e8-29e8bcdfa95a
    internal-label: Recommendations
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
source-git-commit: ca6bb3543583c865c42b8f4d84f01e27a04f9223
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%
---

# Einrichten von Commerce-Services

Adobe Commerce in Cloud-Infrastrukturen und lokale Projekte stellen über den Commerce Services Connector eine Verbindung zu Services wie [!DNL Catalog Service], [!DNL Live Search], [!DNL Product Recommendations] und [!DNL Payment Services] her. Bei [!DNL Adobe Commerce as a Cloud Service] wird diese Verbindung automatisch konfiguriert.

Magento Open Source verwendet den Commerce Services Connector für [!DNL Payment Services]. [!DNL Catalog Service], [!DNL Live Search] und [!DNL Product Recommendations] erfordern Adobe Commerce und sind für Magento Open Source nicht verfügbar.

>[!NOTE]
>
>Adobe Commerce Optimizer bietet native Katalog- und Merchandising-Funktionen, anstatt die separaten [!DNL Live Search]-, [!DNL Catalog Service]- und [!DNL Product Recommendations]-Services zu verwenden. Die Katalogsynchronisierung erfordert keinen Commerce Services-Connector. Für andere Integrationen auf dem Commerce-Backend, z. B. [!DNL Payment Services] und [!DNL Data Connection], ist weiterhin der Connector erforderlich. Siehe [Aktivieren von Adobe Commerce Optimizer](enable-aco.md) für das Optimizer-Setup.


## Erste Schritte

1. Lesen Sie die Dokumentation zum [Commerce Services-Connector](/help/landing/saas.md), um Ihre API-Schlüssel abzurufen und zu konfigurieren.

1. In den [Adobe Commerce Services-Handbüchern](/help/landing/home.md) finden Sie die einzelnen Services, die über den Connector verfügbar sind.

## Ergänzende Leitlinien

- [Konfigurieren von Zahlungen](configure-payments.md)
- [AEM Assets verbinden](connect-aem-assets.md)
- [Integration mit Adobe Experience Platform](integrate-aep.md)
