---
source-git-commit: 18c4528fade63545415135808d2d40ac2b95e86d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%
---
Auf der Seite **Datensynchronisierung** wird ein Überblick über den Synchronisierungsstatus für Produktdaten angezeigt, die aus Ihrer Datenquelle (Ihrem bestehenden Commerce-Katalog, PIM-System (Product Information Management), ERP-System (Enterprise Resource Planning) usw.) in die Merchandising Services-Datenschicht übertragen wurden.

Die **Datensynchronisation** Seite bietet wertvolle Einblicke in die Verfügbarkeit von Produktdaten für Ihre Storefront, sodass sie Ihren Kundinnen und Kunden sofort angezeigt werden können.

## Zugriff auf den Arbeitsbereich „Datensynchronisation“

Wie Sie den Arbeitsbereich *Datensynchronisierung* öffnen, hängt vom verwendeten Produkt ab:

- **Adobe Commerce Admin** (Adobe Commerce as a Cloud Service) - Wählen Sie *Stores* > **Katalogsynchronisierung**.
- **Adobe Commerce Optimizer Studio** - Wählen Sie *Store-Setup* > **Datensynchronisierung**.

![Datensynchronisation](/help/assets/ccdm-shared/setup/data-sync.png)

Die **Datensynchronisation** enthält die folgenden Felder:

| Feld | Beschreibung |
| --- | --- |
| Katalogquelle | Spezifisches Gebietsschema für die synchronisierten Daten. |
| [!DNL Catalog Service] | Zeigt das neueste Synchronisierungsupdate, die Gesamtzahl der empfangenen Produkte, ein Suchfeld und eine Tabelle der synchronisierten Produkte für [!DNL Catalog Service] an. |
| Produkterkennung | Zeigt das neueste Synchronisierungsupdate, die Gesamtzahl der empfangenen Produkte, ein Suchfeld und eine Tabelle der synchronisierten Produkte für die Suche an. |
| Recommendations | Zeigt das neueste Synchronisierungsupdate, die Gesamtzahl der empfangenen Produkte, ein Suchfeld und eine Tabelle der synchronisierten Produkte für Recommendations an. |
| In den letzten 3 Stunden erhaltene Produkte | Zeigt die Anzahl der Produkte an, die innerhalb der letzten drei Stunden von der Katalogquelle zur Merchandising Services-Datenschicht übertragen wurden. Wenn Sie Ihren Katalog gelegentlich aktualisieren, ist dieser Wert häufig null. |
| Gesamtzahl der Produkte im Katalog | Gibt die Gesamtzahl der Katalogprodukte an, die in der Datenschicht für Merchandising-Services verfügbar sind. |
| Synchronisierte Produkte | Enthält Details zu den Produkten, die mit der Merchandising Services-Datenschicht synchronisiert werden. Standardmäßig wird diese Tabelle nach „Zuletzt aktualisiert“ sortiert. Um ein bestimmtes Produkt zu finden, verwenden Sie das Feld **[!UICONTROL Search by Name or SKU]** . |

## Liste der synchronisierten Produkte

Um die Details eines synchronisierten Produkts im JSON-Format anzuzeigen, klicken Sie auf das Code-Symbol ![Code-Link](/help/assets/ccdm-shared/setup/data-sync-details.png) in der Zeile des Produkts in der Tabelle der synchronisierten Produkte.

![Synchronisierte Produktdetails](/help/assets/ccdm-shared/setup/synced-products.png)

## Katalogdaten neu synchronisieren

Wenn bestimmte Produkte nicht auf der Seite **Datensynchronisierung** angezeigt werden, müssen Sie eine Neusynchronisierung von Ihrem vorgelagerten System aus starten. Beachten Sie jedoch, dass eine Neusynchronisierung die Belastung für Hardware-Ressourcen erhöhen kann. In den folgenden Szenarien kann es jedoch erforderlich sein, den Katalog neu zu synchronisieren:

- Wenn wesentliche Änderungen an Ihrem Produktkatalog vorgenommen werden, z. B. beim Hinzufügen neuer Produkte, Aktualisieren von Produktdetails oder Ändern von Kategorien

- Wenn Sie Diskrepanzen oder Leistungsprobleme bei der Anzeige von Produktdaten auf Ihren Storefronts bemerken

>[!IMPORTANT]
>
>Die Dauer der Synchronisierung hängt von der Größe Ihres Katalogs und der Menge der aktualisierten Daten ab.

## Überprüfen, ob die Datensynchronisierung funktioniert

Bei Projekten, die Adobe Commerce als Upstream-Datenquelle verwenden, können Sie den Datenexportprozess überwachen und Resynchronisierungsvorgänge über die Seite Daten-Feed-Synchronisierungsstatus initiieren. Weitere Informationen finden Sie unter [Überwachung des Synchronisierungsstatus von Daten-Feeds](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status).
