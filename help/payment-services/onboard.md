---
title: an Bord [!DNL Payment Services]
description: Verbinden Sie Ihre -Instanz mit  [!DNL Payment Services] -Funktionalität, indem Sie einige Onboarding-Schritte ausführen.
role: User
level: Intermediate
feature: Payments, Checkout, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Onboard-[!DNL Payment Services]

Um mit der Verwendung von [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] zu beginnen, müssen Sie einige Onboarding-Schritte ausführen, um Ihre Instanz mit der Zahlungsfunktion zu verbinden.

## Onboarding-Fluss

Dieses Flussdiagramm zeigt den allgemeinen Prozess für das Onboarding von [!DNL Payment Services].

![Onboarding-Fluss](assets/onboarding-diagram.svg){width="600" zoomable="yes"}

>[!NOTE]
>
> Bei Adobe Commerce-Versionen 2.4.7 oder neuer können Sie den Schritt „Marketplace-Erweiterung“ überspringen, da [!DNL Payment Services] vorkonfiguriert verfügbar ist.

Nach Abschluss des Onboardings für Sandbox- oder Live-Zahlungen ist die Finanzberichterstattung über [!DNL Payment Services] in der Admin Console verfügbar.

Wenn sowohl Sandbox- als auch Live-Zahlungen integriert und aktiviert sind, können Sie einfach von der [!DNL Payment Services] aus zwischen diesen Modi wechseln.

## Voraussetzungen

Um [!DNL Payment Services] verwenden zu können, müssen alle abhängigen Module aktiviert sein und Folgendes für Ihre Instanz verfügbar sein:

* Services-Connector-Modul
* Dienste-ID-Modul
* API-Schlüssel

Die Dienste-Connector- und Dienste-ID-Module werden während der [ von automatisch  [!DNL Payment Services]](install.md).

Nach Abschluss der Installation wird in den Konfigurationseinstellungen (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) ein neuer Abschnitt angezeigt, wenn Sie **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**erweitern.

Informationen zum Erstellen oder Zugreifen auf API-Schlüssel finden Sie unter [API-Anmeldeinformationen](#obtain-api-credentials).

## Onboarding-Schritte

1. [Installieren der  [!DNL Payment Services] -Erweiterung](install.md#get-payment-services).
1. [API-Anmeldeinformationen abrufen](connect.md#obtain-api-credentials).
1. [Instanz mit ](connect.md#configure-commerce-services) Services von Commerce verbinden Diese Verbindung darf nur einmal pro Commerce-Instanz hergestellt werden.
1. [Richten Sie den Sandbox-](sandbox.md#enable-sandbox-testing) ein (oder fahren Sie alternativ mit [Aktivieren von Live-Zahlungen](sandbox.md#enable-live-payments) fort, wenn Sie die Funktionalität in einer anderen Umgebung getestet haben) mit einem PayPal-Zahlungsverarbeitungskonto.
1. [Als  [!DNL Payment Services]  festlegen](production.md#set-payment-services-as-payment-method) im Sandbox-Modus, um mit der Verarbeitung von Testzahlungen zu beginnen.
1. [Berechtigung für Zahlungen anfordern](production.md#request-payments-entitlement-from-adobe) um das Live-Onboarding zu aktivieren.
1. [Umfassendes Onboarding von Händlern](production.md#complete-merchant-onboarding), um Live-Zahlungen für Ihre Commerce-Websites zu aktivieren.
1. [Erhalten Sie Ihre  [!DNL Payment Services] -Händler-ID](production.md#configure-pricing-tier) und übergeben Sie sie an den Vertrieb, um die richtige Preisstufe zu konfigurieren.
1. [Aktivieren [!DNL Payment Services] im Live-Modus](production.md#enable-live-payments), um mit der Verarbeitung von Live-Zahlungen zu beginnen.
1. Testen Sie Zahlungen sowohl in [Sandbox](sandbox.md#test-in-sandbox-environment)- als auch [](production.md#test-in-production).

>[!NOTE]
>
>Wenn Sie Ihre Commerce-Services nicht im Admin-Bereich konfigurieren (Schritt 3), können Sie keine Sandbox- oder Live-Zahlungen einrichten.

## Fehlerbehebung

* [Fehlerbehebung [!DNL Payment Services] Installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [PayPal-Sandbox-Konto nicht verifiziert](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [Verzögerte [!DNL Payment Services] Berichtsdaten](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [Testkreditkarte schlägt mit PayPal bei der Verarbeitung von Zahlungen in einer Sandbox-Umgebung fehl](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
