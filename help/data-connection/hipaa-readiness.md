---
title: HIPAA-Bereitschaft für [!DNL Commerce] Services
description: Erfahren Sie, wie Sie mit der [!DNL Data Connection]-Erweiterung [!DNL Commerce] Daten für Experience Platform freigeben und die HIPAA-Konformität aufrechterhalten können.
role: Admin, Leader
feature: Security, Compliance
exl-id: 8851e6d2-c466-4d8e-bfa4-20d0ad6522b5
TQID: 'https://experienceleague.adobe.com/PxrtL1nHtJsRJuAehDVKRk0ZuJz0ta7i84j1K6An1QU'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
topic_v2:
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
    internal-label: Governance
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 1%
---
# HIPAA-Bereitschaft für [!DNL Commerce] Services

Mit der [!DNL Data Connection]-Erweiterung können Sie [!DNL Commerce] Backoffice-Ereignisdaten für Experience Platform freigeben und die HIPAA-Konformität aufrechterhalten.

>[!IMPORTANT]
>
>Da Storefront-Ereignisse Client-seitig generiert werden, liegt es in der Verantwortung des Händlers ([&#x200B; Storefront-Ereignisdaten zu senden](connect-data.md#data-collection) an Experience Platform.

In diesem Artikel erfahren Sie mehr über:

- Installation
- So stellen Sie sicher, dass an Experience Platform gesendete Daten HIPAA-fähig sind
- Datenverschlüsselung in [!DNL Commerce]

## Installation

Wenn Sie das Add-on für das Gesundheitswesen für Adobe [!DNL Commerce] erworben haben, haben Sie höchstwahrscheinlich bereits die [HIPAA-fähige Erweiterung](https://experienceleague.adobe.com/de/docs/commerce-admin/start/compliance/hipaa-ready-service/overview#installation) installiert. Um sicherzustellen, dass Ihre [!DNL Commerce] Back-Office-Ereignisdaten HIPAA-fähig sind, müssen Sie auch die [!DNL Data Connection]-Erweiterung mit der zusätzlichen **Data Services HIPAA**-Erweiterung installieren. Die **Data Services HIPAA**-Erweiterung stellt sicher, dass alle Back-Office-Daten, die Sie an Experience Platform senden, HIPAA-fähig sind. Erfahren Sie [wie Sie die Erweiterung installieren](install.md#install-the-data-services-hipaa-extension).

>[!IMPORTANT]
>
>Wenn Sie die **Data Services HIPAA**-Erweiterung installieren, werden Storefront-Ereignisdaten, die von Live Search und Product Recommendations verwendet werden, nicht mehr erfasst. Dies liegt daran, dass Storefront-Ereignisdaten Client-seitig generiert werden. Um Storefront-Ereignisdaten weiterhin zu erfassen und zu senden, aktivieren Sie die Ereigniserfassung für diese Services erneut. Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/config/general/general#data-services)Allgemeine Konfiguration“.

## So stellen Sie sicher, dass an Experience Platform gesendete Daten HIPAA-fähig sind

Alle Back-Office-Ereignisdaten, die die [!DNL Data Connection]-Erweiterung an Experience Platform sendet, werden in [!DNL Commerce] als vertraulich betrachtet. Es liegt jedoch in der Verantwortung des Händlers, Datennutzungskennzeichnungen auf sein [!DNL Commerce] in Experience Platform anzuwenden, um bestimmte Daten explizit als sensibel zu kennzeichnen. Wenn Sie Datennutzungskennzeichnungen direkt auf ein Schema anwenden, werden diese Kennzeichnungen auf alle vorhandenen und zukünftigen Datensätze übertragen, die auf diesem Schema basieren.

Eine Übersicht über Datennutzungskennzeichnungen und ihre Rolle im Data Governance-Framework finden Sie unter [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) in der Dokumentation zu Experience Platform.

### Anwenden von Datennutzungskennzeichnungen auf [!DNL Commerce]

Befolgen Sie die Schritte im Tutorial [Verwalten von Datennutzungskennzeichnungen für ein Schema](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/tutorials/labels), um zu erfahren, wie Sie Kennzeichnungen auf Ihr [!DNL Commerce]-Schema anwenden.

Im [Glossar der sensiblen Kennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/reference#sensitive) erfahren Sie mehr über die verfügbaren Kennzeichnungen, die Sie auf die Felder in Ihrem [!DNL Commerce] anwenden können. Beispielsweise kennzeichnet das Label `RHD` geschützte Gesundheitsinformationen (PHI) oder Patienteninformationen, die von Adobe vertraglich zum Hochladen zugelassen sind.

Wenn Ihre [!DNL Commerce] als sensibel gekennzeichnet sind, können Sie Richtlinien durchsetzen, um Datenoperationen zu verhindern, die Richtlinienverletzungen darstellen. Erfahren Sie mehr über [Richtliniendurchsetzung](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/enforcement/overview) in Experience Platform.

## Datenverschlüsselung in Commerce

Adobe [!DNL Commerce] verwendet eine Verschlüsselung auf Blockebene. Für die Speicherung verwendet [!DNL Commerce] Amazon Elastic Block Store (EBS). Alle EBS-Volumes werden mit dem AES-256-Algorithmus verschlüsselt, was bedeutet, dass die Daten im Ruhezustand verschlüsselt werden. [!DNL Commerce] Daten während der Übertragung werden über sichere, verschlüsselte Verbindungen mit HTTPS ([&#x200B; v1.2) &#x200B;](https://datatracker.ietf.org/doc/html/rfc5246).

>[!IMPORTANT]
>
>Commerce unterstützt keine Verschlüsselung oder Verschlüsselung auf Spalten- oder Zeilenebene, wenn sich die Daten nicht im Ruhezustand befinden oder nicht zwischen Servern übertragen werden.

### Datenverschlüsselung in Experience Platform

Wenn Händler ihre Daten an Experience Platform senden, werden diese Daten mit HTTPS TLS v1.2 gesendet. Erfahren Sie mehr darüber, wie [Experience Platform](https://experienceleague.adobe.com/de/docs/experience-platform/landing/governance-privacy-security/encryption) Daten verschlüsselt.

## Handhabung von Datenschutzanfragen durch [!DNL Commerce]

Erfahren Sie[!DNL Commerce] wie [Datenschutzanfragen verarbeitet](handle-privacy-request.md).
