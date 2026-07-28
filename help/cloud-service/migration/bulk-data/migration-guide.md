---
title: Massendatenmigration ausführen
description: Erfahren Sie, wie Sie mit der CLI eine Massendatenmigration von einer Adobe Commerce PaaS- oder On-Premise-Instanz zu Adobe Commerce as a Cloud Service konfigurieren und ausführen.
feature: Cloud
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Developer
level: Intermediate
autotag-review: '2026-07-22T19:19:07.600Z'
TQID: 'https://experienceleague.adobe.com/z9659Vnf2JLxJ4U5p3tEEjurj5Mg3bfKj68Gheq2AXY'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
subfeature_v2:
  - id: f8ddfd3b-6194-46e8-a176-0e918039be56
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 670b6214b28be93a16130552a226a8cadb487324
workflow-type: tm+mt
source-wordcount: 2802
ht-degree: 0%

---

# Ausführen einer Massendatenmigration

{{bulk-data-early-access}}

Dieses Handbuch ist eine schrittweise Anleitung zum Ausführen einer Datenmigration von einer [!DNL Adobe Commerce] PaaS- oder On-Premise-Installation zum [!DNL Adobe Commerce as a Cloud Service] mithilfe des Tools für die Massendatenmigration. Die tatsächlichen Konfigurationswerte und umgebungsspezifischen Details variieren je nach Einrichtung.

Bevor Sie beginnen, vergewissern Sie sich, dass Sie alle Elemente in der [Checkliste zur Kundenbereitschaft“ abgeschlossen &#x200B;](readiness-checklist.md) den API-Zugriff mit dem [Migrationsservice-Zugriffshandbuch“ &#x200B;](cdms-access.md) haben.

>[!NOTE]
>
>Eine umfassende technische Dokumentation, die die Architektur des Tools, das interne Design, das Datenumwandlungs-Framework und das Framework für Integritätstests abdeckt, ist Teil des Tool-Verteilungspakets.

## Voraussetzungen

- **[!DNL Docker]** und **[!DNL Docker Compose]** müssen auf dem Computer installiert sein, auf dem Sie die Migration ausführen.
- Der Benutzer, der die Migration ausführt, muss über die Berechtigung zum Ausführen von `docker`- und `docker compose`-Befehlen (oder der Legacy-`docker-compose`) verfügen. Am [!DNL Linux] muss der Benutzer in der `docker` sein. Auf [!DNL macOS] und [!DNL Windows] muss [!DNL Docker Desktop] ausgeführt werden und zugänglich sein. Die Migrations-CLI ruft [!DNL Docker] wiederholt auf und Berechtigungsfehler blockieren hier die Ausführung.
- Die Kernkonfiguration muss zwischen Quelle und Ziel konsistent sein, bevor Sie die Migration ausführen. Kernkonfigurationsdaten wie Speichereinstellungen und Systemkonfiguration werden von diesem Tool nicht migriert. Richten Sie sie unabhängig auf dem Ziel ein und richten Sie sie vor der Migration an der Quelle aus.

## Einrichten des Tool-Pakets

Einrichten der Umgebung für die Massendatenmigration:

>[!VIDEO](https://video.tv.adobe.com/v/3496121)

1. Extrahieren Sie den Inhalt von `ccsaas-migration-tools.tar.gz`.

1. Führen Sie alle Befehle aus dem extrahierten `ccsaas-migration-tools`-Ordner aus, in dem sich `bin/console` befindet.

1. Stellen Sie sicher, dass in den Ordner Protokolle, Cache-[!DNL Composer] und generierte Dateien geschrieben werden können.

   Ändern Sie den Besitz aller Dateien und Unterordner unter diesem Verzeichnis auf den Betriebssystembenutzer, der die Migration ausführt, damit das Tool konsistent lesen und schreiben kann. Zum Beispiel auf [!DNL Linux]: `chown -R <user>:<group> <project-root>`.

1. Erstellen Sie die `.env`- und `.my.cnf`-Dateien im Projektstamm, indem Sie die Beispieldateien (`.example.env` nach `.env` und `.my.cnf.example` nach `.my.cnf`) kopieren und dann die in den folgenden Abschnitten beschriebenen Werte ausfüllen.

### Beispielkonfigurationsdateien

Die `.example.env`- und `.my.cnf.example`-Dateien im Repository-Stamm sind der Ausgangspunkt für Ihre Konfiguration. Kopieren Sie jede Datei in ihren Arbeitsnamen und geben Sie die erforderlichen Werte ein.

| Beispieldatei | Kopieren in | Was es abdeckt |
| --- | --- | --- |
| `.example.env` | `.env` | Anmerkungsliste aller unterstützten Umgebungsvariablen: Leistung, CDMS, IMS, Ziel-SaaS, Quell-URLs, Authentifizierung, OAuth und optionale PaaS-Werte (`MAGENTO_CLOUD_CLI_TOKEN`, wenn `id=` in `.my.cnf` festgelegt ist). Eine vollständige Variablenliste ist in der `.env`-Datei verfügbar. |
| `.my.cnf.example` | `.my.cnf` | Referenz `[section]` Layouts für lokale [!DNL MySQL] und PaaS (`id=project:environment`). Der `[section]` muss mit `SOURCE_CONNECTION_NAME` in `.env` übereinstimmen. Zu den Feldern gehören `user`, `password`, `host`, `port`, `database` und `id=` für PaaS. |

## Konfigurieren der Umgebungsdatei

Die `.env` Datei im Projektstamm ist die Migrations- und Extraktionskonfiguration. Sie steuert die CLI-Pipeline, einschließlich Quell- und Ziel-URLs, OAuth, der Remote-CDMS-Verbindung, SaaS- und IMS-Authentifizierung und anderer Switches.

>[!NOTE]
>
>URLs dürfen keine abschließenden Schrägstriche enthalten. Verwenden Sie beispielsweise `https://example.com` anstelle von `https://example.com/`.

Bearbeiten Sie die `.env` und legen Sie mindestens die folgenden Werte korrekt fest. Eine vollständige Liste der unterstützten Variablen finden Sie in den Inline-Anmerkungen in `.example.env`.

```shell-session
SOURCE_INSTANCE_URL=https://<source-host>
SOURCE_INSTANCE_GRAPHQL_URL=https://<source-host>/graphql
SOURCE_INSTANCE_REST_URL=https://<source-host>/rest
SOURCE_INSTANCE_CONSUMER_KEY=<consumer_key>
SOURCE_INSTANCE_CONSUMER_SECRET=<consumer_secret>
SOURCE_INSTANCE_ACCESS_TOKEN=<access_token>
SOURCE_INSTANCE_ACCESS_TOKEN_SECRET=<access_token_secret>
```

### Konfigurieren der OAuth-Quellberechtigungen

>[!VIDEO](https://video.tv.adobe.com/v/3496142)

Diese vier Werte signieren Anfragen vom Migrations-Tool an die Quell-Store-APIs. Um sie zu erhalten, öffnen Sie die [!UICONTROL Admin] und navigieren Sie zu [!UICONTROL **System**] > [!UICONTROL **Erweiterungen**] > [!UICONTROL **Integrationen**]. Erstellen oder öffnen Sie eine Integration und kopieren Sie dann die Werte in `.env`:

```shell-session
SOURCE_INSTANCE_CONSUMER_KEY=<consumer_key>
SOURCE_INSTANCE_CONSUMER_SECRET=<consumer_secret>
SOURCE_INSTANCE_ACCESS_TOKEN=<access_token>
SOURCE_INSTANCE_ACCESS_TOKEN_SECRET=<access_token_secret>
```

### Festlegen des Cloud-CLI-Tokens

>[!NOTE]
>
>Dies gilt nur für [!DNL Adobe Commerce on Cloud] Quellinstanzen. Das Tool erkennt den Quelltyp automatisch aus `.my.cnf`. Wenn der `SOURCE_CONNECTION_NAME` Abschnitt eine `id=` enthält (z. B. `id=project:production`), ist die Quelle [!DNL Adobe Commerce on Cloud] und `MAGENTO_CLOUD_CLI_TOKEN` erforderlich. Bei lokalen Quellen ohne `id=` ist dieses Token nicht erforderlich und die Tunneleinrichtung wird übersprungen.

1. Navigieren Sie zu `https://accounts.magento.cloud` und melden Sie sich an.

1. Klicken Sie auf Ihr Profilbild und wählen Sie [!UICONTROL **Kontoeinstellungen**].

1. Navigieren Sie zum Abschnitt [!UICONTROL **API-Token**].

1. Wählen Sie [!UICONTROL **API-Token erstellen**], geben Sie ihm einen beschreibenden Namen und kopieren Sie das generierte Token.

1. Setzen Sie das Token in `.env`:

   ```text
   MAGENTO_CLOUD_CLI_TOKEN=<your_magento_cloud_api_token>
   ```

>[!NOTE]
>
>Wenn Sie die Cloud-CLI zum ersten Mal verwenden, müssen Sie auch Ihren öffentlichen SSH-Schlüssel zu Ihrem Konto hinzufügen. Anweisungen finden Sie [&#x200B; „Handbuch &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/secure-connections) gesicherter Verbindungen“.

### Commerce-Admin-Einstellungen ausrichten

Stellen Sie vor der Migration sicher, dass die folgenden Einstellungen zwischen Quelle und Ziel konsistent sind.

>[!NOTE]
>
>Um eine reibungslose Migration sicherzustellen, empfiehlt [!DNL Adobe], alle Kernkonfigurationen in der Zielinstanz mit der Quelle konsistent zu machen.

### Target SaaS- und IMS-Anmeldedaten konfigurieren

>[!VIDEO](https://video.tv.adobe.com/v/3496167)

Dies sind die [!DNL Adobe Commerce as a Cloud Service] IMS- und API-Einstellungen für das Ziel. Sie benötigen die Mandanten-ID, die Organisations-ID, die IMS-OAuth-Server-zu-Server-Anmeldeinformationen und den richtigen IMS-Host für Ihre Umgebung. Abstimmung mit Ihrem Adobe-Team für Organisations-, Mandanten- und Profilzugriff. Versuchen Sie nicht, vertrauliche Werte abzuleiten oder zu schätzen.

#### IMS-Anmeldeinformationen generieren

Verwenden Sie die [Adobe Developer Console](https://developer.adobe.com/console/). Sie benötigen [!UICONTROL Developer] oder [!UICONTROL Admin] Zugriff auf die Adobe-Organisation, um Projekte zu erstellen. Eine einfache Benutzeranmeldung reicht nicht aus, um APIs hinzuzufügen.

1. Erstellen Sie ein Projekt oder öffnen Sie ein vorhandenes und wählen Sie dann [!UICONTROL Add API] aus.

1. [!UICONTROL **Adobe Commerce as a Cloud Service auswählen**] und fortfahren.

1. Wählen [!UICONTROL **als Authentifizierungstyp OAuth Server-zu**] Server aus und fahren Sie fort.

1. Wählen Sie das Produktprofil aus, das Ihr Adobe-Team für diesen Mandanten erwartet, und wählen Sie dann [!UICONTROL **Konfigurierte API speichern**].

1. Öffnen Sie in der Projekt-Seitenleiste [!UICONTROL **OAuth Server-zu-Server**] (oder [!UICONTROL **Anmeldeinformationen**]) und kopieren Sie dann die Client-ID und das Client-Geheimnis in `.env` as `ADOBE_IMS_CLIENT_ID` und `ADOBE_IMS_CLIENT_SECRET`.

Der IMS-Token-Endpunkt (`ADOBE_IMS_URL`) muss mit der Umgebung der Berechtigung übereinstimmen.

| Stufe | Typische `ADOBE_IMS_URL` |
| --- | --- |
| QA oder Staging | `https://ims-na1-stg1.adobelogin.com` |
| Vorproduktion oder Produktion | `https://ims-na1.adobelogin.com` |

>[!NOTE]
>
>`na1` in diesen URLs stellt die Region dar, in der Ihre Zielinstanz bereitgestellt wird. Ersetzen Sie sie durch die entsprechende Regionskennung, wenn Ihre Instanz in einer anderen Region bereitgestellt wird.

`ADOBE_IMS_META_SCOPES` muss mit den für diese Berechtigung bereitgestellten Bereichen übereinstimmen. Die `.example.env`-Datei enthält die vollständige, durch Kommas getrennte Bereichszeichenfolge als Referenz. Ändern Sie sie nur, wenn Adobe Sie dazu anweist.

#### Zuordnen [!DNL Adobe I/O] Anmeldeinformationen zur Umgebungsdatei

In [!DNL Developer Console] werden die OAuth-Server-zu-Server-Werte als Client-ID und Client-Geheimnis dargestellt, die der folgenden JSON-Struktur entsprechen:

```json
{
  "client_id": "xxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "client_secret": "xxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```

Ordnen Sie sie `.env` zu (Beispiel-Platzhalter):

```shell-session
TARGET_ORG_ID=<org_id>@AdobeOrg
ADOBE_IMS_URL=https://ims-na1.adobelogin.com
ADOBE_IMS_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxxx
ADOBE_IMS_CLIENT_SECRET=xxxxxxxxxxxxxxxxxxxxxxxxxxx
ADOBE_IMS_META_SCOPES=AdobeID,openid,additional_info.projectedProductContext
```

Die SaaS-API-Hosts unterscheiden sich zwischen der Vorproduktion und der Produktion. `TARGET_INSTANCE_REST_URL` und `TARGET_INSTANCE_GRAPHQL_URL` müssen dieselbe Commerce-API-Umgebung wie Ihre Migration verwenden, entweder vor der Produktion oder in der Produktion. Mischen Sie keine Ebene mit dem CDMS oder Mandanten der anderen Ebene.

| Umgebung | Typischer Host in `TARGET_INSTANCE_*_URL` |
| --- | --- |
| Vorproduktion oder Sandbox | `https://na1-sandbox.api.commerce.adobe.com/{tenantId}` |
| Produktion | `https://na1.api.commerce.adobe.com/{tenantId}` |

>[!NOTE]
>
>`na1` in diesen URLs stellt die Region dar, in der Ihre Zielinstanz bereitgestellt wird. Ersetzen Sie sie durch die entsprechende Regionskennung, wenn Ihre Instanz in einer anderen Region bereitgestellt wird.

```shell-session
TARGET_TENANT_ID=<tenant_id>
TARGET_ORG_ID=<org_id>@AdobeOrg
ADOBE_IMS_URL=https://ims-na1.adobelogin.com
ADOBE_IMS_CLIENT_ID=<client_id>
ADOBE_IMS_CLIENT_SECRET=<client_secret>
ADOBE_IMS_META_SCOPES=AdobeID,openid,additional_info.projectedProductContext
TARGET_INSTANCE_REST_URL=https://na1-sandbox.api.commerce.adobe.com/{tenantId}
TARGET_INSTANCE_GRAPHQL_URL=https://na1-sandbox.api.commerce.adobe.com/{tenantId}/graphql
```

Ersetzen Sie bei SaaS-Produktions-Hosts in beiden `TARGET_INSTANCE_*`-URLs `na1-sandbox` durch `na1`. Verwenden Sie den entsprechenden `ADOBE_IMS_URL` für diese Ebene, wie in der vorherigen Tabelle dargestellt.

### Festlegen des CDMS-Endpunkts

Zeigen Sie mit dem Migrations-Tool auf den CDMS-API-Host, der der Umgebung entspricht, zu der Sie migrieren. `CDMS_HOST` (und normalerweise `CDMS_PORT=443`) in `.env` festlegen. Verwenden Sie einen Host, entweder vor der Produktion oder in der Produktion, aber nicht beides.

| Umgebung | Verwendungszeitpunkt | `CDMS_HOST` |
| --- | --- | --- |
| Vorproduktion | Prä-Produktions- oder Sandbox-artige Ausführungen, produktionsfremde CDMS | `https://commerce-data-migration-service-preprod-external.adobe.io` |
| Produktion | Live-Produktionsmigration oder -umstellung | `https://commerce-data-migration-service-prod-external.adobe.io` |

Legen Sie den Block fest, der Ihrer Ausführung entspricht, oder heben Sie den Kommentar auf:

```shell-session
# Pre-production CDMS
CDMS_HOST=https://commerce-data-migration-service-preprod-external.adobe.io
CDMS_PORT=443

# Production CDMS (use for prod cutover only)
# CDMS_HOST=https://na1.api.commerce.adobe.com
# CDMS_PORT=443
```

### Festlegen des Store-Codes

`STORE_CODE` ist der Code der Speicheransicht, der vom Migrations-Tool für REST-API-Aufrufe der Quellinstanz, die Erstellung synthetischer Tests und die Datenbereinigung verwendet wird. Sie wird auch während der Ladephase als `x-store-code`-Header gesendet.

`STORE_CODE` Standardwert ist `default` in `.example.env`. Stellen Sie sicher, dass dies mit dem Standard-Code der Store-Ansicht Ihrer Quellinstanz übereinstimmt. Um dies zu überprüfen, gehen Sie in der [!UICONTROL Admin] zu [!UICONTROL **Stores**] > [!UICONTROL **Alle Stores**] und suchen Sie in der Spalte [!UICONTROL **Code**] nach der Store-Ansicht, die verwendet werden sollte. Wenn der dort angezeigte Code nicht `default` wird, aktualisieren Sie `STORE_CODE` in `.env` entsprechend.

## Datenbankverbindungsdatei konfigurieren

>[!VIDEO](https://video.tv.adobe.com/v/3496152)

Die `.my.cnf`-Datei enthält [!DNL MySQL] Verbindungseinstellungen für die Extraktionsseite des Migrations-Tools. Erstellen Sie sie durch Kopieren von `.my.cnf.example` nach `.my.cnf` im Projektstamm. Der Abschnittsname muss mit `SOURCE_CONNECTION_NAME` in `.env` übereinstimmen.

Für eine lokale oder selbst gehostete Quelle:

```ini
[<connection-name>]
user=<db_user>
password='<db_password>'
host=<db_host>
port=3306
database=<db_name>
```

>[!NOTE]
>
>Der Computer, auf dem das Migrations-Tool ausgeführt wird, muss direkten Netzwerkzugriff auf die Quelldatenbank haben. Das Tool stellt keine lokale Konnektivität her und überprüft sie nicht automatisch. Vergewissern Sie sich, dass der Host, der Port und die Anmeldeinformationen vom Migrationscomputer aus erreichbar sind, bevor Sie einen Migrationsbefehl ausführen.

Für eine [!DNL Adobe Commerce on Cloud]:

```ini
[<connection-name>]
id=<project_id>:<environment>
```

Das `id=` Feld teilt dem Tool mit, dass die Quelle PaaS ist und dass der Trigger-Tunnel mithilfe von `MAGENTO_CLOUD_CLI_TOKEN` eingerichtet wird. Die `project_id`- und `environment` sind in der [!DNL Cloud Console] oder über die `magento-cloud project:list`- und `magento-cloud environment:list` verfügbar.

## Vorbereiten des Netzwerks und der Instanzen

Die einfache HTTP-Authentifizierung vor dem Store kann API- und Tool-Traffic blockieren. Stellen Sie sicher, dass sie für die von der Migration verwendete Quell-URL deaktiviert ist oder dass die Pfade des Tools zulässig sind, sodass REST- und GraphQL-Anfragen den Store erreichen können.

### Wahrung der Stabilität der Quelldatenbank während der Extraktion

Während das Tool Daten aus der Quelldatenbank extrahiert, sollten keine anderen Prozesse in sie schreiben. Gleichzeitige Schreibvorgänge können zu einem inkonsistenten Snapshot führen.

- Beenden Sie Cron für die Quelle und alle Betriebssystemplaner, die `bin/magento` oder andere Writer ausführen, für das Extraktionsfenster oder stellen Sie sicher, dass sie nicht während der Extraktion ausgeführt werden können.
- Überprüfen Sie andere Integrationen wie ERP, OMS, PIM, benutzerdefinierte Aufträge und Drittanbieter-APIs, die in dieselbe Datenbank schreiben. Beim Anhalten oder Blockieren von Schreibvorgängen für das Extraktionsfenster werden die Tabellen während der Extraktion nicht mutiert.
- Dies ergänzt den Wartungsmodus und den Tunnel- oder Datenbankzugriff. Gemeinsam reduzieren sie Storefront- und API-Traffic. Cron- und -Integrationen sind separate Quellen für Schreibvorgänge, die Sie explizit steuern müssen.

### Target

Wenn der Zielkatalog vor der Migration gelöscht werden muss, löschen Sie Produkte in [!UICONTROL Admin] in kleinen Batches, z. B. jeweils 200, um doppelte Katalogkonflikte und Zeitüberschreitungen bei der Massenlöschung zu vermeiden.

## Erstellen und Ausführen der Migration

Arbeiten aus dem extrahierten Projektverzeichnis mit Schreibzugriff.

### Halten Sie die Sitzung über SSH am Leben

Wenn Sie eine Verbindung über SSH herstellen, kann ein ausgelassenes Netzwerk Ihre Shell zerstören und eine lange Migration unterbrechen. Der GNU-`screen`-Befehl hält die Sitzung auf dem Server am Leben:

```bash
screen -S migration          # new session named "migration"
# run ./bin/console commands here; when you want to disconnect without stopping work:
# press Ctrl+A, release, then press d   # detach
screen -ls                   # list sessions
screen -x migration          # reattach to "migration"
```

Sie können auch `tmux` verwenden, wenn es auf dem Server verfügbar ist.

### Docker-Image erstellen

Erstellen Sie das von `bin/console` verwendete [!DNL Docker]-Image, das PHP, die CLI und Abhängigkeiten enthält. Führen Sie dies vor der ersten Ausführung oder nach Docker-Datei- oder Basisbildänderungen aus.

```bash
./bin/console build
```

### Starten der unterstützenden Services

Starten Sie die [!DNL Docker Compose] für das Tool, z. B. die lokale Testdatenbank und, wenn in `.env` aktiviert, optionale lokale Services. Die genauen Dienste hängen von Ihrer Konfiguration ab. Führen Sie dies nach einem erfolgreichen Build und vor den Befehlen Shell, Migration oder Schrittweise aus.

```bash
./bin/console start
```

### Initialisieren des CLI-Containers

Starten Sie den CLI-Container einmal, damit der Einstiegspunkt die Einrichtung für Ihr bereitgestelltes Projekt abschließen kann, z. B. eine [!DNL Composer] Installation. Führen Sie dies einmal vor der ersten Migrationsausführung in einer neuen Umgebung aus.

```bash
./bin/console shell
exit
```

### Ausführen der Migration

Das Tool unterstützt zwei Migrationsansätze. Wählen Sie den für Ihren Anwendungsfall passenden aus.

#### Einphasige Migration

Auf der Quellinstanz ist kein Wartungsmodus erforderlich. Führen Sie die vollständige Migrations-Pipeline mit einem einzigen Befehl aus:

```bash
./bin/console migration
```

Der Befehl führt alle Pipeline-Schritte automatisch von Ende zu Ende in der folgenden Reihenfolge aus.

1. **Konfigurationsprüfung** - Validiert Umgebungsvariablen und die Einrichtung von Tools.
1. **Umgebungsinitialisierung** - Startet [!DNL Docker] Services, öffnet Cloud-Tunnel (falls zutreffend) und führt Unit-Tests durch.
1. **Integrationstests und CDMS-Initialisierung** - Führt Integrationstests durch und initialisiert die CDMS-API-Verbindung.
1. **Migration erstellen** - registriert die Migration beim CDMS und wartet auf die Analyse des Zielschemas. Die Migrations-ID wird in `.migration_id` gespeichert.
1. **Funktionstests und Testdatengenerierung** — Führt Funktionstests durch und generiert synthetische Testdaten auf der Quelle zur Integritätsprüfung (falls aktiviert).
1. **Datenextraktion** - Extrahiert Daten aus der Quellinstanz.
1. **In Ziel laden** - Lädt extrahierte Daten in die [!DNL Adobe Commerce as a Cloud Service]. Staging-Ansichten werden auf der Quelle bereinigt, und Quelltestdaten werden parallel zur Last über REST entfernt.
1. **Datenintegritätsprüfung** - Trigger-Prüfsummenüberprüfung und führt lokale API-Überprüfungstests durch. Die Ergebnisse werden protokolliert, und Fehler stoppen die Pipeline nicht.
1. **Bereinigung der Testdaten auf dem Ziel** - Entfernt synthetische Testdaten aus der Zielinstanz.
1. **Ergebnisse verarbeiten** - Erzeugt eine Zusammenfassung der Migration und lädt optional Artefakte aus dem Speicher herunter.

Verwenden Sie diese Option, wenn kein Wartungsfenster erforderlich ist, was typisch für End-to-End-Trockenläufe, Entwicklungs- oder Sandbox-Umgebungen oder für eine Migration ist, bei der die Quelle während der Extraktion live bleiben kann.

>[!WARNING]
>
>Verwenden Sie diese Option nicht, wenn eine eingefrorene Quelle erforderlich ist, z. B. keine Produktionsmigration, bei der während der Extraktion keine neuen Bestellungen oder Datenänderungen auftreten dürfen. Verwenden Sie stattdessen eine stufenweise Migration. Verwenden Sie diesen Befehl nicht als Schritt innerhalb des schrittweisen Wartungs-Workflows.

#### Mehrphasige Migration mit Wartungsmodus

Der Wartungsmodus ist auf der Quellinstanz erforderlich, um die Datenkonsistenz während der Extraktion sicherzustellen. Die Migration ist in verschiedene Phasen unterteilt, die Sie in der richtigen Reihenfolge ausführen müssen.

>[!NOTE]
>
>Zwei verschiedene CLIs sind beteiligt. Die `./bin/console` Befehle werden aus dem Projektstamm des Migrations-Tools ausgeführt. Die `bin/magento maintenance:*` Befehle werden auf dem Quell- [!DNL Adobe Commerce] Anwendungs-Server, über SSH zum Installationsstamm oder über die [!UICONTROL Admin] ausgeführt. Das Tool gibt keine [!DNL Magento] in Ihrem Auftrag aus.

| Phase | Wer betreibt es? | Staat Source |
| --- | --- | --- |
| 1. `migration:before-maintenance` | Tool | Live - Wartung noch nicht aktivieren |
| &#x200B;2. Wartungsmodus aktivieren | Manuell | Übergang zu eingefroren |
| 3. `migration:during-maintenance` | Tool | Eingefroren — Die Wartung darf während dieser Phase nicht deaktiviert werden |
| &#x200B;4. Wartungsmodus deaktivieren | Manuell (bedingt) | Quellinstanz wieder in Betrieb nehmen |
| 5. `migration:cleanup` (optional) | Tool | Live - muss außerhalb der Wartung sein |

**Phase 1 — Vor der Wartung (Quelle ist aktiv)**

Führen Sie aus, während die Quellinstanz live ist und Traffic akzeptiert. Der Zugriff von REST und GraphQL auf die -Quelle muss vollständig verfügbar sein. Aktivieren Sie den Wartungsmodus nicht, bevor diese Phase abgeschlossen ist.

Kehren Sie zum Serverstamm zurück und führen Sie Folgendes aus:

```bash
./bin/console migration:before-maintenance
```

1. **Konfigurationsprüfung** - Validiert Umgebungsvariablen und die Einrichtung von Tools.
1. **Umgebungsinitialisierung** - Startet [!DNL Docker] Services, öffnet PaaS-Cloud-Tunnel (falls zutreffend) und führt Unit-Tests durch.
1. **Integrationstests und CDMS-Initialisierung** - Führt Integrationstests durch und initialisiert die CDMS-API-Verbindung.
1. **Migration erstellen** - registriert die Migration beim CDMS und wartet auf die Analyse des Zielschemas. Die Migrations-ID wird in `.migration_id` gespeichert.
1. **Funktionstests** - Führt Funktionstests für die Live-Quelle durch.
1. **Generieren von Testdaten** - Erstellt Kunden und Bestellungen für synthetische Tests an der Quelle zur Integritätsprüfung (falls aktiviert).

**Phase 2 — Wartungsmodus aktivieren (manuell)**

Aktivieren Sie den Wartungsmodus an der Quelle und pausieren Sie alle Aktivitäten, die in die Datenbank schreiben oder sich auf sie auswirken, einschließlich geplanter Aufträge, Drittanbieterintegrationen, Bestellverarbeitung und Synchronisierung von Medien-Assets.

Führen Sie auf dem Commerce-Quellserver (Installationsstamm) Folgendes aus:

```bash
bin/magento maintenance:enable
```

**Phase 3 — Während der Wartung (Quelle eingefroren)**

Mit der Quellinstanz im Wartungsmodus ausführen. Die Quelle muss für die gesamte Dauer dieser Phase eingefroren bleiben. Deaktivieren Sie den Wartungsmodus erst, wenn **Phase 3** erfolgreich abgeschlossen wurde.

```bash
./bin/console migration:during-maintenance
```

1. **Einrichtung des Cloud** Tunnels - öffnet für [!DNL Adobe Commerce on Cloud] Quellinstanzen erneut Cloud-Tunnel und überprüft die Datenbankkonnektivität. Bei On-Premise-Instanzen wird automatisch übersprungen.
1. **Datenextraktion** - Extrahiert Daten aus der eingefrorenen Quellinstanz.
1. **Staging-Ansichtsbereinigung** - Entfernt Staging-Ansichten über eine direkte Datenbankverbindung aus der Quelle (im Wartungsmodus sicher).
1. **Zu Ziel laden** - Lädt die extrahierten Daten in die [!DNL Adobe Commerce as a Cloud Service] und wartet auf ihren Abschluss.
1. **Datenintegritätsprüfung** - Trigger CDMS-Prüfsummenüberprüfung und Durchführung lokaler API-Überprüfungstests. Die Ergebnisse werden protokolliert, und Fehler stoppen die Pipeline nicht.
1. **Bereinigung der Testdaten auf dem Ziel** - Entfernt synthetische Testdaten aus der Zielinstanz.
1. **Ergebnisse verarbeiten** - Erzeugt eine Zusammenfassung der Migration und lädt optional Artefakte aus dem Speicher herunter.

**Phase 4 — Wartungsmodus deaktivieren (manuell, bedingt)**

In dieser Phase wird der Wartungsmodus deaktiviert, sodass der Traffic zur Quellinstanz wieder aktiviert wird. Dieser Schritt ist erforderlich, bevor die Bereinigungsphase ausgeführt wird, da die Bereinigung über REST mit der Quelle kommuniziert und mit `HTTP 503` fehlschlägt, wenn der Wartungsmodus noch aktiv ist.

Führen Sie auf dem Commerce-Quellserver Folgendes aus:

```bash
bin/magento maintenance:disable
```

**Phase 5 - Bereinigung (optional, Quelle muss live sein)**

Entfernen Sie die in Phase 1 erstellten Kundinnen und Kunden sowie Bestellungen **synthetischen Tests** REST aus der Quellinstanz. Diese Phase kann nur ausgeführt werden, nachdem der Wartungsmodus deaktiviert wurde.

>[!NOTE]
>
>Überspringen Sie diese Phase, wenn `SKIP_TEST_DATA_CREATION=true` in `.env` festgelegt ist, da keine Testdaten erstellt wurden.

Kehren Sie zum Serverstamm zurück und führen Sie Folgendes aus:

```bash
./bin/console migration:cleanup
```

1. **Einrichten der Datenbankverbindung** - öffnet für [!DNL Adobe Commerce on Cloud] Quellinstanzen erneut Cloud-Tunnel. Bei lokalen Instanzen richtet die direkte Datenbankkonnektivität ein und überprüft sie.
1. **Source-REST-Bereinigung** - Entfernt Kunden und Bestellungen synthetischer Tests aus der Quelle über die REST-API.

## Fortsetzen oder erneutes Ausführen einer Migration

Das Migrations-Tool verfolgt den Fortschritt mithilfe einer `.migration_id` Datei im Projektstamm. Diese Datei wird beim Start einer neuen Migration automatisch erstellt und zeichnet die aktuelle Migrationskennung auf.

### Nach einem Fehler fortsetzen

Wenn ein Migrationsdurchgang fehlschlägt oder unterbrochen wird, führen Sie denselben Befehl erneut aus, um ihn vom letzten erfolgreichen Schritt (Extraktion, Laden oder Verifizierung) aus fortzusetzen, anstatt von Grund auf neu zu starten. Bereits abgeschlossene Schritte werden automatisch übersprungen.

>[!IMPORTANT]
>
>Wenn Sie die `migration:during-maintenance` Phase fortsetzen, muss die Quelle während der gesamten Zeit im Wartungsmodus bleiben. Wenn die Quelle aus der Wartung genommen wurde oder die Daten zwischen den Ausführungen geändert wurden, kann die wiederaufgenommene Migration zu inkonsistenten Ergebnissen führen.

### Starten einer neuen Migration

Um einen vorherigen Durchlauf zu verwerfen und eine völlig neue Migration zu starten, löschen Sie die `.migration_id`-Datei, bevor Sie die nächste Migration beginnen:

```bash
rm .migration_id
```

Wenn `.migration_id` vorhanden und die vorherige Migration bereits abgeschlossen ist, druckt das Tool eine Meldung, die besagt, dass die Migration bereits abgeschlossen ist, und empfiehlt, die Datei zu löschen.

## Überprüfen von Protokollen und Debugging

Alle Migrationsprotokolle werden in das `logs/` im Projektstammverzeichnis geschrieben und in Unterverzeichnisse mit Zeitstempel unterteilt:

```text
logs/
  2026-03-23_14-30-00/     ← one directory per run
    index.log              ← main pipeline log (start here)
    ...
```

- `index.log` ist das Haupt-Pipeline-Orchestrierungsprotokoll. Wenn ein Schritt fehlgeschlagen ist, wird angezeigt, welches Skript mit einem Code ungleich null beendet wurde und warum.
- Protokolle für einzelne Schritte, z. B. `09b_run_load.log` und `11_verify_data_integrity_local.log`, enthalten detaillierte Ausgaben für jede Phase.
