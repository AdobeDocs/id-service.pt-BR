---
description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do serviço de ID.
keywords: ID Service
seo-description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do serviço de ID.
seo-title: Perguntas frequentes do serviço de ID
title: Perguntas frequentes do serviço de ID
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Perguntas frequentes do serviço de ID{#id-service-faqs}

Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do serviço de ID.

## Recurso {#section-659e89f8b9a74cb8afff35587dc96836}

**Qual tipo de funcionalidade ou capacidade o serviço de ID fornece?**

Consulte a [Visão geral](../introduction/overview.md).

**Por que o serviço de ID não está fazendo uma chamada para recuperar a Experience Cloud ID?**

Isso pode ser difícil de diagnosticar. Uma coisa que você pode verificar são os cabeçalhos da política de segurança de conteúdo no seu site. Se você tiver uma política de segurança rigorosa, essas configurações poderão bloquear as chamadas de terceiros feitas pelo serviço de ID. See [Content Security Policies and the Experience Cloud Identity Service](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**armazenamento de arquivo VisitorAPI.js**

Você pode ter problemas se hospedar o arquivo VisitorAPI.js como um arquivo local em aplicativos para dispositivos móveis. Recomendamos que você hospede o arquivo em um servidor da Web.

## Tempos de carregamento e latência da página {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Como a biblioteca VisitorAPI.js do serviço de ID afeta o tempo de carregamento da página?**

Coloque a biblioteca VisitorAPI.js no início da página na `<head>` seção do código. Isso ajuda a garantir que a chamada de uma ID sai antes do corpo da página começar a carregar e maximiza a probabilidade da ID ser retornada com sucesso.

The ID service call is asynchronous and is the only call to the [demdex.net domain](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/reference/demdex-calls.html). A chamada do serviço de ID não impede o carregamento de outros elementos na página.

Para [!DNL Target] clientes do, ao inserir o código do serviço de ID no `<body>` da página é possível aumentar a probabilidade de bloquear uma chamada do [!DNL Target]. É necessário inserir o código do serviço de ID no corpo na página. Ele deve ser inserido após a tag aberta `<body>`.

**O serviço de ID efetua uma chamada de servidor com cada carregamento de página?**

Não, essa chamada só ocorrerá na primeira vez que a página for renderizada e uma vez a cada 7 dias depois. Enquanto isso, as chamadas do servidor não são obrigatórias. O serviço de ID opera no modo do cliente e não precisa fazer uma chamada de servidor para retornar uma ID.

Consulte [Visão geral](../introduction/overview.md).

**Ao usar o serviço de ID, o que pode causar tempos lentos de carregamento de página ou afetar a experiência do usuário?**

É difícil catalogar todas as condições possíveis. Milhares de milhões de clientes consumidores conectam-se aos nossos serviços e à tremenda variedade de onde e como eles se conectam afetam o desempenho. Por exemplo:

* As velocidades variam muito nas redes móveis. Essas redes também sofrem de perda de sinal e dados ou de pacotes de voz.
* A conectividade é afetada por dispositivos que se conectam através do WiFi sob diversas condições. Por exemplo, a perda de pacotes e os problemas de velocidade são comuns em locais públicos como cafeterias ou em outros ambientes como aviões onde os pacotes devem rebater através de um satélite antes de chegar às redes terrestres.
* Redes locais mal configuradas podem afetar negativamente a conectividade e a velocidade.
* Os dispositivos cliente podem ter seus próprios problemas, como memória baixa, troca excessiva de disco ou energia limitada da CPU em relação às cargas de trabalho atuais.
* Os navegadores fazem a fila e executam chamadas de servidor remoto e até processam as respostas com regras diferentes, dependendo do criador e da versão do navegador. Esse comportamento afeta a velocidade e o desempenho.

**É possível nomear algumas melhorias realizadas para reduzir o tempo de carregamento da página?**

Por exemplo, thread yielding. Introduzimos o encadeamento no caso de várias solicitações de sincronização de ID. Observamos em relatórios de laboratório que, para clientes que executam várias sincronizações de ID, a interface do usuário seria bloqueada devido a muitos cálculos contínuos da CPU. Como resultado, introduzimos o encadeamento de encadeamento para separar as solicitações de sincronização de ID por 100 ms cada.

Essa alteração melhora o desempenho para clientes que usam o Visitante 2.3.0+ e DIL 6.10+. As melhorias nos tempos de carregamento da página são mostradas na figura abaixo:

![](assets/id_sync_improvements_copy.png)

**As solicitações do navegador que usam CORS vs JSON-P afetam o desempenho da página?**

As solicitações de recursos com CORS geralmente são mais preferíveis do que com JSONP. Com o JSONP, alguns navegadores fazem fila e despriorizam solicitações em relação a outras chamadas síncronas e assíncronas na página. O CORS ajuda a garantir que essas solicitações sejam tratadas com prioridade mais alta na pilha de chamadas do navegador.

Consulte [Suporte ao CORS no serviço de identidade da Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Segurança {#section-b176b8492fbe4acfb79ebb30ec902f98}

**O serviço de ID suporta CORS?**

Sim. Consulte [Suporte ao CORS no serviço de identidade da Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**O que é o CORS?**

*`Cross-Origin Resource Sharing`* ou CORS, é um método que os navegadores usam para solicitar recursos. O serviço de ID sempre solicita recursos usando o CORS em navegadores compatíveis. O serviço de ID solicita recursos com JSON-P em navegadores mais antigos que não suportam CORS. Consulte [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**O que acontece se meus requisitos de segurança são estritos demais e eu desejar não usar JSONP?**

Se você tiver requisitos de segurança estritos, defina a configuração da API do serviço de ID como `useCORSOnly: true`. Você só deve ativar esse modo se estiver confiante de que os visitantes do site usam navegadores compatíveis com CORS.

See [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) and [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html)

