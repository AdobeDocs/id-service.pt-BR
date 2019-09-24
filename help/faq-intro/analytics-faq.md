---
description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do Analytics com o serviço de identidade da Experience Cloud.
keywords: Serviço de identidade da Experience Cloud
seo-description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do Analytics com o serviço de identidade.
seo-title: Perguntas frequentes do Analytics e do serviço de identidade
title: Perguntas frequentes do Analytics e do serviço de identidade
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Perguntas frequentes do Analytics e do serviço de identidade{#analytics-and-id-service-faqs}

Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso do Analytics com o serviço de identidade.

## Servidores de rastreamento {#section-9a2ad7842e364c869e1650480d17f8ef}

**Como encontro as informações do meu servidor de rastreamento?**

Cada parte devidamente configurada do código do AppMeasurement contém as informações do servidor de rastreamento.

Entretanto, às vezes, os clientes podem separar os arquivos do AppMeasurement do Analytics. Por exemplo, alguns clientes podem colocar variáveis de configuração em um arquivo, usar um segundo arquivo para plugins e colocar o código do AppMeasurement em um terceiro arquivo. Isso não é recomendado.

Se você não conseguir encontrar as informações do servidor de rastreamento, sua instância do Analytics pode não estar configurada adequadamente. Entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html) se não for possível encontrar as informações do servidor de rastreamento.

**O que acontece se eu usar um serviço de identidade e alterar o servidor de rastreamento?**

Não há mudanças para os usuários já identificados pelo serviço de identidade. Os visitantes herdados que não foram transferidos para o serviço de identidade e ainda estão identificados com um cookie do Analytics são removidos. A quantidade de usuários afetados depende do tempo de atividade do serviço de identidade. Por exemplo, uma implementação na qual o serviço de identidade esteve ativo por 1 semana pode ter mais usuários herdados do que uma na qual o serviço de identidade esteve ativo por 6 meses, pois os usuários que retornam ao site já teriam migrado.

## Implementação e configuração {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Devo configurar um CNAME para rastrear os visitantes nos domínios?**

Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).

Nos navegadores que aceitam cookies de terceiros, um é definido pelo [domínio demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) durante a solicitação para recuperar uma ID de visitante. Esse cookie permite que o serviço de identidade retorne a mesma ID de visitante da Experience Cloud em todos os domínios configurados usando a mesma ID da organização. Nos navegadores que rejeitam cookies de terceiros, uma nova ID de visitante da Experience Cloud será atribuída para cada domínio.

Se o site principal não for visitado primeiro, os visitantes serão identificados de diferentes maneiras no site secundário e no site principal nos navegadores que não aceitam cookies de terceiros mesmo quando um CNAME estiver configurado.

**Por que o parâmetro Experience Cloud ID (MID) não está na solicitação do Analytics?**

Se o serviço de identidade retorna as informações corretamente, mas você não visualiza o parâmetro `MID`, certifique-se de ter realizado a atualização para uma versão compatível do AppMeasurement.

**Meu site pode usar o código H e o AppMeasurement para JavaScript com o serviço de identidade?**

Sim. Desde que ambos os arquivos estejam relacionados ao mesmo arquivo VisitorAPI.js, você pode usar uma combinação de código H e AppMeasurement para JavaScript no seu site.

No entanto, o código H não é suportado pelo código da versão 1.6 ou posterior de visitorAPI.js. Se você deseja atualizar para a versão 1.6 (ou posterior) de visitorAPI.js, não é possível continuar a usar o código H.

**O que é um período de carência e como faço para configurá-lo?**

Consulte [O Período](../reference/analytics-reference/grace-period.md) de carência do serviço de identidade e entre em contato com o [Atendimento](https://helpx.adobe.com/marketing-cloud/contact-support.html)ao cliente.

**Por que é necessário migrar para a Coleta de dados em tempo real (RDC) a fim de mudar o serviço de identidade?**

A RDC adiciona benefícios de desempenho globais e é necessária para assegurar que sua implementação esteja pronta para recursos futuros que aproveitam a rede global de notas de borda da Adobe. Consulte [Requisitos do Analytics: coleta de dados regionais (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Relatório {#section-123cd55a32e54a45a23beb140becfa8f}

**Quais são algumas das causas possíveis das discrepâncias ao usar o Analytics com o serviço de identidade?**

Causas comuns de discrepâncias ao usar o serviço de identidade:

* O uso contínuo do cookie legacy s_vi. Isso contribui para as discrepâncias da coleta de dados.
* Contar duas vezes os visitantes ao navegar de uma pesquisa até um pop-up.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**O que acontece no Analytics quando o serviço de identidade não consegue definir o cookie AMCV?**

Existem três cenários em potencial em que isso afeta os dados do Analytics para novos visitantes:

1. Um usuário final deixa a página antes dos cookies AMCV serem definidos com sucesso (na janela de tempo limite de 30 segundos).

   Se um visitante deixar uma página antes de terminar de carregar, a ocorrência do Analytics não é enviada. O Analytics não receberá os dados desse cenário e considera os dados perdidos ao fechar a página antecipadamente. Com base nos testes que incluíram as localidades próximas, descobrimos que esse cenário representa menos de 1% do tráfego médio. É importante observar que esse cenário ocorre mesmo sem a presença do serviço de identidade: é um artefato da inclusão do código de coleta de dados do Analytics no fim da página.

1. Um usuário final não recebe um serviço de identidade ou uma Analytics ID na janela de tempo limite de 30 segundos devido às conexões lentas ou à "rotação" do navegador.

   O serviço de identidade e a Analytics ID não são definidos e ao visitante é atribuída uma ID de cliente. Embora isso permite a captura dos dados do Analytics, o perfil do visitante será interrompido quando uma Analytics ID for definida em uma página subsequente. A ID do lado do cliente também não corresponderá ao perfil do visitante existente armazenado no Audience Manager ou no Analytics. Essa ID do lado do cliente também aparecerá como dois visitantes diferentes no Analytics se dois domínios separados estiverem sendo enviados para o mesmo conjunto de relatórios.

1. Um usuário final não recebe um serviço de identidade durante a janela de tempo limite de 30 segundos, mas recebe uma ID de rastreamento padrão do Analytics e o período de carência não é habilitado.

   O cenário três tem o mesmo resultado do cenário dois com a ID do lado do cliente sendo usada.

>[!TIP]
>
>O uso das atualizações mais recentes para VisitorAPI.js e AppMeasurement.js com as configurações padrão deve evitar qualquer impacto grave ou observável devido aos três cenários improváveis acima.

>[!MORE_LIKE_THIS]
>
>* [Atendimento ao cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html)

