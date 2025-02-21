---
title: Handhabung von Cookie-Einschränkungen
description: Erfahren Sie, wie Produktempfehlungen mit Cookie-Einschränkungen umgehen.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Handhabung von Cookie-Einschränkungen

Sowohl Adobe Commerce als auch Magento Open Source bitten um Zustimmung, bevor Daten in Browser-Cookies gespeichert werden. Weitere Informationen finden Sie unter [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

Wenn Sie das `magento/product-recommendations` Modul für die Produktion bereitstellen, beginnt es mit der Erfassung von Shopper Interaction-Ereignissen in Ihrer Storefront. Da Daten für diese Ereignisse in Browser-Cookies oder im lokalen Speicher gespeichert werden können, unterstützt die Funktion den Cookie-Beschränkungsmodus, da Ereignisse erst dann erfasst werden, wenn der Käufer seine Cookie-Zustimmung erteilt hat.

Dies funktioniert möglicherweise nicht mit Einverständnislösungen für Drittanbieter-Cookies. Es liegt in der Verantwortung jedes Händlers sicherzustellen, dass die Datenerfassung nicht erfolgt, bevor eine Cookie-Zustimmung erteilt wurde, wie dies oft gesetzlich vorgeschrieben ist. Wenn Sie das Cookie-Einverständnis mit benutzerdefiniertem Code verwalten, können Sie ein Do-Not-Tracking-Cookie namens `mg_dnt` verwenden, um die Datenerfassung einzuschränken.

- Name des Cookies:

  ```text
  `const DNT_COOKIE = "mg_dnt";`
  ```

- Setzen Sie das Do-Not-Track-Cookie, um die Datenerfassung zu deaktivieren:

  ```text
  `$.mage.cookies.set(DNT_COOKIE, true);`
  ```

- So löschen Sie das Cookie, wenn der Benutzer Cookies akzeptiert hat:

  ```text
  `$.mage.cookies.clear(DNT_COOKIE);`
  ```
