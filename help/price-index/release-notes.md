---
title: '[!DNL Catalog Adapter] Versionshinweise'
description: Die neuesten Versionsinformationen für  [!DNL Catalog Adapter]  für Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
roles: Admin, Developer
exl-id: d4dd0288-8853-43fe-9103-1aead8d3b56e
source-git-commit: 47419e7e19611dc4a045c195f259e2126ab77372
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Versionshinweise zur [!DNL Catalog Adapter]-Erweiterung

In diesen Versionshinweisen werden die neuesten Versionen der [!DNL Catalog Adapter]-Erweiterung beschrieben. Unterstützung wird für die aktuelle Hauptversion bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.

Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bug](../assets/bug.svg) Bekannte Probleme


>[!NOTE]
>
>Die [Catalog Adapter-Erweiterung](catalog-adapter.md) deaktiviert die Adobe Commerce-Preisindizierung. Wenn Sie es installiert haben, können Sie die auf Ihrem System installierte Version mit dem Composer überprüfen. In einigen Fällen empfiehlt es sich, die Katalogadaptererweiterung auf dem System zu aktualisieren, um Fehlerbehebungen oder neue Funktionen aufzunehmen, ohne die Commerce Service-Version zu aktualisieren.

## Aktuelle Hauptversion

## Version 1.0.10

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Preisabfragen für importierte oder neu erstellte Bundle-Produkte zu internen Server-Fehlern führen konnten, da das System versuchte, eine verkettete SKU für die Suche anstelle der richtigen, gültigen SKU zu verwenden. Preisabfragen für Bundle-Produkte verwenden jetzt die entsprechende SKU und werden korrekt aufgelöst.<!--MDEE-1040-->

## Version 1.0.9

![Fix](../assets/fix.svg) Hinzugefügte Kompatibilität für PHP 8.4. <!--MDEE-941-->

## Version 1.0.8

![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, das zu einem Fehler im Ausnahmenprotokoll beim Hinzufügen konfigurierbarer Produktvarianten mit numerischen SKUs zur Wunschliste führte. <!--MDEE-876-->
