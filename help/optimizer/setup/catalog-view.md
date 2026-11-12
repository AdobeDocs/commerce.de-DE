---
title: Katalogansichten
description: Erfahren Sie, was Katalogansichten sind und wie Sie sie erstellen, um Ihren Produktkatalog nach Geschäftsstruktur, Richtlinien und Preisen zu organisieren.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und [!DNL Adobe Commerce Optimizer] (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: 76c1b81c-b456-4334-89bd-6027308cbc47
TQID: https://experienceleague.adobe.com/Jmze0Pq3kSNMIXqkkML-hmmlZnv-XKgeEgRB8Q8NZ6s
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
nudge: true
source-git-commit: d081e975b03805a0f46d5194f8c3cd46e3c86839
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%
---
# Katalogansichten für Merchandising-Services

{{$include /help/_includes/ccdm-shared/setup/catalog-view.md}}

## Katalogansichten verwalten

Verwenden Sie diese Anweisungen, um Katalogansichten zu verwalten:

- [Erstellen einer Katalogansicht](#create-a-catalog-view) - Legen Sie den Namen, die Katalogquelle, die Richtlinien und das Preisbuch fest. Geben [&#x200B; dann die Katalogansicht für Empfehlungen und Produkterkennungsregeln an](#specify-catalog-views-for-recommendations-and-product-discovery-rules) überprüfen Sie [Katalogebenen](#catalog-layers) die Produktattribute überschreiben, oder [machen Sie die Katalogansicht privat](#make-a-catalog-view-private).
- [Bearbeiten einer Katalogansicht](#edit-a-catalog-view) - Aktualisieren der Quellen, Richtlinien, Preisliste und Schutzeinstellungen.
- [Löschen einer Katalogansicht](#delete-a-catalog-view) - Entfernen einer nicht mehr benötigten Katalogansicht.
- [Details der Katalogansicht anzeigen](#view-catalog-view-details) - Überprüfen Sie die Konfiguration einer Katalogansicht in der Tabelle Katalogansichten .

### Erstellen einer Katalogansicht

Bereiten Sie vor dem Erstellen einer Katalogansicht die folgenden Elemente nach Bedarf vor:

- Eine [Katalogquelle](catalog-sources.md)
- [Richtlinien](policies.md) die Produktfilter definieren
- [Katalogebenen](catalog-layer.md) wenn Sie Produktattribute überschreiben müssen
- [Preisbücher](pricebooks.md) für die in der Ansicht angezeigten Preise
- [Schlüssel mit eingeschränktem Zugriff](restricted-access-keys.md) wenn Sie eine private Katalogansicht erstellen möchten

#### Konfiguration

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

#### Angeben von Katalogansichten für Recommendations und Regeln zur Produkterkennung

Sie können eine Katalogansicht angeben, wenn Sie [Empfehlungseinheiten erstellen](../merchandising/recommendations/create.md) oder [Merchandisingregeln](../merchandising/rules/add.md).

#### Katalogebenen

Mit Katalogschichten können Sie ausgewählte Produktattribute überschreiben, ohne die Quellkatalogdaten zu ändern. Verwenden Sie Ebenen, um Namen, Beschreibungen, Bilder, Links oder Metadaten für eine Katalogansicht anzupassen.

Siehe [Katalogebenen](catalog-layer.md).

#### Erstellen einer privaten Katalogansicht

Standardmäßig ist eine Katalogansicht für Client-Programme öffentlich, die auf die GraphQL-Merchandising-API zugreifen können. Um den Zugriff einzuschränken, konfigurieren Sie eine private Katalogansicht, indem Sie **[!UICONTROL Catalog Protection]** aktivieren.

Informationen zum Schützen einer Katalogansicht und zum Überprüfen, ob der Zugriff erzwungen wird, finden Sie unter [Private Katalogansichten](private-catalog-view.md).

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

Wählen Sie im Arbeitsbereich **[!UICONTROL Catalog views]** das Symbol ![Informationen](/help/assets/ccdm-shared/recommendations/info-icon.png), damit eine Katalogansicht ihre Konfigurationsdetails anzeigt.

![Details zur Katalogansicht](../assets/catalog-view-details.png)

Von hier aus können Sie Konfigurationsdetails der Katalogansicht sehen, z. B.:

- Ansichts-ID
- Name
- Katalogquellen
- Richtlinien
- Erstellt am
- Data Modified

Einige dieser Konfigurationseinstellungen werden benötigt, wenn Sie Ihre Storefront einrichten oder die Datenerfassungs-API verwenden.
