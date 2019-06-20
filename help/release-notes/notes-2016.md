---
description: Lançamentos, atualizações ou alterações de recursos no serviço da Experience Cloud ID para 2016.
keywords: Serviço de ID
seo-description: Lançamentos, atualizações ou alterações de recursos no serviço da Experience Cloud ID para 2016.
seo-title: Notas de versão de 2016
title: Notas de versão de 2016
uuid: 7 a 5 a 314 a -3 ff 8-4561-9 c 64-6 c 10 d 2223887
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Notas de versão de 2016 {#release-notes}

Lançamentos, atualizações ou alterações de recursos no serviço da Experience Cloud ID para 2016.

Essas alterações também estão contempladas nas [notas de versão da Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/). Consulte as [notas de versão anteriores](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) para ver anúncios anteriores.[!DNL Experience Cloud]

## Version 1.10 {#section-7d719b3213344a46858835042e0214ed}

Novembro de 2016

>[!IMPORTANT]
>
>* Version 1.10 requires [!DNL AppMeasurement] 1.8.0.
>* Usando a Biblioteca de serviço da Experience Cloud ID 2.0.0 +, a sincronização de ID será iniciada para o Adobe Media Optimizer por padrão. Consulte [Entender sincronização de ID e taxas de correspondência](/help/introduction/match-rates.md).


**Correções e melhorias**

* Adicionadas instruções sobre como implementar o serviço de ID em um ambiente do servidor.
* Adicionada `Visitor.overwriteCrossDomainMCIDAndAID`, uma função booleana que permite substituir as IDs da Experience Cloud e Analytics em outros domínios pertencentes a você. See [Overwrite Visitor ID](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* Adição do `TS = UTC`carimbo de data e hora   como a propriedade da função `visitor.appendVisitorIDsTo`. O serviço de ID usa o carimbo de data e hora para determinar se é preciso usar as IDs no URL de redirecionamento com base em um intervalo de 5 minutos. Consulte [Função Anexar ID do visitante](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Added `Visitor.getLocationHint,` a new function that returns a region ID. See [Get Region IDs (Location Hint)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* Adicionadas `idSyncByURL` e `idSyncByDataSource`, 2 funções que permitem implementar manualmente uma sincronização de ID no iFrame de publicação de destino. See [ID Synchronization by URL or Data Source](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Corrigido um problema que bloqueava a chamada de rastreamento do AppMeasurement se `disableThirdPartyCalls:true`.
* Corrigido um bug que impedia o serviço de ID de passar a Experience Cloud ID (MID) para domínios diferentes.

## Version 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Outubro de 2016

**Correções e melhorias**

* Corrigido um bug que passava as IDs exclusivas do usuário do Audience Manager (AAMUUIDs) como Experience Cloud IDs para o serviço de ID.
* Se a vida útil (TTL) de um cookie AMCV tiver expirado, o serviço de ID retornará essa informação ao servidor, desde que o cookie contenha uma Experience Cloud ID. Após esta chamada, o serviço de ID faz uma chamada assíncrona para atualizar o cookie. Isso ajuda a aprimorar o desempenho, pois o serviço de ID não precisa aguardar uma resposta do servidor. Ele pode usar valores de cookies AMCV já existentes e solicitar uma atualização.
* O serviço de ID sincroniza automaticamente as Experience Cloud IDs (MIDs) com o Adobe Media Optimizer e outros domínios internos da Adobe diretamente na página. A sincronização automática está habilitada para todas as contas atuais e novas. Isso ajuda a aumentar as taxas de correspondência no Media Optimizer. Aplicável ao VisitorAPI.js versão 1.8 ou mais recente. Consulte também [Como entender a sincronização de IDs e as taxas de correspondência](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Documentação nova e revisada**

**Novo:**[Obter as IDs de região e de usuário do cookie AMCV](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Version 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

Setembro de 2016

**Correções e melhorias**

Adicionado `disableThirdPartyCalls` como um sinalizador booleano opcional, que pode ser definido na função `Visitor.getInstance`. Quando `disableThirdPartyCalls= true`, o serviço de ID não fará chamadas para outros domínios. Por padrão, `disableThirdPartyCalls= false` Consulte [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Versão 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

Agosto de 2016

**Correções e melhorias**

* Adicionado `idSyncAttachIframeOnWindowLoad` como um sinalizador booleano que pode ser definido na função `Visitor.getInstance`. Quando `idSyncAttachIframeOnWindowLoad= true`, o serviço de ID carrega o iFrame de sincronização de ID na janela. Por padrão, o serviço de ID carrega o iFrame o mais rápido possível. Esse sinalizador *substitui* `idSyncAttachIframeASAP`, que está obsoleto. See [Visitor.getInstance Function Variables](../library/function-vars/function-vars.md).

* Adicionado o recuso compatível com o rastreamento de [!DNL Experience Cloud] IDs por domínios, aplicativos nativos e híbridos em transições da Web. Consulte [Função de ajuda Anexar ID do visitante](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Adicionadas funções ao código visitorAPI.js que especificam se o serviço de ID gerou a [!DNL Experience Cloud] ID de visitante ou de servidor, ou se as chamadas atingirem o tempo limite. See [Funções de rastreamento de tempo limite](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) e [Rastreamento da geração de ID de visitante do cliente](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Documentação nova e revisada**

Revised: [Requirements for the Experience Cloud ID Service](../reference/requirements.md)

**Problemas conhecidos**

Clientes que usarem os códigos DIL do [!DNL Audience Manager] e visitorAPI.js na mesma página deverão definir a variável DIL como `secureDataCollection= false`. Consulte [secureDataCollection](https://marketing.adobe.com/resources/help/en_US/aam/?f=dil-secure-data-collection.html).

## Version 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Julho de 2016

>[!IMPORTANT]
>
>Version 1.6.0 of the [!DNL Experience Cloud] ID service *requires* AppMeasurement for JavaScript version 1.6.2. If you upgrade to ID service version 1.6.0, please make sure you are using the right AppMeasurement code version.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recurso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>CORS (Cross-Origin Resource Sharing, ou Compartilhamento de recursos de várias origens) </p> </td> 
   <td colname="col2"> <p>O CORS permite que os navegadores solicitem recursos de um domínio diferente do atual. O serviço da Experience Cloud ID é compatível com os padrões CORS para permitir solicitações de recursos de origem cruzada do cliente. O serviço de ID reverte solicitações JSONP em navegadores incompatíveis com CORS. </p> <p>Consulte: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Suporte para CORS no serviço de Experience Cloud ID </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Correções e melhorias**

* Adição de um parâmetro `d_fieldgroup` para chamadas de sincronização de ID para `dpm.demdex.net`. O novo parâmetro é usado para solucionar problemas internos e realizar a depuração.

* Adicionado um atributo de título ao iFrame do serviço de ID. Um título de iFrame ajuda os leitores de tela a fornecerem informações de página aos usuários que precisam de auxílio em interações com conteúdos online. O atributo de título do iFrame está definido como `Adobe ID Syncing iFrame`.
* Adição do `idSyncAttachIframeASAP: true` como um sinalizador opcional que pode ser definido na função `Visitor.getInstance`. Quando definido como `true`, o serviço de ID carrega o iFrame de sincronização de ID da maneira mais rápida possível. Isso foi criado para ajudar a melhorar as taxas de correspondência de sincronização de ID. Por padrão, o serviço de ID carrega o iFrame na janela. See [Visitor.getInstance Function Variables](../library/function-vars/function-vars.md).

* Corrigido um bug com uma função de retorno de chamada que provocava um loop infinito no AppMeasurement.
* Alterado o intervalo padrão de `loadTimeout` de 500 milissegundos para 30.000 milissegundos. See [Visitor.getInstance Function Variables](../library/function-vars/function-vars.md).

**Documentação nova e revisada**

**Novo menu**

* [Implementar o serviço da Experience Cloud ID no Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Implementar o serviço da Experience Cloud ID para o Analytics, o Audience Manager e o Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Revisado**

* [Requisitos para o serviço de Experience Cloud ID](../reference/requirements.md)
* [Testar e verificar o serviço da Experience Cloud ID](../implementation-guides/test-verify.md)

## Version 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

Junho de 2016

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recurso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Alterações no atributo <span class="codeph">iframe.sandbox</span> </p> </td> 
   <td colname="col2"> <p>Agora, o iFrame fica configurado da seguinte maneira: <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>A permissão de apenas estes dois tokens ajuda a melhorar a segurança, além de oferecer o serviço de ID com o recurso básico necessário para a sincronização de ID. </p> <p>O atributo sandbox não é compatível com o Internet Explorer versão 9 ou anterior. Para obter mais informações, consulte a seção Atributos na <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" format="https" scope="external">Documentação do iFrame </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Codificação da Experience Cloud ID (MID) </p> </td> 
   <td colname="col2"> <p>O serviço de ID codifica o valor MID originado do servidor ou quando ele está configurado pela função <span class="codeph">visitor.setMarketingCloudVisitorID()</span>. For more information about the MID, see <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies and the Experience Cloud ID </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correções**

A API de visitante deixou de forçar uma chamada extra de re-sincronização com o Audience Manager quando não há uma ID antiga de visitante do Analytics.

## Versão 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Maio de 2016

**Atualizações de documentação**

* [Requisitos do SDK para Android e iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench e o serviço da Experience Cloud ID](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [Testar e verificar o serviço da Experience Cloud ID](../implementation-guides/test-verify.md)

## Versão 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

Abril de 2016

**Atualizações de documentação**

[Implementar o serviço da Experience Cloud ID no Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## Version 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

Março de 2016

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recurso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Suporte para cancelamento </p> </td> 
   <td colname="col2"> <p>O serviço da <span class="keyword">Experience Cloud</span> ID é compatível com solicitações de recusa do visitante. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Alteração do intervalo de sincronização de ID </p> </td> 
   <td colname="col2"> <p>O serviço da <span class="keyword">Experience Cloud ID</span> agora faz chamadas de sincronização de ID em cada chamada para os servidores de coleta de dados. Antes, o serviço de ID realizava apenas uma solicitação durante a primeira chamada para a obtenção de uma <span class="keyword">Experience Cloud</span> ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Atualizações de documentação**

* [Implementar o serviço da Experience Cloud ID para ](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd): novo procedimento que descreve como configurar o serviço de ID com o Analytics[!DNL Analytics].

* [Pontos de decisão de migração do serviço da Experience Cloud ID](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257) : texto revisado para esclarecer alguns pontos. Trabalhar com um domínio único significa poder migrar de um CNAME de coleta de dados se não desejar mais gerenciá-lo. No entanto, não há necessidade de realizar essa alteração se o CNAME estiver funcionando.

## Versão 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Janeiro de 2016

**Atualizações de documentação**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Tópico </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> Estados de autenticação e IDs do cliente </a> </p> </td> 
   <td colname="col2"> <p>Texto revisado. As IDs do cliente devem ser passadas apenas como valores não codificados. A codificação das IDs cria identificadores duplamente codificados. </p> </td> 
  </tr> 
 </tbody> 
</table>

