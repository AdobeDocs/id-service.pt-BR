---
description: 'null'
keywords: ordem das operações; Serviço de ID
seo-description: 'null'
seo-title: Coletas de dados CNAME e rastreamento entre domínios
title: Coletas de dados CNAME e rastreamento entre domínios
uuid: ba 42 c 822-b 677-4139-b 1 ed -4 d 98 d 3320 fd 0
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Coletas de dados CNAMEs e Rastreamento entre domínios{#data-collection-cnames-and-cross-domain-tracking}

Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).

Nos navegadores que aceitam cookies de terceiros, um cookie é definido pelos servidores de coleta de dados durante a solicitação de uma ID de visitante. Esse cookie permite que o serviço de ID do visitante retorne a mesma ID de visitante da Experience Cloud em todos os domínios configurados usando a mesma ID da organização da Experience Cloud.

Nos navegadores que rejeitam cookies de terceiros, uma nova ID de visitante da Experience Cloud será atribuída para cada domínio.

O cookie demdex.net possibilita que o serviço de ID de visitante ofereça o mesmo nível de rastreamento entre domínios que o cookie s_vi do Analytics, onde o cookie é aceito em alguns navegadores e usado entre domínios, mas rejeitado por outros navegadores.

## Coletas de dados CNAME {#section-48fd186d376a48079769d12c4bd9f317}

Quando o cookie do Analytics foi definido pelo servidor de coleta de dados, muitos clientes configuraram os registros do servidor de coleta de dados CNAME como parte de uma [implementação de cookie original](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/) para evitar problemas com os navegadores que rejeitam cookies de terceiros. Esse processo configura o domínio do servidor da coleta de dados para corresponder ao domínio do site, de modo que o cookie da ID de visitante seja definido como um cookie original.

Como o serviço de ID de visitante define o cookie de visitante diretamente no domínio do site atual usando o JavaScript, esta configuração não é mais necessária para definir cookies originais.

Os clientes que possuem uma única propriedade da Web (um único domínio) podem sair das coletas de dados CNAME e usar seu nome de host da coleta de dados padrão no lugar (`omtrdc.net` ou `2o7.net`).

Contudo, existe outro benefício em usar um CNAME para a coleta de dados, que permite rastrear os visitantes entre um domínio inicial principal e outros domínios em navegadores que não aceitam cookies de terceiros. Os clientes que possuem várias propriedades da Web (vários domínios) se beneficiarão com a possibilidade de manter uma coleta de dados CNAME. A seção a seguir explica como o rastreamento de visitantes funciona entre domínios.

## Como os CNAMEs permitem o rastreamento entre domínios {#section-78925af798e24917b9abed79de290ad9}

Devido ao modo como os cookies originais podem ser usados em um contexto de terceiros no Apple Safari e em alguns outros navegadores, um CNAME permite rastrear os clientes entre um domínio primário e outros domínios que usaram o mesmo servidor de rastreamento.

Por exemplo, você tem um site primário em `mymainsite.com`. You configured the CNAME record to point to your secure data collection server: `smetrics.mymainsite.com`.

Quando um usuário visita `mymainsite.com`, o cookie do serviço de ID é definido pelo servidor de coleta de dados. This is allowed since the domain of the data collection server matches the domain of the website, and is what is known as using a cookie in a *first-party context*, or just a *first-party cookie*.

If you are also using this same data collection server on other sites (for example, `myothersiteA.com`, and `myothersiteB.com`), and a visitor later visits these sites, the cookie that was set during the visit to `mymainsite.com` is sent in the HTTPS request to the data collection server (remember that browsers send all cookies for a domain with all HTTPS requests to that domain, even if the domain doesn&#39;t match the domain of the current website). This is what is known as using a cookie in a *third-party context*, or just a *third-party cookie*, and it enables the same visitor ID to be used on these other domains. Observe que os navegadores tratam os cookies em contextos de terceiros de forma diferente do que os cookies primários.

*Observação: O Safari bloqueia todos os cookies no contexto de terceiros independentemente de como eles estejam definidos.*

Assim, seu domínio de coleta deve ser um domínio que as pessoas costumam visitar, para que um visitante seja identificado em domínios. If there is no *common* domain to use for the data collection domain, there is no cross-domain benefit to maintaining a CNAME for the data collection domain. Se o site de entrada principal não for visitado primeiro, os visitantes serão identificados de maneiras diferentes no site secundário e no site principal.

## Habilitar o suporte para CNAME com o serviço da Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Data collection server CNAME support is enabled by setting the `visitor.marketingCloudServerSecure` variables.
