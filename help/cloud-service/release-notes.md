---
title: '[!DNL Adobe Commerce as a Cloud Service] Versionshinweise'
description: Erfahren Sie mehr über die neuesten Funktionen und Verbesserungen in [!DNL Adobe Commerce as a Cloud Service].
feature-set: Commerce
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Developer, User, Leader
level: Beginner
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
exl-id: cf06dec6-8d6b-413e-9977-df88373c188e
TQID: 'https://experienceleague.adobe.com/NSIeUn0B5i19ldOZSVu4PJy9vqY4NGrXY1Y485sV09U'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eb30f47f-d87a-400f-8f78-63ce7979ff56
source-git-commit: ef32511703a96b5f4db32d54229e9a7cbe961f12
workflow-type: tm+mt
source-wordcount: 4182
ht-degree: 0%

---

# Versionshinweise

Die folgenden Versionshinweise enthalten Aktualisierungen zu [!DNL Adobe Commerce as a Cloud Service].

>[!NOTE]
>
>Wenn Sie Adobe Commerce On-Premise oder Adobe Commerce in der Cloud-Infrastruktur verwenden, lesen Sie die [Versionshinweise zu Adobe Commerce](https://experienceleague.adobe.com/de/docs/commerce-operations/release/notes/overview).

## Juni 2026 - #1 {#latest}

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

<!-- [!BADGE Sandbox]{type=Caution tooltip="The items listed are currently only available in Sandbox environments. Adobe makes new releases available in Sandbox environments first to provide time to test upcoming changes before the release is available on Production environments."} -->

Die folgenden Elemente wurden am 4. Juni 2026 in Produktionsumgebungen veröffentlicht.

>[!BEGINSHADEBOX]

### Hinzufügen und Bearbeiten von benutzerdefinierten Gutscheincodes in der Admin Console

Händler können jetzt [benutzerdefinierte Gutscheincodes erstellen und bearbeiten](https://experienceleague.adobe.com/de/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon#method-3-custom-coupon-codes) direkt über die [!DNL Commerce Admin] auf manuelle Warenkorbpreisregeln. Eine neue Schaltfläche [!UICONTROL **Benutzerdefinierten Gutschein hinzufügen**] ist im Abschnitt [!UICONTROL **Verwalten von Gutscheincodes**] verfügbar, wenn Sie eine Warenkorb-Preisregel bearbeiten. <!-- CCSAAS-4508 -->

### Verfolgen von Sendungen mit standardmäßigen und benutzerdefinierten Spediteuren

Die Nachverfolgung von Bestellungen ist jetzt zuverlässig für standardmäßige und benutzerdefinierte Versanddienstleister in der [!DNL Commerce Admin], sodass Händler konsistente Tracking-Erlebnisse nach dem Kauf bereitstellen können. Zuvor konnte die Auswahl eines Providers wie UPS oder FedEx und die Anwendung einer Tracking-ID verhindern, dass der Tracking-Link angezeigt wurde. Es ist keine Händleraktion erforderlich, um dieses Verhalten wiederherzustellen. Die Unterstützung für Tracking-Links ist auch für [benutzerdefinierte Provider](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/shipping-reference/) verfügbar, die mit dem [!DNL App Builder Integration Starter Kit] erstellt wurden. <!-- ACCS-891 -->

### Anzeigen von Attributeingabetypen im Raster „Produktattribute“

Eine neue Spalte [!UICONTROL **Attributtyp**] ist jetzt im Raster Produktattribute in ([!UICONTROL **Stores**] > _[!UICONTROL Attributes]_>[!UICONTROL **Product**]) sichtbar, die den Eingabetyp (z. B. Textfeld, Dropdown oder Ja/Nein) für jedes Produktattribut anzeigt, einschließlich der von Erweiterungen bereitgestellten Typen. Dies erleichtert die Identifizierung und Verwaltung von Attributen bei der Arbeit mit großen Attributsätzen. <!-- ACCS-925 -->

### Anpassen der Antwortkopfzeile für benutzerdefinierte E-Mails

Händler können jetzt den Header [!UICONTROL **Antwort an**] konfigurieren, der vom Endpunkt [POST /rest/V1/custom-email/send](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/custom-email/) verwendet wird, sodass Antworten von Kunden an eine andere Adresse als den Absender weitergeleitet werden können. <!-- ACCS-1037 -->

### Zeigen Sie die Stufenpreise auf der Seite „Produktbearbeitung“ in großen freigegebenen Katalogumgebungen an.

Händler mit einer großen Anzahl freigegebener Kataloge können jetzt auf die schreibgeschützte Registerkarte [!UICONTROL **Stufenpreise**] auf der Seite „Produktbearbeitung“ im [!DNL Commerce Admin] zugreifen. <!-- CCSAAS-4922 -->

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Es wurde ein Problem behoben, bei dem der REST-Endpunkt POST `V1/async/custom-email/send` einen `UnstructuredArray` Validierungsfehler zurückgab. Der asynchrone Endpunkt funktioniert jetzt konsistent mit dem synchronen POST-`V1/custom-email/send`-Endpunkt. <!-- ACCS-921 -->

* Es wurde ein Problem behoben, bei dem benutzerdefinierte serialisierbare Attribute für Entitäten wie Unternehmen unbeabsichtigt gelöscht wurden, wenn die Entität über REST aktualisiert wurde, ohne die benutzerdefinierten Attribute in die Payload einzubeziehen. Benutzerdefinierte Attribute werden jetzt beibehalten, wenn sie nicht angegeben werden. <!-- ACCS-946 -->

* Es wurde ein Fehler „Verbraucher ist nicht autorisiert“ behoben, der die Gastanmeldung bei GraphQL verhindern konnte, wenn der `X-Adobe-Company`-Header in der Anfrage vorhanden war. <!-- ACCS-949 -->

* Fehlerkorrektur - Das Bearbeiten oder Löschen einer Firma in der [!DNL Commerce Admin] schlägt jetzt nicht mehr fehl, nachdem über den REST-Endpunkt PUT `V1/customers/companies` REST eine Kundin oder ein Kunde der Firma zugewiesen wurde. <!-- ACCS-856 -->

* Es wurde ein Problem mit veralteten Auftragsrasterstatus behoben. <!-- CCSAAS-4915 -->

* Fehlerkorrektur - Auf der [!DNL Commerce Admin], auf der Dateien, die als Beispiele und Links zu herunterladbaren Produkten angehängt sind, beim Zugriff auf die Seite zur Produktbearbeitung einen `404` zurückgaben, tritt jetzt kein Fehler mehr auf. <!-- CCSAAS-4394 -->

* Fehlerkorrektur - Beim Erstellen einer Sendung für eine Bestellung, die konfigurierbare Produkte enthält, tritt jetzt kein Fehler mehr wegen des „Undefined Array Key &#39;simple_sku&#39;&quot; mehr auf. <!-- CCSAAS-4877 -->

* Die `guestOrderByToken` GraphQL-Abfrage gibt jetzt eine aussagekräftigere Fehlermeldung zurück, wenn sie mit einem falsch formatierten Token statt mit einem internen Server-Fehler aufgerufen wird. <!-- CCSAAS-4921 -->

* Die `customer` GraphQL-Abfrage gibt jetzt eine informativere Fehlermeldung zurück, wenn Kundenbestellungen nicht geladen werden können. <!-- ACCS-867 -->

* Der GET- `V1/customers/{customerId}` REST-Endpunkt gibt jetzt das `assistance_allowed` Konfigurationsfeld zurück. <!-- USF-4132 -->

{{accs-release}}

>[!ENDSHADEBOX]

## Mai 2026 - #1

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 7. Mai 2026 in Produktionsumgebungen veröffentlicht.

>[!BEGINSHADEBOX]

### reCAPTCHA für programmgesteuerte OTP-Authentifizierung überspringen

Mit einer neuen Konfigurationsoption können Sie die reCAPTCHA-Validierung für die [`exchangeOtpForCustomerToken`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/exchange-otp-customer-token/) GraphQL-Mutation überspringen. Dies ermöglicht B2B-Punchout-Workflows, bei denen der einmalige Passwortaustausch (OTP) programmgesteuert ohne Formulareingabe initiiert wird, was die reCAPTCHA-Validierung überflüssig macht. Diese Funktion baut auf der Funktion [einmaligen Code-Anmeldung](https://experienceleague.adobe.com/de/docs/commerce-admin/customers/customer-accounts/manage/login-as-customer){target="_blank"} auf, die mit der Version vom März 2026 eingeführt wurde. Die `exchangeOtpForCustomerToken`-Mutation erfordert standardmäßig weiterhin reCAPTCHA, wenn reCAPTCHA für die Kundenanmeldung aktiviert ist. Wenden Sie sich an Ihren Adobe Commerce Customer Success Manager, um diese Option zu aktivieren. <!-- ACCS-850 -->

### Teilweise fakturierte Bestellungen bearbeiten

Die Schaltfläche [!UICONTROL **Bearbeiten**] ist jetzt auf dem Bildschirm [!UICONTROL **Bestellansicht**] für teilweise fakturierte Bestellungen verfügbar, sodass Händler mehr Flexibilität haben, noch in Bearbeitung befindliche Bestellungen zu ändern. Zuvor konnten Bestellungen mit Rechnungen nicht bearbeitet werden, auch wenn nicht fakturierte Artikel übrig blieben. Solange ein beliebiger Artikel in der Bestellung noch fakturiert werden kann, kann die Bestellung bearbeitet werden. Händler mit benutzerdefinierten Integrationen, die sich auf die vorherige Bearbeitungsbeschränkung stützen, sollten ihre Workflows überprüfen. <!-- ACCS-849 -->

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Es wurde ein Problem behoben, bei dem das `stock_item`-Erweiterungsattribut im `GET /V1/products` REST-API-Listenendpunkt nicht zurückgegeben wurde. Die Antwort stimmt jetzt mit dem dokumentierten API-Vertrag überein. <!-- ACCS-819 -->

* Es wurde ein Problem behoben, bei dem Links zum Zurücksetzen des Kennworts in E-Mails einen 404-Fehler zurückgaben. <!-- ACCS-797 -->

* Verbesserte Abfrageleistung des Auftragsverlaufs für Unternehmen, die Datumsbereichsfilter verwenden. <!-- ACCS-859 -->

* Es wurde ein Problem behoben, bei dem Benutzer von B2B-Unternehmen Peer-Bestellungen von sehen konnten, bevor ein Benutzer dem Unternehmen beitrat. <!-- ACCS-859 -->

* Es wurden Checkout-Timeout-Probleme behoben, die sich beim Laden von Anführungszeichen mit aktiviertem `trigger_recollect` auf die REST-API-Leistung auswirken konnten. <!-- CCSAAS-4904 -->

* Es wurden Seitenladeprobleme behoben, die nach dem Senden einer Bestellung im [!DNL Commerce Admin] auftreten konnten. <!-- CCSAAS-4413 -->

* Es wurde ein Problem behoben, bei dem Bestellungen mit demselben Zeitstempel veraltete Bestellstatusinformationen im Auftragsraster anzeigen konnten. <!-- CCSAAS-4890 -->

{{accs-release}}

>[!ENDSHADEBOX]

## April 2026 - #3

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 27. April 2026 in Produktionsumgebungen veröffentlicht.

>[!BEGINSHADEBOX]

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Es wurde der Endpunkt `GET /V1/order-statuses` REST-API zum Abrufen aller konfigurierten Bestellstatus mit ihren Statuszuweisungen hinzugefügt. <!-- CEXT-6100 -->

* Es wurde ein Problem behoben, das dazu führte, dass `custom_attributes` für Entitäten wie Bestellung, Warenkorb, Rechnung, Gutschrift und Firma nicht im REST-Schema angezeigt wurden. <!-- CCSAAS-4818 -->

* Doppelte Nachrichtenverarbeitungsfehler (`MessageLockException`) im asynchronen Bulk-API-Verbraucher behoben. <!-- CCSAAS-4805 -->

* Anzahl der Produktattribute, die jetzt als Von-/Bis-Bereichsfilter im [!DNL Commerce Admin] Produktraster gerendert werden, wenn das Attribut für Filteroptionen aktiviert ist. <!-- ACCS-761 -->

* Es wurde ein Problem behoben, bei dem in E-Mails zu Warenkorbabbruch bei Verwendung von [!DNL AEM Assets] keine Produktbilder angezeigt wurden. <!-- ACCS-798 -->

* Fehlerkorrektur - Beim Hinzufügen von Dateien, Beispielen oder Links zu herunterladbaren Produkten tritt jetzt der Fehler „Max. Upload-Größe“ nicht mehr auf. <!-- ACCS-813 -->

* Fehlerkorrektur - Beim Speichern eines Produkts, das mehreren freigegebenen Katalogen zugewiesen ist, tritt jetzt kein Fehler mehr auf. <!-- ACCS-788 -->

* Es wurde ein Problem behoben, bei dem die Abfrage zum Auftragsverlauf langsam sein und zu Fehlern wegen unzureichendem Arbeitsspeicher in der Datenbank für Unternehmen mit vielen Bestellungen führen konnte. <!-- ACCS-808 -->

* Fehlerkorrektur - Die Validierung der Importdatei kann jetzt fehlschlagen. <!-- CCSAAS-4364 -->

* Die **[!UICONTROL Recently Viewed/Compared Products]**-Konfiguration wurde aus dem Abschnitt **[!UICONTROL Catalog]** in **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**&#x200B;entfernt, da sie in [!DNL Adobe Commerce as a Cloud Service] Admin nicht unterstützt wird. <!-- ACCS-793 -->

>[!ENDSHADEBOX]

## April 2026 - #2

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

<!-- [!BADGE Sandbox]{type=Caution tooltip="The items listed are currently only available in Sandbox environments. Adobe makes new releases available in Sandbox environments first to provide time to test upcoming changes before the release is available on Production environments."} -->

Die folgenden Elemente wurden am 16. April 2026 in Produktionsumgebungen veröffentlicht.

>[!BEGINSHADEBOX]

### Implementieren benutzerdefinierter Angebotsumfänge mit Webhooks

Der `plugin.magento.out_of_process_totals_collector.api.get_total_modifications.execute` [Webhook](https://developer.adobe.com/commerce/extensibility/webhooks/) ist jetzt in [!DNL Adobe Commerce as a Cloud Service] verfügbar. Verwenden Sie sie, um Änderungen an benutzerdefinierten Anführungssummen durch prozessexterne Erweiterbarkeit zu implementieren. <!-- CEXT-5896 -->

### Wiederverwendbare E-Mail-Erinnerungsregeln (experimentell)

>[!IMPORTANT]
>
>Diese Funktion ist experimentell und muss aktiviert werden, indem Sie sich an Ihren Adobe Commerce Customer Success Manager wenden oder ein Support-Ticket erstellen.

[E-Mail-Erinnerungsregeln](https://experienceleague.adobe.com/de/docs/commerce-admin/marketing/communications/email-reminders/email-reminder-rules#rule-repeatability) unterstützen jetzt eine optionale Einstellung für die Wiederverwendbarkeit von Regeln, mit der dieselbe Regel erneut auf einen Kunden angewendet werden kann, nachdem die ursprüngliche Trigger-Bedingung nicht mehr gilt.

Wenn beispielsweise ein Kunde einen Warenkorb verlässt, den Kauf abschließt und später einen neuen Warenkorb aufgibt, kann die Regel erneut in Trigger treten. Ohne diese Einstellung wird ein Kunde, der den ursprünglichen Trigger löscht, dauerhaft von zukünftigen Übereinstimmungen derselben Regel ausgeschlossen.

### Auswertung „Zahlungsdienste-Transaktionen“ anzeigen

Wenn Sie [[!DNL Payment Services]](https://experienceleague.adobe.com/de/docs/commerce/payment-services/get-started/production) aktiviert haben, ist die [Dashboard-Benutzeroberfläche](../payment-services/payments-home.md) jetzt in der [!DNL Commerce Admin] verfügbar und bietet Zugriff auf den [Transaktionsbericht](../payment-services/reporting.md#transactions-report-view) zum Anzeigen und Verwalten von Zahlungstransaktionen. <!-- PAY-6510 -->

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Fehlerkorrektur - Auf der Seite „Freigegebene Kataloge - Firmen zuweisen“ tritt jetzt kein 500-Fehler mehr auf, wenn große freigegebene Kataloge mit der Admin-Benutzeroberfläche SDK verwendet werden. <!-- CCSAAS-4783 -->

* Es wurde ein Problem behoben, bei dem Firmenkunden keine eigenen Bestellungen sehen konnten, wenn diese Bestellungen aufgegeben wurden, bevor der Kunde dem Unternehmen zugewiesen wurde. <!-- ACCS-746 -->

>[!ENDSHADEBOX]

## April 2026

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 1. April 2026 in Produktionsumgebungen veröffentlicht.

>[!BEGINSHADEBOX]

### Hinzufügen von Dateien zu Produkten

[!DNL Adobe Commerce as a Cloud Service] unterstützt jetzt [Hinzufügen von Dateien zu Produkten](./product-files.md) mithilfe von Produktattributen vom Typ „Datei“. Sie können Dateien manuell auf der Seite zur Produktbearbeitung, programmgesteuert über die REST-API oder stapelweise hochladen, indem Sie externe URLs in CSV bereitstellen. <!-- ACCS-535, ACCS-565 -->

### Überprüfen Sie den Preis und den Status des Warnhinweis-Abonnements über GraphQL.

Mit den neuen GraphQL-Abfragen [`isSubscribedProductAlertStock`](https://developer.adobe.com/commerce/webapi/graphql/schema/products/queries/is-subscribed-product-alert-stock/){target="_blank"} und [`isSubscribedProductAlertPrice`](https://developer.adobe.com/commerce/webapi/graphql/schema/products/queries/is-subscribed-product-alert-price/){target="_blank"} können Storefronts bestimmen, ob ein Käufer bereits Aktien- oder Preiswarnhinweise für ein Produkt abonniert hat. <!-- ACCS-334 -->

### Erstellen numerischer Produktattribute zur Unterstützung negativer Werte

Ein neuer `numeric` [Eingabetyp für Produktattribute](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/attributes-input-types) ermöglicht es Händlern, Dezimalattribute zu erstellen, die negative Werte unterstützen. <!-- ACCS-600 -->

### Abfrage einer reCAPTCHA-Konfiguration für mehrere Formulare in einer GraphQL-Anfrage

Die [`recaptchaFormConfigs` Abfrage &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/store/queries/recaptcha-form-configs/) Konfigurationsdetails für mehrere Formulartypen in einer einzigen Anfrage zurückgeben. <!-- ACCS-628 -->

### Alle Firmenbestellungen mit neuer B2B-Berechtigung anzeigen

Eine neue `view_all_company_orders` [Unternehmensrolle](https://developer.adobe.com/commerce/webapi/rest/b2b/roles/) ermöglicht es B2B-Unternehmenskunden, alle Bestellungen innerhalb ihres Unternehmens anzuzeigen, einschließlich historischer Bestellungen, die von Admin-Benutzern erstellt wurden. <!-- ACCS-675 -->

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Sie können jetzt die Ergebnisse der Auftrags- und Unternehmens-REST-API mit entsprechenden benutzerdefinierten Attributen filtern, um Szenarien wie Suchvorgänge für unternehmensweite Aufträge zu unterstützen. <!-- ACCS-633 -->

* Es wurde ein Fehler behoben, der in der Browser-Entwicklerkonsole angezeigt werden konnte. <!-- CCSAAS-4650 -->

* Fehlerkorrektur - Beim Stornieren einer Gastbestellung mit Bestellkommentaren tritt jetzt kein Fehler mehr auf. <!-- ACCS-674 -->

* Fehlerkorrektur - Jetzt tritt kein Fehler mehr auf, wenn ein gruppiertes Produkt mit vielen zugehörigen Artikeln zu einer Anforderungsliste hinzugefügt wird. <!-- ACCS-627 -->

>[!ENDSHADEBOX]

## März 2026 - #2

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 24. März 2026 in Produktionsumgebungen veröffentlicht.

>[!BEGINSHADEBOX]

### Melden Sie sich als Kunde mit einmaligen Codes an

Admins können jetzt [einmalige Codes) über die [!DNL Commerce Admin]- und REST](https://experienceleague.adobe.com/de/docs/commerce-admin/customers/customer-accounts/manage/login-as-customer)API für den Kundidentitätswechsel generieren. Der einmalige Code kann über die `generateCustomerToken`- oder `exchangeOtpForCustomerToken` GraphQL-Mutationen in ein Kunden-Zugriffstoken umgetauscht werden, sodass für verkäuferunterstützte Einkaufsszenarien passwortlose Abläufe „Als Kunde anmelden“ möglich sind. <!-- ACCS-404 -->

Anleitungen zur Implementierung dieser Funktion mithilfe von APIs finden Sie in der Dokumentation [REST-](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/login-as-customer/)) und [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/) .

### Verwalten von Geschenkkartenkonten über die REST-API

[Geschenkkartenkonten](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/gift-card-accounts/) können jetzt über die REST-API erstellt, aktualisiert, gelöscht und abgefragt werden. Darüber hinaus ist die Unterstützung von JSON-Massenimporten über den `/V1/import/json`-Endpunkt verfügbar, sodass bei Drittanbieterintegrationen Geschenkgutscheine programmgesteuert synchronisiert werden können. <!-- ACCS-476 -->

### Trigger-Transaktions-E-Mails über die REST-API

Mit einem neuen REST-API-Endpunkt (`POST /V1/custom-email/send`) können Sie bei Bedarf Transaktions-E-Mails von [Triggern &#x200B;](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/custom-email/), indem Sie eine E-Mail-Vorlagen-ID, eine Empfänger-E-Mail und Vorlagenvariablen angeben. Die API unterstützt verschachtelte Arrays als Vorlagenvariablen für komplexe E-Mail-Inhalte. <!-- ACCS-325, ACCS-481 -->

### Abonnieren Sie den Webhook „Out-of-Process Shipping Get-Rates“

Der `plugin.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates` Webhook ist jetzt in der Liste Admin Webhooks in [!DNL Adobe Commerce as a Cloud Service] verfügbar. Verwenden Sie sie zur Implementierung [benutzerdefinierter Versandmethoden](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/shipping-use-cases/#shipping-methods). <!-- ACCS-478 -->

### Hochladen von PDFs und anderen Dateien über Produktattribute

Mit einer neuen „Datei“ [Attributeingabetyp](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/attributes-input-types) können Sie Attributsätze erstellen, in denen Sie Dateien wie PDFs in einzelne Produkte hochladen können. Sie können die zulässigen Dateierweiterungen und die maximale Dateigröße konfigurieren, indem Sie zu [!UICONTROL **Stores**] > [!UICONTROL **Konfiguration**] > [!UICONTROL _Katalog_] > [!UICONTROL **Produktdateiattribute**] navigieren. <!-- ACCS-535, ACCS-565 -->

### Benutzerdefinierte Unternehmensattribute konfigurieren

Administratoren können jetzt benutzerdefinierte Attribute für Unternehmen auf der Seite „Unternehmen bearbeiten“ im [!DNL Commerce Admin] verwalten. Benutzerdefinierte Attribute können über die Admin-Benutzeroberfläche konfiguriert, gespeichert und für [!DNL Adobe Commerce as a Cloud Service] validiert werden.

Um die benutzerdefinierten Attribute eines Unternehmens zu konfigurieren, navigieren Sie zu [!UICONTROL **Kunden**] > [!UICONTROL **Firmen**] und wählen Sie ein Unternehmen aus, um die Bearbeitungsseite zu öffnen. Wählen Sie dann die Registerkarte [!UICONTROL **Benutzerdefinierte Attribute**], um neue Attribute hinzuzufügen.
<!-- ACCS-294 -->

### Abonnieren von Preis- und Aktienwarnhinweisen über GraphQL

EDS-Storefronts funktionieren jetzt mit [Preis- und Lagerwarnungen](https://experienceleague.adobe.com/de/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup). <!-- ACCS-334 -->

Darüber hinaus gibt es mehrere neue GraphQL-Mutationen, um Preis- und Aktienwarnungen zu abonnieren oder zu kündigen:

+++Neue GraphQL-Mutationen

```graphql
mutation {
  subscribeProductAlertStock(input: { sku: "ADB111" }) {
    success
    message
  }
}
```

```graphql
mutation {
  unsubscribeProductAlertStock(input: { sku: "ADB111" }) {
    success
    message
  }
}
```

```graphql
mutation {
  unsubscribeProductAlertStockAll {
    success
    message
  }
}
```

```graphql
mutation {
  subscribeProductAlertPrice(input: { sku: "ADB112" }) {
    success
    message
  }
}
```

```graphql
mutation {
  unsubscribeProductAlertPrice(input: { sku: "ADB115" }) {
    success
    message
  }
}
```

```graphql
mutation {
  unsubscribeProductAlertPriceAll {
    success
    message
  }
}
```

+++

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Die Rolle [!UICONTROL Sales] > [!UICONTROL View Orders] Unternehmen funktioniert jetzt erwartungsgemäß. <!-- ACCS-604 -->

* Das Attribut `last_login_at`-Kundenerweiterung ist jetzt über die REST-API verfügbar, sodass Integrationen das neueste Anmeldedatum für jeden Kunden abrufen können. <!-- ACCS-555 -->

* Es wurde ein Problem mit den Vorschlägen für [!DNL AEM Assets] Integrationsformulare behoben. <!-- ACCS-209 -->

* Es wurde ein Problem behoben, bei dem Massenzuweisungen von Unternehmen und Aufhebungen von Zuweisungen im freigegebenen Katalograster einen Fehler verursachen konnten. <!-- CCSAAS-4614 -->

* Es wurde ein Problem behoben, bei dem benutzerdefinierte Warenkorbpreise überschrieben wurden, wenn dasselbe Produkt erneut mit einer anderen Menge oder einem anderen benutzerdefinierten Preis zum Warenkorb hinzugefügt wurde. <!-- ACCS-529 -->

* Die UIDs der Anforderungslistenelemente stimmen jetzt mit den UIDs der Warenkorb- und Wunschlistenelemente überein. <!-- ACCS-349 -->

* Fehlerkorrektur - Bei der Produktbearbeitung tritt jetzt kein Timeout mehr auf, wenn große freigegebene Kataloge verwendet werden. <!-- CCSAAS-4657 -->

* Die Endpunkte GET `/V1/directory/countries` und GET `/V1/directory/countries/:countryId` REST API für Admin-Integrationen wurden erneut aktiviert, sodass Kunden gültige Länder- und Regionsdaten nachschlagen können. <!-- ACCS-518 -->

* Fehlerkorrektur - In der REST-API tritt jetzt kein Timeout mehr auf, wenn ein Benutzer über einen großen freigegebenen Katalog verfügt. <!-- ACCS-4657 -->

* Es wurde ein Problem behoben, bei dem blockierte B2B-Unternehmen weiterhin Produkte zum Warenkorb hinzufügen konnten. <!-- ACCS-552 -->

* Wenn Sie über eine große Datenmenge in den Kunden- oder Firmenrastern verfügen, sind die Exportschaltflächen nicht mehr verfügbar, um Fehler zu vermeiden. <!-- ACCS-320 -->

* Es wurde ein Problem behoben, bei dem angehängte Dateigrößen nicht korrekt angezeigt wurden. <!-- ACCS-566 -->

* Es wurde ein Problem beim Erstellen und Löschen von „Datei“-Attributtypen in der [!DNL Commerce Admin] behoben. <!-- ACCS-605, ACCS-606 -->

>[!ENDSHADEBOX]


## März 2026 - #1

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 9. März 2026 in Produktionsumgebungen von [!DNL Adobe Commerce as a Cloud Service] veröffentlicht.

>[!BEGINSHADEBOX]

### App Builder AI-Kodierungstools und -Tutorials

Sie können jetzt das Entwickler-Tool [AI-Codierung](https://developer.adobe.com/commerce/extensibility/developer-agent/){target="_blank"} verwenden, um neue [!DNL App Builder]-Programme zu erstellen und vorhandene [!DNL Adobe Commerce] PHP-Erweiterungen in [!DNL App Builder]-Programme zu konvertieren. Die folgenden Tutorials zeigen, wie Sie die Tools verwenden:

* [Voraussetzungen für das Tutorial](./tutorials/tutorial-prerequisites.md)
* [Tutorial zur Bewertungserweiterung](./tutorials/ratings-extension.md)
* [Tutorial zur Erweiterung der Versandmethode](./tutorials/shipping-method-extension.md)

### Zugriff auf die App Builder-App-Verwaltung über den Administrator

Die [!DNL Commerce Admin] enthält jetzt ein Menüelement mit einer Verknüpfung zu [App Management](https://developer.adobe.com/commerce/extensibility/app-management/){target="_blank"}, einer einheitlichen Shell für die Verwaltung [!DNL App Builder] Apps, die mit der Commerce-Instanz verknüpft sind. Dieser Zusatz basiert auf dem neuesten SDK-Update der Admin-Benutzeroberfläche. <!-- CEXT-5755 -->

### Änderung des Erstellungslimits der Anforderungsentität

Die Anzahl der Websites, Stores und Store-Ansichten war zuvor auf 50 begrenzt. Sie können jetzt eine [Support-Anfrage](https://experienceleague.adobe.com/home?lang=de&support-tab=home#support) senden, um diese Beschränkungen bei Bedarf zu ändern. <!-- ACCS-398 -->

### Anpassen von Storefront-Authentifizierungsnachrichten mit strukturierten Fehler-Codes

Die [`generateCustomerToken` GraphQL-Mutation](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/){target="_blank"} gibt jetzt typisierte Fehler-Codes zusammen mit Fehlermeldungen zurück, sodass Storefronts bestimmte Benutzeroberflächenmeldungen pro Fehlerursache anzeigen können. Zu den verfügbaren Fehlercodes gehören: `CUSTOMER_MISSING_EMAIL`, `CUSTOMER_MISSING_PASSWORD`, `CUSTOMER_SIGN_IN_INCORRECT_OR_LOCKED`, `CUSTOMER_ACCOUNT_NOT_CONFIRMED` und `CUSTOMER_GENERIC_ERROR`. <!-- ACCS-301 -->

### Senden automatischer E-Mail-Erinnerungen für Inaktivität bei Warenkorb und Wunschliste

Das [E-Mail-Erinnerungsmodul](https://experienceleague.adobe.com/de/docs/commerce-admin/marketing/communications/email-reminders/email-reminder-rules) (`Magento_Reminder`) ist jetzt in [!DNL Adobe Commerce as a Cloud Service] aktiv, sodass Händler automatisierte Erinnerungsregeln erstellen können, die E-Mails an Kunden basierend auf der Inaktivität zum Warenkorb und zur Wunschliste als Trigger versenden. <!-- CCSAAS-4597 -->

### Webhook zum Abonnieren von Ereignissen zum Löschen von Kategorien

Der `observer.catalog_category_delete_before` Webhook ist jetzt in [!DNL Adobe Commerce as a Cloud Service] verfügbar. Verwenden Sie sie, um Logik auszuführen, bevor eine Kategorie gelöscht wird. <!-- CEXT-5862 -->

### Verfolgen von Gastbestellungen mit einer registrierten E-Mail

Mit einer neuen optionalen Konfiguration auf Store-Ebene können Kunden [Gastbestellungen verfolgen](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-guest#allow-guest-order-access-for-registered-emails) wenn die Bestellung über eine E-Mail-Adresse aufgegeben wurde, die mit einem registrierten Kundenkonto übereinstimmt. <!-- ACCS-289 -->

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Es wurde ein Problem behoben, bei dem einige Organisations-Admins fälschlicherweise ohne Berechtigung für Einzelmandanten auf Mandanteninstanzen zugreifen konnten. <!-- ACCS-335 -->

* Fehlerkorrektur - Jetzt wird kein Benutzer mehr aus dem [!DNL Commerce Admin] abgemeldet, wenn Änderungen an einem freigegebenen Katalog vorgenommen werden. <!-- ACCS-318 -->

* Ein Problem wurde behoben, das dazu führte, dass einige Webhooks-Felder in der [!DNL Commerce Admin]-Benutzeroberfläche falsch angezeigt wurden. <!-- CEXT-5874 -->

>[!ENDSHADEBOX]

## Februar 2026 - #2

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 24. Februar 2026 in Produktionsumgebungen von [!DNL Adobe Commerce as a Cloud Service] veröffentlicht.

>[!BEGINSHADEBOX]

### Kontextfelder mit Commerce-Ereignissen senden

[!DNL Adobe Commerce as a Cloud Service] unterstützt jetzt [Kontextfelder](https://developer.adobe.com/commerce/extensibility/events/context-fields/) in Ereignis-Payloads, sodass Sie Daten einschließen können, die standardmäßig nicht Teil des Ereignisses sind. <!-- CEXT-5713 -->

### Speichern von Angebotselementen mit einem neuen Webhook abonnieren

Der `observer.sales_quote_item_save_before` Webhook ist jetzt in [!DNL Adobe Commerce as a Cloud Service] verfügbar. Verwenden Sie sie, um Logik auszuführen, bevor ein Angebotselement gespeichert wird. <!-- ACCS-346 -->

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Es wurde ein Fehler behoben, der zu Anzeigeproblemen in der [!DNL Commerce Admin] Produktliste führen konnte. Die Produktliste begrenzt jetzt die Anzahl der angezeigten freigegebenen Kataloge, um die Leistung zu verbessern. <!-- CCSAAS-1242 -->

* Es wurde ein GraphQL-Fehler behoben, der das Hinzufügen anpassbarer Geschenkkarten zum Warenkorb verhindern konnte. <!-- ACCS-313 -->

>[!ENDSHADEBOX]

## Februar 2026 - #1

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 10. Februar 2026 in Produktionsumgebungen von [!DNL Adobe Commerce as a Cloud Service] veröffentlicht.

>[!BEGINSHADEBOX]

### Versandmethoden anpassen und Admin-Berichte anzeigen

An der [!DNL Commerce Admin] wurden die folgenden Verbesserungen vorgenommen:

* Verbesserte prozessexterne (Versand[Webhook-Payloads), &#x200B;](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/shipping-use-cases/#payload) benutzerdefinierte Attribute für Versandadressen einzuschließen. Durch diese Änderung können Händler benutzerdefinierte Versandmethoden implementieren. <!-- ACCS-235 -->

* Zugriff auf Admin-Berichte hinzugefügt, einschließlich Berichte für [Kunden](https://experienceleague.adobe.com/de/docs/commerce-admin/start/reporting/customer-reports), [Marketing](https://experienceleague.adobe.com/de/docs/commerce-admin/start/reporting/marketing-reports), [Produkte](https://experienceleague.adobe.com/de/docs/commerce-admin/start/reporting/product-reports) und [Verkauf](https://experienceleague.adobe.com/de/docs/commerce-admin/start/reporting/sales-reports). <!-- CCSAAS-3085 -->

>[!NOTE]
>
>Berichte, die in [!DNL Adobe Commerce as a Cloud Service] nicht verfügbar sind, sind nur als PaaS gekennzeichnet [!BADGE nur PaaS]{type=Informative url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."}.

### Benutzerdefinierte Rechnungsbeträge über die REST-API erfassen

Die Rechnung-API unterstützt jetzt [benutzerdefinierte &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/invoices#custom-capture-amounts)) mithilfe von Erweiterungsattributen. <!-- ACCS-186, ACCS-197, ACCS-143 -->

>[!NOTE]
>
>Aufgrund rechtlicher Einschränkungen ist der benutzerdefinierte Erfassungsbetrag nur in der Region Nordamerika (NA) und anderen Regionen verfügbar, in denen eine Übererfassung von Zahlungen zulässig ist.

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen sind in dieser Version enthalten:

* Der Filter Couponraster wurde korrigiert, sodass alle benutzerdefinierten Coupons angezeigt werden, die über die API oder durch Importieren erstellt wurden. <!-- CCSAAS-4509 -->

* Es wurde ein Problem in der [!DNL Storefront Compatibility B2B Package] behoben, bei dem die `setNegotiableQuoteShippingAddress`-Mutation die manuell eingegebenen Adressen nicht im Adressbuch des Kunden speicherte, selbst wenn `save_in_address_book` auf `true` gesetzt war. <!-- LYNX-1031 -->

<!-- The above change will also be covered by the B2B changelog published on February 13, 2026. -->

* Es wurde ein Problem behoben, bei dem Produktbilder aufgrund beschädigter `no_selection` in benutzerdefinierten Attributen im Zusammenhang mit Asset-Rollen nicht richtig in [!DNL Edge Delivery Services] angezeigt wurden. <!-- ACAP-1206 -->

* Es wurde ein Problem behoben, das den Zugriff von zusammengeführten Benutzerkonten mit null Vornamen- oder Nachnamenwerten auf den Commerce-Admin verhinderte. <!-- ACCS-200 -->

* Die Konfiguration des Asset-Wählers wurde vereinfacht, indem automatisch regionsspezifische IMS-Client-IDs bereitgestellt wurden. Händler müssen keine Support-Tickets mehr senden, um den Asset-Selektor für die Zuordnung von Produktkategoriebildern zu Assets zu konfigurieren. Das System verwendet jetzt automatisch dedizierte IMS-Client-IDs, die auf der Commerce-Region basieren. <!-- ACCS-175 -->

* Verschiedene Leistungs- und Optimierungsverbesserungen. <!-- CCSAAS-4485, CCSAAS-4497, ACCS-196 -->

>[!ENDSHADEBOX]

## Januar 2026

[!BADGE Produktion]{type=Neutral tooltip="Die aufgelisteten Elemente sind derzeit in Produktionsumgebungen verfügbar."}

Die folgenden Elemente wurden am 20. Januar 2026 in Produktionsumgebungen von [!DNL Adobe Commerce as a Cloud Service] veröffentlicht.

>[!BEGINSHADEBOX]

### B2B-Drop-ins

An den B2B-Drop-in-Komponenten wurden die folgenden Änderungen vorgenommen:

* [!DNL Commerce Storefront on Edge Delivery Services] enthält jetzt [B2B-Drop-in-Komponenten](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/?lang=de). Die folgenden B2B-Drop-ins sind jetzt verfügbar:

   * **[Unternehmensverwaltung](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/company-management/?lang=de)** - Ermöglicht die Verwaltung von Unternehmensprofilen und rollenbasierte Berechtigungen für Adobe Commerce-Storefronts.
   * **[Unternehmens-](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/company-switcher/?lang=de)**: Bietet eine UI-Komponente, mit der Benutzende zwischen mehreren Unternehmen wechseln können, denen sie zugeordnet sind.
   * **[Bestellungen](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/purchase-order/?lang=de)** - Verwaltet Bestellungen-Workflows, Genehmigungsregeln und den Bestellverlauf für B2B-Transaktionen.
   * **[Angebotsverwaltung](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/quote-management/?lang=de)** - Ermöglicht verhandelbare Angebote für B2B-Kunden mit Angebotsanfrage-, Verhandlungs- und Genehmigungs-Workflows.
   * **[Anforderungslisten](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/requisition-list/?lang=de)**: Bietet Tools zum Erstellen und Verwalten von Anforderungslisten für Wiederholungskäufe und Massenbestellungen.

* Das Kompatibilitätspaket für die B2B-Storefront wurde veröffentlicht. Dieses Paket erweitert das [!DNL Adobe Commerce] B2B-GraphQL-Schema , um die Entwicklung auf B2B-Systemen zu verbessern.

<!-- 
* [!DNL Commerce Storefront on Edge Delivery Services] now includes [B2B drop-in components](http://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/?lang=de). For a complete list of available B2B drop-in blocks, refer to the [storefront documentation](http://experienceleague.adobe.com/developer/commerce/storefront/merchants/b2b-commerce-blocks/).

* Released the [B2B Storefront Compatibility Package](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/storefront-compatibility-b2b/?lang=de). This package enhances the [!DNL Adobe Commerce] B2B GraphQL schema to help improve development on B2B systems. 
-->

### Klickbare Links zu externen Versandtrackern

Wandeln Sie die in den Kunden-E-Mails enthaltenen Sendungsverfolgungsnummern aus reinem Text in anklickbare Links um, indem Sie [benutzerdefinierte Tracking-URLs aktivieren](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/delivery/shipping-settings#shipment-tracking-urls). Diese Funktion wird für USPS, UPS, FedEx und DHL unterstützt. <!-- See PR #716 in commerce-admin -->

### Google reCAPTCHA Enterprise-Support

[!DNL Adobe Commerce as a Cloud Service] Storefronts unterstützen jetzt [reCAPTCHA Enterprise](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/captcha/security-google-recaptcha-enterprise). Diese Funktion bietet erweiterten Bot-Schutz durch die Verwendung von adaptiver Risikoanalyse und maschinellem Lernen, um menschliche Benutzer genau von automatisierten Bots zu unterscheiden. Es erhöht die Website-Sicherheit, verhindert betrügerische Aktivitäten und reduziert Spam und Missbrauch, um ein vertrauenswürdiges Einkaufserlebnis zu erhalten. <!-- CCSAAS-4242 -->

### Instanzspezifischer Admin-Zugriff

Sie können jetzt [&#x200B; einzelnen [!DNL Adobe Commerce as a Cloud Service]-Instanzen in der Admin Console &#x200B;](./user-management.md#add-users)Benutzerzugriff zuweisen“. <!-- CCSAAS-4337 -->
<!-- See PR #332 -->

### Beobachtbarkeit

Durch die Verwendung von [!DNL App Builder] erhalten Sie einen tieferen Einblick in Ihre [!DNL Adobe Commerce as a Cloud Service]-Instanz mit [OpenTelemetry Observability](https://developer.adobe.com/commerce/extensibility/observability/), die jetzt automatisch verfügbar ist. OpenTelemetry bietet Metriken, Protokolle und Traces, mit denen Sie die Leistung überwachen, Probleme schneller beheben und Ihre Storefront optimieren können. Diese Funktion ermöglicht proaktive Einblicke in den Systemzustand und verbessert die Zuverlässigkeit für Ihre Kunden.

>[!NOTE]
>
>Die OpenTelemetry-Beobachtbarkeit erfordert die Verwendung von [!DNL App Builder] oder anderen OOPE-Angeboten (Out-of-Process-Erweiterbarkeit).

### Preisstufe für Katalogpreisregeln

Sie können jetzt mehrstufige Preisnachlässe mit Rabatten für Katalogregeln mithilfe von [Katalogpreisregeln](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/products/pricing/product-price-tier#enable-tier-pricing-for-catalog-price-rules) kombinieren. Diese Verbesserung ermöglicht es Ihnen, dynamischere und wettbewerbsfähigere Preisstrategien zu entwickeln, die Masseneinkäufe belohnen und gleichzeitig Aktionsrabatte anwenden. Das Ergebnis ist eine größere Flexibilität, um Kunden zu gewinnen, den Bestellwert zu steigern und Konversionen zu fördern.<!-- See PR #708 in commerce-admin -->

### Verbesserungen und Fehlerbehebungen

Die folgenden ausgewählten Verbesserungen, Optimierungen und Fehlerbehebungen in dieser Version:

* Fehlerkorrektur - Beim Hochladen einer Datei auf S3 tritt jetzt kein Fehler mehr auf. <!-- CCSAAS-4189 -->

* Es wurde ein `User is not entitled to access this instance` behoben, der beim Anmelden bei Commerce Admin oder beim Zugriff auf die REST-API auftreten konnte. <!-- CCSAAS-4324 -->

* Fehlerkorrektur - Bei der Vorschau eines Newsletters aus dem Newsletter-Vorlagenraster oder beim Einreihen in die Warteschlange tritt jetzt kein Fehler mehr auf. <!-- CCSAAS-4398 -->

* Fehlerkorrektur - Beim Klicken auf die Schaltfläche [!UICONTROL **Daten neu laden**] im Admin-Dashboard tritt jetzt kein `404` mehr auf. <!-- CCSAAS-4468 -->

* Es wurde ein Problem behoben, bei dem benutzerdefinierte Produktattribute nicht über die REST-API aktualisiert werden konnten, wenn [!DNL AEM Assets integration] aktiviert war und das Produkt Bilder hatte. <!-- ACAP-1178 -->

* Verschiedene Leistungs- und Optimierungsverbesserungen.
<!-- CCSAAS-4255 -->
<!-- CCSAAS-4233 -->
<!-- CCSAAS-4220 -->
<!-- CCSAAS-4252 -->
<!-- CCSAAS-4330 -->
<!-- CCSAAS-3669 -->
<!-- CCSAAS-4462 -->

>[!ENDSHADEBOX]

## November 2025

>[!BEGINSHADEBOX]

### Verbesserungen

* [Benutzerverwaltung](./user-management.md) - hat die Rolle **Produktadministrator** in der Admin Console geändert, um den Benutzerzugriff auf den Commerce-Administrator automatisch zu aktualisieren. <!-- CCSAAS-3012 -->

* Es wurde die Möglichkeit hinzugefügt, verhandelbare Angebotsanhänge sowie Dateien und Bilder, die mit Kunden und Kundenadressen verknüpft sind, mithilfe von vordefinierten URLs in [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/uploads) und [REST3 hochzuladen und &#x200B;](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/s3-uploads) abzurufen. Mit REST können Sie auch Kategoriebilder hochladen. <!-- CCSAAS-3250 -->

* Die Endpunkte `POST /V1/customers` und `PUT /V1/customers/{customerId}` wurden der [REST-API“ hinzugefügt](https://developer.adobe.com/commerce/webapi/rest/reference/) um Kunden zu erstellen und zu aktualisieren. Diese Endpunkte erfordern eine IMS-Autorisierung. <!-- CCSAAS-3112 -->

* Es wurde die [`exchangeOtpForCustomerToken`-Mutation hinzugefügt](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/exchange-otp-customer-token/) für die die E-Mail-Adresse eines Käufers und ein einmaliges Kennwort (One-Time Password, OTP) erforderlich sind und für die im Austausch ein Kunden-Token empfangen wird. Diese Mutation wird normalerweise in Szenarien verwendet, in denen sich ein Kunde mithilfe eines OTP authentifizieren muss, der an seine E-Mail oder sein Telefon gesendet wird.

* Wenn eine im Konfigurationsbildschirm [!UICONTROL **E-Mail-Adressen speichern**] im Admin-Bereich definierte Adresse einen Wert enthält, der auf `example.com` endet, sendet Commerce keine E-Mails an diese Adresse. Stattdessen protokolliert das System, dass die E-Mail nicht gesendet wurde.  <!-- CCSAAS-3533 -->

#### Benutzerdefinierte Bestellattribute

* Admin-Benutzer können jetzt [benutzerdefinierte Bestellattribute](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/order-management/orders/order-processing#custom-order-attributes) direkt in den Bildschirmen „Bestellansicht“, „Bearbeiten“ und „Erstellen“ im Admin-Bedienfeld anzeigen und bearbeiten. Diese Verbesserung verbessert die Verwaltung von benutzerdefinierten Bestelldaten, die über GraphQL erstellt wurden. <!-- CEXT-5044 -->

>[!ENDSHADEBOX]
