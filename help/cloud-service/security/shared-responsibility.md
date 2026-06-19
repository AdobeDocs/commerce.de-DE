---
title: Geteilte Verantwortung
description: Erfahren Sie mehr über die Sicherheitsaufgaben der einzelnen an Ihrem Projekt  [!DNL Adobe Commerce as a Cloud Service]  Parteien.
feature: Cloud, Security
role: Admin, Developer, Leader
level: Intermediate
exl-id: 424fe5cd-5d54-425d-97ce-024476d18dde
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
autotag-review: '2026-06-18T16:19:21.186Z'
TQID: 'https://experienceleague.adobe.com/ZjR9eFTVz8RIrYIN1CxyEgegGoZljXJKrtWZStx-ln0'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
subfeature_v2:
  - id: d9ced453-36f4-4eb5-b2f3-1d593e32476b
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 15a99ce130efaf3a35968cfc01747fe1b6ab93c9
workflow-type: tm+mt
source-wordcount: 340
ht-degree: 0%

---

# Gemeinsames Verantwortungs-, Sicherheits- und Betriebsmodell

[!DNL Adobe Commerce as a Cloud Service] ist ein On-Demand-Service, der sich auf ein Sicherheits- und Betriebsmodell mit gemeinsamer Verantwortung stützt. Adobe und Kunden teilen sich diese Verantwortlichkeiten, wobei jede Partei eine eigene Verantwortung für die Sicherung und den Betrieb des Adobe Commerce-Programms trägt.

>[!BEGINSHADEBOX]

Die folgenden Zusammenfassungstabellen verwenden das RACI-Modell, um die gemeinsamen Sicherheitsaufgaben von Adobe und Kunden aufzuzeigen.

**R** — Verantwortlich
**a** — Rechenschaftspflichtig
**C** — konsultiert
**i** — informiert

>[!ENDSHADEBOX]

| Aufgabe | Adobe | KUNDE |
| --- | --- | --- |
| Definieren der WAF-Ursprungsregeln für das Backend | RA | |
| Definieren von Backend-CDN-WAF-Regeln | RA | |
| Bereitstellung und Wartung [!DNL Adobe Developer App Builder] Anwendungen | | RA |
| Bereitstellen von Backend-Plattform-WAF-Regeln | RA | |
| Bereitstellen von Backend-CDN-WAF-Regeln | RA | |
| Beheben von Kernfehlern in [!DNL Adobe Commerce as a Cloud Service] | RA | I |
| Patches für die [!DNL Adobe Commerce as a Cloud Service]-Infrastruktur veröffentlichen | RA | |
| Skalierung (Infrastruktur) | RA | |
| Skalierung (Hauptanwendung) | RA | |
| Integrieren externer Anwendungen | | RA |
| Installieren von App Builder Apps | | RA |
| Testen der Leistung aller App Builder-Apps | | RA |
| Design und Design von benutzerdefinierten App Builder-Apps | | RA |
| Backend-DNS konfigurieren | RA | I |
| Onboarding-Backend-CDN | RA | I |
| Unterstützen von Backend-CDN | RA | I |
| Beziehen eines Backend-DNS-Anbieters | RA | |
| Bereitstellen der Produktions- und Sandbox-Umgebungen | A | R |
| Zugriff auf Dynamics for Adobe Commerce in der Cloud-Infrastruktur | R | C |
| Beheben von Backend-Kundensicherheitsproblemen | RA | I |
| Beheben von Backend-CDN-Sicherheitsproblemen | RA | |
| Unterstützung von Adobe bei der Sicherheitsforschung (Scans/Audits) | RA | |
| Durchführen von PCI-ASV-Scans | RA | I |
| Wiederherstellen von PCI-Scans für die Adobe Commerce-Infrastruktur | R | |
| Verwalten von Betriebssystem- und Plattformgeheimnissen | RA | |
| Überwachen von Backend-Sicherheitsprotokollen | RA | |
| Steuerung des Kunden-Supports und des Zugriffs | A | R |
| Jährliche Tests und Dokumentation des Adobe DR-Plans sowie der Sicherung und Wiederherstellung | RA | |
| Jährliche Prüfung und Dokumentation des Notfallwiederherstellungsplans | RA | |
| Debugging und Problemisolierung | R | R |
| Rechtzeitige Unterstützung des Debugging- und Problemisolierungsprozesses | R | R |
| Veröffentlichen von Aktualisierungen und Patches in Adobe Commerce Core | RA | I |
| Installieren von Updates und Patches für Adobe Commerce Core | RA | I |
| Qualität der Adobe Commerce-Kernanwendungen | RA | |
