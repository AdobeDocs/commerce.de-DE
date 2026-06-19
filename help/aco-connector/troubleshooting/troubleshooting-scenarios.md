---
title: Fehlerbehebungsszenarien für den  [!DNL Adobe Commerce Optimizer Connector]
description: Diagnostizieren und beheben Sie unerwartetes Verhalten in  [!DNL Adobe Commerce Optimizer Connector] , das durch eine falsche Konfiguration oder Fehlinterpretation von Synchronisierungsergebnissen verursacht wurde.
autotag-review: '2026-06-17T15:08:59.000Z'
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
subfeature_v2:
  - id: a40ebd6b-b542-4432-a730-1803ef74518d
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 182aa9ce819807d1ede85c4fa459714e7dfe0478
workflow-type: tm+mt
source-wordcount: 516
ht-degree: 0%

---


# Fehlerbehebungsszenarien für die [!DNL Adobe Commerce Optimizer Connector]

Auf dieser Seite werden Verhaltensweisen beschrieben, die Sie beim Arbeiten mit den [!DNL Adobe Commerce Optimizer Connector] beobachten können und die normalerweise durch eine falsche Konfiguration oder Interpretation von Synchronisierungsergebnissen verursacht werden. Verwenden Sie die folgenden Beschreibungen, um die Grundursache zu identifizieren und die entsprechende Lösung anzuwenden.

## Der Feedstatus zeigt „Erfolg“ an, aber die Daten sind in [!DNL Adobe Commerce Optimizer] nicht sichtbar

**Problem:** Die **[!UICONTROL Data Feed Sync Status]** meldet eine erfolgreiche Synchronisierung, aber Produkte, Preise usw. werden in [!DNL Adobe Commerce Optimizer] nicht wie erwartet angezeigt.

**Ursache:** Ein erfolgreicher Feed-Status bedeutet, dass die Daten vom Aufnahme-Endpunkt akzeptiert wurden und nicht, dass die Übertragung durch [!DNL Adobe Commerce Optimizer] abgeschlossen ist. Die Vermehrung kann mehrere Minuten nach der Aufnahme dauern.

**Lösung:**

- Warten Sie einige Minuten und aktualisieren Sie die [!DNL Adobe Commerce Optimizer].
- Vergewissern Sie sich, dass die in [!DNL Adobe Commerce] konfigurierte Mandanten-ID mit der [!DNL Commerce Optimizer] Umgebung übereinstimmt, die Sie überprüfen.
- Überprüfen Sie, ob [&#x200B; richtige (](../../optimizer/setup/catalog-sources.md)) oder das richtige Preisbuch in [!DNL Commerce Optimizer] ausgewählt ist.

## Produkte fehlen im exportierten Katalog

**Problem** Einige Produkte werden nach einer vollständigen Katalogsynchronisierung nicht in [!DNL Adobe Commerce Optimizer] angezeigt.

**Ursache:** Wenn die Validierung von Produkten beim Export fehlschlägt, werden sie nicht synchronisiert. Produkte, die deaktiviert oder im Katalog nicht sichtbar sind, werden von der Produkt-API nicht zurückgegeben.

**Lösung:**

- Vergewissern Sie sich, dass die betroffenen Produkte der Website zugewiesen sind und die Store-Ansicht als Katalogquelle verwendet wird.
- Vergewissern Sie sich, dass die Produkte aktiviert sind und auf eine Sichtbarkeit eingestellt sind, die Kataloglisten enthält.
- Überprüfen Sie die Fehlerdetails pro Element für den Katalog-Feed unter **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Data Feed Sync Status]**.

## Preise sind falsch oder fehlen in [!DNL Adobe Commerce Optimizer]

**Problem:** Produkte werden in [!DNL Adobe Commerce Optimizer] angezeigt, zeigen aber keinen Preis an, der mit [Produkte - GraphQL-](https://developer.adobe.com/commerce/services/reference/graphql/#products){target="_blank"}) zurückgegeben wurde, oder der Preis stimmt nicht mit dem überein, was in [!DNL Adobe Commerce] konfiguriert ist.

**Ursache:** Der Preisbuchfeed verwendet einen Bereich, der einer bestimmten Website und Kundengruppe zugeordnet ist. Eine falsche Konfiguration [Katalogansicht](../../optimizer/setup/catalog-view.md) kann zu fehlenden oder falschen Preisen führen.

**Lösung:**

- Stellen Sie sicher, dass die Website in der Exportkonfiguration des Connectors für die Synchronisierung konfiguriert ist. Siehe [Anpassen der Datenexportkonfiguration](../get-started.md#customize-the-commerce-scopes-export-configuration).
- Vergewissern Sie sich, dass die in [!DNL Commerce Optimizer] verwendete Preisbuch-ID in der Konfiguration [Katalogansicht](../../optimizer/setup/catalog-view.md){target="_blank"} vorhanden ist, die für die Produktabfrage verwendet wird.

## Daten in [!DNL Adobe Commerce Optimizer] werden nach der Synchronisierung überschrieben oder unerwartet geändert

**Problem** Datenänderungen, die direkt in [!DNL Adobe Commerce Optimizer] von einem externen System (z. B. einem PIM oder ERP) angewendet werden, gehen verloren oder werden rückgängig gemacht, nachdem der Connector eine Synchronisierung ausgeführt hat.

**Ursache:** Wenn andere Systeme als [!DNL Adobe Commerce] direkt in [!DNL Adobe Commerce Optimizer] schreiben, z. B. ein PIM oder ein anderes externes System, können Datenkonflikte auftreten. Der Connector synchronisiert *auf eine Weise* von [!DNL Adobe Commerce] nach [!DNL Adobe Commerce Optimizer] und synchronisiert keine Änderungen zurück nach [!DNL Adobe Commerce]. Folglich werden direkt in [!DNL Adobe Commerce Optimizer] geschriebene Daten nicht in [!DNL Adobe Commerce] übernommen und können bei einer späteren Synchronisierung überschrieben werden.


**Lösung:**

Anstatt Katalogänderungen direkt in [!DNL Adobe Commerce Optimizer] zu schreiben, verwenden Sie [Katalogebenen](../../optimizer/setup/catalog-layer.md){target="_blank"}, um Änderungen außerhalb von [!DNL Adobe Commerce] anzuwenden. Mit Katalogschichten können externe Systeme Katalogdaten innerhalb von [!DNL Adobe Commerce Optimizer] anreichern oder überschreiben, ohne dass es zu Konflikten mit der Connector-Synchronisierung kommt.

## Fehlerbehebungsszenarien für häufige [!DNL SaaS Data Export]

Informationen zu Problemen im Zusammenhang mit den zugrunde liegenden [!DNL SaaS Data Export], die sich auf den Connector auswirken können, finden Sie [Fehlerbehebung für Szenarien [!DNL SaaS Data Export]](../../data-export/troubleshooting/troubleshooting-scenarios.md).
