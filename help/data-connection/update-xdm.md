---
title: Aktualisieren von Zeitreihen-Ereignisschemata für die Datenaufnahme in Commerce
description: Erfahren Sie, wie Sie ein Schema, einen Datensatz und einen Datenstrom erstellen, um Zeitreihen-Ereignisdaten für die Datenaufnahme in Commerce zu erfassen und zu senden.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Aktualisieren von Zeitreihen-Ereignisschemata für die Datenaufnahme in Commerce

Einer der [&#x200B; Onboarding-Schritte &#x200B;](overview.md#onboarding-steps) Verwendung der [!DNL Data Connection]-Erweiterung besteht darin, auf den Arbeitsbereich Datenstrom zuzugreifen und [einen &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de) zu erstellen), der speziell für Adobe Commerce gilt. Wenn Sie diesen Datenstrom erstellen, müssen Sie auch ein Schema auswählen, das die Daten beschreibt, die Sie aufnehmen möchten. Dieses Schema muss Commerce-spezifische Feldergruppen enthalten.

In diesem Artikel erhalten Sie die Feldergruppen, die Ihr Schema enthalten muss, um die folgenden von den Adobe Commerce-Ereignissen bereitgestellten Zeitreihendaten erfolgreich zu erfassen:

- [Verhalten](events.md) - Umfasst Storefront, Profil, Suche und B2B-Ereignisse.
- [Back Office](events-backoffice.md) - Enthält den Bestellstatus und Profilereignisse.

Weitere Informationen zu [Zeitreihendaten](data-ingestion.md).

Erfahren Sie mehr über [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=de).

## Schema mit Verhaltens- und Backoffice-Ereignisdaten der Zeitreihen aktualisieren

In diesem Abschnitt erfahren Sie, wie Sie Ihr vorhandenes Schema aktualisieren oder ein Schema erstellen, um Verhaltens- und Backoffice-Ereignisdaten einzuschließen.

>[!NOTE]
>
>Informationen [&#x200B; Hinzufügen profilspezifischer Felder finden &#x200B;](#time-series-profile-event-data) unter von Zeitreihen-Profilereignisdaten .

1. Wenn Sie noch kein Schema haben, erstellen [&#x200B; eines](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=de#create) wobei die Klasse auf &quot;**&quot;**.

1. [Fügen Sie &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=de#add-field-groups) folgenden Commerce-spezifischen Feldergruppen hinzu (oder bearbeiten Sie Ihr vorhandenes Schema und fügen Sie diese Feldergruppen hinzu):

   - Site-Suche
   - Web-Seite besuchen
   - Benutzer-Anmeldeprozess
   - Referenzschlüssel
   - Persönliche Kontaktdaten
   - Kanaldetails
   - Commerce-Details
   - Adobe Analytics ExperienceEvent Commerce (wenn Sie Daten an Adobe Analytics senden möchten)

   >[!NOTE]
   >
   > Legen Sie keine Commerce-spezifischen Feldergruppen als `Primary identity` fest. Dadurch wird das Feld als erforderlich identifiziert, und Experience Platform erwartet dieses Feld bei jedem Ereignis. Wenn dieses Feld fehlt, schlägt die Datenaufnahme fehl.

   Ihr Schema enthält jetzt Commerce-spezifische Feldergruppen, sodass die Zeitreihendaten, die aus den Commerce-Ereignissen [Verhalten](events.md) und [Back Office](events-backoffice.md) erfasst wurden, im Schema dargestellt werden.

1. [Aktivieren](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=de#profile) Sie das Schema für das Profil.

   Wenn ein Schema für das Profil aktiviert ist, werden alle Datensätze, die aus diesem Schema erstellt werden, in Real-Time CDP einbezogen, wobei Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht jedes Kunden zu erstellen.

1. [Erstellen eines Datensatzes](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=de#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema.

   Ein Datensatz ist ein Konstrukt zur Datenspeicherung und -verwaltung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. [Erstellen Sie einen Datenstrom](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de) und wählen Sie das Schema aus, das die Commerce-spezifischen Feldergruppen und den entsprechenden Datensatz enthält.

   Der Datenstrom leitet die erfassten Daten an den Datensatz weiter. Die Daten werden im Datensatz basierend auf dem ausgewählten Schema dargestellt.

Mit den Schemata, Datensätzen und Datenströmen, die für Verhaltens- und Backoffice-Daten konfiguriert sind, können [&#x200B; Ihre Commerce](connect-data.md#data-collection)Instanz so konfigurieren, dass diese Daten erfasst und an Experience Platform gesendet werden.

Informationen zum Einschließen der Profilinformationen Ihres Kunden finden Sie unter [Zeitreihen-Profilereignisdaten](#time-series-profile-event-data).

## Zeitreihen-Profilereignisdaten

Zeitreihen-Profilereignisdaten werden aus den folgenden Ereignissen generiert:

- [`accountCreated`](events-backoffice.md#accountcreated)
- [`accountUpdated`](events-backoffice.md#accountupdated)
- [`accountDeleted`](events-backoffice.md#accountdeleted)

Wenn Sie die Profilereignisdaten Ihres Kunden in die Experience Platform aufnehmen möchten, können Sie Ihr bestehendes Commerce-Schema aktualisieren und denselben bereits konfigurierten Datenstrom verwenden. Alternativ können Sie einen profilspezifischen Datenstrom und ein Schema erstellen. Diese Entscheidung basiert auf der Data Governance Ihres Unternehmens. Die nächsten beiden Abschnitte führen Sie durch beide Fälle.

### Senden von Zeitreihen-Profilereignisdaten an Experience Platform mithilfe Ihres vorhandenen Datenstroms

Wenn Sie Zeitreihen ([&#x200B; Profilereignisdaten) zu &#x200B;](events-backoffice.md#customer-profile-events-server-side) vorhandenen Commerce-Datenstrom hinzufügen möchten, fügen Sie die `Demographic Details` Feldergruppe zu Ihrem Schema hinzu. Ihr Schema enthält jetzt die folgenden Commerce-spezifischen Feldergruppen:

- Site-Suche
- Web-Seite besuchen
- Benutzer-Anmeldeprozess
- Referenzschlüssel
- Persönliche Kontaktdaten
- Kanaldetails
- Commerce-Details
- Adobe Analytics ExperienceEvent Commerce (wenn Sie Daten an Adobe Analytics senden möchten)
- Neu: **Demografische Details**

Durch Hinzufügen der `Demographic Details` Feldergruppe in Ihrem bestehenden Commerce-Schema werden der Datensatz und der Datenstrom, die bereits mit Ihrem Commerce-Schema verknüpft sind, für diese Zeitreihen-Profildaten verwendet.

### Senden von Zeitreihen-Profilereignisdaten an Experience Platform in einem separaten Datenstrom

Wenn Sie ([&#x200B; Profilereignisdaten) zu &#x200B;](events-backoffice.md#customer-profile-events-server-side) neuen profilspezifischen Datenstrom und Schema hinzufügen möchten, führen Sie die folgenden Schritte aus.

1. [Erstellen Sie &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=de#create) Schema und legen Sie die Klasse auf **Erlebnisereignis** fest.

1. [Hinzufügen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=de#add-field-groups) die folgenden profilspezifischen Feldergruppen:

   - Demografische Details
   - Persönliche Kontaktdaten
   - Kanaldetails
   - Commerce-Details

1. [Aktivieren](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=de#profile) Sie das Schema für das Profil.

   Wenn ein Schema für das Profil aktiviert ist, werden alle Datensätze, die aus diesem Schema erstellt werden, in Real-Time CDP einbezogen, wobei Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht jedes Kunden zu erstellen.

1. [Erstellen Sie einen &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=de#create-a-dataset) basierend auf dem von Ihnen erstellten Schema.

   Ein Datensatz ist ein Konstrukt zur Datenspeicherung und -verwaltung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. [Erstellen Sie einen Datenstrom](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=de) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen und den entsprechenden Datensatz enthält.

   Der Datenstrom leitet die erfassten Daten an den Datensatz weiter. Die Daten werden im Datensatz basierend auf dem ausgewählten Schema dargestellt.

Mit den Schemata, Datensätzen und Datenströmen, die für Kundenprofildaten konfiguriert sind, können [&#x200B; Ihre Commerce](connect-data.md#data-collection)Instanz so konfigurieren, dass diese Daten erfasst und an Experience Platform gesendet werden.

Informationen zum Erstellen eines Schemas, Datensatzes und Datenstroms für Profildatensatzdaten finden Sie unter [Senden von Profildatensatzdaten an Experience Platform](profile-data.md).
