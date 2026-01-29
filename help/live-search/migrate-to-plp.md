---
title: Migration vom Suchadapter zum PLP-Widget
description: Erfahren Sie, wie Sie vom veralteten Suchadapter zum Widget  [!DNL Live Search] Produktlistenseite“ migrieren.
source-git-commit: 8811f0f271928fbc827e5a0164542da473c57224
workflow-type: tm+mt
source-wordcount: '2053'
ht-degree: 0%

---

# Migration vom Suchadapter zum PLP-Widget

Der Suchadapter ist seit [ 4.0.0 ](release-notes.md#live-search-400)veraltet[!DNL Live Search] und erhält nur Sicherheits-Updates. Das [Widget „Produktlistenseite (PLP)](plp-styling.md) ist die unterstützte Lösung für alle [!DNL Live Search] Implementierungen, die in Zukunft durchgeführt werden. Dieser Leitfaden hilft Ihnen zu verstehen, wann die Migration einfach ist und wann zusätzliche Arbeit erforderlich ist.

## Voraussetzungen

Stellen Sie sicher, dass Ihre Umgebung diese Anforderungen erfüllt, bevor Sie mit dem Migrationsprozess beginnen.

Vor Beginn der Migration:

**Technische**:

- Adobe Commerce 2.4.4 oder höher.
- [!DNL Live Search] Erweiterung installiert.
- Zugriff auf die Befehlszeile (CLI).
- Zugriff auf Commerce Admin.
- Staging- oder QS-Umgebung für Tests.

**Sicherung und Vorbereitung**:

1. Sichern Sie Ihre Datenbank und Ihren Code.
1. Dokumentieren Sie aktuelle Anpassungen.
1. Überprüfen Sie [Grenzen und Beschränkungen](boundaries-limits.md) um sicherzustellen, dass das PLP-Widget Ihren Anforderungen entspricht.
1. Planen Sie die Migration in einer Zeit mit geringem Traffic.
1. Benachrichtigen Sie die Stakeholder über potenzielle Änderungen am Verhalten der Storefront.

**Überprüfen Sie die aktuelle Implementierung**:

- Überprüfen Sie Ihre aktuelle [!DNL Live Search].
- Dokumentieren Sie, welche Facetten verwendet werden und wie sie konfiguriert sind.
- Testen Sie alle Suchfunktionen und dokumentieren Sie die erwarteten Verhaltensweisen.
- Erfassen Sie Screenshots der aktuellen Suchergebnispräsentation.

**Versionskompatibilität**:

- Adobe Commerce 2.4.4 oder neuer wird ausgeführt.
- Bereit für die Aktualisierung auf [!DNL Live Search] 4.0.0 oder höher.

## Migrationsszenarios

### Einfache Migration (keine zusätzlichen Arbeiten erforderlich)

Sie können direkt zum PLP-Widget migrieren, wenn Ihre Implementierung ALLE der folgenden Kriterien erfüllt:

**Standard-Storefront auf Luma-**:

- Sie verwenden das Luma-Design oder ein Design, das von Luma mit minimalen Anpassungen erbt.
- Sie haben keine benutzerdefinierten Änderungen an PLP-Layouts oder -Vorlagen vorgenommen.
- Sie haben keine benutzerdefinierten JavaScript-Erweiterungen erstellt, die mit Suchergebnissen interagieren.

**Standardproduktkatalog**:

- Alle Produktattribute verwenden standardmäßige Quellmodelle (keine benutzerdefinierten Quellmodelle).
- Es gibt keine benutzerdefinierten Produktarten, für die eine spezielle Rendering-Logik erforderlich ist.
- Ihr Katalog verwendet nur Standardfacetten und Filter.

**Standardintegrationen**:

- Sie verwenden keinen Google Tag Manager (GTM) für Analysen.
- Sie verwenden keine Erweiterungen von Drittanbietern, die das Suchverhalten ändern.

Wenn Ihre Implementierung diese Kriterien erfüllt, fahren Sie mit [Standard-Migrationsschritte](#standard-migration-steps) fort.

### Migration, die zusätzliche Arbeit erfordert

Zusätzliche Arbeit ist erforderlich, wenn Ihre Implementierung eine der folgenden Eigenschaften aufweist:

**Benutzerdefinierte Design-Änderungen**:

- Benutzerdefinierte PLP-Layouts, die Luma-Vorlagen überschreiben.
- Benutzerdefiniertes CSS oder JavaScript für suchadapterspezifische Elemente.
- Benutzerdefinierte Vorlagenänderungen an PLP oder zugehörigen Dateien.
- Design erbt nicht von Luma (z. B. benutzerdefiniertes Design von Grund auf).

**Benutzerdefinierte Produktattribute**:

- Produktattribute mit benutzerdefinierten Quellmodellen, die als Facetten verwendet werden.
- Benutzerdefinierte Produktarten mit speziellen Anzeigeanforderungen.
- Programmatische Attribute mit `"is_user_defined": false`.

**Erweiterte Integrationen**:

- Google Tag Manager (GTM) wird aktiv zum Tracking verwendet.
- In die Suche integrierte Analyse- oder Personalisierungs-Tools von Drittanbietern.
- Benutzerdefinierte Ereignisverfolgung oder Datenschichtimplementierung.
- Integration mit externen Such- oder Empfehlungs-Engines.

**Headless- oder PWA-**:

- Verwenden der Headless-Architektur (z. B. PWA Studio, Vue Storefront).
- Benutzerdefiniertes Frontend-Framework (React, Vue, Angular).
- Verwenden von GraphQL ausschließlich für Katalogabfragen.
- Implementierung benutzerdefinierter Storefront-Ereignisse.

**Benutzerdefinierter Widget-**:

- Zuvor angepasster Suchanpassungs-Code.
- Hosten benutzerdefinierter Versionen von Widgets in Ihrem eigenen CDN.
- Benutzerdefinierte JavaScript-Erweiterungen für die Suchfunktion.

Wenn Ihre Implementierung eines dieser Szenarien aufweist, finden Sie weitere Informationen unter [Komplexe Migrationsszenarien](#complex-migration-scenarios).

## Standardmäßige Migrationsschritte

Führen Sie für Implementierungen ohne spezielle Anpassungen die folgenden Schritte aus:

### Schritt 1: Upgrade-[!DNL Live Search]

Aktualisieren Sie Ihre [!DNL Live Search]-Erweiterung auf Version 4.0 oder höher, um auf das PLP-Widget zuzugreifen.

**Rolle**: Händler oder Partner

1. Überprüfen Sie Ihre aktuelle [!DNL Live Search]:

   ```bash
   composer show magento/live-search | grep version
   ```

1. Wenn Sie Version 3.x oder früher verwenden, aktivieren Sie das AdvancedSearch-Modul vor dem Upgrade:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

1. Aktualisieren Sie `composer.json` so, dass [!DNL Live Search] 4.0 oder höher erforderlich ist:

   ```json
   "require": {
      "magento/live-search": "^4.0"
   }
   ```

1. Führen Sie das Upgrade aus:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

1. Führen Sie das Setup-Upgrade aus und kompilieren Sie erneut:

   ```bash
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   ```

1. Stellen Sie bei Bedarf statische Inhalte bereit:

   ```bash
   bin/magento setup:static-content:deploy
   ```

### Schritt 2: PLP-Widget aktivieren

Konfigurieren Sie das PLP-Widget in Commerce Admin.

**Rolle**: Händler

Das PLP-Widget ist standardmäßig für Neuinstallationen von [!DNL Live Search] 4.0.0 und höher aktiviert. Beim Upgrade von einer früheren Version:

1. Navigieren Sie zu **[!UICONTROL Stores]** > Einstellungen > **[!UICONTROL Configuration]**.
1. Navigieren Sie zu **[!UICONTROL Live Search]** > **[!UICONTROL Storefront Features]**.
1. Erweitern Sie den Abschnitt **[!UICONTROL Storefront Features]** .
1. Setzen Sie **[!UICONTROL Enable Product Listing Widgets]** auf **Ja**.
1. Klicken Sie auf **[!UICONTROL Save Config]**.
1. Leeren Sie den Cache: **[!UICONTROL System]** > Tools > **[!UICONTROL Cache Management]** > **[!UICONTROL Flush Magento Cache]**.

### Schritt 3: Test beim Staging

Validieren Sie die Migration in einer Nicht-Produktionsumgebung, bevor Sie live gehen.

**Rolle**: Händler/Partner

Testen Sie die Suchfunktion gründlich, bevor Sie sie in der Produktion bereitstellen:

**Funktionstests**:

- Überprüfen Sie, ob die Suchergebnisse korrekt angezeigt werden.
- Alle konfigurierten Facetten testen.
- Überprüfen Sie, ob die Kategoriennavigation funktioniert.
- Testen der Paginierung durch Ergebnisse.
- Stellen Sie sicher, dass die Sortieroptionen erwartungsgemäß funktionieren.
- Testen Sie die Funktion „In den Warenkorb legen“ für einfache Produkte.

**Sehtest**:

- Vergewissern Sie sich, dass die Produktbilder korrekt angezeigt werden.
- Überprüfen Sie, ob Produktnamen und -preise ordnungsgemäß gerendert werden.
- Testfarbfelder (falls verwendet).
- Überprüfen Sie das responsive Verhalten auf Mobilgeräten.
- Überprüfen Sie, ob der Stil Ihrer Marke entspricht.

**Leistungstests**:

- Messen Sie die Seitenladezeiten.
- Testen Sie mit einer realistischen Kataloggröße.
- Überwachen der Server-Ressourcennutzung.
- Überprüfen Sie die Browser-Konsole auf JavaScript-Fehler.

### Schritt 4: Bereitstellung für Produktion

Verschieben Sie die validierte Konfiguration in Ihre Live-Storefront.

**Rolle**: Händler/Partner

1. Planen Sie die Bereitstellung nach Möglichkeit während des Wartungsfensters.
1. Befolgen Sie den standardmäßigen Bereitstellungsprozess.
1. Aktivieren Sie das PLP-Widget in der Produktion mit [Schritt 2: Aktivieren Sie das PLP-Widget](#step-2-enable-the-plp-widget).
1. Sofort nach der Bereitstellung auf Probleme überwachen.
1. Halten Sie einen Rollback-Plan bereit, wenn kritische Probleme auftreten.

### Schritt 5: Validieren und Überwachen

Nachverfolgen der Suchleistung und des Kundenerlebnisses nach der Migration.

**Rolle**: Händler

Überwachen Sie nach der Bereitstellung Schlüsselmetriken:

- Suchrate ohne Ergebnisse
- Konversionsrate von Suche nach Warenkorb
- Seitenladeleistung
- Kundenfeedback oder Support-Tickets
- JavaScript-Fehler in der Browser-Konsole

## Komplexe Migrationsszenarien

Für die folgenden Szenarien sind über die standardmäßigen Migrationsschritte hinaus zusätzliche Planungen, benutzerdefinierte Entwicklungen oder spezielle Unterstützung erforderlich.

### Benutzerdefiniertes Design mit Layout-Änderungen

In diesem Szenario verfügen Sie über benutzerdefinierte Vorlagen oder Layouts, die das standardmäßige Produktlistenverhalten überschreiben.

**role**: Entwickler/Partner

1. **Audit-Anpassungen**:
   - Dokumentieren Sie alle XML-Dateien mit benutzerdefiniertem Layout in Ihrem Design.
   - Überprüfen Sie alle benutzerdefinierten Vorlagenänderungen an Produktlistenseiten oder zugehörigen Dateien.
   - Identifizieren Sie benutzerdefinierte CSS-Klassen, die für die Formatierung verwendet werden.
   - Dokumentieren benutzerdefinierter JavaScript-Interaktionen.

1. **Migrieren zu CSS-basierten Anpassungen**:
   - Das PLP-Widget verwendet spezifische CSS-Klassen (siehe [PLP-Stilhandbuch](plp-styling.md)).
   - Erstellen Sie visuelle Anpassungen mithilfe der CSS-Klassen des PLP-Widgets neu.
   - Testen Sie, ob benutzerdefinierte Stile korrekt angewendet werden.

1. **Entfernen widersprüchlicher Anpassungen**:
   - Layout-XML entfernen, die die Struktur der Produktliste ändert.
   - Bereinigen Sie JavaScript, das auf suchadapterspezifische Elemente abzielt.
   - Update-Vorlagen überschreiben, die mit dem Widget-Rendering kollidieren.

1. **Gründlich testen**:
   - Überprüfen Sie, ob alle visuellen Anpassungen mit dem PLP-Widget funktionieren.
   - Stellen Sie sicher, dass keine Layout-Konflikte auftreten.
   - Testen Sie über alle Haltepunkte und Geräte hinweg.

### Produktattribute mit benutzerdefinierten Quellmodellen

In diesem Szenario haben Sie Facetten, die Produktattribute mit benutzerdefinierten Quellmodellen verwenden, die nicht vom Suchadapter unterstützt werden, aber vom PLP-Widget unterstützt werden.

**Rolle**: Händler (Admin-Konfiguration)

1. **Identifizieren Sie die betroffenen Attribute**:
   - Überprüfen Sie die als Facetten verwendeten Produktattribute.
   - Identifizieren Sie, welche benutzerdefinierte Quellmodelle verwenden.
   - Dokumentieren der aktuellen Facettenkonfiguration.

1. **Aktualisieren und Aktivieren des PLP-Widgets**:
   - Befolgen Sie [Standard-Migrationsschritte](#standard-migration-steps).
   - Das PLP-Widget unterstützt benutzerdefinierte Quellmodellattribute.

1. **Facetten neu konfigurieren**:
   - Gehen Sie zu **[!UICONTROL Marketing]** > SEO &amp; Search > **[!UICONTROL Live Search]**.
   - Überprüfen Sie die Facettenkonfiguration auf betroffene Attribute.
   - Testfacetten funktionieren ordnungsgemäß mit benutzerdefinierten Quellmodellen.

1. **Validieren**:
   - Testen der Filterung mit benutzerdefinierten Quellmodellfacetten.
   - Stellen Sie sicher, dass alle Attributwerte korrekt angezeigt werden.
   - Sicherstellen, dass die Leistung akzeptabel ist.

### Integration von Google Tag Manager (GTM)

In diesem Szenario gibt es ein bekanntes Problem, bei dem die Aktivierung des PLP-Widgets dazu führen kann, dass GTM fehlschlägt.

**role**: Entwickler/Partner + Customer Engineering

**Option 1: Suche nach Adapter fortsetzen (nur interimistisch)**

- Lassen Sie den Suchadapter aktiviert, wenn GTM geschäftskritisch ist.
- Sie sollten wissen, dass Sie nur Sicherheitsupdates erhalten.
- Planen Sie die Migration, wenn die GTM-Kompatibilität behoben ist.
- Wenden Sie sich an den Adobe-Support , um Informationen zur GTM-Kompatibilität zu erhalten.

**Option 2: Migrieren des GTM-Trackings auf einen alternativen Ansatz**

1. **Implementieren einer benutzerdefinierten Ereignisauflistung**:

   - Verwenden Sie die [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/).
   - Erfassen Sie Such- und Produktinteraktionsereignisse.
   - Pushen Sie Ereignisse manuell an die GTM-Datenschicht.

1. **Führen Sie die folgenden Schritte aus**:

   - Prüfung der aktuellen GTM-Tracking-Anforderungen.
   - GTM-Ereignisse Storefront-Ereignissen zuordnen.
   - Implementieren benutzerdefinierter Ereignis-Listener.
   - Testen des Datenflusses zu GTM.
   - Validieren von Analyseberichten.

**Option 3: GTM durch Adobe Analytics ersetzen**

- Ziehen Sie ggf. eine Migration zu [Adobe Analytics](https://business.adobe.com/products/adobe-analytics.html) in Betracht.
- Wenden Sie sich an den Customer Engineering.

**An wen wenden**: Senden eines Support-Tickets für GTM-Kompatibilitätsaktualisierungen oder Customer Engineering-Unterstützung.

### Szenario: Headless- oder PWA-Implementierung

In diesem Szenario verfügen Sie über eine Headless- oder PWA-Storefront, für die eine benutzerdefinierte Ereigniserfassung erforderlich ist und die standardmäßige PLP-Widget-Benutzeroberfläche nicht verwendet werden kann.

**role**: Entwickler/Partner

1. **Referenzimplementierungen überprüfen**:
   - Studieren Sie den [PLP-Widget-Quell-Code](https://github.com/adobe/storefront-product-listing-page).
   - Lesen Sie die API-Dokumentation für [[!DNL Live Search] GraphQL](graphql.md).
   - Verstehen Sie die [Abfragen des Katalog-Service](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/).

1. **Implementieren einer benutzerdefinierten Benutzeroberfläche**:
   - Verwenden Sie [!DNL Live Search] GraphQL-API für Abfragen.
   - Erstellen benutzerdefinierter Produktlisten-Komponenten.
   - Implementieren Sie die Benutzeroberfläche für Facettenbildung.
   - Paginierung und Sortierung handhaben.

1. **Implementieren der Ereignissammlung**:
   - Siehe [Dokumentation zu Storefront-](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search).
   - Implementieren Sie die erforderlichen Ereignisse:
      - `search-request-sent`
      - `search-response-received`
      - `search-results-view`
      - `product-page-view`
      - `add-to-cart`
   - Testen von Ereignisdatenflüssen an Adobe Commerce.

1. **Facettensortierung konfigurieren**:
   - Bei Headless-Implementierungen können Facetten nach Anzahl sortiert werden.
   - Konfigurieren von in **[!UICONTROL Live Search]** > **[!UICONTROL Facets]** Workspace.
   - Setzen Sie **[!UICONTROL Sort Type]** auf **Count** für bessere Benutzererlebnisse.

1. **Testen und Validieren**:
   - Überprüfen Sie die Genauigkeit der Suchergebnisse.
   - Testen der Facettenfunktionalität.
   - Vergewissern Sie sich, dass Ereignisse korrekt verfolgt werden.
   - Leistungsmetriken überwachen.
   - Validieren der Funktionsfähigkeit intelligenter Merchandising-Funktionen.

### Szenario: Code-Änderungen für benutzerdefinierte Widgets

In diesem Szenario haben Sie zuvor den Suchadapter- oder Widget-Code angepasst und müssen Anpassungen migrieren.

**role**: Entwickler/Partner

1. **Vorhandene Anpassungen**:
   - Listet alle Anpassungen auf, die an der Adaptersuche vorgenommen wurden.
   - Identifizieren Sie die Geschäftsanforderungen, die für jede Anpassung bestimmend sind.
   - Stellen Sie fest, ob weiterhin Anpassungen erforderlich sind.

1. **Überprüfen Sie, ob die integrierten Funktionen Ihren Anforderungen entsprechen**:
   - Überprüfen Sie [PLP-Widget-Funktionen](plp-styling.md#widget-features).
   - Überprüfen Sie, ob die CSS-basierte Anpassung ausreicht.
   - Testen des standardmäßigen PLP-Widget-Verhaltens.

1. **Wenn benutzerdefinierter Code weiterhin benötigt wird**:
   - Klonen Sie das [PLP-Widget-Repository](https://github.com/adobe/storefront-product-listing-page).
   - Implementieren Sie Ihre Anpassungen.
   - Hosten Sie in Ihrem eigenen CDN.
   - Aktualisieren Sie die Commerce-Konfiguration zur Verwendung Ihres benutzerdefinierten Widgets.

   >[!WARNING]
   >
   >Wenn Sie das PLP-Widget mit Code aus dem Repository anpassen, sind Sie für die Wartung und Aktualisierung verantwortlich. Neue PLP-Widget-Funktionen von Adobe sind möglicherweise nicht mit Ihren Anpassungen kompatibel.

1. **Gründlich testen**:
   - Testen Sie alle benutzerdefinierten Funktionen.
   - Stellen Sie sicher, dass Commerce-Updates die Anpassungen nicht beschädigen.
   - Dokumentieren Sie Ihre benutzerdefinierte Implementierung.
   - Planen Sie die laufende Wartung.

## Bekannte Einschränkungen und Randfälle

Beachten Sie bei der Migration die folgenden Einschränkungen:

**PLP-Widget-Einschränkungen**:

- **Sortierreihenfolge**: Wenn das PLP-Widget aktiviert ist, kann die Sortierreihenfolge auf den Produktlistenseiten nicht geändert werden (aufsteigend/absteigend).
- **Zum Warenkorb hinzufügen**: Die Schaltflächen „Zum Warenkorb hinzufügen“ sind nur für einfache Produkte im Widget verfügbar.
- **Preisstufe**: Im PLP-Widget nicht unterstützt.
- **MwSt.-Anzeige**: Die Preise verstehen sich inklusive MwSt., können jedoch nicht separat ausgewiesen werden.

**Funktionsunterschiede zum Suchanschluss**:

- **Farbfelder**: Das `color`-Attribut muss genau wie `color` geschrieben sein (nicht „color“ oder benutzerdefinierte Namen), damit die Farbfelder ordnungsgemäß funktionieren.
- **Design-Stil**: Benutzerdefinierte Design-Klassen werden nicht vom Widget vererbt; sie müssen auf Widget-spezifische CSS-Klassen abzielen.
- **Benutzerdefinierte Produkttypen**: Wird im Widget nicht unterstützt.

**Leistungsaspekte**:

- Bei großen Katalogen (mehr als 50.000 Produkte) kann es zu längeren ersten Seitenladevorgängen kommen.
- Mehrere Facetten mit vielen Werten können die Leistung beeinträchtigen.
- Die Leistung von Mobilgeräten kann je nach Kataloggröße variieren.

**Kompatibilitätsprobleme**:

- Kompatibilitätsproblem mit Google Tag Manager (siehe [GTM-Szenario](#google-tag-manager-gtm-integration)).
- Einige Erweiterungen von Drittanbietern können mit dem PLP-Widget in Konflikt stehen.
- Benutzerdefinierte Checkout-Erweiterungen müssen möglicherweise aktualisiert werden.

## Hilfe wird abgerufen

Wenden Sie sich je nach Bedarf an die entsprechende Ressource.

Der **Adobe-Support** kann bei Folgendem helfen:

- Standard-Migrationsverfahren für die Live Search
- Konfigurationsprobleme mit PLP-Widgets
- Probleme bei der Facetten- oder Attributindizierung
- Leistungsprobleme bei Standardimplementierungen
- Upgrade-Fehler

**Entwicklungspartner/Systemintegratoren** sollten kontaktiert werden für:

- Benutzerdefinierte Design-Änderungen
- Implementierungen von benutzerdefiniertem Widget-Code
- Kompatibilität mit Erweiterungen von Drittanbietern
- Headless- oder PWA-Implementierung
- Benutzerdefinierte Ereignisverfolgung

Informationen zum Adobe-Support finden Sie im [Hilfezentrum-Benutzerhandbuch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).

## FAQs

Hier finden Sie Antworten auf häufig gestellte Fragen zur Migration vom Suchadapter zum PLP-Widget.

**F: Erhält der Suchadapter Fehlerbehebungen oder Funktionsaktualisierungen?**

A: Nein. Der Suchadapter ist veraltet und erhält nur Sicherheitsupdates. Fehlerbehebungen, Leistungsverbesserungen und neue Funktionen sind nur im PLP-Widget verfügbar. Wenn Sie auf Probleme mit dem Suchadapter stoßen, ist die Migration zum PLP-Widget die empfohlene Lösung.

**F: Wird die Migration meine Storefront stören?**

A.: Wenn Sie beim Staging die richtigen Testverfahren befolgen, sollte die Migration nahtlos sein. Einen Rollback-Plan für die Produktionsbereitstellung haben.

**F: Wie lange dauert die Migration?**

A: Für Standardimplementierungen: 1-2 Stunden. Bei benutzerdefinierten Implementierungen: 1-4 Wochen, je nach Komplexität.

**F: Funktionieren meine Merchandising-Regeln für die Suche weiterhin?**

A.: Ja, alle im Arbeitsbereich &quot;[!DNL Live Search]&quot; konfigurierten Merchandising-Regeln, Synonyme und Facetten für die Suche funktionieren weiterhin mit dem PLP-Widget.

**F: Muss ich meine Facetten neu konfigurieren?**

A: Im Allgemeinen nein, aber wenn Sie durch benutzerdefinierte Quellmodellattribute mit dem Suchadapter eingeschränkt waren, können Sie sie jetzt mit dem PLP-Widget verwenden.

**F: Was ist mit meinem benutzerdefinierten CSS?**

A: Sie müssen CSS aktualisieren, um die PLP-Widget-Klassen anzusprechen. Siehe die [CSS-Klassen-Referenz](plp-styling.md#css-classes).

**F: Wirkt sich dies auf meine Suchleistung aus?**

A: Das PLP-Widget ist für Leistung konzipiert. Die meisten Händler sehen gleiche oder bessere Leistung. Große Kataloge sollten im Staging getestet werden.
