---
title: Hintergrundprozesskonfiguration
description: Konfigurieren Sie die Zeitpläne für  [!DNL Store Fulfillment]  Prozesse im Hintergrund, die zum Synchronisieren von Daten mit den Fulfillment-Services verwendet werden.
role: Admin, Developer
level: Intermediate
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Hintergrundprozesskonfiguration

Die Store-Fulfillment-Integration verwendet Hintergrundprozesse und Nachrichtenwarteschlangen für eine optimale Leistung und Skalierung. Erstellen Sie Umgebungen für Ihre Adobe Commerce-Stores mit [Bereitstellungsvariablen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#cron_consumers_runner) die automatisch gestartet werden [Message Queue Runner](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework).

Hintergrundprozesse werden mithilfe der standardmäßigen Adobe Commerce-Funktion [Geplante Aufgaben](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/cron) verwaltet. Diese Prozesse sind für die Synchronisierung der Konfigurationsdaten von Bestellungen und Händlern mit Web-Services für die Store-Erfüllung verantwortlich.

## Geplante Aufgaben für Store Fulfillment verwalten

Navigieren Sie vom Administrator zu **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Überprüfen Sie die Standardkonfiguration für Store Fulfillment-Services. Sie können diese Einstellungen je nach Auftragsverarbeitungsvolumen und Ressourcenverfügbarkeit anpassen.
