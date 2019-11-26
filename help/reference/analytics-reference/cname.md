---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: Coletas de dados CNAMEs e Rastreamento entre domínios
title: Coletas de dados CNAME e rastreamento entre domínios
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 989b5f537848a7506a96e2eac17409f8b0307217

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

O Analytics usará a ID de terceiros, a menos que as IDs de terceiros estejam ativadas e os navegadores permitam o uso. A ID de terceiros é nomeada por cliente para que um cliente não possa combinar dados com outro cliente no Analytics.

## Domínios herdados do Analytics

Antes do lançamento do serviço de ID de visitante da Adobe, muitos clientes usavam os domínios nativos de análise para definir os cookies de ID. Isso inclui `omtrdc.net`, `2o7.net` ou um domínio CNAME. `omtrdc.net`, `2o7.net`, em alguns casos, um domínio CNAME foi usado para armazenar cookies de terceiros. Os cookies definidos dessa forma eram restritos a um único cliente para que os clientes não pudessem combinar seus dados com dados de outros clientes. Domínios CNAMED de terceiros, às vezes chamados de domínios amigáveis de terceiros, eram usados quando os clientes queriam rastrear usuários em sites que eles possuíam (por exemplo, example.com, example.co.jp). Este método ou o uso de CNAME para suportar domínios amigáveis de terceiros está obsoleto para permitir o serviço de ID de visitante mais robusto e com reconhecimento de privacidade. Os clientes devem mudar para o serviço de ID de visitante com um CNAME por domínio assim que possível.

## Forneça sua própria identidade

Se um cliente escolher, poderá ignorar completamente o sistema de identificação da Adobe e implementar uma sua própria ID de visitante [personalizada](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md). Há algumas coisas para se ter em mente se escolhermos esta rota.

- Você precisará implementar a opção de não participação e os controles de privacidade apropriados
- Essa ID se aplica somente ao Analytics
- Você é responsável por persistir nessa ID

## CNAMES de coleta de dados

A Adobe ainda recomenda o uso de um CNAME em conjunto com o serviço de ID de visitante. Isso permite que a ID de visitante primária persista usando cookies HTTP, o que torna os cookies mais duráveis.

## OPTOUT

A Adobe fornece aos clientes as APIs para compartilhar sinais de recusa com nossos sistemas, de modo que os clientes, por sua vez, possam permitir que os usuários optem pelo rastreamento. Fornecemos instruções detalhadas sobre como o cliente pode implementar os controles adequados para suportar a escolha do usuário; a API [de](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) opção de não participação ou as opções para [impedir que o cookie seja acionado](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md) até que o consentimento seja obtido

## Habilitar o suporte para CNAME com o serviço de identidade da Experience Cloud {#section-25d4feb686d944e3a877d7aad8dbdf9a}

O suporte ao CNAME do servidor de coleta de dados é [ativado ao configurar um CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) e ao configurar a `visitor.marketingCloudServerSecure` variável no Serviço de identidade da Experience Cloud e ao configurar `s.trackingServerSecure` no AppMeasurement.
