---
title: Hinzufügen von Dateien zu Produkten
description: Erfahren Sie, wie Sie Dateien wie PDFs, Handbücher und Datenblätter mithilfe von Dateityp-Produktattributen in [!DNL Adobe Commerce as a Cloud Service] an Produkte anhängen.
feature: Catalog Management, Products, Integration
role: Admin, Developer
level: Intermediate
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 848ba518d170c9a0270b2513fdc8efb6813f6845
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Hinzufügen von Dateien zu Produkten

[!DNL Adobe Commerce as a Cloud Service] unterstützt einen &quot;[&quot; (Produktattribut-Eingabetyp), &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/attributes-input-types){target="_blank"} es Händlern ermöglicht, Dateien wie PDFs, Handbücher, Zertifikate und Datenblätter direkt an Produkte anzuhängen. Dateien werden im Amazon S3-Medienspeicher gespeichert und können über die Storefront mithilfe von GraphQL oder über Integrationen mithilfe der REST-API aufgerufen werden.

Es gibt drei Möglichkeiten, Dateien in Produktdateiattribute hochzuladen:

* [Admin-Benutzeroberfläche](#upload-through-the-admin) - Dateien manuell auf die Seite zur Produktbearbeitung hochladen.
* [REST API](#upload-through-the-rest-api) - Hochladen von Dateien über die REST-API mithilfe von S3-vordefinierten URLs.
* [Produktimport](#upload-through-product-import) - Importieren Sie Dateien in großen Mengen, indem Sie externe URLs in CSV bereitstellen.

## Voraussetzungen

Vor dem Hochladen von Dateien müssen Sie ein Dateiattribut erstellen und es einem Attributsatz zuweisen.

* [Dateiattribut erstellen](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create){target="_blank"} - **[!UICONTROL Catalog Input Type for Store Owner]** auf &quot;**[!UICONTROL File]**&quot; festlegen.

* [Attribut einem Attributsatz zuweisen](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/create/attribute-sets#create-an-attribute-set){target="_blank"} - Ziehen Sie das neue Dateiattribut in die gewünschte Gruppe.

* Konfigurieren Sie zulässige Dateitypen und deren Größe in der Konfiguration [Produktdateiattribute](https://experienceleague.adobe.com/de/docs/commerce-admin/config/catalog/product-file-attributes).

## Hochladen von Dateien über den Administrator

Nachdem Sie [Dateiattribut erstellen](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create){target="_blank"} und es einem Attributsatz zuweisen, können Sie Dateien direkt über die Produktbearbeitungsseite hochladen.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.

1. Öffnen Sie das Produkt, das Sie bearbeiten möchten.

1. Suchen Sie das Feld Dateiattribut und klicken Sie auf **[!UICONTROL Upload]** , um eine Datei auszuwählen.

![Schaltfläche „Datei hochladen“ in „Admin“](./assets/upload-file.png){width="600" zoomable="yes"}

1. Klicken Sie auf **[!UICONTROL Save]**.

Um eine Datei zu ersetzen, löschen Sie die vorhandene Datei und laden Sie eine neue hoch. Die hochgeladene Datei wird im Amazon S3-Medienspeicher gespeichert.

## Hochladen über die REST-API

Verwenden Sie den [S3-vordefinierten URL-Fluss](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/s3-uploads/){target="_blank"} um Dateien programmgesteuert über die REST-API hochzuladen. Dieser Prozess funktioniert für Produktdateiattribute auf die gleiche Weise wie für andere Medientypen wie für Kategoriebilder und Kundenattributdateien.

Der Prozess umfasst vier Schritte:

1. Rufen Sie `POST V1/media/initiate-upload` mit dem Dateinamen und der `media_resource_type` für Produktdateiattribute auf.
1. Verwenden Sie die zurückgegebene vordefinierte URL, um die Datei direkt an Amazon S3 zu `PUT`.
1. Rufen Sie `POST V1/media/finish-upload` an, um den Upload zu bestätigen.
1. Weisen Sie den zurückgegebenen Schlüssel dem Dateiattribut des Produkts über `PUT /V1/products/{sku}` zu und übergeben Sie dabei den Schlüssel als [benutzerdefiniertes Attribut](https://developer.adobe.com/commerce/webapi/rest/modules/custom-attributes/)-Wert.

## Hochladen durch Produktimport

Sie können Dateien mithilfe der „Import-API[&#x200B; oder der Admin](https://developer.adobe.com/commerce/webapi/rest/modules/import/){target="_blank"}Import-Benutzeroberfläche stapelweise an Produkte anhängen. Produktdateiattribute unterstützen nur den Import aus externen URLs, der demselben Ansatz folgt wie [Methode 2 für den Produktbildimport](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/import/data-import-product-images#method-2-import-images-from-external-server){target="_blank"}. Commerce lädt die Datei von der angegebenen URL herunter und speichert sie im S3-Medienspeicher.

>[!NOTE]
>
>Das Importieren von Dateien von einem lokalen Serverpfad (Methode 1) wird in [!DNL Adobe Commerce as a Cloud Service] nicht unterstützt, da kein direkter Dateisystemzugriff besteht.

### URL in einer eigenen Spalte angeben

Verwenden Sie den Attributcode als CSV-Spaltenüberschrift und die vollständige URL als Wert. Wenn der Attributcode beispielsweise `file_upload` ist, würde die CSV wie folgt aussehen:

```csv
sku,name,file_upload
ADB112,"My Product",https://example.com/files/manual.pdf
```

### URL in `additional_attributes` angeben

Alternativ können Sie das Dateiattribut in die `additional_attributes` Spalte einfügen:

```csv
sku,name,additional_attributes
ADB112,"My Product",file_upload=https://example.com/files/manual.pdf
```

In beiden Fällen muss die URL öffentlich zugänglich sein und die Dateierweiterung und -größe müssen den [konfigurierten Einschränkungen“ &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/config/catalog/product-file-attributes){target="_blank"}.

## Abrufen von Dateien über GraphQL

[!DNL Adobe Commerce as a Cloud Service] stellt der Endpunkt [Catalog Service GraphQL](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/){target="_blank"} Produktdaten bereit. Dateiattribute werden im Feld `attributes` auf der `ProductView` angezeigt, wobei die `value` die vollständige öffentliche URL zur Datei enthält:

```graphql
{
  products(skus: ["ADB112"]) {
    sku
    name
    attributes(roles: []) {
      name
      label
      value
    }
  }
}
```

Die Antwort enthält das Dateiattribut mit der öffentlichen URL:

```json
{
  "data": {
    "products": [
      {
        "sku": "ADB112",
        "name": "Example product",
        "attributes": [
          {
            "name": "file",
            "label": "FILE",
            "value": "https://<host>/media/catalog/product_file/manual.pdf",
          }
        ]
      }
    ]
  }
}
```

>[!NOTE]
>
>Für diese Abfrage sind die Kopfzeilen `Magento-Website-Code` und `Magento-Store-View-Code` erforderlich. Weitere Informationen finden Sie unter [Abfrage von Catalog Service-Produkten](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/){target="_blank"}.

## Abrufen von Dateien über die REST-API

Beim Abrufen eines Produkts über [REST-API](https://developer.adobe.com/commerce/webapi/reference/rest/saas/){target="_blank"} (`GET /V1/products/{sku}`) werden Dateiattribute im `custom_attributes`-Array mit dem Dateinamen als Wert angezeigt:

```json
{
  "custom_attributes": [
    {
      "attribute_code": "file_upload",
      "value": "manual_7aa0b2d63f6d3dbf.pdf"
    }
  ]
}
```
