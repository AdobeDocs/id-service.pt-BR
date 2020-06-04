---
title: Identificação dos visitantes únicos
description: Documentação para Adobe ECID (serviço de ID)
translation-type: tm+mt
source-git-commit: d39cb79bac3a0a277e6390a8127c1f1b68579fa6
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 56%

---


# Identificação dos visitantes únicos

O método para identificar visitantes únicos entre vários contextos inclui uma sequência priorizada para garantir a precisão nessa determinação. A tabela a seguir mostra essa sequência priorizada:

| Ordem usada | Parâmetro de Query (método de coleta) | valor da coluna post_visid_type | Presente quando |
|---|---|---|---|
|  1  | vid [(s.visitorID)](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` está definida. |
|  2  | aid  [(s_vi cookie)](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  | 3  | Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://docs.adobe.com/content/help/pt-BR/id-service/using/reference/analytics-reference/grace-period.html) configured.  |
|  3  | mid[(cookie AMCV_ definido pelo Serviço de identidade)](https://docs.adobe.com/content/help/pt-BR/id-service/using/home.html)  |  5  |  O navegador do Visitante aceita cookies (primários) e o Serviço[!UICONTROL de]identidade é implantado.  |
|  4  | fid [(fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript)](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  |  4  |  O navegador do Visitante aceita cookies (primários).  |
|  5  |  [Cabeçalho do assinante do HTTP Mobile](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  |  2  |  O dispositivo é reconhecido como um dispositivo móvel.  |
|  6  |  [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html)  |  1  |  O navegador do Visitante não aceita cookies. |

Para obter informações sobre como os visitantes únicos são relatados, consulte [Visitantes únicos no Analytics](https://docs.adobe.com/content/help/pt-BR/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
