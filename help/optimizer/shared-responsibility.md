---
title: Geteilte Verantwortung
description: Erfahren Sie mehr über die Sicherheitsaufgaben der einzelnen an Ihrem Projekt  [!DNL Adobe Commerce Optimizer]  Parteien.
role: Admin, Architect, Leader
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 7c407bfc2becfb0ba6babe5958bcb790c178f406
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Gemeinsames Verantwortungs-, Sicherheits- und Betriebsmodell

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
| Anwenden von Patches auf unterstützende Services | RA | |
| Definieren der WAF-Ursprungsregeln für das Backend | RA | |
| Definieren von Backend-CDN-WAF-Regeln | RA | |
| Bereitstellen von Backend-Plattform-WAF-Regeln | RA | |
| Bereitstellen von Backend-CDN-WAF-Regeln | RA | |
| Beheben von Fehlern in [!DNL Adobe Commerce Optimizer] | RA | I |
| Freigabe [!DNL Adobe Commerce Optimizer]Infrastruktur-Patches | RA | |
| Skalierung (Infrastruktur) | RA | I |
| Integrieren externer Anwendungen | | RA |
| Installieren von App Builder Apps | | RA |
| Testen der Leistung aller App Builder-Apps | | RA |
| Design und Design von benutzerdefinierten App Builder-Apps | | RA |
| Backend-DNS konfigurieren | RA |  |
| Onboarding-Backend-CDN | RA |  |
| Unterstützen von Backend-CDN | RA |  |
| Beziehen eines Backend-DNS-Anbieters | RA | |
| Bereitstellen der Produktions- und Sandbox-Umgebungen | A | R |
| Zugriff auf Dynamics für Adobe Commerce Optimizer | R | C |
| Beheben von Backend-Kundensicherheitsproblemen | RA | I |
| Beheben von Backend-CDN-Sicherheitsproblemen | RA | |
| Unterstützung von Adobe bei der Sicherheitsforschung (Scans/Audits) | RA | |
| Durchführen von PCI-ASV-Scans | RA | I |
| Wiederherstellen von PCI-Scans für die Adobe Commerce Optimizer-Infrastruktur | R | |
| Verwalten von Betriebssystem- und Plattformgeheimnissen | RA | |
| Überwachen von Backend-Sicherheitsprotokollen | RA | |
| Steuerung des Kunden-Supports und des Zugriffs | A | R |
| Jährliche Tests und Dokumentation des Adobe DR-Plans sowie der Sicherung und Wiederherstellung | RA | |
| Jährliche Prüfung und Dokumentation des Notfallwiederherstellungsplans | RA | |
| Debugging und Problemisolierung | R | R |
| Rechtzeitige Unterstützung des Debugging- und Problemisolierungsprozesses | R | R |
| Installieren von Updates und Patches für Adobe Commerce Optimizer | RA | I |
| Qualität der Adobe Commerce Optimizer-Kernanwendungen | RA | |
