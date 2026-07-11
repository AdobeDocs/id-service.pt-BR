---
description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do Serviço de ID de visitante.
keywords: Serviço de ID de visitante
title: Perguntas frequentes do Serviço de ID de visitante
exl-id: 4dd2220c-8a9d-4e27-838b-be5ad357cb3e
TQID: https://experienceleague.adobe.com/FxgL8UXSmoJM1oFr47yCAgYGcTa2PqKvSNM4bHjTw1M
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 824
ht-degree: 53%

---

# Perguntas frequentes do Serviço de ID de visitante{#id-service-faqs}

Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do Serviço de ID de visitante.

## Funcionalidade {#section-659e89f8b9a74cb8afff35587dc96836}

**Que tipo de funcionalidade ou capacidade o Serviço de ID de Visitante fornece?**

Consulte a [Visão geral](../introduction/overview.md).

**Por que o Serviço de ID do visitante não está fazendo uma chamada para recuperar a ECID?**

Isso pode ser difícil de diagnosticar. Uma coisa que você pode verificar são os cabeçalhos da política de segurança de conteúdo no seu site. Se você tiver uma política de segurança rigorosa, essas configurações poderão bloquear as chamadas de terceiros feitas pelo Serviço de ID de visitante. Consulte [Políticas de Segurança de Conteúdo e o Serviço de ID de Visitante](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**`VisitorAPI.js`armazenamento de arquivos**

Você pode ter problemas se hospedar o `VisitorAPI.js` como um arquivo local em aplicativos móveis. Recomendamos que você hospede o arquivo em um servidor da Web.

## Tempos de carregamento e latência da página {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Como a biblioteca `VisitorAPI.js` do Serviço de ID do Visitante afeta o tempo de carregamento da página?**

Coloque a biblioteca `VisitorAPI.js` na parte superior da página na seção `<head>` do código. Isso ajuda a garantir que a chamada de uma ID sai antes do corpo da página começar a carregar e maximiza a probabilidade da ID ser retornada com sucesso.

A chamada do Serviço de ID de Visitante é assíncrona e é a única chamada para o [domínio demdex.net](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=pt-BR). A chamada do Serviço de ID do visitante não impede o carregamento de outros elementos na página.

Para clientes do Target, ao colocar o código do Serviço de ID de visitante no `<body>` da página é possível aumentar a probabilidade de bloquear uma chamada do Target. É necessário inserir o código do Serviço de ID de visitante no corpo da página. Ele deve ser inserido após a tag aberta `<body>`.

**O Serviço de ID do Visitante faz uma chamada de servidor com cada carregamento de página?**

Não, essa chamada só ocorrerá na primeira vez que a página for renderizada e depois uma vez a cada 7 dias. Enquanto isso, as chamadas do servidor não são obrigatórias. O Serviço de ID de visitante opera no modo lado do cliente e não precisa fazer uma chamada de servidor para retornar uma ID.

Consulte [Visão geral](../introduction/overview.md).

**Ao usar o Serviço de ID de Visitante, o que pode causar tempos lentos de carregamento de página ou afetar a experiência do usuário?**

É difícil catalogar todas as condições possíveis. Bilhões de clientes consumidores conectam-se aos nossos serviços e à grande variedade de onde e como eles se conectam afetam o desempenho. Por exemplo:

* As velocidades variam muito nas redes móveis. Essas redes também sofrem de perda de sinal e dados ou de pacotes de voz.
* A conectividade é afetada por dispositivos que se conectam através do WiFi sob diversas condições. Por exemplo, a perda de pacotes e os problemas de velocidade são comuns em locais públicos como cafeterias ou em outros ambientes como aviões onde os pacotes devem rebater através de um satélite antes de chegar às redes terrestres.
* Redes locais mal configuradas podem afetar negativamente a conectividade e a velocidade.
* Os dispositivos cliente podem ter seus próprios problemas, como memória baixa, troca excessiva de disco ou energia limitada da CPU em relação às cargas de trabalho atuais.
* Os navegadores fazem a fila e executam chamadas de servidor remoto e até processam as respostas com regras diferentes, dependendo do criador e da versão do navegador. Esse comportamento afeta a velocidade e o desempenho.

**É possível nomear algumas melhorias feitas para reduzir o tempo de carregamento da página?**

Por exemplo, encadeamento. Introduzimos o encadeamento no caso de várias solicitações de sincronização de ID. Observamos em relatórios de laboratório que, para clientes que executam várias sincronizações de ID, a interface do usuário seria bloqueada devido a muitos cálculos contínuos da CPU. Como resultado, introduzimos o encadeamento para separar as solicitações de sincronização de ID por 100 ms cada.

Essa alteração melhora o desempenho para clientes que usam o Visitor 2.3.0+ e DIL 6.10+. As melhorias nos tempos de carregamento da página são mostradas na figura abaixo:

![](assets/id_sync_improvements_copy.png)

**As solicitações do navegador que usam CORS vs JSON-P afetam o desempenho da página?**

As solicitações de recursos com CORS geralmente são mais preferíveis do que com JSONP. Com o JSONP, alguns navegadores fazem fila e não priorizam solicitações em relação a outras chamadas síncronas e assíncronas na página. O CORS ajuda a garantir que essas solicitações sejam tratadas com prioridade mais alta na pilha de chamadas do navegador.

Consulte o [Suporte para CORS no Serviço de ID de Visitante](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Segurança {#section-b176b8492fbe4acfb79ebb30ec902f98}

**O Serviço de ID do Visitante oferece suporte ao CORS?**

Sim. Consulte o [Suporte para CORS no Serviço de ID de Visitante](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**O que é o CORS?**

*`Cross-Origin Resource Sharing`* ou CORS, é um método que os navegadores usam para solicitar recursos. O Serviço de ID de visitante sempre solicita recursos usando o CORS em navegadores compatíveis. O Serviço de ID de visitante solicita recursos com JSON-P em navegadores mais antigos que não são compatíveis com o CORS. Consulte o [Suporte para CORS no Serviço de ID de Visitante](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**O que acontece se meus requisitos de segurança são estritos demais e eu desejar não usar JSONP?**

Se você tiver requisitos de segurança estritos, defina a configuração da API do Serviço de ID de visitante como `useCORSOnly: true`. Você só deve ativar esse modo se estiver confiante de que os visitantes do site usam navegadores compatíveis com o CORS.

Consulte o [Suporte para CORS no Serviço de ID de Visitante](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) e [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html)

