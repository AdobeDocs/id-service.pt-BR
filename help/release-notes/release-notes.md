---
description: Lançamentos, atualizações ou alterações de recursos no Serviço de identidade da Experience Platform.
keywords: Serviço de ID
seo-description: Lançamentos, atualizações ou alterações de recursos no Serviço de identidade da Experience Platform.
seo-title: Notas de versão de 2019
title: Notas de versão de 2019
uuid: a 5 a 59410-7 f 85-48 f 9-a 30 a-fef 1 c 2 e 2 b 558
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Notas de versão de 2019 {#release-notes}

Lançamentos, atualizações ou alterações de recursos no Serviço de identidade da Experience Platform.

## Notas de versão de 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Lançamentos, atualizações e alterações de recursos do serviço da [!DNL Experience Cloud] ID.

## Versão 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Serviço de opt-in**. O Opt-in é uma extensão da [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) que permite controlar se (e quais) as bibliotecas da Experience Cloud podem criar cookies nas páginas web para os visitantes. Usando o [Launch](https://docs.adobelaunch.com/), você pode simplificar a obtenção dos consentimentos de opt-in dos visitantes para a solução da Experience Cloud habilitado o Analytics, o Target, o Audience Manager e outras ou todas as soluções selecionadas da Experience Cloud no seu sistema de gerenciamento de consentimentos.

## Versão 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Descrição |
|---|---|
| O sinalizador `disableIdSyncs` não está funcionando ao passar uma string. | Correção. Os valores definidos no `disableidSyncs` parâmetro para `getInstance` função agora são respeitados. |
| iFrames de terceiros não recebem uma ECID | Correção da ECID no Safari Mobile e de ECIDs em vários iFrames que não funcionavam. |

