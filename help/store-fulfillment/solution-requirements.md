---
title: Store-Erfüllungsanforderungen
description: Anforderungen an die Bereitstellung und das Onboarding von [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Store-Erfüllungsanforderungen für Adobe Commerce

In den folgenden Abschnitten werden die technischen und geschäftlichen Anforderungen für die Installation und Aktivierung der Store Fulfillment-Lösung für Adobe Commerce beschrieben.

## Anforderungen an Plattform- und Softwareversionen

Die [!DNL Store Fulfillment]-Lösung steht Adobe Commerce-Kunden auf den folgenden Plattformen zur Verfügung.

- Adobe Commerce auf Cloud-Infrastruktur (ECE)
- Adobe Commerce On-Premises (EE)

Lesen Sie vor der Installation oder dem Upgrade die Versionshinweise und Adobe Commerce-Systemanforderungen , um die aktuellsten Informationen zur Versionskompatibilität, zu Updates oder Änderungen zu erhalten, die sich auf Installations- oder Upgrade-Anforderungen auswirken können.

- [Versionshinweise zur Store-Erfüllung](release-notes.md)

- [Versionshinweise zu Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/release/versions.html?lang=de) in den *Versionsinformationen zu Adobe Commerce*.

- [Adobe Commerce-Systemanforderungen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=de) im *Adobe Commerce-Installationshandbuch*.


## Store Assist-App-Anforderungen

Der End-to-End-Prozess zur Verwaltung von Abholaufträgen wird über die auf Mobilgeräten installierte Store Assist-App verwaltet. Diese Geräte - bereitgestellt vom Einzelhändler oder von Mitarbeitern des Geschäfts, die ihre persönlichen Smartphones verwenden - müssen folgende Anforderungen erfüllen:

**Mindestanforderungen an das Betriebssystem**

- ANDROID 6
- iOS 12

**Mindestanforderungen an die Hardware**

- 1 GB RAM
- 600 MB freier Speicherplatz

## Geschäftsanforderungen

Ihr Unternehmen muss die folgenden Mindestkriterien erfüllen, um die Store Fulfillment-Lösung zu implementieren:

- Nur in den USA ansässige Unternehmen

- B2C-Einzelhändler (Business to Consumer Packaged Goods, CPG) Hersteller, die direkt an Verbraucher verkaufen (D2C), oder Händler, die direkt an Verbraucher oder kleine Unternehmen verkaufen

- Mindestens ein physisches Geschäft oder Lager

- Verwalten des Produktbestands mit Inventory management for Adobe Commerce (auch als MSI bezeichnet)

- Konsortialfähigkeit des Händlerbestands

- Store-Wi-Fi-Verfügbarkeit an allen Standorten, die die Store-Fulfillment-Lösung unterstützen: mindestens 3 Mbit/s Internetgeschwindigkeit

- Store- und Warehouse-Associates haben während ihrer Schicht Zugriff auf iOS- oder Android-Mobilgeräte, entweder privat oder vom Händler bereitgestellt

- Produkte, die mithilfe der Store Fulfillment-Lösung verwaltet werden, müssen Produktattribute aufweisen, die entweder eine SKU oder einen UPC-Produkt-Code enthalten
