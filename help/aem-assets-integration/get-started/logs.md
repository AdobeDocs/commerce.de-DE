---
title: Anzeigen und Verwalten von Protokollen
description: Erfahren Sie, wo Sie Protokolle für die AEM Assets-Integration für Commerce finden und verwalten können.
feature: CMS, Media, Integration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
exl-id: 9c6c8694-6ded-4cc8-a3ab-d1dfb50e3583
source-git-commit: d425bad4d3314aa0e14b639ffb8d89dd8b6b0f74
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Anzeigen und Verwalten von Protokollen

Die AEM Assets-Integration stellt die folgenden Protokolldateien in Ihrer Commerce-Instanz bereit:

- `/var/log/aem-assets-integration.log`
- `/var/log/aem-assets-integration-errors.log`

Eine Asset-orientierte Ansicht synchronisierter Assets in Admin, einschließlich Suche, Filtern und Zusammenfassung der Synchronisierungsfehler, finden Sie unter [Anzeigen des AEM Assets-Synchronisierungsstatus](sync-status.md).

Bitten Sie Ihren Systemadministrator, den Drehplan für die Protokolldateien auf diese Protokolle zu überprüfen, um zu verhindern, dass sie zu groß werden. In einigen Umgebungen drehen sich Protokolle automatisch. In anderen müssen Sie die Protokollrotation manuell konfigurieren.  Weitere Informationen finden Sie in den folgenden Themen:

- Bitten Sie bei lokalen Installationen von Adobe Commerce Ihren Systemadministrator, eine [&#x200B; einzurichten](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings).
- Informationen zu Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).
