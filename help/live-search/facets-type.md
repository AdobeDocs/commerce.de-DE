---
title: Facettenarten
description: '[!DNL Live Search] Facetten sind dynamisch und werden ggf. in der Liste Filter angezeigt.'
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Facettenarten

[!DNL Live Search] verwendet eine Vielzahl von Facettentypen. Sie werden nur dann in der Liste *Filter* angezeigt, wenn sie relevant sind. Die Liste der verfügbaren Facetten ändert sich je nach den zurückgegebenen Produkten. Die folgenden Merkmale beeinflussen ihre Darstellung und ihr Verhalten:

* Facetten angeheftet - Die am häufigsten verwendeten Facetten können oben in der Liste angeheftet werden. Die übrigen Facetten werden in der Reihenfolge *Sortierungstyp* nach den angehefteten Facetten aufgeführt.
* Dynamische Facetten - Produktattribute, die [Adobe Sensei](https://www.adobe.com/sensei.html) am relevantesten für einen Produktsatz und eine Abfrage findet. Die Berechnung berücksichtigt die Attributmetadaten des gesamten Katalogs und bestimmt zum Zeitpunkt der Abfrage die relevantesten Facetten für die Abfrage.

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

Bei [!DNL Commerce] Storefronts wird die Facettenbeschriftung durch die [*Attributeigenschaften*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html?lang=de) bestimmt. Für Stores mit mehreren Ansichten können zusätzliche Beschriftungen unter *Verwalten von Beschriftungen* definiert werden. Bei Headless-Implementierungen werden Beschriftungen aus dem [Facettenarbeitsbereich“ ](faceting-workspace.md).

### Sortiertyp

Alle für die Storefront gerenderten Facetten werden alphabetisch sortiert. Bei Headless-Implementierungen können Facetten alphabetisch oder nach Anzahl sortiert werden.

| Sortiertyp | Beschreibung |
|--- |--- |
| Alphabetisch | In der Liste *Filter* werden Facetten alphabetisch sortiert. |
| Count | (Nur Headless) Bei Headless-Implementierungen können Facetten auch nach der Anzahl der Werte sortiert werden, die pro Facette im aktuellen Satz zurückgegebener Produkte gefunden werden. |
