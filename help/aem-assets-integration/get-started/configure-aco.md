---
title: Konfigurieren von AEM Assets für Commerce Optimizer
description: Erfahren Sie, wie Sie die AEM Assets-Integration für  [!DNL Adobe Commerce Optimizer] konfigurieren.
feature: CMS, Media, Configuration, Integration
source-git-commit: 0c2e50338cbf286704239b6d1f628180e85a3bef
workflow-type: tm+mt
source-wordcount: '1244'
ht-degree: 0%

---


# Konfigurieren von AEM Assets für [!DNL Adobe Commerce Optimizer]

[!BADGE nur SaaS]{type=Positive tooltip="Gilt nur für Adobe Commerce Optimizer-Projekte."}

Die AEM Assets Integration for [!DNL Adobe Commerce Optimizer] ermöglicht Händlern die Verwendung von AEM Assets als zentralisierte Digital Asset Management-Lösung für Produktbilder. In diesem Handbuch wird die für [!DNL Commerce Optimizer] spezifische Konfiguration beschrieben.

Die folgende Abbildung zeigt einen Überblick über die Produktsynchronisierung zwischen [!DNL Adobe Commerce Optimizer] und der AEM Assets-Integration.

![Fluss von AEM Assets zu [!DNL Commerce Optimizer]](../assets/aco-asset-sync-architecture.png){width="700"}

Diese Integration verfügt über zwei unabhängige Ereignisflüsse. Beide verwenden [Adobe I/O Events](https://developer.adobe.com/events/docs/) zum Übertragen von Ereignissen an den Assets Integration Service, aber jede Richtung verwendet einen eigenen Ereignisanbieter:

* **Von AEM Assets an den Assets-Integrationsdienst**: Wenn ein Asset genehmigt, abgelehnt oder entfernt wird, wird das Ereignis an den Assets-Integrationsdienst gesendet. Der Service ordnet Assets mithilfe von `match-by-SKU` (Metadatengesteuert) oder einem [benutzerdefinierten Matcher (App Builder) Produkten zu &#x200B;](../synchronize/custom-match.md){target=_blank} sendet dann die `product-asset` Zuordnungen an [!DNL Commerce Optimizer], wo sie als Produktebenen gespeichert werden.

  >[!NOTE]
  >
  >Die von der Integration verwendete `AEM-Assets` Katalogebene wird beim Onboarding automatisch erstellt. Sie müssen sie nicht zuvor erstellen. Hintergrundinformationen zur Funktionsweise von Katalogebenen und zum Verhalten der AEM-Assets-Ebene finden Sie unter [AEM-Assets-Ebene](../../optimizer/setup/catalog-layer.md#aem-assets-layer).

* **Vom [!DNL Adobe Commerce Optimizer] zum Assets Integration Service**: Wenn ein Produkt in [!DNL Commerce Optimizer] aktualisiert wird, wird das Ereignis an den Assets Integration Service gesendet. Der Service synchronisiert alle übereinstimmenden Asset-Zuordnungen zurück mit [!DNL Commerce Optimizer].

## Einschränkungen

Die [!DNL Commerce Optimizer]-Integration hat die folgenden Einschränkungen:

### Layer-bezogene Einschränkungen

* Verwenden Sie eine dedizierte Ebene für AEM Assets-Inhalte.

  Payloads, die von AEM Assets gesendet werden, befüllen eine Commerce Optimizer-Katalogschicht. Werte in dieser Ebene überschreiben die Basisattribute des Katalogs, in dem Felder bereitgestellt werden. Wenn die Integration ein Feld in der Payload auslässt, können die entsprechenden Werte in dieser Ebene mit leeren Werten überschrieben werden. Die Freigabe einer Ebene für nicht verwandte Commerce-Workflows - oder die Wiederverwendung einer Ebene, die bereits nicht von AEM stammende Produktdaten speichert - kann **unbeabsichtigten Datenverlust** oder verwirrende Überschreibungen verursachen. Reservieren Sie den Ebenennamen (z. B. den **`AEM-Assets`**) hauptsächlich für die AEM-gesteuerte Produktbildsynchronisierung.

* Die Integration unterstützt eine Katalogquelle pro Mandant: ein einzelnes Gebietsschema und eine benannte Ebene. Die Konfiguration mehrerer AEM-Assets-Ebenen oder mehrerer Gebietsschemata für denselben Mandanten wird derzeit nicht unterstützt.

* Die Wiederverwendung einer vorhandenen Ebene oder die Freigabe einer Ebene mit nicht zugehörigen Workflows ist häufig eine Ursache für vermeidbare Support-Fälle.

### Sonstige Einschränkungen

* **Nur Bilder**: Die Integration unterstützt derzeit keine Video- oder anderen Medientypen.
* **Keine Kategoriebilder**: Die Synchronisierung von Kategoriebildern ist nicht verfügbar. Kategoriebilder von AEM Assets für den Assets-Selektor (Einfügen in die Benutzeroberfläche) werden nicht unterstützt.
* **Keine Unterscheidung zwischen mehreren Sites**: Die Integration verarbeitet keine Website-übergreifenden. Ein mit einem Produkt verknüpftes Bild wird über alle Kanäle und Richtlinien hinweg gleich angezeigt.
* **Bildposition / -reihenfolge**: Bildposition und -reihenfolge werden nicht unterstützt.
* **Produkt muss vorhanden**: Wenn das Produkt nicht in [!DNL Commerce Optimizer] vorhanden ist, wird die Ebene für diese Produkt-Asset-Zuordnung nicht erstellt.

## Voraussetzungen

Stellen Sie vor dem Konfigurieren der Integration Folgendes sicher:

* Eine aktive [!DNL Adobe Commerce Optimizer] mit der Berechtigung **Produktvisualisierungen** (bündelt Dynamic Media mit OpenAPI-Funktionen + [AEM Assets Prime](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-prime)) oder eine vom Kunden bereitgestellte AEM Assets-Lizenz (z. B. **AEM Assets Ultimate**) mit aktivierter Dynamic Media-Funktion.
* Zugriff auf eine AEM Assets as a Cloud Service-Umgebung.
* Sowohl [!DNL Commerce Optimizer] als auch AEM Assets in derselben Adobe IMS-Organisation.
* Dynamic Media mit aktivierter OpenAPI in Ihrer AEM Assets-Umgebung (die Aktivierungsschritte finden [&#x200B; unter „Konfigurieren &#x200B;](configure-aem.md#prerequisites) AEM Assets-Projekts„).

### AEM Assets zuerst konfigurieren

Um die Integration zu unterstützen, konfigurieren Sie das AEM Assets-Projekt und die Umgebungen, bevor Sie mit dem Onboarding der AEM Assets-Integration mit [!DNL Commerce Optimizer] beginnen. Dazu gehört die Aktivierung von Dynamic Media mit OpenAPI-Funktionen und die Bereitstellung der Commerce-Metadatenschemata, -Ereignisse und der Benutzeroberfläche in Ihrem AEM-Projekt.

* [!BADGE Empfohlen]{type=Positive} Aktivieren Sie in der Version `2026.5.26309` und höher von AEM die Integration von Cloud Manager ohne Code-Bereitstellung. Folgen Sie [Aktivieren der Commerce-Integration (Self-Service)](configure-aem.md#enable-aem-commerce-self-service).

* Stellen Sie das `assets-commerce`-Paket in früheren AEM-Versionen manuell bereit.
Folgen Sie [Installieren Sie das Paket assets-commerce manuell](configure-aem.md#install-the-assets-commerce-package-manually).

>[!TIP]
>
> Sie können die aktuelle AEM-Version über das Menü oben rechts überprüfen: **[!UICONTROL Help]** > **[!UICONTROL About AEM]**.

## Onboarding

>[!IMPORTANT]
>
>Bevor Sie ein Support-Ticket zur Aktivierung der Integration mit [!DNL Commerce Optimizer] senden, schließen Sie den Prozess zum [&#x200B; von AEM Assets &#x200B;](#configure-aem-assets-first). Für die Unterstützung müssen die AEM Assets-Umgebungen und das -Projekt so konfiguriert sein, dass sie die AEM Commerce-Integration unterstützen, einschließlich der Bereitstellung des `assets-commerce` (oder Self-Service-Äquivalents) für Metadaten und Ereignisse. Das Öffnen eines Tickets vor der Konfiguration von AEM kann die Einführung verzögern.

Um die AEM Assets-Integration mit [!DNL Commerce Optimizer] zu integrieren, muss der Adobe-Support Ihre Adobe Commerce Optimizer-Instanz beim Assets Integration Service registrieren und sie abonnieren:

* AEM Assets-Ereignisse (Asset genehmigt, aktualisiert, entfernt)
* [!DNL Commerce Optimizer] Katalogereignisse (Produkt erstellt, aktualisiert)

Um diesen Prozess einzuleiten, erstellen [ein Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) das die folgenden Informationen enthält:

* **[!DNL Adobe Commerce Optimizer]Mandanten-ID** (Instanz-ID) in Ihrer [!DNL Commerce Optimizer]-URL oder in der Benutzeroberfläche von Commerce Cloud Manager.
* **AEM-Programm-ID und Umgebungs** ID, die Sie beim Konfigurieren von [AEM Assets](#configure-aem-assets-first) für die Integration eingerichtet haben.
* **Matching-Regel**: Übereinstimmung nach SKU oder [externer Matcher (App Builder)](../synchronize/custom-match.md){target=_blank}.
* **Layer**: Der Name der Katalogebene, mit der der Mandant registriert werden soll (siehe **Layer-bezogene Einschränkungen**). Geben Sie einen benutzerdefinierten Namen nur an, wenn dies beabsichtigt ist. Andernfalls wird der **`AEM-Assets`** verwendet.
* **Locale**: Das Gebietsschema der Katalogquelle, mit dem der Mandant registriert werden soll (z. B. `en-US`). Dieses Gebietsschema muss mit dem Gebietsschema übereinstimmen, das Sie in Ihrer Katalogansicht und den Produktkatalogdaten verwenden.

### Konfigurieren der Katalogansicht

Nachdem der [!DNL Commerce Optimizer]-Mandant registriert wurde, konfigurieren Sie Ihre Katalogansicht so, dass die Storefront und APIs AEM-gesteuerte Bilddaten enthalten:

* **Quelle des Katalogs (Gebietsschema) auswählen** — Wählen Sie dasselbe Gebietsschema aus, das Sie in Ihrem Support-Ticket angegeben haben (z. B. **`en-US`**). Die Integration registriert ein Gebietsschema pro Mandant. Eine Nichtübereinstimmung verhindert, dass synchronisierte Bilder in der beabsichtigten Katalogansicht angezeigt werden.
* **Katalogebene zuweisen** - Weisen Sie dieser Katalogansicht die **`AEM-Assets`** Ebene (oder Ihren benutzerdefinierten Ebenennamen aus dem Ticket) zu.

Wenn das Gebietsschema oder die Ebene nicht korrekt zugewiesen ist, werden **Bilddaten nicht angezeigt** verhalten sich unerwartet - auch wenn die Synchronisierung im Upstream erfolgreich war.

## Synchronisierung

Nach der Konfiguration synchronisiert die Integration `product-asset` automatisch.

Weitere Informationen finden [&#x200B; unter &#x200B;](../synchronize/custom-match.md)Benutzerdefinierter automatischer Abgleich“.

### Beispiel für Übereinstimmung nach SKU-Workflow

Ein typischer Fluss beim Hinzufügen eines vorhandenen Assets zu einem neuen Produkt:

1. Erstellen Sie das Produkt in [!DNL Commerce Optimizer] (über API oder Datenaufnahme). Das Produkt kann zunächst ohne Bilder vorhanden sein.

1. Öffnen Sie in AEM Assets das Asset, das Sie dem Produkt zuordnen möchten.

1. Fügen Sie die Produkt-SKU zu den **Commerce:skus**-Metadaten hinzu und weisen Sie Bildrollen zu (z. B. `thumbnail`, `image`).

1. Genehmigen Sie das Asset für die Bereitstellung. Dadurch wird das Ereignis Trigger, das der Assets-Integrationsdienst verarbeitet.

1. Der Assets-Integrationsdienst sendet die Produkt-Image-Zuordnung an [!DNL Commerce Optimizer]. Das Produkt in [!DNL Commerce Optimizer] wird mit den Bildern des Assets aktualisiert.

1. Überprüfen Sie, ob das Bild sichtbar ist. Warten Sie einige Minuten, bis die Synchronisierung abgeschlossen ist, und überprüfen Sie dann das Produkt in der [!DNL Commerce Optimizer]-Benutzeroberfläche oder fragen Sie die Storefront-APIs ab, um zu bestätigen, dass das Bild zurückgegeben wird.

## Umgang mit Bildrollen

Wenn ein Produkt mehrere Assets hat, die dieselbe Bildrolle verwenden (z. B. zwei Assets mit der Rolle `thumbnail`), stellt die Integration sicher, dass nur ein Asset diese Rolle behält, um doppelte Rollen in der [!DNL Commerce Optimizer] und unerwartetes Verhalten der Storefront zu vermeiden.

**Verhalten:** Wenn eine Aktualisierung von AEM Assets gesendet wird, erhält das zuletzt aktualisierte Asset die Bildrolle (z. B. `thumbnail`) und die Rolle wird aus dem vorherigen Asset entfernt, in dem sie enthalten war. Dadurch wird verhindert, dass doppelte Bildrollen in der Storefront angezeigt werden.

## Ähnliche Themen

* [Produktvisualisierung](../../optimizer/setup/product-visuals.md)
* [Konfigurieren des AEM Assets-Projekts](configure-aem.md)
* [Benutzerdefinierter automatischer Abgleich](../synchronize/custom-match.md)
* [Übersicht über die AEM Assets-Integration](../overview.md)
