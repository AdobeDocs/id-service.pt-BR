---
title: Identificação dos visitantes únicos
description: Documentação para Adobe ECID (serviço de ID)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
source-git-commit: c65816530ae2269b216f60b9b0450077e5aaac2f
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 100%

---

# Identificação dos visitantes únicos

O método para identificar visitantes únicos entre vários contextos inclui uma sequência priorizada para garantir a precisão nessa determinação. A tabela a seguir mostra essa sequência priorizada:

| Pedido usado | Parâmetro do query (método de coleta) | Valor da coluna post_visid_type | Apresentar quando |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=pt-BR)  | 0  | `s.visitorID` está definida. |
|  2  | aid  [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=pt-BR#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | O visitante tinha um cookie s_vi antes de implantar o serviço de ID de visitante ou você tem um [período de carência](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=pt-BR) de ID de visitante configurado.  |
|  3  | mid [cookie AMCV_ definido pelo Serviço de identidade](../introduction/cookies.md)  |  5  |  O navegador do visitante aceita cookies (primários), e o [!DNL Identity Service] é implantado.  |
|  4  | fid [cookie de fallback no H.25.3 ou mais recente ou AppMeasurement para JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=pt-BR#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  O navegador do visitante aceita cookies (primários).  |
|  5  |  [Cabeçalho do assinante do HTTP Mobile](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=pt-BR)  |  2  |  O dispositivo é reconhecido como um dispositivo móvel.  |
|  6  |  [Endereço IP, Agente do usuário, Endereço IP de gateway](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=pt-BR)  |  1  |  O navegador do visitante não aceita cookies. |

{style="table-layout:auto"}

Para obter informações sobre como os visitantes únicos são relatados, consulte [Visitantes únicos no Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=pt-BR).
