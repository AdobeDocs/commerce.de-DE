---
title: Adobe Commerce SaaS im Vergleich zu PaaS
description: Vergleichen Sie Adobe Commerce SaaS- und PaaS-Modelle, um den optimalen Implementierungsansatz für Ihre Geschäftsanforderungen zu ermitteln.
feature: App Builder, GraphQL, Integration, Saas
role: Developer, Admin, Leader
level: Intermediate
exl-id: c8c9a0b4-f47c-46ec-bc9d-39dee9641f59
source-git-commit: 3fe22d47b6fd6cf1077cbd4644ffad08f55826ca
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 0%

---

# Funktionsvergleich

Adobe Commerce bietet drei Bereitstellungsmodelle:

- [!BADGE Nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."} [Adobe Commerce as a Cloud Service](overview.md) (SaaS)
- [!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."} [Adobe Commerce on Cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview) (PaaS)
- [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview) (lokal)

Dieser Vergleich konzentriert sich auf die Unterschiede zwischen Software-as-a-Service (SaaS)- und Platform-as-a-Service (PaaS)-Modellen. Diese Modelle bieten verschiedene Stufen der Anpassung, Erweiterbarkeit und Kontrolle über Ihre Commerce-Implementierung.

>[!NOTE]
>
>Das On-Premise-Modell weist ähnliche Funktionen wie das PaaS-Modell auf. Daher gilt dieser Vergleich auch, wenn SaaS- und On-Premise-Implementierungen verglichen werden.

## Funktionen zur Store-Verwaltung

Die [Commerce Admin-Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/guide-overview) ist die primäre Oberfläche für den Zugriff auf Funktionen zur Verwaltung von Backend-Store-Vorgängen, Inventar, Preisen, Promotions und Kundeninteraktionen. [!DNL Adobe Commerce as a Cloud Service] bietet jedoch einzigartige Lösungen, die einige der bekannten Funktionen ersetzen, die in [!DNL Adobe Commerce on Cloud]- und On-Premise-Projekten verfügbar sind.

In der folgenden Tabelle werden die Funktionen und Ersatzlösungen beschrieben, die in [!DNL Adobe Commerce as a Cloud Service] verfügbar sind:

<table>
    <thead>
        <tr>
            <th>PaaS-Modell [!BADGE PaaS only]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip=„Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte.“}</th>
            <th>SaaS-Modell [!BADGE SaaS only]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip=„Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (Adobe-verwaltete SaaS-Infrastruktur).“}</th>
            <th>Details</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/gallery/media-gallery-asset-management">Digital Asset Management</a></td>
            <td><a href="../aem-assets-integration/overview.md">AEM Assets-Integration</a></td>
            <td>Ein robustes DAM-System (Digital Asset Management), das für die Verwaltung von Rich-Media-Inhalten mit Adobe Experience Manager integriert ist. Alternativ bietet die standardmäßige Digital File and Asset Management-Funktion grundlegende Asset-Management-Tools zum Speichern und Verwalten digitaler Assets.</td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/guide-overview">Content Management System (CMS)</a></td>
            <td rowspan="3"><a href="https://experienceleague.adobe.com/developer/commerce/storefront/merchants/get-started/">Storefront Builder</a></td>
            <td rowspan="3">Eine CMS, mit der Benutzende Storefront-Inhalte einfach mit der Dokumenterstellung oder einem visuellen Editor erstellen und verwalten können, und bietet native Experimentierfunktionen.</td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/guide-overview">Page Builder</a></td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite">URL-Neuschreibungen</a></td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging">Inhalts-Staging</a></td>
            <td rowspan="2"><a href="../catalog-service/overview.md">Katalog-Service</a></td>
            <td rowspan="2">Ein Rich-View-Model-Service (schreibgeschützt) zum Verwalten von Katalogdaten und Rendern von produktbezogenen Storefront-Erlebnissen.</td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/merchandising/visual-merch/visual-merchandiser">Visual Merchandiser</a></td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/payments">Zahlungen</a></td>
            <td><a href="../payment-services/guide-overview.md">Zahlungsdienste</a></td>
            <td>Ein integrierter Zahlungsdienst, der sichere und effiziente Transaktionen ermöglicht.</td>
        </tr>
    </tbody>
</table>

## Erweiterbarkeit und Plattformfunktionen

In der folgenden Tabelle werden die Funktionen der Plattform und die Erweiterungsfunktionen verglichen, damit Sie die Unterschiede besser verstehen und entscheiden können, welches Modell am besten zu Ihren Geschäftsanforderungen passt, bevor Sie mit der Implementierung beginnen.

<table>
    <thead>
        <tr>
            <th>Funktion</th>
            <th>PaaS-Modell [!BADGE PaaS only]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip=„Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte.“}</th>
            <th>SaaS-Modell [!BADGE SaaS only]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip=„Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (Adobe-verwaltete SaaS-Infrastruktur).“}</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Platform-Funktionen</strong></td>
        </tr>
        <tr>
            <td>B2B-Funktionalität</td>
            <td>Vollständige B2B-Funktionen nach der Installation verfügbar</td>
            <td>Vorinstalliert mit B2B-Kernfunktionen<sup>1</sup></td>
        </tr>
        <tr>
            <td>Experimentieren</td>
            <td>Add-on für bestimmte Ebenen</td>
            <td>A/B-Tests zur Optimierung von Interaktion und Konversion</td>
        </tr>
        <tr>
            <td>Funktions- und Sicherheits-Updates</td>
            <td>Erfordert manuelles Upgrade und Patching</td>
            <td>Automatisch bereitstellen</td>
        </tr>
        <tr>
            <td>Hosting-Infrastruktur</td>
            <td>Einzelmandant</td>
            <td>Mehrmandant</td>
        </tr>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Commerce Admin-Anpassung</strong></td>
        </tr>
        <tr>
            <td>Erweiterbare Hauptverwaltungsbildschirme</td>
            <td>Vollständige Anpassung des Layouts und der Funktionen</td>
            <td>Vordefinierte Filter, Sichtbarkeitssteuerelemente</td>
        </tr>
        <tr>
            <td>Erweiterbare neue Admin-Bildschirme</td>
            <td>Standardmäßige Admin-UI-Integration und Einschleusen externer Apps (Admin-UI SDK)</td>
            <td>Einschleusen externer Apps (Admin UI SDK)</td>
        </tr>
        <tr>
            <td>Anpassbares Admin-Design</td>
            <td>Erweiterbares Design-Framework</td>
            <td>Kein Design-Framework</td>
        </tr>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Erweiterbarkeit</strong></td>
        </tr>
        <tr>
            <td>Erweiterbarkeitsmodell</td>
            <td>In-Prozess (PHP-Anpassung) und Out-of-Process (APIs, Ereignisse, App Builder)</td>
            <td>Nur Out-of-Process (APIs, Ereignisse, App Builder)</td>
        </tr>
        <tr>
            <td>Erweiterbare Web-APIs</td>
            <td>Native REST/GraphQL-Erweiterbarkeit und API-Mesh mit benutzerdefinierten Resolvern</td>
            <td>API-Mesh mit benutzerdefinierten Resolvern</td>
        </tr>
        <tr>
            <td>Erweiterbarkeit von Datenmodellen</td>
            <td>Vollständige Anpassung des Datenmodells</td>
            <td>Benutzerdefinierte Attribute für Kern- und B2B-<sup>2</sup></td>
        </tr>
        <tr>
            <td>Technologien</td>
            <td>CSS, CLI, HTML, JS, PHP, XML</td>
            <td>CSS, CLI, HTML, JS, Knoten</td>
        </tr>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Daten und Speicher</strong></td>
        </tr>
        <tr>
            <td>Anpassungen des Suchindex</td>
            <td>Native Suchanpassung</td>
            <td>Erfordert Lösungen von Drittanbietern</td>
        </tr>
        <tr>
            <td>Benutzerdefinierte E-Mail-Typen</td>
            <td>Vollständige E-Mail-Anpassung</td>
            <td>Nur Standard-E-Mail-Vorlagen</td>
        </tr>
        <tr>
            <td>Benutzerdefinierter Datenspeicher</td>
            <td>DB, Datei, Cache, Warteschlange</td>
            <td>App Builder-Statusbibliothek (nur -Datei)<sup>3</sup></td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">
                <sup>1</sup> Die <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview">B2B-Funktionen</a> wie die Unternehmensführung und die Kostenvoranschläge, sind in SaaS standardmäßig verfügbar. Branchenspezifische Anpassungen können jedoch zusätzliche Überlegungen zur Implementierung erfordern.
                <br><br>
                <sup>2</sup> Die Erweiterbarkeit von Datenmodellen in SaaS unterstützt <a href="https://developer.adobe.com/commerce/webapi/graphql/schema/attributes/mutations/">Erweiterung von Kernentitäten</a> über Produkt- und Kundenentitäten hinaus, einschließlich B2B-Entitäten. Für branchenspezifische Datenmodelle (z. B. händlerspezifische Attribute) können jedoch zusätzliche Überlegungen zur Architektur erforderlich sein.
                <br><br>
                <sup>3</sup> Adobe arbeitet aktiv an der Integration von Document DB, um persistente Speicheranforderungen für SaaS zu erfüllen. Derzeit müssen bei Implementierungen, die eine langfristige Datenspeicherung erfordern, möglicherweise zusätzliche Infrastrukturen bereitgestellt und gewartet werden.
            </td>
        </tr>
    </tfoot>
</table>

>[!NOTE]
>
>Adobe empfiehlt bei der Migration auf SaaS Folgendes:
>
>- Verschieben Sie nach Möglichkeit geeignete Funktionen auf die prozessexterne Erweiterbarkeit.
>- Verkleinern Sie die Fläche, für die ein Übergang erforderlich ist.
>- Erwägen Sie [!DNL API Mesh] für die Erweiterung der API-Funktionalität.
>- Überwachen Sie die fortlaufende Plattformentwicklung und neue Funktionsveröffentlichungen von Adobe.
>- Bewerten Sie branchenspezifische Datenmodellanforderungen anhand der verfügbaren Erweiterungsoptionen.
>- Erwägen Sie die [ von (Merchandising-Services, die auf Katalogansichten und Richtlinien basieren](../optimizer/setup/catalog-view.md).
