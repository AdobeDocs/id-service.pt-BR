---
description: Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.
keywords: Serviço de ID
seo-description: Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados pelo servidor.
seo-title: Implementação do lado do servidor combinada com JavaScript
title: Implementação do lado do servidor combinada com JavaScript
uuid: 256 ea 0 e 7-1 eb 4-4 c 92-9 a 7 e-f 61 cb 1 ed 13 c 7
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Implementação do lado do servidor combinada com JavaScript {#server-side-implementation-mixed-with-javascript}

Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.

A API de serviço de ID fornece métodos, [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) e [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) para recuperar os valores de ID que podem ser passados para o servidor.

Certifique-se de marcar a ID de visitante da Experience Cloud e a ID de visitante do Analytics, além de enviar ambas as IDs (quando presentes) para verificar se os dados enviados estão associados ao perfil de visitante atual do Analytics.

>[!IMPORTANT]
>
>No momento, o appmeasurement para Java não oferece suporte ao serviço da Experience Cloud ID.

## API de inserção de dados {#section-955ce7664a4646d38b3005cb2df40baf}

Include the Analytics visitor ID (if set) in the `<visitorID>` element.

Include the Experience Cloud visitor ID in the `<marketingCloudVisitorID>` element.

Consulte [Tags XML suportadas](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags).

## AppMeasurement para Java {#section-d664b94934924d048300d9c2b6560085}

No momento, o serviço da Experience Cloud ID não é compatível com o appmeasurement para Java.
