---
title: Unterstützung für benutzerdefinierte Produktarten im SaaS-Katalogdatenexport
description: Erfahren Sie, wie das Commerce Storefront MCP Catalog Enablement-Modul den SaaS-Datenexport in die Lage versetzt, nicht erkannte, benutzerdefinierte Produktarten von Drittanbietern als einfache Produkte in Katalogdaten darzustellen, die an den Live Search- und Catalog-Service gesendet werden.
role: Admin, Developer
hide: true
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: fd87417a494987f33009d386019d870b306dcf73
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%
---
# Unterstützung für benutzerdefinierte Produktarten im SaaS-Katalogdatenexport

>[!IMPORTANT]
>
>Die Unterstützung für benutzerdefinierte Produktarten ist derzeit **Early Access** als Teil der [!DNL Commerce Storefront MCP] verfügbar. Dieses Modul wird in Adobe Commerce-Versionen 2.4.4 und höher unterstützt. Verfügbarkeits-, Verpackungs- und Installationsanforderungen können sich vor der allgemeinen Verfügbarkeit ändern. Um eine Einladung zu diesem **Early Access** anzufordern, senden Sie eine E-Mail an [commerceeap@adobe.com](mailto:commerceeap@adobe.com). Das Adobe-Team wird mit den nächsten Schritten und Eignungsanforderungen antworten.

## Überblick

[!DNL SaaS Data Export] erkennt die standardmäßigen Adobe Commerce-Produktarten (einfach, konfigurierbar, Bundle usw.), wenn Katalogdaten für verbundene Commerce-Services wie [Live Search](../live-search/overview.md) und [Catalog Service) ](../catalog-service/overview.md). Mit Erweiterungen von Drittanbietern können **benutzerdefinierte Produktarten) eingeführt werden** die [!DNL SaaS Data Export] nativ nicht erkennt.

Mit dem Modul zur Aktivierung des MCP-Katalogs der Commerce-Storefront können [!DNL SaaS Data Export] diese nicht erkannten, benutzerdefinierten Produkttypen als &quot;**Produkte“** der Payload des ausgehenden Katalogs darstellen, sodass Käufer, die die [!DNL Commerce Storefront MCP] verwenden, sie über kataloggestützte Services finden können.

## Umfang des Verhaltens

- Das Modul zur Aktivierung des MCP-Katalogs der Commerce-Storefront ändert den in Adobe Commerce gespeicherten Produkttyp nicht. Die Darstellung eines benutzerdefinierten Produkttyps als einfaches Produkt gilt nur für Katalogdaten, die an [!DNL Live Search] und [!DNL Catalog Service] gesendet werden.
- Es ist keine Admin-Einstellung oder Laufzeitkonfiguration erforderlich. Standardwarentypen werden weiterhin normal exportiert.
- Das Modul zielt auf benutzerdefinierte Produkttypen ab, die durch Erweiterungen von Drittanbietern eingeführt wurden, nicht auf die standardmäßigen Commerce-Produkttypen.

## Installieren des Moduls

Um das Modul zur Aktivierung des MCP-Katalogs der Commerce-Storefront zu aktivieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer require magento/module-storefront-mcp-enablement --no-update
composer update magento/module-storefront-mcp-enablement --with-dependencies
bin/magento setup:upgrade
```

## Katalogdaten neu synchronisieren

Durch die Installation des Moduls werden die zugrunde liegenden Produktdaten in Adobe Commerce nicht geändert, sodass vorhandene benutzerdefinierte Produktelemente nicht automatisch erneut exportiert werden. Um die neue einfache Produktdarstellung auf Katalogdaten anzuwenden, die bereits vor der Installation des Moduls synchronisiert wurden, synchronisieren Sie Ihre Katalogdaten manuell neu. Siehe [Daten manuell neu synchronisieren](data-sync-manage.md#manually-resync-data).
