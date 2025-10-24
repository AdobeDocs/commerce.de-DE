---
title: Versionshinweise zur AEM Assets-Integration
description: Informationen zu allen AEM Assets-Integrationsversionen finden Sie in den Versionshinweisen .
feature: CMS, Media, Release Notes
exl-id: 0d639565-812f-481a-afd6-6e6fa54ed70e
source-git-commit: 4e7ad5d57dfc1da1020d4f67b1051303d3b499f9
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Versionshinweise zur AEM Assets-Integration

Diese Versionshinweise beschreiben die erste Version von AEM Assets Integration und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Funktionsänderungen und -korrekturen, die außerhalb der regulären Funktionsveröffentlichungsversion veröffentlicht wurden, finden Sie in den Abschnitten _Gehostete Service-Updates_.

Weitere Informationen zu kommenden Versionen, zum Produkt-Support und dazu, welche Adobe Commerce-Versionen die AEM Assets-Integrationserweiterung unterstützen, finden Sie unter Adobe Commerce [Versionsplan](https://experienceleague.adobe.com/de/docs/commerce-operations/release/planning/schedule) und [Produktverfügbarkeit](https://experienceleague.adobe.com/de/docs/commerce-operations/release/product-availability).

## Gehostete Service-Aktualisierungen

In diesen Versionshinweisen werden Funktionsänderungen und -korrekturen beschrieben, die außerhalb der regulären Funktionsversionen für den gehosteten Service stattfanden und veröffentlicht wurden.

+++Gehostete Service-Aktualisierungen

_11. September 2025_

![Neues Problem](../assets/new.svg) Die Endpunkte [benutzerdefinierten automatischen Abgleich](https://experienceleague.adobe.com/de/docs/commerce/aem-assets-integration/synchronize/custom-match){target=_blank} wurden mit einem neuen `asset_matches`-Attribut aktualisiert.

_11. Februar 2025_

![Neues Problem](../assets/new.svg) Jetzt können Händler Bilder für Produkte und Kategorien synchronisieren.

+++

## v1.2.6

_24. Oktober 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Problem behoben](../assets/fix.svg)<!-- Issue ACAP-1163 --> Es wurde ein Problem behoben, bei dem aufeinander folgende Massenprodukt-Aktualisierungsanfragen das Status-Tracking-Flag hängen ließen, was die korrekte Verarbeitung nachfolgender Aktualisierungen verhinderte. Jetzt wird der Status zurückgesetzt, selbst wenn ein Fehler auftritt.

## v1.2.5

_22. Oktober 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Problem behoben](../assets/fix.svg)<!-- Issue ACAP-1161 --> Es wurde ein Problem behoben, bei dem die Aktualisierung der Position einer vorhandenen Imagemap in Adobe Commerce Admin zu einem PHP-Typfehler führte.

## v1.2.4

_17. Oktober 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Problem behoben](../assets/fix.svg)<!-- Issue ACAP-1155 --> Die allgemeine Stabilität von benutzerdefinierten Attributen wurde verbessert. Benutzerdefinierte Attribute werden jetzt bei Verwendung asynchroner APIs korrekt aktualisiert.

![Problem behoben](../assets/fix.svg)<!-- Issue ACAP-1074 --> Jetzt schlägt die [Synchronisierung von Produkt](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/store-urls#configure-the-base-url){target=_blank}Asset) nicht fehl, wenn eine Basis-Link-URL definiert ist.

## v1.2.3

_2. Oktober 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Problem behoben](../assets/fix.svg)<!-- Issue ACAP-1135 --> Es wurde ein Problem beim Aktualisieren von Produktattributen behoben. Produktattribute werden nun erwartungsgemäß aktualisiert, und bei fehlgeschlagenen Aktualisierungen wird anstelle einer 200-Fehlermeldung ein entsprechender Fehler zurückgegeben.

## v1.2.2

_18. September 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Problem behoben](../assets/fix.svg)<!-- Issue ACAP-1110 --> Verbesserte allgemeine Bildstabilität auf Mini-Warenkorb-, -Warenkorb- und -Checkout-Seiten. Bilder auf diesen Seiten werden jetzt ordnungsgemäß geladen.

## v1.2.0

_7. August 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Neues Problem](../assets/new.svg)<!-- Issue ACAP-1018 --> Händler können jetzt die Quelle für Bild- und Medien-Assets auswählen, indem sie beim Konfigurieren der Assets[Integration über den Administrator einen &quot;](https://experienceleague.adobe.com/de/docs/commerce/aem-assets-integration/get-started/setup-synchronization){target=_blank}&quot; auswählen.

![Neues Problem](../assets/new.svg)<!-- Issue ACAP-1078 --> Die Endpunkte [benutzerdefinierten automatischen Abgleich](https://experienceleague.adobe.com/de/docs/commerce/aem-assets-integration/synchronize/custom-match){target=_blank} wurden mit einem neuen `asset_matches`-Attribut aktualisiert. Durch diese Änderung können Sie Ihre eigene Matching-Logik implementieren, um alle mit einem bestimmten `productSku` verknüpften Assets zurückzugeben.

## v1.1.2

_11. Juni 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Neues Problem](../assets/new.svg)<!-- Issue ACAP-1041 --> Es wurde Unterstützung für Adobe Commerce 2.4.8 und PHP 8.4 hinzugefügt.

## v1.1.0

_23. April 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Neues Problem](../assets/new.svg)<!-- Issue ACAP-955 --> Anstelle der AEM[Bereitstellungs-URL &#x200B;](https://experienceleague.adobe.com/de/docs/commerce/aem-assets-integration/get-started/setup-synchronization#optional-configure-the-custom-domain-url) jetzt eine benutzerdefinierte Domain-URL verwendet werden. Wenn ein Händler in seinem AEM **Dashboard einen** benutzerdefinierten Domain-Namen) festlegt, muss diese **benutzerdefinierte Domain-URL** in Commerce hinzugefügt werden.

![Problem behoben](../assets/fix.svg)<!-- Issue ACAP-987 --> Verbesserte Gesamtprotokolle für AEM Assets-Synchronisierungsprozesse.

## v1.0.22

_12. März 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Neues Problem](../assets/new.svg)<!-- Issue ACAP-xx --> Der Assets-Selektor benötigt jetzt die [Assets-Selektor-IMS](https://experienceleague.adobe.com/de/docs/commerce/aem-assets-integration/get-started/setup-synchronization)Client-ID, um die Zuordnung von AEM Assets-Bildern mit Produktkategorien und von Page Builder generierten Inhalten zu aktivieren.

## v1.0.20

_11. Februar 2025_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"} Adobe Commerce Version 2.4.5 und höher.

![Neu](../assets/new.svg)<!-- Issue ACAP-xx --> Allgemeine Verfügbarkeitsversion.
