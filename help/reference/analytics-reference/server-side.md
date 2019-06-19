---
description: Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.
keywords: Serviço de ID
seo-description: Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados pelo servidor.
seo-title: Implementação do lado do servidor combinada com JavaScript
title: Implementação do lado do servidor combinada com JavaScript
uuid: 256 ea 0 e 7-1 eb 4-4 c 92-9 a 7 e-f 61 cb 1 ed 13 c 7
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Implementação do lado do servidor combinada com JavaScript {#server-side-implementation-mixed-with-javascript}

Em algumas implementações as IDs de visitante são passadas do JavaScript para um servidor, de modo que outros eventos do Analytics (como uma compra) possam ser enviados ao servidor.

A API de serviço de ID fornece métodos, [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) e [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) para recuperar os valores de ID que podem ser passados para o servidor.

Certifique-se de marcar a ID de visitante da Experience Cloud e a ID de visitante do Analytics, além de enviar ambas as IDs (quando presentes) para verificar se os dados enviados estão associados ao perfil de visitante atual do Analytics.

>[!IMPORTANT]
>
>No momento, o appmeasurement para Java não suporta o Serviço de identidade da plataforma Experience Platform.

## API de inserção de dados {#section-955ce7664a4646d38b3005cb2df40baf}

Inclua a ID de visitante do Analytics (se definido) no `<visitorID>` elemento.

Inclua a ID de visitante da Experience Cloud no `<marketingCloudVisitorID>` elemento.

Consulte [Tags XML suportadas](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags).

## AppMeasurement para Java {#section-d664b94934924d048300d9c2b6560085}

No momento, o Serviço de identidade da plataforma Experience Platform não é compatível com o appmeasurement para Java.
