---
title: Testen in der Staging-Umgebung
description: Erfahren Sie, wie Sie [!DNL Product Recommendations] aus Ihrer Produktionsumgebung in Ihrer Staging-Umgebung zu Testzwecken verwenden.
feature: Services, Recommendations, Staging
exl-id: 5b6d7615-6021-4419-98ea-006c8a299fe4
TQID: 'https://experienceleague.adobe.com/7e7e3T-vgkN-Pbqx6TwrBAWTEozhzS0h--tguOGe0yI'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: dec06508-d41f-555a-87e8-29e8bcdfa95a
    internal-label: Recommendations
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
    internal-label: Behavioral data
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: eb30f47f-d87a-400f-8f78-63ce7979ff56
    internal-label: Machine learning
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%
---
# Testen in der Staging-Umgebung

Bevor Sie Empfehlungen in Ihrer Produktionsumgebung bereitstellen, testen Sie den Service in einer Nicht-Produktionsumgebung, um sicherzustellen, dass alles erwartungsgemäß funktioniert.

[!DNL Product Recommendations] geben Produkte zurück, die auf [Käuferverhaltensdaten](events.md) basieren, die in Ihrer Storefront erfasst wurden. In einer produktionsfremden Umgebung liegen Ihnen jedoch wahrscheinlich keine Verhaltensdaten von Käufern vor. Der einzige Empfehlungstyp, den Sie ohne Verhaltensdaten testen können, ist `More like this`. Dieser Empfehlungstyp erfordert keine Eingabedaten, da er eine direkte Inhaltsähnlichkeits-Übereinstimmung verwendet.

Die folgenden Empfehlungstypen erfordern Verhaltensdaten:

- Am häufigsten angezeigt
- hat dieses angezeigt, hat Folgendes angezeigt
- Das kaufte ich, das kaufte ich

Wie können Ihre Empfehlungen in einer Nicht-Produktionsumgebung mithilfe von Verhaltensdaten getestet werden? Es gibt mehrere Möglichkeiten.

## Abrufen von Empfehlungen aus der Produktionsumgebung (empfohlen)

Mit Adobe Commerce können Sie Empfehlungen aus Ihrer Produktionsumgebung abrufen und in Ihrer Nicht-Produktionsumgebung in der Vorschau anzeigen, indem Sie [&#x200B; SaaS](settings.md)Datenbereich wechseln.

Um Empfehlungen aus Ihrer Produktionsumgebung abzurufen, müssen Sie Folgendes sicherstellen:

- Die Storefront-Datenerfassung ist [konfiguriert und aktiviert](install-configure.md) in der Produktionsumgebung.
- Der Katalog in Ihrer produktionsfremden Umgebung ist größtenteils identisch mit dem Katalog in der Produktionsumgebung. Durch die Verwendung ähnlicher Kataloge wird sichergestellt, dass die in den Empfehlungseinheiten zurückgegebenen Produkte denen in der Produktionsumgebung genau entsprechen.

## Generieren von Verhaltensdaten in einer Nicht-Produktionsumgebung

1. Stellen Sie das `magento/product-recommendations`-Modul in einer Nicht-Produktionsumgebung bereit, in der die Katalogdaten Ihrem Produktionskatalog ähnlich sind.

1. Verwenden Sie eine der Nicht-Produktions-Datenspeicher-IDs für [Konfiguration](../landing/saas.md#saas-configuration) im Admin-Bereich.

1. Erzeugen Sie die Daten selbst, indem Sie auf Ihre Storefront klicken, um das Verhalten der tatsächlichen Käufer nachzuahmen (oder erstellen Sie ein Automatisierungsskript). Durch Ihre Tests generieren Sie Verhaltensereignisse in Ihrer produktionsfremden Umgebung. Diese Ereignisse werden verwendet, um die Produktaffinitäten zu erzeugen, die Empfehlungen unterstützen. Zum Testen schlägt [!DNL Commerce] vor, mit den folgenden Empfehlungstypen zu interagieren:

   - Am häufigsten angezeigt - Erfordert minimale Eingabedaten. Benutzer müssen Produkte anzeigen.
   - Angezeigt, angezeigt durch : Erfordert, dass mehrere Benutzer mehrere Produkte anzeigen.
   - Haben gekauft, haben gekauft - Erfordert, dass mehrere Benutzer mehrere Produkte kaufen.

### Einschränkungen

- Die Verhaltens- und Katalogdaten aus dem produktionsfremden [SaaS-Datenraum](../landing/saas.md#saas-configuration) identifizieren eine isolierte Umgebung, in der die resultierenden Produktempfehlungen vollständig auf den Verhaltensdaten basieren, die in der zugehörigen Storefront generiert wurden.

- Da Sie nicht über große Mengen an Verhaltensdaten verfügen, sind die Eingabedaten für die Berechnung von Produktverknüpfungen spärlich. Diese Daten werden jedoch weiterhin an Sensei gesendet, um die Modelle für maschinelles Lernen zu berechnen und Empfehlungen auf der Grundlage der in dieser Umgebung generierten Daten bereitzustellen.
