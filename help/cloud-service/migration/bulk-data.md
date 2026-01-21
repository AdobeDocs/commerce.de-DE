---
title: Tool für die Massendatenmigration
description: Erfahren Sie, wie Sie mit dem Tool für die Massendatenmigration Daten aus Ihrer bestehenden Adobe Commerce in der Cloud-Instanz zu migrieren [!DNL Adobe Commerce as a Cloud Service].
feature: Cloud
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Developer
level: Intermediate
exl-id: 81522de9-df54-4651-b8ed-58956376af86
source-git-commit: e582ce85b58b57922a8cdd63dbe32bd0f08c64f9
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 0%

---

# Tool für die Massendatenmigration

Das Tool für die Massendatenmigration folgt einer verteilten Architektur, die eine sichere und effiziente Datenmigration von PaaS- zu SaaS-Umgebungen ermöglicht. Mit diesem Tool können Lösungsimplementierende Daten aus einer bestehenden Adobe Commerce on Cloud-Instanz (PaaS) nach [!DNL Adobe Commerce as a Cloud Service] (SaaS) migrieren. Weitere Informationen zum Migrationsprozess finden Sie unter [Migrationsübersicht](./overview.md).

>[!NOTE]
>
>Das Tool für die Massendatenmigration unterstützt nur die Migration von Commerce-Kerndaten von Erstanbietern. Die Migration benutzerdefinierter Daten wird derzeit nicht unterstützt.

In der folgenden Abbildung werden die Architektur und die Schlüsselkomponenten für die Verwendung der Tool für die Massendatenmigration erläutert.

![Architekturdiagramm für das Bulk-Daten-Migrationstool, das den Datenfluss zwischen PaaS und SaaS zeigt](../assets/bulk-data-diagram.png){zoomable="yes"}

## Migration arbeitsablauf

Die arbeitsablauf zur Massendatenmigration umfasst die folgenden Schritte:

1. Festlegen eine neue Umgebung für die Migration ein.
1. Kopieren Sie Ihre Daten aus Ihrem alten System.
1. Verschieben Sie Ihre Daten in das neue System.
1. Stellen Sie Ihren Produktkatalog im neuen System zur Verfügung.
1. Überprüfen Sie, ob Ihre Daten korrekt migriert wurden.

In den folgenden Abschnitten werden diese Schritte im Detail beschrieben.

## Zugreifen auf die Tool zur Massendatenmigration

Das Tool für die Massendatenmigration ist wie folgt verfügbar:

- **1. Quartal 2026** (noch nicht verfügbar) - Nach der ersten Version des Tools für die Massendatenmigration können Sie durch Senden eines Support-Tickets darauf zugreifen.
- **1. Quartal 2026** (noch nicht verfügbar) - Nach der öffentlichen Veröffentlichung des Tools für die Massendatenmigration ist es von dieser Seite aus zugänglich.

## Erstellen einer Zielumgebung

Der Lösungsimplementierer erstellt eine Zielumgebung für die Migration. Diese Umgebung speichert die aus der Quellinstanz migrierten Daten.

Erstellen [&#x200B; zunächst eine neue  [!DNL Adobe Commerce as a Cloud Service] SaaS) &#x200B;](../getting-started.md#create-an-instance).

### Konfigurieren des Extraktionstools

Extrahieren Sie mit dem Extraktions-Tool Daten aus der Quellinstanz.

1. Laden Sie das Extraktions-Tool über den von Adobe bereitgestellten Link herunter.
1. Legen Sie die folgenden Umgebungsvariablen im Extraktions-Tool fest:
   - Verbindung Details zu Ihrer bestehenden MySQL-Datenbank
   - Die Target-Komponente Mandanten-ID für Ihre [!DNL Adobe Commerce as a Cloud Service] Instanz
   - Ihre IMS-Anmeldedaten, einschließlich:
      - Client ID
      - Client geheim
      - IMS-Geltungsbereiche
      - IMS-URL : Die Basis-URL. Beispiel: `https://ims-na1.adobelogin.com/`.
      - Kennung der IMS-Organisation

   Wählen Sie für IMS-Bereiche und andere Werte Ihren OAuth-Typ im **Abschnitt Anmeldeinformationen** in Ihrem Projekt in der [Adobe Systems Developer Console](https://developer.adobe.com/console/) aus. Mehr Informationen sind in der Datei enthalten, die `.example.env` im Extraktion Tool enthalten ist.

### Extract Daten

Vor Ausführung des Extraktions-Tools muss der Implementierer der Lösung einen SSH-Tunnel zur PaaS-Datenbank einrichten, indem er Folgendes verwendet:

```bash
magento-cloud tunnel:open
```

Führen Sie dann das Extraktions-Tool aus. Dieses führt folgende Vorgänge aus:

1. Stellen Sie eine Verbindung zur PaaS-Datenbank her, analysieren Sie deren Schema und vergleichen Sie es mit den Details des SaaS-Mandantenschemas.
1. Generieren eines Extraktions- und Umwandlungsplans basierend auf den gemeinsamen Schemaelementen zwischen PaaS und SaaS.
1. Extrahieren Sie die Daten mithilfe des Catalog Data Management Service (CDMS).

### Daten laden

Führen Sie die von Adobe Systems bereitgestellten Ladedaten Tool aus. Diese Tool wird:

1. Stellen Sie mithilfe eines Migrations Konto eine Verbindung zur SaaS-Mandantendatenbank her.
1. Generieren Sie einen Beladungsplan.
1. Führen Sie den Plan aus und verschieben Sie die Daten stapelweise in die SaaS-Mandantendatenbank.
1. Katalog Medien verarbeiten und in die Target-Komponente Umgebung übertragen.
1. Leeren Sie den SaaS-Redis-Cache und invalidieren Sie die Datenbankindizes für den Mandanten.

### Aufnahme von Katalogdaten

Nach dem Laden der Daten fließen die Katalogdaten automatisch von der SaaS-Mandantendatenbank zum Katalog-Service.

Der Katalog-Service gibt diese Daten für die Live-Suche und für Produktempfehlungen frei. Für diesen Prozess ist kein manueller Eingriff erforderlich. Die Daten sind in allen -Services verfügbar, sobald die Aufnahme abgeschlossen ist.

### Prüfung der Datenintegrität

Nach der Migration führt CDMS die folgenden automatischen Datenintegritätsprüfungen durch, um die Genauigkeit und Vollständigkeit der migrierten Daten sicherzustellen:

**API-basierte Verifizierung**

Während der Verifizierung vergleicht CDMS die REST- und GraphQL-API-Antworten von zuvor ausgeführten Abfragen mit den entsprechenden Datensätzen aus der Zielinstanz. Alle Diskrepanzen sind im Migrationsstatus sichtbar.

**Überprüfung auf Datenbankebene**

Bei der Überprüfung zählt CDMS die Anzahl der extrahierten Datensätze und vergleicht diese Anzahl mit der Anzahl der geladenen Datensätze.

**Prüfung auf Anfrage (optional)**

Sie können auch manuell eine umfassende Überprüfung aller Systemdatensätze in Trigger nehmen:

>[!NOTE]
>
>Dieser Prozess ist ressourcenintensiv und sollte nur in Sandbox-Umgebungen verwendet werden.

Die vollständige Verifizierung umfasst:

- Vollständige API-basierte Verifizierung mit allen vorab extrahierten REST- und GraphQL-API-Antworten
- Detaillierter Bericht über festgestellte Inkonsistenzen.
