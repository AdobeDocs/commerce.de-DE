---
title: Sicherheit und Compliance
description: Überprüfen Sie die Sicherheits- und Compliance-Anforderungen für Ihre Site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html?lang=de
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Sicherheit und Compliance

Die Sicherheit ist in [!DNL Payment Services] von größter Wichtigkeit, und es werden keine von der Private oder Payment Card Industry (PCI) regulierten Informationen über Ihre [!DNL Payment Services] weitergegeben.

## Commerce-Sicherheit

[!DNL Adobe Commerce] und [!DNL Magento Open Source] unterstützen verschiedene Sicherheitsfunktionen.

Siehe [Sicherheit](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/security){target="_blank"} im Core-Benutzerhandbuch, um die Best Practices für die Sicherheit zu überprüfen und zu erfahren, wie Sie Admin-Sitzungen und Anmeldeinformationen verwalten, CAPTCHA implementieren und Website-Einschränkungen verwalten.

## PCI-Compliance

Die Zahlungskartenbranche (Payment Card Industry, PCI) hat eine Reihe von Anforderungen für Unternehmen festgelegt, die Zahlungen per Kreditkarte über das Internet akzeptieren. Neben der Aufrechterhaltung einer sicheren Umgebung sind Händler, die mit Kreditkarteninformationen von Kunden umgehen, dafür verantwortlich, einige Standardrichtlinien zu erfüllen.

Weitere Informationen finden [&#x200B; unter &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-admin/start/compliance/payments/compliance-pci){target="_blank"} für PCI-Compliance .

Händler können einen [Selbstbewertungsfragebogen (SAQ) ausfüllen](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"} bei dem es sich um ein Selbstvalidierungstool zur Bewertung der Sicherheit von Karteninhaberdaten handelt.

### Kreditkartenfelder

Bei Kreditkartenfeldern werden keine PCI-regulierten Daten über Ihre Services weitergeleitet. Sie müssen diese Daten nicht speichern oder pflegen, was die Bedenken hinsichtlich der PCI-Compliance erheblich verringert.

### 3DS

PCI 3-D Secure (3DS) ermöglicht die Authentifizierung des Käufers bei seinem Kreditkartenaussteller bei Online-Kreditkartenkäufen. Diese zusätzliche Sicherheitsebene trägt dazu bei, Online-Betrug zu verhindern, und ist im Rahmen der EU-Compliance-Vorschriften erforderlich.

[!UICONTROL Payment Services] bietet 3DS-Funktionen, mit denen Händler die EU-Vorschriften einhalten und Kunden und Händler vor betrügerischen Aktivitäten in ihren Geschäften schützen können.

Wenn Sie ein Händler in der EU oder Großbritannien sind, für den die 3DS-Konformität erforderlich ist, müssen Sie 3DS (standardmäßig `Off`) im [Konfigurationsadministrator](configure-admin.md#credit-card-fields) manuell aktivieren.

>[!IMPORTANT]
>
>Die 3DS-Anforderung gilt für Transaktionen, bei denen sich das Unternehmen und die Bank des Karteninhabers im [Europäischen Wirtschaftsraum](https://www.efta.int/eea) (EWR) und in Großbritannien befinden. Händler in den Vereinigten Staaten benötigen kein 3DS, können es aber bei Bedarf für ihre Transaktionen aktivieren.

Bestellungen, die vom Händler-/Ladenpersonal für den Käufer aufgegeben werden, sind nicht mit 3DS-Compliance-Maßnahmen konfiguriert.

>[!MORELIKETHIS]
>
> * Siehe [3DS in Einstellungen](configure-admin.md#3ds) für weitere Informationen.
> * Weitere [&#x200B; zu bestimmten Kreditkarten für 3DS-Tests finden Sie &#x200B;](https://developer.paypal.com/docs/checkout/advanced/customize/3d-secure/test/) der PayPal-Entwicklerdokumentation unter „Testkarten“.

### Kartengewölbe

Wenn ein Käufer [tresor - oder „speichert“ - seine Kreditkarteninformationen](vaulting.md) für zukünftige Käufe in Ihren Geschäften werden nur minimale Kreditkarteninformationen mit dem Käufer geteilt (letzte vier Ziffern, Kartenablaufdatum und Kartenmarke). Kreditkartenangaben werden beim Zahlungsdienstleister gespeichert. Wenn eine Karte abläuft oder sie die gespeicherten Informationen nicht mehr benötigen, können sie dieses Token löschen, damit die Informationen vom Zahlungsdienstleister nicht mehr gespeichert werden.

Weitere Informationen [&#x200B; Sie unter &#x200B;](vaulting.md)Kreditkartenabwicklung).

### PayPal-Zahlungstasten

Mit PayPal-Zahlungs-Buttons werden keine PCI-regulierten Daten über Ihre Services weitergeleitet. Sie müssen diese Daten nicht speichern oder pflegen, was die Bedenken hinsichtlich der PCI-Compliance erheblich verringert.

Aus Sicherheitsgründen gibt PayPal die Rechnungsadresse beim Checkout nicht weiter - nur Land, E-Mail und Name werden verwendet. Optional können Sie den PayPal-Checkout Ihrer Website aktivieren, um die vollständige Rechnungsadresse zurückzugeben, indem Sie sich an PayPal wenden und einen Prüfprozess durchführen.

PayPal bietet auch einen integrierten Betrugsschutz, der maschinelles Lernen nutzt, um Sie bei der Betrugsbekämpfung zu unterstützen. Weitere Informationen finden Sie in der [&#x200B; zum &#x200B;](https://www.paypal.com/us/webapps/mpp/security/seller-protection) von PayPal.

## Schutz vor Betrug

Mit der Erweiterung „Signifyd[&#x200B; können Sie den automatischen Schutz vor Betrug für Zahlungs-Services &#x200B;](https://commercemarketplace.adobe.com/signifyd-module-connect.html). Weitere Informationen [&#x200B; Sie unter &#x200B;](fraud-protection.md)Signifikante Betrugssicherheit“.

PayPal bietet in der Entwicklerdokumentation weitere Optionen [Betrugsschutz](https://www.paypal.com/us/cshelp/article/what-is-fraud-protection-help1014){target=_blank}:

* Weitere [&#x200B; finden Sie unter &#x200B;](https://www.paypal.com/us/enterprise/fraud-protection-advanced#fraud-protection-advanced){target=_blank} für Betrug.
* Weitere Informationen [&#x200B; Sie unter &#x200B;](https://www.paypal.com/us/cshelp/article/what-is-chargeback-protection-help608){target=_blank}Chargeback-Schutz).
