---
title: Einrichten der Storefront
description: Erfahren Sie, wie Sie das Tool für Strukturvorlagen ausführen, um Ihre Storefront  [!DNL Adobe Commerce as a Cloud Service] .
role: Developer
exl-id: 02928dc4-1777-483e-b0ee-b04fc813864d
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 47eb8ee55bb093767f76aa23df8bb347ee280aae
workflow-type: tm+mt
source-wordcount: '737'
ht-degree: 0%

---

# Einrichten der Storefront

Die folgenden Schritte zeigen, wie Sie mit dem Befehl `aio commerce init` Ihre Adobe Commerce-Storefront mit Edge Delivery schnell einrichten können. Dieser Prozess richtet Folgendes ein:

* [Commerce Storefront powered by Edge Delivery Services](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=de) - Eine leistungsstarke, skalierbare und sichere Storefront, die auf Adobes Edge Delivery Services basiert.
* [API Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/mesh/) - eine API-Plattform, mit der Entwickelnde mehrere Datenquellen zu einem einzigen GraphQL-Endpunkt kombinieren können. API Mesh orchestriert die Drittanbieter-API mit der Adobe-API über ein einziges Gateway. Eine Abfrage an den einzelnen GraphQL-Endpunkt kann Ergebnisse aus mehreren Quellen zurückgeben.
* [Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/) - Eine Sammlung von Entwickler-Tools mit Zugriff auf APIs, Ereignisse, Laufzeitfunktionen und Plug-ins, mit denen Sie Projekte für Adobe-Programme erstellen können.
* [Adobe I/O Runtime](https://developer.adobe.com/runtime/docs/) - Eine Server-lose Engine für die Bereitstellung von benutzerdefiniertem Code, der auf Ereignisse reagiert und Funktionen in der Cloud ausführt.

## Voraussetzungen

Bevor Sie den `aio commerce init`-Befehl ausführen, müssen Sie die folgenden Voraussetzungen erfüllen:

1. Installieren Sie Node Version Manager (NVM).

   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
   ```

1. Installieren Sie Node.js und NPM. Weitere Informationen finden Sie unter [Node.js](https://nodejs.org/en/).

   ```bash
   nvm install 22
   ```

   ```bash
   npm install -g npm
   ```

1. Installieren Sie [Adobe I/O Runtime CLI](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

   ```bash
   npm install -g @adobe/aio-cli
   ```

1. Installieren Sie das Adobe I/O API Mesh-Plug-in.

   ```bash
   aio plugins:install @adobe/aio-cli-plugin-api-mesh
   ```

1. Installieren des Adobe I/O Commerce-Plug-ins.

   ```bash
   aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce
   ```

1. Vorhandene Plug-ins aktualisieren.

   ```bash
   aio plugins:update
   ```

1. Melden Sie sich bei Ihrem Adobe Experience Cloud-Konto an.

   ```bash
   aio login
   ```

   Wenn mit dem Befehl `aio login` kein Browser-Fenster gestartet wird, lesen Sie den Abschnitt [Fehlerbehebung](#troubleshooting).

1. Wählen Sie die IMS-Organisation, das Projekt und den Arbeitsbereich aus. Verwenden Sie die Pfeiltasten und drücken Sie **Eingabetaste** um Ihre Auswahl zu treffen. Weitere Informationen zu `aio`-Befehlen finden Sie in der [Adobe I/O-CLI-Dokumentation](https://github.com/adobe/aio-cli-plugin-console?tab=readme-ov-file#commands).

   ```bash
   aio console org select
   ```

   ```bash
   aio console project select
   ```

   ```bash
   aio console workspace select
   ```

1. Falls noch nicht geschehen, akzeptieren Sie die Nutzungsbedingungen für Entwickler in der Adobe Developer-Konsole, indem Sie zu https://developer.adobe.com/console/home navigieren und auf **Akzeptieren und fortfahren** klicken.

## Ausführen des `aio commerce init` Befehls

Wenn Sie den folgenden Befehl ausführen, wird eine Strukturvorlage für Ihre Commerce-Storefront erstellt. Dieses Gerüst bietet einen guten Ausgangspunkt für das Erstellen und Verstehen Ihrer Storefront. Weitere Informationen zum Arbeiten mit der Storefront finden Sie in der Dokumentation zur [Adobe Commerce Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de).


1. Führen Sie den `init` Befehl aus:

   ```bash
   aio commerce init
   ```

1. Wenn Sie bereits bei GitHub angemeldet sind, geben Sie `Y` ein, um das Repository unter Ihrem Benutzernamen zu erstellen.

1. Geben Sie den Namen des Repositorys ein, das Sie erstellen möchten.

1. Wählen Sie eine der folgenden Optionen aus:

   * **Verwenden des Demo-Adobe Commerce-Mandanten** - Verwenden eines Demo-Mandanten.
      * Wenn Sie diese Option auswählen, werden Sie aufgefordert, den AEM Code Sync-Bot in einem Browserfenster zu installieren. Sie müssen das von Ihnen erstellte Repository angeben und den Bot autorisieren. Kehren Sie zur CLI zurück und geben Sie `y` ein, um die Installation des AEM Code Sync-Bots zu bestätigen.
   * **Verfügbaren Adobe Commerce-Mandanten auswählen** - Wählen Sie einen bestehenden Commerce-Mandanten in der ausgewählten Organisation aus.
      * Wenn Sie diese Option auswählen, müssen Sie das Projekt und den Arbeitsbereich auswählen, um ein Netz in zu erstellen.
   * **Geben Sie Ihre eigene Adobe Commerce-Mandanten-API** URL an: Wählen Sie diese Option, wenn Sie Teilnehmer eines Testzugriffsprogramms sind. Geben Sie die API-URL ein, die Sie in Ihrer Adobe-Onboarding-E-Mail angegeben haben.

   >[!NOTE]
   >
   >Wenn Sie die Option `Pick an available API (Mesh -> SaaS)` auswählen, müssen Sie über ein vorhandenes Projekt und Workspace in der Adobe Developer Console verfügen. [Erstellen eines Vorlagenprojekts](https://developer.adobe.com/developer-console/docs/guides/projects/projects-template/) und Auswahl von App Builder erstellt automatisch die erforderlichen Arbeitsbereiche.

1. Sobald der Prozess abgeschlossen ist, können Sie Ihre Storefront mit den folgenden Methoden anpassen:

   * Code anpassen: `https://github.com/<username or org>/<repo name>`
   * Inhalt bearbeiten: `https://da.live/#/<username or org>/<repo name>`
   * Konfiguration verwalten: `https://da.live/sheet#/<username or org>/<repo name>/configs-stage`
   * Vorschau der Storefront: `https://main--<repo name>--<username or org>.aem.page/`
   * Lokal ausführen: `aio commerce:dev`

Informationen zum Anpassen Ihrer Storefront finden Sie in der Dokumentation zur [Adobe Commerce Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de).

## Fehlerbehebung

Bei Problemen mit dem `aio login` empfiehlt Adobe, sich vollständig von der CLI und dem Browser abzumelden und sich dann erneut anzumelden.

1. Um sich von der CLI abzumelden, führen Sie Folgendes aus:

   ```bash
   aio logout
   ```

1. Navigieren Sie in Ihrem Browser zur [Adobe Developer Console](https://developer.adobe.com/console), klicken Sie oben rechts auf Ihr Profilsymbol und wählen Sie **Abmelden** aus.

1. Kehren Sie zur CLI zurück und führen Sie den Befehl `aio login` erneut aus. Dadurch sollte ein Browser-Fenster zur Anmeldung aufgerufen werden. Anschließend können Sie Ihre Organisation, Ihr Projekt und Ihren Arbeitsbereich auswählen.

   ```bash
   aio console org select
   ```

   ```bash
   aio console workspace select
   ```

   ```bash
   aio console project select
   ```

## Nächste Schritte

Weitere Informationen finden Sie in den folgenden Artikeln:

* Weitere Informationen zum Verwalten und Anzeigen von Inhalten und Daten in der Storefront finden Sie unter [Storefront-Inhalte aktualisieren](./use-cases.md#update-storefront-content).
* Weitere Informationen zu Funktionen für kontextuelle Experimente finden Sie unter [Kontextuelle Experimente](./use-cases.md#contextual-experimentation).
* Weitere Informationen zur Verwendung der generativen KI zur Automatisierung der Erstellung hochwertiger Inhalte finden Sie unter [Varianten generieren](./use-cases.md#generate-variations).
* Weitere Informationen zum Aktualisieren von Website-Inhalten und zur Integration mit Commerce-Frontend-Komponenten und Backend-Daten finden Sie in der [Dokumentation zur Adobe Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de).
