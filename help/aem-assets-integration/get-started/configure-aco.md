---
title: Konfigurieren von AEM Assets für Commerce Optimizer
description: Erfahren Sie, wie Sie die AEM Assets-Integration für  [!DNL Adobe Commerce Optimizer] konfigurieren.
feature: CMS, Media, Configuration, Integration
source-git-commit: 42f0e0cb72c6429eb6f08f1922c4171195a78d2b
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 0%

---


# Konfigurieren von AEM Assets für [!DNL Adobe Commerce Optimizer]

[!BADGE nur SaaS]{type=Positive tooltip="Gilt nur für Adobe Commerce Optimizer-Projekte."}

Die AEM Assets Integration for [!DNL Adobe Commerce Optimizer] ermöglicht Händlern die Verwendung von AEM Assets als zentralisierte Digital Asset Management-Lösung für Produktbilder. In diesem Handbuch wird die für [!DNL Commerce Optimizer] spezifische Konfiguration beschrieben.

Im Gegensatz zu Adobe Commerce (PaaS) oder Adobe Commerce as a Cloud Service (ACCS) verfügt [!DNL Commerce Optimizer] über keine Benutzeroberfläche mit Administratorkonfiguration. Um die Integration zu aktivieren, erstellen Sie ein Support-Ticket mit Ihren [!DNL Adobe Commerce Optimizer]- und AEM Assets-Details. Der Adobe-Support konfiguriert die Integration und registriert Ihren Mandanten beim Assets Integration Service.

**Bereiten Sie AEM Assets vor dem Senden des Tickets vor.** Bei der Mandantenregistrierung wird davon ausgegangen, dass die AEM-Seite für Commerce verwendet werden kann. Ein Beispiel: Nach der Bereitstellung des AEM Commerce `assets-commerce`-Pakets funktionieren Metadaten und Ereignisse wie beschrieben. **Das Öffnen eines Tickets vor der Konfiguration von AEM kann das Onboarding verzögern.**

Die folgende Abbildung zeigt einen Überblick über die Produktsynchronisierung zwischen [!DNL Adobe Commerce Optimizer] und der AEM Assets-Integration.

![Fluss von AEM Assets zu [!DNL Commerce Optimizer]](../assets/aco-asset-sync-architecture.png){width="700"}

Diese Integration umfasst zwei Hauptflüsse:

* **Von AEM Assets**: Wenn ein Asset genehmigt, abgelehnt oder entfernt wird, fließt das Ereignis über die Adobe-Pipeline zum Assets Integration Service. Der Service ordnet Assets Produkten mithilfe von `match-by-SKU` (Metadatengesteuert) oder einem [benutzerdefinierten Matcher (App Builder) zu &#x200B;](../synchronize/custom-match.md){target=_blank} sendet dann die `product-asset` Zuordnungen an die Commerce Optimizer, wo sie als Produktebenen gespeichert werden.

* **Von[!DNL Adobe Commerce Optimizer]**: Wenn ein Produkt in [!DNL Commerce Optimizer] aktualisiert wird, fließt das Ereignis über die Adobe-Pipeline zum Assets Integration Service. Der Service synchronisiert alle übereinstimmenden Asset-Zuordnungen zurück mit der [!DNL Adobe Commerce Optimizer].

## Voraussetzungen

Stellen Sie vor dem Konfigurieren der Integration Folgendes sicher:

* Eine aktive [!DNL Adobe Commerce Optimizer] mit Berechtigung für Produktvisualisierungen oder eine beliebige AEM Assets-Lizenz mit Dynamic Media.
* Zugriff auf eine AEM Assets as a Cloud Service-Umgebung.
* Sowohl [!DNL Commerce Optimizer] als auch AEM Assets in derselben Adobe IMS-Organisation.
* Dynamic Media mit aktivierter OpenAPI in Ihrer AEM Assets-Umgebung (die Aktivierungsschritte finden [&#x200B; unter „Konfigurieren &#x200B;](configure-aem.md#prerequisites) AEM Assets-Projekts„).

## AEM Assets zuerst konfigurieren

Führen Sie die AEM Assets-Schritte **vor** Sie [ein Support-Ticket](#onboarding) für die Mandantenregistrierung aus. Das Installationsmuster stimmt mit dem von Adobe Commerce as a Cloud Service überein (siehe [Konfigurieren des AEM Assets-Projekts zur Unterstützung von Commerce-Metadaten](configure-aem.md).

### Schritt 1: AEM Commerce-Paket bereitstellen

Installieren und stellen Sie das `assets-commerce` in Ihrem AEM-Projekt bereit, damit Commerce-Metadatenschemata, Ereignisse und die Benutzeroberfläche verfügbar sind.

Führen Sie das vollständige Verfahren unter [Installieren des `assets-commerce`-Pakets](configure-aem.md#step-1-install-the-assets-commerce-package) aus. Bevor Sie ein Support-Ticket öffnen, führen Sie die folgenden Schritte aus:

1. Klonen Sie das Cloud Manager-Git-Repository und kopieren Sie den [AEM Assets Commerce](https://github.com/ankumalh/assets-commerce)Repository-Code in Ihr Projekt.

1. Ersetzen Sie in allen `filter.xml` und `pom.xml` Dateien für Ihr Projekt alle Vorkommen von &lt;my-app> durch Ihren App-Namen.

1. Übertragen, übertragen, die Bereitstellungs-Pipeline ausführen und überprüfen, ob die Registerkarte **[!UICONTROL Commerce]** in den Asset-Eigenschaften angezeigt wird.

Unter [Installieren des `assets-commerce`-](configure-aem.md#step-1-install-the-assets-commerce-package) finden Sie Screenshots zu Cloud Manager, Pipeline-Schritte und Fehlerbehebungen, wenn die Registerkarte **[!UICONTROL Commerce]** fehlt.

### Schritt 2: Aktivieren von Dynamic Media mit OpenAPI

Dynamic Media mit OpenAPI-Funktionen muss in Ihrer AEM Assets-Umgebung aktiviert werden. Self-Service-Pfade (z. B. Cloud Manager für Produktvisualisierungen) und Adobe-Support-Routen werden unter &quot;[&#x200B; des AEM Assets-Projekts“ &#x200B;](configure-aem.md#prerequisites).

### Schritt 3: Anwenden von Commerce-Metadaten und Genehmigen von Assets

Fügen Sie Ihren Produktbildern in AEM Assets Commerce-Metadaten hinzu. Felddefinitionen finden Sie unter [AEM Commerce-Paketinhalte](configure-aem.md#aem-commerce-assets-commerce-package-contents).

Das Asset muss den Status **Genehmigt** aufweisen, damit die Daten mit dem Trigger synchronisiert werden können. Beim Speichern von Metadaten allein tritt kein Trigger des Ereignisses auf.

### Schritt 4: Optional - Commerce-Metadatenprofil konfigurieren

Wenn Sie sich für die Verwendung von AEM-Metadatenprofilen zur Optimierung der Bearbeitung entscheiden, konfigurieren Sie diese **nachdem** das Paket bereitgestellt wurde und Ihr Team mit den erforderlichen Commerce-Feldern vertraut ist - dasselbe optionale Muster wie **Konfigurieren des AEM Assets-Projekts**.

Siehe [Konfigurieren eines Metadatenprofils](configure-aem.md#step-2-optional-configure-a-metadata-profile).

## Einschränkungen

Die [!DNL Commerce Optimizer]-Integration hat die folgenden Einschränkungen:

### Layer-bezogene Einschränkungen

Lesen Sie diesen Abschnitt **vorher**, bevor Sie einen Namen für die Katalogebene in Ihrem Support-Ticket auswählen. Das Auswählen oder Freigeben von Ebenen ohne diesen Kontext ist häufig eine Ursache für vermeidbare Support-Fälle.

**Verwenden Sie eine dedizierte Ebene für AEM Assets-Inhalte.** Payloads, die von AEM Assets gesendet werden, befüllen einen Commerce Optimizer-Katalog **Layer**. Werte in dieser Ebene **überschreiben** Basisattribute des Katalogs, in denen Felder bereitgestellt werden. Wenn die Integration ein Feld in der Payload auslässt, können die entsprechenden Werte in dieser Ebene mit leeren Werten überschrieben werden. Die Freigabe einer Ebene für nicht verwandte Commerce-Workflows - oder die Wiederverwendung einer Ebene, die bereits nicht von AEM stammende Produktdaten speichert - kann **unbeabsichtigten Datenverlust** oder verwirrende Überschreibungen verursachen. Planen Sie die Ebenenauswahl **bevor** Sie Ihr Support-Ticket öffnen und reservieren Sie diesen Ebenennamen (z. B. den **`AEM-Assets`**) hauptsächlich für die AEM-gesteuerte Produktbild-Synchronisierung.

>[!IMPORTANT]
>
>Die Integration unterstützt **eine Katalogquelle pro Mandant**: ein einzelnes Gebietsschema und **eine benannte Ebene**. Die Konfiguration mehrerer AEM-Assets-Ebenen oder mehrerer Gebietsschemata für denselben Mandanten wird derzeit nicht unterstützt.

### Sonstige Einschränkungen

* **Nur Bilder**: Die Integration unterstützt derzeit keine Video- oder anderen Medientypen.
* **Keine Kategoriebilder**: Die Synchronisierung von Kategoriebildern ist nicht verfügbar. Kategoriebilder von AEM Assets für den Assets-Selektor (Einfügen in die Benutzeroberfläche) werden nicht unterstützt.
* **Keine Unterscheidung zwischen mehreren Sites**: Die Integration verarbeitet keine Website-übergreifenden. Ein mit einem Produkt verknüpftes Bild wird über alle Kanäle und Richtlinien hinweg gleich angezeigt.
* **Bildposition / -reihenfolge**: Bildposition und -reihenfolge werden nicht unterstützt.
* **Produkt muss vorhanden**: Wenn das Produkt nicht in [!DNL Commerce Optimizer] vorhanden ist, wird die Ebene für diese Produkt-Asset-Zuordnung nicht erstellt.

## Onboarding

Um die AEM Assets-Integration mit [!DNL Commerce Optimizer] zu integrieren, müssen [&#x200B; ein Support-Ticket erstellen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).

Der Adobe-Support verwendet die Informationen in Ihrem Ticket, um Ihren Mandanten beim Assets Integration Service zu registrieren und die Integration zu konfigurieren.

Stellen Sie sicher, dass Sie [AEM Assets zuerst konfigurieren](#configure-aem-assets-first) abgeschlossen haben, bevor Sie das Ticket senden.

Fügen Sie die folgenden Informationen in Ihr Support-Ticket ein:

* **[!DNL Adobe Commerce Optimizer]Mandanten-ID** (Instanz-ID) in Ihrer [!DNL Commerce Optimizer]-URL oder in der Benutzeroberfläche von Commerce Cloud Manager.
* **AEM-Programm-ID**.
* **AEM-Umgebungskennung**.
* **Matching-Regel**: Übereinstimmung nach SKU oder [externer Matcher (App Builder)](../synchronize/custom-match.md){target=_blank}.
* **Layer**: Der Name der Katalogebene, mit der der Mandant registriert werden soll (siehe **Layer-bezogene Einschränkungen**). Geben Sie einen benutzerdefinierten Namen nur an, wenn dies beabsichtigt ist. Andernfalls wird der **`AEM-Assets`** verwendet.
* **Locale**: Das Gebietsschema der Katalogquelle, mit dem der Mandant registriert werden soll (z. B. `en-US`). Dies muss mit dem Gebietsschema übereinstimmen, das Sie in Ihrer Katalogansicht und in den Produktkatalogdaten verwenden.

Nachdem der Adobe-Support Ihr Ticket verarbeitet hat, wird die Integration konfiguriert und Ihr Mandant wird beim Assets Integration Service registriert.

Sobald das Onboarding abgeschlossen ist:

1. **Registrierung beim Assets Integration Service**: Ihr [!DNL Commerce Optimizer]-Mandant wird beim Assets Integration Service registriert, wobei Ihre [!DNL Adobe Commerce Optimizer]-Mandanten-ID, AEM-Programm-ID, AEM-Umgebungs-ID, Übereinstimmungsregel, Gebietsschema und Ebenenname verwendet werden, die im Ticket angegeben sind.

1. **Ereignisabonnement**: Assets Integration Service abonniert:

   * AEM Assets-Ereignisse (Asset genehmigt, aktualisiert, entfernt)
   * [!DNL Commerce Optimizer] Katalogereignisse (Produkt erstellt, aktualisiert)

Konfigurieren Sie Ihre [Katalogansicht](https://experienceleague.adobe.com/de/docs/commerce/optimizer/setup/catalog-view) so, dass Storefront und APIs AEM-gesteuerte Bilddaten enthalten:

* **Katalogquelle (Gebietsschema)** - Wählen Sie dasselbe Gebietsschema aus, das Sie in Ihrem Support-Ticket angegeben haben (z. B. **`en-US`**). Die Integration registriert ein Gebietsschema pro Mandant. Eine Nichtübereinstimmung verhindert, dass synchronisierte Bilder in der beabsichtigten Katalogansicht angezeigt werden.
* **Katalogebene** - Weisen Sie dieser Katalogansicht die **`AEM-Assets`** Ebene (oder Ihren benutzerdefinierten Ebenennamen aus dem Ticket) zu.

Wenn das Gebietsschema oder die Ebene nicht korrekt zugewiesen ist, werden Bilddaten möglicherweise **nicht angezeigt** oder verhalten sich unerwartet - auch wenn die Synchronisierung im Upstream erfolgreich war.

## Synchronisierung

Nach der Konfiguration synchronisiert die Integration `product-asset` automatisch.

Weitere Informationen finden [&#x200B; unter &#x200B;](../synchronize/custom-match.md)Benutzerdefinierter automatischer Abgleich“.

### Beispiel für Übereinstimmung nach SKU-Workflow

Ein typischer Fluss beim Hinzufügen eines vorhandenen Assets zu einem neuen Produkt:

1. Erstellen Sie das Produkt in [!DNL Commerce Optimizer] (über API oder Datenaufnahme). Das Produkt kann zunächst ohne Bilder vorhanden sein.

1. Öffnen Sie in AEM Assets das Asset, das Sie dem Produkt zuordnen möchten.

1. Fügen Sie die Produkt-SKU zu den **Commerce:skus**-Metadaten hinzu und weisen Sie Bildrollen zu (z. B. `thumbnail`, `image`).

1. Genehmigen Sie das Asset für die Bereitstellung. Dadurch wird das Ereignis Trigger, das der Assets Integration Service verarbeitet.

1. Assets Integration Service sendet die Produkt-Image-Zuordnung an [!DNL Commerce Optimizer]. Das Produkt in [!DNL Commerce Optimizer] wird mit den Bildern des Assets aktualisiert.

1. Überprüfen Sie, ob das Bild sichtbar ist. Warten Sie einige Minuten, bis die Synchronisierung abgeschlossen ist (normalerweise innerhalb weniger Minuten), überprüfen Sie dann das Produkt in der [!DNL Commerce Optimizer]-Benutzeroberfläche (z. B. Datensynchronisierung oder Katalogansicht) oder fragen Sie die Storefront-APIs (Catalog Service, Live Search, Storefront GraphQL API) ab, um zu bestätigen, dass das Bild zurückgegeben wird.

## Umgang mit Bildrollen

Wenn ein Produkt mehrere Assets hat, die dieselbe Bildrolle verwenden (z. B. zwei Assets mit der Rolle `thumbnail`), stellt die Integration sicher, dass nur ein Asset diese Rolle behält, um doppelte Rollen in der [!DNL Commerce Optimizer] und unerwartetes Verhalten der Storefront zu vermeiden.

**Verhalten:** Wenn eine Aktualisierung von AEM Assets gesendet wird, erhält das zuletzt aktualisierte Asset die Bildrolle (z. B. `thumbnail`) und die Rolle wird aus dem vorherigen Asset entfernt, in dem sie enthalten war. Dadurch wird verhindert, dass doppelte Bildrollen in der Storefront angezeigt werden.

## Ähnliche Themen

* [Produktvisualisierung](../../optimizer/setup/product-visuals.md)
* [Konfigurieren des AEM Assets-Projekts](configure-aem.md)
* [Benutzerdefinierter automatischer Abgleich](../synchronize/custom-match.md)
* [Übersicht über die AEM Assets-Integration](../overview.md)
