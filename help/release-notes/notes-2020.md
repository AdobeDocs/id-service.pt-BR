---
description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
keywords: Serviço de ID
title: Notas de versão de 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 99%

---

# Notas de versão da Experience Cloud - 2020 {#release-notes}

Lançamentos, atualizações ou mudanças futuras do Serviço de identidade da Experience Cloud.

## Versão 5.1.1

* Patch de correção para a configuração do cookie AMCV com `SameSite=None` quando VisitorJS é carregado em um iFrame.

## Versão 5.1.0

* Adicionar configuração de `sameSiteCookie` para especificar o atributo `SameSite` do cookie AMCV. Essa configuração aceita os seguintes valores para o atributo `SameSite`:
   * `Strict`
   * `Lax`
   * `None`

Para obter mais informações sobre esses valores de atributos, visite [web.dev](https://web.dev/samesite-cookies-explained/) e [Atualizações do SameSite por The Chromium Projects](https://www.chromium.org/updates/same-site/).

## Versão 5.0.1

* Patch de correção para incluir o sinalizador `d_cf` quando uma nova string de consentimento IAB é enviada para as bordas da Coleção de dados da Adobe.

## Versão 5.0.0

* Versão 5.0.0 do Visitor com suporte para `IAB 2.0`.

## Versão 4.6

* Ativar `loadSSL` sinalizador por padrão. Todas as chamadas para o Serviço de identidade serão ativadas `https` por padrão.  Os clientes podem defini-lo como falso se quiserem chamar os Serviços de identidade no http a partir de suas `non-ssl` páginas.
* Atualização da função usada para detectar a `Internet-Explorer (IE)` versão para corrigir um problema reportado por `ESLint`.
Correção de um problema de desempenho em `Internet-Explorer (IE) 11` que a ECID recebe o opt-in `pre-approval` e é atualizada posteriormente.

## Versão 4.5

* A partir da versão 4.5, a ECID rejeitará IDs em branco enviados para o método `setCustomerIDs`.
* Correção de um problema em que o opt-in é configurado como `doesOptInApply=false` e `isIabContext=true`.

Consulte as [notas de versão da Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=pt-BR) para ver as notas de versão mensais de todos os produtos.
