---
title: Versionshinweise
description: Die neuesten Versionsinformationen für das  [!DNL Adobe Commerce Optimizer].
role: Admin, Developer, User, Leader
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: e420d461-9ea2-4e32-aa37-230b14a297d7
source-git-commit: d0967674d05018f13dc6c8a562005d65d44e42ab
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---

# Versionshinweise

Die folgenden Versionshinweise enthalten Aktualisierungen zu [!DNL Adobe Commerce Optimizer].

## April 2026

**Veröffentlichungsdatum:**. April 2026

>[!BEGINSHADEBOX]

### Katalogregeln

Merchandising-Regeln enthalten jetzt [Kategorieregeln](./merchandising/rules/add.md), sodass Sie eine oder mehrere Kategorien auswählen und die Produktreihenfolge auf Kategorieseiten steuern können, indem Sie dieselben intelligenten Ranking- und manuellen Aktionen (Pin, Boost, Bury) wie für die Suche verwenden.

### Preisfilter

Empfehlungsfilter unterstützen jetzt einen [Preisfilter](./merchandising/recommendations/filters.md#price) mit dem Sie eine Mindest- und Höchstpreisspanne für Produkte festlegen können.

### Zusätzliche Versionshinweise

[!DNL Adobe Commerce Optimizer] funktioniert mit den neuesten Versionen der AEM Assets-Integration, dem Commerce Optimizer-Connector und [!DNL Adobe Commerce Storefront]. Über die folgenden Links können Sie Versionshinweise für jeden Bereich anzeigen:

| Erweiterbarkeit | Schaufenster |
| --- | --- |
| [AEM Assets-Integration](../aem-assets-integration/release-notes.md)<br>[Commerce Optimizer-Connector](../aco-connector/release-notes.md) | [Storefront-Versionsinformationen](https://experienceleague.adobe.com/developer/commerce/storefront/releases/)<br>[Storefront-Änderungsprotokoll](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/) |

>[!ENDSHADEBOX]

## Februar 2026

**Veröffentlichungsdatum**: 19. Februar 2026

>[!BEGINSHADEBOX]

Es wurde die Möglichkeit hinzugefügt, eine Katalogansicht anzugeben, wenn Sie [Empfehlungseinheiten erstellen](./merchandising/recommendations/create.md) oder ([) &#x200B;](./merchandising/rules/add.md).

### Zusätzliche Versionshinweise

[!DNL Adobe Commerce Optimizer] funktioniert mit den neuesten Versionen der AEM Assets-Integration, dem Commerce Optimizer-Connector und [!DNL Adobe Commerce Storefront]. Über die folgenden Links können Sie Versionshinweise für jeden Bereich anzeigen:

| Erweiterbarkeit | Schaufenster |
| --- | --- |
| [AEM Assets-Integration](../aem-assets-integration/release-notes.md)<br>[Commerce Optimizer-Connector](../aco-connector/release-notes.md) | [Storefront-Versionsinformationen](https://experienceleague.adobe.com/developer/commerce/storefront/releases/)<br>[Storefront-Änderungsprotokoll](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/) |

>[!ENDSHADEBOX]

## Dezember 2025

**Veröffentlichungsdatum:**. Dezember 2025

>[!BEGINSHADEBOX]

### Opportunities

KI-gestützte Empfehlungen zur Site-Optimierung sind jetzt über die [Adobe Sites Optimizer-Integration](./manage-results/opportunities.md) verfügbar. Diese Funktion hilft Merchandisern, Probleme, die die Leistung der Commerce-Site beeinträchtigen, zu identifizieren und zu beheben, indem automatisierte Erkennung und intelligente Empfehlungen bereitgestellt werden.

### Katalogebenen

Es wurden [Katalogebenen](./setup/catalog-layer.md) hinzugefügt, damit Sie Produktdaten ändern können, ohne die Quelldaten zu ändern, einschließlich der Ebenenprioritätsverwaltung und der Integration mit Adobe Sites Optimizer-Funktionen zur automatischen Fehlerbehebung.

### Zusätzliche Versionshinweise

[!DNL Adobe Commerce Optimizer] funktioniert mit den neuesten Versionen der AEM Assets-Integration, dem Commerce Optimizer-Connector und [!DNL Adobe Commerce Storefront]. Über die folgenden Links können Sie Versionshinweise für jeden Bereich anzeigen:

| Erweiterbarkeit | Schaufenster |
| --- | --- |
| [AEM Assets-Integration](../aem-assets-integration/release-notes.md)<br>[Commerce Optimizer-Connector](../aco-connector/release-notes.md) | [Storefront-Versionsinformationen](https://experienceleague.adobe.com/developer/commerce/storefront/releases/)<br>[Storefront-Änderungsprotokoll](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/) |

>[!ENDSHADEBOX]

## Oktober 2025

**Veröffentlichungsdatum:**. Oktober 2025

>[!BEGINSHADEBOX]

### Commerce Optimizer Salesforce Commerce Connector

Das [!DNL Commerce Optimizer Salesforce Commerce Connector] ist ein neues Starter-Kit für die App Builder-Integration, mit dem Commerce-Administratoren und -Entwickler Salesforce B2C Commerce-Katalogdaten nahtlos mit [!DNL Commerce Optimizer] verbinden können.<!--COMOPT-536-->

**Für Administratoren:**

* Katalogaktualisierungen in Salesforce (Produkte, Preise, Metadaten, Preisverzeichnisse) werden automatisch mit Commerce Optimizer synchronisiert, sodass kein manueller Eingriff erforderlich ist.
* Die Integration arbeitet unabhängig von Adobe Commerce, wodurch die Komplexität und die potenziellen Fehlerquellen reduziert werden.
* Admins können sich auf geplante regelmäßige Aktualisierungen verlassen, um präzise Katalogdaten in Commerce Optimizer sicherzustellen und so das Merchandising und Produktempfehlungen zu verbessern.

**Für Entwickler:**

* Das Starter Kit bietet ein optimiertes, erweiterbares Framework für die Aufnahme von Salesforce-Katalogdaten in SaaS-Merchandising-Services.
* Referenzimplementierungen, Entwurfsdokumentation und Codebeispiele sind verfügbar, um benutzerdefinierte Integrationen oder die Fehlerbehebung zu beschleunigen.<!--COMOPT-536-->

### Mehrschichtige Suche

* GA-Version für die folgenden erweiterten Suchfunktionen: Mehrschichtige Suche mit `startsWith` und `contains`. [Weitere Informationen](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#layered-search-and-expansion-of-search-types).

### Kategorien-APIs

Eine neue Kategorien-REST-API ist jetzt verfügbar, mit der Admins und Entwickler mehrere Kategoriestrukturen für die Navigation und Produktgruppierung programmgesteuert erstellen, aktualisieren und verwalten können. Die API unterstützt sowohl globale als auch kanalspezifische Konfigurationen und ist für hohe Skalierbarkeit ausgelegt. Sie unterstützt bis zu 10.000 Kategoriestrukturen und 500 Kategorien pro Struktur. Weitere Informationen finden Sie unter [Kategorien](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/#categories) im _Merchandising Services-Entwicklerhandbuch_.<!--DCAT-2649-->

### Zusätzliche Versionshinweise

[!DNL Adobe Commerce Optimizer] funktioniert mit den neuesten Versionen der AEM Assets-Integration, dem Commerce Optimizer-Connector und [!DNL Adobe Commerce Storefront]. Über die folgenden Links können Sie Versionshinweise für jeden Bereich anzeigen:

| Erweiterbarkeit | Schaufenster |
| --- | --- |
| [AEM Assets-Integration](../aem-assets-integration/release-notes.md)<br>[Commerce Optimizer-Connector](../aco-connector/release-notes.md) | [Storefront-Versionsinformationen](https://experienceleague.adobe.com/developer/commerce/storefront/releases/)<br>[Storefront-Änderungsprotokoll](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/) |

>[!ENDSHADEBOX]

## August 2025

**Veröffentlichungsdatum:**. August 2025

>[!BEGINSHADEBOX]

### EU-Region jetzt verfügbar

Unterstützung für Kunden-IMS-Organisationen aus der Region der Europäischen Union (eu1) ist jetzt verfügbar. Sie können jetzt **Europäische Union** als **Region** auswählen, wenn [eine Commerce Optimizer-Instanz &#x200B;](./get-started.md#step-1-create-an-instance) Cloud Manager hinzufügen. Die Region der Europäischen Union ist nur für Produktionsumgebungen verfügbar.

Die Basis-Produktions-URLs für die Region der Europäischen Union lauten:

* Administrator: `https://eu1.admin.commerce.adobe.com`
* REST und GraphQL: `https://eu1.api.commerce.adobe.com`

![Instanz erstellen](./assets/create-instance.png){width="600" align="center" zoomable="yes"}

### Zusätzliche Versionshinweise

[!DNL Adobe Commerce Optimizer] funktioniert mit den neuesten Versionen der AEM Assets-Integration, dem Commerce Optimizer-Connector und [!DNL Adobe Commerce Storefront]. Über die folgenden Links können Sie Versionshinweise für jeden Bereich anzeigen:

| Erweiterbarkeit | Schaufenster |
| --- | --- |
| [AEM Assets-Integration](../aem-assets-integration/release-notes.md)<br>[Commerce Optimizer-Connector](../aco-connector/release-notes.md) | [Storefront-Versionsinformationen](https://experienceleague.adobe.com/developer/commerce/storefront/releases/)<br>[Storefront-Änderungsprotokoll](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/) |

>[!ENDSHADEBOX]
