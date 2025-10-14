---
title: Testen in der Staging-Umgebung
description: Erfahren Sie, wie  [!DNL Product Recommendations]  aus Ihrer Produktionsumgebung in Ihrer Staging-Umgebung zu Testzwecken verwenden können.
feature: Services, Recommendations, Staging
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '426'
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
