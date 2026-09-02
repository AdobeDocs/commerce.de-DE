---
title: Entwicklung für Produktempfehlungen-Admins
description: Ein Überblick über die Architektur und Entwicklungsfunktionen von Product Recommendations.
exl-id: 5967259e-c531-4fc7-9abd-cc18433fab33
TQID: https://experienceleague.adobe.com/DtPYY7DaB-A7-VyTeXkjL9Y2My-WOQx-9CD-TgrcTmk
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bbbea26f-9621-49eb-9ab8-e06fb3bbce8c
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
source-git-commit: 127067a1ef47c7d9e51c5792e03b568dd818fe8e
workflow-type: tm+mt
source-wordcount: 300
ht-degree: 0%

---

# Entwicklung für Produktempfehlungen-Admins

Produktempfehlungen sind ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, Umsätze steigern und die Kundenbindung steigern können. Produktempfehlungen werden in der Storefront in Form von Einheiten wie „Kunden, die dieses Produkt angesehen haben, haben auch dieses Produkt angesehen“, „Kunden, die dieses Produkt gekauft haben, haben auch gekauft“, „Empfohlen für Sie“ usw. angezeigt. [Adobe AI](https://business.adobe.com/ai.html) unterstützt Adobe Commerce Product Recommendations, das Algorithmen für künstliche Intelligenz und maschinelles Lernen verwendet, um eine umfassende Analyse aggregierter Kundendaten durchzuführen. Wenn diese Daten mit Ihrem Commerce-Katalog kombiniert werden, ergeben sich für den Erstkäufer sehr ansprechende, relevante und personalisierte Erlebnisse.

>[!NOTE]
>
>Wenn Ihre Storefront mit PWA Studio implementiert wird, lesen Sie den Abschnitt [Dokumentation zu PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Erfahren Sie, wie Sie Produktempfehlungen in eine [Headless](headless.md)-Umgebung integrieren können, wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden. Headless-Instanzen müssen Eventing implementieren, um den Arbeitsbereich Produktempfehlungen zu unterstützen.

## Architektonischer Überblick

Commerce Product Recommendations werden allgemein als SaaS bereitgestellt. Auf der Commerce-Seite befindet sich die Storefront, die die Layout-Vorlage „Event Collector“ und „Recommendations“ enthält, und das Backend, das die Daten-Services, das SaaS-Exportmodul und die Admin-Benutzeroberfläche umfasst. Adobe AI Intelligence-Services werden auf der SaaS-Seite genutzt.

![Architekturdiagramm für Produktempfehlungen](assets/arch-diag-sensei.svg)

Nach der Installation und Konfiguration ermöglichen es die Empfehlungsmodule Ihrer Storefront, Verhaltensdaten zu erfassen. Adobe AI kombiniert diese Daten mit Ihren Katalogdaten, um die vom Recommendations-Service verwendeten Produktverknüpfungen zu berechnen. Anschließend können Sie Einheiten für Produktempfehlungen direkt über die Admin-Benutzeroberfläche erstellen, verwalten und bereitstellen.

## Nächste Schritte

Lesen Sie die folgenden Themen, um mit Produktempfehlungen zu beginnen:

- [Implementieren von Produktempfehlungen](implementation-workflow.md)

- [Installieren und Konfigurieren von Produktempfehlungen](install-configure.md)

- [Erstellen von Produktempfehlungen](create.md)
