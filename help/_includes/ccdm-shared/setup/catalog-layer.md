---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 0%
---
Mit Katalogschichten können Sie Produktdaten ändern, ohne die ursprünglichen Quelldaten zu ändern. Ebenen ändern Produktattribute wie Namen, Beschreibung, Bilder, Links und Metadaten, indem über dem Basiskatalog eine Ebene erstellt wird. Ihre ursprünglichen Produktdaten bleiben intakt, sodass Sie Produkte sicher anpassen und Änderungen jederzeit rückgängig machen können.

![Katalogebenen](/help/assets/ccdm-shared/setup/catalog-layers.png)

## Zugriff auf den Arbeitsbereich Katalogansichten

Katalogebenen können über den Arbeitsbereich *Katalogansichten* durch Auswahl einer Katalogansicht verwaltet werden. Wie Sie den Arbeitsbereich öffnen, hängt vom verwendeten Produkt ab:

- **Adobe Commerce Admin** (Adobe Commerce as a Cloud Service) - Wählen Sie *Katalog* > **Katalogansichten**.
- **Adobe Commerce Optimizer Studio**—Wählen Sie *Store-Setup* > **Katalogansichten**.

## Funktionsweise von Katalogebenen

Wenn ein Kunde Ihre Storefront aufruft, kombiniert das System Ihre Basiskatalogdaten mit aktiven Katalogebenen, um die endgültigen Produktinformationen anzuzeigen. Der Prozess läuft wie folgt ab:

1. **Ebenenanwendung** - Wenn eine Anfrage mit einer Kanal-ID und einer Umgebungs-ID erfolgt, ruft der Store-Service die entsprechende Katalogansicht ab.

1. **Datenzusammenführung** - Das System wendet Katalogschichten auf Produktdaten basierend auf der Prioritätsreihenfolge der Schicht an.

1. **Feldbehandlung** - Verschiedene Feldtypen werden unterschiedlich verarbeitet:

   * **Felder überschreiben** - Textfelder wie Name, Beschreibung und Meta-Titel werden durch Ebenenwerte ersetzt, wobei die Ebene mit der höheren Priorität Vorrang hat.
   * **Felder zusammenführen** - Array-Felder wie Bilder, Links und Attribute werden aus mehreren Ebenen kombiniert, um eine einheitliche Antwort zu erzielen.

1. **Prioritätsauflösung** - Das Reihenfolgenfeld bestimmt, welche Ebene Vorrang hat. Wenn mehrere Ebenen dasselbe Feld ändern, hat die Ebene mit der höheren Ordnungszahl eine höhere Priorität (z. B. ist Reihenfolge 10 die höchste).

## Anwendungsfälle für Katalogebenen

Katalogebenen werden häufig für Folgendes verwendet:

* **SEO-Optimierung** - Überschreiben von Produktmetadaten-Titeln und -Beschreibungen basierend auf KI-Empfehlungen von [Sites Optimizer](../manage-results/opportunities.md).
* **Saisonale Kampagnen** - Aktualisieren Sie Produktnamen, Beschreibungen oder Bilder für Werbeaktionen vorübergehend, ohne die Quelldaten zu ändern.
* **Regionale Anpassung** - Zeigt verschiedene Produktinformationen basierend auf geografischem Standort oder Sprache an.
* **A/B-Tests** - Testen Sie verschiedene Produktpräsentationen, um die Konversionsraten zu optimieren.
* **Verwaltung mehrerer Marken** - Passen Sie Produktattribute für verschiedene Ansichten des Markenkatalogs an.
* **Produktvisualisierungen** - Wenden Sie Produktbilder aus AEM Assets als Ebene über Ihrem Basiskatalog an.

## AEM-Assets-Ebene

Diese Ebene enthält Produktbilder, die aus AEM Assets synchronisiert wurden. Wie andere Katalogebenen wird es über die [Product Layers-API](https://developer.adobe.com/commerce/services/reference/rest/#tag/Product-Layers){target=_blank} gefüllt. Der Assets Integration Service transformiert AEM-Asset-Metadaten und Bereitstellungs-URLs in das API-Format und sendet die Daten automatisch, wenn Assets in AEM Assets genehmigt wurden.

Die Integration unterstützt eine Quelle pro Mandant (ein Gebietsschema + eine Ebene).

### Funktionsweise der AEM-Assets-Ebene

1. **Automatische Erstellung**: Die Ebene wird erstellt, wenn die AEM Assets-Integration für Ihre Instanz konfiguriert ist.

1. **Bildsynchronisierung**: Wenn Assets in AEM Assets genehmigt werden, transformiert der Assets Integration Service die Asset-Daten und aktualisiert die `AEM-Assets` über die Produktebenen-API.

1. **Ebenenzuweisung**: Weisen Sie die `AEM-Assets` Katalogansicht zu, in der AEM Assets-Bilder angezeigt werden sollen.

### Zuweisen der AEM-Assets-Ebene zu einer Katalogansicht

>[!CAUTION]
>
> Weisen Sie die AEM-Assets-Ebene Ihrer Katalogansicht zu. Wenn die Ebene nicht zugewiesen ist, werden Produktbilddaten unerwartet überschrieben.

So zeigen Sie AEM Assets-Bilder in Ihrer Storefront an:

1. Wählen Sie im Arbeitsbereich Katalogansichten die Katalogansicht aus, auf die Sie die Ebene anwenden möchten.

1. Suchen Sie im Abschnitt Katalogebenen die Ebene **AEM-Assets**.

1. Um die Ebene für diese Katalogansicht zu aktivieren, aktivieren Sie sie.

1. Klicken Sie auf **[!UICONTROL Save]** , um die Änderungen anzuwenden.

Nach der Zuweisung geben die Merchandising-Services- und Storefront-GraphQL-APIs sowohl Basiskatalogbilder als auch AEM Assets-Bilder für Produkte zurück.

## Hinzufügen einer Katalogebene über die Datenaufnahme

Sie können Ihren Produkten während der Datenaufnahme Katalogebenen hinzufügen. Diese Methode eignet sich ideal für Massenvorgänge oder automatisierte Workflows. Sie importieren Katalogebenen mit der Aufnahme-API, aber [&#x200B; Festlegen der Reihenfolge &#x200B;](#manage-layer-priorities) Ebenen erfolgt über die Benutzeroberfläche.

**Voraussetzungen:**

* API-Anmeldeinformationen mit Berechtigung für den Zugriff auf den Datenaufnahme-Service
* Produkt-SKUs, die bereits im Basiskatalog vorhanden sind

**Schritte:**

1. Bereiten Sie Ihre Ebenendaten im erforderlichen Format mit den Produktattributen vor, die Sie ändern möchten.

1. Verwenden Sie den API-Endpunkt „Product Layers“, um die Ebenendaten aufzunehmen.

1. Überprüfen Sie, ob die Ebene erfolgreich aufgenommen wurde, indem Sie die Konfiguration der Katalogansicht überprüfen.

Detaillierte API-Spezifikationen und Payload-Beispiele finden Sie unter [Produktebenen](https://developer.adobe.com/commerce/services/reference/rest/#tag/Product-Layers){target=_blank} in der Entwicklerdokumentation.

## Manuelles Hinzufügen einer Katalogebene in der Benutzeroberfläche

Die Benutzeroberfläche für die Katalogansicht ermöglicht die manuelle Erstellung und Verwaltung von Ebenen. Dies ist besonders für Integrationen wie Sites Optimizer nützlich, die KI-gestützte Empfehlungen generieren. Verwenden Sie für Massenschichtvorgänge die Datenaufnahme-API-Methode [oben beschrieben](#add-a-catalog-layer-via-data-ingestion).

Wenn in Ihrer Katalogansicht keine Sites Optimizer-Ebene vorhanden ist, erstellt die Funktion zur automatischen Fehlerbehebung in Sites Optimizer automatisch eine Ebene und weist ihr die höchste Priorität (höchste Zahl) zu. Wenn Sie diese Ebene löschen, wird sie bei der nächsten Ausführung der Funktion zur automatischen Fehlerbehebung in Sites Optimizer neu erstellt und die bestehenden Ebenen werden in niedrigere Ordnungszahlen verschoben. Wenn die Sites Optimizer-Ebene bereits mit einer anderen Bestellnummer vorhanden ist, ändert die Funktion für die automatische Fehlerbehebung ihre Priorität nicht.

**So erstellen Sie eine manuelle Ebene:**

1. Wählen Sie im Arbeitsbereich **[!UICONTROL Catalog views]** die Katalogansicht aus, auf die Sie die Ebene anwenden möchten.

1. Klicken Sie im Abschnitt Katalogebenen auf **Katalogebene hinzufügen**.

1. Konfigurieren Sie die Ebeneneigenschaften:

   * **Ebenenname** - Geben Sie einen beschreibenden Namen ein, um den Zweck der Ebene zu identifizieren.
   * **Produkte** - Wählen Sie die Produkte aus, für die diese Ebene gilt.
   * **Attribute** - Wählen Sie aus, welche Produktattribute geändert werden sollen (Name, Beschreibung, Bilder, Meta-Tags usw.).
   * **Werte** - Geben Sie die neuen Werte für jedes ausgewählte Attribut ein.

1. Klicken Sie auf **[!UICONTROL Save]** , um die Ebene zu erstellen.

Die neue Ebene wird der Katalogansicht hinzugefügt und automatisch der nächsten verfügbaren Bestellnummer zugewiesen.

## Vorschau von Ebeneneffekten


Bevor Sie Ebenen aktivieren oder Prioritäten ändern, können Sie sich eine Vorschau ansehen, wie sie sich auf Produktdaten auswirken.

**Vorschau von Ebenenänderungen anzeigen:**

1. Wählen Sie im Arbeitsbereich **[!UICONTROL Catalog views]** die Katalogansicht mit den Ebenen aus, die Sie in der Vorschau anzeigen möchten.

1. Wählen Sie im Abschnitt Katalogebenen ein bestimmtes Produkt aus oder verwenden Sie die Vorschaufunktion.

1. Überprüfen Sie die kombinierten Produktdaten, die zeigen, wie Ebenen die Grundkatalogwerte ändern.

1. Nehmen Sie nach Bedarf Anpassungen am Ebeneninhalt oder an der Prioritätsreihenfolge vor.

## Verwalten der Aktivierung und Löschung von Ebenen

Sie können Katalogebenen aktivieren oder deaktivieren, ohne sie zu löschen, sodass Sie steuern können, wann bestimmte Anpassungen angewendet werden.

**So aktivieren oder deaktivieren Sie eine Ebene:**

1. Wählen Sie im Arbeitsbereich **[!UICONTROL Catalog views]** die Katalogansicht aus, die die Ebene enthält.

1. Suchen Sie im Abschnitt Katalogebenen die Ebene, die Sie umschalten möchten.

1. Klicken Sie auf den Umschalter Aktivierung , um die Ebene zu aktivieren oder zu deaktivieren.

   * **Aktiv** - Die Ebene wird auf Produktdaten angewendet.
   * **Inaktiv** - Die Ebene wird beibehalten, aber nicht auf Produktdaten angewendet.

1. Die Änderung wird sofort in Ihrer Storefront wirksam.

**So löschen Sie eine Ebene:**

Verwenden Sie die Datenerfassungs-API, um [eine Katalogschicht zu löschen](https://developer.adobe.com/commerce/services/reference/rest/#operation/deleteProductLayers){target=_blank}.

## Verwalten von Ebenenprioritäten

Die Reihenfolge, in der Ebenen angewendet werden, bestimmt, welche Werte in Ihrer Storefront angezeigt werden, wenn mehrere Ebenen dasselbe Produktattribut ändern. Durch die Verwaltung von Prioritäten wird sichergestellt, dass die richtigen Daten angezeigt werden.

**Grundlegendes zur Prioritätsreihenfolge:**

* Jeder Ebene wird eine Ordnungsnummer (1, 2, 3 usw.) zugewiesen
* Höhere Zahlen geben eine höhere Priorität an und überschreiben alle anderen Ebenen
* Wenn mehrere Ebenen dasselbe Feld ändern, hat die Ebene mit der höheren Ordnungszahl Vorrang
* Priorität gilt nur für das Überschreiben von Feldern (Name, Beschreibung, Meta-Tags)
* Felder (Bilder, Links, Attribute) verbinden Daten aus allen Ebenen

**So ordnen Sie die Ebenenprioritäten neu an:**

1. Wählen Sie im Arbeitsbereich **[!UICONTROL Catalog views]** die Katalogansicht mit den Ebenen aus, die Sie neu anordnen möchten.

1. Suchen Sie im Abschnitt Katalogebenen die Ebene, die Sie verschieben möchten.

1. Ziehen Sie die Ebene per Drag-and-Drop, um ihre Position zu ändern, oder verwenden Sie die Steuerelemente zur Neuanordnung.

1. Das System aktualisiert die Bestellnummern automatisch auf der Grundlage der neuen Reihenfolge.

1. Klicken Sie auf **[!UICONTROL Save]** , um die neue Prioritätsreihenfolge anzuwenden.

>[!IMPORTANT]
>
>Änderungen an der Ebenenpriorität werden sofort wirksam und wirken sich auf das aus, was Kunden in Ihrer Storefront sehen. Überprüfen Sie vor dem Speichern die Vorschau, um sicherzustellen, dass die richtigen Werte angewendet werden.

## Best Practices

Befolgen Sie beim Arbeiten mit Katalogebenen die folgenden Empfehlungen:

* **Beschreibende Namen verwenden** - Namensebenen, um ihren Zweck deutlich anzugeben (z. B. „Holiday 2025 Campaign“ oder „SEO-Optimierung - Produktseiten„).

* **Ebenen begrenzen** - Während das System mehrere Ebenen unterstützt, kann die Verwendung zu vieler Ebenen die Leistung beeinträchtigen. Konsolidieren Sie Ebenen nach Möglichkeit.


* **Dokumentprioritätslogik** - Verfolgen Sie, welche Ebenen Vorrang haben, um unbeabsichtigte Überschreibungen zu vermeiden.

* **Sites Optimizer-Ebenen überprüfen** - Bei Verwendung der automatischen Fehlerbehebung in Sites Optimizer erstellt das System Ebenen mit der höchsten Priorität. Achten Sie beim Hinzufügen manueller Ebenen, die KI-Empfehlungen überschreiben. Weitere Informationen zur Verwendung von [Sites Optimizer](../manage-results/opportunities.md).

* **Überwachen der Leistung** - Wenn Sie langsame Ladevorgänge der Produktseite bemerken, überprüfen Sie Ihre Ebenenkonfiguration und erwägen Sie die Konsolidierung von Ebenen.

## Ähnliche Themen

* [Katalogansichten](catalog-view.md) - Konfigurieren von Katalogansichten für verschiedene Storefronts
* [Produktvisualisierungen](https://experienceleague.adobe.com/de/docs/commerce/optimizer/setup/product-visuals) - Verwenden von AEM Assets für Produktbilder
* [Opportunities](../manage-results/opportunities.md) - Erfahren Sie mehr über KI-gestützte Optimierung mithilfe von Katalogschichten
* [Eingeschränkte Zugriffsschlüssel](restricted-access-keys.md) - Schützen einer Katalogansicht mit Authentifizierung mit signierten Token
