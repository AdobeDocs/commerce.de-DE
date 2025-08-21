---
title: Headless
description: Erfahren Sie, wie  [!DNL Product Recommendations]  in eine Headless-Storefront integriert werden können.
exl-id: c40dac31-f87e-402a-ba50-e8aa4c1d66aa
source-git-commit: 1548b7e11249febc2cd8682581616619f80c052f
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Headless

Sie können [!DNL Product Recommendations] entweder mit [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) oder einer benutzerdefinierten Frontend-Technologie wie React oder Vue JS in eine Headless-Storefront integrieren.

Benutzerdefinierte und Headless-Integratoren sollten diese Anweisungen für Luma und PWA als Implementierungsvorschlag heranziehen. Es gibt viele Möglichkeiten, Produktempfehlungen in Headless-Lösungen zu implementieren. Diese Dokumentation deckt nicht alle Szenarien ab. Integratoren müssen das Entwickeln, Entwerfen und Testen für ihre -Implementierungen abdecken.

[!DNL Product Recommendations] benötigen [Verhaltens- und Katalogdaten](https://experienceleague.adobe.com/docs/commerce/product-recommendations/developer/development-overview.html?lang=de) um zu funktionieren. Der Synchronisierungsprozess für Katalogdaten bleibt in einer Headless-Implementierung unverändert, für die Erfassung von Verhaltensdaten sind jedoch Änderungen erforderlich.

>[!NOTE]
>
>Headless-Instanzen müssen Eventing implementieren, um das Produktempfehlungs-Dashboard zu unterstützen.

Um [!DNL Product Recommendations] in eine Headless-Storefront zu integrieren, müssen Sie:

1. Senden Sie Verhaltensdaten an Adobe Sensei, um die Ergebnisse der Produktempfehlungen zu analysieren und zu berechnen. Sie können auch zusätzliche Daten senden, um Produktempfehlungen ([) ](workspace.md) aktivieren.

1. Rufen Sie Ergebnisse von Produktempfehlungen ab und rendern Sie diese Ergebnisse auf der Seite.

Sie können diese beiden Aktionen mit den verfügbaren SDKs ausführen, wie im folgenden Workflow beschrieben.

1. [Installieren](install-configure.md) Sie das [!DNL Product Recommendations].

1. Installieren und verwenden Sie die [Adobe Commerce Storefront Event SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) zum Auslösen der [Verhaltensereignisse](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations).

   Die minimal erforderlichen Ereignisse, um [!DNL Product Recommendations] Ergebnisse zurückzugeben:

   | Ereignis | Kategorie |
   |--- | ---|
   | `view` | Produkt |
   | `add-to-cart` | Produkt |
   | `place-order` | Auschecken |

   Um [Metriken-Reporting](workspace.md) zu aktivieren, sind die folgenden zusätzlichen Ereignisse erforderlich:

   | Ereignis | Kategorie |
   |--- | ---|
   | `impression-render` | Empfehlungseinheit |
   | `view` | Empfehlungseinheit |
   | `rec-click` | Empfehlungseinheit |
   | `rec-add-to-cart-click` | recommendation-unit (wenn in der Recommendations-Vorlage die Schaltfläche „Zum Warenkorb hinzufügen“ vorhanden ist) |

1. Wenn die Ereignisse ausgelöst werden, verwenden Sie den [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/), um die Ereignisse zu verarbeiten und an Adobe Sensei zu senden.

1. Nachdem die Verhaltensdaten erfasst wurden, können Sie [ Admin ](create.md)Erstellen[!DNL Product Recommendations].

1. Verwenden Sie [Recommendations SDK](https://developer.adobe.com/commerce/services/product-recommendations/), um die Empfehlungseinheiten aus der Storefront abzurufen. SDK gibt die erforderlichen Produktdaten zum Rendern der Empfehlungseinheiten auf einer Seite zurück.

1. Erfahren Sie, wie Sie mit der [`recommendations` GraphQL-Abfrage ](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) Informationen zu Produktempfehlungsblöcken für eine bestimmte SKU zurückgeben und vieles mehr.
