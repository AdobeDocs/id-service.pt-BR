---
description: Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.
keywords: Serviço de ID
seo-description: Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.
seo-title: Implementação do lado do servidor combinada com JavaScript
title: Implementação do lado do servidor combinada com JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Implementação do lado do servidor combinada com JavaScript {#server-side-implementation-mixed-with-javascript}

Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.

A API de serviço de ID fornece métodos, [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) e [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md) para recuperar os valores de ID que podem ser passados para o servidor.

Certifique-se de marcar a ID de visitante da Experience Cloud e a ID de visitante do Analytics, além de enviar ambas as IDs (quando presentes) para verificar se os dados enviados estão associados ao perfil de visitante atual do Analytics.

>[!IMPORTANT]
>
>No momento, o AppMeasurement para Java não é compatível com o serviço da Experience Cloud ID.

## API de inserção de dados {#section-955ce7664a4646d38b3005cb2df40baf}

Inclua a ID de visitante do Analytics (se configurada) no elemento `<visitorID>`.

Inclua a ID de visitante da Experience Cloud no elemento `<marketingCloudVisitorID>`.

Consulte [Tags XML compatíveis](https://marketing.adobe.com/developer/pt_BR/documentation/data-insertion/r-supported-tags).

## AppMeasurement para Java {#section-d664b94934924d048300d9c2b6560085}

No momento, o serviço da Experience Cloud ID não é compatível com o AppMeasurement para Java.
