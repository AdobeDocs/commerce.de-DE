---
title: Grenzen und Beschränkungen
description: Erfahren Sie mehr über die Grenzen und Einschränkungen von  [!DNL Adobe Commerce Optimizer] , um sicherzustellen, dass es den Anforderungen Ihres Unternehmens entspricht.
role: Admin, Developer
exl-id: 58d94da9-8d48-4513-8b6a-8e8c7c27a2a5
source-git-commit: 149b87fc822e5d07eed36f3d6a38c80e7b493214
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Grenzen und Beschränkungen

>[!NOTE]
>
>In dieser Dokumentation werden die Grenzen und Einschränkungen für die Entwicklung für frühzeitigen Zugriff beschrieben. Sie spiegelt nicht alle für die allgemeine Verfügbarkeit vorgesehenen Funktionen wider.

Im Folgenden finden Sie Begrenzungen und Einschränkungen für Adobe Commerce Optimizer.

## Katalog

- Die garantierte Rate der Katalogaufnahme ist: 1000 Produkte/Minute und 5000 Preise/Minute
- Die Gesamtzahl der Produktaktualisierungen pro Tag beträgt 1.000.000.
- Die Gesamtzahl der in einer Instanz zulässigen SKUs beträgt 250.000. 
- Die maximale Anzahl von Bereichen ist 50.
- Die Anzahl der Varianten pro Produkt beträgt 10.000.
- Die Produktgröße darf 200 KB nicht überschreiten.

## Preise

- Die maximale Anzahl von Preisbüchern beträgt 1.000.

## Suche und Storefront

- Die Anzahl der Produkte, die eine einzelne Suchanfrage zurückgeben kann, beträgt 100.
- Die maximale Anzahl filterbarer Attribute ist 200
- Die maximale Anzahl durchsuchbarer Attribute ist 200
- Die maximale Anzahl sortierbarer Attribute ist 50
- Die maximale Anzahl von Facetten ist 100. Alle Facetten müssen filterbare Attribute sein.
- Die maximale Anzahl von Optionen, die eine einzelne Facettenkatze zurückgibt, beträgt 100, die pro Support-Anfrage erhöht werden können.

## Kanäle und Richtlinien

- Die maximale Anzahl von Kanälen pro Mandant beträgt 1.000.
- Die maximale Anzahl von Richtlinien, die einem Kanal zugewiesen werden können, beträgt 10.
- Die maximale Anzahl der in einer Richtlinie verwendeten Attributwerte ist 100. 

## Produkterkennung und Empfehlungen

- Für die Produkterkennung werden attributbasiertes Merchandising und Preiseinstellungen nicht unterstützt.
- Für Empfehlungen:

   - [!DNL Adobe Commerce Optimizer] unterstützt den Empfehlungstyp _Kürzlich angezeigt_ für den frühzeitigen Zugriff.
   - Einschlüsse oder Ausschlüsse von Kategorien oder Attributen werden nicht unterstützt.
   - Sie können keine Vorschau von Recommendations in [!DNL Adobe Commerce Optimizer] anzeigen.
