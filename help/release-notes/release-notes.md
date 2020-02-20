---
description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
keywords: ID Service
seo-description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
seo-title: Notas de versão de 2019
title: Notas de versão de 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: ba84c4dac9023ab13f5176c5665adbbdaeb00d33

---


# Notas de versão de 2019 {#release-notes}

Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.

## Notas de versão de 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Lançamentos, atualizações e alterações de recursos do serviço da [!DNL Experience Cloud] ID.

## Versão 4.4 {#version-4point4}

**Novo recurso**

[Suporte a hash SHA 256 para setCustomerIDs](/help/reference/hashing-support.md). O serviço de Experience Cloud ID (ECID) é compatível com o algoritmo de hash SHA -256 que permite transmitir IDs do cliente ou endereços de email e enviar IDs com hash.

**Correções, melhorias, aprimoramentos**

* Fizemos uma atualização de configuração no `cookieDomain`. A biblioteca ECID agora filtra a sequência vazia `cookieDomain` e `initConfig` e usa o domínio do cookie de nível superior, retornado pelo método getDomain. (CORE-29223)
* Corrigimos um erro relacionado ao `getVisitorValues` no `localVisitor`. (CORE-31287)
* Corrigimos um erro em que havia uma inconsistência no valor MCOPTOUT no navegador Safari, retornado pelo método `getVisitorValue`. (CORE-29719)
* Atualizamos a biblioteca de aceitação adicionando `optIn.off` para cancelar a inscrição nos eventos.
* Corrigimos um erro relacionado à função setTimeout, em que `setTimeout` violava a Política de segurança de conteúdo (CSP) em alguns sites do cliente. (CORE-30623)

## Versão 4.3 {#version-4point3}

**Suporte para ITP 2.1**. Se um servidor de rastreamento estiver definido em um CNAME próprio, um novo cookie (s_ecid) será colocado com o valor ECID. A biblioteca ECID faz referência ao valor para manter a ID além de 7 dias. Consulte [Métodos de biblioteca da ECID em um mundo da ITP Safari](/help/reference/ecid-library-methods.md).

**Correção de bug para a configuração secureCookie.**

## Versão 4.1

Atualização `publishDestinations` por nova alteração da API. Com essa atualização, as informações do referenciador da página podem ser expostas durante a sincronização de ID, se desejado. (CORE-23693)

## Versão 4.2

Suporte para o plug-in do Audience Manager para IAB TCF, disponível por meio do objeto de aceitação ECID.

**Correções**

* Falha do IAB + OptIn ao obter a MID para clientes revisitados (CORE-26022)
* Corrigido o erro na configuração do opt-in doOptInApply no DTM (DTM-12958)
* A opção de não participação ECID desativa sincronizações de ID (CORE-23814)

## Versão 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Serviço de opt-in**. O Opt-in é uma extensão da Experience Cloud ID (ECID) que permite controlar se (e quais) as bibliotecas da Experience Cloud podem criar cookies nas páginas da Web dos visitantes. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versão 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Descrição |
|---|---|
| O sinalizador`disableIdSyncs` não está funcionando ao passar uma string. | Fixo. Os valores definidos no `disableidSyncs` parâmetro para a `getInstance` função agora são honrados. |
| iFrames de terceiros não recebem uma ECID | Correção da ECID no Safari Mobile e de ECIDs em vários iFrames que não funcionavam. |

