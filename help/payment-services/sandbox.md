---
title: Einrichten der Test-Sandbox
description: Verwenden Sie ein PayPal-Sandbox-Konto, um  [!DNL Payment Services]  Testmodus zu verwenden.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
feature: Payments, Checkout, Configuration, Install, Paas, Saas
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '614'
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
   1. Klicken Sie im Abschnitt _[!UICONTROL Sandbox Accounts]_&#x200B;auf die drei Punkte in der Spalte&#x200B;_[!UICONTROL Manage accounts]_ für das von Ihnen erstellte Sandbox-Konto.
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

## Testen in Sandbox-Umgebung

Es wird dringend empfohlen, Testdatenräume für Integrations- und Staging-Umgebungen zu verwenden und Zahlungen in der Produktion mit echten Kreditkarten und Banken zu testen, bevor Sie diese Funktion Käufern bereitstellen.

Weitere Informationen [ Sie unter ](test-validate.md) und Validieren .
