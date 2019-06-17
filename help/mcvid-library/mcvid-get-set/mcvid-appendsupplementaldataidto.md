---
description: Este método auxiliar anexa a ID de dados suplementares (SDID) como um parâmetro de sequência de caracteres de consulta a um URL de redirecionamento. Isso é útil ao usar A4T e é necessário manter a SDID de uma página para outra, além de unir essas visitas separadas. Para usar essa função, é necessário implementar o serviço de ID com a mesma ID da organização nos domínios de origem e destino.
keywords: Serviço de ID
seo-description: Este método auxiliar anexa a ID de dados suplementares (SDID) como um parâmetro de sequência de caracteres de consulta a um URL de redirecionamento. Isso é útil ao usar A4T e é necessário manter a SDID de uma página para outra, além de unir essas visitas separadas. Para usar essa função, é necessário implementar o serviço de ID com a mesma ID da organização nos domínios de origem e destino.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f 3504 d 82-8 da 3-4971-818 b -3 df 57 df 4 ec 2 d
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Este método auxiliar anexa a ID de dados suplementares (SDID) como um parâmetro de sequência de caracteres de consulta a um URL de redirecionamento. Isso é útil ao usar A4T e é necessário manter a SDID de uma página para outra, além de unir essas visitas separadas. Para usar essa função, é necessário implementar o serviço de ID com a mesma ID da organização nos domínios de origem e destino.

Conteúdo:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Sintaxe e amostra de código </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Saída de exemplo </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Sintaxe e amostra de código </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Alterar o tempo limite da SDID com sdidParamExpiry </a> </li> 
</ul>

## Sintaxe e amostra de código {#section-cbb0b2f73bcc418386796c24c01b2365}

**Sintaxe:**` appendSupplementalDataIDTo( *`URLSDID`*, *``*)`

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## Saída de exemplo {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Como mostrado abaixo, o redirecionamento do URL contém a SDID do visitante, a ID da organização e um carimbo de data e hora UNIX na chamada para a página de destino.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Alterar o tempo limite da SDID com sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

A configuração [sdidparamexpiry](../../mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) permite alterar o intervalo de expiração SDID padrão ao passar essa ID de uma página para outra usando a função `appendSupplementalDataIDTo` de ajuda. Por padrão, o código do serviço de ID na página de destino tem 30 segundos para obter a SDID do URL enviada pela página de referência. Se o código do serviço de ID na página de destino não conseguir recuperar a SDID em menos de 30, é necessário solicitar uma nova SDID. Essa funcionalidade serve principalmente para clientes A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo limite.

Se for necessário alterar o tempo limite da SDID padrão, adicione `sdidParamExpiry` à função `Visitor.getInstance` com a seguinte sintaxe:

**Sintaxe:**` sdidParamExpiry: *`tempo em segundos`*`

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
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```
