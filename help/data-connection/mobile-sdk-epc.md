---
title: Integrieren von Adobe Experience Platform Mobile SDK mit Commerce
description: Erfahren Sie, wie Sie die Adobe Experience Platform Mobile SDK mit Ihrer Headless- oder benutzerdefinierten Commerce-Storefront verwenden.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Integrieren von Adobe Experience Platform Mobile SDK mit Commerce

>[!IMPORTANT]
>
>Adobe Experience Platform Mobile SDK für iOS unterstützt iOS 11 oder höher.

Durch die Integration von [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) mit der Commerce Mobile App können Händler Commerce-[ (Ereignisdaten](events.md) an Experience Platform Edge senden.

Wenn Commerce-Ereignisdaten am Edge verfügbar sind, können andere Adobe Experience Cloud-Programme darauf zugreifen. Sie können die Daten beispielsweise verwenden, um Zielgruppen in Real-Time CDP zu erstellen, und dann [diese Zielgruppen verwenden](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) um Ihre Mobile App von Commerce zu personalisieren.

## Konfiguration

Installieren und konfigurieren Sie SDK in der Experience Platform, um mit der Verwendung von Adobe Experience Platform Mobile SDK mit Commerce zu beginnen. Schließen Sie dann Ihre Konfiguration in Commerce ab.

### Experience Platform

1. Erfahren Sie mehr über die Funktionen mobiler Apps durch das Tutorial zu [Adobe Experience Cloud in Mobile Apps](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [Installieren und Konfigurieren](https://developer.adobe.com/client-sdks/documentation/getting-started/) der SDK in Experience Platform.

   >[!NOTE]
   >
   >Das Schema, das Sie in der Experience Platform erstellen und konfigurieren, entspricht dem Schema, das Sie im Anwendungscode in Ihrer Commerce Mobile App verwenden.

### Commerce

Nachdem Sie die SDK-Konfiguration für Experience Platform abgeschlossen haben, fügen Sie die SDK-Konfiguration zu Commerce hinzu.

1. Um Commerce-Ereignisdaten über die SDK an Experience Platform zu senden, müssen Sie ein XDM-Schema im Anwendungs-Code angeben. Dieses Schema muss mit dem Schema ([) ](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) SDK in Experience Platform übereinstimmen.

   Das folgende Beispiel zeigt, wie Sie das `web.webpagedetails.pageViews`-Ereignis verfolgen und die `identityMap` mithilfe des E-Mail-Felds festlegen.

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. Herstellen einer Verbindung zur Commerce Cloud-Umgebung.

   Fügen Sie in den Build-Einstellungen Ihres Projekts die URL zum Commerce GraphQL-Endpunkt hinzu. Beispielsweise:

   - Debug: http://_debug_.commerceSite.cloud/graphql/
   - Version: http://_release_.commerceSite.cloud/graphql/

1. Um Daten von den Commerce GraphQL-Endpunkten abzurufen, generieren Sie zunächst die erforderlichen Dateien und Ordner in Ihrem Projekt mithilfe des [Apollo Code Generator](https://www.apollographql.com/docs/ios/).

   1. Wählen Sie im Projektverzeichnis [install](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) Apollo iOS aus.

   1. [Initialisieren](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) der Apollo Codegen-CLI.

      Dadurch wird eine `apollo-codegen-configuration.json` Datei erstellt.

   1. Generieren Sie die erforderlichen GraphQL-Dateien und -Ordner in Ihrem Projekt, indem Sie den Inhalt der `apollo-codegen-configuration.json`-Datei durch Folgendes ersetzen:

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [Abrufen](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) des Commerce GraphQL-Schemas.

      Stellen Sie sicher, dass der Pfad zur `./apollo-codegen-config.json`-Datei lautet, die den Verweis auf das Commerce GraphQL-Schema enthält.

   1. [Generieren](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) des Quell-Codes

      Stellen Sie sicher, dass der Pfad zur `./apollo-codegen-config.json`-Datei ist, die die Konfigurationsinformationen zum Generieren der erforderlichen Dateien und Verzeichnisse enthält.

   1. Fügen Sie innerhalb des neu erstellten **GraphQLGenerated**-Ordners GraphQL-Typen hinzu oder bearbeiten Sie sie. Sie können beispielsweise einen `DynamicBlocks.graphql` mit folgendem Inhalt hinzufügen:

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   Sie haben jetzt Adobe Experience Platform Mobile SDK in Ihre Commerce Mobile App integriert. Ereignisdaten fließen von Ihrer App zum Experience Platform Edge.

## So unterscheidet man von Mobile Apps generierte Commerce-Ereignisse

Alle [Ereignisse](events.md) enthalten ein Feld namens `channel`. Das Feld `channel` enthält `channel._id` und `channel._type`, für die eine Luma-Storefront über Namespace-Werte von `"https://ns.adobe.com/xdm/channels/web"` bzw. `"https://ns.adobe.com/xdm/channel-types/web"` verfügt. Bei einer mobilen Storefront sind die Namespace-Werte jedoch `"https://ns.adobe.com/xdm/channels/mobile-app"` bzw. `"https://ns.adobe.com/xdm/channel-types/mobile"`.

## Nächste Schritte

Informationen zum Abrufen von Real-Time CDP-Zielgruppen aus Ihrer mobilen Commerce-App mit Informationen zu Warenkorbpreisregeln, dynamischen Blöcken und zugehörigen Produktregeln finden Sie unter [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html#retrieve-audiences-using-the-adobe-experience-platform-mobile-sdk).
