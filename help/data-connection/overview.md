---
title: '[!DNL Data Connection]'
description: Erfahren Sie, wie Sie Adobe Commerce-Daten mit Adobe Experience Platform mithilfe der  [!DNL Data Connection] -Erweiterung integrieren.
recommendations: noCatalog
exl-id: 660f9337-cad8-47fb-a959-0770f0fd813c
TQID: https://experienceleague.adobe.com/-wfkGM2isTVmAaJokndxVy0-UtZ4pM9msYXmh2IE-Hc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 5ba5dfa23580b5eefa8271277e78c6ea67879b90
workflow-type: tm+mt
source-wordcount: 1373
ht-degree: 1%

---

# [!DNL Data Connection]

>[!IMPORTANT]
>
>Der Experience Platform-Connector wurde in [!DNL Data Connection] umbenannt.

Die [!DNL Data Connection]-Erweiterung verbindet Ihre Adobe Commerce-Webinstanz mit der Adobe Experience Platform und der Edge Network. Für Entwickler mobiler Apps verwenden Sie die Adobe Experience Platform Mobile SDK mit Commerce , um Commerce-Daten zu erfassen und an die Experience Platform zu senden. [Weitere Informationen](./mobile-sdk-epc.md).

Händler, die mehrere Websites betreiben, können die entsprechenden [!DNL Data Connection] für jede Website konfigurieren, einschließlich der Sandbox-Auswahl für Experience Platform. Siehe [Verbinden von Commerce-Daten mit Adobe Experience Platform](connect-data.md#configuration-scope) für globale Felder im Vergleich zu Feldern, die sich auf Websites beziehen.

Ihr Commerce-Store enthält eine Fülle von Daten. Informationen darüber, wie Kundinnen und Kunden die Produkte auf Ihrer Site durchsuchen, anzeigen und schließlich kaufen, können Möglichkeiten aufzeigen, ein personalisierteres Einkaufserlebnis zu schaffen. Diese Daten können zwar native Commerce-Funktionen wie Warenkorbpreisregeln und dynamische Blöcke enthalten, die Daten bleiben jedoch in Ihrer Commerce-Instanz isoliert.

Der Adobe Experience Platform bietet eine Reihe von Technologien, die bei der Einspeisung von Daten aus Ihrem Commerce-Store diese Daten über den Edge Network an andere Adobe DX-Produkte verteilen können, um Erkenntnisse über das Kaufverhalten Ihrer Kundinnen und Kunden zu gewinnen. Mit diesen tiefen Einblicken können Sie auf allen Kanälen ein personalisierteres Einkaufserlebnis schaffen.

Die folgende Abbildung zeigt, wie Ihre Commerce-Daten von Ihrem Store zu anderen Adobe DX-Produkten fließen, wenn die [!DNL Data Connection] installiert und konfiguriert ist.

![Datenfluss zum Experience Platform Edge](assets/commerce-edge.png)

In der obigen Abbildung werden Ihre Verhaltens-, Back-Office- und Kundenprofildaten mithilfe einer SDK, einer API und eines Quell-Connectors an Experience Platform Edge gesendet. Sie müssen nicht vollständig verstehen, wie diese Teile funktionieren, da die Erweiterung die Komplexität der Datenfreigabe für Sie handhabt. Wenn sich die Ereignisdaten am Edge befinden, können Sie sie in nachgelagerten Adobe-DX-Produkten wie [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=de), [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=de), [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html?lang=de) und [Journey Optimizer &#x200B;](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=de). Geführte Beispiele finden Sie unter [Verwenden von Adobe Journey Optimizer zum Senden einer E-Mail zu einem Transaktionsabbruch](using-ajo.md) und [Erstellen einer Zielgruppe in Real-Time CDP mithilfe von Commerce-Ereignisdaten](create-audience.md).

## Zurückziehen von Experience Platform-Daten nach Commerce

Das Senden Ihrer Commerce-Daten an Experience Platform mithilfe der [!DNL Data Connection]-Erweiterung ist eine Seite der Datenfreigabefunktionen von Commerce. Die andere Seite, bei der es sich um eine optionale Erweiterung handelt, heißt [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html?lang=de). Mit dieser Erweiterung können Sie Zielgruppen in Real-Time CDP erstellen und diese Zielgruppen in Ihrem Commerce-Store bereitstellen, um über Warenkorbpreisregeln, zugehörige Produktregeln und dynamische Blöcke zu informieren.

Der Datenfluss von Ihrem Commerce-Store zum Experience Platform und zurück über die Audience Activation-Erweiterung sieht im Großen und Ganzen wie folgt aus:

![[!DNL Data Connection] Fluss](assets/data-connection.png)

Nachdem Sie die Verbindung zwischen Commerce zu Experience Platform und Experience Platform zu Commerce eingerichtet haben, fließen die Daten weiter. Sie müssen die Verbindung nicht erneut herstellen, es sei denn, dies wird durch ein Upgrade erforderlich.

## Konzepte

Für die Datenfreigabe zwischen diesen beiden Systemen müssen Sie mehrere Konzepte verstehen.

- **Datentypen** - [!DNL Data Connection] erfasst **Verhaltensdaten (Storefront)** aus dem Browser, **Backoffice**-Daten von Commerce-Servern und **Profil**-Daten. Die Admin beschriftet die Storefront-Sammlung **Storefront-Ereignisse**. Siehe [Typen von Commerce-Daten](data-ingestion.md) für die vollständige Taxonomie.

- **Verhaltensdaten (Storefront-Daten** - Werden aus Kundeninteraktionen auf der Site erfasst, z. B. `addToCart`, `pageView`, `startCheckout` und `completeCheckout`. Siehe [Storefront-](events.md#storefront-events).

- **Back-Office-Daten** - werden auf Commerce-Servern erfasst, einschließlich [Bestellstatus](events-backoffice.md#order-status) Ereignissen wie [`orderPlaced`](events-backoffice.md#orderplaced) und [`orderShipped`](events-backoffice.md#ordershipmentcompleted). Siehe [Back-Office-Ereignisse](events-backoffice.md).

- **Profildatensätze** - Momentaufnahmendaten, die gesendet werden, wenn ein Kundenprofil in Commerce erstellt wird. Siehe [Profildatensätze](events-profilerecord.md) und [Profildatensatzschema aktualisieren](profile-data.md).

- **Profilereignisse** - Zeitreihenereignisse für Änderungen des Profillebenszyklus auf dem Server. Siehe [Kundenprofil-Ereignisse](events-backoffice.md#customer-profile-events).

- **Experience Platform und Edge Network** - Das Data Warehouse für die meisten Adobe DX-Produkte. Daten, die an Experience Platform gesendet werden, werden über Experience Platform Edge Network an Adobe DX-Produkte weitergegeben. Sie können beispielsweise Journey Optimizer starten, Ihre spezifischen Commerce-Ereignisdaten vom Edge abrufen und in Journey Optimizer eine E-Mail zu einem Transaktionsabbruch erstellen. Journey Optimizer kann diese E-Mail dann senden, wenn sich im Commerce-Store Transaktionsabbrüche befinden. Weitere Informationen über die [Experience Platform und die Edge Network](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html?lang=de).

- **Schema** - Das Schema beschreibt die Struktur der gesendeten Daten. Bevor Experience Platform Ihre Commerce-Daten aufnehmen kann, müssen Sie ein Schema erstellen, das die Datenstruktur beschreibt und Einschränkungen für den Datentyp bereitstellt, der in den einzelnen Feldern enthalten sein kann. Schemata bestehen aus einer Basisklasse und keiner oder mehreren Schemafeldgruppen. Das Schema verwendet die XDM-Struktur, die alle Adobe DX-Produkte lesen können. Das Schema stellt sicher, dass an die Experience Platform gesendete Daten in allen DX-Produkten verstanden werden. Weitere Informationen zu [Schemata](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html?lang=de).

- **Dataset** - Ein Konstrukt zur Speicherung und Verwaltung von Daten, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben. Alle Daten, die erfolgreich in Adobe Experience Platform aufgenommen werden, sind in Datensätzen enthalten. Weitere Informationen zu [Datensätzen](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=de).

- **Datastream** - ID, die den Datenfluss von Adobe Experience Platform zu anderen Adobe DX-Produkten ermöglicht. Diese ID muss mit einer bestimmten Website innerhalb Ihrer spezifischen Adobe Commerce-Instanz verknüpft sein. Wenn Sie diesen Datenstrom erstellen, geben Sie das oben erstellte XDM-Schema an. Weitere Informationen zu [Datenströmen](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de).

## Unterstützte Architektur

Die [!DNL Data Connection]-Erweiterung ist auf den folgenden Architekturen verfügbar:

- PHP/Luma
- [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
- [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html?lang=de)

>[!BEGINSHADEBOX]

## Voraussetzungen

Um die [!DNL Data Connection]-Erweiterung verwenden zu können, müssen Sie über Folgendes verfügen:

- Adobe Commerce 2.4.4 oder neuer
- Adobe ID und Organisations-ID
- [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=de) der zum Erfassen von Storefront-Ereignisdaten erforderlich ist
- Berechtigungen für andere Adobe DX-Produkte.

>[!ENDSHADEBOX]

## Aktivieren der Erweiterung {#enable-extension}

Die Aktivierung der [!DNL Data Connection]-Erweiterung umfasst auf allgemeiner Ebene die folgenden Schritte:

1. [Installieren](install.md) der [!DNL Data Connection].
1. [Melden Sie sich bei &#x200B;](https://helpx.adobe.com/de/manage-account/using/access-adobe-id-account.html) Adobe-Konto an und [&#x200B; Sie Ihre Organisations](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de#concept_EA8AEE5B02CF46ACBDAD6A8508646255)ID an, um sie zu bestätigen. Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge gefolgt von `@AdobeOrg` (zwingend erforderlich).
1. Stellen Sie sicher[&#x200B; dass Sie über die Berechtigung für die Datenerfassung in Experience Platform &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html?lang=de).
1. Überprüfen Sie die [Datentypen](data-ingestion.md) die Sie erfassen und senden können.
1. Erstellen oder aktualisieren Sie Ihr [Zeitreihen](update-xdm.md)Ereignisschema oder [Profildatensatzdatenschema](profile-data.md) mit Commerce-spezifischen Feldergruppen.
1. [Erstellen eines Datensatzes](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=de#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema. Dieser Datensatz enthält die Commerce-Daten, die an Experience Platform Edge gesendet werden.
1. [Erstellen Sie einen Datenstrom](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
1. [Verbindung zu Commerce Services herstellen](../landing/saas.md).
1. [Verbindung zu Adobe Experience Platform herstellen](connect-data.md).

Der Rest dieses Handbuchs führt Sie durch alle diese Schritte, um sich mit der Leistungsfähigkeit von Adobe DX-Produkten in Ihrem Commerce-Store vertraut zu machen.

>[!NOTE]
>
>Entwickler von Mobilgeräten erfahren, wie [&#x200B; Adobe Experience Platform Mobile SDK &#x200B;](./mobile-sdk-epc.md) Commerce integrieren.

## HIPAA-Bereitschaft

Mit der [!DNL Data Connection]-Erweiterung können Sie [!DNL Commerce] Backoffice-Daten mit der Experience Platform teilen und die HIPAA-Konformität aufrechterhalten. [Weitere Informationen](hipaa-readiness.md).

## Zielgruppe

Dieses Handbuch richtet sich an Händler in Adobe Commerce, die ihren Commerce-Store erweitern und personalisieren möchten, um ihren Kunden ein noch besseres Einkaufserlebnis zu bieten.

## Support

Wenn Sie Informationen benötigen oder Fragen haben, die in diesem Handbuch nicht behandelt werden, verwenden Sie die folgenden Ressourcen:

- [Hilfezentrum](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=de){target="_blank"}
- [Support-Tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=de#submit-ticket){target="_blank"} — Senden Sie ein Ticket, um zusätzliche Hilfe zu erhalten.
