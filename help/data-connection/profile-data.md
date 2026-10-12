---
title: Aktualisieren des Profildatensatzschemas für die Commerce-Datenaufnahme
description: Erfahren Sie, wie Sie ein Schema, einen Datensatz und einen Datenstrom erstellen, um Commerce-Profildatensatzdaten zu erfassen und an Experience Platform zu senden.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 25741837-f423-4204-8520-80b7cd9d44bd
TQID: 'https://experienceleague.adobe.com/I8bptw1tNdzXfCC6hFtn7fuz-BIiALXG4g6lLhga6ec'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%
---
# Aktualisieren des Profildatensatzschemas für die Commerce-Datenaufnahme

Wenn Ihre Kunden ein Profil auf Ihrer Commerce-Site erstellen, wird ein Profildatensatz erstellt und die Daten werden erfasst. Sie müssen ein Schema und einen Datensatz speziell für diesen Profildatensatz erstellen, bevor Sie diese Profildaten an die Experience Platform streamen können.

1. [Erstellen](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/ui/resources/schemas) eines Schemas und Festlegen der Klasse auf **Individuelles Profil**.

1. [Hinzufügen](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/ui/resources/schemas) die folgenden profilspezifischen Feldergruppen:

   - identityMap
   - Demografische Details
   - Persönliche Kontaktdaten
   - Details zum Benutzerkonto

1. [Aktivieren](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/ui/resources/schemas) Sie das Schema für das Profil.

   Wenn ein Schema für das Profil aktiviert ist, werden alle Datensätze, die aus diesem Schema erstellt werden, in Real-Time CDP einbezogen, wobei Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht jedes Kunden zu erstellen.

1. [Erstellen eines Datensatzes](https://experienceleague.adobe.com/de/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform) basierend auf dem von Ihnen erstellten oder aktualisierten Schema.

   Ein Datensatz ist ein Konstrukt zur Datenspeicherung und -verwaltung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. Erstellen Sie [&#x200B; Experience Platform einen &#x200B;](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces#create-namespaces)benutzerdefinierten Namespace“ mit den folgenden Werten:

   - **Anzeigename**: _Commerce-Kunden-ID_
   - **Identitätssymbol**: _CustomerId_
   - **Type**: _Individuelle geräteübergreifende ID_

   ![Benutzerdefinierten Namespace erstellen](assets/custom-namespace.png){width="700" zoomable="yes"}

   Klicken Sie auf **[!UICONTROL Create]**. Der Service für einheitliche Profile verwendet einen benutzerdefinierten Namespace zum Zusammenfügen von Profilfragmenten.

Wenn das Schema, der Datensatz und der benutzerdefinierte Namespace für Kundenprofildatensatzdaten konfiguriert sind, können Sie Ihre Commerce[Instanz so konfigurieren](connect-data.md#data-collection) dass diese Daten erfasst und an Experience Platform gesendet werden.

Informationen zum Erstellen eines Schemas, Datensatzes und Datenstroms für Verhaltens- und Backoffice-Ereignisdaten finden Sie unter [Aktualisieren von Zeitreihen-Ereignisschemas für die Commerce-Datenaufnahme](update-xdm.md).
