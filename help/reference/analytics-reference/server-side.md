---
description: Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.
keywords: Serviço de ID
title: Implementação do lado do servidor combinada com JavaScript
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Implementação do lado do servidor combinada com JavaScript {#server-side-implementation-mixed-with-javascript}

Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.

A API do serviço de ID fornece os métodos [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) e [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) para recuperar os valores de ID que podem ser passados para o servidor.

Certifique-se de marcar a ID de visitante da Experience Cloud e a ID de visitante do Analytics, além de enviar ambas as IDs (quando presentes) para verificar se os dados enviados estão associados ao perfil de visitante atual do Analytics.

>[!IMPORTANT]
>
>No momento, o AppMeasurement para Java não é compatível com o serviço de identidade da Experience Cloud.

## API de inserção de dados {#section-955ce7664a4646d38b3005cb2df40baf}

Inclua a ID de visitante do Analytics (se configurada) no elemento `<visitorID>`.

Inclua a ID de visitante da Experience Cloud no elemento `<marketingCloudVisitorID>`.

Consulte [Tags XML suportadas](https://developer.adobe.com/).

## AppMeasurement para Java {#section-d664b94934924d048300d9c2b6560085}

No momento, o serviço de identidade da Experience Cloud não é compatível com o AppMeasurement para Java.
