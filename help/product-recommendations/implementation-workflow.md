---
title: Implementierungs-Workflow
description: Erfahren Sie, wie Sie  [!DNL Product Recommendations]  erfolgreich in Ihrer Storefront implementieren.
exl-id: 4a784d04-8be6-473f-afb3-264af06c850a
source-git-commit: 458f34c45406db871ec61ff408aa624f163b6ee0
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Implementierungs-Workflow

[!DNL Product Recommendations] verwendet sowohl Verhaltens- als auch Katalogdaten:

- Verhalten - Daten aus der Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, Artikel, die einem Warenkorb hinzugefügt werden, und Käufe. Adobe Commerce und Adobe AI erfassen keine personenbezogenen Daten.

- Katalog : Produktmetadaten wie Name, Preis und Verfügbarkeit.

Bei der Installation des `magento/product-recommendations module` aggregiert Adobe AI die Verhaltens- und Katalogdaten und erstellt [!DNL Product Recommendations] für jeden Empfehlungstyp. Der [!DNL Product Recommendations]-Service stellt diese Empfehlungen dann in Ihrer Storefront bereit. Verwenden Sie den folgenden Workflow, um Produktempfehlungen in Ihrer Storefront zu implementieren:

>[!NOTE]
>
> Wenn Ihre Storefront mit PWA Studio implementiert wird, lesen Sie den Abschnitt [Dokumentation zu PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie, wie Sie [&#x200B; in &#x200B;](headless.md) Headless-Storefront [!DNL Product Recommendations] (integrieren) können.

## Workflow

1. **Bereitstellung der Datenerfassung in der Produktion**

   Für die Bereitstellung von [!DNL Product Recommendations] sind zwei [Datenquellen](type.md) Kataloge und Verhaltensdaten erforderlich. Da die Produktion die einzige Umgebung ist, in der die Aktionen Ihrer Kunden erfasst und analysiert werden, können Sie so früh wie möglich mit der Datenerfassung in der Produktion beginnen. [Erfahren Sie](events.md) wie Adobe AI Modelle für maschinelles Lernen trainiert, die zu qualitativ hochwertigeren Empfehlungen führen. Wenn Sie mit der Erfassung von Verhaltensdaten in der Produktion beginnen, können Sie [Empfehlungen abrufen](staging-environment.md#fetch-recommendations-from-production-environment-recommended) die auf diesen Produktionsdaten basieren, während Sie in Nicht-Produktionsumgebungen arbeiten. Anschließend können Sie mit verschiedenen Empfehlungen testen und experimentieren, die auf der Grundlage der in der Produktion erfassten echten Kundendaten berechnet werden.

   Um die Datenerfassung für die Produktion bereitzustellen, müssen [&#x200B; das &#x200B;](install-configure.md)-Modul installieren [!DNL Product Recommendations] konfigurieren, indem Sie einen [API-Schlüssel](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=de) bereitstellen.

   >[!TIP]
   >
   > Durch die Bereitstellung der Datenerfassung ändert sich weder das Erscheinungsbild Ihrer Storefront noch das Erlebnis Ihrer Kunden. Nur das Erstellen und Bereitstellen von Empfehlungseinheiten ändert das Kundenerlebnis in Ihrer Storefront. Stellen Sie sicher, dass Sie die Nicht-Produktionsumgebung testen, bevor Sie sie in der Produktion bereitstellen. Erstellen Sie außerdem keine Empfehlungseinheiten, bis Sie Ihre Vorlage anpassen. Siehe den nächsten Schritt.

1. **Passen Sie die Vorlage an Ihren Stil an**

   Ihre Storefront stellt Ihre Marke dar. Achten Sie daher darauf, die Vorlage für Produktempfehlungen an Ihr Site-Design anzupassen.

   >[!TIP]
   >
   > Durch Anpassen der Vorlage können Sie Ihr Stylesheet angeben, überschreiben, wo eine Empfehlungseinheit auf einer Seite angezeigt wird usw.

   Siehe [Anpassen](https://experienceleague.adobe.com/docs/commerce/product-recommendations/developer/customize.html?lang=de) in der Entwicklerdokumentation, um zu erfahren, wie Sie diesen Schritt durchführen.

1. **Testen von Recommendations in Ihrer produktionsfremden Umgebung**

   Es empfiehlt sich immer, eine neue Technologie in Ihrer produktionsfremden Umgebung zu testen, bevor Sie sie in der Produktion bereitstellen. Beim Testen von Recommendations in Ihrer produktionsfremden Umgebung können Sie verschiedene Empfehlungseinheitentypen, Positionierungen und Seiten verwenden. Sie können Empfehlungen auf der Grundlage von Verhaltensdaten abrufen, die bereits während des Tests in Ihrer produktionsfremden Umgebung in der Produktion erfasst wurden, sodass die Empfehlungsergebnisse auf dem Einkaufsverhalten der tatsächlichen Kunden basieren.

   >[!TIP]
   >
   > Stellen Sie sicher, dass der Katalog Ihrer produktionsfremden Umgebung weitgehend mit dem Katalog identisch ist, den Sie in der Produktionsumgebung haben. Durch die Verwendung ähnlicher Kataloge wird sichergestellt, dass die in den Empfehlungseinheiten zurückgegebenen Produkte die Produkte in der Produktion genau imitieren.

   Unter [Abrufen](staging-environment.md) von Verhaltensdaten aus Ihrer Produktionsumgebung erfahren Sie, wie Sie diesen Schritt abschließen.

1. **Erstellen und Bereitstellen von Recommendations für Ihre Produktions-Storefront**

   Nachdem Sie nun die Verhaltensdatenerfassung in der Produktion bereitgestellt, die Vorlage für Produktempfehlungen geändert und Empfehlungen mit dem tatsächlichen Käuferverhalten getestet haben, sind Sie bereit, den gesamten Code in die Produktion weiterzuleiten und Live[Produktempfehlungen &#x200B;](create.md) erstellen.
