---
title: Katalogansichten
description: Erfahren Sie, was Katalogansichten sind und wie Sie sie erstellen, um Ihren Produktkatalog nach Geschäftsstruktur, Richtlinien und Preisen zu organisieren.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 76c1b81c-b456-4334-89bd-6027308cbc47
TQID: https://experienceleague.adobe.com/Jmze0Pq3kSNMIXqkkML-hmmlZnv-XKgeEgRB8Q8NZ6s
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
nudge: true
source-git-commit: 42c252f70f6ed1d7a5c1fd2832324308294da264
workflow-type: tm+mt
source-wordcount: 1317
ht-degree: 0%

---

# Katalogansichten für Merchandising-Services

Eine Katalogansicht definiert die Produkte und Preise, die ein Kunde abrufen kann. Es kombiniert Katalogquellen, Katalogschichten, Richtlinien und Preisbücher, um verschiedene Marken, Regionen, Geschäftseinheiten oder Kanäle zu unterstützen.

## Was sind Katalogansichten?

Katalogansichten definieren, wie Ihr Produktkatalog organisiert und angezeigt wird. Sie dienen als Filter, die Folgendes bestimmen:

- **Welche Produkte sichtbar sind** basierend auf der Unternehmensstruktur (Marken, Regionen, Händler)
- **Welche Preise werden angezeigt** durch verknüpfte Preisbücher
- **Filterung von Produkten** Verwendung von Richtlinien (Attribute wie Marke, Modell, Kategorie)
- **Was [Katalogquelle](catalog-sources.md) wird basierend** Attributen wie „locale“ verwendet
- **Wer kann auf die Daten der Ansicht zugreifen** über [Katalogschutz](private-catalog-view.md) und [eingeschränkte Zugriffsschlüssel](restricted-access-keys.md)

Sie können beispielsweise separate Katalogansichten erstellen für:

- Eine Marke oder Geschäftseinheit
- Eine geografische Region
- Ein Händler- oder Partnerkanal
- Ein Kundensegment mit bestimmten Preisen

## Erstellen einer Katalogansicht

Bereiten Sie vor dem Erstellen einer Katalogansicht die folgenden Elemente nach Bedarf vor:

- Eine [Katalogquelle](catalog-sources.md)
- [Richtlinien](policies.md) die Produktfilter definieren
- [Katalogebenen](catalog-layer.md) wenn Sie Produktattribute überschreiben müssen
- [Preisbücher](pricebooks.md) für die in der Ansicht angezeigten Preise
- [Schlüssel mit eingeschränktem Zugriff](restricted-access-keys.md) wenn Sie eine private Katalogansicht erstellen möchten

### Konfiguration

In diesem Abschnitt erstellen Sie eine Katalogansicht, wählen eine [Richtlinie](policies.md) und ein [Preisbuch](pricebooks.md).

1. Gehen Sie im linken Menü zu **[!UICONTROL Store setup]** und klicken Sie auf **[!UICONTROL Catalog views]**.

1. Klicken Sie auf **[!UICONTROL Create catalog view]**. &#x200B;

1. Konfigurieren Sie die Details der Katalogansicht:

   - **Name** - Geben Sie den Namen der Katalogansicht ein, z. B. `Celport`. &#x200B;
   - **Katalogquellen** - Wählen Sie die [Katalogquelle](catalog-sources.md), z. B. `en-US`.
   - **Katalogebenen** - Überprüfen Sie aufgenommene Ebenen und deren Priorität.
   - **Richtlinien** - Wählen Sie in der Dropdown-Liste die entsprechenden Richtlinien aus. Beispiel: „Marke“, „Modell“. &#x200B;Stellen Sie sicher, dass Sie bereits [eine Richtlinie erstellt haben](policies.md).

1. Wählen Sie das Preisbuch aus, das mit der Katalogansicht verknüpft werden soll.

   - **Alle verfügbaren Preislisten verwenden** - Mit dieser Option werden Preisdaten aus allen verfügbaren Preislisten abgerufen.
   - **Nur ausgewählte Preisbücher zulassen** - Diese Option zeigt das Dialogfeld **Zulässige Preisbücher hinzufügen** an. In diesem Dialog können Sie auswählen, welches Preisbuch für die Katalogansicht verwendet werden soll.
   - **Nur ein Preisbuch** - Wählen Sie diese Option, wenn nur ein Preisbuch gilt. Diese Option ist erforderlich, wenn Sie eine private Katalogansicht konfigurieren möchten, die nur auf ein Preisbuch verweisen kann. Siehe [Preisbuchbeschränkung für private Katalogansichten](private-catalog-view.md#price-book-restriction-on-private-catalog-views).
   - **Preise deaktivieren** - Diese Option ist derzeit nicht verfügbar.

   >[!NOTE]
   >
   >Eine Preisbuch-ID steuert, welche Preisfindung angefordert wird. Der Zugriff auf die Katalogansicht wird dadurch nicht eingeschränkt. Um den Zugriff einzuschränken, aktivieren Sie den Katalogschutz, um eine [private Katalogansicht“ &#x200B;](private-catalog-view.md) erstellen.

1. (Optional) Schalten Sie **[!UICONTROL Catalog Protection]** auf **[!UICONTROL Enabled]** um, um die Daten dieser Katalogansicht auf Clients mit einem gültigen signierten Token zu beschränken. Siehe [Schützen einer &#x200B;](private-catalog-view.md#protect-a-catalog-view)) für Einrichtungsschritte.

1. Klicken Sie auf **[!UICONTROL Add]** , um die Katalogansicht mit den verknüpften Preisbüchern und Richtlinien zu erstellen.

Die Seite mit den Katalogansichten wird aktualisiert, um die neue Katalogansicht anzuzeigen&#x200B;

Nachdem Sie diese Schritte ausgeführt haben, ist die Katalogansicht jetzt so konfiguriert, dass Produkte und Preise basierend auf Ihren ausgewählten Quellen und Richtlinien angezeigt werden.

### Angeben von Katalogansichten für Recommendations und Regeln zur Produkterkennung

Sie können eine Katalogansicht angeben, wenn Sie [Empfehlungseinheiten erstellen](../merchandising/recommendations/create.md) oder [Merchandisingregeln](../merchandising/rules/add.md).

## Katalogebenen

Mit Katalogschichten können Sie ausgewählte Produktattribute überschreiben, ohne die Quellkatalogdaten zu ändern. Verwenden Sie Ebenen, um Namen, Beschreibungen, Bilder, Links oder Metadaten für eine Katalogansicht anzupassen.

Siehe [Katalogebenen](catalog-layer.md).

## Erstellen einer privaten Katalogansicht

Standardmäßig ist eine Katalogansicht für Client-Programme öffentlich, die auf die GraphQL-Merchandising-API zugreifen können. Um den Zugriff einzuschränken, konfigurieren Sie eine private Katalogansicht, indem Sie **[!UICONTROL Catalog Protection]** aktivieren.

Informationen zum Schützen einer Katalogansicht und zum Überprüfen, ob der Zugriff erzwungen wird, finden Sie unter [Private Katalogansichten](private-catalog-view.md).

## Katalogansichten verwalten

Gehen Sie wie folgt vor, um die Eigenschaften vorhandener Katalogansichten zu aktualisieren oder anzuzeigen.

### Bearbeiten einer Katalogansicht

1. Suchen Sie im **[!UICONTROL Catalog views]** Arbeitsbereich die Katalogansicht.
1. Um das Menü Aktionen zu öffnen, wählen Sie (**[!UICONTROL ...]**) aus.
1. Wählen Sie **[!UICONTROL Edit]** aus, um auf den Editor für die Katalogansicht zuzugreifen.
1. Aktualisieren Sie den Namen, die Katalogquellen, die Richtlinien, die Preisbuchinformationen und die **[!UICONTROL Catalog Protection]** (einschließlich zugewiesener eingeschränkter Zugriffsschlüssel) nach Bedarf.
1. Klicken Sie auf **[!UICONTROL Save]**.

### Löschen einer Katalogansicht

1. Suchen Sie im **[!UICONTROL Catalog views]** Arbeitsbereich die Katalogansicht.
1. Um das Menü Aktionen zu öffnen, wählen Sie (**[!UICONTROL ...]**) aus.
1. Wählen Sie **[!UICONTROL Delete]** aus.
1. Bestätigen Sie den Löschvorgang.

   Wenn das Bestätigungsdialogfeld angezeigt wird, klicken Sie auf **[!UICONTROL Delete]**.

### Details zur Katalogansicht anzeigen

Diese Option bietet eine schnelle Möglichkeit, alle Parameter der Katalogansicht anzuzeigen, während Sie auf der **[!UICONTROL Catalog views]** bleiben.

Wählen Sie im Arbeitsbereich **[!UICONTROL Catalog views]** das Symbol ![Informationen](../assets/info-icon.png), damit eine Katalogansicht ihre Konfigurationsdetails anzeigt.

![Details zur Katalogansicht](../assets/catalog-view-details.png)

Von hier aus können Sie Konfigurationsdetails der Katalogansicht sehen, z. B.:

- Ansichts-ID
- Name
- Katalogquellen
- Richtlinien
- Erstellt am
- Data Modified

Einige dieser Konfigurationseinstellungen werden benötigt, wenn Sie Ihre Storefront einrichten oder die Datenerfassungs-API verwenden.

## Überblick über die Architektur

Katalogansichten sind Teil des Merchandising Services-Frameworks, das das in Adobe Commerce Foundations verwendete Website-, Store- und Store-Review-Framework durch ein flexibleres Modell ersetzt:

![[!DNL Merchandising Services] Architektur](../assets/merchandising-svcs-architecture.png)

### Funktionsweise

**1. Datenaufnahme**
Katalogdaten aus PIM, ERP und anderen Systemen werden in das Merchandising Services-Framework aufgenommen. Jede SKU enthält Gebietsschema-Informationen und Produktattribute, die Katalogansichten, Richtlinien und Gebietsschemata zugeordnet sind. Weitere Informationen zur Datenaufnahme finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/).

**2. Unified Base Catalog**
Die erfassten Daten erstellen einen einheitlichen Basiskatalog in der Katalog-Service-Datenpipeline. Durch diese zentrale Quelle werden Datenduplikate in allen Geschäftsbereichen vermieden.

**3. Katalogansichten**
Mehrere Katalogansichten stellen verschiedene Geschäftseinheiten dar (z. B. „Texas Retail“, „Texas Retail Seasonal„). Gebietsschemata, Richtlinien und Preisverzeichnisse können aus Gründen der Flexibilität über Katalogansichten hinweg gemeinsam genutzt werden.

**4. Multi-Channel-Versand**
Die gefilterten Katalogdaten werden an Ziele wie Edge Delivery Services, Marktplätze, Werbeplattformen und benutzerdefinierte Mikro-Storefronts bereitgestellt. Weitere Informationen zur Bereitstellung von Katalogdaten finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/).

Wenn eine Katalogansicht aktiviert **[!UICONTROL Catalog Protection]**, erfordert der Versand an dieses Ziel ein gültiges signiertes Token von einem zugewiesenen [eingeschränkten Zugriffsschlüssel](restricted-access-keys.md). Nicht autorisierte Anfragen werden abgelehnt, anstatt Katalogdaten zu erhalten.

### Schlüsselkomponenten

| Komponente | Zweck | Beispiel |
|---|---|---|
| **Katalogansicht** | Geschäftseinheit oder Vertriebskanal | Händlernetzwerk, regionaler Store |
| **Richtlinie** | Produktfilter basierend auf Attributen | Marke, Modell, Kategorie |
| **Gebietsschema** | Einstellung für Sprache/Region | en-US, fr-CA, es-MX |
| **Preisbuch** | Preisstruktur | Einzelhandel, Großhandel, Mitarbeiter |
| **Schlüssel für eingeschränkten Zugriff** | Anmeldedaten mit signiertem Token, die Zugriff auf eine geschützte Katalogansicht gewähren | Partner-Portal-Schlüssel, B2B-Preisschlüssel |

### Datenfluss

1. **Aufnehmen** - Produktdaten aus PIM/ERP-Systemen
2. **Prozess** - Anwenden von Katalogansichten, Richtlinien und Preisen
3. **Versand** - Bereitstellung eines gefilterten Katalogs an Storefronts, Marktplätze usw.

## Wichtigste Funktionen

| Funktion | Vorteil |
|---|---|
| **Single Base Catalog** | Eliminierung von Datenduplikaten in allen Geschäftsbereichen |
| **Flexible Preisgestaltung** | Mehrere Preisbücher pro SKU für verschiedene Kundensegmente |
| **skalierbar** | Effiziente Verwaltung von mehr als 200 Millionen SKUs |
| **Multi-Channel** | Kataloge für Storefronts, Marktplätze und Werbeplattformen bereitstellen |
| **Echtzeit-Updates** | Schnelles Aktualisieren von Katalogdaten für Promotions und Kampagnen |
| **Private Katalogansichten** | Katalogansicht mithilfe der Validierung signierter Token auf autorisierte Clients beschränken |

## Anwendungsszenarien

### Mehrmarkenkonglomerat

**Herausforderung**: Verwaltung mehrerer Marken, Länder und Sprachen<br>
**Lösung**: Einzelner Katalog mit Katalogansichten für jede Kombination aus Marke und Region

### Autoteilehändler

**Challenge**: 3.000 Händler mit den gleichen Produkten, aber unterschiedlichen Preisen<br>
**Lösung**: Ein Katalog mit händlerspezifischen Katalogansichten und Preisbüchern

### Retailer mit mehreren Standorten

**Challenge**: Unterschiedliche Preise und Lagerbestände pro Standort<br>
**Lösung**: Standortbasierte Katalogansichten mit regionsspezifischen Richtlinien

>[!NOTE]
>
>Detaillierte Informationen zur Aufnahme und Bereitstellung von Katalogdaten finden Sie unter [Entwicklerdokumentation](https://developer.adobe.com/commerce/services/optimizer/).

## Ähnliche Themen

- [Katalogquellen](catalog-sources.md) - Definieren des maßgeblichen Umfangs von Produkten, Attributen und Kategorien für das Verhalten bei Suche, Filterung und Sortierung
- [Katalogebenen](catalog-layer.md) Erfahren Sie, wie Sie Produktdaten ändern, ohne die ursprüngliche Quelle zu ändern
- [Private Katalogansichten](private-catalog-view.md) - Erstellen Sie eine private Katalogansicht, um den Zugriff auf autorisierte Clients zu beschränken
- [Schlüssel mit eingeschränktem Zugriff](restricted-access-keys.md) - Erstellen, Zuweisen und Drehen der Schlüssel zum Signieren von Token für den Katalogschutz
- [Richtlinien](policies.md) - Erstellen von Richtlinien zum Filtern von Produkten in Katalogansichten
- [Preisbücher](pricebooks.md) - Verwalten von Preisstrukturen für verschiedene Kundensegmente
