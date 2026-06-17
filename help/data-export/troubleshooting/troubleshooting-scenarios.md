---
title: Fehlerbehebungsszenarien für [!DNL SaaS Data Export]
description: Erfahren Sie, wie Sie ein unerwartetes  [!DNL SaaS Data Export] -Verhalten diagnostizieren und beheben können, das durch eine Fehlkonfiguration, Indexereinstellungen oder falsche Interpretation von Synchronisierungsergebnissen verursacht wurde.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7id: c32adafa-ed01-4b31-997e-2413013911b0id: e7dae43f-215c-4cdf-90d3-c5a461a6e669id: c18ed297-2187-4aec-affb-9d9654eca6fc
subfeature_v2: id: a40ebd6b-b542-4432-a730-1803ef74518d
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 991
ht-degree: 0%

---


# Fehlerbehebungsszenarien für [!DNL SaaS Data Export]

Auf dieser Seite werden Verhaltensweisen beschrieben, die Sie beim Arbeiten mit den [!DNL SaaS Data Export] beobachten können und die normalerweise durch eine falsche Konfiguration oder Interpretation von Synchronisierungsergebnissen verursacht werden. Verwenden Sie die folgenden Beschreibungen, um die Grundursache zu identifizieren und die entsprechende Lösung anzuwenden.

## Konfigurierbares Produkt oder Bundle fehlt in Commerce-Services {#configurable-bundle-missing}

**Problem:** Ein konfigurierbares oder gebündeltes Produkt hat den Status *Aktiviert* in [!DNL Adobe Commerce], wird jedoch entweder nicht in der Storefront zurückgegeben oder in den SaaS-Services von Commerce mit dem Status *Deaktiviert* angezeigt.

**Ursache:** Der effektive Status von zusammengesetzten Produkten hängt vom Status ihrer untergeordneten Produkte ab, nicht nur vom Status des übergeordneten Produkts. Commerce SaaS-Services spiegeln diesen berechneten Status wider:

- **Konfigurierbare Produkte** - Es muss mindestens eine Produktvariante aktiviert sein.
- **Bundle-**: Für jede erforderliche Bundle-Option muss mindestens ein Produkt aktiviert sein.

Wenn diese Bedingungen nicht erfüllt sind, wird das übergeordnete Produkt als deaktiviert behandelt, selbst wenn sein eigener Status auf *Aktiviert“*.

**Lösung:**

- Stellen Sie bei konfigurierbaren Produkten sicher, dass mindestens eine zugehörige einfache Produktvariante aktiviert und der richtigen Website- und Store-Ansicht zugewiesen ist.
- Stellen Sie bei Bundle-Produkten sicher, dass jede erforderliche Bundle-Option über mindestens ein aktiviertes untergeordnetes Produkt verfügt. Eine erforderliche Option mit allen deaktivierten untergeordneten Elementen bewirkt, dass das gesamte Bundle als deaktiviert behandelt wird.
- Nachdem Sie die entsprechenden untergeordneten Produkte aktiviert haben, synchronisieren Sie den Trigger erneut oder warten Sie auf die nächste geplante Synchronisierung. Bestätigen Sie dann den aktualisierten Status in den Commerce SaaS-Services.

## Preise werden nach Aktivierung der Katalogpreisregel nicht aktualisiert {#prices-not-updated}

**Problem:** Nach der Aktivierung einer Katalogpreisregel mit der Funktion „Geplantes Update“ werden die Preise nicht aktualisiert. Die `commerce-data-export.log` zeigt `synced: 0` für `prices` Feed an, nachdem geplante Aktualisierungen angewendet wurden.

**Ursache:** Es kann zu einer Wettlaufsituation zwischen Cron-Gruppen kommen, wenn geplante Updates für Katalogpreisregeln verwendet werden. Der `catalog_data_exporter_product_prices` Indexer kann ausgeführt werden, bevor seine Abhängigkeit, der `catalogrule_product`, den Neuaufbau abgeschlossen hat. Infolgedessen liest der Preisexporteur veraltete Daten und exportiert keine Änderungen.

**Lösung:**

Die sofortige Lösung für dieses Problem ist eine Problemumgehung: Konfigurieren Sie beide Cron-Gruppen so, dass sie sequenziell ausgeführt werden, um die Wettlaufbedingung zu beseitigen:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Cron (Scheduled Tasks)]**.
1. Legen Sie **[!UICONTROL Use Separate Process]** für beide auf **[!UICONTROL No]** fest:
   - Cron-Konfigurationsoptionen für Gruppe: **[!UICONTROL index]**
   - Cron-Konfigurationsoptionen für Gruppe: **[!UICONTROL staging]**
1. Leeren Sie den Konfigurations-Cache nach dem Speichern.

>[!NOTE]
>
>Da beide Gruppen sowohl im Prozess als auch sequenziell ausgeführt werden, blockiert eine langsame vollständige Neuindizierung die Staging-Ausführung bis zum Abschluss. Bei großen Katalogen kann dies Staging-Aktualisierungen verzögern.

## Diskrepanz bei Katalogdaten zwischen [!DNL Adobe Commerce] und verbundenen Services {#catalog-data-discrepancy}

**Problem:** Produktdaten, die in verbundenen Commerce-Services angezeigt werden (z. B. [!DNL Live Search] oder [!DNL Product Recommendations]), stimmen nicht mit den Katalogdaten in [!DNL Adobe Commerce] überein. Beispielsweise erscheint ein Produktname, ein Preis oder eine Beschreibung in der Storefront veraltet oder falsch.

**Ursache:** Nachdem eine Neusynchronisierung ausgelöst wurde, kann es bis zu einer Stunde dauern, bis die Daten aktualisiert und in Benutzeroberflächenkomponenten angezeigt werden. Wenn die Diskrepanz über dieses Fenster hinaus weiterhin besteht, wurde das Element möglicherweise bei der letzten Synchronisierung nicht aufgenommen oder die Synchronisierung hat keine Änderung erkannt, da die Feed-Daten bereits als „auf dem neuesten Stand“ markiert waren.

**Lösung:**

1. Öffnen Sie in der Commerce-Storefront die Suchergebnisse. Wählen Sie dann das betreffende Produkt aus, um seine Detailansicht zu öffnen.
1. Kopieren Sie die JSON-Ausgabe und überprüfen Sie, ob sie mit dem übereinstimmt, was Sie im [!DNL Commerce] Katalog haben.
1. Wenn der Inhalt nicht übereinstimmt, nehmen Sie eine geringfügige Änderung am Produkt in Ihrem Katalog vor, z. B. das Hinzufügen eines Leerzeichens oder eines Punkts, um die Erkennung der Änderung zu erzwingen.
1. Warten Sie auf eine Neusynchronisierung oder einen Trigger oder eine manuelle Neusynchronisierung der CLI oder [[!UICONTROL Data Feed Sync Status]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status) Seite im Admin Console.

Weitere Informationen zur Fehlerbehebung bei Katalogdaten in [!DNL Product Recommendations] finden Sie unter [Fehlerbehebung beim Modul „Produktempfehlungen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce) in der Commerce Knowledge Base.

## Datensynchronisation läuft nicht planmäßig {#sync-not-on-schedule}

**Problem:** Die Datensynchronisation wird nicht planmäßig ausgeführt oder es werden trotz Produktänderungen in [!DNL Adobe Commerce] keine Elemente synchronisiert.

**Ursache:** Die häufigsten Ursachen sind Cron-Aufträge, die nicht ausgeführt werden, oder Indexer, die nicht im **[!UICONTROL Update by Schedule]** konfiguriert sind.

**Lösung:**

- [Bestätigen Sie, dass Cron-Aufträge ausgeführt werden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Stellen Sie sicher, dass die Indexer für die folgenden Feeds auf **[!UICONTROL Update by Schedule]** eingestellt sind: Katalogattribute, Produkt, Produktüberschreibungen und Produktvariante. Führen Sie eine Überprüfung von [[!UICONTROL Index Management]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) in Commerce Admin durch oder verwenden Sie die CLI: `bin/magento indexer:show-mode | grep -i feed`.

## Katalogsynchronisierung hat den Status Fehlgeschlagen . {#catalog-sync-failed}

**Problem:** Katalogsynchronisierung zeigt auf der **[!UICONTROL Data Feed Sync Status]** den Status **Fehlgeschlagen** an.

**Ursache:** Während der Datenerfassungs- oder -übermittlungsphase ist ein nicht behebbarer Fehler aufgetreten. Häufige Ursachen sind Probleme bei der API-Authentifizierung, Netzwerkfehler oder Fehler bei der Datenvalidierung.

**Lösung:**

1. Überprüfen Sie die Fehlerprotokolle zu Datenexporten, um Details zum Fehler zu erhalten. Siehe [Überprüfen von Protokollen und Fehlerbehebung](logging.md) für Protokollformat und erweiterte Protokollierungsoptionen:
   - `var/log/commerce-data-export-errors.log` auf Fehler bei der Datenerfassung.
   - `var/log/saas-export-errors.log` auf Fehler bei der Datenübermittlung.
1. Wenn der Fehler nicht mit der Konfiguration oder einer Erweiterung eines Drittanbieters zusammenhängt, [ Sie ein Support-Ticket ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) den entsprechenden Protokolleinträgen.

## Protokoll zeigt Meldungen vom Typ „Vorgang übersprungen - Prozess gesperrt“ {#process-locked}

**Problem:** Die `commerce-data-export.log` enthält Einträge, die den folgenden ähneln:

```json
{"feed":"products","operation":"partial sync","status":"operation skipped - process locked by \"full sync(1234)\"", ...}
```

**Ursache:** Dies ist ein erwartetes Verhalten, kein Fehler. Die Meldung wird angezeigt, wenn eine durch Cron ausgelöste partielle Synchronisierung versucht, ausgeführt zu werden, während bereits eine vollständige Neuindizierung oder `saas:resync` ausgeführt wird. Die [!DNL SaaS Data Export]-Erweiterung verwendet einen Feed-Sperrmechanismus, um widersprüchliche gleichzeitige Synchronisierungsvorgänge zu verhindern.

**Lösung:**

Es ist keine Aktion erforderlich. Sobald der laufende Prozess abgeschlossen ist und die Sperre aufhebt, erfasst und synchronisiert die nächste Cron-Ausführung alle ausstehenden Änderungen. Einzelheiten zur Funktionsweise des Sperrmechanismus finden Sie unter [Feed-Sperrmechanismus für SaaS-Datenexport](../feed-lock-mechanism.md).

>[!MORELIKETHIS]
>
> - [Überprüfen Sie die Protokolle und führen Sie eine Fehlerbehebung durch](logging.md)
> - [Protokollcodes-Referenz](log-codes-reference.md)
> - [Feed-Lock-Mechanismus für SaaS-Datenexport](../feed-lock-mechanism.md)
