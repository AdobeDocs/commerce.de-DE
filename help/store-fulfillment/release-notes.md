---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Versionshinweise'
description: Informationen zu allen Versionen finden  [!DNL Store Fulfillment by Walmart Commerce Technologies]  in den Versionshinweisen .
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Store Fulfillment Services by Walmart Commerce Technologies] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Unter [Kommende Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html?lang=de) erfahren Sie mehr über Versionspläne und Support.

Unter [Produktverfügbarkeit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=de) erfahren Sie, welche Adobe Commerce-Versionen diese Erweiterung unterstützen.

## v1.5.0

*3. August 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}[Adobe Commerce 2.4.4 bis 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=de), einschließlich der Sicherheits-Patch-Versionen 2.4.6-p1, 2.4.5-p3 und 2.4.4-p4

Diese Version enthält die folgenden Aktualisierungen:

![Neu](../assets/fix.svg) Die Erweiterung wurde aktualisiert, um [Adobe Commerce-Sicherheits-Patch](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html?lang=de)Versionen 2.4.6-p1, 2.4.5-p3 und 2.4.4-p4 zu unterstützen.

![Neu](../assets/new.svg)<!-- WMTP-918 --> Es wurde Unterstützung für die Konfigurationsoption [Asynchrones Senden](sales-emails.md) für Verkaufs-E-Mails hinzugefügt. Händler, die auf Version 1.5.0 aktualisieren, haben die Möglichkeit, E-Mails sofort (standardmäßig) oder asynchron zu senden.

![Neu](../assets/new.svg)<!-- WMTP-916--> Die [Quellen-Konfiguration](merchant-store-configuration.md) wurde aktualisiert, um internationale Telefonnummernformate zu unterstützen.

![Neu](../assets/new.svg) Es wurde eine Logik hinzugefügt, um zu verhindern, dass Rückerstattungsbeträge den verbleibenden oder fakturierten Betrag überschreiten.

![Neu](../assets/new.svg)<!-- WMTP-882 --> Ersetzt `google.map.LatLng` Objekt durch JSON-Literale, um die Kompatibilität mit älteren Versionen von [!DNL Google Maps] zu unterstützen.

![Problem behoben](../assets/fix.svg)<!-- WMTP- --> Das Skript, das die `[!DNL Available for Store Pickup]`- und `[!DNL Available for Home Delivery]`-Produktattribute erstellt, wurde aktualisiert, um Konflikte in Attributkategorien zu vermeiden.

![Problem behoben](../assets/fix.svg)<!-- WMTP-915 --> Es wurde ein Kompatibilitätsproblem behoben, das beim Laden und Speichern einiger Entitäten zu einer Endlosschleife führte.

![Problem behoben](../assets/fix.svg)<!-- WMTP-921 --> Es wurde ein Problem behoben, das verhinderte, dass [!DNL Ship to Store] Angebotsvalidierung ausgelöst wurde, wenn ein Artikel von einer Produktdetailseite (PDP) zum Warenkorb hinzugefügt wurde.

![Problem behoben](../assets/fix.svg)<!-- WMTP- 932 --> Es wurde ein Checkout-Problem behoben, durch das Kundinnen und Kunden die Versandmethode Startseite für Elemente auswählen konnten, die nicht für den Heimversand infrage kommen.

![Problem behoben](../assets/fix.svg) Installations-Updates:

- &#x200B;<!-- WMTP-880--> Es wurde ein Fehler behoben, der dazu führte, dass bei der Installation der [!DNL Store Fulfillment]-Erweiterung ein falscher Website-Code zurückgegeben wurde.

- &#x200B;<!-- WMTP-878--> Es wurde ein Problem für SKU-Ganzzahlen behoben, bei dem der Datentyp während der Installation in den String-Typ umgewandelt werden musste.

![Problem behoben](../assets/fix.svg)<!-- WMTP-915--> Es wurde ein Fehler behoben, der durch einen fehlenden Fehler-Code beim Einchecken verursacht wurde.

![Problem behoben](../assets/fix.svg)<!-- WMTP-932 --> Es wurde ein Fehler im Zusammenhang mit der teilweisen Zurückweisung während der Ausgabevorgänge behoben.

![Neu](../assets/new.svg)<!-- WMTP-953 --> Der API-Endpunkt „Abbrechen“ wurde aktualisiert, um den Statusparameter als optionales Objekt zu nutzen.

![Neu](../assets/new.svg)<!-- WMTP-960 --> Verbesserte Protokollierungsdetails für den Dispense-API-Endpunkt.

## v1.4.0

*13. April 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/fix.svg) [!DNL Store Fulfillment] ist jetzt [kompatibel mit [!DNL Adobe Commerce] 2.4.4 bis 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=de).


## v1.3.0

*27. Februar 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Diese Version enthält die folgende Aktualisierung:

![Neu](../assets/fix.svg)<!-- WMTP-795 --> Es wurde die Möglichkeit hinzugefügt, die Store Fulfillment-Lösung für eine bestimmte Site zu deaktivieren, indem der Standardbereich für die Systemkonfigurationseinstellung von „Website“ in „global“ geändert wird.

## v1.2.0

*27. September 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Diese Version enthält die folgende Aktualisierung:

![Neu](../assets/fix.svg) [!DNL Store Fulfillment] ist jetzt [kompatibel mit [!DNL Adobe Commerce] 2.4.4 bis 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=de).


## v1.1.0

*15. Juli 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Stabilität: Allgemeine Verfügbarkeit

![Neu](../assets/fix.svg)<!-- WMTP-731 --> Vereinfachte [Eincheckerlebniskonfiguration) für ](check-in-experience-setup.md) Store Assist-App durch Hinzufügen von standardmäßigen Automarken- und Modellauswahlen. In der vorherigen Version mussten Händler die Automarken- und Modellauswahl manuell konfigurieren.

## v1.0.0

*4. März 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Stabilität: Allgemeine Verfügbarkeit

## Store-Assist-App

Informationen zu neuen Versionen der Store Assist-App finden Sie in den App-Informationen im [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} oder [Google Play Store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
