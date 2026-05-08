---
title: Sicherheitsarchitektur und Datenfluss
description: Erfahren Sie mehr über die Sicherheitsarchitektur und den Datenfluss für Adobe Commerce as a Cloud Service.
role: Admin, Developer, Leader
badgeSaas: label="Nur SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: feb48068137c6a63e6594167fe969c3aa4b044c4
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# Sicherheitsarchitektur und Datenfluss

Das folgende Beispiel veranschaulicht, wie Daten normalerweise in [!DNL Adobe Commerce as a Cloud Service] fließen:

![Datenflussdiagramm für Adobe Commerce as a Cloud Service](../assets/data-flow-1.png)

## Erzählung zum Datenfluss

**Schritt 1**: Die Einkäufer geben die URL der Storefront des Händlers in ihren Browser ein. Dadurch wird die URL an das Content Delivery Network (externes CDN) der Storefront des Commerce gesendet.

**Schritt 2**: Wenn die Site-URL zwischengespeichert wird, gibt das Storefront-CDN sie an den Käufer zurück. Wenn er nicht bereits zwischengespeichert ist, was passieren könnte, wenn dies die erste Anfrage für eine Ressource ist, leitet das externe CDN die Anfrage des Käufers an das interne CDN weiter und speichert die Antwort für nachfolgende Anfragen zwischen.

**Schritt 2a**: Wenn die Anfrage Bilder oder Videos betrifft, wird sie zur Erfüllung an [!DNL Product Visuals] gesendet und an die Storefront zurückgegeben.

**Schritt 3**: Wenn die Site-URL im internen CDN zwischengespeichert wird, wird sie von diesem Cache zurückgegeben. Ist dies nicht der Fall, wird er an [!DNL API Mesh] gesendet und die Antwort wird für nachfolgende Anfragen zwischengespeichert.

**Schritt 4**: [!DNL API Mesh] fungiert als Orchestrierungsschicht und bestimmt, ob die Anfrage an [!DNL Adobe Commerce as a Cloud Service] oder ein Drittanbietersystem gesendet werden soll, um die Anfrage zu erfüllen.

>[!NOTE]
>
>[!DNL API Mesh] werden Anfragen nur dann an Drittanbietersysteme senden, wenn Sie Ihre Netzkonfiguration entsprechend angepasst haben.

**Schritt 5**: Anfragen, die an gesendet werden, passieren [!DNL Adobe Commerce as a Cloud Service] eine Web Application Firewall (WAF), die verdächtige oder bösartige Anfragen blockiert. Wenn die angeforderte URL im [!DNL Commerce] CDN zwischengespeichert wird, wird sie von diesem Cache bereitgestellt. Wenn er nicht zwischengespeichert wird, wird er von einem oder mehreren [!DNL Adobe Commerce as a Cloud Service]-Microservices (z. B. Foundation, Suche und Recommendations) zurückgegeben und dann für zukünftige Anfragen zwischengespeichert.

**Schritt 5a**: Wenn die Anfrage an ein Drittanbietersystem gesendet wird, wird die Antwort an [!DNL API Mesh] zurückgegeben.

**Schritt 5b**: Wenn die Anfrage zur Zahlungsabwicklung dient, rendert der Zahlungsdienstleister einen iframe in die Storefront, damit der Käufer die Kreditkarteninformationen sicher eingeben und den Zahlungsvorgang abschließen kann.

**Schritt 6**: Sobald Antworten von [!DNL Adobe Commerce as a Cloud Service]- oder Drittanbieterdiensten von [!DNL API Mesh] empfangen werden, werden sie zu einem einheitlichen Diagramm zusammengefügt und an [!DNL Commerce Storefront] zurückgegeben, um die Anfrage des Käufers zu bearbeiten.
