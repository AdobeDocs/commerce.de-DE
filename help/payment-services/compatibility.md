---
title: Kompatibilität für [!DNL Payment Services]
description: Erfahren Sie [!DNL Payment Services]  ob in Ihrem Land verfügbar ist und ob es mit Ihrer Adobe Commerce-Version kompatibel ist.
role: User
level: Intermediate
feature: Payments, Checkout, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---


# Kompatibilität für [!DNL Payment Services]

[!DNL Payment Services] ist für Adobe Commerce und Magento Open Source verfügbar. [!DNL Payment Services] ist jetzt mit Adobe Commerce Version 2.4.x kompatibel.

## Voraussetzungen

Um [!DNL Payment Services] zu verwenden, müssen Sie zunächst eine Verbindung mit Ihrer Commerce-Instanz herstellen. **Sie richten diese Verbindung nur einmal**.

1. Wenn Sie sich nicht sicher sind, ob Ihre Instanz verbunden ist, navigieren Sie zu **System** > Services > **Commerce Services Connector** und zeigen Sie die öffentlichen und privaten API-Schlüsselwerte in den Abschnitten Sandbox-Schlüssel und Produktionsschlüssel sowie die Felder Projekt und Datenraum im Abschnitt SaaS-Kennung an. Wenn diese Werte vorhanden sind, ist Ihre Instanz verbunden.

1. Wenn Sie weiterhin eine Verbindung mit Ihrer Instanz herstellen müssen, lesen Sie die Anweisungen auf der Seite [Commerce Services Connector](../landing/saas.md) .

   >[!TIP]
   >
   > Weitere Informationen finden Sie in unserem Tutorial-Video ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector) [Adobe Commerce Services Connector.

1. Wenn Sie Ihre Instanz bereits verbunden haben, navigieren Sie für die nächsten Schritte zur [Onboarding](onboard.md)-Seite.

>[!IMPORTANT]
>
> Alle Händler, die eine Berechtigung für [!DNL Payment Services] haben **können (einen Produktionsdatenbereich** und **zwei Testdatenbereiche** nutzen.

## Standard im Vergleich zu Advanced [!DNL Payment Services] Experience

[!DNL Payment Services] bietet **Standard** (Express-Checkout) und **Erweitert** (vollständig unterstützt) Zahlungsoptionen und Onboarding-Flüsse, je nach dem Land, in dem Sie tätig sind.

>[!NOTE]
>
> [!DNL Payment Services] bietet [Express-Checkout](../payment-services/payments-options.md) (eine Untergruppe von Zahlungsoptionen) für andere [verfügbare Länder beim Onboarding](../payment-services/production.md#complete-merchant-onboarding).

### Welche [!DNL Payment Services] ist die richtige für Sie?

>[!VIDEO](https://video.tv.adobe.com/v/3447811)

Siehe [Verbinden](connect.md) für weitere Informationen zum Einrichten der [!DNL Payment Services].

>[!BEGINTABS]

>[!TAB Standard (Express-Checkout)]

![check](assets/icon-check.png) PayPal Checkout

![check](assets/icon-check.png) PayPal Debit- oder Kreditkartenschaltfläche

![check](assets/icon-check.png) Benutzerdefinierte Checkout-Konfigurationen

![check](assets/icon-check.png) Standardpreise

![check](assets/icon-check.png) **Verfügbar in XX Ländern**

[![Weitere Informationen](assets/learn-more-button.svg)](onboard.md)

>[!TAB Erweitert (vollständig unterstützt)]

![check](assets/icon-check.png) Debitkarte

![check](assets/icon-check.png) PayPal-Guthaben

![Überprüfen](assets/icon-check.png) Kreditkartenfelder

![check](assets/icon-check.png) Apple Pay-Schaltfläche

![check](assets/icon-check.png) Google Pay-Schaltfläche

![check](assets/icon-check.png) PayPal-Zahlungsschaltflächen

![check](assets/icon-check.png) Venmo-Taste

![check](assets/icon-check.png) PayPal Debit- oder Kreditkartenschaltfläche

![check](assets/icon-check.png) Schaltfläche „Später bezahlen“

![check](assets/icon-check.png) Benutzerdefinierte Checkout-Konfigurationen

![check](assets/icon-check.png) Angepasste Preise

![check](assets/icon-check.png) (Preisfindungsfunktionen für L2/L3 - nur USA)

![check](assets/icon-check.png) **Nur verfügbar in USA, Kanada (CA), Australien (AUS). Frankreich (FR), Vereinigtes Königreich (UK)**

[![Weitere Informationen](assets/learn-more-button.svg)](onboard.md)

>[!ENDTABS]

Weitere Informationen zu Versionen [ Versionen ](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) versionsspezifischen Versionen finden Sie auf den [[!DNL Payment Services] Lebenszyklusrichtlinie](release-notes.md) und den Versionshinweisen .

Die vollständigen Anweisungen und den Start des Onboarding-Prozesses finden Sie unter [Erste Schritte mit [!DNL Payment Services]](onboard.md).

### Akzeptierte Kreditkarten und Währungen

[!DNL Payment Services] akzeptiert die Währungen der Länder [in denen es verfügbar ist](#availability). Weitere Informationen [ Einrichten von ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) finden Sie unter „Währungskonfiguration“.

Weitere Informationen zu den Währungen und Zahlungsmethoden, die mit PayPal-Produkten und -Services verfügbar sind, finden Sie auf den folgenden Seiten:

* [Dokumentation zu unterstützten Währungen](https://developer.paypal.com/docs/reports/reference/paypal-supported-currencies/).

* [Dokumentation zu Zahlungsmethoden](https://developer.paypal.com/docs/checkout/payment-methods/).
