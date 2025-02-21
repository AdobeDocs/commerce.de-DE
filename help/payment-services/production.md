---
title: Für  [!DNL Payment Services]  aktivieren
description: Schließen Sie den Onboarding-Prozess ab, indem Sie  [!DNL Payment Services]  für die Produktion aktivieren.
feature: Payments, Checkout, Configuration, Install
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# [!DNL Payment Services] für Produktion aktivieren

Sie können den Service in die Produktion aufnehmen und den [Onboarding-Prozess](onboard.md) gemäß den Schritten in diesem Thema abschließen, nachdem Sie:

* [Installieren](install.md) der Payment Services-Erweiterung
* [Konfigurieren und Verbinden](connect.md) Ihrer Instanz
* [Einrichten](sandbox.md) und [Testen](test-validate.md) Ihrer Sandbox

## [!DNL Payment Services] als Zahlungsmethode festlegen

Nachdem Sie [Commerce-Services konfiguriert](connect.md#configure-commerce-services) und entweder [Sandbox-Tests](sandbox.md#enable-sandbox-testing) oder [Live-](#enable-live-payments) aktiviert haben, müssen Sie [!DNL Payment Services] als Zahlungsmethode festlegen.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Enable Payment Services]**.

   Diese Option ist sichtbar, wenn Sie [!DNL Payment Services] noch nicht als Zahlungsmethode für eine oder mehrere Ihrer Websites konfiguriert haben.

   Sie gelangen in den Einstellungsbereich der Startansicht mit den entsprechenden erweiterten Optionen (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), wo Sie die [!DNL Payment Services] als [Zahlungsmethode“ ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods){target="_blank"} können.

1. Legen Sie in _[!UICONTROL General Configuration]_**[!UICONTROL Enable]**auf `Yes` fest.
1. Legen Sie **[!UICONTROL Payment Action]** sowohl für _[!UICONTROL Credit Card Fields]_als auch für_[!UICONTROL PayPal payment buttons]_ auf einen der folgenden Werte fest:

   | Einstellung | Beschreibung |
   |---|---|
   | `Authorize` | Genehmigt den Kauf und hält die Mittel zurück. Der Betrag wird erst abgehoben, wenn er vom Händler „eingezogen“ wurde. |
   | `Authorize and Capture` | Genehmigt den Kauf und der Händler „erfasst“ die Gelder. |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] unterstützt partielle Aufnahmen. Ein Händler kann Teile einer Bestellung teilweise erfassen (Rechnung). Sie können beispielsweise jedes Element einzeln erfassen oder jetzt ein Element und den Rest später.

1. Klicken Sie auf **[!UICONTROL Save]**.
1. Klicken Sie auf **[!UICONTROL Go to Payment Services]** , um zur [!DNL Payment Services]-Startseite zurückzukehren.
1. [Leeren Sie den Cache](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   Das Löschen sollte nach jeder Konfigurationsänderung erfolgen.

Weitere Informationen [ Konfigurieren von Kreditkartenfeldern und PayPal](settings.md)Zahlungs-Buttons finden Sie unter „Konfigurieren von Zahlungsdiensten“.

## Umfassendes Onboarding von Händlern

Der nächste Schritt bei der Aktivierung Ihrer Stores mit Payment Services besteht darin, das Live-Onboarding abzuschließen.

Payment Services bietet [**Erweiterte** (vollständig unterstützte) und **Standard** (Express-Checkout) Zahlungsoptionen ](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) Onboarding-Flüsse, je nach dem Land, in dem Sie tätig sind, und Ihrem bevorzugten Zahlungserlebnis.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Live onboarding]**.

   Diese Option ist sichtbar, wenn Sie das Live-Onboarding für [!DNL Payment Services] noch nicht abgeschlossen haben.

1. Wählen _im Modal „Land_&quot; das Land aus, von dem aus Sie tätig sind.

   Payment Services bietet vollständige Unterstützung für alle Zahlungsoptionen in [fünf ](../payment-services/overview.md#availability). Payment Services bietet Express Checkout-Funktionen (eine Untergruppe von Zahlungsoptionen) für alle anderen Länder, die in der Länderliste dargestellt sind.

   Das Land, das Sie aus der Liste auswählen, bestimmt die Zahlungsoptionen, und der Onboarding-Ablauf - [Erweitert](#advanced-onboarding) (vollständig unterstützt) oder [Standard](#standard-onboarding) (Express-Checkout) - steht Ihnen zur Verfügung.

>[!TIP]
>
> Sobald Sie sich für eine Onboarding-Option entschieden haben und mit ihr fortfahren - Standard oder Erweitert -, müssen Sie das Onboarding erneut abschließen, um ein Upgrade oder ein Downgrade von Ihrer ursprünglichen Auswahl durchzuführen.

### Erweitertes Onboarding

Dieser Onboarding-Fluss ist für Händler in ([ unterstützten Ländern) ](../payment-services/overview.md#availability).

Nachdem das Land ausgewählt wurde:

1. Wählen Sie im angezeigten Modal die Option **Erweitert** aus.

   Für die Option **Standard** fahren Sie mit dem [Standard-Onboarding-Ablauf](#standard-onboarding) fort.

1. Klicken Sie **Weiter**.
1. Fahren Sie mit dem PayPal-Fluss für das vollständig unterstützte erweiterte Onboarding fort und verwenden Sie Ihre PayPal-Kontoanmeldeinformationen (nicht Ihre Sandbox-Kontoanmeldeinformationen) _oder_ melden Sie sich für ein neues PayPal-Konto an.

>[!IMPORTANT]
>
>**Erweitertes Onboarding** erfordert, dass Händler [Zahlungsansprüche anfordern](#request-payments-entitlement-from-adobe) um Live-Onboarding zu aktivieren.

### Standard-Onboarding

Dieser standardmäßige Onboarding-Ablauf ist für Händler in Ländern verfügbar, für die [nur Express-Checkout-](../payment-services/overview.md#availability)) bereitgestellt wird.

Nachdem das Land ausgewählt wurde:

1. Klicken Sie im modalen Fenster _Payment Services Agreement_ auf den Link **Payment Services Agreement**, um die Adobe Commerce Payment Services Agreement anzuzeigen.
1. Klicken Sie im Modal _Payment Services Agreement_ auf **I Accept**.
1. Fahren Sie mit dem PayPal-Fluss für das Express-Checkout-Onboarding fort und verwenden Sie Ihre PayPal-Kontoanmeldeinformationen (nicht Ihre Sandbox-Kontoanmeldeinformationen) oder melden Sie sich für ein neues PayPal-Konto an.

>[!IMPORTANT]
>
>[Apple-Pay- und -Kreditkartenfelder](../payment-services/payments-options.md) sind für das **Standard-Onboarding“ nicht**.

## E-Mail-Adresse bestätigen

1. Navigieren Sie in der Admin -Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   Die Schaltfläche &quot;_[!UICONTROL Live onboarding]_&quot; ist nicht mehr sichtbar, und es wird ein Textfeld &quot;[!UICONTROL Live payments pending]&quot; angezeigt.

   In diesem Textfeld werden Sie möglicherweise auch aufgefordert, Ihre E-Mail-Adresse mit PayPal zu bestätigen, um das Onboarding abzuschließen.

1. Wenn Sie aufgefordert werden, Ihre E-Mail-Adresse zu bestätigen, überprüfen Sie Ihre E-Mail auf die von PayPal gesendete Bestätigungsnachricht und klicken Sie, um Ihre E-Mail-Adresse zu bestätigen.
1. Navigieren Sie in der Admin -Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Aktualisieren Sie Ihr Browser-Fenster.

   Wenn das Onboarding eines PayPal-Händlers genehmigt wurde, sollte eine Benachrichtigung angezeigt werden, die angibt, dass sich Ihr Zahlungssystem im Sandbox-Modus befindet und keine Live-Zahlungen verarbeitet.

   >[!IMPORTANT]
   >
   >Wenn Sie die Einwilligung zur [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] zur Abwicklung Ihrer Zahlungen widerrufen (in Ihren PayPal-Kontoeinstellungen), können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services] bearbeitet werden. Auf Ihrer Zahlungsdienste-Startseite wird ein Warnhinweis zur widerrufenen Einwilligung angezeigt.

## Zahlungsansprüche von Adobe anfordern

Um Ihre Stores aktivieren zu können, fordern Sie Zahlungsberechtigungen von Adobe an (nur für [ Onboarding](#advanced-onboarding)):

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Get Live Payments]** in Ihrer [!DNL Payment Services].

   ![Anfordern von Berechtigungen](assets/request-entitlements.png){width="500" zoomable="yes"}

1. Füllen Sie das Formular aus.
1. Ein Mitglied des Vertriebsteams wird sich mit Ihnen in Verbindung setzen.

Alternativ können Sie die Zahlungsansprüche von Adobe unter [business.adobe.com](https://business.adobe.com/resources/payment-services.html) anfordern.

>[!IMPORTANT]
>
>**Live-Onboarding** ist erst verfügbar, nachdem die Zahlungsansprüche genehmigt wurden.

## Preisstufe konfigurieren

[!DNL Payment Services] abrufen _Händler-ID_:

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie in der Startansicht auf **[!UICONTROL Settings]**. Siehe [Startseite](payments-home.md) für weitere Informationen.
1. Wählen Sie die erforderliche _Händler-ID_ aus und senden Sie sie an Ihren Kundenbetreuer, der die richtige Preisstufe konfiguriert.

Weitere Informationen [ Zahlungsvorgänge finden Sie unter ](levels-card-payment-transactions.md) 2 und 3.

## Live-Zahlungen aktivieren

Eine _Produktions-Händler_ ID) wird automatisch generiert und in der [Konfiguration“ ](configure-admin.md). Diese ID darf nicht geändert werden.

Live-Zahlungen aktivieren:

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf der Startseite oben rechts auf der Seite auf **[!UICONTROL Settings]** . Siehe [Startseite](payments-home.md) für weitere Informationen.
1. Legen Sie im Abschnitt _[!UICONTROL General Configuration]_**[!UICONTROL Payment mode]**auf `Production` fest.
1. Klicken Sie auf **[!UICONTROL Save]**.
1. [Leeren Sie den Cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management){target="_blank"}.

   >[!IMPORTANT]
   >
   >Wenn Sie Ihren Cache nicht löschen, können Kunden die PayPal-Zahlungsoptionen während des Checkouts nicht sehen.

Wenn Sie zurück zur Startseite [!DNL Payment Services], wird die Sandbox-Zahlungsmodusmeldung nicht mehr angezeigt, da Sie jetzt Live-Zahlungen verarbeiten.

Siehe [Konfigurieren von in der Admin](configure-admin.md) für die Optionen für die Legacy-Konfiguration.

>[!IMPORTANT]
>
>Wenn Sie die Einwilligung zur [!DNL Payment Services] für die Abwicklung Ihrer Zahlungen widerrufen (in Ihren PayPal-Kontoeinstellungen), können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services] bearbeitet werden. Wenn Sie die Zahlungsverarbeitung wieder aktivieren möchten, müssen Sie das Onboarding erneut abschließen. Auf Ihrer Zahlungsdienste-Startseite wird ein Warnhinweis zur widerrufenen Einwilligung angezeigt.

## Test in Produktion

Es wird dringend empfohlen, Zahlungen in der Produktion mit echten Kreditkarten und Banken zu testen, bevor Sie diese Funktion Käufern offenlegen.

Weitere Informationen [ Sie unter ](test-validate.md) und Validieren .
