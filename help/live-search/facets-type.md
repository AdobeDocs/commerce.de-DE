---
title: Facettenarten
description: '[!DNL Live Search] Facetten sind dynamisch und werden ggf. in der Liste Filter angezeigt.'
exl-id: cd05c0c5-1028-4d66-951d-0b61c1ecc440
TQID: https://experienceleague.adobe.com/8cO5HLAkJLHHqyL-cYb3USCk4E9q1KSRJQ1fOGK0HB4
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 428
ht-degree: 0%

---

# Facettenarten

[!DNL Live Search] verwendet eine Vielzahl von Facettentypen. Sie werden nur dann in der Liste *Filter* angezeigt, wenn sie relevant sind. Die Liste der verfügbaren Facetten ändert sich je nach den zurückgegebenen Produkten. Die folgenden Merkmale beeinflussen ihre Darstellung und ihr Verhalten:

* Facetten angeheftet - Die am häufigsten verwendeten Facetten können oben in der Liste angeheftet werden. Die übrigen Facetten werden in der Reihenfolge *Sortierungstyp* nach den angehefteten Facetten aufgeführt.
* Dynamische Facetten - Produktattribute, die [Adobe AI](https://business.adobe.com/de/ai.html) am relevantesten für einen Produktsatz und eine Abfrage findet. Die Berechnung berücksichtigt die Attributmetadaten des gesamten Katalogs und bestimmt zum Zeitpunkt der Abfrage die relevantesten Facetten für die Abfrage.

  >[!NOTE]
  >
  >Wenn Sie bemerken, dass in der GraphQL-Abfrageantwort nach dem Erstellen dynamischer Facetten Zeitüberschreitungsfehler auftreten, ändern Sie alle Facetten in Anheftet , um zu sehen, ob dies die Leistungsprobleme behebt.

* Beliebte Facetten - Produktattribute, die am häufigsten in Suchergebnissen vorhanden sind.
* Preisfacetten - Rücksendung von Produkten nach Preisbereich. Sie können die Anzahl der Auswahlen und das Preisintervall im Arbeitsbereich [*Einstellungen*](settings.md) angeben.

Zum Zeitpunkt der Abfrage generiert [!DNL Live Search] die Suchergebnisse in Gruppen dynamischer und beliebter Facetten.

![Facetten - Preis](assets/storefront-search-results-run-price.png)

## Storefront- und Headless-Optionen

Facetten, die für die [!DNL Commerce] Storefront gerendert werden, werden vom Suchadapter verarbeitet, der Anfragen weiterleitet und die Ergebnisse in der Storefront rendert. Alle [!DNL Commerce] Facetten der Storefront werden alphabetisch mit Einzelauswahloptionen sortiert, unabhängig vom Eingabetyp, der dem entsprechenden Attribut zugewiesen ist. In der Storefront verfügbare Facetten werden entsprechend dem aktuellen Design gerendert und spiegeln alle Anpassungen wider, die an der Präsentation der mehrschichtigen Navigation vorgenommen wurden.

Im Gegensatz dazu werden [Headless](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/)-Implementierungen von der API verarbeitet und unterstützen zusätzliche Optionen. Headless-Facetten können alphabetisch oder nach Anzahl sortiert werden und entweder Einzel- oder Mehrfachauswahl-Optionen haben.

### Facettenbeschriftungen

Bei [!DNL Commerce] Storefronts wird die Facettenbeschriftung durch die [*Attributeigenschaften*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html?lang=de) bestimmt. Für Stores mit mehreren Ansichten können zusätzliche Beschriftungen unter *Verwalten von Beschriftungen* definiert werden. Bei Headless-Implementierungen werden Beschriftungen aus dem [Facettenarbeitsbereich“ &#x200B;](faceting-workspace.md).

### Sortiertyp

Alle für die Storefront gerenderten Facetten werden alphabetisch sortiert. Bei Headless-Implementierungen können Facetten alphabetisch oder nach Anzahl sortiert werden.

| Sortiertyp | Beschreibung |
|--- |--- |
| Alphabetisch | In der Liste *Filter* werden Facetten alphabetisch sortiert. |
| Count | (Nur Headless) Bei Headless-Implementierungen können Facetten auch nach der Anzahl der Werte sortiert werden, die pro Facette im aktuellen Satz zurückgegebener Produkte gefunden werden. |
