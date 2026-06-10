---
title: Geteilte Verantwortung
description: Erfahren Sie mehr über die Sicherheitsaufgaben der einzelnen an Ihrem Projekt  [!DNL Adobe Commerce as a Cloud Service]  Parteien.
feature: Cloud, Security
role: Admin, Developer, Leader
level: Intermediate
exl-id: 424fe5cd-5d54-425d-97ce-024476d18dde
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
TQID: 'https://experienceleague.adobe.com/ZjR9eFTVz8RIrYIN1CxyEgegGoZljXJKrtWZStx-ln0'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: bd989d82-1e15-4534-88db-f1f51dd77ffa
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ef32511703a96b5f4db32d54229e9a7cbe961f12
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
