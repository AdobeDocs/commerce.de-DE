---
title: Konfigurieren von IMS-Benutzerberechtigungen für die AEM Assets-Integration
description: Erfahren Sie, wie die IMS-Identität und Admin Console-Profile den Zugriff auf AEM Assets-Bereitstellungen, den Asset-Selektor und automatisch ausgefüllte Commerce-Konfigurationsfelder ermöglichen.
feature: CMS, Media, Configuration
source-git-commit: 0fd98bf86555c914f7a5b1e177c31c37764dbf84
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---

# Benutzerberechtigungen und IMS

**IMS** (Adobe Identity Management System) ist die Authentifizierungsebene. Für Adobe Commerce as a Cloud Service ist die IMS-Authentifizierung standardmäßig im Admin-Bereich aktiviert. Für Adobe Commerce in der Cloud oder lokal ist IMS optional. [Aktivieren von IMS für Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/ims/adobe-ims-config.html){target=_blank} bietet eine erweiterte Konfigurationsoberfläche (Asset-Selektor, automatisch ausgefüllte Dropdown-Listen). Sie können die Integration jedoch auch ohne IMS konfigurieren, indem Sie **Programm-ID** und **Umgebungs-ID** manuell eingeben.

Die AEM Assets-Integration erfordert auch bestimmte **Adobe Admin Console-Produktprofile** wenn Sie IMS verwenden. Benutzende, die die Integration in Commerce Admin konfigurieren, benötigen das Produktprofil **AEM Assets DM OpenAPI Users - delivery** oder das Produktprofil **author** als Fallback. Dies wird über Admin Console-Produktprofile in der IMS-Organisation des Benutzers gesteuert und ermöglicht:

* **Asset-Selektor** ermöglicht die Auswahl von Bildern aus AEM Assets beim Verwalten von Kategoriebildern oder Page Builder-Inhalten.
* **Automatisch ausgefüllte Konfigurationsfelder** wie **Programm-ID**, **Umgebungs-ID** und **Domain-Zuordnung** Dropdown-Listen, die basierend auf ihren Admin Console-Produktprofilen (Versand oder Autor) Werte aus der IMS-Sitzung des Benutzers abrufen.

Ohne die richtigen Berechtigungen ist der Asset-Wähler nicht verfügbar und diese Felder erscheinen leer oder müssen manuell eingegeben werden.
>[!BEGINSHADEBOX]

**So arbeiten IMS und Berechtigungen zusammen**

Adobe IMS stellt die Benutzeridentität und den Organisationskontext bereit, während Adobe Admin Console definiert **welche (Produktprofile**(Berechtigungen) es hat. Die AEM Assets-Integration verwendet die IMS-Details plus das zugewiesene Profil, um zu bestimmen, ob Konfigurationsfelder automatisch ausgefüllt und der Asset-Selektor aktiviert werden kann.

>[!ENDSHADEBOX]

## Warum Produktprofile erforderlich sind

Die Integration kann nur Domains laden, die einem Profil zugeordnet sind. Daher können Benutzer über die folgenden Produktprofile verfügen:

* **AEM-Versand-Produktprofil**. Erforderlich für die Asset-Wähler- und Konfigurations-Benutzeroberfläche, wenn der Benutzer sowohl über Autoren- als auch über Bereitstellungsprofile verfügt. Die Integration verwendet das Produktprofil AEM-Versand , sofern verfügbar.

* **Produktprofil erstellen**. Erforderlich für den Zugriff auf die AEM Assets-Benutzeroberfläche. Dient auch als Fallback für die Asset-Wähler- und Konfigurations-Benutzeroberfläche, wenn der Benutzer nicht über das Produktprofil &quot;AEM-Bereitstellung“ in seiner Admin Console verfügt.

Domains (einschließlich Programm-ID, Umgebungs-ID und Domain-Zuordnung) werden dem AEM-Versand-Produktprofil zugewiesen. Die Integration lädt Domains aus dem Produktprofil **Versand von AEM** falls verfügbar, oder kehrt zurück zum Produktprofil **Autor**, wenn das Produktprofil AEM-Versand nicht in der Admin Console des Benutzers enthalten ist. Benutzende benötigen eines dieser Profile, um:

* Füllen Sie die **Programm**, **Umgebungs-ID** und **Domain-Zuordnung** in der Commerce Admin-Konfiguration aus.
* Verwenden Sie den Asset-Wähler, um Assets in AEM Assets zu durchsuchen und auszuwählen.

Wenn keines der Profile konfiguriert ist, können Benutzer **Programm-ID** und **Umgebungs-ID** manuell eingeben, aber der Asset-Wähler ist nicht verfügbar.

## Berechtigungen nach Bereitstellungstyp erteilen

>[!BEGINTABS]

>[!TAB Adobe Commerce as a Cloud Service]

[!BADGE nur SaaS]{type=Positive tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."}

Die IMS-Authentifizierung ist standardmäßig aktiviert. Fügen Sie den Benutzer dem Produktprofil **AEM Assets DM OpenAPI Users - delivery** in der [Adobe Admin Console](https://adminconsole.adobe.com/) oder dem Produktprofil **author** (z. B. `<environment-name> - author - <program-id> - <environment-id>`) als Ausweichlösung hinzu, wenn der Benutzer das Produktprofil AEM-Versand nicht in der Admin Console hat.

>[!NOTE]
>
> Benutzende müssen auch zu Commerce und AEM Assets hinzugefügt werden. Siehe [Hinzufügen von Benutzenden zu AEM Assets oder Produktvisualisierungen](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/user-management#add-a-user-to-aem-assets-or-product-visuals){target=_blank} im _Benutzerhandbuch und Identity Management_ für die vollständige Einrichtung.

![Admin Console-Produktprofil für AEM Assets-Versand](../assets/aem-assets-delivery-product-profile.png){width="600" zoomable="yes"}

>[!TAB Adobe Commerce in der Cloud oder lokal]

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."}

Die **IMS-Client-**) ist für PaaS erforderlich, um den Asset-Wähler zu aktivieren. Unter [Konfigurieren des AEM Assets-Projekts](configure-aem.md#prerequisites) finden Sie Voraussetzungen, einschließlich der Vorgehensweise beim Abrufen der IMS-Client-ID beim Aktivieren von Dynamic Media mit OpenAPI.

So verwenden Sie den Asset-Selektor und automatisch ausgefüllte Konfigurationsfelder (Programm-ID, Umgebungs-ID, Domain-Zuordnung):

1. [Adobe IMS für Commerce aktivieren](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/ims/adobe-ims-config.html){target=_blank} sodass der Commerce-Administrator die IMS-Authentifizierung verwendet und die Admin Console-Produktprofile der Benutzenden lesen kann.

1. [Öffnen Sie ein Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases), um eine benutzerdefinierte IMS-Client-ID für den Asset-Wähler anzufordern.

1. Fügen Sie in der [Adobe Admin Console](https://adminconsole.adobe.com/) den Benutzer dem Produktprofil **AEM Assets DM OpenAPI Users - delivery** oder dem Produktprofil **author** (z. B. `<environment-name> - author - <program-id> - <environment-id>`) als Ausweichlösung hinzu, wenn der Benutzer nicht über das Produktprofil AEM-Versand in seiner Admin Console verfügt.

Ohne IMS können Sie die Integration weiterhin konfigurieren, indem Sie die Programm-ID und die Umgebungs-ID im Commerce Admin manuell eingeben.

>[!ENDTABS]

## Verwandte Dokumentation

* [Konfigurieren von IMS-Benutzerberechtigungen für die AEM Assets-Integration](setup-synchronization.md) - Verbinden Sie Commerce mit AEM Assets und konfigurieren Sie übereinstimmende Regeln.
* [Manuelle Asset-Auswahl](../synchronize/asset-selector-integration.md) - Verwenden Sie den Asset-Selektor für Kategoriebilder und Page Builder.
* [Benutzer zu AEM Assets oder Produktvisualisierungen hinzufügen](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/user-management#add-a-user-to-aem-assets-or-product-visuals){target=_blank} - Fügen Sie ACCS zuerst Benutzer zu Commerce und AEM Cloud Manager (Geschäftsinhaber, Bereitstellungs-Manager) hinzu. Das Profil **AEM Assets DM OpenAPI Users - delivery** (oder **author**-Profil als Fallback) ist eine zusätzliche Anforderung für die Asset-Wähler- und Auto-Ausfüllen-Funktionen.
* [Weisen Sie Team-Mitglieder der AEM-Bereitstellungsebene zu](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem#add-team-members){target=_blank}. AEM-Dokumentation für den Versandzugriff.
