---
title: Migrieren von Mediendateien zu AEM
description: Migrieren Sie die Mediendateien aus Adobe Commerce oder einer externen Quelle in das AEM Assets-DAM.
feature: CMS, Media, Integration
exl-id: ccb13e90-8b18-4f1e-94ce-f0dacea2f617
source-git-commit: ac880333814d9d9a45e658e2a637cd9634dbfb1f
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Migrieren von Mediendateien in das AEM Assets-DAM

Sowohl Adobe Commerce als auch Adobe Experience Manager (AEM) bieten integrierte Funktionen zur Optimierung der Migration von Mediendateien von Commerce zum AEM Assets **Digital Asset Management System (DAM)**. Sie können auch Mediendateien aus anderen Quellen migrieren.

## Voraussetzungen

| Kategorie | Anforderung |
|----------|-------------|
| **Systemanforderungen** | <ul><li>AEM as a Cloud Service-Umgebung mit AEM Assets bereitgestellt</li><li>Ausreichende Speicherkapazität</li><li>Netzwerkbandbreite für große Dateiübertragungen</li></ul> |
| **Erforderlicher Zugriff und Berechtigungen** | <ul><li>Administratorzugriff auf AEM Assets as a Cloud Service</li><li>Zugriff auf das Quellsystem, in dem Mediendateien gespeichert werden (Adobe Commerce oder externes System)</li><li>Entsprechende Berechtigungen für den Zugriff auf Cloud-Speicher-Services</li></ul> |
| **Cloud-Speicherkonto** | <ul><li>AWS S3- oder Azure Blob Storage-Konto</li><li>Konfiguration von privaten Containern/Buckets</li><li>Authentifizierungsdaten</li></ul> |
| **Source-Inhalte** | <ul><li>Organisierte Mediendateien bereit für die Migration</li><li>Bild- und Videodateien in <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/file-format-support#image-formats">von AEM Assets unterstützten Formaten</a>.</li><li>Bereinigen von duplizierten Assets</li></li> |
| **Metadatenvorbereitung** | <ul><li><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/aem-asset-management/getting-started/aem-assets-configure-aem">AEM Assets-Metadatenprofil für Commerce-Assets konfiguriert</a></li><li>Zugeordnete Metadatenwerte für jedes Asset</li><li>CSV-Datei-Editor (z. B. Microsoft Excel)</li></ul> |

## Best Practices für die Migration

1. Kuratieren Sie Assets vor der Migration, indem Sie nicht verwendete und doppelte Inhalte entfernen.

1. Organisieren Sie Assets logisch nach Größe, Format oder Anwendungsfall.

1. Erwägen Sie, große Migrationen in kleinere Batches aufzuteilen.

1. Planung ressourcenintensiver Importe außerhalb der Spitzenzeiten

1. Validieren der Metadatenzuordnung vor dem vollständigen Import

## Migrations-Workflow

Befolgen Sie den Migrations-Workflow, um Mediendateien aus Adobe Commerce oder einem anderen externen System zu exportieren und in das AEM Assets-DAM zu importieren.

### Schritt 1: Exportieren von Inhalten aus der vorhandenen Datenquelle

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."}

Für Adobe Commerce-Händler kann das **Remote-Speichermodul** den Import und Export von Mediendateien erleichtern. Mit diesem Modul können Unternehmen Mediendateien mithilfe von Remote-Speicherdiensten wie AWS S3 speichern und verwalten. Informationen zum Einrichten des Remote-Speichers für Ihre Commerce-Instanz finden Sie unter [Konfigurieren des Remote](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-aws-s3) im **Commerce-Konfigurationshandbuch**.

Wenn Sie Mediendateien haben, die außerhalb von Adobe Commerce gespeichert sind, laden Sie sie direkt in eine der [Datenquellen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/bulk-import-assets-view#prerequisites) hoch, die von AEM as a Cloud Service unterstützt werden.

### Schritt 2: Erstellen einer CSV-Datei für die Metadatenzuordnung

Erstellen Sie eine CSV-Datei, die jede Mediendatei ihren Commerce-Produktdaten zuordnet. Wählen Sie eine der folgenden Methoden:

* **Adobe Commerce (PaaS)**: Verwenden Sie den CLI-Befehl, um die CSV automatisch aus Ihrem Katalog zu generieren
* Manuelles Erstellen der CSV-Datei

#### Exportieren von Metadaten mithilfe der CLI

[!BADGE Nur PaaS]{type=Informative tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur)."}

Verwenden Sie den CLI-Befehl für die AEM Assets-Integration, um automatisch eine Metadaten-CSV-Datei zu generieren, die Bild-URLs, Positionen und Rollen aus den im Commerce-Projekt gespeicherten Produktmediendateien enthält.

1. Führen Sie die verfügbaren Befehle auf, um zu überprüfen, ob das AEM Assets-Integrationsmodul installiert ist:

   ```bash
   bin/magento list aem
   ```

   Die benutzerdefinierten Erweiterungsbefehle werden unter `aem` am Anfang der Befehlsliste angezeigt.

1. Führen Sie den Metadatenexportbefehl mit Ihrem AEM-Pfadpräfix aus:

   ```bash
   bin/magento aem:assets:export:csv <AEM-path-prefix>
   ```

   Der `<AEM-path-prefix>` ist der Basisordnerpfad, in dem Ihre Assets im AEM Assets DAM gespeichert werden (z. B. `/content/dam/commerce/`).

   ```bash
   bin/magento aem:assets:export:csv /content/dam/commerce/
   ```

   Dadurch wird eine `metadata.csv` im `var/export` erstellt, die Bild-URLs, Positionen und Rollen für jedes Produkt-Asset in Ihrem Commerce-Katalog enthält.

#### CSV manuell erstellen

Für Mediendateien, die außerhalb von Adobe Commerce gespeichert werden, müssen Sie die CSV-Datei manuell erstellen. Die Spaltenüberschriften **müssen übereinstimmen** mit den Feldnamen, die in Ihrem [AEM Assets-Metadatenprofil konfiguriert ](configure-aem.md). Füllen Sie nach dem Erstellen der Datei die Zeilen mit den Metadatenwerten für jede Mediendatei.

| Metadaten | Beschreibung | Wert |
|-------|-------------|--------|
| assetPath | Der vollständige Pfad, in dem das Asset im AEM Assets-Repository gespeichert wird.<br><br>Verwenden Sie den Pfad, um Unterordner zu erstellen und Commerce-Assets zu organisieren, z. B. `content/dam/commerce/<brand>/<type>`. | `/content/dam/commerce/<sub-folder>/..<filename>` |
| Handel:positions | Die Position/Reihenfolge des Assets in den Produktkatalogen | Mehrere numerische Werte, durch senkrechte Striche getrennt („Zahl: multi„) |
| Handel:isCommerce | Markierung, die angibt, ob das Asset in Commerce verwendet wird | `Yes` |
| Handel:skus | Mit diesem Asset verknüpfte Produkt-SKUs | Mehrere Zeichenfolgenwerte, durch senkrechte Striche getrennt (Zeichenfolge: multi) |
| Handel:roles | Die Rollen oder Typen von Bildern für das Asset (z. B. `thumbnail`, `main image`, `swatch`) | Mehrere Werte, durch Semikolons getrennt (z. B. „Miniaturansicht; Bild; Farbfeld_Bild; SMALL_IMAGE„) |

+++CSV-Code

Verwenden Sie diesen CSV-Beispielcode, um die Datei in einem Code-Editor oder einer Tabellenkalkulationsprogramm wie Microsoft Excel zu erstellen.

```csv
assetPath,commerce:positions{{Number: multi}},commerce:isCommerce{{String}},commerce:skus{{String: multi}},commerce:roles{{String: multi}}
/content/dam/commerce/sample1.jpg,1,Yes,sku1,thumbnail; image; swatch_image; small_image
/content/dam/commerce/sample2.jpg,1|1|1,Yes,sku1|sku2|sku3,thumbnail; image; swatch_image; small_image|image|image; small_change
```

+++

### Schritt 3: Massenimport von Assets in AEM Assets

Nachdem Sie die Metadatenzuordnungsdatei erstellt haben, verwenden Sie das Tool für den Massenimport von AEM Assets , um Ihre Assets zu importieren.

Im Folgenden finden Sie einen allgemeinen Überblick über die Verwendung des Tools.

1. [Melden Sie sich bei Ihrer AEM Assets as a Cloud Service-Autorenumgebung ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/aem-users#login-aem).

1. Wählen Sie in der Ansicht Experience Manager-Tools die Option **[!UICONTROL Assets]** > **[!UICONTROL Bulk Import]** aus.

   ![AEM Assets-Authoring](../assets/aem-assets-bulk-import-selection.png){width="600" zoomable="yes"}

1. Wählen Sie aus den Massenimportkonfigurationen die Option **[!UICONTROL Create]** aus, um das Konfigurationsformular zu öffnen.

   ![AEM Assets-Authoring](../assets/aem-assets-bulk-import-configuration.png){width="600" zoomable="yes"}

1. Richten Sie die Konfiguration ein und speichern Sie sie.

   Sie benötigen:

   * Authentifizierungsdaten für Ihre Datenquelle
   * Der Zielordner in AEM Assets, in dem importierte Dateien gespeichert werden
   * Optional. Informationen über die MIME-Typen, die Dateigröße und andere Parameter zum Anpassen der Importkonfiguration
   * Der Pfad zur CSV-Datei für die Metadatenzuordnung, die Sie in die Cloud-Speicherinstanz hochgeladen haben.

   Ausführliche Anweisungen finden Sie unter [Konfigurieren des Tools für den Massenimport](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/add-assets#configure-bulk-ingestor-tool) im *AEM Assets as a Cloud Service-Benutzerhandbuch*.

1. Verwenden Sie nach dem Speichern der Konfiguration die Tools für den Massenimport, um den Importvorgang zu testen und auszuführen.

>[!MORELIKETHIS]
>
> [Video-Demo zum Tool für den Massenimport](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/add-assets#asset-bulk-ingestor)
> [Tipps, Best Practices und Einschränkungen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/add-assets#tips-limitations)
> [Hochladen oder Aufnehmen von Assets mithilfe von APIs](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/admin/developer-reference-material-apis#asset-upload)
