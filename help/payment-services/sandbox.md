---
title: Einrichten der Test-Sandbox
description: Verwenden Sie ein PayPal-Sandbox-Konto, um  [!DNL Payment Services]  Testmodus zu verwenden.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
feature: Payments, Checkout, Configuration, Install, Paas, Saas
source-git-commit: 6727102c54e0ac81df289ecd66ec61156662b8b9
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# Einrichten der Test-Sandbox

Bevor Sie mit dem Sandbox-Onboarding beginnen, müssen Sie sich für ein kostenloses PayPal-Entwicklerkonto anmelden und sowohl Händler- (zum Onboarding) als auch Kundenkonten erstellen (zum Testen Ihres Checkouts). Sie können bei Bedarf mehrere Entwicklerkonten erstellen.

Mit einem PayPal-Sandbox-Konto können Sie [!DNL Payment Services] im Testmodus verwenden. PayPal erfordert, dass Sie ein vom PayPal-Entwicklerportal generiertes Geschäfts-Sandbox-Testkonto, eine E-Mail-Adresse und ein Passwort für das Sandbox-Onboarding verwenden. *Erstellen Sie während des Sandbox-Onboarding-Prozesses kein weiteres Konto.*

## Sandbox-Onboarding

So schließen Sie das Sandbox-Onboarding ab:

1. Navigieren Sie zur Seite [PayPal-Entwicklerkonto](https://developer.paypal.com/developer/accounts/).
1. Klicken Sie auf **[!UICONTROL Log in to Dashboard]** und melden Sie sich mit Ihrem vorhandenen PayPal Developer Portal-generierten Business-Sandbox-Testkonto an oder klicken Sie auf **Registrieren** um ein Konto zu erstellen.
1. Erstellen Sie ein PayPal-Sandbox-Konto:
   1. Navigieren Sie zu _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. Klicken Sie auf **[!UICONTROL Create account]**.

      Wenn Sie während des PayPal-Onboarding-Prozesses ein PayPal-Sandbox-Konto erstellt haben, müssen Sie [Ihre Onboarding-Sandbox zurücksetzen](#reset-your-sandbox-account) da Sie sonst Ihre E-Mail nicht verifizieren können.

   1. Wählen Sie **[!UICONTROL Business]** als Kontotyp aus und klicken Sie auf **[!UICONTROL Create]**.
   1. Klicken Sie im Abschnitt _[!UICONTROL Sandbox Accounts]_auf die drei Punkte in der Spalte_[!UICONTROL Manage accounts]_ für das von Ihnen erstellte Sandbox-Konto.
   1. Klicken Sie auf **[!UICONTROL View/edit account]**.

      ![PayPal - Sandbox-Konto anzeigen/bearbeiten](assets/onboarding-viewedit-sandbox.png){width="300" zoomable="yes"}

   1. Kopieren Sie die E-Mail-ID und das systemgenerierte Kennwort und speichern Sie sie zur späteren Verwendung.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Sandbox onboarding]**.

   Diese Option ist sichtbar, wenn Sie das Sandbox-Onboarding für [!DNL Payment Services] noch nicht abgeschlossen haben.

   Eine Sandbox-Händler-ID wird automatisch generiert und in [Einstellungen](configure-admin.md) eingefügt. Diese ID darf nicht geändert werden.

   Es wird ein PayPal-Fenster angezeigt, in dem Sie ein PayPal-Konto verbinden können, um mit der Annahme von Zahlungen zu beginnen.

1. Geben Sie die E-Mail-Adresse und das Passwort des PayPal-Sandbox-Kontos ein, das Sie in Schritt 3 generiert haben (nicht Ihre PayPal-Geschäftskontoinformationen), sowie Ihr Land oder Ihre Region.
1. Klicken Sie auf **[!UICONTROL Next]**.

   ![PayPal - PayPal-Konto für Zahlungen verbinden](assets/paypal-connectacct.png){width="300" zoomable="yes"}

1. Folgen Sie weiterhin dem PayPal-Fluss und verwenden Sie Ihre zuvor gespeicherten Sandbox-Kontoanmeldeinformationen.
1. Navigieren Sie in der _Admin_-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   Die Schaltfläche &quot;**[!UICONTROL Sandbox onboarding]**&quot; ist nicht mehr sichtbar, und es wird der Text „Sandbox-Zahlungen ausstehend“ angezeigt.

Wenn das Onboarding Ihrer PayPal-Sandbox genehmigt wurde, sollte eine Benachrichtigung angezeigt werden, die besagt, dass sich Ihr Zahlungssystem derzeit im Sandbox-Modus befindet und keine Live-Zahlungen verarbeitet.

>[!IMPORTANT]
>
>Wenn Sie die Einwilligung zur [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] zur Abwicklung Ihrer Zahlungen widerrufen (in Ihren PayPal-Kontoeinstellungen), können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services] bearbeitet werden. Auf Ihrer Zahlungsdienste-Startseite wird ein Warnhinweis zur widerrufenen Einwilligung angezeigt. Um den Warnhinweis zu schließen, klicken Sie auf **[!UICONTROL Do not show again]**.

### Sandbox-Konto zurücksetzen

Wenn Sie während des PayPal-Onboarding-Prozesses ein PayPal-Sandbox-Konto erstellt haben, müssen Sie Ihre Onboarding-Sandbox zurücksetzen, da Sie sonst Ihre E-Mail nicht verifizieren können.

So setzen Sie Ihr Sandbox-Konto zurück:

1. Klicken Sie auf **[!UICONTROL Reset sandbox]**. [Erstellen eines PayPal-Geschäfts-Sandbox-Kontos](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Klicken Sie auf **[!UICONTROL Sandbox onboarding]** und führen Sie die nächsten Schritte aus.

## Telefonnummer des Kontakts aktivieren

Mit der Telefonnummer des Kontakts können Sie die Telefonnummern des Kontakts abrufen, die PayPal von Ihren Kunden sammelt. PayPal sammelt immer Kontakt-Telefonnummern von PayPal-Kontoinhabern, um ihre Identität zu bestätigen und sie zu kontaktieren, um Probleme mit ihren Konten zu lösen oder ihre Erfüllungsprozesse abzuschließen. PayPal rät jedoch davon ab, Kontaktnummern direkt vom Händler zu verwenden, da dies negative Auswirkungen auf den Umsatz haben kann. Weitere Informationen finden [ in der Dokumentation ](https://www.sandbox.paypal.com/businessmanage/preferences/website)PayPal - Telefonnummern für Kontakte“.

Diese Funktion ist standardmäßig `off`. Wenn Sie diese Option aktivieren, können Store-Administratoren Telefonnummern sehen, wenn ein Kunde einen markenspezifischen Checkout-Fluss außerhalb der Checkout-Seite abschließt.

>[!IMPORTANT]
>
>Diese Einstellung gilt nicht für andere Checkout-Flüsse.

## Land des Käufers

In der Produktion verwendet PayPal die Geolokalisierung des Käufers, um zu bestimmen, welche Zahlungsmethoden in Checkout- und Express-Flüssen verfügbar sind. Da der Sandbox-Modus keine Geolokalisierung unterstützt, verwenden Sie die Konfiguration **Land des Käufers** um den Standort des Käufers zu simulieren und zu steuern, welche Zahlungsmethoden gerendert werden.

Diese Einstellung ist nützlich, um regionsspezifische Zahlungsmethoden wie Venmo (nur USA), Pay Later (USA und Großbritannien) oder [Lokale Zahlungsmethoden](payments-options.md#local-payment-methods) (Europa) zu testen, ohne ein VPN zu benötigen.

So konfigurieren Sie das Land des Käufers:

1. Navigieren Sie in _Admin_-Seitenleiste zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.

1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]** aus.

1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.

1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL General Configuration]_ .

1. Legen Sie **[!UICONTROL Method]** auf `Sandbox` fest.

1. Wählen Sie das gewünschte Land aus der Dropdown-Liste **[!UICONTROL Buyer's country]** aus.

1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.

>[!NOTE]
>
>Die **[!UICONTROL Buyer's country]** wird nur angezeigt, wenn die Methode auf `Sandbox` gesetzt ist. Dies hat keine Auswirkungen auf die Produktionsumgebungen.

## Testen in Sandbox-Umgebung

Es wird dringend empfohlen, Testdatenräume für Integrations- und Staging-Umgebungen zu verwenden und Zahlungen in der Produktion mit echten Kreditkarten und Banken zu testen, bevor Sie diese Funktion Käufern bereitstellen.

Weitere Informationen [ Sie unter ](test-validate.md) und Validieren .
