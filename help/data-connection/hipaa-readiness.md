---
title: HIPAA-Bereitschaft für  [!DNL Commerce]  Services
description: Erfahren Sie, wie Sie die  [!DNL Data Connection] -Erweiterung verwenden können, um Daten  [!DNL Commerce]  Experience Platform freizugeben und die HIPAA-Konformität aufrechtzuerhalten.
role: Admin, Leader
feature: Security, Compliance
exl-id: 8851e6d2-c466-4d8e-bfa4-20d0ad6522b5
source-git-commit: 290e3310bd7940c4ccd11317d273b75cc974223b
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

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

Wenn Sie das Add-on für das Gesundheitswesen für Adobe [!DNL Commerce] erworben haben, haben Sie höchstwahrscheinlich bereits die [HIPAA-fähige Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview#installation) installiert. Um sicherzustellen, dass Ihre [!DNL Commerce] Back-Office-Ereignisdaten HIPAA-fähig sind, müssen Sie auch die [!DNL Data Connection]-Erweiterung mit der zusätzlichen **Data Services HIPAA**-Erweiterung installieren. Die **Data Services HIPAA**-Erweiterung stellt sicher, dass alle Back-Office-Daten, die Sie an Experience Platform senden, HIPAA-fähig sind. Erfahren Sie [wie Sie die Erweiterung installieren](install.md#install-the-data-services-hipaa-extension).

>[!IMPORTANT]
>
>Wenn Sie die **Data Services HIPAA**-Erweiterung installieren, werden Storefront-Ereignisdaten, die von Live Search und Product Recommendations verwendet werden, nicht mehr erfasst. Dies liegt daran, dass Storefront-Ereignisdaten Client-seitig generiert werden. Um Storefront-Ereignisdaten weiterhin zu erfassen und zu senden, aktivieren Sie die Ereigniserfassung für diese Services erneut. Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general#data-services)Allgemeine Konfiguration“.

## So stellen Sie sicher, dass an Experience Platform gesendete Daten HIPAA-fähig sind

Alle Back-Office-Ereignisdaten, die die [!DNL Data Connection]-Erweiterung an Experience Platform sendet, werden in [!DNL Commerce] als vertraulich betrachtet. Es liegt jedoch in der Verantwortung des Händlers, Datennutzungskennzeichnungen auf sein [!DNL Commerce] in Experience Platform anzuwenden, um bestimmte Daten explizit als sensibel zu kennzeichnen. Wenn Sie Datennutzungskennzeichnungen direkt auf ein Schema anwenden, werden diese Kennzeichnungen auf alle vorhandenen und zukünftigen Datensätze übertragen, die auf diesem Schema basieren.

Eine Übersicht über Datennutzungskennzeichnungen und ihre Rolle im Data Governance-Framework finden Sie unter [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) in der Dokumentation zu Experience Platform.

### Anwenden von Datennutzungskennzeichnungen auf [!DNL Commerce]

Befolgen Sie die Schritte im Tutorial [Verwalten von Datennutzungskennzeichnungen für ein Schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/labels), um zu erfahren, wie Sie Kennzeichnungen auf Ihr [!DNL Commerce]-Schema anwenden.

Im [Glossar der sensiblen Kennzeichnungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/reference#sensitive) erfahren Sie mehr über die verfügbaren Kennzeichnungen, die Sie auf die Felder in Ihrem [!DNL Commerce] anwenden können. Beispielsweise kennzeichnet das Label `RHD` geschützte Gesundheitsinformationen (PHI) oder Patienteninformationen, die von Adobe vertraglich zum Hochladen zugelassen sind.

Wenn Ihre [!DNL Commerce] als sensibel gekennzeichnet sind, können Sie Richtlinien durchsetzen, um Datenoperationen zu verhindern, die Richtlinienverletzungen darstellen. Erfahren Sie mehr über [Richtliniendurchsetzung](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) in Experience Platform.

## Datenverschlüsselung in Commerce

Adobe [!DNL Commerce] verwendet eine Verschlüsselung auf Blockebene. Für die Speicherung verwendet [!DNL Commerce] Amazon Elastic Block Store (EBS). Alle EBS-Volumes werden mit dem AES-256-Algorithmus verschlüsselt, was bedeutet, dass die Daten im Ruhezustand verschlüsselt werden. [!DNL Commerce] Daten während der Übertragung werden über sichere, verschlüsselte Verbindungen mit HTTPS ([&#x200B; v1.2) &#x200B;](https://datatracker.ietf.org/doc/html/rfc5246).

>[!IMPORTANT]
>
>Commerce unterstützt keine Verschlüsselung oder Verschlüsselung auf Spalten- oder Zeilenebene, wenn sich die Daten nicht im Ruhezustand befinden oder nicht zwischen Servern übertragen werden.

### Datenverschlüsselung in Experience Platform

Wenn Händler ihre Daten an Experience Platform senden, werden diese Daten mit HTTPS TLS v1.2 gesendet. Erfahren Sie mehr darüber, wie [Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/encryption) Daten verschlüsselt.

## Handhabung von Datenschutzanfragen durch [!DNL Commerce]

Erfahren Sie[!DNL Commerce] wie [Datenschutzanfragen verarbeitet](handle-privacy-request.md).
