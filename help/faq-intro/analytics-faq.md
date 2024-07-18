---
description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do Analytics com o serviço de identidade da Experience Cloud.
keywords: Serviço de identidade da Experience Cloud
title: Perguntas frequentes do Analytics e do serviço de identidade
exl-id: 98aeca0d-41a2-4b18-b307-19a6de816e38
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 99%

---

# Perguntas frequentes do Analytics e do serviço de identidade{#analytics-and-id-service-faqs}

Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do Analytics com o serviço de identidade.

## Servidores de rastreamento {#section-9a2ad7842e364c869e1650480d17f8ef}

**Como faço para encontrar minhas informações do servidor de rastreamento?**

Cada parte corretamente configurada do código AppMeasurement contém as informações do servidor de rastreamento.

No entanto, às vezes, os clientes podem dividir o arquivo do Analytics AppMeasurement em arquivos separados. Por exemplo, alguns clientes podem colocar variáveis de configuração em um arquivo, usar um segundo arquivo para plug-ins e colocar o código do AppMeasurement em um terceiro arquivo. Isso não é recomendado.

Se você não encontrar as informações do servidor de rastreamento, a instância do Analytics pode não estar configurada corretamente. Entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) se não conseguir encontrar as informações do servidor de rastreamento.

**O que acontece se eu usar um serviço de identidade e alterar o servidor de rastreamento?**

Não há mudanças para os usuários já identificados pelo serviço de identidade. Os visitantes herdados que não foram transferidos para o serviço de identidade e ainda estão identificados com um cookie do Analytics são removidos. A quantidade de usuários afetados depende do tempo de atividade do serviço de identidade. Por exemplo, uma implementação na qual o serviço de identidade esteve ativo por 1 semana pode ter mais usuários herdados do que uma na qual o serviço de identidade esteve ativo por 6 meses, pois os usuários que retornam ao site já teriam migrado.

## Implementação e configuração {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Preciso configurar um CNAME para rastrear visitantes entre domínios?**

Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).

Nos navegadores que aceitam cookies de terceiros, um cookie é definido no [domínio demdex.net](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=pt-BR) durante a solicitação para recuperar uma ID de visitante. Esse cookie permite que o serviço de identidade retorne a mesma ID de visitante da Experience Cloud em todos os domínios configurados usando a mesma ID da organização. Em navegadores que rejeitam cookies de terceiros, uma nova ID de visitante da Experience Cloud é atribuída para cada domínio.

Mesmo quando um CNAME é configurado, se o site de entrada principal não for visitado primeiro, os visitantes são identificados de forma diferente no site secundário e no site principal em navegadores que não aceitam cookies de terceiros.

**Por que o parâmetro da Experience Cloud ID (MID) não está na solicitação do Analytics?**

Se o serviço de identidade retorna as informações corretamente, mas você não visualiza o parâmetro `MID`, certifique-se de ter realizado a atualização para uma versão compatível do AppMeasurement.

**Meu site pode usar o código H e o AppMeasurement para JavaScript com o serviço de identidade?**

Sim. Desde que ambos os arquivos se refiram ao mesmo arquivo VisitorAPI.js, você pode usar uma combinação de código H e AppMeasurement para JavaScript no seu site.

No entanto, o código H não é compatível com a versão 1.6 ou superior do código visitorAPI.js. Se desejar atualizar para visitorAPI.js v 1.6 (ou superior), não será possível continuar usando o código H.

**O que é um período de carência e como configurá-lo?**

Consulte [Período de carência do serviço de identidade](../reference/analytics-reference/grace-period.md) e entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html).

**Por que é necessário migrar para a Coleta de dados em tempo real (RDC) a fim de mudar o serviço de identidade?**

A RDC adiciona benefícios de desempenho globais e é necessária para garantir que sua implementação esteja pronta para recursos futuros que usam a rede global de notas de borda da Adobe. Consulte [Requisitos do Analytics: Coleta de dados regionais (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Relatórios {#section-123cd55a32e54a45a23beb140becfa8f}

**Quais são algumas das causas possíveis das discrepâncias ao usar o Analytics com o serviço de identidade?**

Causas comuns de discrepâncias ao usar o serviço de identidade:

* Uso continuado do cookie s_vi herdado. Isso contribui para discrepâncias na coleta de dados.
* Contagem dupla de visitantes quando eles navegam de uma pesquisa para um pop-up.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**O que acontece no Analytics quando o serviço de identidade não consegue definir o cookie AMCV?**

Há três cenários possíveis em que isso afeta os dados do Analytics para novos visitantes:

1. Um usuário final deixa uma página antes que os cookies AMCV sejam definidos com êxito (dentro da janela de tempo limite de 30 segundos).

   Se um visitante deixar uma página antes de terminar o carregamento, a ocorrência do Analytics não será enviada. O Analytics não receberá dados desse cenário e considerará que os dados foram perdidos por um encerramento antecipado da página. A partir de nossos testes que incluíam geografia periférica, verificamos que esse cenário representava menos de 1% do tráfego em média. É importante observar que esse cenário ocorre mesmo sem a presença do serviço de identidade: é um artefato da inclusão do código de coleta de dados do Analytics no fim da página.

1. Um usuário final não recebe um serviço de identidade ou uma Analytics ID na janela de tempo limite de 30 segundos devido às conexões lentas ou à &quot;rotação&quot; do navegador.

   O serviço de identidade e a Analytics ID não são definidos e ao visitante é atribuída uma ID do lado do cliente. Embora isso permita que os dados do Analytics sejam capturados, o perfil do visitante será interrompido quando, em uma página subsequente, uma ID do Analytics for definida. A ID do lado do cliente também não corresponderá a nenhum perfil de visitante existente armazenado no Audience Manager ou no Analytics. Essa ID do lado do cliente também aparecerá como dois visitantes diferentes no Analytics se dois domínios separados estiverem sendo enviados para o mesmo conjunto de relatórios.

1. Um usuário final não recebe um serviço de identidade durante a janela de tempo limite de 30 segundos, mas recebe uma ID de rastreamento padrão do Analytics e o período de carência não é habilitado.

   O cenário três tem o mesmo resultado do cenário dois com a ID do lado do cliente sendo usada.

>[!TIP]
>
>O uso das atualizações mais recentes para VisitorAPI.js e AppMeasurement.js com as configurações padrão deve evitar qualquer impacto grave ou observável devido aos três cenários improváveis acima.

>[!MORELIKETHIS]
>
>* [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html)
