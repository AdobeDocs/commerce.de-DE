---
title: Pflegen genauer und relevanter Inhalte
description: Eine E-Commerce-Plattform ist einer der wichtigsten Interaktionskanäle. Durch nahtlose Aktualisierungen im Asset-Management-System wird sichergestellt, dass Commerce-Storefronts immer die aktuellsten Produktinformationen anzeigen.
feature: CMS, Media, Integration
exl-id: 2c749e84-fcc4-4bf9-90b2-87438329889e
TQID: https://experienceleague.adobe.com/cTeAl0vABSDcqSR9S7pGkV2yGnFHz11VmXtPoE0C86M
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: c18ed297-2187-4aec-affb-9d9654eca6fcid: d1e21356-0064-4f48-9089-16e3f0dbd2a6
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: da3860b0-d637-47df-bef0-273751180266
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 416
ht-degree: 0%

---

# Pflegen genauer und relevanter Inhalte

Eine echte Inhaltsbereitstellung umfasst eine Kombination von Schlüsselpfeilern wie **Erstellung und Produktion**, **Workflow und Planung** und **Bereitstellung und Aktivierung**. Jede dieser Säulen ist für sich genommen wertvoll und trägt dazu bei, einen signifikanten Wert für Unternehmen zu erzielen:

![Schlüsselstützen](../assets/key-pillars.png){width="600" zoomable="yes"}

Eine E-Commerce-Plattform ist einer der wichtigsten Interaktionskanäle. Durch nahtlose Aktualisierungen im Asset-Management-System wird sichergestellt, dass Commerce-Storefronts immer die aktuellsten Produktinformationen anzeigen. Dies ist für die Erreichung der drei Hauptziele eines jeden **DAM (Digital Asset Management System)** &lt;> **Commerce-Integration**:

* Verbesserung **Time-to-Market (TTM** für neue Produkteinführungen.

* Beseitigen Sie betriebliche Ineffizienzen und reduzieren Sie manuelle Interaktionen.

* Stellen Sie die Markenkonsistenz sicher, indem Sie immer genehmigte Inhalte bereitstellen, die den Markenrichtlinien entsprechen.

Um diese Ziele zu erreichen, werden für die AEM Assets-Integration für Commerce sowohl **Adobe Commerce**- als auch **AEM Assets**-Ereignisse abonniert, wodurch eine dynamische Synchronisierung zwischen Inhalten und Commerce sichergestellt wird.

## Adobe Commerce-Katalogänderungen

Die AEM Assets-Integration überwacht die Produkterstellungsereignisse, die ausgelöst werden, wenn Produkte in **Admin** oder mithilfe der **API** erstellt werden. Nach der Auslösung werden genehmigte Assets aus dem DAM synchronisiert, die mit der neuen Produkt-SKU verknüpft sind.

Durch die Entkopplung der Inhaltserstellung vom Katalogmanagement erhalten Unternehmen mehrere Vorteile:

* Content-Teams können unabhängig agieren, sodass hochwertige Assets für die Produkteinführung bereit sind.

* Produktaktualisierungen bleiben schnell, da die Asset-Erstellung Katalogänderungen nicht verzögert, was die Verwaltung neuer Produkte flexibler macht.

* Die Automatisierung verbessert die Effizienz und Genauigkeit und verringert Abweichungen zwischen Produktdaten und zugehörigen Inhalten.

>[!NOTE]
>
> CSV-Produktimporte in PaaS und SaaS führen keine Trigger-Aktualisierungsereignisse durch. Verwenden Sie die -API für Katalogimporte und -aktualisierungen.

## AEM Assets-Lebenszyklusänderungen

Die Integration überwacht auch Asset-Statusänderungen in AEM Assets. Da Adobe Commerce als Interaktionskanal dient, werden in der Storefront nur genehmigte Assets angezeigt.

Die Integration automatisiert die Lebenszyklusverwaltung von Assets, um sicherzustellen, dass die Storefront-Inhalte präzise und markenkonform bleiben.

* Nur genehmigte Assets werden veröffentlicht, wodurch die Markenintegrität und die Einhaltung behördlicher Auflagen gewährleistet bleibt.

* Veraltete oder irrelevante Assets werden automatisch entfernt, sodass veraltete Inhalte nicht angezeigt werden können.

* Die nahtlose Synchronisation zwischen Asset-Genehmigung und Produktanzeige reduziert manuellen Aufwand und Verzögerungen.

Durch die Nutzung der AEM Asset Selector-Integration können Unternehmen eine optimierte, genaue und effiziente Änderung der Inhaltsbereitstellung beibehalten und dadurch sowohl das Kundenerlebnis als auch die betriebliche Effizienz verbessern.
