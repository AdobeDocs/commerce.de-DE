---
title: Verwalten von eingeschränkten Zugriffsschlüsseln für freigegebene B2B-Kataloge
description: Erfahren Sie, wie Sie die eingeschränkten Zugriffsschlüssel verwalten, die der Adobe Commerce Optimizer-Connector verwendet, um Prognosen für den B2B-freigegebenen Katalog zu sichern.
role: Admin, Developer
feature: Integration, Configuration
badgePaas: label="Nur PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: a40ebd6b-b542-4432-a730-1803ef74518d
    internal-label: Data Transfer
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
    internal-label: Data integration
source-git-commit: a3ade1a31d3c2905b601f71bda118de89c43cf59
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%
---

# Verwalten von eingeschränkten Zugriffsschlüsseln für freigegebene B2B-Kataloge

[!BADGE Private Beta]{type=Caution tooltip="Erfordert die Adobe Commerce Optimizer Connector B2B-Erweiterung, die sich derzeit in der privaten Beta-Version befindet."}

Wenn Sie [!DNL Adobe Commerce] freigegebenen B2B-Kataloge mit dem [!DNL Adobe Commerce Optimizer Connector B2B extension] verwenden, generiert die Erweiterung automatisch den ersten Schlüssel mit eingeschränktem Zugriff und weist ihn zu, wenn eine Katalogansicht erstellt wird. Verwenden Sie die Seite &quot;[!UICONTROL Restricted Access Keys]&quot; in Commerce Admin, um diesen Schlüssel anzuzeigen und um zusätzliche Schlüssel zu erstellen, zuzuweisen oder zu löschen.

![Eingeschränkte Zugriffsschlüssel für freigegebene B2B-Katalogansichten](assets/restricted-access-keys.png){width="800" zoomable="yes"}

>[!NOTE]
>
>Informationen zum manuellen Verwalten von Schlüsseln für Nicht-B2B-Anwendungsfälle wie Partnerportale finden Sie unter [Schlüssel mit eingeschränktem Zugriff](/help/optimizer/setup/restricted-access-keys.md#create-a-restricted-access-key).

## Zugriff auf die Seite {#access-the-page}

Navigieren Sie vom Commerce-Administrator aus zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Restricted Access Keys]**.

Sie können der Katalogansicht über das Raster Freigegebener Katalog oder über das Raster Firma einen Schlüssel zuweisen. Siehe [Zuweisen von Schlüsseln zu einer freigegebenen B2B-Katalogansicht](#assign-keys-to-a-shared-catalog-view).

>[!NOTE]
>
>Eine Referenz der Felder auf dieser Seite finden Sie unter [Verwaltung von eingeschränkten Zugriffsschlüsseln](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/catalog-view-sync/restricted-access-keys){target="_blank"} im *Commerce Admin Guide*.—>

## Wenn Sie mehr als den automatischen Schlüssel benötigen {#when-you-need-more-than-the-automatic-key}

Der vom [!DNL Adobe Commerce Optimizer Connector B2B extension] generierte automatische Schlüssel deckt die meisten freigegebenen B2B-Kataloge ab, ohne dass Sie etwas unternehmen müssen. Verwalten Sie Schlüssel in diesen Fällen selbst:

- **Drehen eines Schlüssels** - Erstellen Sie einen neuen Schlüssel, weisen Sie ihn der Katalogansicht neben der vorhandenen zu, bestätigen Sie, dass er funktioniert, und löschen Sie dann den alten Schlüssel. Die automatische Drehung ist noch nicht verfügbar.
- **Schlüssel kann nicht verknüpft werden** - Wenn [Synchronisierungsstatus der Katalogansicht](catalog-view-sync-status.md) eine schlüsselbezogene Abweichung aufweist, versuchen Sie erneut, die Zuweisung der Katalogansicht zu speichern, um den fehlgeschlagenen Link erneut zu versuchen. Wenn der Schlüssel immer noch fehlschlägt, führen Sie [!UICONTROL Reconcile & Repair] aus, um den Schlüssel oder Status wiederherzustellen, bevor Sie einen Ersatz erstellen. Erstellen Sie einen Ersatzschlüssel nur, wenn der Schlüssel abgelaufen ist oder der Fehler dauerhaft nicht behebbar ist.
- **Öffentlichen Schlüssel suchen** - Wählen Sie auf der Seite Schlüssel für eingeschränkten Zugriff die Option **[!UICONTROL View Public Key]** aus, um den öffentlichen Schlüssel eines Schlüssels anzuzeigen und zu kopieren.

In einer Katalogansicht können bis zu drei Schlüssel gleichzeitig zugewiesen sein. Während der Schlüsselrotation akzeptiert [!DNL Adobe Commerce Optimizer] Token, die von einem zugewiesenen, nicht abgelaufenen Schlüssel signiert sind - es gibt keinen manuellen Schritt, um einen „aktiven“ Schlüssel festzulegen.

## Schlüssel erstellen

Erstellen Sie auf der Seite [!UICONTROL Restricted Access Keys] einen Schlüssel, indem Sie **[!UICONTROL Create Key]** auswählen.

Commerce generiert ein neues Schlüsselpaar und speichert den privaten Schlüssel. Die Tabelle Schlüssel für eingeschränkten Zugriff wird mit einem neuen Schlüsseleintrag aktualisiert, der die eindeutige Schlüssel-ID anzeigt. Verwenden Sie diese [!UICONTROL Key ID], wenn Sie den Schlüssel einer Katalogansicht zuweisen.

Der öffentliche Schlüssel wird erst dann bei [!DNL Adobe Commerce Optimizer] registriert, wenn Sie den Schlüssel einer Katalogansicht zuweisen. Nach der Registrierung wird der Tabelleneintrag Schlüssel mit eingeschränktem Zugriff aktualisiert und zeigt nun die Katalogzuweisung und das Ablaufdatum an.

## Zuweisen von Schlüsseln zu einer aus dem freigegebenen B2B-Katalog projizierten Katalogansicht {#assign-keys-to-a-shared-catalog-view}

Weisen Sie Schlüssel aus der Katalogansicht dem Unternehmenskonto oder der freigegebenen Katalogseite zu oder heben Sie die Zuweisung auf, nicht aus dem [!UICONTROL Restricted Access Keys].

Eine Katalogansicht muss mindestens einen Schlüssel haben und kann höchstens drei enthalten.

- Wenn Sie versuchen, einen vierten Schlüssel zuzuweisen, erhalten Sie eine Fehlermeldung, wenn Sie versuchen, den Wert zu speichern: `A Catalog View can have at most 3 access keys.`
- Wenn eine Katalogansicht nur einen Schlüssel hat, kann dieser Schlüssel nicht gelöscht oder die Zuweisung aufgehoben werden.

Um die Konfiguration des Schlüssels für die Katalogansicht zu aktualisieren, können Sie darauf über die Seite „Unternehmenskonto“ oder über die Seite „Freigegebener Katalog“ zugreifen.

>[!BEGINTABS]

>[!TAB Schlüssel von einem Unternehmenskonto aus verwalten]

1. Öffnen Sie von der Commerce-Admin aus die Unternehmensseite (**[!UICONTROL Customers]** > **[!UICONTROL Companies]**).

1. Wählen Sie in [!UICONTROL Action] Spalte für die Firma [!UICONTROL Edit] aus.

1. Um die Liste der Katalogansichten anzuzeigen, die aus dem freigegebenen Katalog projiziert wurden, der dem Unternehmen zugewiesen ist, erweitern Sie den Abschnitt _[!UICONTROL Catalog Views]_.

Auf der Registerkarte werden die Katalogansichten aufgelistet, die aus dem freigegebenen Katalog projiziert werden, einschließlich der ihnen zugewiesenen Schlüssel.

1. Wählen Sie in der Spalte [!UICONTROL Actions] für die zu aktualisierende Katalogansicht **[!UICONTROL Edit Restricted Access Keys]** aus.

   ![Dropdown-Liste „Schlüssel für eingeschränkten Zugriff bearbeiten“ mit Schlüsseln, die einer Katalogansicht zugewiesen sind](assets/restricted-access-key-selector.png){width="500" zoomable="yes"}

1. Um einen Schlüssel zuzuweisen, wählen Sie die Dropdown-Liste **[!UICONTROL Access Keys]** aus. Wählen Sie dann einen nicht zugewiesenen Schlüssel durch den [!UICONTROL key ID] aus, z. B. `#42`. Klicken Sie dann auf [!UICONTROL Done] , um es der Katalogansicht zuzuweisen.

   Schlüssel, die bereits einer anderen Katalogansicht zugewiesen sind, werden entsprechend gekennzeichnet.

1. Um ein Zugriffs-Token zu entfernen, entfernen Sie es aus dem Feld [!UICONTROL Access Tokens] , indem Sie das Steuerelement `x` in der Schlüsselbeschriftung auswählen.

1. Um die Konfigurationsaktualisierungen zu speichern und anzuwenden, wählen Sie **[!UICONTROL Save]** aus.

>[!TAB Verwalten von Schlüsseln aus einem freigegebenen Katalog]

1. Öffnen Sie von der Commerce-Admin aus die Seite Freigegebener Katalog (**[!UICONTROL Catalog]** > **[!UICONTROL Shared catalogs]**).

1. Wählen Sie in [!UICONTROL Action] Spalte für die freigegebene **[!UICONTROL General Settings]** aus dem Menü [!UICONTROL Select] .

1. Um die Liste der Katalogansichten anzuzeigen, die aus dem freigegebenen Katalog projiziert wurden, wählen Sie im Menü [!UICONTROL Shared Catalog Information] die Option **[!UICONTROL Catalog Views]** aus.

Auf der Seite [!UICONTROL Catalog Views] werden die Katalogansichts-ID, die zugehörige Shop-Ansicht und der Zugriffsschlüssel für jede Katalogansicht aufgelistet.

1. Wählen Sie in der Spalte [!UICONTROL Actions] für die zu aktualisierende Katalogansicht **[!UICONTROL Edit Restricted Access Keys]** aus.

   ![Dropdown-Liste „Schlüssel für eingeschränkten Zugriff bearbeiten“ mit Schlüsseln, die einer Katalogansicht zugewiesen sind](assets/restricted-access-key-selector.png){width="500" zoomable="yes"}

1. Um einen Schlüssel zuzuweisen, wählen Sie die Dropdown-Liste **[!UICONTROL Access Keys]** aus. Wählen Sie dann einen nicht zugewiesenen Schlüssel anhand des Standardschlüsseltitels aus, z. B. `#42`. Klicken Sie dann auf [!UICONTROL Done] , um es der Katalogansicht zuzuweisen.

   Schlüssel, die bereits einer anderen Katalogansicht zugewiesen sind, werden entsprechend gekennzeichnet.

1. Um ein Zugriffs-Token zu entfernen, entfernen Sie es aus dem Feld [!UICONTROL Access Tokens] , indem Sie das Steuerelement `x` in der Schlüsselbeschriftung auswählen.

1. Um die Konfigurationsaktualisierungen zu speichern und anzuwenden, wählen Sie **[!UICONTROL Save]** aus.

>[!ENDTABS]

## Verwalten des Ablaufs und der Verlängerung von Schlüsseln

Sie können die Standardschlüssellebensdauer für Schlüssel mit eingeschränktem Zugriff konfigurieren. Der Wert bestimmt das Ablaufdatum, das festgelegt wird, wenn die [!DNL Adobe Commerce Optimizer Connector B2B]-Erweiterung den ursprünglichen Schlüssel generiert oder wenn Sie einen neuen Schlüssel manuell erstellen.

Das Ablaufdatum wird in der Spalte [!UICONTROL Expires At] auf der Seite [!UICONTROL Restricted Access Keys] angezeigt.

Um die Dauer zu ändern, gehen Sie zu **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL ACO Restricted Access Keys]**. Aktualisieren Sie auf der Seite [!UICONTROL Provisioning] das Feld **[!UICONTROL Default Key Expiry (days)]** . Die Standardlebensdauer des Systemschlüssels wird zunächst für einen längeren Zeitraum (~100 Jahre) festgelegt. Stellen Sie sicher, dass Sie sie auf einen Wert aktualisieren, der Ihren Sicherheitsrichtlinien entspricht.

### Schlüsselverlängerung

Wenn sich ein Schlüssel innerhalb von 10 Tagen nach seinem Ablauf befindet, wird auf der Seite [!UICONTROL Restricted Access Keys] neben seinem Eintrag ein Warnsymbol angezeigt. Wenn Sie den Schlüssel nicht verlängern, bevor er abläuft, wird die Katalogansicht unzugänglich, bis Sie einen neuen Schlüssel zuweisen.

Sie können jederzeit einen neuen Schlüssel erstellen und zuweisen und den alten Schlüssel entfernen, nachdem Sie bestätigt haben, dass der neue Schlüssel funktioniert.

## Bekannte Einschränkungen

Die automatische Tastenrotation ist noch nicht verfügbar.

>[!MORELIKETHIS]
>
> - [Verwalten von eingeschränkten Zugriffsschlüsseln](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/catalog-view-sync/restricted-access-keys){target="_blank"} — Vollständiger Feldverweis für diese Seite im *Commerce Admin Guide* —>
> - [Synchronisierung der Katalogansicht überwachen](catalog-view-sync-status.md) — Überwachen der Katalogansichten, die durch diese Schlüssel geschützt werden
> - [Private Katalogansichten](/help/optimizer/setup/private-catalog-view.md) - Erfahren Sie, was eine von einem Connector verwaltete private Katalogansicht ist
> - [Eingeschränkte Zugriffsschlüssel](/help/optimizer/setup/restricted-access-keys.md) - Erfahren Sie, wie der manuelle, ACO Studio-basierte Schlüsselfluss für Nicht-B2B-Anwendungsfälle funktioniert
