---
title: Katalogebene
description: Erfahren Sie, wie Sie mit Katalogebenen Produktdaten ändern können, ohne die ursprünglichen Quelldaten zu ändern, sodass Sie Änderungen jederzeit sicher anpassen und rückgängig machen können.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 4a904527af172a5e35b87410135d55484d07ad84
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Katalogebene

Mit Katalogschichten können Sie Produktdaten ändern, ohne die ursprünglichen Quelldaten zu ändern. Ebenen wenden Änderungen an bestimmten Produktattributen an, z. B. Name, Beschreibung, Bilder, Links und Metadaten, indem eine Ebene über Ihrem Basiskatalog erstellt wird. Ihre ursprünglichen Produktdaten bleiben intakt, sodass Sie Produkte sicher anpassen und Änderungen jederzeit rückgängig machen können.

![Katalogebenen](../assets/catalog-layers.png)

## Funktionsweise von Katalogebenen

Wenn ein Kunde Ihre Storefront aufruft, kombiniert das System Ihre Basiskatalogdaten mit aktiven Katalogebenen, um die endgültigen Produktinformationen anzuzeigen. So funktioniert der Prozess:

1. **Ebenenanwendung** - Wenn eine Anfrage mit einer Kanal-ID und einer Umgebungs-ID erfolgt, ruft der Store-Service die entsprechende Katalogansicht ab.

1. **Datenzusammenführung** - Das System wendet Katalogschichten auf Produktdaten basierend auf der Prioritätsreihenfolge der Schicht an.

1. **Feldbehandlung** - Verschiedene Feldtypen werden unterschiedlich verarbeitet:

   - **Felder überschreiben** - Textfelder wie Name, Beschreibung und Meta-Titel werden durch die in der Ebene definierten Werte ersetzt, wobei die Ebene mit der höheren Priorität Vorrang hat.
   - **Felder zusammenführen** - Array-Felder wie Bilder, Links und Attribute werden aus mehreren Ebenen kombiniert, um eine einheitliche Antwort zu erzielen.

1. **Prioritätsauflösung** - Das Reihenfolgenfeld bestimmt, welche Ebene Vorrang hat. Wenn mehrere Ebenen dasselbe Feld ändern, hat die Ebene mit der Nummer niedrigerer Ordnung eine höhere Priorität (z. B. Reihenfolge 1 ist die höchste).

## Anwendungsfälle für Katalogebenen

Katalogebenen werden häufig für Folgendes verwendet:

- **SEO-Optimierung** - Überschreiben von Produktmetadaten-Titeln und -Beschreibungen basierend auf KI-Empfehlungen von [Sites Optimizer](../manage-results/opportunities.md).
- **Saisonale Kampagnen** - Aktualisieren Sie Produktnamen, Beschreibungen oder Bilder für Werbeaktionen vorübergehend, ohne die Quelldaten zu ändern.
- **Regionale Anpassung** - Zeigt verschiedene Produktinformationen basierend auf geografischem Standort oder Sprache an.
- **A/B-Tests** - Testen Sie verschiedene Produktpräsentationen, um die Konversionsraten zu optimieren.
- **Verwaltung mehrerer Marken** - Passen Sie Produktattribute für verschiedene Ansichten des Markenkatalogs an.

## Hinzufügen einer Katalogebene über die Datenaufnahme

Sie können Ihren Produkten während der Datenaufnahme Katalogebenen hinzufügen. Diese Methode eignet sich ideal für Massenvorgänge oder automatisierte Workflows.

>[!NOTE]
>
>Sie importieren Katalogebenen mit der Aufnahme-API, aber [ Festlegen der Reihenfolge ](#manage-layer-priorities) Ebenen erfolgt über die Benutzeroberfläche.

**Voraussetzungen:**

- API-Anmeldeinformationen mit Berechtigung für den Zugriff auf den Datenaufnahme-Service
- Produkt-SKUs, die bereits im Basiskatalog vorhanden sind

**Schritte:**

1. Bereiten Sie Ihre Ebenendaten im erforderlichen Format mit den Produktattributen vor, die Sie ändern möchten.

1. Verwenden Sie den API-Endpunkt „Product Layers“, um die Ebenendaten aufzunehmen.

1. Überprüfen Sie, ob die Ebene erfolgreich aufgenommen wurde, indem Sie die Konfiguration der Katalogansicht überprüfen.

Detaillierte API-Spezifikationen und Payload-Beispiele finden Sie unter [Produktebenen](https://developer.adobe.com/commerce/services/reference/rest/#tag/Product-Layers) in der Entwicklerdokumentation.

## Manuelles Hinzufügen einer Katalogebene in der Benutzeroberfläche

>[!NOTE]
>
>Diese Funktion ist noch nicht verfügbar.

Die Benutzeroberfläche für die Katalogansicht ermöglicht die manuelle Erstellung und Verwaltung von Ebenen. Dies ist besonders für Integrationen wie Sites Optimizer nützlich, die KI-gestützte Empfehlungen generieren.

>[!NOTE]
>
>Wenn in Ihrer Katalogansicht keine Sites Optimizer-Ebene vorhanden ist, erstellt die Funktion zur automatischen Fehlerbehebung in Sites Optimizer automatisch eine und weist ihr Reihenfolge 1 (höchste Priorität) zu. Wenn Sie diese Ebene löschen, wird sie bei der nächsten Ausführung der Funktion zur automatischen Fehlerbehebung in Sites Optimizer neu erstellt und die bestehenden Ebenen werden in niedrigere Ordnungszahlen verschoben. Wenn die Sites Optimizer-Ebene bereits mit einer anderen Bestellnummer vorhanden ist, ändert die Funktion für die automatische Fehlerbehebung ihre Priorität nicht.

>[!TIP]
>
>Verwenden Sie für Massenschichtvorgänge die Datenaufnahme-API-Methode [oben beschrieben](#add-a-catalog-layer-via-data-ingestion).

**So erstellen Sie eine manuelle Ebene:**

1. Navigieren Sie **Store-Setup** > **Katalogansichten**.

1. Wählen Sie die Katalogansicht aus, in der Sie die Ebene anwenden möchten.

1. Klicken Sie im Abschnitt Katalogebenen auf **Katalogebene hinzufügen**.

1. Konfigurieren Sie die Ebeneneigenschaften:

   - **Ebenenname** - Geben Sie einen beschreibenden Namen ein, um den Zweck der Ebene zu identifizieren.
   - **Produkte** - Wählen Sie die Produkte aus, für die diese Ebene gilt.
   - **Attribute** - Wählen Sie aus, welche Produktattribute geändert werden sollen (Name, Beschreibung, Bilder, Meta-Tags usw.).
   - **Werte** - Geben Sie die neuen Werte für jedes ausgewählte Attribut ein.

1. Klicken Sie auf **Speichern**, um die Ebene zu erstellen.

Die neue Ebene wird der Katalogansicht hinzugefügt und automatisch der nächsten verfügbaren Bestellnummer zugewiesen.

## Vorschau von Ebeneneffekten

>[!NOTE]
>
>Diese Funktion ist noch nicht verfügbar.

Bevor Sie Ebenen aktivieren oder Prioritäten ändern, können Sie sich eine Vorschau ansehen, wie sie sich auf Produktdaten auswirken.

**Vorschau von Ebenenänderungen anzeigen:**

1. Navigieren Sie **Store-Setup** > **Katalogansichten**.

1. Wählen Sie die Katalogansicht mit den Ebenen aus, die Sie in der Vorschau anzeigen möchten.

1. Wählen Sie im Abschnitt Katalogebenen ein bestimmtes Produkt aus oder verwenden Sie die Vorschaufunktion.

1. Überprüfen Sie die kombinierten Produktdaten, die zeigen, wie Ebenen die Grundkatalogwerte ändern.

1. Nehmen Sie nach Bedarf Anpassungen am Ebeneninhalt oder an der Prioritätsreihenfolge vor.

## Aktivieren, Deaktivieren oder Löschen von Ebenen

Sie können Katalogebenen aktivieren oder deaktivieren, ohne sie zu löschen, sodass Sie steuern können, wann bestimmte Anpassungen angewendet werden.

**So aktivieren oder deaktivieren Sie eine Ebene:**

1. Navigieren Sie **Store-Setup** > **Katalogansichten**.

1. Wählen Sie die Katalogansicht aus, die die Ebene enthält.

1. Suchen Sie im Abschnitt Katalogebenen die Ebene, die Sie umschalten möchten.

1. Klicken Sie auf den Umschalter Aktivierung , um die Ebene zu aktivieren oder zu deaktivieren.

   - **Aktiv** - Die Ebene wird auf Produktdaten angewendet.
   - **Inaktiv** - Die Ebene wird beibehalten, aber nicht auf Produktdaten angewendet.

1. Die Änderung wird sofort in Ihrer Storefront wirksam.

**So löschen Sie eine Ebene:**

Verwenden Sie die Datenerfassungs-API, um [eine Katalogschicht zu löschen](https://developer.adobe.com/commerce/services/reference/rest/#operation/deleteProductLayers).

## Verwalten von Ebenenprioritäten

Die Reihenfolge, in der Ebenen angewendet werden, bestimmt, welche Werte in Ihrer Storefront angezeigt werden, wenn mehrere Ebenen dasselbe Produktattribut ändern. Durch die Verwaltung von Prioritäten wird sichergestellt, dass die richtigen Daten angezeigt werden.

**Grundlegendes zur Prioritätsreihenfolge:**

- Jeder Ebene wird eine Ordnungsnummer (1, 2, 3 usw.) zugewiesen
- Reihenfolge 1 hat die höchste Priorität und überschreibt alle anderen Ebenen
- Wenn mehrere Ebenen dasselbe Feld ändern, hat die Ebene mit der Nummer niedrigerer Ordnung Vorrang
- Priorität gilt nur für das Überschreiben von Feldern (Name, Beschreibung, Meta-Tags)
- Felder (Bilder, Links, Attribute) verbinden Daten aus allen Ebenen

**So ordnen Sie die Ebenenprioritäten neu an:**

1. Navigieren Sie **Store-Setup** > **Katalogansichten**.

1. Wählen Sie die Katalogansicht mit den Ebenen aus, die Sie neu anordnen möchten.

1. Suchen Sie im Abschnitt Katalogebenen die Ebene, die Sie verschieben möchten.

1. Ziehen Sie die Ebene per Drag-and-Drop, um ihre Position zu ändern, oder verwenden Sie die Steuerelemente zur Neuanordnung.

1. Das System aktualisiert die Bestellnummern automatisch auf der Grundlage der neuen Reihenfolge.

1. Klicken Sie **Speichern**, um die neue Prioritätsreihenfolge anzuwenden.

>[!IMPORTANT]
>
>Änderungen an der Ebenenpriorität werden sofort wirksam und können sich auf das auswirken, was Kunden in Ihrer Storefront sehen. Überprüfen Sie die Vorschau vor dem Speichern, um sicherzustellen, dass die richtigen Werte angewendet werden **Vorschau ist noch nicht verfügbar**.

## Best Practices

Befolgen Sie beim Arbeiten mit Katalogebenen die folgenden Empfehlungen:

- **Beschreibende Namen verwenden** - Namensebenen, um ihren Zweck deutlich anzugeben (z. B. „Holiday 2025-Kampagne“ oder „SEO-Optimierung - Produktseiten„).

- **Ebenen begrenzen** - Während das System mehrere Ebenen unterstützt, kann die Verwendung zu vieler Ebenen die Leistung beeinträchtigen. Konsolidieren Sie Ebenen nach Möglichkeit.

<!--- **Test before activating**—Always preview layer effects before activating them on your live storefront. !!!REMOVE IF PREVIEW NOT AVAILABLE FOR GA!!!-->

- **Dokumentprioritätslogik** - Verfolgen Sie, welche Ebenen Vorrang haben sollten, um unbeabsichtigte Überschreibungen zu vermeiden.

- **Sites Optimizer-Ebenen überprüfen** - Bei Verwendung der automatischen Fehlerbehebung in Sites Optimizer erstellt das System Ebenen mit der höchsten Priorität. Achten Sie beim Hinzufügen manueller Ebenen, die KI-Empfehlungen überschreiben können. Weitere Informationen zur Verwendung von [Sites Optimizer](../manage-results/opportunities.md).

- **Überwachen der Leistung** - Wenn Sie langsame Ladevorgänge der Produktseite bemerken, überprüfen Sie Ihre Ebenenkonfiguration und erwägen Sie die Konsolidierung von Ebenen.

## Ähnliche Themen

- [Katalogansichten](catalog-view.md) - Konfigurieren von Katalogansichten für verschiedene Storefronts
- [Opportunities](../manage-results/opportunities.md) - Erfahren Sie mehr über die KI-gestützte Optimierung mithilfe von Katalogschichten
