---
title: Auf Erweiterungs-Updates prüfen
description: Erfahren Sie, wie Adobe Commerce nach neuen AEM Assets-Integrationserweiterungsversionen sucht und Admins darüber informiert, einschließlich der manuellen CLI-Prüfung.
feature: CMS, Media
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
source-git-commit: 7950f5d171b35054be42ca60d19bafcf43c53cd6
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 4%
---
# Auf Aktualisierungen der Erweiterung prüfen

Bei AEM Assets Integration Extension-Version 1.4.6 und höher prüft Adobe Commerce automatisch, ob eine neuere Version der Erweiterung verfügbar ist, und benachrichtigt Administratoren im Admin-Bereich. Diese Prüfung wird asynchron im Rahmen der geplanten Verarbeitung ausgeführt und blockiert nicht das Rendern der Admin-Seite.

## Funktionsweise der Update-Prüfung

* Bei der Update-Prüfung wird Ihre installierte `aem-assets-integration`-Paketversion mit der höchsten kompatiblen Version verglichen, die von [repo.magento.com](https://repo.magento.com/admin/dashboard) verfügbar ist.
* Ergebnisse werden zwischengespeichert. Beim Laden einer Admin-Seite wird das zuletzt zwischengespeicherte Ergebnis gelesen, anstatt eine Live-Netzwerkanfrage auszulösen.
* Wenn `repo.magento.com` nicht verfügbar oder die zurückgegebenen Metadaten ungültig sind, behält Commerce das letzte erfolgreiche zwischengespeicherte Ergebnis bei und blockiert nicht den Administrator.

>[!NOTE]
>
>Die Aktualisierungsprüfung ist für Adobe Commerce in Cloud- und On-Premise-Bereitstellungen vorgesehen.

## Aktualisierungsbenachrichtigungen anzeigen

Admins können eine verfügbare Aktualisierungsbenachrichtigung an beiden Orten sehen:

* **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Adobe Services]** > **[!UICONTROL AEM Assets Integration]**
* Das Dropdown-Menü „Admin-Benachrichtigung“

Jede Benachrichtigung wird angezeigt:

* Die installierte Version
* Die verfügbare Version
* Die Versionsklassifizierung
* Link zu den Versionshinweisen

Wählen Sie **[!UICONTROL Remind me later]** aus, um die Benachrichtigung für diese Commerce-Instanz zu synchronisieren, oder deaktivieren Sie alle Aktualisierungsbenachrichtigungen.

## Ausführen einer manuellen Aktualisierungsprüfung

Um sofort nach einer verfügbaren Aktualisierung zu suchen, führen Sie den folgenden Befehl aus dem Commerce-Stammverzeichnis aus:

```bash
bin/magento aem:assets:check-update
```

Dieser Befehl sucht nur nach verfügbaren Aktualisierungen und meldet diese. Es werden keine Composer-Dateien geändert oder ein Update bereitgestellt. Um ein Update zu installieren, folgen Sie den Composer-Anweisungen unter [Installieren von Adobe Commerce-Paketen](configure-commerce.md).

## Veröffentlichen von Metadaten für Erweiterungspakete

Die Aktualisierungsprüfung liest die Veröffentlichungsmetadaten aus dem Abschnitt `extra` der `composer.json`-Datei des installierten Pakets:

```json
{
  "extra": {
    "release_notes_url": "https://experienceleague.adobe.com/de...",
    "release_type": "feature",
    "compatible_commerce_versions": ">=2.4.7 <2.5.0"
  }
}
```

## Nächster Schritt

* [Installieren von Adobe Commerce-Paketen](configure-commerce.md)
