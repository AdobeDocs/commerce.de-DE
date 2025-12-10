---
title: Katalogsynchronisierung
description: Erfahren Sie, wie Sie Produktdaten vom - [!DNL Commerce]  nach  [!DNL Commerce Services].
feature: Catalog Management, Data Import/Export, Catalog Service
exl-id: 99f96b93-b036-490c-8c57-40463a0de365
source-git-commit: c6725fc524e9d239ccc0f16701e92ad5d2fc7729
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Katalogsynchronisierung

>[!NOTE]
>
> Das Dashboard zur Katalogsynchronisierung wird jetzt zum Dashboard für das Daten-Management. Dieses überarbeitete Dashboard unterstützt jetzt [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md) v6.0.0+, [[!DNL Live Search]](../live-search/overview.md) v4.1.0+ und [[!DNL Catalog Service]](../catalog-service/overview.md) v1.17+. Kunden können das Daten-Management-Dashboard erhalten, indem sie auf die neueste Version eines dieser Services aktualisieren. Weitere Informationen hierzu finden Sie in der Dokumentation [Data Management Dashboard](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html?lang=de) . Dieses aktuelle Thema bleibt für die Benutzer übrig, die noch kein Upgrade durchgeführt haben und noch über das Dashboard zur Katalogsynchronisierung verfügen.

Adobe Commerce verwendet Indexer, um Katalogdaten in Tabellen zu kompilieren. Der Prozess wird automatisch durch [Ereignisse](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html?lang=de#events-that-trigger-full-reindexing) wie eine Änderung des Produktpreises oder des Lagerbestands ausgelöst.

Der Katalog-Synchronisierungs-Service verschiebt Produktdaten laufend von einer [!DNL Adobe Commerce]-Instanz zur [!DNL Commerce Services]-Plattform, um die Daten auf dem neuesten Stand zu halten. Beispielsweise erfordert [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) aktuelle Kataloginformationen, um Empfehlungen mit korrekten Namen, Preisen und Verfügbarkeit genau zurückzugeben. Verwenden Sie das _Catalog Sync_-Dashboard, um den Synchronisierungsprozess oder die Befehlszeilenschnittstelle zu beobachten und zu verwalten, um eine Katalogsynchronisierung Trigger und Produktdaten für die Nutzung durch [!DNL Commerce Services] neu zu indizieren. Siehe [Referenz zur Befehlszeilenschnittstelle](../data-export/data-export-cli-commands.md) im _SaaS-_.

## Zugriff auf das Dashboard zur Katalogsynchronisierung

Um auf das Dashboard für die Katalogsynchronisierung zuzugreifen, wählen Sie **System** > _Datenübertragung_ > **Katalogsynchronisierung** aus.

Mit dem Dashboard **Katalogsynchronisierung** können Sie:

- Anzeigen des Synchronisierungsstatus (**In Bearbeitung**, **Erfolg**, **Fehlgeschlagen**)
- Anzeigen der Gesamtzahl der synchronisierten Produkte
- Synchronisierte Produkte suchen, um ihren aktuellen Status anzuzeigen
- Store-Katalog nach Name, SKU usw. durchsuchen
- Anzeigen synchronisierter Produktdetails in JSON, um eine Synchronisierungsdiskrepanz zu diagnostizieren
- Synchronisierungsvorgang neu starten

### Letzte Synchronisierung

meldet einen Synchronisierungsstatus von:

- **Erfolg**: Zeigt das Datum und die Uhrzeit an, zu der die Synchronisierung erfolgreich war und die Anzahl der aktualisierten Produkte
- **Fehlgeschlagen** - Zeigt Datum und Uhrzeit des Synchronisierungsversuchs an.
- **In Bearbeitung** - Zeigt Datum und Uhrzeit der letzten erfolgreichen Synchronisierung an

Der Katalogsynchronisierungsvorgang wird automatisch jede Stunde ausgeführt. Wenn in der Storefront keine erwarteten Produkte angezeigt werden oder die Produkte Ihre letzten Änderungen nicht widerspiegeln, können Sie [Probleme mit der Katalogsynchronisierung](#resolvesync) beheben.

### Produkte synchronisiert

Zeigt die Gesamtzahl der aus Ihrem [!DNL Commerce] synchronisierten Produkte an. Nach der ersten Synchronisierung sollten nur geänderte Produkte synchronisiert werden.

## Resynchronisation {#resync}

Wenn Sie eine erneute Synchronisierung Ihres Katalogs vor der stündlich geplanten Synchronisierung initiieren müssen, können Sie eine erneute Synchronisierung erzwingen.

>[!NOTE]
>
> Erzwungene Neusynchronisierung des gesamten Produktkatalogs für Trigger, wodurch die Belastung der Hardware-Ressourcen erhöht werden kann.

1. Wählen Sie im Dashboard _Katalogsynchronisierung_ die Option **Einstellungen** aus.

   Die _Katalogsynchronisierungseinstellungen_ wird angezeigt.

1. Klicken _im Abschnitt „Daten_&quot; auf [!UICONTROL Resync].

   [!DNL Commerce] synchronisiert Ihren Katalog im nächsten geplanten Synchronisierungsfenster. Je nach Größe Ihres Katalogs kann dieser Vorgang lange dauern.

## Synchronisierte Katalogprodukte

Die Tabelle **Synchronisierte Katalogprodukte** zeigt die folgenden Informationen an.

| Feld | Beschreibung |
|---|---|
| ID | Eindeutige Kennung des Produkts |
| -Name | Name der Storefront des Produkts |
| Typ | Identifiziert den Produkttyp, z. B. einfach, konfigurierbar oder herunterladbar |
| Zuletzt exportiert | Datum, an dem das Produkt zuletzt erfolgreich aus Ihrem Katalog exportiert wurde |
| Zuletzt geändert | Datum der letzten Änderung des Produkts in Ihrem Katalog |
| SKU | Zeigt die Lagereinheit für das Produkt an |
| Preis | Preis des Produkts |
| Sichtbarkeit | Sichtbarkeitseinstellung eines Produkts gemäß Definition im [!DNL Commerce] |

## Beheben von Katalogsynchronisierungsproblemen {#resolvesync}

Siehe [Protokolle und Fehlerbehebung](../data-export/troubleshooting-logging.md#troubleshooting) im _SaaS-Datenexporthandbuch_.
