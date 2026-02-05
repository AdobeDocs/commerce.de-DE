---
title: '[!DNL Adobe Commerce as a Cloud Service] Versionshinweise'
description: Erfahren Sie mehr über die neuesten Funktionen und Verbesserungen in [!DNL Adobe Commerce as a Cloud Service].
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Developer, User, Leader
level: Beginner
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: cf06dec6-8d6b-413e-9977-df88373c188e
source-git-commit: 454f8f03250691ceb650893bb0b8cfda6e2204c8
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 0%

---

# Versionshinweise

Die folgenden Versionshinweise enthalten Aktualisierungen zu [!DNL Adobe Commerce as a Cloud Service].

>[!NOTE]
>
>Wenn Sie Adobe Commerce On-Premise oder Adobe Commerce in der Cloud-Infrastruktur verwenden, lesen Sie die [Versionshinweise zu Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

## Februar 2026 {#latest}

[!BADGE Sandbox]{type=Caution tooltip="Die aufgelisteten Elemente sind derzeit nur in Sandbox-Umgebungen verfügbar. Adobe stellt neue Versionen zunächst in Sandbox-Umgebungen zur Verfügung, um Zeit zum Testen bevorstehender Änderungen zu haben, bevor die Version in Produktionsumgebungen verfügbar ist."}

Die folgenden Elemente sind derzeit nur in Sandbox-Umgebungen von [!DNL Adobe Commerce as a Cloud Service] verfügbar. Diese Version wird voraussichtlich am 10. Februar 2026 in Produktionsumgebungen verschoben.

>[!BEGINSHADEBOX]

### Versandmethoden anpassen und Admin-Berichte anzeigen

An der [!DNL Commerce Admin] wurden die folgenden Verbesserungen vorgenommen:

* Verbesserte prozessexterne (Versand[Webhook-Payloads), &#x200B;](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/shipping-use-cases/#payload) benutzerdefinierte Attribute für Versandadressen einzuschließen. Durch diese Änderung können Händler benutzerdefinierte Versandmethoden implementieren. <!-- ACCS-235 -->

* Zugriff auf Admin-Berichte hinzugefügt, einschließlich Berichten für Marketing, Vertrieb, Kunden und Produkte. <!-- CCSAAS-3085 -->

### Benutzerdefinierte Rechnungsbeträge über die REST-API erfassen

Die Rechnungs-API unterstützt jetzt benutzerdefinierte Erfassungsbeträge mithilfe von Erweiterungsattributen. Mit dieser Funktion können Händler einen benutzerdefinierten Betrag erfassen, wenn sie eine Rechnung mithilfe des `POST V1/order/:orderId/invoice` REST-Endpunkts erstellen und den Betrag im Feld &quot;`extension_attributes.custom_capture_amount`&quot; der Payload angeben. Dadurch haben Händler größere Flexibilität bei Teilerfassungen und speziellen Zahlungsszenarien. Wenden Sie sich an Ihren Support-Mitarbeiter, um diese Funktion zu aktivieren. <!-- ACCS-186, ACCS-197, ACCS-143 -->

>[!NOTE]
>
>Aufgrund rechtlicher Einschränkungen ist der benutzerdefinierte Erfassungsbetrag nur in der Region Nordamerika (NA) und anderen Regionen verfügbar, in denen eine Übererfassung von Zahlungen zulässig ist.

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Der Filter Couponraster wurde korrigiert, sodass alle benutzerdefinierten Coupons angezeigt werden, die über die API oder durch Importieren erstellt wurden. <!-- CCSAAS-4509 -->

* Es wurde ein Problem in der [!DNL Storefront Compatibility B2B Package] behoben, bei dem die `setNegotiableQuoteShippingAddress`-Mutation die manuell eingegebenen Adressen nicht im Adressbuch des Kunden speicherte, selbst wenn `save_in_address_book` auf `true` gesetzt war. <!-- LYNX-1031 -->

<!-- The above change will also be covered by the B2B changelog published on February 13, 2026. -->

* Es wurde ein Problem behoben, bei dem Produktbilder aufgrund beschädigter [!DNL Edge Delivery Services] in benutzerdefinierten Attributen im Zusammenhang mit Asset-Rollen nicht richtig in `no_selection` angezeigt wurden. <!-- ACAP-1206 -->

* Es wurde ein Problem behoben, das den Zugriff von zusammengeführten Benutzerkonten mit null Vornamen- oder Nachnamenwerten auf den Commerce-Admin verhinderte. <!-- ACCS-200 -->

* Die Konfiguration des Asset-Wählers wurde vereinfacht, indem automatisch regionsspezifische IMS-Client-IDs bereitgestellt wurden. Händler müssen keine Support-Tickets mehr senden, um den Asset-Selektor für die Zuordnung von Produktkategoriebildern zu Assets zu konfigurieren. Das System verwendet jetzt automatisch dedizierte IMS-Client-IDs, die auf der Commerce-Region basieren. <!-- ACCS-175 -->

* Verschiedene Leistungs- und Optimierungsverbesserungen. <!-- CCSAAS-4485, CCSAAS-4497, ACCS-196 -->

{{accs-release}}

>[!ENDSHADEBOX]

## Januar 2026

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 20. Januar 2026 in Produktionsumgebungen von [!DNL Adobe Commerce as a Cloud Service] veröffentlicht.

>[!BEGINSHADEBOX]

### B2B-Drop-ins

An den B2B-Drop-in-Komponenten wurden die folgenden Änderungen vorgenommen:

* [!DNL Commerce Storefront on Edge Delivery Services] enthält jetzt [B2B-Drop-in-Komponenten](http://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/). Die folgenden B2B-Drop-ins sind jetzt verfügbar:

   * **[Unternehmensverwaltung](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/company-management/)** - Ermöglicht die Verwaltung von Unternehmensprofilen und rollenbasierte Berechtigungen für Adobe Commerce-Storefronts.
   * **[Unternehmens-](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/company-switcher/)**: Bietet eine UI-Komponente, mit der Benutzende zwischen mehreren Unternehmen wechseln können, denen sie zugeordnet sind.
   * **[Bestellungen](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/purchase-order/)** - Verwaltet Bestellungen-Workflows, Genehmigungsregeln und den Bestellverlauf für B2B-Transaktionen.
   * **[Angebotsverwaltung](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/quote-management/)** - Ermöglicht verhandelbare Angebote für B2B-Kunden mit Angebotsanfrage-, Verhandlungs- und Genehmigungs-Workflows.
   * **[Anforderungslisten](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/requisition-list/)**: Bietet Tools zum Erstellen und Verwalten von Anforderungslisten für Wiederholungskäufe und Massenbestellungen.

* Das Kompatibilitätspaket für die B2B-Storefront wurde veröffentlicht. Dieses Paket erweitert das [!DNL Adobe Commerce] B2B-GraphQL-Schema , um die Entwicklung auf B2B-Systemen zu verbessern.

<!-- 
* [!DNL Commerce Storefront on Edge Delivery Services] now includes [B2B drop-in components](http://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/). For a complete list of available B2B drop-in blocks, refer to the [storefront documentation](http://experienceleague.adobe.com/developer/commerce/storefront/merchants/b2b-commerce-blocks/).

* Released the [B2B Storefront Compatibility Package](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/storefront-compatibility-b2b/). This package enhances the [!DNL Adobe Commerce] B2B GraphQL schema to help improve development on B2B systems. -->

### Klickbare Links zu externen Versandtrackern

Wandeln Sie die in den Kunden-E-Mails enthaltenen Sendungsverfolgungsnummern aus reinem Text in anklickbare Links um, indem Sie [benutzerdefinierte Tracking-URLs aktivieren](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/shipping-settings#shipment-tracking-urls). Diese Funktion wird für USPS, UPS, FedEx und DHL unterstützt. <!-- See PR #716 in commerce-admin -->

### Google reCAPTCHA Enterprise-Support

[!DNL Adobe Commerce as a Cloud Service] Storefronts unterstützen jetzt [reCAPTCHA Enterprise](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha-enterprise). Diese Funktion bietet erweiterten Bot-Schutz durch die Verwendung von adaptiver Risikoanalyse und maschinellem Lernen, um menschliche Benutzer genau von automatisierten Bots zu unterscheiden. Es erhöht die Website-Sicherheit, verhindert betrügerische Aktivitäten und reduziert Spam und Missbrauch, um ein vertrauenswürdiges Einkaufserlebnis zu erhalten. <!-- CCSAAS-4242 -->

### Instanzspezifischer Admin-Zugriff

Sie können jetzt [&#x200B; einzelnen &#x200B;](./user-management.md#add-users)-Instanzen in der Admin Console [!DNL Adobe Commerce as a Cloud Service]Benutzerzugriff zuweisen“. <!-- CCSAAS-4337 --><!-- See PR #332 -->

### Beobachtbarkeit

Durch die Verwendung von [!DNL App Builder] erhalten Sie einen tieferen Einblick in Ihre [!DNL Adobe Commerce as a Cloud Service]-Instanz mit [OpenTelemetry Observability](https://developer.adobe.com/commerce/extensibility/observability/), die jetzt automatisch verfügbar ist. OpenTelemetry bietet Metriken, Protokolle und Traces, mit denen Sie die Leistung überwachen, Probleme schneller beheben und Ihre Storefront optimieren können. Diese Funktion ermöglicht proaktive Einblicke in den Systemzustand und verbessert die Zuverlässigkeit für Ihre Kunden.

>[!NOTE]
>
>Die OpenTelemetry-Beobachtbarkeit erfordert die Verwendung von [!DNL App Builder] oder anderen OOPE-Angeboten (Out-of-Process-Erweiterbarkeit).

### Preisstufe für Katalogpreisregeln

Sie können jetzt mehrstufige Preisnachlässe mit Rabatten für Katalogregeln mithilfe von [Katalogpreisregeln](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier#enable-tier-pricing-for-catalog-price-rules) kombinieren. Mit dieser Verbesserung können Sie dynamischere und wettbewerbsfähigere Preisstrategien entwickeln, die Masseneinkäufe belohnen und gleichzeitig Rabatte auf die Werbeaktionen gewähren. Das Ergebnis ist eine größere Flexibilität, um Kunden zu gewinnen, den Bestellwert zu steigern und Konversionen zu fördern.<!-- See PR #708 in commerce-admin -->

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen in dieser Version:

* Fehlerkorrektur - Beim Hochladen einer Datei auf S3 tritt jetzt kein Fehler mehr auf. <!-- CCSAAS-4189 -->

* Es wurde ein `User is not entitled to access this instance` behoben, der beim Anmelden bei Commerce Admin oder beim Zugriff auf die REST-API auftreten konnte. <!-- CCSAAS-4324 -->

* Fehlerkorrektur - Bei der Vorschau eines Newsletters aus dem Newsletter-Vorlagenraster oder beim Einreihen in die Warteschlange tritt jetzt kein Fehler mehr auf. <!-- CCSAAS-4398 -->

* Fehlerkorrektur - Beim Klicken auf die Schaltfläche `404`Daten neu laden [!UICONTROL **im Admin-Dashboard tritt jetzt kein**] mehr auf. <!-- CCSAAS-4468 -->

* Es wurde ein Problem behoben, bei dem benutzerdefinierte Produktattribute nicht über die REST-API aktualisiert werden konnten, wenn [!DNL AEM Assets integration] aktiviert war und das Produkt Bilder hatte. <!-- ACAP-1178 -->

* Verschiedene Leistungs- und Optimierungsverbesserungen.<!-- CCSAAS-4255 --><!-- CCSAAS-4233 --><!-- CCSAAS-4220 --><!-- CCSAAS-4252 --><!-- CCSAAS-4330 --><!-- CCSAAS-3669 --><!-- CCSAAS-4462 -->

{{accs-release}}

>[!ENDSHADEBOX]

## November 2025

>[!BEGINSHADEBOX]

### Verbesserungen

* [Benutzerverwaltung](./user-management.md) - hat die Rolle **Produktadministrator** in der Admin Console geändert, um den Benutzerzugriff auf den Commerce-Administrator automatisch zu aktualisieren. <!-- CCSAAS-3012 -->

* Amazon Es wurde die Möglichkeit hinzugefügt, verhandelbare Angebotsanhänge sowie Dateien und Bilder, die mit Kunden und Kundenadressen verknüpft sind, mithilfe von vordefinierten URLs in [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/uploads) und [REST3 hochzuladen und &#x200B;](https://developer.adobe.com/commerce/webapi/rest/modules/s3-uploads) abzurufen. Mit REST können Sie auch Kategoriebilder hochladen. <!-- CCSAAS-3250 -->

* Die Endpunkte `POST /V1/customers` und `PUT /V1/customers/{customerId}` wurden der [REST-API“ hinzugefügt](https://developer.adobe.com/commerce/webapi/rest/reference/) um Kunden zu erstellen und zu aktualisieren. Diese Endpunkte erfordern eine IMS-Autorisierung. <!-- CCSAAS-3112 -->

* Es wurde die [`exchangeOtpForCustomerToken`-Mutation hinzugefügt](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/exchange-otp-customer-token/) für die die E-Mail-Adresse eines Käufers und ein einmaliges Kennwort (One-Time Password, OTP) erforderlich sind und für die im Austausch ein Kunden-Token empfangen wird. Diese Mutation wird normalerweise in Szenarien verwendet, in denen sich ein Kunde mithilfe eines OTP authentifizieren muss, der an seine E-Mail oder sein Telefon gesendet wird.

* Wenn eine im Konfigurationsbildschirm [!UICONTROL **E-Mail-Adressen speichern**] im Admin-Bereich definierte Adresse einen Wert enthält, der auf `example.com` endet, sendet Commerce keine E-Mails an diese Adresse. Stattdessen protokolliert das System, dass die E-Mail nicht gesendet wurde.  <!-- CCSAAS-3533 -->

#### Benutzerdefinierte Bestellattribute

* Admin-Benutzer können jetzt [benutzerdefinierte Bestellattribute](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#custom-order-attributes) direkt in den Bildschirmen „Bestellansicht“, „Bearbeiten“ und „Erstellen“ im Admin-Bedienfeld anzeigen und bearbeiten. Diese Verbesserung verbessert die Verwaltung von benutzerdefinierten Bestelldaten, die über GraphQL erstellt wurden. <!-- CEXT-5044 -->

>[!ENDSHADEBOX]
