---
description: Lançamentos, atualizações ou alterações de recursos no serviço da Experience Cloud ID.
keywords: Serviço de ID
seo-description: Lançamentos, atualizações ou alterações de recursos no serviço da Experience Cloud ID.
seo-title: Notas de versão de 2019
title: Notas de versão de 2019
uuid: a 5 a 59410-7 f 85-48 f 9-a 30 a-fef 1 c 2 e 2 b 558
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Notas de versão de 2019 {#release-notes}

Lançamentos, atualizações ou alterações de recursos no serviço da Experience Cloud ID.

## Notas de versão de 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Lançamentos, atualizações e alterações de recursos do serviço da [!DNL Experience Cloud] ID.

## Versão 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Serviço de opt-in**. Opt-in é uma extensão da Experience Cloud ID (ECID) que permite controlar se as bibliotecas da Experience Cloud podem criar cookies em páginas da Web para visitantes. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versão 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Descrição |
|---|---|
| O sinalizador `disableIdSyncs` não está funcionando ao passar uma string. | Correção. Values set on `disableidSyncs` parameter for `getInstance` function are now being honored. |
| iFrames de terceiros não recebem uma ECID | Correção da ECID no Safari Mobile e de ECIDs em vários iFrames que não funcionavam. |

