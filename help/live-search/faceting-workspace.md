---
title: Faceting Workspace
description: Lernen Sie den Facettenarbeitsbereich  [!DNL Live Search] .
exl-id: 7108e41b-44a7-4943-b20f-6ee544d099e9
TQID: https://experienceleague.adobe.com/LsVM4inUqk2EozfVN--FH1Ukggt8A8QBIQXW-SmnxZs
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 33cd0e217447351b690646ec8d230f76060a74da
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 0%

---

# Faceting Workspace

Der Arbeitsbereich *Facettieren* listet alle derzeit verfügbaren Facetten auf und bietet Zugriff auf die Tools, die Sie zum Einrichten und Verwalten von Facetten benötigen. Angeheftete Facetten werden zuerst in der Liste der vorhandenen Facetten angezeigt, gefolgt von dynamischen Facetten. Die Liste kann gefiltert werden, um alle Facetten oder nur die angehefteten oder dynamischen Facetten anzuzeigen.

![Facettierender Arbeitsbereich](assets/faceting-workspace.png)

## Festlegen des Umfangs

Wenn Ihre Adobe Commerce-Installation mehrere Store-Ansichten enthält, setzen Sie **Umfang** auf die [Store-](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings), für die Ihre Facetteneinstellungen gelten.

## Filtern der Liste

1. Klicken Sie auf **Steuerelement** Filtern nach“.
1. Wählen Sie eine der folgenden Optionen:

   * Alle Filter
   * angeheftet
   * Dynamisch

## Facette hinzufügen

1. Klicken Sie **Facetten hinzufügen**.
1. Detaillierte Anweisungen finden [ unter ](facets-add.md) von Facetten hinzufügen .

## Spaltenbeschreibungen

| Spalte | Beschreibung |
|--- |--- |
| (erste Spalte) | Listet angeheftete und dynamische Facetten auf, indem [label](facets-type.md) angegeben wird, dass sie für den Erstkäufer sichtbar sind. |
| Sortiertyp | Die [Sortierreihenfolge](facets-type.md) der Facettenwerte. Facetten werden alphabetisch für alle [!DNL Commerce] sortiert. Bei [Headless]-Implementierungen können Facetten entweder alphabetisch oder nach Anzahl sortiert werden. Optionen: Alphabetisch, Anzahl (nur Headless) |
| Maximaler Wert | Die Anzahl der Facettenwerte, die in der Storefront als Filter verfügbar sind, maximal aber 10. |

## Kontrollen

| Kontrolle | Beschreibung |
|--- |--- |
| Facetten hinzufügen | Öffnet den [Facetteneditor](facets-add.md). |
| Filtern nach | Bestimmt den [Typ von Facetten](facets-type.md) die in der Liste angezeigt werden. Optionen: Alle, angeheftet, dynamisch |
