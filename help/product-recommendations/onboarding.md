---
title: Onboarding
description: Erfahren Sie mehr über die Anforderungen und unterstützten Plattformen in [!DNL Product Recommendations].
exl-id: 7b8a1117-b6d5-4e5d-bb97-09f76a024cbd
TQID: https://experienceleague.adobe.com/FLrOFe-Lwe7i3dOwCISflVGEv2MIkXmmE-NqTvpaY-0
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 418
ht-degree: 0%

---

# Onboarding

>[!IMPORTANT]
>
>**Product Recommendations ist kein HIPAA-fähiger Service.** Aktivieren oder verwenden Sie keine Produktempfehlungen in Adobe Commerce-Implementierungen, die das HIPAA-fähige Angebot verwenden oder anderweitig geschützte Gesundheitsinformationen (PHI) verarbeiten. Product Recommendations ist Teil der Commerce SaaS-Services, die derzeit als nicht HIPAA-fähig eingestuft sind.
>
>Weitere Informationen dazu, welche Adobe Commerce-Funktionen HIPAA-fähig sind und welche Services nicht mit PHI verwendet werden dürfen, finden Sie unter [HIPAA-Bereitschaft für Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) und [Vorgänge](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/operations#adobe-commerce-services).

Das Onboarding für [!DNL Product Recommendations] erfordert Zugriff auf die Befehlszeile des Servers und umfasst die folgenden Schritte. Wenn Sie nicht mit der Arbeit über die Befehlszeile vertraut sind, bitten Sie einen Entwickler oder Systemintegrator um Hilfe.

- [Implementierungs-Workflow](implementation-workflow.md)
- [Installieren und Konfigurieren](install-configure.md)
- [Einstellungen](settings.md)
- [Überprüfen](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/verify/)
- [Staging-Umgebung](staging-environment.md)

## Anforderungen

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3 oder 8.4
- Komponist 2

### Unterstützte Plattformen

- Adobe Commerce On-Premise (EE) : 2.4.4+
- Adobe Commerce on Cloud (ECE) : 2.4.4+

## Endpunkt

[!DNL Product Recommendations] kommuniziert über den Endpunkt unter `https://catalog-service.adobe.io/graphql`.

### Page Builder-Unterstützung

[!DNL Product Recommendations] können einer Seite als Page Builder-Inhaltstyp hinzugefügt werden. Informationen zum Hinzufügen der Page Builder-Unterstützung zu Produktempfehlungen finden Sie unter [ und Konfigurieren](install-configure.md).

Anweisungen [[!DNL Page Builder]  Hinzufügen von [!DNL Product Recommendations] zu [!DNL Page Builder] Inhalten finden Sie unter Integration](page-builder.md).

### SaaS-Preisindizierung

Kunden mit Produktempfehlungen können die [SaaS-Preisindizierung](../price-index/price-indexing.md) verwenden, die schnellere Preisänderungen, Aktualisierungen und Synchronisierungszeiten ermöglicht.

### B2B-Unterstützung {#b2bsupport}

B2B-Storefronts erfordern häufig eine komplexe Logik, die die Sichtbarkeit und Preisgestaltung des Produkts für jeden Kunden oder jede Kundengruppe bestimmt. [!DNL Product Recommendations] jetzt [Unterstützung](release-notes.md) diese Funktion, indem [Kategorieberechtigungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [freigegebene Kataloge](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html) und [kundengruppenspezifische Preise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). Wenn Sie beispielsweise bestimmte Kategorien aus Ihrem Einzelhandelskunden-Segment ausgeblendet haben, werden einem Käufer in diesem Segment keine Empfehlungen für Produkte in diesen Kategorien angezeigt. Wenn Sie einen freigegebenen Katalog für bestimmte Kundengruppen und Unternehmen definieren, sehen diese Kunden außerdem nur Empfehlungen für Produkte, auf die sie zugreifen können. Alle empfohlenen Produkte spiegeln den korrekten kundengruppenspezifischen Preis basierend auf der Kundengruppe jedes Käufers wider.

>[!NOTE]
>
>Händler können Widgets oder Storefront-Elemente mithilfe der [Catalog Service](../catalog-service/overview.md) Storefront-API anpassen und erweitern, aber jede Anpassung liegt außerhalb des Zuständigkeitsbereichs des Support-Teams von Adobe.
