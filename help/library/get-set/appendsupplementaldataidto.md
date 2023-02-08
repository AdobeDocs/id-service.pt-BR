---
description: Este método público anexa a ID de Dados Suplementares (SDID) como um parâmetro de sequência de consulta a um URL de redirecionamento. Isso é útil ao usar o A4T e é necessário manter a SDID de uma página para outra e unir essas visitas separadas. Para usar essa função, é necessário implementar o serviço de ID com a mesma ID da organização nos domínios de origem e destino.
keywords: Serviço de ID
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
source-git-commit: 2500b6d7b392731009f9149d8821be9505ba4b76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 96%

---

# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Este método público anexa a ID de Dados Suplementares (SDID) como um parâmetro de sequência de consulta a um URL de redirecionamento. Isso é útil ao usar o A4T e é necessário manter a SDID de uma página para outra e unir essas visitas separadas. Para usar essa função, é necessário implementar o serviço de ID com a mesma ID da organização nos domínios de origem e destino.

Conteúdo:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Sintaxe e amostra de código </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Saída de exemplo </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Sintaxe e amostra de código </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Alterar o tempo limite da SDID com sdidParamExpiry </a> </li> 
</ul>

## Sintaxe e amostra de código {#section-cbb0b2f73bcc418386796c24c01b2365}

**Sintaxe:** ` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Amostra de código**

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## Saída de exemplo {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Como mostrado abaixo, o redirecionamento do URL contém a SDID do visitante, a ID da organização e um carimbo de data e hora UNIX na chamada para a página de destino.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Alterar o tempo limite da SDID com sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

A configuração de [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) permite que você substitua o intervalo de expiração da ID de dados suplementares (SDID) padrão ao passá-la de uma página para outra usando a função auxiliar `appendSupplementalDataIDTo`. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter a SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não conseguir recuperar a SDID em menos de 30 segundos, ele solicitará uma nova SDID. Essa funcionalidade destina-se principalmente a clientes do A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo limite.

Se for necessário alterar o tempo limite da SDID padrão, adicione `sdidParamExpiry` à `Visitor.getInstance` função com a seguinte sintaxe:

**Sintaxe:** ` sdidParamExpiry: *`tempo em segundos`*`

**Amostra de código**

Quando configurado, o código do serviço de ID pode ser semelhante a este exemplo. Essa amostra define o tempo limite de SDID como 15 segundos.

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 
```
