---
title: Versionshinweise
description: Die neuesten Versionsinformationen zur  [!DNL Data Connection]  von Adobe Commerce.
feature: Personalization, Integration, Release Notes
exl-id: f3b92632-947d-40cd-89b7-24ed0680be51
TQID: https://experienceleague.adobe.com/kjXCkifzTRTjVJZuy3fb6VPhQkblOaT7-GxwJP4Dv3Y
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: e0eb8757-182f-49f3-94a4-1587d16f5094id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 1350
ht-degree: 2%

---

# Versionshinweise

>[!IMPORTANT]
>
>Der Experience Platform-Connector wurde in [!DNL Data Connection] umbenannt.

Diese Versionshinweise enthalten Aktualisierungen der [!DNL Data Connection]-Erweiterung und umfassen Folgendes:

![Neu](../assets/new.svg) - Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
![Bug](../assets/bug.svg) - Bekannte Probleme

Informationen zu Funktionsänderungen und -korrekturen im Zusammenhang mit Erweiterungen, die von der [!DNL Data Connection]-Erweiterung verwendet werden, finden Sie unter **Unterstützte Service-Updates**.

Unter [Kommende Versionen](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) erfahren Sie mehr über Versionspläne und Support.

In der Entwicklerdokumentation erfahren [, welche Commerce-Versionen dieses Modul unterstützen](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Unterstützte Service-Updates

In diesen Versionshinweisen werden Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit Erweiterungen beschrieben, die von der [!DNL Data Connection]-Erweiterung verwendet werden.

+++Unterstützte Service-Updates

_7. August 2025_

![Neu](../assets/new.svg) - Mit Version 3.3.0 können Sie jetzt ([ Attribute zu Profilen) ](custom-identities.md).

_2. August 2024_

![Korrigieren](../assets/fix.svg) - Feste Summe der Zahlungen, wenn die Bestellsumme so konfiguriert ist, dass Steuern enthalten sind.
![Neu](../assets/new.svg) - Ein `taxAmount` Feld wurde hinzugefügt, um Kaufereignisse zu bestellen.
![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt, benutzerdefinierten Daten zu Ereignissen hinzuzufügen. Im Folgenden finden Sie ein [Beispiel](https://github.com/adobe/commerce-events/blob/main/examples/events/custom-event-override.md).

_24. Januar 2024_

![Neu](../assets/new.svg) - Die `data-services-b2b`-Erweiterung wurde aktualisiert und enthält jetzt ein neues Anforderungsereignis namens `deleteRequisitionList` für B2B-Händler.

_16. November 2023_

![Behebung](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem fälschlicherweise eine Fehlermeldung angezeigt wurde, wenn eine Bestellung mit mehreren Versandadressen aufgegeben wurde.
![Korrigieren](../assets/fix.svg) - Es wurde ein Problem im `productPageView` behoben, bei dem das Feld &quot;`productListItems.priceTotal`-Ereignis“ den Preis nicht konvertierte, nachdem die Währung in der Store-Ansicht gewechselt wurde.
![Korrigieren](../assets/fix.svg) - Es wurde ein Problem im Feld &quot;`productListItems`&quot; behoben, bei dem der Währungscode nicht aktualisiert wurde, als der Händler die Store-Ansicht wechselte.

_10. Oktober 2023_

![Neu](../assets/new.svg) - Neues Bestellstatusereignis hinzugefügt: [Bestellung fakturiert](events-backoffice.md#orderinvoiced), [Bestellartikelrücksendung eingeleitet](events-backoffice.md#orderitemsreturninitiated) und [Bestellartikelrücksendung abgeschlossen](events-backoffice.md#orderitemreturncompleted).
![Beheben](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem Änderungen an der Währungskonfiguration nach der Aktualisierung des Caches nicht in den Ereignissen widergespiegelt wurden.
![Behebung](../assets/fix.svg) - Es wurde ein Fehler behoben, der auftrat, wenn die Bestellbestätigungsmeldung nicht angezeigt wurde, wenn die asynchrone Bestellplatzierung aktiviert war.
![Neu](../assets/new.svg) - Es wurden Daten zu `addToRequisitionList` Ereignis für einfache Produkte auf der Kategorieansichtsseite hinzugefügt.
![Beheben](../assets/fix.svg) - Es wurde ein Problem in den `selectedOptions` im `addToRequisitionList` behoben, das auftrat, wenn Produkte von der Bestellbestätigungsseite hinzugefügt wurden.
![Neu](../assets/new.svg) - Produktdaten zu `addToRequisitionList` Ereignis hinzugefügt, wenn Produkte von der Kategorieansichtsseite zur Anforderungsliste hinzugefügt werden.
![Neu](../assets/new.svg) - Ereignis `addToRequisitionList` hinzugefügt, wenn konfigurierbare Produkte auf der Seite Produktansicht zur Anforderungsliste hinzugefügt werden.
![Neu](../assets/new.svg) - `addToRequisitionList` und `removeFromRequisitionList` Ereignisse hinzugefügt, wenn die Produktmenge aus einer Anforderungsliste erhöht und/oder verringert wird.

_10. Juni 2023_

![Beheben](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem `orderId` aufgrund von Präfixen in der Commerce-Bestellkennung im Kontext nicht übergeben wurde.
![Beheben](../assets/fix.svg) - Aktualisierte Konfigurationen der Content Security Policy.

_30. März 2023_

![Neu](../assets/new.svg) - Es wurde eine Erweiterung namens `data-services-b2b` hinzugefügt, die [Anforderungslisten-Ereignisse](events.md#b2b-events) für B2B-Händler enthält.
![Neu](../assets/new.svg) - Das `uniqueIdentifier` Feld wurde zu [search](events.md#search-events)-Ereignissen hinzugefügt. Dieses neue Feld ermöglicht Händlern Querverweise auf Suchanfragen und Suchantworten.

_12. Oktober 2022_

![Neu](../assets/new.svg) - Zwei [Storefront-Ereignisse](events.md), `openCart` und `removeFromCart`, wurden zum SDK und Collector für Adobe Commerce Storefront-Ereignisse hinzugefügt.
![Neu](../assets/new.svg) - Unterstützung für eine [AEM-Storefront hinzugefügt](overview.md#supported-architecture).

+++

## 3.5.0

_17. März 2026_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) PHP 8.5-Unterstützung wurde hinzugefügt.

## 3.4.0

_16. September 2025_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) [!DNL Data Connection] respektiert jetzt vollständig den Cookie-Einschränkungsmodus, indem die Datenerfassung und -speicherung in Cookies/im lokalen Speicher verhindert wird, wenn die Einschränkungen aktiviert sind.

## 3.3.0

_21. März 2025_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) PHP 8.4-Unterstützung wurde hinzugefügt.

## 3.2.1

_17. Januar 2025_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) - [!DNL Data Connection] wurde die [HIPAA-fähige Erweiterung](hipaa-readiness.md) hinzugefügt, damit Händler [!DNL Commerce] Backoffice-Ereignisdaten mit Experience Platform teilen und die HIPAA-Konformität aufrechterhalten können.
![Beheben](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem die [!DNL Data Connection]-Erweiterung `eventForwarding` Daten überschrieb und das `HIPAA`-Flag für alle Kunden setzte. Jetzt setzt die Erweiterung nur noch das Flag für HIPAA-Kunden.

## 3.2.0

_7. Oktober 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt, [benutzerdefinierte Bestellattribute](custom-attributes.md) zu Back-Office-Daten zu erstellen.
![Neu](../assets/new.svg) - Es wurde eine neue Tabelle [Benutzerdefinierte Bestellattribute](connect-data.md#data-customization) hinzugefügt, in der Sie alle benutzerdefinierten Attribute anzeigen können, die in [!DNL Commerce] konfiguriert und an Experience Platform gesendet wurden.
![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt[ Profildatensätze ](connect-data.md#send-customer-profile-data) Daten zu erfassen und an Experience Platform zu senden.

## 3.2.0-beta3

_27. August 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) - Wenn Sie die Betaversion verwenden, stellen Sie sicher, dass Ihre `composer.json`-Datei auf der Stammebene Folgendes enthält: `"minimum-stability": "beta"`. Fügen Sie außerdem `composer require "magento/customers-connector: ^1.2.0"` hinzu, um Kundenprofile von Ihrer Commerce-Instanz an SaaS zu senden.
![Neu](../assets/new.svg) - Diese Version enthält die Patches, die in 3.1.1, 3.1.2, 3.1.3 und 3.1.4 veröffentlicht wurden.

## 3.1.4

_9. August 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Fehlerbehebung](../assets/fix.svg) - Das `experience-platform-connector`-Metapaket wurde aktualisiert, um zusätzliche nicht verwendete Datenexporteure und Indexer zu entfernen.

## 3.1.3

_22. Juli 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Fehlerbehebung](../assets/fix.svg) - Das `experience-platform-connector`-Metapaket wurde aktualisiert, um nicht verwendete Datenexporteure und Indexer zu entfernen.

## 3.1.2

_5. Juni 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Korrigieren](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem beim Initiieren einer [Verlaufssynchronisierung) das falsche ](connect-data.md#specify-order-history-date-range) verwendet wurde.
![Beheben](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem das `startCheckout`-Ereignis in Adobe Commerce 2.4.7 nicht gesendet wurde.

## 3.1.1

_4. April 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) - PHP 8.3 wird nun für alle [!DNL Data Connection] Erweiterungen unterstützt.
![Neu](../assets/new.svg) - Es wurde ein Artikel zur [ (Integration](mobile-sdk-epc.md) der Adobe Experience Platform Mobile SDK mit Commerce hinzugefügt.

## 3.2.0-beta2

_4. März 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) - Wenn Sie die Betaversion verwenden, stellen Sie sicher, dass Ihre `composer.json`-Datei auf der Stammebene Folgendes enthält: `"minimum-stability": "beta"`. Fügen Sie außerdem `composer require "magento/customers-connector: ^1.2.0"` hinzu, um Kundenprofile von Ihrer Commerce-Instanz an SaaS zu senden.
![Neu](../assets/new.svg) - Es wurde die Möglichkeit zum [Hinzufügen benutzerdefinierter Attribute“ ](custom-attributes.md).
![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt[ Profildatensätze ](connect-data.md#send-customer-profile-data) Daten zu erfassen und an Experience Platform zu senden.

## 3.1.0

_16. November 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

![Neu](../assets/new.svg) - Der Experience Platform-Connector wurde in [!DNL Data Connection] umbenannt.
![Behebung](../assets/fix.svg) - Es wurde die Möglichkeit hinzugefügt, eine Fehlerantwort zu protokollieren, wenn Adobe IMS das Zugriffstoken nicht generieren kann.
![Korrektur](../assets/fix.svg) - Es wurde eine Benachrichtigung hinzugefügt, wenn Sie versuchen, historische Bestellungen zu synchronisieren, aber keine Kontoanmeldeinformationen angegeben haben.

## 3.0.0

_10. Oktober 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"} Adobe Commerce-Versionen 2.4.4 und höher

Dies ist eine Hauptversion. [Bearbeiten](install.md#update) Sie die Datei „composer.json“ im Stammverzeichnis Ihres Projekts.

![Neu](../assets/new.svg) - Allgemeine Verfügbarkeit zum [Senden von historischen ](connect-data.md#send-historical-order-data) und Status an die Experience Platform.
![Neu](../assets/new.svg) - Es wurde Unterstützung für OAuth 2.0 beim [ (Konfigurieren](connect-data.md#connect-commerce-data-to-adobe-experience-platform) der [!DNL Data Connection] hinzugefügt.
![Neu](../assets/new.svg) - Beendet die Unterstützung für Adobe Commerce 2.4.3.

## 2.3.0

_27. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.3 und neuer

![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt[ „Storefront-Ereignisse zu senden](connect-data.md#data-collection) an die Experience Platform zu deaktivieren.
![Beheben](../assets/fix.svg) - Aktualisierte Konfigurationen der Content Security Policy.
![Fix](../assets/fix.svg) - Die Unterstützung für Backoffice-Ereignisse in Commerce 2.4.7 wurde korrigiert.
![Neu](../assets/new.svg) - Es wurde eine Benachrichtigung zur Cache-Invalidierung hinzugefügt, wenn Sie Änderungen am [!DNL Data Connection]-Erweiterungsformular speichern.

## 3.0.0-beta1 (nur intern)

_13. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.3 und neuer

![Neu](../assets/new.svg) - (Beta) Es wurde die Möglichkeit hinzugefügt[ Daten und Status ](connect-data.md#send-historical-order-data) historischen Reihenfolge an Experience Platform zu senden.

## 2.2.0

_30. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.3 und neuer

![Neu](../assets/new.svg) - Die `commerce-data-export` und `saas-export` Abhängigkeiten wurden mit der `experience-platform-connector`-Erweiterung gebündelt. Zuvor mussten Sie diese Abhängigkeiten separat installieren. Diese Abhängigkeiten ermöglichen zusammen mit der Konfiguration von Händlern die Server-seitige Verarbeitung von [Back-Office-Ereignissen](events-backoffice.md).
![Neu](../assets/new.svg) - Neues Backoffice-Ereignis namens [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted) hinzugefügt.

## 2.1.1

_28. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.3 und neuer

![Neu](../assets/new.svg) - PHP 8.2 wird nun für alle [!DNL Data Connection] Erweiterungen unterstützt.

## 2.1.0

_17. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.3 und neuer

![Neu](../assets/new.svg) - Die Erweiterung [[!DNL Data Connection] Admin](connect-data.md) wurde aktualisiert, sodass Sie eine eigene AEP Web SDK-Legierung angeben können.
![Behebung](../assets/fix.svg) Geändert in Verwendung von `identityMap` anstelle von `personID` beim Festlegen der primären Identität für alle Daten, die an den Edge gepusht werden.

## 2.0.1

_10. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.3 und neuer

![Beheben](../assets/fix.svg) - Der Adobe Experience Platform-Kontext wird jetzt erst festgelegt, nachdem die Storefront Event Collector- und Storefront Event-SDK erfolgreich geladen wurden.

## 2.0.0

_12. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.3 und neuer

![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt, beim [Verbinden](connect-data.md) Ihrer Adobe Commerce-Instanz mit der Experience Platform Ihre eigene AEP Web SDK anzugeben.
![Korrigieren](../assets/fix.svg) - Die Anforderung an den Datenstrombereich wurde aktualisiert, sodass Datenstrom-IDs für die Website und nicht für die Storeview gültig sind.

## 1.0.0

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce-Versionen 2.4.3 und neuer

![Neu](../assets/new.svg) - Version mit allgemeiner Verfügbarkeit.
