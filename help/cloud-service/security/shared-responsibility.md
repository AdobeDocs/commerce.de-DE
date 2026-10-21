---
title: Geteilte Verantwortung
description: Erfahren Sie mehr über die Sicherheitsaufgaben der einzelnen an Ihrem [!DNL Adobe Commerce as a Cloud Service]-Projekt beteiligten Parteien.
feature: Cloud, Security
role: Admin, Developer, Leader
level: Intermediate
exl-id: 424fe5cd-5d54-425d-97ce-024476d18dde
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
autotag-review: '2026-06-18T16:19:21.186Z'
TQID: 'https://experienceleague.adobe.com/ZjR9eFTVz8RIrYIN1CxyEgegGoZljXJKrtWZStx-ln0'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: de2e2e68-c5d7-4efe-be7b-27528698f06b
    internal-label: Commerce as a Cloud Service
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
subfeature_v2:
  - id: d9ced453-36f4-4eb5-b2f3-1d593e32476b
    internal-label: Account management
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: 8b3db59ed02539646dd53a2e9c7a0925b7c3a804
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%
---
# Gemeinsames Verantwortungs-, Sicherheits- und Betriebsmodell

[!DNL Adobe Commerce as a Cloud Service] ist ein On-Demand-Service, der sich auf ein Sicherheits- und Betriebsmodell mit gemeinsamer Verantwortung stützt. Adobe und Kunden teilen sich diese Verantwortlichkeiten, wobei jede Partei eine eigene Verantwortung für die Sicherung und den Betrieb des Adobe Commerce-Programms trägt.

[!DNL Adobe Commerce as a Cloud Service with Managed Operations] ist ein Premium-Angebot, das zusätzlich zum standardmäßigen Modell der gemeinsamen Verantwortung einen benannten Customer Success Engineer (CSE) und ein P1-Supportteam für Managed Operations rund um die Uhr hinzufügt. Adobe ist weiterhin Eigentümer der Plattform, der Infrastruktur, der Sicherheit und des Kernprogramms und Sie sind weiterhin Eigentümer Ihrer Anpassungen und Integrationen, aber mit Managed Operations wird Adobe Managed Services zu Ihren folgenden Themen konsultiert:

- Integrationen
- App Builder Apps
- Edge Delivery-Storefront
- Event-Management
- Platform-Updates

Adobe Managed Services ist auch gemeinsam für das Testen, Debuggen und die Isolierung von Problemen bei der Notfallwiederherstellung verantwortlich. Ihr CSE begleitet Sie vom Onboarding über die Live-Schaltung und darüber hinaus, sodass Sie in jeder Phase einen Adobe-Experten haben, anstatt alleine zu arbeiten.

>[!BEGINSHADEBOX]

Die folgenden Zusammenfassungstabellen verwenden das RACI-Modell, um die gemeinsamen Sicherheitsaufgaben von Adobe, Adobe Managed Operations und Kunden anzuzeigen.

**R** — Verantwortlich
**a** — Rechenschaftspflichtig
**C** — konsultiert
**i** — informiert

>[!ENDSHADEBOX]

| Aufgabe | Adobe | Adobe Managed Operations | KUNDE |
| --- | --- | --- | --- |
| Definieren der WAF-Ursprungsregeln für das Backend | RA | | |
| Definieren von Backend-CDN-WAF-Regeln | RA | | |
| Bereitstellung und Wartung [!DNL Adobe Developer App Builder] Anwendungen | | | RA |
| Bereitstellen von Backend-Plattform-WAF-Regeln | RA | | |
| Bereitstellen von Backend-CDN-WAF-Regeln | RA | | |
| Beheben von Kernfehlern in [!DNL Adobe Commerce as a Cloud Service] | RA | | I |
| Patches für die [!DNL Adobe Commerce as a Cloud Service]-Infrastruktur veröffentlichen | RA | | |
| Skalierung (Infrastruktur) | RA | | |
| Skalierung (Hauptanwendung) | RA | | |
| Integrieren externer Anwendungen | | C | RA |
| Installieren von App Builder Apps | | C | RA |
| Testen der Leistung aller App Builder-Apps | | C | RA |
| Design und Design von benutzerdefinierten App Builder-Apps | | C | RA |
| Backend-DNS konfigurieren | RA | | I |
| Onboarding-Backend-CDN | RA | | I |
| Unterstützen von Backend-CDN | RA | | I |
| Beziehen eines Backend-DNS-Anbieters | RA | | |
| Bereitstellen der Produktions- und Sandbox-Umgebungen | A | | R |
| Zugriff auf Dynamics for Adobe Commerce in der Cloud-Infrastruktur | R | | C |
| Beheben von Backend-Kundensicherheitsproblemen | RA | | I |
| Beheben von Backend-CDN-Sicherheitsproblemen | RA | | |
| Unterstützung von Adobe bei der Sicherheitsforschung (Scans/Audits) | RA | | |
| Durchführen von PCI-ASV-Scans | RA | | I |
| Wiederherstellen von PCI-Scans für die Adobe Commerce-Infrastruktur | R | | |
| Verwalten von Betriebssystem- und Plattformgeheimnissen | RA | | |
| Überwachen von Backend-Sicherheitsprotokollen | RA | | |
| Steuerung des Kunden-Supports und des Zugriffs | A | C | R |
| Jährliche Tests und Dokumentation des Adobe DR-Plans sowie der Sicherung und Wiederherstellung | RA | C | |
| Jährliche Prüfung und Dokumentation des Notfallwiederherstellungsplans | RA | RA | |
| Debugging und Problemisolierung | R | R | R |
| Rechtzeitige Unterstützung des Debugging- und Problemisolierungsprozesses | R | R | R |
| Veröffentlichen von Aktualisierungen und Patches in Adobe Commerce Core | RA | C | I |
| Installieren von Updates und Patches für Adobe Commerce Core | RA | C | I |
| Qualität der Adobe Commerce-Kernanwendungen | RA | C | |
