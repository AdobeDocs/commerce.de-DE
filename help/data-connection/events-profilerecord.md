---
title: Profileinträge
description: Erfahren Sie, welche Daten ein Profildatensatz erfasst.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# [!DNL Data Connection] Profildatensätze

Im Folgenden werden die Commerce-Profildatensatzdaten beschrieben, die bei der Installation der [!DNL Data Connection] verfügbar sind. Die Daten in Profildatensätzen werden an die Adobe Experience Platform gesendet.

## Profildatensatz

Aktualisierungen von Profildatensätzen sind in der Experience Platform verfügbar, wenn ein neues Profil erstellt, aktualisiert oder gelöscht wird.

### Aus einem Profildatensatz erfasste Daten

Im Folgenden werden die Daten beschrieben, die für einen Profildatensatz erfasst werden.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Werte mit Namespace](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/namespaces). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `person.birthDate` | Geburtsdatum des Käufers. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse `name@domain.com` beispielsweise in RFC2822 und nachfolgenden Standards allgemein definiert. |
| `billingAddress` | Die Postanschrift für die Rechnungsstellung. |
| `billingAddress.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `billingAddress.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `billingAddress.city` | Der Name der Stadt. |
| `billingAddress.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `billingAddress.country` | Der Name des von der Regierung verwalteten Gebiets. Anders als `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in einer beliebigen Sprache enthalten kann. |
| `billingAddress.primary` | Zeigt an, ob dies die primäre Rechnungsadresse ist. Wert ist immer `False`. |
| `billingAddressPhone` | Die der Rechnungsadresse zugeordnete Telefonnummer. |
| `billingAddressPhone.number` | Die Telefonnummer. Beachten Sie, dass die Telefonnummer eine Zeichenfolge ist und aussagekräftige Zeichen wie Klammern `()`, Bindestriche `-` oder Zeichen zur Angabe von Unterwahlkennungen wie Erweiterungen `x` z. B. `1-353(0)18391111` oder `+613 9403600x1234` enthalten kann. |
| `billingAddressPhone.primary` | Zeigt an, ob dies die primäre Telefonnummer für die Rechnungsadresse ist. Wert ist immer `False`. |
| `shippingAddress` | Die Versandadresse. |
| `shippingAddress.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `shippingAddress.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `shippingAddress.city` | Der Name der Stadt. |
| `shippingAddress.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `shippingAddress.country` | Der Name des von der Regierung verwalteten Gebiets. Anders als `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in einer beliebigen Sprache enthalten kann. |
| `shippingAddress.primary` | Zeigt an, ob dies die primäre Versandadresse ist. Wert ist immer `False`. |
| `shippingAddressPhone` | Die mit der Lieferadresse verknüpfte Telefonnummer. |
| `shippingAddressPhone.number` | Die Telefonnummer. Beachten Sie, dass die Telefonnummer eine Zeichenfolge ist und aussagekräftige Zeichen wie Klammern `()`, Bindestriche `-` oder Zeichen zur Angabe von Unterwahlkennungen wie Erweiterungen `x` z. B. `1-353(0)18391111` oder `+613 9403600x1234` enthalten kann. |
| `shippingAddressPhone.primary` | Gibt an, ob dies die primäre Telefonnummer für die Lieferadresse ist. Wert ist immer `False`. |
| `userAccount` | Gibt alle Treuedetails, Voreinstellungen, Anmeldeprozesse und andere Kontoeinstellungen an. |
| `userAccount.startDate` | Das Datum, an dem das Profil erstmals erstellt wurde. |

>[!NOTE]
>
>Jeder Profildatensatz enthält auch das Feld [`identityMap`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/identitymap) , das die vom System generierte Commerce-Kunden-ID als primäre Kennung für das Profil und eine E-Mail-ID enthält, die als sekundäre Kennung verwendet wird.

Erfahren Sie, wie [ein profildatensatzspezifisches Schema erstellen](profile-data.md) das die Daten aus Ihren Profildatensätzen aufnehmen kann.
