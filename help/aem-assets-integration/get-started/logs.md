---
title: Anzeigen und Verwalten von Protokollen
description: Erfahren Sie, wo Sie Protokolle für die AEM Assets-Integration für Commerce finden und verwalten können.
feature: CMS, Media, Integration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
exl-id: 9c6c8694-6ded-4cc8-a3ab-d1dfb50e3583
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%
---
# Anzeigen und Verwalten von Protokollen

Die AEM Assets-Integration stellt die folgenden Protokolldateien in Ihrer Commerce-Instanz bereit:

- `/var/log/aem-assets-integration.log`
- `/var/log/aem-assets-integration-errors.log`

Eine Asset-orientierte Ansicht synchronisierter Assets in Admin, einschließlich Suche, Filtern und Zusammenfassung der Synchronisierungsfehler, finden Sie unter [Anzeigen des AEM Assets-Synchronisierungsstatus](sync-status.md).

Bitten Sie Ihren Systemadministrator, den Drehplan für die Protokolldateien auf diese Protokolle zu überprüfen, um zu verhindern, dass sie zu groß werden. In einigen Umgebungen drehen sich Protokolle automatisch. In anderen müssen Sie die Protokollrotation manuell konfigurieren.  Weitere Informationen finden Sie in den folgenden Themen:

- Bitten Sie bei lokalen Installationen von Adobe Commerce Ihren Systemadministrator, eine [&#x200B; einzurichten](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration#server-settings).
- Informationen zu Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations).
