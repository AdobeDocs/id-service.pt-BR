---
description: Notas de versão e atualizações de 2015.
keywords: Serviço de ID
title: Notas de versão de 2015
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 100%

---

# Notas de versão de 2015 {#release-notes}

Notas de versão e atualizações de 2015.

## Versão 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Novembro de 2015

A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao código de serviço da [!DNL Experience Cloud] ID, de modo a evitar a definição de cookies no domínio de terceiros em um navegador. Consulte [Suporte ao COPPA no serviço de identidade da Experience Cloud](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Para a versão 1.5.3 ou posterior.

## Versão 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

Setembro de 2015

* Correção de um bug no navegador Safari que impedia o funcionamento dos serviços de sincronização quando os usuários bloqueavam cookies de terceiros. (AAM-20764)
* As chamadas ao serviço de ID agora incluem a ID da versão no parâmetro `d_visid_ver=`. A ID retornada ajuda as equipes internas a solucionar problemas e questões de suporte. (AAM-20824)

## Versão 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

Agosto de 2015

* Correção de um bug que impedia o serviço de ID de solicitar um iframe quando não havia dados para sincronizar ou acionar. (AAM-20164)
* Correção de um bug que impedia o serviço de ID de configurar apropriadamente um cookie de domínio multiparte e de nível superior. Por exemplo, se você tem um domínio como `my_company.co.uk`, em determinadas circunstâncias o serviço de ID definiria um cookie somente em `co.uk`. (AN-104683)

   Esse problema afetou apenas alguns clientes que atendiam a *todos* os seguintes critérios:

   * Utilização do serviço de ID.
   * Ativação de um [período de carência ](../reference/analytics-reference/grace-period.md)*ou* utilização de cookies primários, além de usuários que bloquearam os cookies de terceiros.

   * Páginas com domínios multiparte e nível superior.

As revisões de documentação desta versão incluem:

* [Métodos de API e Biblioteca de código](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Reorganização de conteúdo e texto. Na maior parte dos casos, cada método recebe sua própria página.
* [Requisitos do serviço de identidade da Experience Cloud](../reference/requirements.md): Conteúdo revisado e texto reorganizado.

## Versão 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Julho de 2015

O serviço da [!DNL Experience Cloud] ID oferece suporte a diversas IDs e estados de autenticação. Essa alteração também remove o suporte obsoleto para o mapeamento [!DNL Audience Manager] DPID do às IDs de usuários usadas pela `setCustomerIDs`função. Consulte [IDs do cliente e Estados de autenticação](../reference/authenticated-state.md)

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

Consulte [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd).

## Versão 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Fevereiro de 2015

Correção do tratamento do tempo limite em solicitações para AAM Blob e Dica de local. Agora, quando o tempo limite for atingido, o sistema deixará esses campos em branco para a página atual e fará todos os retornos de chamada. O tempo limite é tratado como uma condição de erro, portanto, ele tentará novamente na próxima página. (AN-94473, AN-94474)

## Versão 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Janeiro de 2015

A `<head>/<body>` pesquisa de tag retrabalhada para o contêiner de tag da solicitação JSONP `<script>`, assim como a criação da tag `<script>` para cuidar de diferentes implantações DOM (HTML vs. XHTML), com a possibilidade de diferentes configurações que diferenciam caracteres maiúsculos e minúsculos. (AN-9355)
