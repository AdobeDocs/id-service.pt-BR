---
description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
keywords: Serviço de ID
seo-description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
seo-title: Notas de versão de 2020
title: Notas de versão de 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '147'
ht-degree: 100%

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

Consulte as [notas de versão da Experience Cloud](https://docs.adobe.com/content/help/pt-BR/release-notes/experience-cloud/current.html) para ver as notas de versão mensais de todos os produtos.
