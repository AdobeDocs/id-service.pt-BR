---
description: Lançamentos, atualizações ou alterações de recursos do serviço de identidade da Experience Cloud para 2018.
keywords: Serviço de ID
title: Notas de versão de 2018
exl-id: ad3cccf1-2753-4ac9-a68c-15b2d62bbc1a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 100%

---

# Notas de versão de 2018 {#release-notes}

Lançamentos, atualizações ou alterações de recursos do serviço de identidade da Experience Cloud para 2018.

## Versão 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrição do item </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Mais segurança para cookies AMCV </p> </td> 
   <td colname="col2"> <p>Durante uma verificação de segurança interna, foi descoberto que, ao usar a biblioteca DTM, os cookies usados para o gerenciamento da sessão não especificavam atributos adequados. Isso pode resultar no compartilhamento indevido das informações do cookie. Para resolver esse problema, introduzimos uma configuração que permite ao Cliente definir o cookie AMCV como seguro. Consulte <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versão 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrição do item </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Mais segurança para cookies AMCV </p> </td> 
   <td colname="col2"> <p>Durante uma verificação de segurança interna, foi descoberto que, ao usar a biblioteca DTM, os cookies usados para o gerenciamento da sessão não especificavam atributos adequados. Isso pode resultar no compartilhamento indevido das informações do cookie. Para resolver esse problema, introduzimos uma configuração que permite ao Cliente definir o cookie AMCV como seguro. Consulte secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>O código de integração e a id devem ser números ou strings não vazias </p> </td> 
   <td colname="col2"> <p>Correção de um erro que ocorria ao validar `setCustomerIDs` quando os dados continham uma integração `code` ou `id` que não era um número nem uma string não vazia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> O JS da ECID está disponível no repositório Git público </td> 
   <td colname="col2"> O JS da ECID agora está disponível no repositório Git público para todos os clientes da Experience Cloud em https://github.com/Adobe-Marketing-Cloud/id-service/releases. </td> 
  </tr> 
 </tbody> 
</table>

## Versão 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrição do item </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Pico irreal na contagem de visitantes únicos </p> </td> 
   <td colname="col2"> <p>Com o lançamento do Serviço de identidade da Experience Cloud 3.1.0, encontramos um problema que causava um pico irreal na contagem de visitantes únicos quando a versão foi implementada. Esse comportamento será exibido somente com a versão mais recente da ECID, v3.1.0, e se o usuário selecionar a opção "Permitir somente no site atual" nas configurações de privacidade de um navegador Safari. A versão 3.1.2 corrige esse problema. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versão 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>É recomendado atualizar da versão 3.1.0 para a versão mais recente assim que possível. Consulte a descrição da versão 3.1.2. O pacote mais recente está disponível na Adobe Experience Platform Launch, DTM e AppMeasurement.

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrição do item </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie definido no domínio incorreto </p> </td> 
   <td colname="col2"> <p>Corrigimos um erro em que o cookie temporário do Visitante definia um cookie no domínio do cookie "padrão", em vez de configurá-lo no domínio fornecido na configuração (initConfig). </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versão 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrição do item </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Concessão de encadeamento para solicitações de sincronização de várias IDs </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>Para clientes executando sincronizações de várias IDs, devido a computações contínuas de CPU sendo executadas, a interface do usuário às vezes é bloqueada. Estamos introduzindo a concessão de encadeamento para separar as solicitações de sincronização de ID por 100 ms cada. </p> <p>Essa alteração melhora o desempenho para clientes que usam o Visitor 2.3.0+ e o DIL 6.10+. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Adicionou a capacidade de desabilitar chamadas de terceiros </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>A Adobe renomeou as seguintes configurações para permitir desabilitar chamadas sincronizadas de terceiros. </p> <p>idSyncDisableSyncs para disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing para disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Suporte ao Internet Explorer </p> </td> 
   <td colname="col2"> <p>O serviço de ID não é mais compatível com o Internet Explorer 6, 7, 8 e 9. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Atualização da documentação de getInstance </p> </td> 
   <td colname="col2"> <p>Adicionou um aviso à função Visitor para que ela não seja instanciada com var visitor = new Visitor. </p> </td> 
  </tr> 
 </tbody> 
</table>
