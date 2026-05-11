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
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 319
ht-degree: 0%

---

# Entwicklung für Produktempfehlungen-Admins

Produktempfehlungen sind ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, Umsätze steigern und die Kundenbindung steigern können. Produktempfehlungen werden in der Storefront in Form von Einheiten wie „Kunden, die dieses Produkt angesehen haben, haben es auch angesehen“, „Kunden, die dieses Produkt gekauft haben, haben auch gekauft“, „Empfohlen für Sie“ usw. angezeigt. Adobe Commerce-Produktempfehlungen basieren auf [Adobe AI](https://business.adobe.com/de/ai.html), das Algorithmen für künstliche Intelligenz und maschinelles Lernen verwendet, um eine gründliche Analyse der aggregierten Kundendaten durchzuführen. Wenn diese Daten mit Ihrem Commerce-Katalog kombiniert werden, ergeben sich für den Erstkäufer sehr ansprechende, relevante und personalisierte Erlebnisse.

>[!NOTE]
>
>Wenn Ihre Storefront mit PWA Studio implementiert wird, lesen Sie den Abschnitt [Dokumentation zu PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, lesen Sie das Benutzerhandbuch , um zu erfahren, wie Sie Produktempfehlungen in eine &quot;[&quot;-](headless.md) integrieren. Headless-Instanzen müssen Eventing implementieren, um den Arbeitsbereich Produktempfehlungen zu unterstützen.

## Architektonischer Überblick

Commerce Product Recommendations werden allgemein als SaaS bereitgestellt. Auf der Commerce-Seite befindet sich die Storefront, die die Layout-Vorlage „Event Collector“ und „Recommendations“ enthält, und das Backend, das die Daten-Services, das SaaS-Exportmodul und die Admin-Benutzeroberfläche umfasst. Adobe AI Intelligence-Services werden auf der SaaS-Seite genutzt.

![Architekturdiagramm für Produktempfehlungen](assets/arch-diag-sensei.svg)

Sobald die Empfehlungsmodule installiert und konfiguriert sind, beginnt Ihre Storefront mit der Erfassung von Verhaltensdaten. Adobe AI verarbeitet diese Verhaltensdaten zusammen mit Ihren Katalogdaten und berechnet Produktverknüpfungen, die vom Recommendations-Service genutzt werden. An dieser Stelle kann der Händler Produktempfehlungseinheiten direkt über die Admin-Benutzeroberfläche für seine Storefront erstellen, verwalten und bereitstellen.

## Nächste Schritte

Lesen Sie die folgenden Themen, um mit Produktempfehlungen zu beginnen:

- [Implementieren von Produktempfehlungen](implementation-workflow.md)

- [Installieren und Konfigurieren von Produktempfehlungen](install-configure.md)

- [Erstellen von Produktempfehlungen](create.md)
