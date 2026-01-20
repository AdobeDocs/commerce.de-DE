---
title: Entwicklung für Produktempfehlungen-Admins
description: Ein Überblick über die Architektur und Entwicklungsfunktionen von Product Recommendations.
exl-id: 5967259e-c531-4fc7-9abd-cc18433fab33
source-git-commit: 458f34c45406db871ec61ff408aa624f163b6ee0
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Entwicklung für Produktempfehlungen-Admins

Produktempfehlungen sind ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, Umsätze steigern und die Kundenbindung steigern können. Produktempfehlungen werden in der Storefront in Form von Einheiten wie „Kunden, die dieses Produkt angesehen haben, haben es auch angesehen“, „Kunden, die dieses Produkt gekauft haben, haben auch gekauft“, „Empfohlen für Sie“ usw. angezeigt. Adobe Commerce-Produktempfehlungen basieren auf [Adobe AI](https://business.adobe.com/ai.html), das Algorithmen für künstliche Intelligenz und maschinelles Lernen verwendet, um eine gründliche Analyse aggregierter Kundendaten durchzuführen. Wenn diese Daten mit Ihrem Commerce-Katalog kombiniert werden, ergeben sich für den Erstkäufer sehr ansprechende, relevante und personalisierte Erlebnisse.

>[!NOTE]
>
>Wenn Ihre Storefront mit PWA Studio implementiert wird, lesen Sie den Abschnitt [Dokumentation zu PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, lesen Sie das Benutzerhandbuch , um zu erfahren, wie Sie Produktempfehlungen in eine &quot;[&quot;-](headless.md) integrieren. Headless-Instanzen müssen Eventing implementieren, um den Arbeitsbereich Produktempfehlungen zu unterstützen.

## Architektonischer Überblick

Commerce Product Recommendations werden allgemein als SaaS bereitgestellt. Auf der Commerce-Seite befindet sich die Storefront, die die Layout-Vorlage „Event Collector“ und „Recommendations“ enthält, und das Backend, das die Daten-Services, das SaaS-Exportmodul und die Admin-Benutzeroberfläche umfasst. Adobe AI Intelligence Services werden auf der SaaS-Seite genutzt.

![Architekturdiagramm für Produktempfehlungen](assets/arch-diag-sensei.svg)

Sobald die Empfehlungsmodule installiert und konfiguriert sind, beginnt Ihre Storefront mit der Erfassung von Verhaltensdaten. Adobe AI verarbeitet diese Verhaltensdaten zusammen mit Ihren Katalogdaten und berechnet Produktzuordnungen, die vom Recommendations-Service genutzt werden. An dieser Stelle kann der Händler Produktempfehlungseinheiten direkt über die Admin-Benutzeroberfläche für seine Storefront erstellen, verwalten und bereitstellen.

## Nächste Schritte

Lesen Sie die folgenden Themen, um mit Produktempfehlungen zu beginnen:

- [Implementieren von Produktempfehlungen](implementation-workflow.md)

- [Installieren und Konfigurieren von Produktempfehlungen](install-configure.md)

- [Erstellen von Produktempfehlungen](create.md)
