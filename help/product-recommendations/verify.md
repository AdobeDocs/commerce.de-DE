---
title: Ereignissammlung überprüfen
description: Erfahren Sie, wie Sie sicherstellen können, dass Verhaltensdaten an Adobe Commerce gesendet werden.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Ereignissammlung überprüfen

Nach [ (Installation und Konfiguration](install-configure.md) des `magento/product-recommendations` können Sie überprüfen, ob die Verhaltensdaten an Adobe Commerce gesendet werden. Sie können die in Chrome verfügbaren Entwickler-Tools verwenden oder die Snowplow Chrome-Erweiterung installieren. Weitere Hilfe finden Sie unter [Fehlerbehebung [!DNL Product Recommendations] Modul](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) in der Support Knowledge Base.

## Überprüfen mit Entwickler-Tools in Chrome

So stellen Sie sicher, dass die JS-Datei der Ereigniserfassung auf allen Seiten der Site geladen wird:

1. Wählen Sie in Chrome **Anpassen und steuern Sie Google Chrome** und wählen Sie dann **Weitere Tools** > **Entwickler-Tools**.
1. Wählen Sie die Registerkarte **Netzwerk** und dann den Typ **JS** aus.
1. Nach `ds.` filtern
1. Laden Sie die Seite neu.
1. In der Spalte **Name** sollte `ds.js` oder `ds.min.js` angezeigt werden.

![Event Collector JS](assets/filter-ds.png)
_Event Collector JS_

So stellen Sie sicher, dass Ereignisse auf Seiten Ihrer Site ausgelöst werden (Startseite, Produkt, Checkout usw.):

1. Stellen Sie sicher, dass Sie alle Anzeigenblocker in Ihrem Browser deaktivieren und Cookies auf der Website akzeptieren.
1. Wählen Sie in Chrome **Anpassen und steuern Sie Google Chrome** (die drei vertikalen Punkte in der oberen rechten Ecke des Browsers) und klicken Sie dann auf **Weitere Tools** > **Entwicklertools**.
1. Wählen Sie die Registerkarte **Netzwerk** und filtern Sie nach `tp2`.
1. Laden Sie die Seite neu.
1. Aufrufe unter `tp2` sollten in der Spalte **angezeigt**.

![Auslösen von Ereignissen](assets/filter-tp2.png)
_Überprüfen, ob Ereignisse ausgelöst werden_

## Überprüfen mit der Snowplow Chrome-Erweiterung

Installieren Sie die [Snowplow Analytics Debugger-Erweiterung für Chrome](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). Diese Erweiterung zeigt die Ereignisse an, die erfasst und an Adobe Commerce gesendet werden.

1. Stellen Sie sicher, dass Sie alle Anzeigenblocker in Ihrem Browser deaktivieren und Cookies auf der Website akzeptieren.

1. Wählen Sie in Chrome **Anpassen und steuern Sie Google Chrome** (die drei vertikalen Punkte in der oberen rechten Ecke des Browsers) und klicken Sie dann auf **Weitere Tools** > **Entwicklertools**.

1. Wählen Sie die Registerkarte **Snowplow Analytics Debugger**.

1. Wählen Sie in **Spalte** Ereignis“ **Strukturiertes Ereignis** aus.

1. Scrollen Sie nach unten, bis Sie **Kontextdaten (_)_**. Suchen Sie im **Schema**&#x200B;nach der Storefront-Instanz.

1. Stellen Sie sicher, dass [SaaS-Datenspeicher-ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) korrekt eingestellt ist.

![Schneepflugfilter](assets/snowplow-filter.png)
_Schneepflugfilter_

>[!NOTE]
>
> Der Wert `Data validity : NOT FOUND` im Debugger zeigt ein internes Schema an. Das Snowplow Chrome-Plug-in kann die Ereignisse nicht mit einem internen Schema validieren. Dies hat keine Auswirkungen auf die tatsächliche Funktionalität.

## Überprüfen, ob Ereignisse korrekt ausgelöst werden

Um sicherzustellen, dass die für Metriken verwendeten Ereignisse korrekt ausgelöst werden, suchen Sie im Snowplow Analytics-Debugger nach den Ereignissen `impression-render`, `view` und `rec-click` . Siehe die [vollständige Liste der Ereignisse](https://experienceleague.adobe.com/docs/commerce/product-recommendations/developer/events.html).

>[!NOTE]
>
> Wenn [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Adobe Commerce keine Verhaltensdaten, bis der Käufer einwilligt. Wenn der Cookie-Einschränkungsmodus deaktiviert ist, werden standardmäßig Verhaltensdaten erfasst.
