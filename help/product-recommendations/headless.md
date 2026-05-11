---
title: Headless
description: Erfahren Sie, wie  [!DNL Product Recommendations]  in eine Headless-Storefront integriert werden können.
exl-id: c40dac31-f87e-402a-ba50-e8aa4c1d66aa
TQID: https://experienceleague.adobe.com/J3qXs-SWuDCz7pQwzGm0VcOOFoU1QM2M4qwsTxxPwE8
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: f42e0a1a-0d79-488d-a83f-f2c30672b137
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c4147b6e-073b-4d3c-9ab1-d60f2f4434efid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 372
ht-degree: 0%

---

# Headless

Sie können [!DNL Product Recommendations] entweder mit [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) oder einer benutzerdefinierten Frontend-Technologie wie React oder Vue JS in eine Headless-Storefront integrieren.

Benutzerdefinierte und Headless-Integratoren sollten diese Anweisungen für Luma und PWA als Implementierungsvorschlag heranziehen. Es gibt viele Möglichkeiten, Produktempfehlungen in Headless-Lösungen zu implementieren. Diese Dokumentation deckt nicht alle Szenarien ab. Integratoren müssen das Entwickeln, Entwerfen und Testen für ihre -Implementierungen abdecken.

[!DNL Product Recommendations] benötigen [Verhaltens- und Katalogdaten](https://experienceleague.adobe.com/docs/commerce/product-recommendations/developer/development-overview.html) um zu funktionieren. Der Synchronisierungsprozess für Katalogdaten bleibt in einer Headless-Implementierung unverändert, für die Erfassung von Verhaltensdaten sind jedoch Änderungen erforderlich.

>[!NOTE]
>
>Headless-Instanzen müssen Eventing implementieren, um das Produktempfehlungs-Dashboard zu unterstützen.

Um [!DNL Product Recommendations] in eine Headless-Storefront zu integrieren, müssen Sie:

1. Senden Sie Verhaltensdaten an Adobe AI, um die Ergebnisse der Produktempfehlungen zu analysieren und zu berechnen. Sie können auch zusätzliche Daten senden, um Produktempfehlungen ([) ](workspace.md) aktivieren.

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

1. Wenn die Ereignisse ausgelöst werden, verwenden Sie den [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/), um die Ereignisse zu verarbeiten und an Adobe AI zu senden.

1. Nachdem die Verhaltensdaten erfasst wurden, können Sie [ Admin ](create.md)Erstellen[!DNL Product Recommendations].

1. Verwenden Sie [Recommendations SDK](https://developer.adobe.com/commerce/services/product-recommendations/), um die Empfehlungseinheiten aus der Storefront abzurufen. SDK gibt die erforderlichen Produktdaten zum Rendern der Empfehlungseinheiten auf einer Seite zurück.

1. Erfahren Sie, wie Sie mit der [`recommendations` GraphQL-Abfrage ](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) Informationen zu Produktempfehlungsblöcken für eine bestimmte SKU zurückgeben und vieles mehr.
