---
description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
keywords: ID Service
seo-description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
seo-title: Notas de versão de 2020
title: Notas de versão de 2020
translation-type: tm+mt
source-git-commit: d0057a8242dafca63101b1a2f569766bde11bea7
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 91%

---


# Notas de versão da Experience Cloud - 2020 {#release-notes}

Lançamentos, atualizações ou alterações de recursos do serviço de identidade da Experience Cloud (ECID).

## Versão 4.6

* Ativar `loadSSL` sinalizador por padrão. Todas as chamadas para o Serviço de identidade serão ativadas `https` por padrão.  Os clientes podem defini-lo como falso se quiserem chamar os Serviços de identidade no http a partir de suas `non-ssl` páginas.
* Atualização da função usada para detectar a `Internet-Explorer (IE)` versão para corrigir um problema reportado por `ESLint`.
Correção de um problema de desempenho em `Internet-Explorer (IE) 11` que a ECID recebe o opt-in `pre-approval` e é atualizada posteriormente.

## Versão 4.5

* A partir da versão 4.5, a ECID rejeitará IDs em branco enviados para o método `setCustomerIDs`. 
* Correção de um problema em que o opt-in é configurado como `doesOptInApply=false` e `isIabContext=true`.

Consulte as notas [de versão do](https://docs.adobe.com/content/help/pt-BR/release-notes/experience-cloud/current.html) Experience Cloud para ver as notas de versão mensais de todos os produtos.
