---
title: Checkliste für die Kundenbereitschaft
description: Erfahren Sie, wie Sie sich mit einer Checkliste zur Bereitschaft, die die Interaktion, den Computer, die Quelle und das Ziel abdeckt, auf eine Massendatenmigration zu Adobe Commerce as a Cloud Service vorbereiten.
feature: Cloud
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
role: Developer
level: Intermediate
autotag-review: '2026-07-22T19:19:18.443Z'
TQID: 'https://experienceleague.adobe.com/728hkK-dzIPzyuBhuNyOqEE9FxlVGdVc9R2wIRcXobk'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: c32adafa-ed01-4b31-997e-2413013911b0
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
source-wordcount: 1171
ht-degree: 0%

---

# Checkliste für die Kundenbereitschaft

{{bulk-data-early-access}}

Verwenden Sie diese Checkliste, um sich mit dem Tool für die Massendatenmigration auf eine Datenmigration von einer [!DNL Adobe Commerce on Cloud] oder lokalen Instanz [!DNL Adobe Commerce as a Cloud Service] vorzubereiten.

Das Migrations-Tool wird als Teil des Interaktionsprozesses mit dem von Commerce bereitgestellten Engineering (CDE) bereitgestellt. Der Zugriff auf das Tool erfolgt aufgrund einer unterzeichneten CDE-Vereinbarung und ist nicht öffentlich verfügbar.

Diese Checkliste enthält, was vor der Freigabe des Tools vorhanden sein muss ([Schritt 1](#stage-1-before-tool-access)) und was Sie benötigen, um mit der Konfiguration und Ausführung des Tools zu beginnen, sobald Sie das Tool haben ([Schritt 2](#stage-2-before-running-the-migration)). Überprüfen Sie diese Checkliste frühzeitig mit Ihrem Adobe-Team, da einige Elemente die Koordinierung mit Adobe erfordern.

## Schritt 1: vor dem Tool-Zugriff

Füllen Sie Folgendes aus oder bestätigen Sie es, bevor Sie das Migrations-Tool und die Dokumentation bereitstellen.

- **CDE-**: Eine unterzeichnete, von Commerce bereitgestellte Entwicklungsvereinbarung muss vorhanden sein. Der Tool-Zugriff wird beim Abschluss-Sign-Schritt des Code-Lebenszyklus gewährt. Abstimmung mit Ihrem Adobe-Team
- **Scoping Questionnaire Completed** - Während der CDE-Ermittlung wird ein Scoping-Fragebogen ausgefüllt, um zu bestätigen, dass die Migration mit den aktuellen Tool-Funktionen durchführbar ist, und um den Datenspeicherbedarf und die Komplexität zu bewerten. Stellen Sie sicher, dass Sie dies mit Ihrem Adobe-Team abschließen, bevor Sie fortfahren.
- **Keine HIPAA-Daten bestätigt** - Die Quellinstanz darf keine HIPAA-regulierten Daten enthalten. Bestätigen Sie dies, bevor Sie fortfahren.
- **Bereitgestellte IP-**: Geben Sie Ihrem Adobe-Team die Liste der statischen IP-Adressen, von denen aus das Migrations-Tool ausgeführt werden soll. Dies ist erforderlich, damit der Netzwerkzugriff auf der Adobe-Seite konfiguriert werden kann.
- **Zielinstanz bereitgestellt** - Die Zielinstanz muss [!DNL Adobe Commerce as a Cloud Service] bereitgestellt werden, bevor die Migration beginnt. Stimmen Sie sich mit Ihrem Adobe-Team ab, um zu bestätigen, dass die Instanz bereit ist.

## Schritt 2: vor Ausführung der Migration

Nachdem Sie Zugriff auf das Tool haben, sollten Sie die folgenden Elemente vorbereiten, bevor Sie mit der Konfiguration und Ausführung beginnen.

### Migrationsmaschine

Das Migrations-Tool wird auf einem von Ihnen gesteuerten Computer ausgeführt, z. B. auf einem speziellen Sprungfeld. Diese Maschine muss folgende Anforderungen erfüllen.

- **[!DNL Docker]und [!DNL Docker Compose] installiert** - Das Tool ist [!DNL Docker]. Sowohl `docker` als auch `docker compose` (oder die veraltete `docker-compose`) müssen auf dem Migrationsrechner installiert sein und funktionieren.
- **[!DNL Docker]Ausführungsberechtigungen** - Der Benutzer, der die Migration ausführt, muss berechtigt sein, [!DNL Docker] Befehle auszuführen. Am [!DNL Linux] muss der Benutzer in der `docker` sein. Auf [!DNL macOS] und [!DNL Windows] muss [!DNL Docker Desktop] ausgeführt werden und zugänglich sein.
- **Schreibfähiger Arbeitsordner** - Das Verzeichnis, in das das Migrations-Tool extrahiert wird, muss vom Migrationsbenutzer vollständig schreibbar sein. Das Tool schreibt Protokolle, Cache, [!DNL Composer] und generierte Dateien während der Ausführung.
- **Ausreichend Speicherplatz** - Stellen Sie sicher, dass ausreichend freier Speicherplatz für extrahierte Daten, [!DNL Docker] Bilder und Protokollausgaben vorhanden ist. Der erforderliche Speicherplatz hängt von der Größe der Quelldatenbank ab.
- **On-Premise-Quellen: Direkte Datenbankkonnektivität vom Migrationsrechner** - Für lokale Quellinstanzen muss der Migrationsrechner über direkten Netzwerkzugriff auf die Quelldatenbank verfügen. Das Tool stellt nicht automatisch eine lokale Datenbankkonnektivität her. Vergewissern Sie sich, dass der Host, der Port und die Anmeldeinformationen vom Migrationscomputer aus erreichbar sind, bevor Sie einen Migrationsbefehl ausführen.
- **Cloud-CLI installiert und SSH-Schlüssel registriert** - Für [!DNL Adobe Commerce on Cloud] Quellinstanzen muss die [Cloud-CLI](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview) auf dem Migrationsrechner installiert sein. Ihr öffentlicher SSH-Schlüssel muss ebenfalls in Ihrem Konto registriert sein. Anweisungen finden Sie [&#x200B; „Handbuch &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/secure-connections) gesicherter Verbindungen“.

### Source-Instanz

- **Zugriff auf Source Store-APIs** — Der Zugriff auf die REST- und GraphQL-APIs des Quellspeichers muss vom Migrationsrechner aus möglich sein. Stellen Sie sicher, dass keine HTTP-Autorisierungs- oder Netzwerkeinschränkung den API-Traffic an die Quell-URL blockiert.
- **Source OAuth-Anmeldeinformationen** - Das Migrations-Tool verwendet OAuth zur Authentifizierung beim Quellspeicher. Erstellen oder bestätigen Sie eine Integration in der Quelle [!UICONTROL **Admin**] ([!UICONTROL **System**] > [!UICONTROL **Erweiterungen**] > [!UICONTROL Integrations]) und halten Sie den Consumer Key, das Consumer Secret, das Access Token und das Access Token Secret bereit.
- **PaaS-Quellen: Magento Cloud-API** Token - Generieren Sie ein [!DNL Cloud]-API-Token aus Ihren [Cloud-Kontoeinstellungen](https://accounts.magento.cloud) unter [!UICONTROL **Kontoeinstellungen**] > [!UICONTROL **API-Token**]. Nur erforderlich, wenn die Quelle eine [!DNL Adobe Commerce on Cloud] ist.
- **Source-Datenbankanmeldeinformationen** - (nur On-Premise) Die Details der Quell- [!DNL MySQL] Datenbankverbindung müssen konfiguriert werden: `host`, `port`, `user`, `password` und `database`.
- **Möglichkeit, Cron anzuhalten** - Sie müssen in der Lage sein, Cron auf der Quellinstanz für die Dauer der Datenextraktion zu stoppen, um gleichzeitige Schreibvorgänge zu verhindern.
- **Möglichkeit, Integrationen und Hintergrundaufträge anzuhalten** - Alle Drittanbieterintegrationen (ERP, OMS, PIM), geplanten Aufträge oder Hintergrundprozesse, die in die Quelldatenbank schreiben, müssen für das Extraktionsfenster angehalten werden.
- **Möglichkeit, den Wartungsmodus zu aktivieren und zu deaktivieren** - (Nur stufenweise Migration) Wenn Sie eine stufenweise Migration mit einem Wartungsfenster ausführen, müssen Sie in der Lage sein, den Wartungsmodus auf der Quellinstanz zu aktivieren und zu deaktivieren.

### Zielinstanz

- **Mandanten-ID und Organisations-ID bestätigt** - Beziehen Sie vor der Konfiguration Ihre `TARGET_TENANT_ID` und `TARGET_ORG_ID` von Ihrem Adobe-Team.
- **IMS OAuth Server-zu-Server-Anmeldeinformationen** - Erforderlich, damit sich das Migrations-Tool beim Ziel authentifizieren kann. Generiert über die [Adobe Developer Console](https://developer.adobe.com/console/). Sie benötigen [!UICONTROL Developer] oder [!UICONTROL Admin] Zugriff auf Ihre Adobe-Organisation, da der einfache Benutzerzugriff zum Erstellen von Anmeldeinformationen nicht ausreicht. Stimmen Sie sich mit Ihrem Adobe-Team ab, um das richtige Produktprofil auszuwählen, und halten Sie die Client-ID (`ADOBE_IMS_CLIENT_ID`) und das Client-Geheimnis (`ADOBE_IMS_CLIENT_SECRET`) bereit.
- **CDMS-Endpunkt-URL** - von Ihrem Adobe-Team bereitgestellt. Versuchen Sie nicht, diesen Wert abzuleiten. Sie benötigen sowohl den Vorproduktions-Endpunkt für Sandbox- und Testmigrationen als auch den Produktions-Endpunkt für Live-Cutover-Migrationen.
- **Kernkonfiguration, die zwischen Quelle und Ziel abgestimmt ist** - Kernkonfigurationsdaten wie Store-Einstellungen und Systemkonfiguration werden vom Tool nicht migriert. Richten Sie sie vor der Migration manuell auf dem Ziel so ein, dass sie mit der Quelle übereinstimmt.
- **B2B-Stores: B2B-Funktionen konsistent konfiguriert** - Wenn die Quelle ein B2B-fähiger Store ist, stellen Sie sicher, dass die relevanten B2B-[!UICONTROL Admin]-Einstellungen vor der Migration sowohl auf der Quelle als auch auf dem Ziel konsistent konfiguriert sind. Die [&#x200B; erforderlichen Einstellungen finden Sie &#x200B;](migration-guide.md) Migrationshandbuch .

### Migrationsplanung

- **Migrationsansatz entschieden** - Bestimmen Sie vor dem Start, welcher Ansatz zu Ihrem Anwendungsfall passt.
  - Einphasige Migration - kein Wartungsmodus erforderlich. Eignet sich für Trockenläufe, Entwicklungs- oder Sandbox-Umgebungen oder jede Migration, bei der die Quelle während der Extraktion live bleiben kann.
  - Mehrphasenmigration - Wartungsmodus ist erforderlich. Eine mehrphasige Migration ist für Produktionsmigrationen erforderlich, bei denen die Quelle während der Extraktion eingefroren werden muss, um die Datenkonsistenz sicherzustellen.
- **Wartungsfenster geplant** — Gilt nur für mehrphasige Migrationen. Planen und kommunizieren Sie das Wartungsfenster im Voraus. Die Quellinstanz steht Endbenutzern während der Extraktions- und Ladephasen nicht zur Verfügung.
- **Store-Ansicht-Code bestätigt** - Identifizieren Sie den Store-Ansicht-Code (`STORE_CODE`) in der Quellinstanz. Standardmäßig ist `default` festgelegt, aber der tatsächliche Code muss unter [!UICONTROL Admin] > [!UICONTROL Stores] > [!UICONTROL All Stores] übereinstimmen. Ein falscher Speicher-Code kann Datenvorgänge während der Migration beeinträchtigen.

Nachdem Sie alle Elemente bestätigt haben, können Sie den Zugriff auf den Service mit dem [Migrationshandbuch für den Service](cdms-access.md) überprüfen und dann die Konfigurations- und Ausführungsschritte im [Migrationshandbuch](migration-guide.md) starten.
