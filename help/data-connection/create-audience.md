---
title: Erstellen einer Zielgruppe in Real-Time CDP mithilfe  [!DNL Commerce]  Ereignisdaten
description: Erfahren Sie, wie Sie  [!DNL Commerce] -Ereignisdaten verwenden, um eine Zielgruppe in Real-Time CDP zu erstellen
role: Admin, Developer
feature: Personalization, Integration
exl-id: 0e9d286b-c459-44db-bbf8-2cb46e21739d
source-git-commit: a3e19940e2a3d8a240bb17703cfdd9903df311aa
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---

# Erstellen von Zielgruppen in Real-Time CDP mithilfe [!DNL Commerce] Ereignisdaten

Verwenden Sie Ereignisdaten, die aus Ihrem [!DNL Commerce] erfasst werden, um Zielgruppen in Real-Time CDP zu erstellen. Die erfassten Daten basieren auf dem Browser-Verhalten, früheren Käufen, Profilattributen, Konversions- oder Abwanderungsneigungen, dem Treuestatus, einem hohen und niedrigen Kundenwert und mehr.

## Welche Daten sollte ich verwenden?

Erstellen Sie Zielgruppen in Real-Time CDP mithilfe von Daten aus Storefront-, Back-Office- und Profilereignissen.

| Datentypen | Storefront-Daten (Verhaltensereignisse) | Back-Office-Daten (Server-seitige Ereignisse) | Kundenprofil- und Segmentdaten |
|---|---|---|---|
| **Definition** | Klicks oder Aktionen, die Kunden auf Ihrer Site durchführen. | Informationen über den Lebenszyklus und Details jeder Bestellung (vergangene und aktuelle). | Wer sind Ihre Kunden und für welche Segmente sind sie qualifiziert? |
| **Von Adobe Commerce erfasste Ereignisse** | `productPageView`<br>`addToCart` | `placeOrder`<br>`orderplaced`<br>`orderLineItemRefunded`<br>`order Canceled`<br>`order history` | `createAccount`<br>`editAccount`<br>`Profile Record` |

## Was haben andere Kunden erreicht?

Adobe [!DNL Commerce]-Kunden haben durch die Aktivierung von in Real-Time CDP erstellten Zielgruppen und deren Bereitstellung in ihrer [!DNL Commerce]-Instanz erhebliche geschäftliche Vorteile erzielt.

Ein globales, markenübergreifendes Bekleidungsgeschäft mit retailer:

- Eine Quelle der Wahrheit mit 10 Millionen von einheitlichen Kundenprofilen
- Es wurden mehr als 40 einzigartige Zielgruppen von „Kunden mit hohen Absichten“ erstellt, um kanalübergreifend zu interagieren

Ein globales Getränkeunternehmen sammelte:

- 98 Millionen Kundenprofile aus über 100 Ländern

## Fangen wir an

In diesem Artikel erfahren Sie, wie Sie:

- Erstellen Sie eine Zielgruppe in Real-Time CDP basierend auf den [!DNL Commerce], die die Ereignisse erfassen
- Aktivieren dieser Zielgruppe für Ihren [!DNL Commerce] Store
- Verwenden Sie die Zielgruppe in [!DNL Commerce], um eine Warenkorb-Preisregel zu informieren

>[!IMPORTANT]
>
>Führen Sie die in diesem Artikel beschriebenen Aufgaben mithilfe Ihrer [!DNL Commerce] Sandbox-Umgebung aus. Dadurch wird sichergestellt, dass die an Experience Platform gesendeten Storefront- und Backoffice-Ereignisdaten Ihre Produktionsereignisdaten nicht verwässern.

### Voraussetzungen

Bevor Sie beginnen, stellen Sie Folgendes sicher:

- Sie haben die Berechtigung zur Verwendung von Real-Time CDP. Wenn Sie sich nicht sicher sind, wenden Sie sich an Ihren Systemintegrator oder das Entwicklungs-Team, das Projekte und Umgebungen verwaltet.
- Sie [ die ](install.md)-Erweiterung in [&#128279;](connect-data.md) und [!DNL Data Connection] [!DNL Commerce] konfiguriert.
- Sie [bestätigt](connect-data.md#confirm-that-event-data-is-collected) dass Ihre [!DNL Commerce] Ereignisdaten am Experience Platform Edge eintreffen.

### &#x200B;1. Erstellen einer Zielgruppe

Eine Zielgruppe ist eine Gruppe von Kundinnen und Kunden, die ein ähnliches Verhalten oder ähnliche Merkmale aufweisen. In dieser Übung erstellen Sie eine Zielgruppe, die Personen qualifiziert, die sich für ein bestimmtes Produkt aus Ihrem Geschäft interessieren.

Um diese Übung zu vereinfachen, verwenden Sie Ereignisdaten aus dem `productPageView`. Dieses Ereignis erfasst Details zum angezeigten Produkt, z. B. Produktname, SKU, Preis usw.

Verwenden Sie diese Ereignisdaten, um anzugeben, dass die Zielgruppe Personen umfasst, die mindestens ein Ereignis vom Typ „Produktansichten“ haben, bei dem die SKU (Produktkennung) einem bestimmten Produkt auf Ihrer Site entspricht und das Ereignis innerhalb des letzten Tages auftritt. &#x200B;

1. Öffnen Sie Experience Platform und wählen Sie **[!UICONTROL Audiences]** aus dem linken Navigationsmenü aus.

   ![Zielgruppen-Dashboard](assets/audience-left-rail.png)

1. Klicken Sie auf **[!UICONTROL Create Audience]**.

   ![Zielgruppe erstellen](assets/browse-create-audience.png)

   Der **Segment Builder**-Arbeitsbereich wird angezeigt.

1. Wählen **Arbeitsbereich „Segment**&quot; die Erstellungsmethode **Regel erstellen** aus.

   ![Regel erstellen](assets/build-rule.png)

   Im **Segment Builder**-Arbeitsbereich definieren Sie die Regeln und Bedingungen für Ihre Zielgruppe&#x200B; Diese Regeln und Bedingungen basieren auf Ereignis- und Profildaten aus Ihrem Commerce Store und definieren die Kriterien, die bestimmen, ob eine Benutzerin oder ein Benutzer für die Zielgruppe geeignet ist. Sie können beispielsweise eine Regel erstellen, die Benutzer enthält, die ein bestimmtes Produkt angesehen haben, oder Benutzer, die innerhalb eines bestimmten Zeitraums einen Kauf getätigt haben. Weitere Informationen zu [Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) und Regeln und Bedingungen.

1. Wählen Sie die [Ereignisse](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) aus.

   ![Registerkarte „Ereignisse“](assets/audience-events-tab.png)

1. Suchen Sie nach dem Ereignistyp „Produktansichten“. Ziehen Sie sie dann per Drag-and-Drop in den **Segment Builder**-Arbeitsbereich.

1. Kehren Sie zur Registerkarte **Ereignisse** zurück und suchen Sie nach „SKU“, dem Datenfeld unter dem `productListItems`. Ziehen Sie sie in den **Segment Builder**-Arbeitsbereich oben auf dem Ereignis **Produktansicht**.

   Der **Ereignisregeln** wird angezeigt, in dem Sie das spezifische Produkt angeben können, aus dem Sie Ihre Zielgruppe erstellen möchten.

   ![SKU auswählen](assets/audience-addsku.png)

1. Legen Sie das Zeitintervall auf einen Tag fest, indem Sie auf **Beliebige Zeit** klicken und *Letzte* mit dem Wert *1*.

   Beim Erstellen einer Zielgruppe können Sie ein Zeitintervall angeben, in dem die letzte Aktivität erfasst wird. Durch das Festlegen eines Zeitintervalls können Sie Benutzende auf der Grundlage ihrer letzten Interaktionen oder Verhaltensweisen innerhalb eines bestimmten Zeitraums ansprechen.

1. Legen **im Bereich** Zielgruppeneigenschaften“ auf der rechten Seite des Arbeitsbereichs die Zielgruppeneigenschaften fest, indem Sie einen Namen, eine Beschreibung und eine Auswertungsmethode für die Zielgruppe angeben.

1. Um die Zielgruppe zu speichern, klicken Sie auf **[!UICONTROL Save and Close]**.

   Die Details Ihrer Audience werden im Dashboard **Audience** angezeigt.

### &#x200B;2. Aktivieren Sie die Zielgruppe für das [!DNL Commerce]

Sie stellen eine Zielgruppe in [!DNL Commerce] zur Verfügung, indem Sie sie für das [!DNL Commerce] aktivieren.

>[!IMPORTANT]
>
>Wenn Sie [!DNL Commerce] noch nicht als verfügbares Ziel für den Datenempfang festgelegt haben, lesen Sie den Abschnitt [Adobe [!DNL Commerce] Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce).

1. Klicken **auf der Registerkarte** Details“ Ihrer Zielgruppe auf **Für Ziel aktivieren**.

1. Wählen Sie Ihr [!DNL Commerce] aus. Klicken Sie dann auf **Weiter**.

1. Schließen Sie den Aktivierungsvorgang ab, indem Sie auf **[!UICONTROL Finish]** klicken.

## &#x200B;3. Anzeigen der Zielgruppe im Zielgruppen-Dashboard

In [!DNL Commerce] können Sie alle &quot;[&quot; Zielgruppen anzeigen](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) die mithilfe des Dashboards [!DNL Commerce]Real-Time CDP-Zielgruppen **für Ihre** personalisiert werden können.

Um auf das Dashboard **Real-Time CDP** Zielgruppen zuzugreifen, gehen Sie zur Seitenleiste _Admin_ und dann zu **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

Suchen Sie im Dashboard nach der von Ihnen erstellten Zielgruppe. Beachten Sie, dass es in einer Warenkorb-Preisregel oder einem dynamischen Block nicht verwendet wird. Im nächsten Abschnitt verknüpfen Sie die Zielgruppe mit einer Warenkorb-Preisregel.

![Real-Time CDP-Zielgruppen-Dashboard](assets/real-time-cdp-dashboard.png)

### &#x200B;4. Erstellen Sie eine Warenkorb-Preisregel basierend auf der Zielgruppe

In diesem Abschnitt erfahren Sie, wie Sie eine Warenkorb-Preisregel basierend auf Ihrer neuen Zielgruppe erstellen.

1. Vergewissern Sie sich, dass Ihre neue Zielgruppe im Dashboard **Real-Time CDP-Zielgruppen** angezeigt wird.
1. [Erstellen einer Warenkorb-Preisregel](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [Legen Sie die Bedingung ](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) Warenkorb-Preisregel mithilfe Ihrer neuen Zielgruppe fest.
1. [Legen Sie die Aktion ](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions), die beim Hinzufügen des Produkts zum Warenkorb ausgeführt werden soll.
1. Fahren Sie mit der Konfiguration Ihrer Warenkorb-Preisregel fort.
1. Navigieren Sie zur Kundenansicht Ihrer Sandbox-Instanz.
1. Fügen Sie das Produkt, das Sie basierend auf der Zielgruppe von erstellt haben, zum Warenkorb hinzu. Beachten Sie, dass die Warenkorb-Preisregel aktiviert ist.

## einpacken

In dieser Übung haben Sie eine Zielgruppe in Real-Time CDP erstellt und für das [!DNL Commerce] aktiviert. Anschließend haben Sie in der [!DNL Commerce] eine auf dieser Zielgruppe basierende Warenkorbpreisregel erstellt und die Regel in Ihrer Sandbox-Umgebung aktiviert.
