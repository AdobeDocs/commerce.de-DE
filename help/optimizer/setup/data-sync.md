---
title: Datensynchronisation
description: Erfahren Sie, wie Sie Ihre Katalogdaten mit [!DNL Adobe Commerce Optimizer] synchronisieren.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: f49a86b8793e2d91413acfbc0b922cb94db67362
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Datensynchronisation

Auf der Seite **Datensynchronisierung** wird ein Überblick über den Synchronisierungsstatus für Produktdaten angezeigt, die aus Ihrer Datenquelle (Ihrem bestehenden Commerce-Katalog, PIM-System (Product Information Management), ERP-System (Enterprise Resource Planning) usw.) in [!DNL Adobe Commerce Optimizer] übertragen wurden.

Die **Datensynchronisation** Seite bietet wertvolle Einblicke in die Verfügbarkeit von Produktdaten für Ihre Storefront, sodass sie Ihren Kundinnen und Kunden sofort angezeigt werden können.

Die **Datensynchronisation** befindet sich unter *Setup* > **Datensynchronisation**.

![Datensynchronisation](../assets/data-sync.png)

Die **Datensynchronisation** enthält die folgenden Felder:

| Feld | Beschreibung |
|--- |--- |
| Katalogquelle | Spezifisches Gebietsschema für die synchronisierten Daten. |
| [!DNL Catalog Service] | Zeigt das neueste Synchronisierungsupdate, die Gesamtzahl der empfangenen Produkte, ein Suchfeld und eine Tabelle der synchronisierten Produkte für [!DNL Catalog Service] an. |
| Produkterkennung | Zeigt das neueste Synchronisierungsupdate, die Gesamtzahl der empfangenen Produkte, ein Suchfeld und eine Tabelle der synchronisierten Produkte für die Suche an. |
| Recommendations | Zeigt das neueste Synchronisierungsupdate, die Gesamtzahl der empfangenen Produkte, ein Suchfeld und eine Tabelle der synchronisierten Produkte für Recommendations an. |
| In den letzten 3 Stunden erhaltene Produkte | Zeigt die Anzahl der Produkte an, die innerhalb der letzten drei Stunden von der Katalogquelle an Adobe Commerce Optimizer übertragen wurden. Wenn Sie Ihren Katalog gelegentlich aktualisieren, ist dieser Wert häufig null. |
| Gesamtzahl der Produkte im Katalog | Gibt die Gesamtzahl der Katalogprodukte an, die für Adobe Commerce Optimizer verfügbar sind. |
| Synchronisierte Produkte | Enthält Details zu den mit Adobe Commerce Optimizer synchronisierten Produkten. Standardmäßig wird diese Tabelle nach „Zuletzt aktualisiert“ sortiert. Um ein bestimmtes Produkt zu finden, verwenden Sie das Feld **[!UICONTROL Search by Name or SKU]** . |

## Liste der synchronisierten Produkte

Um die Details eines synchronisierten Produkts im JSON-Format anzuzeigen, klicken Sie auf das Code-Symbol ![Code-Link](../assets/data-sync-details.png) in der Zeile des Produkts in der Tabelle der synchronisierten Produkte.

![Produktdetails synchronisieren](../assets/synced-products.png)

## Katalogdaten neu synchronisieren

Wenn bestimmte Produkte nicht auf der Seite **Datensynchronisierung** angezeigt werden, müssen Sie eine Neusynchronisierung von Ihrem vorgelagerten System aus starten. Beachten Sie jedoch, dass eine Neusynchronisierung die Belastung für Hardware-Ressourcen erhöhen kann. In den folgenden Szenarien kann es jedoch erforderlich sein, den Katalog neu zu synchronisieren:

- Wenn wesentliche Änderungen an Ihrem Produktkatalog vorgenommen werden, z. B. beim Hinzufügen neuer Produkte, Aktualisieren von Produktdetails oder Ändern von Kategorien

- Wenn Sie Diskrepanzen oder Leistungsprobleme bei der Anzeige von Produktdaten auf Ihren Storefronts bemerken

>[!IMPORTANT]
>
>Die Dauer der Synchronisierung hängt von der Größe Ihres Katalogs und der Menge der aktualisierten Daten ab.
