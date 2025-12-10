---
title: So  [!DNL Commerce]  Services Datenschutzanfragen
description: Erfahren Sie [!DNL Commerce]  wie -Services Anfragen zum Zugriff auf und Löschen von Daten verarbeitet.
role: Admin, Leader
feature: Security, Compliance
exl-id: 1408ca77-6956-4519-93a6-bc9be9bffeff
source-git-commit: c6725fc524e9d239ccc0f16701e92ad5d2fc7729
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Datenschutzanfragen

Adobe Experience Platform Privacy Service bietet eine RESTful-API und eine Benutzeroberfläche, die Sie bei der Verwaltung von Kundendatenanfragen unterstützen. Mit Privacy Service können Sie Anfragen für den Zugriff auf und die Löschung von personenbezogenen oder vertraulichen Kundendaten aus Adobe Experience Cloud-Programmen stellen, was die automatische Einhaltung gesetzlicher und unternehmensinterner Datenschutzbestimmungen erleichtert.

Weitere Informationen zu Privacy Service und zum Erstellen und Verwalten von Datenschutzanfragen finden Sie in der Dokumentation zu Adobe Experience Platform:

* [Übersicht über Privacy Service](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/home)
* [Verwalten von Datenschutzaufträgen in der Privacy Service-Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/ui/user-guide)

## Verwalten individueller Datenschutzanfragen

Sie können einzelne Anfragen zum Zugreifen auf und Löschen von Verbraucherdaten aus [!DNL Commerce] auf zwei Arten senden:

* Über die **Privacy Service-Benutzeroberfläche**. Siehe die Dokumentation [hier](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/ui/user-guide#_blank).
* Über die **Privacy Service-API**. Siehe die Dokumentation [hier](https://developer.adobe.com/experience-platform-apis/references/privacy-service/#_blank) und API-Informationen [hier](https://developer.adobe.com/experience-platform-apis/#_blank).

Privacy Service unterstützt zwei Arten von Anfragen: **Datenzugriff** und **Datenlöschung**.

>[!NOTE]
>
>Dieser Artikel konzentriert sich auf Datenschutzanfragen für [!DNL Commerce]. Wenn Sie Datenschutzanfragen für [Platform Data Lake](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/privacy), [Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/privacy) oder [Identity Service) &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/privacy), lesen Sie die entsprechenden Benutzerhandbücher. Beachten Sie, dass Lösch- und Zugriffsanfragen an jedes System einzeln gestellt werden müssen, da eine Datenschutzanfrage an Commerce keine Daten aus allen diesen Systemen entfernt.

## Datenzugriff

Geben **für &quot;**&quot; &quot;Commerce (Personalization)“ über die Benutzeroberfläche an (oder `commerceMarketingData` als Produkt-Code in der API).

## Löschen von Daten

Bei Löschanfragen löscht Privacy Service [!DNL Commerce] in Commerce SaaS-Services gespeicherten Daten zu Marketing-Zwecken. Das bedeutet, dass Profile und Bestellungen von betroffenen Personen nicht mehr zur Verwendung in Kampagnen und Kunden-Journey an Adobe-Marketing-Anwendungen gesendet werden. Privacy Service löscht jedoch keine Daten in der [!DNL Commerce]-Anwendung, da diese für Transaktionsanforderungen von Händlern erforderlich sein können. Händler sind für alle Datenlöschungs-/-zugriffsanfragen im [!DNL Commerce] verantwortlich. Weitere Informationen finden [&#x200B; unter „Gemeinsame Verantwortung](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility)Sicherheits- und Betriebsmodell“

[!DNL Commerce] werden Händler über Löschanfragen informieren, indem sie ihnen Informationen über betroffene Personen senden, die das Löschen bestimmter Daten verlangen.

## Erstellen von Zugriffs- und Löschanfragen

### Voraussetzungen

Um Anfragen zum Zugreifen auf und Löschen von Daten für Adobe [!DNL Commerce] zu stellen, benötigen Sie Folgendes:

* eine IMS-Organisations-ID
* eine Identitätskennung der Person, für die Sie eine Aktion durchführen möchten, und die entsprechenden Namespaces. Weitere Informationen zu Identity-Namespaces in Adobe [!DNL Commerce] und Experience Platform finden Sie unter [Übersicht zu Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces).

### Beispiel für DSGVO-Anfrage/Löschzugriff:

Geben Sie **Zugriffsanfragen** &quot;Commerce (Personalization)“ über die Benutzeroberfläche an (oder „commerceMarketingData“ als Produkt-Code in der API).

Stellen Sie **„Löschanfragen** sicher, dass das Kontrollkästchen &quot;Commerce (Personalization)“ aktiviert ist. Wenn Kundenprofil- und Bestelldaten bereits von [!DNL Commerce] an Adobe Experience Platform gesendet wurden, müssen Sie außerdem Löschanfragen an die folgenden nachgelagerten Services senden.

* Profil (Produktcode: „profileService„)
* AEP Data Lake (Produktcode: „AdobeCloudPlatform„)
* Identität (Produktcode: „Identität„)

Um Zugriffs- und Löschanfragen über die Datenschutz-API zu senden, müssen Sie sich authentifizieren und die Berechtigungen für Privacy Service verwalten:

* [Authentifizierung und Zugriff auf die Privacy Service-API](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/api/getting-started)
* [Berechtigungen für Privacy Service verwalten](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/permissions)

**Erforderliche Kopfzeilen**

```bash
curl --location --request POST 'https://platform.adobe.io/data/core/privacy/jobs' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {{CLIENT_ID}}' \
--header 'x-gw-ims-org-id: {{IMS_ORGID}}' \
--header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
```

**Anfrage**

```json
{
    "companyContexts": [
      {
        "namespace": "imsOrgID",
        "value": "{{IMS_ORGID}}"
      }
    ],
    "users": [
      {
        "key": "sampleUserKey1",
        "action": ["access"],
        "userIDs": [
          {
            "namespace": "email",
            "value": "dsmith@sample.com",
            "type": "standard"
          }
        ]
      },
      {
        "key": "sampleUserKey2",
        "action": ["access","delete"],
        "userIDs": [
          {
            "namespace": "email",
            "value": "ajones@sample.com",
            "type": "standard"
          }
        ]
      }
    ],
    "include": ["commerceMarketingData"],
    "expandIds": false,
    "priority": "normal",
    "regulation": "gdpr"
}
```

**Antwort**

```json
{
    "requestId": "17284033173196154RX-223",
    "totalRecords": 3,
    "jobs": [
        {
            "jobId": "a52ca032-858e-11ef-bbb4-27391388a0a6",
            "customer": {
                "user": {
                    "key": "sampleUserKey1",
                    "action": [
                        "access"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "dsmith@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        },
        {
            "jobId": "a52ca034-858e-11ef-bbb4-d5d952d69769",
            "customer": {
                "user": {
                    "key": "sampleUserKey2",
                    "action": [
                        "delete"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "ajones@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        },
        {
            "jobId": "a52ca033-858e-11ef-bbb4-8361a5022341",
            "customer": {
                "user": {
                    "key": "sampleUserKey2",
                    "action": [
                        "access"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "ajones@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        }
    ]
}
```
