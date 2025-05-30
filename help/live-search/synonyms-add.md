---
title: Synonyme hinzufügen
description: Fügen Sie  [!DNL Live Search]  hinzu, um die Reaktion auf Suchanfragen zu verbessern.
exl-id: 2dc535ea-35a3-45a8-8171-901005223cc9
source-git-commit: 6dcfd0a54e6a6814b7f5708e0c221452b8af4537
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Synonyme hinzufügen

Erhöhen Sie die Kundeninteraktion, indem Sie Ihre eigene kuratierte Liste [!DNL Live Search] Synonyme hinzufügen. [!DNL Live Search] können bis zu 200 Synonyme pro Shop-Ansicht verwalten.

![[!DNL Live Search] Synonyme](assets/synonym-workspace.png)

## Schritt 1: Synonym hinzufügen

1. Gehen Sie im Admin zu **Marketing** > SEO &amp; Search > **[!DNL Live Search]**.
1. Setzen Sie bei mehreren Stores **Bereich** auf die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings), für die die Synonymeinstellungen gelten.
1. Klicken Sie auf die **Synonyme**.
1. Klicken Sie auf **Schaltfläche „Synonyme**&quot;.

## Schritt 2: Synonym nach Typ definieren

Befolgen Sie die Anweisungen für den [Typ des Synonyms](synonyms-type.md) den Sie erstellen möchten.

### Zweiweg-Synonym

1. Akzeptieren Sie die standardmäßige **bidirektionale** Option.

   ![Zwei-Wege-Synonym hinzufügen](assets/synonym-add-two-way.png)

1. Geben Sie den **Keyword**-Begriff oder die zuzuordnende Phrase ein.
1. Geben Sie **Begriffe**Erweiterung) ein, die Sie als Synonyme für das Keyword hinzufügen möchten. Trennen Sie mehrere Begriffe durch Kommas.
In diesem Beispiel lautet das Keyword, mit dem eine Übereinstimmung erzielt werden soll, „Hose“, und die Menge der Ausdehnungsbegriffe lautet „Hose, Hose“.

   ![Beispiel für ein Zwei-Wege-Synonym](assets/synonym-add-two-way-example.png)

1. Klicken Sie abschließend auf **Speichern**.
Die Gruppe von Synonymen wird in der Liste mit einem Pfeil in beide Richtungen zwischen den einzelnen Begriffen angezeigt, was bedeutet, dass die Begriffe austauschbar sind.

   ![Zwei-Wege-Synonym](assets/synonym-two-way.png)

### Einwegsynonym

1. Klicken Sie auf **Einwegsynonym** Typ.

   ![Einwegsynonym hinzufügen](assets/synonym-add-one-way.png)

1. Geben Sie die Begriffe **Keyword** und **Erweiterung** ein. Trennen Sie mehrere Begriffe durch Kommas.

   ![Beispiel für Einwegsynonyme](assets/synonym-add-one-way-example.png)

   In diesem Beispiel ist das Keyword „pants“ und die Einweg-Erweiterungsbegriffe „capris, peddle-pushers“ sind jeweils eine Untergruppe von „pants“, jedoch mit einer bestimmten Bedeutung.

1. Klicken Sie abschließend auf **Speichern**.
Der Satz von Synonymen wird in der Liste mit einem Einwegpfeil angezeigt, der von den Erweiterungsbegriffen auf das Keyword verweist, um anzugeben, dass die Begriffe Untergruppen des Keywords sind. Ein Pluszeichen trennt jeden Expansionsbegriff.

   ![Einwegsynonym](assets/synonym-one-way.png)

## Schritt 3: Änderungen veröffentlichen

1. Wenn Ihre Synonyme vollständig sind, klicken Sie auf **Änderungen veröffentlichen**.
1. Warten Sie bis zu zwei Stunden, bis Ihre Aktualisierungen in der Storefront verfügbar werden.

## Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| [Typ](synonyms.md) | Bestimmt, ob die Synonyme dieselbe Bedeutung wie das Keyword haben oder eine Teilmenge des Keywords sind. options:<br />bidirektional (Standard) - Begriffe, die dieselbe Bedeutung wie das Keyword haben und dieselben Suchergebnisse zurückgeben<br />unidirektional - Begriffe, die eine Teilmenge des Keywords sind. Einwegsynonyme geben eine engere Liste spezifischer Produkte zurück. |
| Schlüsselwort | Ein Wort, das normalerweise mit einer Auswahl von Produkten in Ihrem Katalog verknüpft ist. |
| Expansion | Zusätzliche Begriffe, die dieselbe oder eine ähnliche Bedeutung wie das Keyword haben. |
