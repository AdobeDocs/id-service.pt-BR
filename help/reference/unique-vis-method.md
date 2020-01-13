---
title: Identificação dos visitantes únicos
description: Documentaçãoa para Adobe ECID (serviço de ID)
translation-type: ht
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# Identificação dos visitantes únicos

O método para identificar visitantes únicos entre vários contextos inclui uma sequência priorizada para garantir a precisão nessa determinação. A tabela a seguir mostra essa sequência priorizada:


 
| Ordem utilizada | Parâmetro de consulta (método de coleta) | valor de coluna post_visid_type | Presente quando |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://marketing.adobe.com/resources/help/pt_BR/sc/implement/visid_custom.html) | 0 |s.visitorID está definido.| 
| 2 | [ajuda (cookie s_vi)](https://marketing.adobe.com/resources/help/pt_BR/sc/implement/visid_analytics.html) | 3 |Visitante teve um cookie s_vi antes de você ter implantado o serviço de ID de visitante, ou você tem um [período de cortesia](https://marketing.adobe.com/resources/help/pt_BR/mcvid/mcvid_grace_period.html) de ID de visitante configurado. |
| 3 | [mid (AMCV_ cookie definido pelo serviço de identidade)](https://marketing.adobe.com/resources/help/pt_BR/mcvid/) | 5 | O navegador do visitante aceita cookies (originais) e o serviço de identidade é implantado. |
| 4 | [fid (cookie de fallback em H.25.3 ou posterior, ou AppMeasurement para JavaScript)](https://marketing.adobe.com/resources/help/pt_BR/sc/implement/visid_fallback.html) | 4 | O navegador do visitante aceita cookies (originais). |
| 5 | [Cabeçalho de assinante móvel do HTTP](https://marketing.adobe.com/resources/help/pt_BR/sc/implement/visid_mobile.html) | 2 | O dispositivo é reconhecido como um dispositivo móvel. |
| 6 | [Endereço IP, Agente do usuário, Endereço IP do gateway](https://marketing.adobe.com/resources/help/pt_BR/sc/implement/visid_fallback.html) | 1 | O navegador do visitante não aceita cookies. |


Para obter informações sobre como os visitantes únicos são relatados, consulte [Visitantes únicos no Analytics](https://docs.adobe.com/content/help/pt-BR/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
