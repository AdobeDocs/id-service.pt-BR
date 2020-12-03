---
title: Identificação dos visitantes únicos
description: Documentação para Adobe ECID (serviço de ID)
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 100%

---


# Identificação dos visitantes únicos

O método para identificar visitantes únicos entre vários contextos inclui uma sequência priorizada para garantir a precisão nessa determinação. A tabela a seguir mostra essa sequência priorizada:

| Pedido usado | Parâmetro do query (método de coleta) | Valor da coluna post_visid_type | Apresentar quando |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` está definida. |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  | 3  | O visitante tinha um cookie s_vi antes de implantar o serviço de ID de visitante ou você tem um [período de carência](https://docs.adobe.com/content/help/pt-BR/id-service/using/reference/analytics-reference/grace-period.html) de ID de visitante configurado.  |
|  3  | mid [cookie AMCV_ definido pelo Serviço de identidade](https://docs.adobe.com/content/help/pt-BR/id-service/using/home.html)  |  5  |  O navegador do visitante aceita cookies (primários) e o [!UICONTROL Serviço de identidade] é implantado.  |
|  4  | fid [cookie de fallback no H.25.3 ou mais recente ou AppMeasurement para JavaScript](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  |  4  |  O navegador do visitante aceita cookies (primários).  |
|  5  |  [Cabeçalho do assinante do HTTP Mobile](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  |  2  |  O dispositivo é reconhecido como um dispositivo móvel.  |
|  6  |  [Endereço IP, Agente do usuário, Endereço IP de gateway](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  |  1  |  O navegador do visitante não aceita cookies. |

Para obter informações sobre como os visitantes únicos são relatados, consulte [Visitantes únicos no Analytics](https://docs.adobe.com/content/help/pt-BR/analytics/components/metrics/unique-visitors.translate.html).
