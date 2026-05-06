---
title: Verbinden [!DNL Adobe Commerce] mit [!DNL Adobe LLM Optimizer]
description: Aktivieren Sie die erforderlichen Commerce-Services, konfigurieren Sie die LLM Optimizer-Verbindung, überprüfen Sie den Katalogzugriff und bestätigen Sie die Bereitschaft des Mandanten, bevor Sie Opportunities prüfen oder Updates bereitstellen.
role: Admin, User
recommendations: noCatalog
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
source-git-commit: 47348a44ff7c5f890c10594f44cae6e771be046f
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# [!DNL Adobe Commerce] mit [!DNL Adobe LLM Optimizer] verbinden

>[!IMPORTANT]
>
>Der Zugriff auf diese Integration ist eingeschränkt. Weitere Informationen erhalten Sie von Ihrem technischen Kundenbetreuer.

In diesem Artikel wird erläutert, wie Sie Ihren [!DNL Adobe Commerce] mit LLM Optimizer verbinden.

>[!NOTE]
>
>Dieser Artikel konzentriert sich auf den Commerce-Teil der Integration. Allgemeine Informationen zu LLM Optimizer finden Sie in der [LLM Optimizer-Produktdokumentation](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/home).

## Aktivieren der erforderlichen Commerce-Services {#enable-commerce-services}

Arbeiten Sie mit Ihrem Commerce-Administrator oder Implementierungspartner zusammen, um Folgendes sicherzustellen:

- Katalogdaten, die LLM Optimizer lesen muss **werden gemäß Ihrer** exportiert oder synchronisiert (einschließlich SaaS-Datenexporteur oder -Connector in Ihrer Bereitstellung).
- API-Zugriff, Anmeldeinformationen und Umgebungs-URLs (Sandbox vs. Produktion) stimmen mit dem **Mandanten** überein, den Sie in LLM Optimizer verwenden möchten.

## Konfigurieren der Commerce-Verbindung in LLM Optimizer {#configure-commerce-connection}

**So konfigurieren Sie die Commerce-Verbindung:**

1. Öffnen Sie in der [!DNL Adobe LLM Optimizer]-Benutzeroberfläche **Kundenkonfiguration** und wählen Sie dann die Registerkarte **[!UICONTROL Commerce]** aus.

   ![Commerce-Konfiguration auf der Registerkarte „Kundenkonfiguration“](../assets/llmo-commerce-config.png)

1. Klicken Sie auf **[!UICONTROL Add Store View]** , um eine neue Zeile zu erstellen, oder erweitern Sie einen vorhandenen Store-Ansichtseintrag, um sie zu bearbeiten.
1. Geben Sie den **[!UICONTROL Store View URL]** ein (erforderlich).

   Verwenden Sie die Storefront-URL für diese Store-Ansicht, einschließlich beliebiger Gebietsschemata oder Pfadpräfixe (z. B. `https://brand.example.com/` oder `https://brand.example.com/fr/`).

1. Geben Sie den **[!UICONTROL Environment ID]** (erforderlich) ein, d. h. die Kennung für die Adobe Commerce-Umgebung, mit der LLM Optimizer eine Verbindung herstellen soll.
1. Geben Sie **[!UICONTROL Website Code]**, **[!UICONTROL Store Code]** und **[!UICONTROL Store View Code]** ein (erforderlich).

   Diese Werte müssen mit den Codes in Ihrem Commerce-Admin für die Website-, Store- und Store-Ansicht übereinstimmen, mit der Sie eine Verbindung herstellen.

1. Optional: Geben Sie **[!UICONTROL Host Name]** mit dem Host-Namen Ihrer Commerce-Instanz ein (z. B. `www.example.com`), wenn dieser Wert sich von der URL unterscheidet.
1. Geben Sie die **[!UICONTROL Adobe Commerce Endpoint]** ein, d. h. die Basis-URL Ihrer Adobe Commerce-Instanz, die für den API-Zugriff verwendet wird.
1. Geben Sie die **[!UICONTROL API Key]** ein, die zum Authentifizieren von Anfragen an Commerce-APIs verwendet werden, oder fügen Sie sie ein.

   Klicken Sie auf **[!UICONTROL Copy]** neben dem Feld, wenn Sie den Schlüssel sicher an eine andere Stelle kopieren müssen.

1. Klicken Sie auf **[!UICONTROL Save]** , um die Konfiguration zu speichern.

Warten Sie nach dem Speichern, bis **erste Synchronisierung** oder Validierungsauftrag abgeschlossen ist, bevor Sie sich auf die Katalog- oder Auditergebnisse für diese Store-Ansicht verlassen.

Um eine Store-Ansichtskonfiguration zu entfernen, öffnen Sie diesen Eintrag und klicken Sie auf **[!UICONTROL Delete]**.

### Feldbeschreibungen {#commerce-connection-fields}

| Feld | Beschreibung |
| --- | --- |
| URL für Store-Ansicht | Die öffentliche URL der Store-Ansicht, die LLM Optimizer im Umfang für Katalog- und Audit-Workflows behandeln sollte. |
| Umgebungs-ID | Kennung der Commerce-Umgebung (aus Ihrer Cloud- oder Bereitstellungsdokumentation oder ggf. vom Administrator). |
| Website-Code | Commerce **[!UICONTROL Website Code]** für die Website, der der Katalog gehört. |
| Code speichern | Commerce **[!UICONTROL Store Code]** für den Store unter dieser Website. |
| Code der Speicheransicht | Commerce **[!UICONTROL Store View Code]** für die Store-Ansicht (z. B. `default`). |
| Host-Name | Hostname der Commerce-Storefront oder -Instanz, wenn im Formular zusätzlich zu anderen URLs dazu aufgefordert wird. |
| Adobe Commerce-Endpunkt | Instanz-URL, über die LLM Optimizer auf Commerce-APIs zugreift. |
| API-Schlüssel | Geheimer Schlüssel für die API-Authentifizierung. Er wird wie jede Produktionsberechtigung behandelt. |

## Bestätigen der Bereitschaft von Mandanten und Umgebungen {#confirm-tenant-readiness}

- Stellen Sie sicher **dass verbundene** Sandbox-)Projekte nicht mit **Produktions-/**-Daten gemischt werden, es sei denn, dies ist beabsichtigt.
- &quot;**-Rollen** in Experience Cloud und Commerce aufeinander abstimmen, sodass die Personen, die Bereitstellungsaktionen genehmigen, auf beiden Seiten über die richtigen Berechtigungen verfügen.

## Nächste Schritte {#next-steps}

[Verwenden von LLM Optimizer mit Adobe Commerce](use-llmo-with-commerce.md) um Opportunities zu überprüfen, Katalogaktualisierungen bereitzustellen und das Überschreibungsverhalten zu verstehen.
