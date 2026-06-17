---
title: manage [!DNL Adobe Commerce Optimizer Connector] synchronization
description: Erfahren Sie, wie Sie die Synchronisierung von Katalogdaten überprüfen und Connector-Feeds zwischen  [!DNL Adobe Commerce]  und  [!DNL Adobe Commerce Optimizer] manuell neu synchronisieren.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
subfeature_v2:
  - id: a40ebd6b-b542-4432-a730-1803ef74518d
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 287
ht-degree: 0%

---

# Verwalten der Synchronisierung mit [!DNL Commerce Optimizer]

Nachdem Sie die [!DNL Adobe Commerce Optimizer Connector] eingerichtet haben, werden die meisten Katalogaktualisierungen automatisch über geplante Cron-Aufträge synchronisiert. Weitere Informationen zur Funktionsweise der automatisierten Synchronisierung finden Sie unter [Connector-Synchronisierungs-Pipeline](connector-sync-pipeline.md). Verwenden Sie die Tools in diesem Thema, um zu überprüfen, ob die Daten [!DNL Adobe Commerce Optimizer] erreichen, und um Feeds bei Bedarf manuell neu zu synchronisieren.

## Überprüfen, ob die Datensynchronisation funktioniert {#verify-that-the-data-sync-is-working}

{{$include /help/_includes/aco-connector/verify-optimizer-data-sync.md}}

## Daten manuell neu synchronisieren {#manually-resync-data}

Wenn Synchronisierungsprobleme durch teilweise Synchronisierung und automatische erneute Versuche nicht behoben werden, können Sie die Katalogdaten manuell neu synchronisieren. Welche Option Sie auswählen, hängt davon ab, wo das Problem seinen Ursprung hat und wie viel Kontrolle Sie benötigen.

| Aufgabe | Option | Notizen |
| --- | --- | --- |
| Überprüfen Sie den Synchronisierungsstatus und synchronisieren Sie erneut vom vorgelagerten System, wenn Produkte fehlen. | **Resynchronisation des Upstream-Systems** | Wählen Sie in [!DNL Commerce Optimizer] die Option **[!UICONTROL Data Sync]** aus und überprüfen Sie, ob die erwarteten Katalogquellen, Produkte, Preise und Attribute angezeigt werden. Wenn Produkte fehlen, synchronisieren Sie mithilfe der **[!UICONTROL Data Feed Sync Status]** oder der Commerce-CLI von der Upstream-[!DNL Adobe Commerce]-Instanz neu (siehe folgende Zeilen). |
| Ausgewählte fehlgeschlagene oder problematische Feed-Elemente des Connectors neu synchronisieren | **[!UICONTROL Data Feed Sync Status]Seite in Commerce Admin** | Überwachen Sie den Exportstatus und synchronisieren Sie ausgewählte Connector-Feed-Elemente über Commerce Admin erneut. Siehe [Überprüfen, ob die Datensynchronisation funktioniert](#verify-that-the-data-sync-is-working). |
| Zielgerichteter Connector-Feed resynchronisiert mit Betriebssteuerung | **Commerce-CLI** | Führen Sie `saas:resync` über die Adobe Commerce-Instanz für Connector-Feeds aus. Siehe [Synchronisieren von Feeds mit der Commerce-CLI](../data-export/data-export-cli-commands.md) und [Unterstützte Feeds](reference/connector-reference.md#supported-feeds). |

>[!MORELIKETHIS]
>
> - [Connector-Synchronisierungs](connector-sync-pipeline.md)-Pipeline - Erfahren Sie, wie automatisierte Synchronisierung, Cron-Zeitpläne und Fehlerbehandlung funktionieren
> - [Geschätztes Datenvolumen und Synchronisierungszeit](reference/estimate-data-volume-sync-time.md) — Berechnet die erwartete Synchronisierungsdauer.
> - [Fehlerbehebung](troubleshooting.md) - Diagnose von Problemen mit Berechtigungen, Synchronisierung und dem Umfang von Exportvorgängen
> - [Connector-Module und Feed-](reference/connector-reference.md): Überprüfungsmodule, API-Endpunkte und unterstützte Feeds
