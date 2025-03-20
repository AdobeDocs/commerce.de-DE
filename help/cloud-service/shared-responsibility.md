---
title: Geteilte Verantwortung
description: Erfahren Sie mehr über die Sicherheitsaufgaben der einzelnen an Ihrem Projekt  [!DNL Adobe Commerce as a Cloud Service]  Parteien.
role: Admin, Architect, Leader
exl-id: 424fe5cd-5d54-425d-97ce-024476d18dde
source-git-commit: d38066b6db7da5bb029391716063ed098be1f519
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Gemeinsames Verantwortungs-, Sicherheits- und Betriebsmodell

{{accs-early-access}}

[!DNL Adobe Commerce as a Cloud Service] ist ein On-Demand-Service, der sich auf ein Sicherheits- und Betriebsmodell mit gemeinsamer Verantwortung stützt. Diese Zuständigkeiten teilen sich Adobe und seine Kunden. Jede Partei ist für die Sicherung und den Betrieb des Adobe Commerce-Programms verantwortlich.

>[!BEGINSHADEBOX]

Die folgenden Zusammenfassungstabellen verwenden das RACI-Modell, um die gemeinsamen Sicherheitsaufgaben von Adobe und Kunden aufzuzeigen.

**R** — Verantwortlich
**a** — Rechenschaftspflichtig
**C** — konsultiert
**i** — informiert

>[!ENDSHADEBOX]

| Aufgabe | Adobe | KUNDE |
| --- | --- | --- |
| Anwenden von Adobe Commerce-Infrastrukturpatches | RA | |
| Anwenden von Patches auf unterstützende Services (z. B. Nginx oder MySQL) | RA | |
| Definieren der WAF-Ursprungsregeln für das Backend | RA | |
| Definieren von Backend-CDN-WAF-Regeln | RA | |
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
