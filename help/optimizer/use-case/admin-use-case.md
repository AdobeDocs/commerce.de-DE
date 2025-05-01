---
title: Carvelo-Anwendungsfall
description: Erfahren Sie, wie Sie  [!DNL Adobe Commerce Optimizer]  verwenden, um Ihren Katalog mithilfe von Kanälen und Richtlinien zu verwalten, und wie Sie Ihre Storefront basierend auf Ihrer Katalogkonfiguration einrichten.
hide: true
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d716dd9d75beb642bfad30271b6ecd3490ee7328
workflow-type: tm+mt
source-wordcount: '1656'
ht-degree: 0%

---

# Carvelo-Anwendungsfall

>[!NOTE]
>
>In dieser Dokumentation wird ein Produkt beschrieben, das sich in der Entwicklung für den frühzeitigen Zugriff befindet und nicht alle für die allgemeine Verfügbarkeit vorgesehenen Funktionen enthält.

Der folgende Anwendungsfall zeigt, wie Sie [!DNL Adobe Commerce Optimizer] verwenden können, um Ihren Katalog so zu organisieren, dass er mit Einzelhandelsvorgängen anhand eines einzigen Basiskatalogs abgeglichen wird. Außerdem wird gezeigt, wie eine Storefront mit Edge Delivery Services eingerichtet wird.

## Voraussetzung

Bevor Sie diesen Anwendungsfall durchgehen, stellen Sie sicher, dass Sie [Ihre Storefront eingerichtet haben](../storefront.md).

## Fangen wir an

In diesem Anwendungsbeispiel arbeiten Sie mit Folgendem:

1. [!DNL Adobe Commerce Optimizer]-Benutzeroberfläche : Richten Sie die erforderlichen Kanäle und Richtlinien ein, um die komplexe Einrichtung des Katalogbetriebs zu verwalten.

1. Commerce-Storefront: Rendern Sie die Storefront mit den in [!DNL Adobe Commerce Optimizer] UI und den Commerce-Storefront-Konfigurationsdateien eingerichteten `fstab.yaml` Katalogdaten und `config.json`.

### Das Wichtigste zum Mitnehmen

Am Ende dieses Artikels werden Sie:

- Lernen Sie die Grundlagen der [!DNL Adobe Commerce Optimizer] mit seinem einzigartigen, leistungsstarken und skalierbaren Katalogdatenmodell kennen.
- Erfahren Sie, wie das Katalogdatenmodell nahtlos mit plattformunabhängigen Storefront-Komponenten integriert wird, die von Adobe erstellt wurden.
- Erfahren Sie, wie Sie Adobe Commerce Optimizer-Kanäle und -Richtlinien verwenden, um benutzerdefinierte Katalogansichten und Datenzugriffsfilter zu erstellen und die Daten an eine Adobe Commerce-Storefront mit Edge Delivery zu senden.

## Unternehmen Szenario – Carvelo Automobile

Carvelo Automobile ist ein fiktives Automobilkonglomerat mit einem komplexen operativen Aufbau.

![Carvelo Automobil](../assets/carvelo.png)

In diesem Diagramm sehen Sie, dass Carvelo Automobilprodukte von drei Marken verkauft. Jede Werbetreibender ist eine andere untergeordnete Firma:

- Aurora (Elektrofahrzeuge)
- Schraube (SUVs)
- Cruz (Hybrid)

Es verkauft diese Marken über drei Händler:

- Arkbridge
- Kingsbluff
- Celport

Diese Vertragshändler gehören zwei verschiedenen Muttergesellschaften an:

- West Coast Inc. (Arkbridge)
- East Coast Inc. (Kingsbluff, Celport)

Jedes Unternehmen verfügt über zwei Preisbücher, mit denen Produkte zu einem bestimmten Preis für verschiedene Käufer (Basis, VIP) verkauft werden.

- `west_coast_inc` und `vip_west_coast_inc`
- `east_coast_inc` und `vip_east_coast_inc`

Wie Sie sehen können, ist dies ein sehr komplexer geschäftlicher Anwendungsfall. Mit [!DNL Adobe Commerce Optimizer] kann ein Händler eine komplexe Geschäftsstruktur unterstützen, indem er einen einzigen Basiskatalog verwendet, um Daten ohne Katalogduplizierung zu syndizieren, Preisbücher (30.000 Preisbücher) zu skalieren und all diese Daten an eine Edge Delivery Services-Storefront bereitzustellen.

Jetzt, da Sie einen Überblick über den geschäftlichen Anwendungsfall haben, ist hier Ihr Ziel, während Sie dieses Tutorial durcharbeiten:

>[!BEGINSHADEBOX]

Carvelo will Teile über seine drei Marken (Aurora, Bolt und Cruz) über die verschiedenen Händler (Akbridge, Kingsbluff und Celport) verkaufen. Carvelo möchte sicherstellen, dass die Vertragshändler nur Zugang zu den korrekten Teilen und Preisen gemäß ihren jeweiligen Lizenzvereinbarungen haben.

Letztlich verfolgt Carvelo zwei Hauptziele:

1. Pflegen Sie eine „globale“ Website, die alle SKUs aller drei Marken enthält.
1. Geben Sie Händlern einen Pfad an, um ihre eigenen Storefronts einzurichten, die auf der eindeutigen SKU-Sichtbarkeit und den Preisen für jede SKU für jeden Händler basieren.

>[!ENDSHADEBOX]

Rufen Sie jetzt Ihre [!DNL Adobe Commerce Optimizer] Instanz auf.

## 1. Zugriff auf die [!DNL Adobe Commerce Optimizer]

Nachdem Sie sich für das Early-Access-Programm entschieden haben, sendet Adobe eine E-Mail, in der die URL für den Zugriff auf die für Sie bereitgestellte L[!DNL Adobe Commerce Optimizer]-Instanz angegeben ist. Diese Instanz ist mit allem vorkonfiguriert, was Sie benötigen, um die in diesem Tutorial beschriebenen Schritte erfolgreich durchzuführen, einschließlich Katalogdaten, die den Anwendungsfall Carvelo Automobile unterstützen.

Beim Starten von [!DNL Adobe Commerce Optimizer] wird Folgendes angezeigt:

![[!DNL Adobe Commerce Optimizer] Benutzeroberfläche](../assets/user-interface.png)

>[!NOTE]
>
>Weitere Informationen [ die verschiedenen Teile der [!DNL Adobe Commerce Optimizer]-Benutzeroberfläche finden ](../overview.md) im Artikel „Übersicht“.

Erweitern Sie in der linken Navigation den Abschnitt **[!UICONTROL Catalog]** und klicken Sie auf **[!UICONTROL Channels]**. Beachten Sie, dass die Arkbridge- und Kingsbluff-Händler bereits Kanäle erstellt haben:

![Vorkonfigurierte Kanäle](../assets/existing-channels-list.png)

>[!NOTE]
>
>Sie können den Kanal **Global** vorerst ignorieren.

Klicken Sie auf das Infosymbol, um die Kanaldetails anzuzeigen.

Arkbridge verfügt über die folgenden Richtlinien:

- Marke
- Modell
- Marken von West Coast Inc
- Arkbridge-Teilekategorien

Kingsbluff hat die folgenden Richtlinien:

- Marke
- Modell
- Marken von East Coast Inc
- Kingsbluff-Teilekategorien

Im nächsten Abschnitt erstellen Sie einen Kanal und Richtlinien für den Celport-Händler.

## 2. Erstellen einer Richtlinie und eines Kanals

Carvelos E-Commerce-Manager muss eine neue Storefront für einen Händler namens *Celport* einrichten, der zum Unternehmen *East Coast Inc* gehört. Celport wird Bremsen und Federungen für die Marken Bolt und Cruz verkaufen.

![Celport-](../assets/celport-dealer.png)

Mit [!DNL Adobe Commerce Optimizer] wird der Commerce Manager:

1. Erstellen Sie eine neue Richtlinie mit dem Namen *Celport-Teilekategorien*, damit Celport nur Brems- und Federungsteile verkaufen kann.
1. Erstellen Sie einen neuen Kanal für die Celport-Storefront.

   Dieser Kanal verwendet Ihre neu erstellte Richtlinie *Celport-Teilekategorien* und die vorhandenen *East Coast Inc Brands*, um sicherzustellen, dass Celport nur die Marken Bolt und Cruz als Teil der Vereinbarung mit East Coast Inc. verkaufen kann. Der Celport-Kanal verwendet das `east_coast_inc` Preisbuch, um Produktpreispläne zu unterstützen, die mit den Lizenzvereinbarungen für Marken übereinstimmen.
1. Aktualisieren Sie die Commerce-Storefront-Konfiguration, um Daten aus dem von Ihnen erstellten Celport-Kanal zu verwenden.

Am Ende dieses Abschnitts wird Celport einsatzbereit sein, um die Produkte von Carvelo zu verkaufen.

### Erstellen einer Richtlinie

Erstellen wir eine neue Richtlinie mit dem Namen *Celport-Teilekategorien* um die SKUs zu filtern, die der Celport-Händler verkauft und die Brems- und Federungsteile enthalten.

1. Erweitern Sie in der linken Navigation den Abschnitt **[!UICONTROL Catalog]** und klicken Sie auf **[!UICONTROL Policies]**.

1. Klicken Sie auf **[!UICONTROL Add Policy]**.

   Es wird eine neue Seite angezeigt, auf der Sie die Richtliniendetails hinzufügen können.

1. Fügen Sie die erforderlichen Details hinzu:

   **Name** = *Celport-Teilekategorien*

1. Klicken Sie auf **[!UICONTROL Add Filter]**.

   Ein Dialogfeld wird zum Hinzufügen von Filterdetails angezeigt.

1. Fügen Sie die Filterdetails hinzu:

   - **Attribut** = *part_category*
   - **Operator** = **IN**
   - **Wert Source** = **STATIC**
   - **Wert** = *Bremsen*, *Aufhängung*

   >[!IMPORTANT]
   >
   >Stellen Sie sicher, dass der angegebene Attributname genau mit dem SKU-Attributnamen im Katalog übereinstimmt.

   Weitere Informationen über den Unterschied zwischen einer STATIC- und einer TRIGGER-Wertquelle finden Sie unter [Quelltypen von Werten](../catalog/policies.md#value-source-types).

1. Klicken Sie im Dialogfeld **[!UICONTROL Filter details]** auf **[!UICONTROL Save]**.

1. Um den soeben erstellten Filter zu aktivieren, klicken Sie auf die Aktionspunkte (…) und wählen Sie **Aktivieren**.

1. Klicken Sie auf **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Wenn die Schaltfläche **[!UICONTROL Save]** nicht aktiv (blau) ist, fehlt möglicherweise der Richtlinienname. Klicken Sie auf das Stiftsymbol neben *Neue Richtlinie*, um sie hinzuzufügen.

1. Gehen Sie zurück zur Liste der Richtlinien, indem Sie auf den Rückwärtspfeil klicken.

   Die neue *Celport-*&quot; wird in der Liste angezeigt.

### Erstellen eines Kanals

Erstellen Sie einen neuen Kanal für den *Celport*-Händler und verknüpfen Sie die folgenden Richtlinien: *East Coast Inc Marken* und *Celport-*.

1. Erweitern Sie in der linken Navigation den Abschnitt **[!UICONTROL Catalog]** und klicken Sie auf **[!UICONTROL Channels]**.

   ![Kanäle](../assets/channels.png)

   Beachten Sie die vorhandenen Kanäle: *Arkbridge*, *Kingsbluff* und *Global*.

   ![Seite „Vorhandene Kanäle“](../assets/existing-channels-list.png)

1. Klicken Sie auf **[!UICONTROL Add Channel]**.

1. Kanaldetails ausfüllen:

   - **name** = *Celport*
   - **Scopes** = *en-US* (Eingabe drücken)
   - **Richtlinien** (Dropdown verwenden) = *East Coast Inc Brands*; *Celport-Teilekategorien*; *Marke*; *Modell*                          

1. Klicken Sie auf **[!UICONTROL Add]** , um den Kanal zu erstellen.

   Die Seite Kanäle wird aktualisiert, um den neuen Kanal anzuzeigen.

   ![Aktualisierte Kanalliste](../assets/updated-channels-list.png)

   >[!NOTE]
   >
   >Wenn die Schaltfläche **[!UICONTROL Add]** nicht blau ist, stellen Sie sicher, dass der Bereich ausgewählt ist, indem Sie den Cursor in den **[!UICONTROL Scopes]** Abschnitt platzieren und die **Eingabetaste** drücken.

1. Rufen Sie die Celport-Kanal-ID ab.

   Klicken Sie auf das Informationssymbol für den Celport-Kanal auf der Seite **Kanäle**.

   ![Celport-Kanal-ID](../assets/celport-channel-id.png)

   Kopieren Sie die Kanal-ID und speichern Sie sie. Sie benötigen diese ID, wenn Sie die Storefront-Konfiguration aktualisieren, um Daten an Ihren neuen Celport-Katalog zu senden.

Nachdem Sie den Celport-Kanal und die zugehörigen Richtlinien erstellt haben, besteht der nächste Schritt darin, die Storefront so zu konfigurieren, dass Ihr neuer Celport-Katalog erstellt wird.

## 3. Aktualisieren der Storefront

Der letzte Teil dieses Tutorials beinhaltet die Aktualisierung der Storefront, die [Sie bereits erstellt haben](#prerequisite) um Daten an den neuen Celport-Katalog zu liefern. In diesem Abschnitt ersetzen Sie die Kanal-ID in Ihrer Storefront-Konfigurationsdatei durch die Kanal-ID für Celport.

1. Öffnen Sie in Ihrer lokalen Entwicklungsumgebung den Ordner, in den Sie das GitHub-Repository geklont haben, mit Ihren Textbausteinkonfigurationsdateien für die Storefront.

1. Öffnen Sie im Stammverzeichnis des Ordners die `config.json`.

   +++config.json-Code

   ```json
   {
    "public": {
      "default": {
      "commerce-core-endpoint": "https://www.aemshop.net/graphql",
      "commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/Fwus6kdpvYCmeEdcCX7PZg/graphql",
      "headers": {
         "cs": {
            "ac-channel-id": "9ced53d7-35a6-40c5-830e-8288c00985ad",
            "ac-environment-id": "Fwus6kdpvYCmeEdcCX7PZg",
            "ac-price-book-id": "west_coast_inc",
            "ac-scope-locale": "en-US"
           }
         },
         "analytics": {
            "base-currency-code": "USD",
            "environment": "Production",
            "store-id": 1,
            "store-name": "ACO Demo",
            "store-url": "https://www.aemshop.net",
            "store-view-id": 1,
            "store-view-name": "Default Store View",
            "website-id": 1,
            "website-name": "Main Website"
          }
       }
      }
   }
   ```

   Beachten Sie, dass die Kopfzeile des Kanals die folgenden Zeilen enthält:

   - `ac-channel-id`:`"9ced53d7-35a6-40c5-830e-8288c00985ad"`
   - `ac-environment-id`: `"Fwus6kdpvYCmeEdcCX7PZg"`
   - `ac-price-book-id`: `"west_coast_inc"`

+++

1. Ersetzen Sie den `ac-channel-id` Wert durch die Celport-Kanal-ID, die Sie zuvor kopiert haben.
1. Ersetzen Sie bei Bedarf den `ac-environment-id` durch die Mandanten-ID für Ihre [!DNL Adobe Commerce Optimizer]. Sie finden die ID in der Onboarding-E-Mail für das Early-Access-Programm oder indem Sie sich an Ihren Adobe-Kundenbetreuer wenden.

   Stellen Sie sicher, dass der `commerce-endpoint` dem GraphQL-Endpunkt für Ihre [!DNL Adobe Commerce Optimizer]-Instanz entspricht.

1. Ersetzen Sie den `ac-price-book-id` durch `"east_coast_inc"`.
1. Speichern Sie die Datei.

Wenn Sie die Änderungen speichern, aktualisieren Sie die Katalogkonfiguration, um den Carvelo-Kanal zu verwenden, der so konfiguriert wurde, dass er nur Brems- und Federungsteile verkauft.

1. Launch die Storefront, um den Celport-spezifischen Katalog Erlebnis zu Ansicht, der von Ihrer Storefront-Konfiguration erstellt wurde.

   1. Im Terminalfenster in Ihrer IDE Beginn Sie Ihre lokale Storefront-Vorschau.

      ```shell
      npm start
      ```

   Der Browser öffnet sich für die lokale Entwicklung Vorschau unter `http://localhost:3000`.

   Wenn der Befehl fehlschlägt oder sich der Browser nicht öffnet, lesen Sie die [Anweisungen für die lokale Entwicklung](../storefront.md) im Thema „Storefront-Setup“.

   1. Suchen Sie im Browser nach `brakes` und drücken Sie die **Eingabetaste**.

      Die Storefront wird aktualisiert, um die Produktlistenseite mit den Bremsteilen anzuzeigen.

   ![Bremsen Produktliste Seite](../assets/brakes-listing-page.png)

   Klicken Sie auf ein Bremsteilbild, um die Produktdetails mit Preisinformationen zu Ansicht und notieren Sie sich die Produktpreisinformationen.

1. Jetzt suchen für `tires`, was ein weiterer Teil Kategorie ist, der in den Anwendungsfalldaten auf Ihrem [!DNL Adobe Commerce Optimizer] Instanz verfügbar ist.

   ![Storefront-Konfiguration mit falschen Kopfzeilen](../assets/storefront-configuration-with-incorrect-headers.png)

   Beachten Sie, dass hier keine Ergebnisse zurückgegeben werden. Der Grund dafür ist, dass der Celport-Kanal so konfiguriert wurde, dass er nur Brems- und Federungsteile verkauft.

1. Experimentieren Sie mit der Aktualisierung Ihrer Storefront-Konfigurationsdatei (`config.json`).

   1. Ändern Sie die `ac-channel-id`- und `ac-price-book`.

      Sie können beispielsweise die Kanal-ID in den Kingsbluff-Kanal und die Preisbuch-ID in `east_coast_inc` ändern. Sie können die für Kingsbluff verfügbaren Teilekategorien sehen, indem Sie die Richtlinie *Kingsbluff-*) lesen.

   1. Speichern Sie die Datei.

      Wenn Sie die Datei speichern, wird die Vorschau der lokalen Storefront automatisch aktualisiert.

   1. Zeigen Sie eine Vorschau der Änderungen im Browser an, indem Sie die Suchfunktion verwenden, um Reifenteile zu finden .

      Beachten Sie die verschiedenen verfügbaren Teiletypen und beachten Sie die Preise, die dem Kingsbluff-Kanal zugewiesen sind.

      Indem Sie die Kopfzeilenwerte in der Konfigurationsdatei der Storefront ändern und die aktualisierte Storefront untersuchen, können Sie sehen, wie einfach es ist, die Katalogansicht und die Datenfilter zu aktualisieren, um das Storefront-Erlebnis anzupassen.

## Das war&#39;s!

In diesem Tutorial haben Sie erfahren, wie [!DNL Adobe Commerce Optimizer] Ihnen dabei helfen können, Ihren Katalog so zu organisieren, dass er mit Ihrem Einzelhandelsgeschäft übereinstimmt, indem er einen einzigen Basiskatalog verwendet. Sie haben auch gelernt, wie Sie eine Storefront mit Edge Delivery Services einrichten.

## Was Sie jetzt tun können

Informationen dazu, wie Sie die Produktsuche und Recommendations nutzen können, um die Shopping-Erlebnis für Ihre Kunden zu personalisieren, finden Sie in der [Merchandising](../merchandising/overview.md) Übersicht.
