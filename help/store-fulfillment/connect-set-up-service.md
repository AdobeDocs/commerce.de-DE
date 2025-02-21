---
title: Verbinden der Store Fulfillment-Lösung
description: Herstellen der Verbindungen zwischen Adobe Commerce und der Store Fulfillment-Lösung Erstellen und autorisieren Sie eine Adobe Commerce-Integration und fügen Sie die Anmeldedaten für das Store-Fulfillment-Konto zur Adobe Commerce-Dienstkonfiguration hinzu.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install, Configuration, User Account, Tools and External Services
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Verbinden der Store Fulfillment-Lösung

Verbinden Sie Store Fulfillment-Services mit Adobe Commerce, indem Sie die erforderlichen Authentifizierungsdaten und Verbindungsdaten zu Adobe Commerce Admin hinzufügen.

- **[Konfigurieren [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)**-Erstellen Sie eine Adobe Commerce-Integration für Store-Fulfillment-Services und generieren Sie die Zugriffstoken, um eingehende Anfragen von den Store-Fulfillment-Servern zu authentifizieren.

- **[Konfigurieren von Kontoanmeldeinformationen für Store Fulfillment Services](#configure-store-fulfillment-account-credentials)**-Fügen Sie Ihre Anmeldedaten hinzu, um Adobe Commerce mit Ihrem Store Fulfillment-Konto zu verbinden.

>[!NOTE]
>
>Schließen Sie die Verbindungskonfiguration ab und validieren Sie die Verbindung erfolgreich, bevor Sie mit dem Testen beginnen.

## Erstellen einer Adobe Commerce-Integration

Um Adobe Commerce mit Store Fulfillment-Services zu integrieren, erstellen Sie eine Commerce-Integration und generieren Zugriffstoken, die zum Authentifizieren von Anfragen von Store Fulfillment-Servern verwendet werden können. Sie müssen auch die Adobe Commerce-[!UICONTROL Consumer Settings] aktualisieren, um `The consumer isn't authorized to access %resources.` Antwortfehler bei Anfragen von Adobe Commerce an [!DNL Store Fulfillment] Services zu verhindern.

1. Erstellen Sie vom Administrator aus die Integration für Store Fulfillment.

   - Benennen der Erweiterung
   - E-Mail-Adresse eingeben
   - Geben Sie Ihr Administratorkonto-Passwort ein

1. Konfigurieren Sie API-Ressourcenzugriffsberechtigungen für die Integration mit den folgenden Elementen:

   - Verkauf > BOPIS-Bestellaktualisierung
   - System > Store Fulfillment-App-Berechtigungen

1. Erstellen Sie die Zugriffstoken für die Authentifizierung, indem Sie die Integration speichern und aktivieren.

1. Kopieren Sie die Zugriffstoken und speichern Sie sie an einem sicheren, verschlüsselten Speicherort.

1. Arbeiten Sie mit Ihrem Account Manager zusammen, um die Konfiguration auf der Seite Store Fulfillment abzuschließen und die Integration zu autorisieren.

1. Aktivieren Sie die Option Adobe Commerce-[!UICONTROL Consumer Settings] zum [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - Navigieren Sie vom Administrator aus zu **[!UICONTROL Stores]** > [!UICONTROL Configuration] > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - Legen Sie die Option [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] auf **[!UICONTROL Yes]** fest.

>[!IMPORTANT]
>
> Das Integrations-Token ist umgebungsspezifisch. Wenn Sie die Datenbank für eine Umgebung mit den Quelldaten aus einer anderen Umgebung wiederherstellen - z. B. Produktionsdaten aus einer Staging-Umgebung wiederherstellen -, schließen Sie die `oauth_token` Tabelle aus dem Datenbankexport aus, damit die Details des Integrations-Tokens beim Wiederherstellungsvorgang nicht überschrieben werden.


## Konfigurieren von Store Fulfillment-Kontoanmeldeinformationen

Nachdem Sie das Aufnahmeformular ausgefüllt haben, wird ein Walmart Store Fulfillment-Konto für Sie erstellt. Sie erhalten die folgenden Anmeldeinformationen, wenn sie verfügbar sind:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (in der Regel identisch mit der obigen Konfiguration)

Diese Anmeldeinformationen sind erforderlich, um Store Fulfillment zu konfigurieren und zu verwenden.

>[!NOTE]
>
>Es kann einige Zeit dauern, bis der Prozess zur Kontoerstellung abgeschlossen ist. Während Sie auf die Anmeldeinformationen warten, [überprüfen und konfigurieren Sie andere Einstellungen für die Store-Fulfillment-Lösung](service-config-settings-overview.md).

### Anmeldedaten hinzufügen, um Verbindung mit Store Fulfillment herzustellen

1. Konfigurieren Sie [Kontoanmeldeinformationen](enable-general.md) für die Produktions- und Sandbox-Umgebungen.

1. Navigieren Sie vom Administrator zu **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Geben Sie die für die **[!UICONTROL Production environment]** angegebenen Kontoanmeldeinformationen ein. Alle Felder sind Pflichtfelder.

1. Wählen Sie **[!UICONTROL Save Config]** aus.

1. Testen Sie die Verbindung, indem Sie **[!UICONTROL Validate Credentials]** auswählen.

>[!NOTE]
>
>Wenn die Anmeldeinformationen ungültig sind, überprüfen Sie, ob Sie für jede Umgebung die richtigen Werte eingegeben haben, und überprüfen Sie erneut. Wenden Sie sich an Ihren Kundenbetreuer, wenn Sie weiterhin Probleme bei der Verbindung haben.
