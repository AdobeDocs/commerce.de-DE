---
title: Typen von Commerce-Daten
description: Erfahren Sie, welche Datentypen Sie erfassen und an die Experience Platform senden können.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 6354963c-f27f-4e69-9ecb-acb4befb7c2a
TQID: 'https://experienceleague.adobe.com/LXMqOhHAZpUHaCeeU5ioKKXVrkLftospQEPDd9H-MD8'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: 76e77db86adecdbd3be76040970c0d0899c34cdc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%
---
# Typen von Commerce-Daten

Die [Datenverbindungserweiterung](overview.md) verbindet Ihre Commerce-Daten mit Experience Platform. Daten, die in Experience Platform verwendet werden können, sind in zwei Verhaltenstypen unterteilt: Zeitreihendaten, die zur Klasse **Erlebnisereignis** gehören, und Datensatzdaten, die zur Klasse **Individuelles Profil** gehören.

Weitere Informationen über [Datenverhalten](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition#data-behaviors) und [Klassen](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition#class) in Experience Platform.

## Zeitreihendaten

Zeitreihendaten liefern eine Momentaufnahme des Systems zu dem Zeitpunkt, zu dem eine Aktion entweder direkt oder indirekt von einem Datensatzsubjekt durchgeführt wurde. Wenn ein Käufer beispielsweise ein Produkt auf Ihrer Site durchsucht, ein Produkt zum Warenkorb hinzufügt, eine Bestellung aufgibt usw. Zeitreihendaten werden mithilfe eines Schemas in Experience Platform aufgenommen, bei dem die Klasse auf „Erlebnisereignis **festgelegt**.

### Erfasste Zeitreihendaten

Unter [Verhaltensereignisse](events.md) und [Backoffice-Ereignisse](events-backoffice.md) erfahren Sie, welche Daten erfasst werden, wenn ein Zeitreihenereignis generiert wird.

### Zum Aufnehmen von Zeitreihen-Ereignisdaten erforderliches Schema

Erfahren Sie, wie [ein Schema erstellen](update-xdm.md) das Verhaltens- und Backoffice-Zeitreihen-Ereignisdaten aufnehmen kann.

## Datensatzdaten

Datensatzdaten liefern Informationen über die Attribute eines Subjekts. Ein Subjekt kann eine Organisation oder eine Einzelperson sein. Beispiel: Ein Käufer auf Ihrer Site erstellt ein Konto, das Datensatzdaten generiert. Diese Daten werden mithilfe eines Schemas in die Experience Platform aufgenommen, bei dem die Klasse auf &quot;**&quot; festgelegt**. Sie können diese Datensatzdaten an den Profilverwaltungs- und Segmentierungs-Service von Adobe senden: [Real-Time CDP](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview).

### Erfasste Profildatensatzdaten

Unter [Kundenprofildatensatzdaten](events-profilerecord.md) erfahren Sie, welche Daten erfasst werden, wenn ein Profildatensatz generiert wird.

### Zum Aufnehmen von Profildatensatzdaten erforderliches Schema

Erfahren Sie, wie [ein Schema erstellen](profile-data.md) das Profildatensatzdaten aufnehmen kann.
