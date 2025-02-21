---
title: Entwicklung für Produktempfehlungen-Admins
description: Ein Überblick über die Architektur und Entwicklungsfunktionen von Product Recommendations.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Entwicklung für Produktempfehlungen-Admins

Produktempfehlungen sind ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, Umsätze steigern und die Kundenbindung steigern können. Produktempfehlungen werden in der Storefront in Form von Einheiten wie „Kunden, die dieses Produkt angesehen haben, haben es auch angesehen“, „Kunden, die dieses Produkt gekauft haben, haben auch gekauft“, „Empfohlen für Sie“ usw. angezeigt. Adobe Commerce-Produktempfehlungen basieren auf [Adobe Sensei](https://www.adobe.com/sensei.html), das Algorithmen für künstliche Intelligenz und maschinelles Lernen verwendet, um eine gründliche Analyse der aggregierten Kundendaten durchzuführen. Wenn diese Daten mit Ihrem Commerce-Katalog kombiniert werden, ergeben sich für den Erstkäufer sehr ansprechende, relevante und personalisierte Erlebnisse.

>[!NOTE]
>
>Wenn Ihre Storefront mit PWA Studio implementiert wird, lesen Sie den Abschnitt [Dokumentation zu PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, lesen Sie das Benutzerhandbuch , um zu erfahren, wie Sie Produktempfehlungen in eine &quot;[&quot;-](headless.md) integrieren. Headless-Instanzen müssen Eventing implementieren, um den Arbeitsbereich Produktempfehlungen zu unterstützen.

## Architektonischer Überblick

Commerce Product Recommendations werden allgemein als SaaS bereitgestellt. Auf der Commerce-Seite befindet sich die Storefront, die die Layout-Vorlage „Event Collector“ und „Recommendations“ enthält, und das Backend, das die Daten-Services, das SaaS-Exportmodul und die Admin-Benutzeroberfläche umfasst. Adobe Sensei Intelligence-Services werden auf der SaaS-Seite genutzt.

![Architekturdiagramm für Produktempfehlungen](assets/arch-diag-sensei.svg)

Sobald die Empfehlungsmodule installiert und konfiguriert sind, beginnt Ihre Storefront mit der Erfassung von Verhaltensdaten. Adobe Sensei verarbeitet diese Verhaltensdaten zusammen mit Ihren Katalogdaten und berechnet Produktverknüpfungen, die vom Recommendations-Service genutzt werden. An dieser Stelle kann der Händler Produktempfehlungseinheiten direkt über die Admin-Benutzeroberfläche für seine Storefront erstellen, verwalten und bereitstellen.

## Nächste Schritte

Lesen Sie die folgenden Themen, um mit Produktempfehlungen zu beginnen:

- [Implementieren von Produktempfehlungen](implementation-workflow.md)

- [Installieren und Konfigurieren von Produktempfehlungen](install-configure.md)

- [Erstellen von Produktempfehlungen](create.md)
