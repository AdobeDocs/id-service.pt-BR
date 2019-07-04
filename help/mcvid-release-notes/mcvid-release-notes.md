---
description: Lançamentos, atualizações ou mudanças futuras do serviço da Experience Cloud ID.
keywords: Serviço de ID
seo-description: Lançamentos, atualizações ou mudanças futuras do serviço da Experience Cloud ID.
seo-title: Notas de versão de 2019
title: Notas de versão de 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Notas de versão de 2019 {#release-notes}

Lançamentos, atualizações ou mudanças futuras do serviço da Experience Cloud ID.

## Notas de versão de 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Lançamentos, atualizações e alterações de recursos do serviço da [!DNL Experience Cloud] ID.

## Versão 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Serviço de opt-in**. O Opt-in é uma extensão da [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/pt_BR/mcvid/) que permite controlar se (e quais) as bibliotecas da Experience Cloud podem criar cookies nas páginas web para os visitantes. Com o [Launch](https://docs.adobelaunch.com/), é possível simplificar a obtenção dos consentimentos de Opt-in dos visitantes para a solução da Experience Cloud, por meio da ativação do Analytics, do Target, do Audience Manager e de outras soluções ou todas as soluções selecionadas da Experience Cloud no sistema de gerenciamento de consentimentos.

## Versão 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Descrição |
|---|---|
| O sinalizador `disableIdSyncs` não está funcionando ao passar uma string. | Fixo. Os valores definidos no `disableidSyncs` parâmetro para a `getInstance` função agora são honrados. |
| iFrames de terceiros não recebem uma ECID | Correção da ECID no Safari Mobile e de ECIDs em vários iFrames que não funcionavam. |

