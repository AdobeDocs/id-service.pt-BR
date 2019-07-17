---
description: Lançamentos, atualizações ou alterações de recursos no serviço de identidade da Experience Cloud.
keywords: Serviço de ID
seo-description: Lançamentos, atualizações ou alterações de recursos no serviço de identidade da Experience Cloud.
seo-title: Notas de versão de 2019
title: Notas de versão de 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Notas de versão de 2019 {#release-notes}

Lançamentos, atualizações ou alterações de recursos no serviço de identidade da Experience Cloud.

## Notas de versão de 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Lançamentos, atualizações e alterações de recursos do serviço da [!DNL Experience Cloud] ID.

## Versão 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Serviço de opt-in**. Opt-in é uma extensão da Experience Cloud ID (ECID) que permite controlar se as bibliotecas da Experience Cloud podem criar cookies em páginas da Web para visitantes. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versão 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Descrição |
|---|---|
| O sinalizador `disableIdSyncs` não está funcionando ao passar uma string. | Fixo. Os valores definidos no `disableidSyncs` parâmetro para a `getInstance` função agora são honrados. |
| iFrames de terceiros não recebem uma ECID | Correção da ECID no Safari Mobile e de ECIDs em vários iFrames que não funcionavam. |

