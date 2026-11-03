---
title: Fehlerbehebung [!DNL App Management]
description: Beheben Sie häufige Probleme bei der Programmzuordnung, -installation, -konfiguration und -upgrades.
feature: App Builder, Extensibility, Integration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 72863f3c-9d27-5dda-afe1-d9f934b1fba0
    internal-label: Extensibility
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
subfeature_v2:
  - id: a743e5dc-8f37-4b5d-a848-03c32ca30598
    internal-label: App Builder
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: a00b9e1654a572e1773b5b7e321683332882d86f
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%
---
# Fehlerbehebung [!DNL App Management]

Verwenden Sie die folgenden Lösungen, um häufige Probleme bei der Programmzuordnung, Installation, Konfiguration und Aktualisierung zu beheben.

## Vor der Kontaktaufnahme mit dem Anwendungsanbieter

Führen Sie die folgenden Schritte für Ihr Problem aus. Wenn Sie Hilfe von Ihrem App-Entwickler oder -Anbieter benötigen, sammeln Sie die folgenden Informationen:

* App-Name und installierte Version, sofern verfügbar unter **[!UICONTROL Manage]** > **[!UICONTROL Details]** auf der App-Karte.
* Betroffene Commerce-Instanz und Adobe-Organisation.
* Fehlgeschlagener Vorgang, z. B. Installation oder Upgrade, und fehlgeschlagener Schritt.
* Angezeigte Fehlermeldung und Screenshot des Fehlers, falls verfügbar.
* Ungefährer Zeitpunkt des Fehlers, einschließlich Zeitzone.
* Alle Wiederholungsversuche und deren Ergebnisse.

## App wird nicht angezeigt

Wenn die App nach der Bereitstellung nicht in der Liste angezeigt wird, überprüfen Sie die folgenden Schritte:

1. Stellen Sie sicher, dass die App in Ihrem Unternehmen bereitgestellt und verfügbar ist.

1. Vergewissern Sie sich, dass Sie bei der richtigen Adobe-Organisation in Developer Console angemeldet sind.

1. Stellen Sie sicher, dass die App bereit zur Verbindung ist (Ihr App-Entwickler oder -Partner kann bestätigen).

Wenn die App weiterhin nicht angezeigt wird, wenden Sie sich an Ihren App-Entwickler oder lesen Sie die Dokumentation zur [Commerce [!DNL App Management]](https://developer.adobe.com/commerce/extensibility/app-management/){target="_blank"}Erweiterbarkeit“, um technische Informationen zu erhalten.

## Synchronisierung von Umfang schlägt fehl

Wenn die Synchronisierung des Umfangs beim Verknüpfen einer App fehlschlägt, versuchen Sie Folgendes:

1. Vergewissern Sie sich, dass Ihre Commerce-Instanz verfügbar und online ist.

1. Überprüfen Sie, ob Ihre API-Anmeldeinformationen gültig sind und über die richtigen Berechtigungen verfügen.

1. Versuchen Sie, in der App-Konfiguration manuell aus **[!UICONTROL Manage Scopes]** zu synchronisieren.

## Konfiguration nicht gespeichert

Wenn die Konfigurationsänderungen nicht gespeichert werden, versuchen Sie Folgendes:

1. Überprüfen Sie, ob alle erforderlichen Felder ausgefüllt und gültig sind.

1. Stellen Sie sicher, dass Sie über die richtigen Berechtigungen zum Ändern der App-Konfiguration verfügen.

1. Bitte Seite aktualisieren und erneut speichern.

Wenn das Problem weiterhin besteht, überprüfen Sie Ihre Browser-Konsole auf Fehler oder wenden Sie sich an Ihren App-Entwickler.

## Installation schlägt fehl

Lassen Sie die Installationsseite geöffnet, ohne sie zu aktualisieren, bis die Installation abgeschlossen ist. Das Schließen oder Aktualisieren kann dazu führen, dass die Installation nicht ordnungsgemäß abgeschlossen werden kann.

Wenn die Installation einen Fehler meldet:

1. Notieren Sie das fehlgeschlagene Element und die angezeigte Fehlermeldung.

1. Vergewissern Sie sich, dass Sie die Vorinstallationsanweisungen für die App ausgefüllt haben.

1. Bitten Sie Ihren App-Entwickler, den fehlgeschlagenen Schritt zu überprüfen und die Ursache zu korrigieren, bevor Sie erneut versuchen, die Installation auszuführen.

Bei einer fehlgeschlagenen Installation können einige Änderungen angewendet werden. Wenn die Installation erneut versucht wird, werden als erfolgreich aufgezeichnete benutzerdefinierte Schritte übersprungen. Fehlgeschlagene oder unterbrochene Schritte können erneut ausgeführt werden. Bitten Sie Ihren Entwickler, nach Ressourcen zu suchen, die durch die partielle Ausführung erstellt wurden.

## Upgrade schlägt fehl

Bei einem fehlgeschlagenen Upgrade können einige Vorgänge angewendet werden. Heben Sie die Verknüpfung nicht auf und installieren Sie die App nicht als routinemäßigen Wiederherstellungsschritt neu, da durch die Aufhebung der Verknüpfung die Konfiguration entfernt wird und destruktive Bereinigungsskripte ausgeführt werden können.

1. Identifizieren Sie den fehlgeschlagenen Schritt und zeichnen Sie alle angezeigten Fehlermeldungen auf.

1. Bitten Sie Ihren App-Entwickler, die Protokolle zu überprüfen, nach bereits vorgenommenen Änderungen an Commerce oder externen Ressourcen zu suchen und die Ursache zu beheben.

1. Wählen Sie in [!DNL App Management] die Option **[!UICONTROL Retry Upgrade]** aus. Diese Aktion steht sowohl für den manuellen als auch für den automatischen Upgrade-Modus zur Verfügung.

Bei jedem erneuten Versuch wird ein neuer Plan aus dem aktuellen Status erstellt. Benutzerdefinierte Installationsschritte, die als erfolgreich aufgezeichnet wurden, werden übersprungen. Fehlgeschlagene oder unterbrochene Schritte können erneut ausgeführt werden. Im Automatikmodus wird bei erneuter Bereitstellung der App auch ein weiterer Upgrade-Versuch Trigger.

Wenn wiederholte Versuche fehlschlagen, bitten Sie Ihren App-Entwickler, die Ausführungs- oder Versuch-IDs und die Ausführungsaktivierungs-ID zur Fehlerbehebung beizubehalten. Statusbefehle, ein Versuchsverlauf und Laufzeitprotokolle finden Sie unter [Wiederholen eines fehlgeschlagenen Upgrades](https://developer.adobe.com/commerce/extensibility/app-management/upgrade-app/#retry-a-failed-upgrade){target="_blank"} in der Entwicklerdokumentation.

## Ressourcen verbleiben nach einem Upgrade

Beim Entfernen eines benutzerdefinierten Installationsschritts aus der Konfiguration einer App wird das Deinstallationsskript nicht ausgeführt und die von ihr erstellten Ressourcen werden nicht entfernt. Der Upgrade-Plan warnt Sie, dass für den entfernten Schritt kein Skript ausgeführt wird und der Schritt nicht auf dem Fortschrittsbildschirm oder in den App-Details nach dem Upgrade angezeigt wird.

Bitten Sie Ihren App-Entwickler zu bestätigen, ob die Ressourcen weiterhin benötigt werden, und führen Sie bei Bedarf eine Bereinigungsmigration durch. Siehe [Aktualisieren einer App](manage-app.md#upgrade-an-app) für den Administrator-Workflow.

Weitere Informationen zur technischen Fehlerbehebung finden Sie unter [Erweiterbarkeit  [!DNL App Management]](https://developer.adobe.com/commerce/extensibility/app-management/){target="_blank"} Commerce.
