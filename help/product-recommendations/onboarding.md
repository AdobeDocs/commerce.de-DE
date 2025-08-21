---
title: Onboarding
description: Erfahren Sie mehr über die Anforderungen und unterstützten Plattformen in [!DNL Product Recommendations].
exl-id: 7b8a1117-b6d5-4e5d-bb97-09f76a024cbd
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: 7d5e3faeef2fb16779d1558027a0b76ff3fe3a38
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Onboarding

Das Onboarding für [!DNL Product Recommendations] erfordert Zugriff auf die Befehlszeile des Servers und umfasst die folgenden Schritte. Wenn Sie nicht mit der Arbeit über die Befehlszeile vertraut sind, bitten Sie einen Entwickler oder Systemintegrator um Hilfe.

- [Implementierungs-Workflow](implementation-workflow.md)
- [Installieren und Konfigurieren](install-configure.md)
- [Einstellungen](settings.md)
- [Überprüfen](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/verify/)
- [Staging-Umgebung](staging-environment.md)

## Anforderungen

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Komponist 2

### Unterstützte Plattformen

- Adobe Commerce On-Premise (EE) : 2.4.4+
- Adobe Commerce on Cloud (ECE) : 2.4.4+

## Endpunkt

[!DNL Product Recommendations] kommuniziert über den Endpunkt unter `https://catalog-service.adobe.io/graphql`.

### Page Builder-Unterstützung

[!DNL Product Recommendations] können einer Seite als Page Builder-Inhaltstyp hinzugefügt werden. Informationen zum Hinzufügen der Page Builder-Unterstützung zu Produktempfehlungen finden Sie unter [ und Konfigurieren](install-configure.md).

Anweisungen [[!DNL Page Builder]  Hinzufügen von ](page-builder.md) zu [!DNL Product Recommendations] Inhalten finden Sie unter Integration[!DNL Page Builder].

### SaaS-Preisindizierung

Kunden mit Produktempfehlungen können die [SaaS-Preisindizierung](../price-index/price-indexing.md) verwenden, die schnellere Preisänderungen, Aktualisierungen und Synchronisierungszeiten ermöglicht.

### B2B-Unterstützung {#b2bsupport}

B2B-Storefronts erfordern häufig eine komplexe Logik, die die Sichtbarkeit und Preisgestaltung des Produkts für jeden Kunden oder jede Kundengruppe bestimmt. [!DNL Product Recommendations] jetzt [Unterstützung](release-notes.md) diese Funktion, indem [Kategorieberechtigungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html?lang=de), [freigegebene Kataloge](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html?lang=de) und [kundengruppenspezifische Preise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=de). Wenn Sie beispielsweise bestimmte Kategorien aus Ihrem Einzelhandelskunden-Segment ausgeblendet haben, werden einem Käufer in diesem Segment keine Empfehlungen für Produkte in diesen Kategorien angezeigt. Wenn Sie einen freigegebenen Katalog für bestimmte Kundengruppen und Unternehmen definieren, sehen diese Kunden außerdem nur Empfehlungen für Produkte, auf die sie zugreifen können. Alle empfohlenen Produkte spiegeln den korrekten kundengruppenspezifischen Preis basierend auf der Kundengruppe jedes Käufers wider.

>[!NOTE]
>
>Händler können Widgets oder Storefront-Elemente mithilfe der [Catalog Service](../catalog-service/overview.md) Storefront-API anpassen und erweitern, aber jede Anpassung liegt außerhalb des Zuständigkeitsbereichs des Support-Teams von Adobe.
