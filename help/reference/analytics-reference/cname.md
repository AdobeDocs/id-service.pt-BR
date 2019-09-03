---
description: 'null'
keywords: ordem de operações, serviço de ID
seo-description: 'null'
seo-title: Coletas de dados CNAMEs e Rastreamento entre domínios
title: Coletas de dados CNAMEs e Rastreamento entre domínios
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Coletas de dados CNAMEs e Rastreamento entre domínios{#data-collection-cnames-and-cross-domain-tracking}

Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).

Nos navegadores que aceitam cookies de terceiros, um cookie é definido pelos servidores de coleta de dados durante a solicitação de uma ID de visitante. Esse cookie permite que o serviço de ID do visitante retorne a mesma ID de visitante da Experience Cloud em todos os domínios configurados usando a mesma ID da organização da Experience Cloud.

Nos navegadores que rejeitam cookies de terceiros, uma nova ID de visitante da Experience Cloud será atribuída para cada domínio.

O cookie demdex.net possibilita que o serviço de ID de visitante ofereça o mesmo nível de rastreamento entre domínios que o cookie s_vi do Analytics, onde o cookie é aceito em alguns navegadores e usado entre domínios, mas rejeitado por outros navegadores.

## Coletas de dados CNAME {#section-48fd186d376a48079769d12c4bd9f317}

Quando o cookie do Analytics foi definido pelo servidor de coleta de dados, muitos clientes configuraram os registros do servidor de coleta de dados CNAME como parte de uma [implementação de cookie próprio](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/) para evitar problemas com os navegadores que rejeitam cookies de terceiros. Esse processo configura o domínio do servidor da coleta de dados para corresponder ao domínio do site, de modo que o cookie da ID de visitante seja definido como um cookie original.

Como o serviço de ID de visitante define o cookie de visitante diretamente no domínio do site atual usando o JavaScript, esta configuração não é mais necessária para definir cookies originais.

Os clientes que possuem uma única propriedade da Web (um único domínio) podem sair das coletas de dados CNAME e usar seu nome de host da coleta de dados padrão no lugar (`omtrdc.net` ou `2o7.net`).

Contudo, existe outro benefício em usar um CNAME para a coleta de dados, que permite rastrear os visitantes entre um domínio inicial principal e outros domínios em navegadores que não aceitam cookies de terceiros. Os clientes que possuem várias propriedades da Web (vários domínios) se beneficiarão com a possibilidade de manter uma coleta de dados CNAME. A seção a seguir explica como o rastreamento de visitantes funciona entre domínios.

## Como os CNAMEs permitem o rastreamento entre domínios {#section-78925af798e24917b9abed79de290ad9}

Devido ao modo como os cookies originais podem ser usados em um contexto de terceiros no Apple Safari e em alguns outros navegadores, um CNAME permite rastrear os clientes entre um domínio primário e outros domínios que usaram o mesmo servidor de rastreamento.

Por exemplo, você tem um site primário em `mymainsite.com`. Você configurou o registro CNAME para apontar para o servidor de coleta de dados seguro: `smetrics.mymainsite.com`.

Quando um usuário visita `mymainsite.com`, o cookie do serviço de ID é definido pelo servidor de coleta de dados. Isso é permitido, pois o domínio do servidor de coleta de dados corresponde ao domínio do site e o que é conhecido como usar um cookie em um *contexto próprio* ou apenas um *cookie próprio*.

Se você também está usando os mesmos servidores de coleta de dados em outros sites (por exemplo, `myothersiteA.com` e `myothersiteB.com`) e um visitante entrar posteriormente nesses sites, o cookie definido durante a visita ao `mymainsite.com` é enviado na solicitação HTTP para o servidor de coleta de dados (lembre-se que os navegadores enviam todos os cookies para um domínio com todas as solicitações HTTP para esse domínio, mesmo que o domínio não corresponda ao domínio do site atual). Isso é conhecido como usar um cookie em um *contexto de terceiros* ou apenas um *cookie de terceiros* e permite que a mesma ID de visitante seja usada em outros domínios. Observe que os navegadores tratam os cookies em contextos de terceiros de forma diferente dos cookies próprios.

*Observação: o Safari bloqueia todos os cookies no contexto de terceiros, independentemente de como foram definidos.*

Assim, seu domínio de coleta deve ser um domínio que as pessoas costumam visitar, para que um visitante seja identificado em domínios. Se não há um domínio *comum* para usar no domínio de coleta de dados, não há benefício entre domínios para manter um CNAME do domínio de coleta de dados. Se o site de entrada principal não for visitado primeiro, os visitantes serão identificados de maneiras diferentes no site secundário e no site principal.

## Habilitar o suporte para CNAME com o serviço de identidade da Experience Cloud {#section-25d4feb686d944e3a877d7aad8dbdf9a}

O suporte do servidor de coleta de dados CNAME é ativado ao configurar as `visitor.marketingCloudServerSecure` variáveis.
