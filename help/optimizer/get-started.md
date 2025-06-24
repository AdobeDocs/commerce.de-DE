---
title: Erste Schritte
description: Erfahren Sie mehr über die ersten Schritte mit [!DNL Adobe Commerce Optimizer].
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: f49a86b8793e2d91413acfbc0b922cb94db67362
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---

# Erste Schritte

In diesem Artikel erfahren Sie, wie Sie sich mit [!DNL Adobe Commerce Optimizer] vertraut machen können. Während sich dieses Handbuch auf Merchandiser- und Administratorrollen konzentriert, enthält es kurze allgemeine Aufgaben, die ein Entwickler ausführen würde. Detaillierte Informationen [ Entwicklerspezifische Inhalte finden Sie ](https://developer-stage.adobe.com/commerce/services/composable-catalog/) der Entwicklerdokumentation .

## Welche Rolle haben Sie?

Die erfolgreiche Einrichtung von [!DNL Adobe Commerce Optimizer] umfasst in der Regel die folgenden Team-Mitglieder:

- Administrator
- Entwickler
- Verkaufsberater

Jedes Teammitglied hat seine eigenen Rollen und Zuständigkeiten, wie in der folgenden Tabelle beschrieben:

| Rolle(n) | Aufgabe |
|---|---|
| Administrator | Verwenden Sie Admin Console, um Administratoren, Benutzergruppen, Benutzer und Entwickler zu erstellen&#x200B;. |
|  | Erstellen Sie eine neue [!DNL Adobe Commerce Optimizer]-Instanz in Commerce Cloud Manager&#x200B; |
|  | Richten Sie Ihre Richtlinien und Katalogansichten ein. |
| Entwickler | Verwenden Sie Developer Console, um ein Projekt zu erstellen, Entwicklern API-Zugriff zu gewähren und erforderliche Programme und Anpassungen zu installieren. |
|  | Verbinden Sie sich mit Ihrem Back-Office-System (Warenkorb, Kasse) mithilfe von API Mesh und App Builder&#x200B;. |
|  | Nehmen Sie die Katalogdaten aus Ihren vorhandenen Commerce-Lösungen mithilfe der Merchandising Services-Datenaufnahme-API auf&#x200B; |
|  | Einrichten der Storefront |
| Verkaufsberater | Einrichten der Produkterkennung&#x200B;. |
|  | Einrichten von Produktempfehlungen. |

Jede Rolle spielt einen integralen Bestandteil beim erfolgreichen Onboarding und Launch Ihrer [!DNL Adobe Commerce Optimizer]. Das folgende Diagramm zeigt einen allgemeinen Workflow vom Anfang bis zum Ende für jede Rolle in Ihrer Organisation:

![Workflow auf hoher Ebene](./assets/high-level-workflow.png){zoomable="yes"}

### Administrator

Administratoren sind für die Einrichtung von Instanzen, die Verwaltung von Benutzern, Gruppen und Berechtigungen für Ihre Organisation verantwortlich.

- **[Zugriff auf die Adobe Admin Console](https://helpx.adobe.com/de/enterprise/admin-guide.html)** - Verwalten von Adobe-Berechtigungen in der gesamten Organisation. Unter [Benutzerverwaltung](./user-management.md) erfahren Sie, wie Sie oder der Produktadministrator oder Systemadministrator Ihres Unternehmens Benutzer zum [!DNL Adobe Commerce Optimizer] Produkt hinzufügen können.

- **Instanz erstellen** - [!DNL Adobe Commerce Optimizer] Instanzen verwenden ein kreditbasiertes System. Sie können mehrere Sandbox- und Produktionsinstanzen erstellen, wobei jede Instanz eine entsprechende Gutschrift erfordert. Die Höhe des Guthabens hängt zunächst von Ihrem Abonnement ab. [Weitere Informationen](#create-an-instance).

- **Auf eine Instanz zugreifen** - Nachdem Sie eine Instanz erstellt haben, können Sie über die [!UICONTROL Commerce Cloud Manager] darauf zugreifen. [Weitere Informationen](#access-an-instance).

- **Einrichten von Katalogansichten und Richtlinien** - Erfahren Sie, wie [ Katalogansichten und Richtlinien definieren](./setup/catalog-view.md). Der Katalog enthält nicht nur Ihre Produktdaten, sondern hilft Ihnen auch bei der Definition Ihrer Geschäftsstruktur.

### Entwickler

Entwickler erstellen Projekte und Anmeldeinformationen, installieren Erweiterungen, nehmen Katalogdaten auf und führen allgemeine Aufgaben der Plattformarchitektur aus. Detaillierte Informationen [ Entwicklerspezifische Inhalte finden Sie ](https://developer-stage.adobe.com/commerce/services/composable-catalog/) der Entwicklerdokumentation .

- **Zugriff auf Developer Console** - Greifen Sie auf die [Developer Console](https://developer.adobe.com/developer-console/docs/guides/getting-started) zu, um ein Projekt für [!DNL Adobe Commerce Optimizer] zu erstellen, Zugriffstoken zu generieren und erforderliche Programme und Anpassungen zu installieren.

- **Aufnehmen von Katalogdaten** - In der Dokumentation [Datenaufnahme-API](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/using-the-api/) erfahren Sie, wie Sie Katalogdaten in [!DNL Adobe Commerce Optimizer] importieren können.

  Die erfassten Katalogdaten sind auf der Seite [Datensynchronisierung](./setup/data-sync.md) sichtbar.

- **Storefront einrichten** - Bevor Sie die Storefront einrichten, müssen Sie zunächst eine Instanz erstellen. Dies ist eine Aufgabe, die normalerweise vom (Administrator[ Ihrer Organisation ausgeführt ](#administrator). Nachdem Sie Ihre Instanz erstellt haben, können Sie mit dem Einrichten [ Commerce-Storefront ](./storefront.md) Edge Delivery Services fortfahren.

### Verkaufsberater

Der Merchandiser verwendet Kundendaten und Analysen, um strategische Entscheidungen über Produktplatzierung, Preise und Werbeaktionen in der Storefront zu treffen und gleichzeitig das Einkaufserlebnis durch Produkterkundung und Empfehlungen zu optimieren.

- **Einrichten von Produkterkundung und Empfehlungen** - Erfahren Sie anhand von Produkterkundungen [Erstellen personalisierter Erlebnisse](./merchandising/overview.md) für Ihre Kunden.

## Instanz erstellen

1. Melden Sie sich bei Ihrem [Adobe Experience Cloud](https://experience.adobe.com/)-Konto an.

1. Klicken Sie unter [!UICONTROL Quick access] auf [!UICONTROL **Commerce**], um die [!UICONTROL Commerce Cloud Manager] zu öffnen.

   Die [!UICONTROL Commerce Cloud Manager] zeigt eine Liste der [!DNL Adobe Commerce] Instanzen an, die in Ihrer Adobe IMS-Organisation verfügbar sind, einschließlich der Instanzen, die für [!DNL Adobe Commerce Optimizer] und [!DNL Adobe Commerce as a Cloud Service] bereitgestellt wurden.

1. Klicken [!UICONTROL **oben rechts**] Bildschirm auf „Instanz hinzufügen“.

   ![Instanz erstellen](./assets/create-aco-instance.png){width="100%" align="center" zoomable="yes"}

1. [!UICONTROL **Commerce Optimizer**].

1. Geben Sie **Name** und **Beschreibung** für Ihre Instanz ein.

1. Wählen Sie die Region aus, in der Ihre Instanz gehostet werden soll.

   >[!NOTE]
   >
   >Nachdem Sie eine Instanz erstellt haben, können Sie die Region nicht mehr ändern.

1. Wählen Sie einen der folgenden [!UICONTROL **Umgebungstypen**] für Ihre Instanz aus:

   - [!UICONTROL **Sandbox**] - Ideal für Design- und Testzwecke. Sie sollten Ihren [!DNL Adobe Commerce Optimizer]-Journey mit der Sandbox-Umgebung beginnen.
   - [!UICONTROL **Produktion**] - Für Live-Stores und kundenorientierte Websites.

   >[!NOTE]
   >
   >Sandbox-Instanzen sind derzeit auf die Region Nordamerika beschränkt.

1. Klicken Sie [!UICONTROL **Instanz hinzufügen**].

   Die neue Instanz ist jetzt in Cloud Manager verfügbar.

1. Um Instanzdetails anzuzeigen, einschließlich der Endpunkte für den GraphQL- und Katalog-Service, der URL für den Zugriff auf das Adobe Commerce Optimizer-Programm und der Instanz-ID (Mandanten-ID), klicken Sie auf das Informationssymbol neben dem Instanznamen.

   ![Instanz erstellen](./assets/aco-instance-details.png){width="100%" align="center" zoomable="yes"}

## Zugriff auf eine Instanz

1. Melden Sie sich bei Ihrem [Adobe Experience Cloud](https://experience.adobe.com/)-Konto an.

1. Klicken Sie unter [!UICONTROL Quick access] auf [!UICONTROL **Commerce**], um die [!UICONTROL Commerce Cloud Manager] zu öffnen.

   Die [!UICONTROL Commerce Cloud Manager] zeigt eine Liste der Instanzen an, die in Ihrer Adobe IMS-Organisation verfügbar sind.

1. Um die mit einer Instanz verknüpfte [!UICONTROL Commerce Optimizer]-Anwendung zu öffnen, klicken Sie auf den Instanznamen.


