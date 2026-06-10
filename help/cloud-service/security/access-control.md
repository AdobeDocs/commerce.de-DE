---
title: Identitäts- und Zugriffsverwaltung
description: Erfahren Sie mehr über die Funktionen zur Identitäts- und Zugriffsverwaltung für Adobe Commerce as a Cloud Service.
role: Admin, Developer, Leader
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
TQID: 'https://experienceleague.adobe.com/lbI3nsLtafel6GtquXnkZmXD2Z3b-rRGPOyr8EqzrjE'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ef32511703a96b5f4db32d54229e9a7cbe961f12
workflow-type: tm+mt
source-wordcount: 419
ht-degree: 0%

---


# Identitäts- und Zugriffsverwaltung

[!DNL Adobe Commerce as a Cloud Service] nutzt die Identitätsinfrastruktur von Adobe im Unternehmensmaßstab, um eine sichere, skalierbare und zentralisierte Zugriffskontrolle über alle Umgebungen hinweg sicherzustellen. Die Identitäts- und Zugriffsverwaltung (IAM) in [!DNL Adobe Commerce as a Cloud Service] vereinfacht die Benutzerbereitstellung, erzwingt den Zugriff mit geringsten Rechten und unterstützt die Einhaltung globaler Sicherheitsstandards.

- **[!DNL Adobe Identity Management Services (IMS)]**: [!DNL Adobe Commerce as a Cloud Service] verwendet [Adobe Identity Management Services (IMS)](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/ims/adobe-ims-integration-overview) um Benutzende zu authentifizieren und Berechtigungen zu verwalten. Dazu gehört die Unterstützung von Anbietern zusammengeführter Identitäten und [rollenbasierte Zugriffssteuerung](../user-management.md).

- **Admin Console Governance**: Administratoren verwalten den Zugriff auf die Storefront und das Backend über die [!DNL Adobe Admin Console]. Berechtigungen können auf bestimmte Funktionen und Rollen beschränkt werden, um den Zugriff mit den geringsten Rechten sicherzustellen.

## Adobe Identity Management Services (IMS)

[!DNL Adobe Commerce as a Cloud Service] verwendet [!DNL Adobe Identity Management Services (IMS)] zur Authentifizierung von Benutzern und zur Verwaltung von Berechtigungen in der gesamten Plattform. IMS bietet:

- **Unterstützung von Federated**: Integration mit Enterprise-Identitätsanbietern wie Azure AD und Okta mithilfe von SAML oder OIDC.
- **Single Sign-On (SSO)**: Nahtloser Zugriff auf [!DNL Adobe Commerce] und andere [!DNL Adobe Experience Cloud].
- **Multi-Factor Authentication (MFA)**: Wird auf Unternehmensebene erzwungen, um die Sicherheit zu verbessern.
- **Globale Redundanz**: Identitätsdaten werden in einer Cloud-Infrastruktur mit mehreren Regionen und einem Lastenausgleich gespeichert.

## Admin Console-Zugriffskontrolle

Der [!DNL Adobe Admin Console] ist der zentrale Hub für die Verwaltung des Benutzerzugriffs auf [!DNL Adobe Commerce as a Cloud Service]:

- **Rollenbasierte Zugriffssteuerung (RBAC)** Weisen Sie Benutzern auf Grundlage ihrer Rollen (z. B. Entwickler, Admin und Analyst) granulare Berechtigungen zu.
- **Produktprofile**: Definieren Sie Zugriffsbereiche für verschiedene Umgebungen wie Staging und Produktion.
- **Delegierte Administration**: Systemadministratoren und Produktadministratoren können den Benutzerzugriff ohne IT-Beteiligung verwalten.

Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/user-management)Benutzerverwaltung“.

## API-Authentifizierung und Integrationssicherheit

Die REST-API-Authentifizierung von [!DNL Adobe Commerce as a Cloud Service] wird über die [!DNL Adobe Identity Management Services (IMS)] von Adobe mithilfe standardisierter OAuth 2-Protokolle durchgeführt. Dieses Authentifizierungssystem unterstützt sowohl interaktive, benutzerbasierte Workflows als auch automatisierte Server-zu-Server-Integrationen und stellt so einen sicheren und angemessenen Zugriff für verschiedene Anwendungsfälle sicher.

>[!NOTE]
>
>Die Generierungsmethoden für Admin- und Integrations-Token in PaaS-Versionen von [!DNL Adobe Commerce] werden in SaaS-Umgebungen nicht unterstützt. Stattdessen müssen Sie ein IMS-Admin-Token über die OAuth-Authentifizierung erhalten.

- **OAuth 2.0-Unterstützung**: Sichere Token-basierte Authentifizierung für Integrationen und Services von Drittanbietern.
- **API-Zugriff im Umfang**: Beschränken des API-Zugriffs auf bestimmte Ressourcen und Vorgänge.
- **Auditprotokollierung**: Verfolgen Sie Authentifizierungsereignisse und Zugriffsänderungen, um die Compliance und die Fehlerbehebung sicherzustellen.

Weitere Informationen finden [&#x200B; unter &#x200B;](https://developer.adobe.com/commerce/webapi/rest/authentication/)-Authentifizierung .
