---
title: Verwenden  [!DNL Adobe LLM Optimizer] mit [!DNL Adobe Commerce]
description: Navigieren Sie zu Commerce-Opportunitys in LLM Optimizer, prüfen Sie die PDP- und Kataloganreicherung, stellen Sie Aktualisierungen für  [!DNL Adobe Commerce] bereit, überprüfen Sie sie in der Admin- und Storefront und erfahren Sie, wie Überschreibungen und Aufnahmevorgänge veraltet sind.
role: Admin, User
recommendations: noCatalog
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: 47348a44ff7c5f890c10594f44cae6e771be046f
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 0%

---

# Verwenden von [!DNL Adobe LLM Optimizer] mit [!DNL Adobe Commerce]

>[!IMPORTANT]
>
>Der Zugriff auf diese Integration ist eingeschränkt. Weitere Informationen erhalten Sie von Ihrem technischen Kundenbetreuer.

Nach dem [Verbinden von Commerce mit LLM Optimizer](connect-to-llmo.md) überprüfen Sie in erster Linie in der **[!DNL Adobe LLM Optimizer]**-Benutzeroberfläche die Chancen und übertragen genehmigte Änderungen in den Katalog, wenn Sie bereit sind. In diesem Artikel werden die beiden Commerce-fokussierten Optimierungstypen beschrieben. Es wird beschrieben, wie Sie **[!UICONTROL Opportunities]** verwenden, wie sich Bereitstellungsaktionen in [!DNL Adobe Commerce] verhalten und wie externe Aktualisierungen mit LLM Optimizer-Vorschlägen interagieren. Ein umfassendes Bild der Integration finden Sie unter [Integration - Übersicht](../overview.md).

## Grundlegendes zur Optimierung von Commerce in LLM Optimizer {#understand-optimizations}

Für Kataloge, die von Commerce unterstützt werden, bietet LLM Optimizer **[!UICONTROL Product Detail Page Enrichment]** und **[!UICONTROL Product Catalog Enrichment]**.

| Fokus | Wofür es gut ist |
| --- | --- |
| **[!UICONTROL Product Detail Page Enrichment]** (PDP-Anreicherung) | Vorschläge, die verbessern, wie eine Produktseite für eine KI-gesteuerte Erkennung liest, ohne das Layout Ihrer Storefront zu ersetzen. |
| **[!UICONTROL Product Catalog Enrichment]** | Vorgeschlagene **Produktname** und **Produktbeschreibung** für bestimmte Produkte, die Sie überprüfen, bei Bedarf bearbeiten und auf Ihren Commerce-Katalog anwenden können. |

Verwenden Sie **[!UICONTROL Opportunities]** , um die Liste der Produkte oder URLs zu öffnen und Vorschläge für den ausgewählten Typ zu bearbeiten.

## Navigieren in Commerce-Opportunities {#navigate-commerce-opportunities}

**So öffnen Sie Opportunitys im Zusammenhang mit Commerce:**

1. Klicken Sie in der linken Leiste auf **[!UICONTROL Opportunities]**.
1. Klicken Sie auf **[!UICONTROL Commerce Opportunity]** , um Optimierungstypen für Ihren [!DNL Adobe Commerce] anzuzeigen.
1. Wählen Sie **[!UICONTROL Product Catalog Enrichment]** oder **[!UICONTROL Product Detail Page Enrichment]** aus, je nachdem, woran Sie arbeiten möchten.

![Filter- und Optimierungstypen für Commerce-Opportunities](../assets/llmo-opportunities.png)

### Opportunity-Metriken verstehen {#opportunity-metrics}

Jede Opportunity-Ansicht fasst die Auswirkungen zusammen, sodass Sie Arbeit priorisieren können:

- **Produktseiten** oder **URLs**: Die Seiten oder Produkte, die für diesen Optimierungstyp bewertet wurden.
- **Agent-Traffic**: Besuche und Interaktionen, die von KI-Agenten initiiert werden, damit Sie wirkungsvolle Opportunities zuerst priorisieren können.

### Vorschlagsstatus verstehen {#suggestion-states}

Beide Anreicherungstypen verwenden dieselben Workflow-Ansichten:

- **[!UICONTROL Current Suggestions]**: Neue oder aktive Elemente zur Überprüfung.
- **[!UICONTROL Fixed Suggestions]**: Elemente, die Sie bereits bereitgestellt oder aufgelöst haben.
- **[!UICONTROL Ignored Suggestions]**: Elemente, die Sie absichtlich von der Aktion ausgeschlossen haben.

### Überprüfen und Bereitstellen der PDP-Anreicherung {#review-deploy-pdp}

Die PDP-Anreicherung ist für Teams gedacht, die klarere Produktseitennachrichten bei der KI-gesteuerten Erkennung wünschen und gleichzeitig das Storefront-Erlebnis für Ihre Merchandiser gestalten möchten.

**So überprüfen Sie die PDP-Anreicherung und stellen sie bereit:**

1. Öffnen Sie **[!UICONTROL Product Detail Page Enrichment]** aus **[!UICONTROL Opportunities]**.
1. Wählen Sie in der **[!UICONTROL URLs with Suggestions]** Tabelle **[!UICONTROL Current Suggestions]** aus.
1. Klicken Sie für eine URL oder SKU auf **[!UICONTROL Preview]** , um die KI-Analyse und die vorgeschlagene Anreicherung zu überprüfen.
1. Optional: Klicken Sie auf **[!UICONTROL Copy]** , um den Inhalt in einen externen Editor einzufügen, oder klicken Sie auf **[!UICONTROL Edit suggestion]** , um ihn an Ort und Stelle zu bearbeiten.
1. Optional: Wenn ein Vorschlag nicht Ihrer Strategie entspricht, verschieben Sie ihn nach **[!UICONTROL Ignored Suggestions]**.
1. Nach der Überprüfung und Genehmigung wählen Sie die Zeile für die zu aktualisierende URL oder SKU aus und klicken dann auf **[!UICONTROL Deploy optimizations]** und bestätigen.

Nach der Bereitstellung werden Vorschläge mit einem Optimierungsstatus in LLM Optimizer **[!UICONTROL Fixed Suggestions]**.

>[!NOTE]
>
>Die Bereitstellung der PDP-Anreicherung erfordert das abgeschlossene Onboarding **Optimieren bei Edge** in LLM Optimizer. Wenn das Onboarding unvollständig ist, werden Sie von der Benutzeroberfläche aufgefordert, die Einrichtung vor der Bereitstellung abzuschließen.

### Überprüfen und Bereitstellen der Produktkataloganreicherung {#review-deploy-catalog}

Die Kataloganreicherung ist für Teams gedacht, die Produktnamen und lange Beschreibungen direkt in Commerce mit Vorschlägen versehen möchten, die Sie vor dem Speichern überprüfen können.

**So überprüfen Sie die Anreicherung des Produktkatalogs und stellen sie bereit:**

1. Öffnen Sie **[!UICONTROL Product Catalog Enrichment]** aus **[!UICONTROL Opportunities]**.
1. Wählen Sie in der **[!UICONTROL URLs with Suggestions]** Tabelle **[!UICONTROL Current Suggestions]** aus.
1. Klicken Sie auf das Erweiterungssteuerelement für die URL- oder SKU-Zeile, um die vorgeschlagenen Aktualisierungen **Produktname** und **Produktbeschreibung** anzuzeigen.
1. Optional: Klicken Sie auf das Bearbeitungssymbol, um den vorgeschlagenen Namen oder die vorgeschlagene Beschreibung vor der Bereitstellung anzupassen.
1. Optional: Wenn ein Vorschlag nicht Ihrer Strategie entspricht, verschieben Sie ihn nach **[!UICONTROL Ignored Suggestions]**.
1. Nach der Überprüfung und Genehmigung wählen Sie die Zeile für die zu aktualisierende URL oder SKU aus und klicken dann auf **[!UICONTROL Deploy optimizations]** und bestätigen.

Genehmigte Name- und Beschreibungsänderungen werden wie andere Produktaktualisierungen im [!DNL Adobe Commerce] gespeichert.

>[!IMPORTANT]
>
>Bereitstellung als Änderung des Produktionskatalogs behandeln. Verwenden Sie Ihre üblichen Verfahren für Änderungskontrolle, Staging und Qualitätssicherung. Bereitstellung erst, nachdem sich Merchandising- und SEO-Stakeholder auf die endgültige Kopie geeinigt haben.

Nach der Bereitstellung werden Vorschläge mit dem Status **Angewendet** in **[!UICONTROL Fixed Suggestions]** verschoben.

## Überprüfen von Aktualisierungen im Commerce Admin {#verify-in-admin}

**So überprüfen Sie die bereitgestellte Kataloganreicherung:**

1. Melden Sie sich bei [!DNL Adobe Commerce]Admin **an**.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Verwenden Sie Filter und den **Store-Ansicht**-Selektor nach Bedarf (z. B. **[!UICONTROL Default Store View]**) und suchen Sie nach der **SKU**.
1. Öffnen Sie das Produkt im Bearbeitungsmodus.

   Das Produktformular zeigt den angereicherten **Produktnamen** an.

   ![Feld „Produktname“ nach der LLM Optimizer-Anreicherung](../assets/llmo-admin-name.png)

1. Optional: Wählen Sie **[!UICONTROL Override LLM Optimizer provided Product Name]** aus, wenn Sie stattdessen einen manuell eingegebenen Namen beibehalten möchten.

Manuelle Überschreibungen beeinflussen, wie Opportunities mit dem Katalog synchronisiert bleiben; siehe [Manuelle Überschreibungen in Admin](#manual-override-in-the-admin).

1. Erweitern Sie den Abschnitt **[!UICONTROL Content]** und suchen Sie das Feld **Beschreibung**.

   Die angereicherte Beschreibung wird angezeigt, wenn Sie Änderungen der Beschreibung bereitgestellt haben.

   ![Beschreibungsfeld nach der LLM Optimizer-Anreicherung](../assets/llmo-admin-description.png)

1. Optional: Wählen Sie **[!UICONTROL Override LLM Optimizer provided Description]** aus, wenn Sie stattdessen eine manuell eingegebene Beschreibung beibehalten möchten.

## Überprüfen von Aktualisierungen in der Storefront {#verify-storefront}

Suchen Sie die SKU in Ihrer Storefront und öffnen Sie die PDP. Bestätigen Sie, dass **name** und alle Bereiche, die die lange **description“**, Ihre Genehmigung widerspiegeln. Bestätigen Sie auch alle nachgelagerten Kanäle, die dieselben Katalogattribute verwenden, sofern für Ihren Rollout relevant.

<!--
## PDP enrichment rollback {#pdp-rollback}

If your project includes PDP enrichment opportunities, **rollback** behavior may support **bulk** or **per-URL** actions, depending on your LLM Optimizer release. Follow the in-product options for rollback. For **[!UICONTROL Product Catalog Enrichment]**, undoing a name or description in Commerce is effectively a new catalog edit or a follow-up opportunity, not a separate undo control in the Admin unless your team implements one.
-->

## Überschreibungen, Aufnahme und veraltete Opportunitys {#overrides-ingestion}

Nachdem LLM Optimizer den Namen oder die Beschreibung eines Produkts aktualisiert hat, können andere Aufnahmesysteme wie REST-API-Aufrufe, CSV-Importe, PIM-Feeds oder ähnliche Prozesse dieselben Felder ändern. In den folgenden Abschnitten wird beschrieben, was in diesem Fall geschieht.

### Die Aufnahme sendet den ursprünglichen Katalogwert erneut

Wenn ein externer Prozess den ursprünglichen Namen oder die ursprüngliche Beschreibung (den Wert, der vor der Bereitstellung von LLM Optimizer vorhanden war) schreibt, berücksichtigt Commerce weiterhin den von LLM Optimizer bereitgestellten Wert für dieses Feld gemäß den Integrationsregeln. Die Opportunity wird möglicherweise nicht allein aufgrund dieser Aufnahme automatisch rückgängig gemacht.

### Aufnahme sendet einen neuen Wert

Wenn der externe Prozess einen neuen Wert sendet, der nicht nur eine Wiederholung des Pre-LLM Optimizer-Textes ist - z. B. das Umbenennen von „Red Shoes“ in „Iconic Red Shoes“ -, wird dieser neue Katalogwert berücksichtigt und die zugehörige LLM Optimizer-Opportunity wird in LLM Optimizer normalerweise als *Stale* markiert, da der Live-Katalog nicht mehr mit dem Vorschlagskontext übereinstimmt.

### Manuelle Überschreibung in der Admin {#manual-override-in-the-admin}

Wenn Sie den Produktnamen oder die Beschreibung im [!DNL Adobe Commerce] (*) manuell*:

- Der *Admin*-Wert wird als Aufzeichnungssystem für diese manuelle Änderung gewonnen.
- Die LLM Optimizer-Opportunity ist als *gekennzeichnet*.
- In LLM Optimizer kehrt die Benutzeroberfläche für diese Opportunity in den Originalzustand zurück, sodass Sie einen neuen Basisplan erstellen oder einen neuen Vorschlag akzeptieren können, wenn die Analyse erneut ausgeführt wird.

Diese Regeln helfen Ihnen zu ermitteln, ob LLM Optimizer, Aufnahme-Feeds oder *Admin*-Bearbeitungen autorisierend sind, wenn mehrere Kanäle dieselbe SKU berühren.

## Best Practices

- **Dokumentsystemeigentümerschaft** für Produktname und -beschreibung, damit PIM- oder Feed-Aufträge nicht unbeabsichtigt mit den Erwartungen von LLM Optimizer kollidieren.
- **Abstimmung mit SEO- und Brand-Teams** vor der Massenbereitstellung von Titeln oder Beschreibungen.
- **Erneut synchronisieren** oder **erneut analysieren** nach wichtigen Katalogimporten, damit die Opportunities den aktuellen Katalogstatus widerspiegeln.

## In der Demo ausprobieren

Verwenden Sie die Demo-Umgebung von Frescopa, um beide Commerce-Opportunity-Typen in Aktion zu sehen:

- [Demo zur Produktkataloganreicherung anzeigen](https://play.llmo.now/org/demo-org/opportunities/commerce-product-catalog-enrichment/e5f2a854-7477-421c-820f-74d5dd595647?siteId=9ae8877a-bbf3-407d-9adb-d6a72ce3c5e3)
- [Demo zur Anreicherung von Produktdetailseiten anzeigen](https://play.llmo.now/org/demo-org/opportunities/commerce-product-page-enrichment/4e8b0428-0893-4864-a00e-fc1d77fb3372?siteId=9ae8877a-bbf3-407d-9adb-d6a72ce3c5e3)

## Verwandte Themen

- [Adobe Commerce mit LLM Optimizer verbinden](connect-to-llmo.md)
- [Übersicht über die Integration](../overview.md)
- [Integrationsbeschränkungen und -grenzen](../boundaries-limits.md)
