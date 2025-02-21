---
title: Benutzer-Setup
description: Richten Sie erweiterte Inventory management-Quellen als Händler-Stores ein, um die Store Fulfillment-Lösung für Adobe Commerce zu unterstützen.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, User Account, Tools and External Services
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Benutzer-Setup

Store Assist-App-Benutzer werden in Adobe Commerce verwaltet. Diese Benutzenden interagieren jedoch nicht direkt mit Adobe Commerce. Die Benutzerverwaltung ist in Adobe Commerce konfiguriert, um sichere Verbindungen zwischen Adobe Commerce und der App zu ermöglichen.

Das Benutzermodell der Store-Fulfillment-App ist von anderen Adobe Commerce-Benutzermodellen getrennt. Die App verwaltet ihr eigenes Berechtigungsmodell über Benutzerrollen und Benutzer, die allen oder bestimmten Standorten zugewiesen werden können. Die folgenden Berechtigungen werden unterstützt: Kommissionierauftrag, Dispensierauftrag und Artikelmengenreduzierung (und -stornierung).

>[!TIP]
>
>Um optimale Ergebnisse zu erzielen[ konfigurieren Sie Ihre Verbindung](connect-set-up-service.md) bevor Sie Benutzer und Berechtigungen für Store Associates hinzufügen, die die Store Assist -App verwenden.

## Store-Assist-App - Benutzerrollen

Erstellen Sie bei der erstmaligen Einrichtung für die Store Assist-App Benutzerrollen, um Benutzerberechtigungen für die Store Assist-App anzupassen. Sie können beispielsweise verschiedene Rollen für Store-Manager und Store-Mitarbeiter erstellen und ihnen unterschiedliche Rollenressourcen zuweisen, um die Berechtigungen für jeden Benutzertyp zu verwalten.

Konfigurieren Sie Benutzerrollen über **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

### Rolleninformationen

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Benutzer aktivieren oder deaktivieren. | Global | Ja |

### Rollenressourcen

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | Listen Sie die verfügbaren Berechtigungsgruppen auf, die einer Benutzerrolle zugewiesen werden können. Derzeit sind für die Store Fulfillment-Lösung keine unterschiedlichen Berechtigungsebenen für Ressourcenrollen definiert. Alle Benutzerrollen haben denselben Ressourcenzugriff. | Global | Ja |

## Store Assist - Benutzerinformationen

Verwalten Sie Benutzerprofile für die Store-Assist-App über die Admin-Systemeinstellungen: **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]** | Benutzer aktivieren oder deaktivieren. | Global | Ja |
| **[!UICONTROL User Name]** | Benutzername, der dem Benutzer zugeordnet ist | Global | Ja |
| **[!UICONTROL First Name]** | Vorname, der dem Benutzer zugeordnet ist | Global | Nein |
| **[!UICONTROL Last Name]** | Nachname, der dem Benutzer zugeordnet ist | Global | Nein |
| **[!UICONTROL Role]** | Dem Benutzer zugewiesene Rolle | Global | Nein |
| **[!UICONTROL Access to all locations]** | Weisen Sie Benutzenden Zugriff auf alle Stores zu oder wählen Sie Stores einzeln aus. | Global | Nein |
| **Interface Locale** | Wenn Ihr Store mehrere Sprachen hat, setzen Sie „Interface Locale“ auf die Sprache, die für die Admin-Oberfläche verwendet werden soll. | Global | Nein |
| **Aktiv von** | Um ein Startdatum festzulegen, wählen Sie das Kalendersymbol aus. | Global | Nein |
| **Aktiv bis** | Legen Sie das Ablaufdatum fest, indem Sie auf das Kalendersymbol klicken. Das Festlegen eines Ablaufdatums ist nützlich, um temporäre Benutzer- oder Rollenzuweisungen einzurichten. Nach dem Ablaufdatum ändert sich der Benutzerkontenstatus in `Inactive`, das Konto kann jedoch bei Bedarf immer noch aktualisiert werden. | Global | Nein |
