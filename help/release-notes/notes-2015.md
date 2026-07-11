---
description: Notas de versão e atualizações de 2015.
keywords: Serviço de ID de visitante
title: Notas de versão de 2015
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
TQID: https://experienceleague.adobe.com/WmeSY7aRbvnZJN0a-lNR-yYzWzF4dfJLPZqA--6lpYQ
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 457
ht-degree: 60%

---

# Notas de versão de 2015 {#release-notes}

Notas de versão e atualizações de 2015.

## Versão 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Novembro de 2015

A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao código do Serviço de ID de visitante, de modo a evitar a definição de cookies no domínio de terceiros em um navegador. Consulte o [Suporte para COPPA no Serviço de ID de Visitante](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Para a versão 1.5.3 ou posterior.

## Versão 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

Setembro de 2015

* Correção de um erro no navegador Safari que impedia o funcionamento dos serviços de sincronização quando os usuários bloqueavam cookies de terceiros. (AAM-20764)
* As chamadas ao Serviço de ID do Visitante agora incluem a ID da versão no parâmetro `d_visid_ver=`. A ID retornada ajuda as equipes internas a solucionar problemas e questões de suporte. (AAM-20824)

## Versão 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

Agosto de 2015

* Correção de um bug que impedia o Serviço de ID do visitante de solicitar um iframe quando não havia dados para sincronizar ou acionar. (AAM-20164)
* Correção de um bug que impedia o Serviço de ID do visitante de configurar apropriadamente um cookie de domínio multiparte e de nível superior. Por exemplo, se você tem um domínio como `my_company.co.uk`, em determinadas circunstâncias o Serviço de ID do visitante definiria um cookie somente em `co.uk`. (AN-104683)

  Esse problema afetou apenas alguns clientes que atendiam a *todos* os seguintes critérios:

   * Uso do Serviço de ID de visitante.
   * Habilitados um [período de carência](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/migration) *ou* que estão usando cookies primários e os usuários bloqueiam cookies de terceiros.
   * Páginas com domínios multiparte e nível superior.

As revisões de documentação desta versão incluem:

* [Métodos de API e Biblioteca de código](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Reorganização de conteúdo e texto. Na maior parte dos casos, cada método recebe sua própria página.
* [Requisitos do Serviço de ID do Visitante](../reference/requirements.md): conteúdo revisado e texto reorganizado.

## Versão 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Julho de 2015

O Serviço de ID do visitante oferece suporte a várias IDs e estados de autenticação. Essa alteração também remove o suporte obsoleto aos mapeamentos DPID do Audience Manager para as IDs de usuário usadas pela função `setCustomerIDs`. Consulte [IDs do cliente e Estados de autenticação](../reference/authenticated-state.md)

## Versão 1.4 {#section-f5c596f355b14da28f45c798df513572}

Maio de 2015

Desde a versão 1.4, o método preferido para definir a configuração é passar um objeto de configuração como o segundo parâmetro para a função `Visitor.getInstance`.

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

## Versão 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Fevereiro de 2015

Correção do tratamento do tempo-limite em solicitações para AAM Blob e Dica de local. Agora, quando o tempo-limite for atingido, o sistema deixará esses campos em branco para a página atual e fará todos os retornos de chamada. O tempo-limite é tratado como uma condição de erro, portanto, ele tentará novamente na próxima página. (AN-94473, AN-94474)

## Versão 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Janeiro de 2015

A `<head>/<body>` pesquisa de tag retrabalhada para o contêiner de tag da solicitação JSONP `<script>`, assim como a criação da tag `<script>` para cuidar de diferentes implantações DOM (HTML vs. XHTML), com a possibilidade de diferentes configurações que diferenciam caracteres maiúsculos e minúsculos. (AN-9355)

