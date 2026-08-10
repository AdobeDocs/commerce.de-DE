---
title: Handhabung von Cookie-Einschränkungen
description: Erfahren Sie, wie Produktempfehlungen mit Cookie-Einschränkungen und Datenschutzbestimmungen umgehen.
exl-id: 7e7342db-b903-4105-93c0-e4022c81673b
TQID: https://experienceleague.adobe.com/qqgwO4KI4koSBcYu9mdrjb6AQFW4guxk6dfLDBEwVb8
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: c4147b6e-073b-4d3c-9ab1-d60f2f4434efid: d3cdead0-685a-4489-9250-4bb709942f66id: e0eb8757-182f-49f3-94a4-1587d16f5094id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 454
ht-degree: 0%

---

# Handhabung von Cookie-Einschränkungen

Sowohl Adobe Commerce als auch Magento Open Source bitten um Zustimmung, bevor Daten in Browser-Cookies gespeichert werden. Weitere Informationen finden Sie unter [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

## Handhabung von Cookie-Einschränkungen durch Produktempfehlungen

Wenn Sie das `magento/product-recommendations` Modul für die Produktion bereitstellen, beginnt es mit der Erfassung von Shopper Interaction-Ereignissen in Ihrer Storefront. Diese Daten können in Browser-Cookies oder im lokalen Speicher gespeichert werden, um Empfehlungsalgorithmen zu unterstützen.

>[!IMPORTANT]
>
>Product Recommendations berücksichtigt jetzt den Cookie-Einschränkungsmodus, indem keine Daten in Cookies oder dem lokalen Speicher erfasst oder gespeichert werden, wenn Cookie-Einschränkungen aktiviert sind. Dazu gehören Verhaltensdaten, die für personalisierte Empfehlungen verwendet werden.

### Von Cookie-Einschränkungen betroffene Daten

Die folgenden Produktempfehlungsdaten werden nicht erfasst, wenn der Cookie-Einschränkungsmodus aktiviert ist:

- **Verhaltensdaten**: Produktansichten, Aktionen zum Hinzufügen zum Warenkorb, Käufe und andere Kundeninteraktionen.
- **Sitzungsdaten**: Informationen zur Shopper-Sitzung und Interaktionen mit Empfehlungseinheiten.
- **Personalization-Daten**: Daten, die für Empfehlungstypen wie „Zuletzt angezeigt“ und „Am häufigsten gekauft“ verwendet werden.

### Auswirkungen auf Empfehlungstypen

Wenn der Cookie-Einschränkungsmodus aktiviert ist und Käufer keine Cookies akzeptiert haben, werden bestimmte Empfehlungstypen möglicherweise nicht angezeigt oder zeigen eingeschränkte Ergebnisse an:

- **Kürzlich angezeigte Produkte**: Erfordert Sitzungsdaten, die in Cookies/im lokalen Speicher gespeichert sind.
- **Empfohlen für Sie**: Erfordert Verhaltensdaten für die Personalisierung.
- **Haben gekauft, haben gekauft, dass**: Erfordert Daten zur Kaufhistorie.

>[!NOTE]
>
>Empfehlungstypen, die nicht auf Verhaltensdaten wie „Am häufigsten angezeigt“ und „Visuelle Ähnlichkeit“ basieren, funktionieren auch bei aktivierten Cookie-Einschränkungen weiterhin normal.

## Einverständnislösungen für Drittanbieter-Cookies

Product Recommendations lässt sich möglicherweise nicht automatisch in Einverständnislösungen für Cookies von Drittanbietern integrieren. Es liegt in der Verantwortung des Händlers, sicherzustellen, dass die Datenerfassung den geltenden Datenschutzgesetzen und -vorschriften entspricht.

Wenn Sie eine benutzerdefinierte Cookie-Einverständnislösung verwenden, können Sie den Mechanismus zum Nicht-Tracking von Cookies implementieren, um die Datenerfassung zu steuern.

### Implementieren von Do-Not-Tracking-Cookies

Sie können das `mg_dnt`-Cookie verwenden, um die Datenerfassung programmgesteuert zu steuern:

#### Cookie-Name

```javascript
const DNT_COOKIE = "mg_dnt";
```

#### Datenerfassung deaktivieren

Setzen Sie das Do-Not-Tracking-Cookie, wenn Benutzer Cookies ablehnen:

```javascript
$.mage.cookies.set(DNT_COOKIE, true);
```

#### Aktivieren der Datenerfassung

Löschen Sie das Do-Not-Track-Cookie, wenn Benutzer Cookies akzeptieren:

```javascript
$.mage.cookies.clear(DNT_COOKIE);
```

## Testen des Cookie-Einschränkungsmodus

So testen Sie, wie sich Produktempfehlungen bei Cookie-Einschränkungen verhalten:

1. Aktivieren Sie den Cookie-Einschränkungsmodus in Ihrer Adobe Commerce-Konfiguration.
1. Besuchen Sie Ihre Storefront, ohne Cookies zu akzeptieren.
1. Überprüfen Sie, ob Empfehlungseinheiten angemessenen Fallback-Inhalt anzeigen.
1. Akzeptieren Sie Cookies und überprüfen Sie, ob die Recommendations mit der Datenerfassung beginnen.

## Einhaltung von Datenschutzbestimmungen

Die Datenerfassung für Produktempfehlungen enthält keine personenbezogenen Daten (PII). Alle Benutzerkennungen, wie Cookie-IDs und IP-Adressen, werden anonymisiert. Weitere Informationen finden Sie in der [Adobe-Datenschutzrichtlinie](https://www.adobe.com/privacy/policy.html).

>[!TIP]
>
>Für Kunden im Gesundheitswesen, die die Data Services HIPAA-Erweiterung verwenden, kann eine zusätzliche Konfiguration erforderlich sein. Siehe [HIPAA-Bereitschaft](../data-connection/hipaa-readiness.md) für weitere Informationen.
