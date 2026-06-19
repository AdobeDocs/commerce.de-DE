---
title: Fehlerbehebung bei [!DNL Adobe Commerce Optimizer Connector]
description: Erfahren Sie, wie Sie  [!DNL Adobe Commerce Optimizer Connector] -/Berechtigungs-, Katalogsynchronisierungs- und Bereichsexportprobleme für PaaS [!DNL Adobe Commerce] Integrationen beheben können.
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
autotag-review: '2026-06-09T19:00:00.000Z'
TQID: 'https://experienceleague.adobe.com/ei86QuJ3nQ2d-6NRoAeJslgDxjGlZRejD-Nx-6SAVdc'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7id: c32adafa-ed01-4b31-997e-2413013911b0id: e7dae43f-215c-4cdf-90d3-c5a461a6e669id: c18ed297-2187-4aec-affb-9d9654eca6fc
subfeature_v2: id: a40ebd6b-b542-4432-a730-1803ef74518d
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 331
ht-degree: 0%

---

# Fehlerbehebung bei der [!DNL Adobe Commerce Optimizer Connector]

Verwenden Sie dieses Handbuch, um häufige Probleme mit dem [!DNL Adobe Commerce Optimizer Connector] während der Ersteinrichtung, der Synchronisierung von Katalog-Feeds und der Konfiguration des Umfangs-Exports zu diagnostizieren und zu beheben. In den folgenden Abschnitten werden die Validierung von Berechtigungen und Mandanten, Fehler bei der Datensynchronisierung und die Diagnose im Zusammenhang mit [!DNL SaaS Data Export] behandelt.

## Die Validierung der Anmeldeinformationen oder des Mandanten schlägt fehl

Wenn die `aco:config:init` bei der Überprüfung der Berechtigung fehlschlägt:

- Führen Sie den `bin/magento aco:config:show` [!DNL Adobe Commerce] CLI-Befehl aus, um die gespeicherten Werte zu überprüfen.
- Vergewissern Sie sich, dass die Mandanten-ID zu der IMS-Organisation gehört, die zum Abrufen der Anmeldeinformationen verwendet wird.
- Überprüfen Sie, ob der OAuth-Client über die erforderlichen Bereiche für den [!DNL Adobe Commerce Optimizer]-Aufnahme-Service verfügt (siehe [Abrufen von IMS-Anmeldeinformationen](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/authentication/#obtain-ims-credentials)).

## Daten werden nicht synchronisiert

**Fehlerdetails auf Elementebene überprüfen:**

Unter [Überprüfen, ob die Datensynchronisation funktioniert](./data-sync-manage.md#verify-that-the-data-sync-is-working) finden Sie Schritte zum Öffnen von **[!UICONTROL Data Feed Sync Status]** in Commerce Admin. Wählen Sie den fehlgeschlagenen Feed aus, um Fehlerdetails pro Element anzuzeigen.

Wichtige Punkte zur Fehlerbehandlung:

- **400-Fehler** werden nicht erneut versucht. Überprüfen Sie die Payload auf falsch formatierte oder fehlende erforderliche Felder. Siehe [Feldzuordnung für Connector-Feeds](reference/field-mapping.md) für das erwartete Format.
- **5xx-Fehler** werden vom `*_resend_failed_items` Cron-Auftrag automatisch wiederholt (wird alle 5 Minuten ausgeführt).

**Konfiguration des Umfangs überprüfen:**

Wenn das Problem nur eine bestimmte Katalogquelle (Shop-Ansicht-Code) oder ein bestimmtes Preisbuch betrifft, überprüfen Sie, ob die Synchronisierung der entsprechenden Website oder Shop-Ansicht deaktiviert ist. Siehe [Anpassen der Exportkonfiguration für Commerce](./get-started.md#customize-the-commerce-scopes-export-configuration).

**Nach Lösung:**

Connector-Feeds zeigen in **[!UICONTROL Data Feed Sync Status]** den Status Erfolgreich an, und die erwarteten Produkte, Preise und Attribute werden auf der Seite **[!UICONTROL Data Sync]** in [!DNL Commerce Optimizer] angezeigt.

## Fehlkonfiguration und Ergebnisauswertung

Einen Katalog spezifischer Verhaltensweisen, die durch eine falsche Konfiguration oder Interpretation von Synchronisierungsergebnissen verursacht werden - wie fehlende Produkte, falsche Preise oder Datenlücken auf Bereichsebene - finden Sie unter [Fehlerbehebungsszenarien](troubleshooting/troubleshooting-scenarios.md).

## [!DNL SaaS Data Export]

Informationen zu [!DNL SaaS Data Export] auf niedrigerer Ebene, einschließlich Protokollspeicherorten und Befehlen zur Resynchronisierung des Feeds, finden Sie im [[!DNL SaaS Data Export]  zur Fehlerbehebung](https://experienceleague.adobe.com/en/docs/commerce/saas-data-export/troubleshooting/logging){target="_blank"}.
