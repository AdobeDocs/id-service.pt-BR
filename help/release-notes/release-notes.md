---
description: Lançamentos, atualizações ou alterações de recursos no serviço de identidade da Experience Cloud.
keywords: Serviço de ID
seo-description: Lançamentos, atualizações ou alterações de recursos no serviço de identidade da Experience Cloud.
seo-title: Notas de versão de 2019
title: Notas de versão de 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# Notas de versão de 2019 {#release-notes}

Lançamentos, atualizações ou alterações de recursos no serviço de identidade da Experience Cloud.

## Notas de versão de 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Lançamentos, atualizações e alterações de recursos do serviço da [!DNL Experience Cloud] ID.

## Versão 4.4 {#version-4point4}

**Novo recurso**

[SHA 256 Hashing Support for setcustomerids](/help/reference/hashing-support.md). O serviço da Experience Cloud ID (ECID) é compatível com o algoritmo de hash SHA -256 que permite transmitir IDs do cliente ou endereços de email e enviar IDs com hash.

**Correções, melhorias, melhorias**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE-29223)
* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE-31287)
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE-29719)
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE-30623)

## Versão 4.3 {#version-4point3}

**Suporte para ITP 2.1**. Se um servidor de rastreamento estiver definido em CNAME próprio, um novo cookie (s_ ecid) será colocado com o valor ECID. A biblioteca ECID faz referência ao valor para persistir na ID além de 7 dias. See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Correção de bug para a configuração securecookie.**

## Versão 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Serviço de opt-in**. Opt-in é uma extensão da Experience Cloud ID (ECID) que permite controlar se as bibliotecas da Experience Cloud podem criar cookies em páginas da Web para visitantes. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versão 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Descrição |
|---|---|
| O sinalizador `disableIdSyncs` não está funcionando ao passar uma string. | Fixo. Os valores definidos no `disableidSyncs` parâmetro para a `getInstance` função agora são honrados. |
| iFrames de terceiros não recebem uma ECID | Correção da ECID no Safari Mobile e de ECIDs em vários iFrames que não funcionavam. |

