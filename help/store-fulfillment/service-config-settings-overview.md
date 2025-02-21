---
title: Konfigurationsübersicht für Store Fulfillment
description: Erfahren Sie mehr über die Arten von Admin-Konfigurationseinstellungen, die zum Anpassen der erweiterten Fulfillment-Funktionen der Store-Fulfillment-Lösung verfügbar sind, und erhalten Sie einen Link zu Anweisungen zum Abschließen der Konfiguration.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Konfigurationsübersicht für Store Fulfillment

Im Adobe Commerce Admin werden die Konfigurationseinstellungen für Store Fulfillment Services von Walmart Commerce Technologies nach Typ kategorisiert.

**Store Fulfillment-Konfigurationseinstellungen nach Typ**

| **Typ** | **Beschreibung** | **API konfigurierbar** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Allgemeine Konfiguration](enable-general.md) | Allgemeine Integrationskonfiguration für die Store-Fulfillment-Lösung, ihre aktiven Funktionen und Anmeldedaten für die Verbindung mit Fulfillment-Services. | Nein |
| [E-Mail-Konfiguration für Vertrieb](sales-emails.md) | Richten Sie zusätzliche E-Mail-Vorlagen für Kundenbenachrichtigungen ein, die während des Eincheckvorgangs gesendet werden. | Nein |
| [Konfiguration für Händler](merchant-store-configuration.md) | Richten Sie erweiterte Inventory management-Quellen als Händler ein. | Ja |
| [Verwaltung von Produktbeständen](product-stock.md) | Konfigurieren Sie die für Kunden verfügbaren Merchant Stock-Nachrichten und -Funktionen. | Ja |
| [Inventory management Source-Übertragung](inventory-stock-transfer.md) | Richten Sie ein neues Lager ein und übertragen Sie Inventar aus dem Standardlager. | Ja |
| [Konfiguration mehrerer Websites/Bereiche](multi-site-and-scope-config.md) | Konfigurieren Sie Lager- und Versandmethoden für mehrere Websites/Store-Bereiche. | Nein |
| [Systemkonfiguration für Hintergrundprozesse](background-processes.md) | Konfigurieren Sie die Zeitpläne für Hintergrundprozesse, die für die Synchronisierung von Daten mit den Fulfillment-Services verwendet werden. | Nein |
| [Store-Speicherort und Zuordnungseinrichtung](store-location-map-provider-setup.md) | Konfigurieren Sie die Möglichkeit, einen Entfernungsanbieter zu verwenden, um nach Einzelhandelsgeschäften zu suchen und diese Informationen in der SSL-Karte anzuzeigen. | Ja |
| [Einchecken von Experience Setup](check-in-experience-setup.md) | Konfigurieren Sie die Autofarbe und die Autoherstellungs-Optionen, die während des Eincheckvorgangs verfügbar sein werden | Ja |
| [Benutzereinrichtung](user-setup.md) | Verwalten Sie Benutzerkonten, Rollen und Berechtigungen für Store-Associates, die die Store Assist-App verwenden. Bereiche. | Ja |
| [App-Setup](app-setup.md) | Überprüfen Sie die verfügbaren Konfigurationen für die Store Assist-App, die für den Abschluss des Onboarding-Prozesses erforderlich sind. Diese Einstellungen können nicht über Adobe Commerce Admin konfiguriert werden. | Ja |

## Verwenden der Konfigurationsreferenz

Zeigen Sie die Konfigurationsreferenz für jeden Einstellungstyp an, indem Sie den Typnamen in der Tabelle _Store Fulfillment-Konfigurationseinstellungen nach Typ_ auswählen.

In der Konfigurationsreferenz für jeden Typ werden die Konfigurationsdetails in einer Tabelle mit den folgenden Spaltenüberschriften angezeigt:

- **Feld** bezieht sich auf den Namen des zu konfigurierenden Felds

- **Beschreibung** enthält wichtige Details zum Zweck und Verhalten des Felds

- **Scope** gibt den Adobe Commerce-Konfigurationsbereich für die Einstellung an (global, Website, Store)

- **Erforderlich** Wert gibt an, ob für das Feld ein Wert festgelegt werden muss

Als technische Referenz finden Sie auch den internen Konfigurationspfad für jedes Feld.
