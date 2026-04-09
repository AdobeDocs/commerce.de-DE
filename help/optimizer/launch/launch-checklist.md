---
title: Checkliste starten
description: Erfahren Sie, wie Sie Konfiguration, Storefront, SEO, CDN, Integrationen, Sicherheit, Analysen und Tests für die Produktion  [!DNL Adobe Commerce Optimizer] .
solution: Commerce
feature: Integration, Storefront, Search, Catalog Management, Personalization
feature-set: Commerce
role: Admin, Developer
level: Intermediate
topic: Administration
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service und  [!DNL Adobe Commerce Optimizer] Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 37b8b8a334ca11daacfd3da03b0441e77329e2e1
workflow-type: tm+mt
source-wordcount: '1940'
ht-degree: 0%

---


# Checkliste starten

Verwenden Sie diese Checkliste, um zu überprüfen, ob Ihr [!DNL Adobe Commerce Optimizer] konfiguriert, getestet und startbereit ist. Bearbeiten Sie die einzelnen Abschnitte gemeinsam mit Ihrem Team und verfolgen Sie den Abschluss in Ihrem eigenen Projektplan oder Tracker. Informationen zu den unten referenzierten Produktfunktionen und Benutzeroberflächenbereichen finden Sie unter [[!DNL Adobe Commerce Optimizer] Dokumentation](../overview.md).

## Anwendungsfall und Architektur {#use-case}

Verwenden Sie diese Checkliste, wenn Sie ein B2C-Erlebnis bereitstellen, das [!DNL Adobe Commerce Optimizer] und Edge Delivery Services (EDS) mit einer bestehenden Adobe Commerce on Cloud-Instanz kombiniert.

Ihre Lösung umfasst in der Regel die folgenden Komponenten:

- **Cloud** - Adobe Commerce on Cloud verwaltet Katalogdaten, Kunden, Assets und Kaufabläufe (Checkout, Bestellverwaltung, Versand usw.).
- **Optimizer** - [!DNL Adobe Commerce Optimizer] liefert Merchandising-Erlebnisse.
- **Storefront** - Adobe Commerce Storefront auf Edge Delivery Services stellt die Benutzeroberfläche bereit.
- **Services von Drittanbietern** - Zahlungs-, Versand- und Steueranbieter.
- **App Builder**-Erweiterbarkeit.
- **API Mesh** - Anfrage-Routing.

## Überprüfen von Adobe Commerce in Cloud Manager {#verify-cloud}

Vergewissern Sie sich, dass Ihre Adobe Commerce on Cloud-Umgebung produktionsbereit ist.

▢ Die Cloud-Instanz ist [bereitgestellt](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/start/new-project).
▢ Test- und Platzhalterdaten werden aus der Instanz entfernt.
▢ Produktionsdaten werden in die Instanz geladen.
▢ Sie kennen den [GraphQL-Endpunkt](https://developer.adobe.com/commerce/webapi/graphql/).
▢ Die Instanz erfüllt [ready-for-launch](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/launch/checklist)-Anforderungen.

## Commerce Optimizer-Instanz überprüfen {#verify-optimizer}

Vergewissern Sie sich, dass Ihre [!DNL Adobe Commerce Optimizer] Produktionsinstanz korrekt eingerichtet ist.

▢ Die Produktionsinstanz ist aktiv. Weitere Informationen [&#x200B; Bereitstellung finden &#x200B;](../get-started.md) unter „Erste Schritte“.
▢ Die Instanz befindet sich in der richtigen Region.
▢ Der Umgebungstyp ist Produktion.
▢ Sie kennen die Organisations-ID, Client-ID, Aufnahme-URL und Commerce Optimizer-URL. Siehe [Erste Schritte](../get-started.md).
▢ konfigurierten Limits und Limits entsprechen den Werten, die von Ihrem Adobe Customer Technical Advisor (CTA) bestätigt wurden.
▢ Testartefakte und Platzhalterdaten wurden aus der Instanz entfernt.

## Storefront-Site überprüfen {#verify-storefront-site}

Vergewissern Sie sich, dass Ihre Edge Delivery Services-Storefront-Site vorhanden und der Zugriff eingeschränkt ist.

▢ Die Storefront-Site ist vorhanden. Siehe [Erstellen einer Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/?lang=de).
▢ Sie kennen den Site-Namen.
▢ Nur autorisierte Personen verfügen über [Berechtigung zum Veröffentlichen](https://tools.aem.live/tools/user-admin/index.html).
▢ Nur autorisierte Personen verfügen über [Berechtigung für Autor](https://docs.da.live/administrators/guides/permissions).

## Überprüfen der Cloud- und Optimizer-Integration {#cloud-optimizer-integration}

Überprüfen Sie, ob Adobe Commerce in Cloud Manager und [!DNL Adobe Commerce Optimizer] Daten korrekt austauschen.

### auf Adobe Commerce

Führen Sie diese Prüfungen in Ihrem Cloud-Projekt durch.

▢ Der Commerce Optimizer-Connector ist [installiert und konfiguriert](../../aco-connector/get-started.md).
▢ Der `aco:conf:show` CLI-Befehl bestätigt die Verbindung zur Commerce Optimizer-Produktionsinstanz. Die Organisations-ID, die Client-ID, die Aufnahme-URL und die Commerce Optimizer-URL stimmen mit der Produktion überein.
▢ Synchronisierungsumfänge in [Exportkonfiguration](../../aco-connector/get-started.md) entsprechen Ihren Anforderungen.
▢ [Status der Daten-Feed-](../../aco-connector/get-started.md)) bestätigt den Datenexport aus der Cloud-Instanz.

### In Commerce Optimizer

Führen Sie diese Prüfungen in der [!DNL Adobe Commerce Optimizer]-Benutzeroberfläche durch.

▢ Das [Datensynchronisations-Dashboard](../setup/data-sync.md) zeigt die empfangenen Daten an. Produkte, Preise und Attribute werden für Catalog Service, Product Discovery und Recommendations angezeigt.
▢ [Preisverzeichnisse](../setup/pricebooks.md) werden automatisch aus Kundengruppen in der Cloud erstellt.
▢ [Katalogansichten](../setup/catalog-view.md) sind vorhanden und Sie kennen ihre IDs.
▢ [Richtlinien](../setup/policies.md) sind vorhanden und Sie kennen ihre IDs.
▢ [Facetten](../merchandising/facets/overview.md) werden konfiguriert.
▢ [Synonyme](../merchandising/synonyms/overview.md) sind konfiguriert.
▢ [Merchandising-Regeln](../merchandising/rules/overview.md) sind konfiguriert.
▢ [Preisgestaltung und Suchsprache](../settings.md) entsprechen Ihren Anforderungen, wenn Sie diese Funktionen verwenden.
▢ [Produktempfehlungen](../merchandising/recommendations/create.md) sind vorhanden und verhalten sich in der Vorschau erwartungsgemäß.
▢ [Suchleistungsdaten](../manage-results/search-performance.md) wird im *Admin* angezeigt.
▢ [Leistungsdaten für Recommendations](../manage-results/recommendation-performance.md) wird in der *Admin* angezeigt.

## Überprüfen der Integration von Storefront und Cloud {#storefront-cloud-integration}

Vergewissern Sie sich, dass die Storefront vom richtigen Adobe Commerce GraphQL-Endpunkt liest.

### auf Adobe Commerce

▢ Storefront-Kompatibilitätspakete sind [installiert](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/storefront-compatibility/install/?lang=de).

### Im Schaufenster

▢ Die `commerce-core-endpoint` für die Storefront verweist auf Ihren [Cloud GraphQL-Endpunkt](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/?lang=de).
▢ Wenn Sie API Mesh als Proxy für Cloud GraphQL verwenden, verweist `commerce-core-endpoint` auf den API-Mesh-Endpunkt anstelle des Cloud GraphQL-Endpunkts.

## Überprüfen der Integration von Storefront und Optimizer {#storefront-optimizer-integration}

Bestätigen Sie die Commerce Optimizer-Einstellungen in der Storefront-Konfiguration.

▢ Ihre Storefront verwendet die richtigen [Commerce Optimizer-Einstellungen](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/?lang=de).
▢ `adobe-commerce-optimizer` ist `true`.
▢ `commerce-endpoint` verweist auf den Produktions-Endpunkt von Commerce Optimizer GraphQL oder auf den API-Mesh-Endpunkt, wenn Sie API-Mesh verwenden.
▢ `headers.cs.AC-view-ID` enthält die Katalogansichts-ID aus Ihrer Commerce Optimizer-Produktionsinstanz.

## Überprüfen von Drittanbieterdiensten in der Cloud {#third-party-services}

Bestätigen Sie Integrationen, die auf Ihrem Commerce-Host-System (nicht in [!DNL Adobe Commerce Optimizer]) ausgeführt werden.

▢ **Zahlungen:** Das Zahlungs-Gateway ist live und wurde getestet (Stripe, PayPal, Adyen usw.).
▢ **Versand:** Versand-API-Verbindungen funktionieren (UPS, FedEx usw.).
▢ **Versand:** Fulfillment-Plattform ist angeschlossen und getestet (z. B. ShipStation).
▢ **Integration der**-Steuerberechnung wird validiert (Avalara, TaxJar usw.).
▢ **Steuer:** Synchronisierung der Buchhaltungssoftware funktioniert (QuickBooks usw.).
▢ **Inventory:** Die Integration von PIM, ERP oder Bestandsverwaltung wird getestet und synchronisiert.
▢ **Architektur:** Das Host-Commerce-System verwaltet Zahlung, Versand, Steuern und Inventar (nicht [!DNL Adobe Commerce Optimizer]).
▢ **Architektur:** API Mesh und App Builder bleiben zwischen dem Commerce-Host-System und [!DNL Adobe Commerce Optimizer] synchron.
▢ **E-Mail** Der Versand von Transaktions-E-Mails funktioniert (Bestellbestätigung, Versand usw.).
▢ **E-Mail:** E-Mail-Vorlagen stimmen mit Ihrer Marke überein und verwenden korrekte Links.

## Überprüfen von App Builder- und API-Mesh {#app-builder-mesh}

Bestätigen der Erweiterungskonfiguration für die Produktion.

### App Builder

▢ Der Arbeitsbereich Produktion enthält alle erforderlichen Konfigurationen und Services.
▢ Die Produktions-App durchläuft Tests für verschiedene Build-Szenarien.
▢ Produktbeschränkungen und -grenzen wurden anhand der [Adobe Developer App Builder-Produktbeschreibung und der {](https://helpx.adobe.com/de/legal/product-descriptions/adobe-developer-app-builder.html){target="_blank"}}Systemeinstellungen und -beschränkungen von App Builder überprüft und [&#128279;](https://developer.adobe.com/app-builder/docs/guides/runtime_guides/system-settings).
{target="_blank"}
▢ Die Produktions-App verwendet App Builder-Produktionsendpunkte.
▢ benutzerdefinierte *Admin*-Bedienfelderweiterungen werden im Produktionsarbeitsbereich bereitgestellt.

### API-Mesh

▢ Konfigurationen und Quellen sind für die Produktion bereit.

### Ereignisse

▢ Adobe I/O Events sind konfiguriert und Abonnements werden überprüft.

## Abschließen des Storefront-Erlebnisses {#finalize-storefront}

Polnische Inhalte, SEO, Leistung, Sicherheit und CDN-Verhalten vor dem Launch.

### Inhalt und Authoring

Bestätigen des Authoring-Workflows und der Storefront-Komponenten

▢ Die Prüfung der Go-Live-Checkliste für &lbrace;1[&#128279;](https://www.aem.live/docs/go-live-checklist) AEM/EDS ist abgeschlossen.

▢ Die Authoring-Quelle ist ein dokumentbasierter oder universeller Editor (und konfiguriert).
▢ Inhalte werden mit dem Vorschau- → Veröffentlichungszyklus veröffentlicht.
▢ Inhalts- und Design-QA ist in der `.aem.live` Domain abgeschlossen.
▢ Ein Favicon ist konfiguriert und wird von der Site korrekt bereitgestellt.
▢ „da.live“ und „product visuals“ verwenden [konfigurierte](https://docs.da.live/administrators/guides/permissions) dedizierte Anmeldeinformationen.
▢ Dropins (Warenkorb, Checkout, PDP, PLP, Auth, Konto) werden [angepasst](../storefront.md) getestet.
▢ Storefront-Branding spiegelt CSS-Design-Token, Typografie und Farben wider.

### SEO und Indizierung

Bestätigen von Metadaten, URLs und crawlen Verhalten.

▢ Metadaten des Dokumenttitels sind für wichtige Seiten (insbesondere PDPs und PLPs) vorhanden. Siehe [SEO-Metadaten](https://experienceleague.adobe.com/developer/commerce/storefront/setup/seo/metadata/?lang=de){target="_blank"} in der Dokumentation zu _Adobe Commerce_.
▢ PDPs umfassen [Metadaten und strukturierte &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/seo/metadata/?lang=de){target="_blank"} (z. B. JSON-LD).
▢ Produkt-URL-Formate sind konsistent (z. B. `domain/product-name`).
▢ Vanity-URLs werden zu kanonischen URLs umgeleitet.
▢ Das Projekt enthält `robots.txt`, die ggf. eine Indizierung ermöglichen, Verweise auf Sitemaps und Blockpfade, die nicht indiziert werden sollen (z. B. `/drafts`).
▢ [Redirect](https://www.aem.live/docs/redirects)-Dateien decken URL-Änderungen aus der Migration ab (z. B. nach dem Entfernen von `.html`).
▢ Sitemap ist vorhanden und wird bei Bedarf an die Google-Suchkonsole gesendet.
▢ kanonische URLs geben `2xx` Status zurück (nicht `3xx` oder `4xx`).
▢ mehrsprachigen Websites enthalten `hreflang` Tags in der Sitemap.
▢ Der Bericht zur Abdeckung der Google-Suchkonsole ist aktuell.

### Pre-Rendering

Bestätigen Sie das Server-seitige Rendering, wo Sie es aktivieren.

▢ Vorab-Rendering ist für wichtige Seiten aktiviert. Siehe [Pre-Rendering für AEM](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-prerender/?lang=de){target="_blank"} in der Dokumentation _Adobe Commerce_.
▢-URLs werden in Kleinbuchstaben geschrieben, damit Links durch Vorab-Rendering nicht beschädigt werden.
▢ HTML-Quelle enthält Metadaten und Textinhalte, die bestätigen, dass das Pre-Rendering funktioniert.
▢ Gebietsschemata zeigen gegebenenfalls die richtigen übersetzten Seiten an.
▢ zusätzliches HTML-Markup wird [konfiguriert](https://www.aem.live/docs/redirects) nach Bedarf hinzugefügt.

### Leistung und Überwachung

Bestätigen Sie die Leistungsgrundlagen und die Analytics-Verkabelung.

▢ Ihre Storefront befolgt [Best Practices für die Leistung](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/performance/?lang=de){target="_blank"} in der Dokumentation zur _Adobe Commerce Storefront_.
▢ (Optional) Google Analytics und Google Tag Manager sind konfiguriert.
▢ Implementierung von [Storefront-](https://github.com/adobe/commerce-events/tree/main/examples/events/snowplow-debugger)) ist gültig und die Daten werden in Ihren [!DNL Live Search]- und [!DNL Product Recommendations]-Dashboards in Adobe Commerce *Admin*.
▢ Der `environment` Analytics-Parameter in der [Commerce-](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/?lang=de){target="_blank"} wird während der Entwicklung `"Testing"` und bei der Live-Schaltung `"Production"`. Siehe [Analytics-Instrumentierung](https://experienceleague.adobe.com/developer/commerce/storefront/setup/analytics/instrumentation/?lang=de){target="_blank"}.
▢ Lighthouse-Werte erfüllen Ihre Ziele (z. B. `100` auf wichtigen Seiten), wenn Sie die Anleitungen in diesem Thema beachten.

### Sicherheit und Zugriff

Bestätigen Sie Berechtigungen und Geheimnisse.

▢ entsprechenden Berechtigungen sind für DAM-Inhalte und EDS-Sites konfiguriert. Siehe [DA.live-Berechtigungen](https://da.live/docs/administration/permissions) und [Authentifizierungseinstellungen für das Authoring](https://www.aem.live/docs/authentication-setup-authoring).
▢ Die Integration von Produktvisualisierungen wird bereitgestellt. Siehe [Übersicht über den Zugriff auf AEM Cloud &#x200B;](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/accessing/overview#).
▢ Links zum Zurücksetzen des Kennworts in E-Mail-Vorlagen stimmen mit Ihrer Edge Delivery Services-Einrichtung überein. Siehe die häufig gestellten Fragen zur Storefront: [Was sollte ich tun, wenn meine Links zur E-Mail-Vorlage nach der Migration zu Edge Delivery Services oder Helix beschädigt sind?](https://experienceleague.adobe.com/developer/commerce/storefront/troubleshooting/faq/?lang=de#what-should-i-do-if-my-email-template-links-are-broken-after-migrating-to-edge-delivery-services-or-helix){target="_blank"}.
▢ Produktionsschlüssel für Integrationen und Zahlungsanbieter sind vorhanden.
▢ Domains werden auf die Zulassungsliste gesetzt und Backend-Webhooks funktionieren.

### CDN und Caching

Bestätigen Sie das CDN-, DNS- und Cache-Verhalten.

▢ Die CDN-Konfiguration verwendet den Produktions-GraphQL-Endpunkt (`yourproject.com/graphql`) für Sidekick-Erweiterungen und -Skripte (z. B. Sitemap-Generierung und Bild-Importer).
▢ Wenn Sie Adobe Commerce Fastly verwenden, ist ein CDN-Bereinigungstoken verfügbar und [Site-](https://tools.aem.live/tools/cdn-setup/index.html)) umfasst `authToken` und `serviceId`.
▢ [CDN-Konfiguration](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/content-delivery-network/?lang=de){target="_blank"} validiert das Caching und die Invalidierung.
▢ Für [Multi-Store-Setups](https://experienceleague.adobe.com/developer/commerce/storefront/setup/seo/indexing/?lang=de#multi-store-setups){target="_blank"} enthalten Catalog Service- und [!DNL Live Search]-Anfragen einen Store-spezifischen Cache-Buster (z. B. einen Abfrageparameter oder eine CDN-Regel).
▢ Push-Invalidierung funktioniert End-to-End (veröffentlichen Sie eine Änderung und überprüfen Sie sie dann auf der Produktions-Domain).
▢ DNS-TTL ist vor der Umstellung niedrig genug.
▢ DNS-A- und CNAME-Einträge sind für alle Domains und Hostnamen korrekt.
▢ Das SSL/TLS-Zertifikat wurde für die Produktions-Domain bereitgestellt und verifiziert.
▢ `www`- und Apex-Weiterleitungen verhalten sich korrekt.

## Sicherheit und Compliance {#security-compliance}

Bestätigung des Sicherheitszustands und der Compliance-Aufgaben

▢ **SSL:** Ein vertrauenswürdiges SSL-/TLS-Zertifikat ist installiert.
▢ **SSL:** HTTPS wird Site-weit erzwungen.
▢ **Zugriff:** Standardkennwörter *Admin* werden geändert und es gilt eine sichere Kennwortrichtlinie. Siehe [!DNL Adobe Commerce Optimizer] [Benutzer- und Identitätsverwaltung](../user-management.md).
▢ **Zugriff:** Die URL *Admin* ist nicht die Standardeinstellung.
▢ **Zugriff** Die Zwei-Faktor-Authentifizierung ist für alle *Admin*-Benutzer aktiviert.
▢ **Zugriff:** Es sind keine inaktiven oder nicht verwendeten Admin-Benutzer mit dem Projekt verknüpft.
▢ **Firewall:** Web Application Firewall (WAF) ist konfiguriert und verifiziert.
▢ **PCI:** Security Penetration Testing on Production (PCI-Umfang) ist abgeschlossen.
▢ **Suche:** Das Adobe Security Scan Tool ist registriert und eine erste Suche ist abgeschlossen.
▢ **Zugriff:** CORS lässt nur genehmigte Ursprünge zu.
▢ **Compliance:** Das [Modell der gemeinsamen Verantwortung](../shared-responsibility.md) für [!DNL Adobe Commerce Optimizer] ist auf dem neuesten Stand und definiert die Verantwortlichkeiten von Adobe im Vergleich zu Kunden klar.
▢ **Compliance** Die Datenschutzrichtlinie, das Cookie-Einverständnis und die DSGVO- oder CCPA-Anforderungen werden überprüft.

## Analyse und Überwachung {#analytics-monitoring}

Messung und Baselines bestätigen.

▢ **RUM:** Real User Monitoring (RUM) ist für einen Vorher-Nachher-Vergleich instrumentiert.
▢ **Analytics:** Die Datenerfassung von Adobe Experience Platform ist konfiguriert (falls zutreffend).
▢ **Analytics:** Verifiziert, dass die MarTech-Tags auf dem Produktions-Host-Namen ausgelöst werden.
▢ **Analytics:** Baseline-Analysen sind dokumentiert; nach dem Start werden Schwankungen (Seitenansichten, Absprungrate usw.) erwartet.
▢ **Ereignisse:** Das Konversions-Tracking funktioniert End-to-End (zum Warenkorb hinzufügen → zur Kasse → Bestätigung).

## Test läuft {#testing}

Qualität vor und nach dem Start prüfen.

▢ **Funktionell:** Die wichtigsten Abläufe funktionieren von Anfang bis Ende: Durchsuchen → suchen → filtern → zum Warenkorb hinzufügen → Checkout → Kontoerstellung.
▢ **Funktionell:** Zahlungs-Gateways akzeptieren echte und Testtransaktionen.
▢ **Funktional** Bestellplatzierung, Bestätigungs-E-Mail und Auftragsverfolgung.
▢ **Funktionell:** Lieferoptionen und Steuerberechnungen sind korrekt.
▢ **Funktionell** Gutscheine, Rabatte und Treueprogramme verhalten sich erwartungsgemäß.
▢ **UAT:** Die Benutzerakzeptanztests sind in der Staging- und Produktionsumgebung abgeschlossen.
▢ **Leistung:** Belastungs- und Belastungstests sind abgeschlossen, und Adobe CTA oder CSE liefert die Ergebnisse.
▢ **Leistung:** Die Seitenladezeit beträgt auf Desktop- und Mobilgeräten weniger als drei Sekunden.
▢ **Leistung:** Lighthouse-Bewertungen erfüllen Ziele auf wichtigen Seiten (z. B. über PageSpeed Insights).
▢ **Leistung:** Bilder, Skripte und Assets werden optimiert.
▢ **Kompatibilität:** Chrome, Firefox, Safari und Edge verhalten sich erwartungsgemäß.
▢ **Kompatibilität:** Responsive Layouts funktionieren auf Smartphones, Tablets und Desktop.
▢ **Kompatibilität:** Leistung ist für 3G, 4G und Wi-Fi akzeptabel.
▢ **Barrierefreiheit:** Ein Audit der Barrierefreiheit ist abgeschlossen (WCAG, Bildschirmlesehilfe, Tastaturnavigation).
▢ **Funktionell:** Es ist ein 404-Überwachungsplan nach der Markteinführung vorhanden.
▢ **UAT:** Es gibt einen Rollback-Plan, der die Tests besteht, wenn Startprobleme auftreten.

## Launch-Tag und nach dem Launch {#launch-post-launch}

Bestätigung von Kommunikations-, Support- und Folgeaufgaben.

▢ **Launch-Koordinierung:** Adobe hat das von Ihnen bestätigte Launch-Datum. Die CTA wurde per E-Mail benachrichtigt.
▢ **Support:** Die P1-Hotline-Nummer wird aufgezeichnet: US (+1) 800-497-0335, dann drücken Sie 6 für Commerce.
▢ **Support:** Ihr Team ist dafür geschult, ein Support-Ticket zu erstellen **bevor Sie** P1-Hotline anrufen.
▢ **Nach dem Start** Überprüfen Sie die Lighthouse-Werte auf der Produktions-Domain.
▢ **Nach dem Start:** Überwachen Sie die Google-Suchkonsole auf Indizierungs- und crawlen Fehler.
▢ **Nach dem Start:** Überwachen Sie 404-Berichte und fügen Sie Umleitungen für ältere URLs mit hohem Traffic hinzu.
▢ **Nach der Einführung** Bestätigen Sie die MarTech- und Analysedaten in der Produktion.
▢ **Nach dem Start:** Bitten Sie Ihren CTA, CSE oder AM, eine Überwachung mit hohem SLA-Wert zu aktivieren.
▢ Es gibt einen Plan für die Notfallwiederherstellung, der die Tests besteht.
▢ Es ist ein Prozess vorhanden, um Textbausteinpakete und Erweiterungspakete auf aktuelle Versionen zu verfolgen und zu aktualisieren.
