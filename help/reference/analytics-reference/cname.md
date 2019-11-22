---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: Coletas de dados CNAMEs e Rastreamento entre domínios
title: Coletas de dados CNAME e rastreamento entre domínios
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 588c4b29ebd3cccea4f2ab032f69a4b6c6e97f2a

---


# Coleta e identidade de dados{#data-collection-and-identity}

No Analytics há três maneiras de usar a ID de visitantes.

- Usar o serviço de ID de [visitante](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- Usar a ID de visitante [herdada do Analytics](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- Fornecer sua própria identidade

## Uso do Serviço de ID do visitante{#using-the-visitor-id-service}

O serviço de ID de visitante é a maneira recomendada para identificar os visitantes. Ele é baseado em dois componentes

- ID primária - uma ID primária que pode ser usada para medir visitantes ao seu próprio site. Essa ID é armazenada na primeira ID de parte e é armazenada em um cookie do lado do cliente e em um cookie do lado do servidor (com um CNAME).
- ID de terceiros (opcional) - uma ID de terceiros separada armazenada em demdex.net que pode ser usada para medir visitantes em vários domínios (por exemplo, example.com e example.net)

O Analytics sempre usará a ID primária e, se a ID de terceiros estiver ativada e presente, a ID de terceiros em cada site será a mesma. No entanto, se a ID de terceiros estiver desativada, seja por suas configurações ou porque o navegador bloqueia cookies de terceiros, não há como vincular o tráfego nos dois sites.

## Domínios herdados do Analytics

Antes de o serviço de ID de visitante ser iniciado, alguns anos atrás, muitos clientes usavam os domínios nativos de análise para definir os cookies de ID. Isso inclui `omtrdc.net`, `2o7.net` ou um domínio CNAME. `omtrdc.net`, `2o7.net` e em alguns casos um domínio CNAME é usado para armazenar cookies de terceiros. Os cookies definidos dessa forma sempre foram restritos a um único cliente para que os clientes não pudessem combinar seus dados entre empresas. Domínios CNAMED de terceiros, às vezes chamados de domínios amigáveis de terceiros, são usados somente quando os clientes desejam rastrear usuários em sites de sua propriedade (por exemplo, example.com, example.co.jp). Este método está sendo descontinuado para permitir um serviço de ID de visitante mais robusto e com reconhecimento de privacidade. Os clientes devem mudar para o serviço de ID de visitante com um CNAME por domínio assim que possível.

## Forneça sua própria identidade

Se um cliente escolher, poderá ignorar completamente o sistema de identificação da Adobe e implementar uma sua própria ID de visitante [personalizada](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md). Há algumas coisas para se ter em mente se escolhermos esta rota.

- Você precisará implementar a opção de não participação e os controles de privacidade apropriados
- Essa ID se aplica somente ao Analytics
- Você é responsável por persistir nessa ID

## CNAMES de coleta de dados

A Adobe ainda recomenda o uso de um CNAME em conjunto com o serviço de ID de visitante. Isso permite que a ID de visitante primária persista usando cookies HTTP, o que torna os cookies mais duráveis.

## Opções

A Adobe oferece as APIs para compartilhar sinais de recusa com nossos sistemas, de modo que você possa oferecer maneiras de os usuários optarem por não fazer o rastreamento. Fornecemos instruções detalhadas sobre a [recusa](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) e a [aceitação](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md)

## Habilitar o suporte para CNAME com o serviço de identidade da Experience Cloud {#section-25d4feb686d944e3a877d7aad8dbdf9a}

O suporte ao CNAME do servidor de coleta de dados é [ativado ao configurar um CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) e ao configurar a `visitor.marketingCloudServerSecure` variável no Serviço de identidade da Experience Cloud e ao configurar `s.trackingServerSecure` no AppMeasurement.
