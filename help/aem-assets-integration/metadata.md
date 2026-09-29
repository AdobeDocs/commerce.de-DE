---
title: Commerce-Metadaten in AEM Assets
description: Erfahren Sie mehr über den Commerce-Namespace, das Metadatenschema und den Alternativtext, den die AEM Assets-Integration in Ihre AEM Assets-Autorenumgebung einfügt.
feature: CMS, Media, Integration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: da3860b0-d637-47df-bef0-273751180266
    internal-label: Digital asset management
source-git-commit: 7950f5d171b35054be42ca60d19bafcf43c53cd6
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%
---
# Commerce-Metadaten in AEM Assets

Commerce-Metadaten sind der Vertrag zwischen AEM Assets und Commerce. Dadurch wird Commerce mitgeteilt, welche Assets für Commerce vorgesehen sind, zu welchen Produkten sie gehören und wie sie verwendet oder angezeigt werden sollen. Diese Metadaten ermöglichen es der AEM Assets-Integration, Asset-Dateien korrekt zuzuordnen und zu synchronisieren.

Commerce-Metadaten ermöglichen die folgenden Funktionen:

* **Markieren Sie ein Asset über** Feld `commerce:isCommerce` als Commerce-geeignet.
* **Verknüpfen eines Assets mit einer oder mehreren Produkt-SKUs** über das `commerce:skus` Feld.
* **Definieren, wie das Asset in Commerce angezeigt wird** über die Felder `commerce:roles` und `commerce:positions` .
* **Fügen Sie Commerce-spezifischen Alt-Text hinzu, der von der Store** Ansicht über die Felder `commerce:altTextStoreViews` und `commerce:altTextValues` verschlüsselt wird.
* **Zeigen Sie diese Felder in der AEM Assets-Eigenschaften** Benutzeroberfläche über eine **[!UICONTROL Commerce]** Registerkarte und ein Schemaformular an.

Informationen zum Konfigurieren dieser Ressourcen in Ihrem AEM-Projekt finden Sie unter [Konfigurieren des AEM Assets-Projekts](get-started/configure-aem.md). Im Rest dieses Themas wird beschrieben, wie die Metadaten bereitgestellt werden.

## AEM Commerce Assets-Commerce-Paketinhalte

Adobe stellt das `assets-commerce` AEM Commerce-Code-Paket bereit, um Commerce-Namespaces und Metadatenschema-Ressourcen zur Experience Manager Assets as a Cloud Service-Konfiguration hinzuzufügen.

Dieser Paket-Code fügt die folgenden Ressourcen zur Authoring-Umgebung von AEM Assets hinzu:

* Ein [benutzerdefinierter Namespace](https://github.com/ankumalh/assets-commerce/blob/main/ui.config/jcr_root/apps/commerce/config/org.apache.sling.jcr.repoinit.RepositoryInitializer~commerce-namespaces.cfg.json), der zur Identifizierung von Commerce-bezogenen Eigenschaften `Commerce`.

  * Ein benutzerdefinierter Metadatentyp `commerce:isCommerce` mit der Bezeichnung `Eligible for Commerce`, um mit einem Adobe Commerce-Projekt verknüpfte Commerce-Assets zu taggen.

  * Ein benutzerdefinierter Metadatentyp `commerce:skus` und eine entsprechende UI-Komponente, um eine **[!UICONTROL Product Data]** Eigenschaft hinzuzufügen. Produktdaten enthalten die Metadateneigenschaften zum Verknüpfen eines Commerce-Assets mit Produkt-SKUs.

    ![Benutzerdefiniertes Produktdaten-Benutzeroberflächen-Steuerelement](assets/aem-commerce-sku-metadata-fields-from-template.png){width="600" zoomable="yes"}

  * Ein benutzerdefinierter Metadatentyp `commerce:roles` und `commerce:positions` Attribute, die zeigen, wie das Asset in Commerce visualisiert wird. Die vier Standardrollen (`image`, `small_image`, `thumbnail` und `swatch_image`) werden weiterhin unterstützt. Ab AEM Assets Integration Extension-Version 1.4.6 können Sie auch eine benutzerdefinierte Bildrolle in `commerce:roles` festlegen, z. B. `hero` oder `custom_role_1`, um eine Rolle zu synchronisieren, die Commerce nicht standardmäßig definiert. Siehe [Benutzerdefinierter automatischer Abgleich](synchronize/custom-match.md) für die Aufnahme von benutzerdefinierten Bildrollen.

    >[!NOTE]
    >
    >Commerce erstellt automatisch ein fehlendes `media_image` für eine benutzerdefinierte Rolle.

  * Metadaten des Alternativtext-Multifelds (_[!UICONTROL Alt texts]_), damit Bearbeiter für jeden Code der Commerce-Store-Ansicht Alternativtext eingeben können. Das Mehrfachfeld bleibt in zwei indexorientierten `String[]` bestehen:

    * `commerce:altTextStoreViews` - Ansichtscode für jede Zeile speichern.
    * `commerce:altTextValues` - Abgleichen von Alternativtext am selben Index wie bei jedem Eintrag in `commerce:altTextStoreViews`.

    App Builder-Implementierungen mit einem [externen Matcher](synchronize/custom-match.md){target=_blank} können diese Eigenschaften beim Transformieren von Asset-Payloads abfangen. Dies ändert nichts daran, wie Produktbilder im Katalog zugewiesen werden oder welchen Umfang sie haben. Siehe [Lokalisierter ALT-Text in AEM Assets-](#localized-alt-text-in-aem-assets-metadata).

* Ein Metadatenschema-Formular mit einer Registerkarte &quot;Commerce&quot;, das die `Eligible for Commerce`- und `Product Data` für das Tagging von Commerce-Assets enthält. Das Formular bietet außerdem Optionen zum Ein- oder Ausblenden der `roles`- und `position` in der AEM Assets-Benutzeroberfläche.

  Registerkarte ![Commerce für das Metadatenschema-Formular von AEM Assets](assets/assets-configure-metadata-schema-form-editor.png){width="600" zoomable="yes"}

* Ein [Beispiel für getaggte und genehmigte Commerce](https://github.com/ankumalh/assets-commerce/blob/main/ui.content/src/main/content/jcr_root/content/dam/wknd/en/activities/hiking/equipment_6.jpg/.content.xml)Assets`equipment_6.jpg` zur Unterstützung der anfänglichen Asset-Synchronisierung. Nur genehmigte Commerce-Assets können von AEM Assets mit Adobe Commerce synchronisiert werden.

>[!NOTE]
>
> Weitere Informationen zum {[}AEM Commerce-Package-Code&rbrace; finden Sie auf &#x200B;](https://github.com/ankumalh/assets-commerce) Seite zu GitHub **&#x200B;**

## Lokalisierter ALT-Text in AEM Assets-Metadaten

Das _[!UICONTROL Alt texts]_&#x200B;Multifield ist im Metadaten-Editor für AEM Assets-Assets auf der Registerkarte **[!UICONTROL Commerce]**&#x200B;verfügbar, wenn Sie ein geeignetes Bild bearbeiten.

>[!IMPORTANT]
>
> Das Verhalten der Pre-Store-Ansicht gilt nur für Alternativtext. Die AEM Assets-Integration synchronisiert nicht verschiedene Produktbilder pro Adobe Commerce-Store-Ansicht. Produktbilder aus AEM werden weiterhin mit Commerce synchronisiert. Dies entspricht dem Verhalten bei der Galeriezuweisung wie vor dieser Version.

Das Multifield enthält eine Zeile pro Commerce-Store-Ansicht. Jede Zeile hat zwei Eingaben:

* **[!UICONTROL Store View Code]** - Die Kennung der Store-Ansicht (z. B. `default` oder `en_US`).

* **[!UICONTROL Alt Text]** - Alternativtext für diese Store-Ansicht, begrenzt auf 255 Zeichen.

Wählen Sie **[!UICONTROL Add]** aus, um weitere Zeilen für zusätzliche Shop-Ansichten hinzuzufügen. Um eine Zeile zu entfernen, klicken Sie auf das Symbol **[!UICONTROL Delete]** in dieser Zeile, um sie zu entfernen.

![Mehrfachfeld „Alt-Texte“ mit Code für Store-Ansicht und Eingabe von Alt-Text](assets/aem-alt-texts.png){width="600" zoomable="yes"}

Beim Speichern blockiert die Client-seitige Validierung die Übermittlung, wenn eine Zeile einen leeren _[!UICONTROL Store View Code]_&#x200B;hat oder wenn zwei Zeilen denselben Code für die Store-Ansicht verwenden (ignoriert Groß-/Kleinschreibung).

Alternativtexteinträge werden in JCR-Asset-Metadaten als zwei indexorientierte `String[]` beibehalten:

* `commerce:altTextStoreViews`: Ansichtscode für jede Zeile speichern.
* `commerce:altTextValues`: Abgleichen von ALT-Text am selben Index wie bei jedem Eintrag in `commerce:altTextStoreViews`.

Wenn diese Assets mit Adobe Commerce synchronisiert werden, wird Alt-Text für die Einzelspeicheransicht in die Produktmediensammlung für die entsprechenden Speicheransichts-Codes geschrieben. Die zugrunde liegende Bildzuordnung bleibt unverändert.

Beispiel für Metadatenwerte:

```text
commerce:altTextStoreViews = ["en_US", "fr_FR"]
commerce:altTextValues = ["Running shoe", "Chaussure de course"]
```

Wenn diese Assets mit Adobe Commerce synchronisiert werden, wird jeder Alt-Text-Wert in das Standardbild-**[!UICONTROL Label]**-Feld von Commerce für den entsprechenden Code für die Store-Ansicht geschrieben. Die Integration füllt keine vom Kunden erstellte `alt_text`-Datenbankspalte.

Alt-Text wird pro Shop-Ansicht lokalisiert, aber die zugrunde liegende Produktbildzuweisung und Galerie-Zuordnung bleiben unverändert. Eine einzelne Bildzuweisung gilt weiterhin entsprechend dem bestehenden Verhalten in der Commerce-Galerie.
