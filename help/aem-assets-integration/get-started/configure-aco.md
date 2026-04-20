---
title: Konfigurieren von AEM Assets für Commerce Optimizer
description: Erfahren Sie, wie Sie die AEM Assets-Integration für  [!DNL Adobe Commerce Optimizer] konfigurieren.
feature: CMS, Media, Configuration, Integration
source-git-commit: 14c4178338859d55a7391139033d51d1aa6f7678
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 0%

---


# Konfigurieren von AEM Assets für [!DNL Adobe Commerce Optimizer]

[!BADGE nur SaaS]{type=Positive tooltip="Gilt nur für Adobe Commerce Optimizer-Projekte."}

Die AEM Assets Integration for [!DNL Adobe Commerce Optimizer] ermöglicht Händlern die Verwendung von AEM Assets als zentralisierte Digital Asset Management-Lösung für Produktbilder. In diesem Handbuch wird die für [!DNL Commerce Optimizer] spezifische Konfiguration beschrieben.

Im Gegensatz zu Adobe Commerce (PaaS) oder Adobe Commerce as a Cloud Service (ACCS) verfügt [!DNL Commerce Optimizer] über keine Benutzeroberfläche mit Administratorkonfiguration. Um die Integration zu aktivieren, erstellen Sie ein Support-Ticket mit Ihren [!DNL Adobe Commerce Optimizer]- und AEM Assets-Details. Der Adobe-Support konfiguriert die Integration und registriert Ihren Mandanten beim Assets Integration Service.

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
* Dynamic Media mit aktivierter OpenAPI in Ihrer AEM Assets-Umgebung.

## Onboarding

Um die AEM Assets-Integration mit [!DNL Commerce Optimizer] zu integrieren, müssen [&#x200B; ein Support-Ticket erstellen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).

Der Adobe-Support verwendet die Informationen in Ihrem Ticket, um Ihren Mandanten beim Assets Integration Service zu registrieren und die Integration zu konfigurieren.

Fügen Sie die folgenden Informationen in Ihr Support-Ticket ein:

* **[!DNL Adobe Commerce Optimizer]Mandanten-ID** (Instanz-ID) in Ihrer [!DNL Commerce Optimizer]-URL oder in der Benutzeroberfläche von Commerce Cloud Manager.
* **AEM-Programm-ID**.
* **AEM-Umgebungskennung**.
* **Matching-Regel**: Übereinstimmung nach SKU oder [externer Matcher (App Builder)](../synchronize/custom-match.md){target=_blank}.
* **Layer**: Der Name der Katalogebene, mit der der Mandant registriert werden soll. Geben Sie bei Bedarf einen benutzerdefinierten Namen an. Andernfalls wird die `AEM-Assets` verwendet.
* **Locale**: Das Gebietsschema der Katalogquelle, mit dem der Mandant registriert werden soll (z. B. `en-US`).

>[!IMPORTANT]
>
> Die Integration unterstützt eine Quelle pro Mandant, nämlich die Kombination aus einem Gebietsschema und einer Ebene.

Nachdem der Adobe-Support Ihr Ticket verarbeitet hat, wird die Integration konfiguriert und Ihr Mandant wird beim Assets Integration Service registriert.

Sobald das Onboarding abgeschlossen ist:

1. **Registrierung beim Assets Integration Service**: Ihr [!DNL Commerce Optimizer]-Mandant wird beim Assets Integration Service unter Verwendung der [!DNL Adobe Commerce Optimizer]-Mandanten-ID, der AEM-Programm-ID, der AEM-Umgebungs-ID und des Mandanten registriert.

1. **Ereignisabonnement**: Assets Integration Service abonniert:

   * AEM Assets-Ereignisse (Asset genehmigt, aktualisiert, entfernt)
   * [!DNL Commerce Optimizer] Katalogereignisse (Produkt erstellt, aktualisiert)

### Einschränkungen

Die [!DNL Commerce Optimizer]-Integration hat die folgenden Einschränkungen:

* **Einzelschicht pro Händler** - Die AEM Assets-Integration unterstützt eine AEM-Assets-Schicht pro Händler (eine Quelle pro Mandant). Die Konfiguration mehrerer Ebenen pro Händler wird derzeit nicht unterstützt.
* **Nur Bilder** - Die Integration unterstützt keine Video- oder anderen Medientypen.
* **Keine Kategoriebilder** - Die Kategoriebildsynchronisierung ist nicht verfügbar. Kategoriebilder von AEM Assets für den Assets-Selektor (Einfügen in die Benutzeroberfläche) werden nicht unterstützt.
* **Keine Unterscheidung zwischen mehreren Sites** - Die Integration verarbeitet keine Website-übergreifenden. Ein mit einem Produkt verknüpftes Bild wird über alle Kanäle und Richtlinien hinweg gleich angezeigt.
* **Bildposition/Bildreihenfolge** - Bildposition und -reihenfolge werden nicht unterstützt.
* **Produkt muss vorhanden** - Wenn das Produkt nicht in [!DNL Commerce Optimizer] vorhanden ist, wird die Ebene für diese Produkt-Asset-Zuordnung nicht erstellt.
* **Ebenenfeld überschreiben** - Werte in einer Ebene überschreiben den Basiskatalog. Wenn ein Feld nicht in der Payload der Ebene gesendet wird, kann es mit einem leeren Wert überschrieben werden. Verwenden Sie eine dedizierte Ebene für AEM Assets-Inhalte. Die Wiederverwendung einer vorhandenen Ebene für andere Zwecke kann zu unbeabsichtigtem Datenverlust führen.

### Konfigurieren von AEM Assets

Der Installations- und Konfigurationsprozess von AEM Assets für [!DNL Commerce Optimizer] entspricht dem für Adobe Commerce as a Cloud Service. Die [&#x200B; Schritte finden Sie unter „Konfigurieren des AEM Assets-Projekts zur Unterstützung &#x200B;](configure-aem.md) Commerce-Metadaten“.

Stellen Sie sicher, dass Ihre AEM Assets-Umgebung bereit ist:

1. **AEM Assets-Konfiguration**: Konfigurieren Sie das Commerce-Metadatenprofil. Siehe [Konfigurieren eines Metadatenprofils](configure-aem.md#step-2-optional-configure-a-metadata-profile).

1. **Aktivierung von Dynamic Media**: Überprüfen Sie, ob Dynamic Media mit OpenAPI-Funktionen in Ihrer AEM Assets-Umgebung aktiviert ist.

## Konfigurieren von AEM Assets

Um die Synchronisierung von Produkten und Assets zu aktivieren, konfigurieren Sie Ihre AEM Assets-Umgebung.

### Schritt 1: Aktivieren von Dynamic Media mit OpenAPI

Dynamic Media mit OpenAPI muss in Ihrer AEM Assets-Umgebung aktiviert sein. Mit Produktvisualisierungen und neuen AEM Assets-Lizenzen können Sie diese Funktion über Cloud Manager im Self-Service aktivieren. Ältere AEM Assets-Lizenzen benötigen Adobe-Support, um sie zu aktivieren. Die [&#x200B; Schritte zur Aktivierung finden Sie &#x200B;](configure-aem.md#prerequisites) „Konfigurieren des AEM Assets-Projekts“.

### Schritt 2: Optional. Konfigurieren des Commerce-Metadatenprofils

Richten Sie das Metadatenprofil in AEM Assets ein, um Commerce-spezifische Metadaten zu speichern.

Detaillierte [&#x200B; finden Sie unter „Konfigurieren &#x200B;](configure-aem.md#step-2-optional-configure-a-metadata-profile) Metadatenprofils“.

### Schritt 3: Anwenden von Metadaten auf Assets

Hinzufügen von Commerce-Metadaten zu Ihren Produktbildern in AEM Assets.

Felddefinitionen finden Sie im [Inhalt &#x200B;](configure-aem.md#aem-commerce-assets-commerce-package-contents) AEM Commerce-Pakets und [Konfigurieren eines Metadatenprofils](configure-aem.md#step-2-optional-configure-a-metadata-profile) für die Einrichtungsschritte.

Das Asset muss den Status **Genehmigt** aufweisen, damit die Daten mit dem Trigger synchronisiert werden können. Beim Speichern von Metadaten allein tritt kein Trigger des Ereignisses auf.

>[!CAUTION]
>
> Weisen Sie die `AEM-Assets` Ihrer [Katalogansicht“ &#x200B;](https://experienceleague.adobe.com/de/docs/commerce/optimizer/setup/catalog-view). Wenn die Ebene nicht zugewiesen ist, können Produktbilddaten unerwartet überschrieben werden.

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
