---
title: Deutlicher Schutz vor Betrug
description: Automatisierten Betrugsschutz für mit Signifyd  [!DNL Payment Services] .
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security, Paas, Saas
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Deutlicher Schutz vor Betrug

Mit der Erweiterung „Signifyd[!DNL Payment Services] können Sie den automatischen Schutz vor Betrug für [&#128279;](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce unterstützt Signifyd-Versionen 5.4.0 und höher. [!DNL Payment Services] unterstützt Signifikante Flüsse vor und nach der Authentifizierung.

Die Signifyd/[!DNL Payment Services]-Integration bietet Abdeckung für Kreditkarten, Debitkarten, Tresorkarten, Checkout über den Admin sowie PayPal- und Apple-Zahlungsmethoden. Während einige Details der Transaktionen nicht zwischen Zahlungsdiensten und Signifid geteilt werden, bietet Signifid eine umfassende Risikoabdeckung für alle Zahlungsmethoden und gewährleistet so einen maximalen Schutz.

>[!CAUTION]
>
> [Fastlane](payments-options.md#fastlane-button) ist nicht mit Signifyd kompatibel.

Siehe [Signifyd-Dokumentation](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension), um mehr über die Installation und Konfiguration der Erweiterung zu erfahren.

## Onboarding

Sie müssen direkt mit Signifyd kommunizieren, um die Erweiterung für die Verwendung mit [!DNL Payment Services] zu integrieren - es ist keine [!DNL Payment Services] Konfiguration erforderlich. Sie können die Significed-Erweiterung in Admin konfigurieren, sobald sie installiert ist. Jede Unterstützung im Zusammenhang mit dieser Erweiterung wird von Signify verwaltet.

Beim Onboarding mit Signified müssen Sie:

1. Kontakt Angegeben, um ein neues Konto einzurichten.
1. Standardmäßig ist Signifyd [auf die Zulassungsliste gesetzt &#x200B;](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) um sicherzustellen, dass Signifyd keinen Trigger für andere Zahlungsoptionen erzeugt, die es derzeit nicht unterstützt. Wenn Sie eine bestimmte Zahlungsmethode verbieten möchten, müssen Sie Änderungen vornehmen.
1. Bestätigen Sie mit Signifyd, dass PayPal keine Bestellungen über die Betrugsschutzeinstellung des Händlers in PayPal zurückweist, die von Signifyd genehmigt werden könnten.
1. Aktivieren Sie die Signify-Erweiterung, um mit [!DNL Payment Services] kompatibel zu sein:
   * Bei Verwendung von [!DNL Payment Services] im _Live_-Modus muss sich SignifyID im Produktionsmodus befinden.
   * Bei Verwendung von [!DNL Payment Services] im _Sandbox_-Modus muss sich SignifyID im Testmodus befinden.

## Konfiguration

Da Signifyd einige Maßnahmen bei Ihren Bestellungen ergreift, ist es notwendig, die Erweiterung so zu konfigurieren, dass sie sich entsprechend der Zahlungsaktion verhält, die Sie für [!DNL Payment Services] festgelegt haben.

Diese Konfigurationsoptionen sind nicht mit den Zahlungsdiensten und der Signified-Integration kompatibel:

* Wenn [!DNL Payment Services] mit der `Authorize` Zahlungsaktion konfiguriert ist _und_ sich im `PostAuth` befindet, wobei die _[!UICONTROL Decline Guarantees]_&#x200B;Option auf **Gutschrift erstellen**&#x200B;gesetzt ist.

  Grund: [!DNL Payment Services] erstellt eine Autorisierungstransaktion, die Signify dann zurückerstatten versucht.


* [!DNL Payment Services] wird mit der `Authorize and Capture` Zahlungsaktion konfiguriert _und_ Signifyd befindet sich im `PostAuth`-Modus, wobei die _[!UICONTROL Decline Guarantees]_&#x200B;Option auf **Auftrag stornieren**.

  Grund: [!DNL Payment Services] erstellt eine Erfassungstransaktion, die Signifyd dann zu annullieren versucht.


Siehe Signifiyd-Dokumentation für Informationen [Konfigurieren der Erweiterung](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Siehe die Signifyd-Dokumentation [weitere Informationen zu den Auftrags-Workflows](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
