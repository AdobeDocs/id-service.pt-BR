---
description: Esse método auxiliar permite anexar a ID de dados complementares (SDID) como um parâmetro de string de query a um URL de redirecionamento. Isso é útil ao usar o A4T e você precisa persistir no SDID de uma página para outra e unir essas visitas separadas. Para usar essa função, você deve ter implementado o serviço de ID com a mesma ID da organização nos domínios de origem e de destino.
keywords: ID Service
seo-description: Esse método auxiliar permite anexar a ID de dados complementares (SDID) como um parâmetro de string de query a um URL de redirecionamento. Isso é útil ao usar o A4T e você precisa persistir no SDID de uma página para outra e unir essas visitas separadas. Para usar essa função, você deve ter implementado o serviço de ID com a mesma ID da organização nos domínios de origem e de destino.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 30%

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Esse método auxiliar permite anexar a ID de dados complementares (SDID) como um parâmetro de string de query a um URL de redirecionamento. Isso é útil ao usar o A4T e você precisa persistir no SDID de uma página para outra e unir essas visitas separadas. Para usar essa função, você deve ter implementado o serviço de ID com a mesma ID da organização nos domínios de origem e de destino.

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

A configuração de [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) permite que você substitua o intervalo de expiração da ID de dados suplementares (SDID) padrão ao passá-la de uma página para outra usando a função auxiliar `appendSupplementalDataIDTo`. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter o SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não puder recuperar o SDID em menos de 30 segundos, ele solicitará um novo SDID. Essa funcionalidade é principalmente para clientes A4T que precisam passar o SDID de uma página para outra e desejar controle sobre esse intervalo de tempo limite.

Se for necessário alterar o tempo limite da SDID padrão, adicione `sdidParamExpiry` à `Visitor.getInstance` função com a seguinte sintaxe:

**Sintaxe:**` sdidParamExpiry: *`tempo em segundos`*`

**Amostra de código**

Quando configurado, o código do serviço de ID pode ser semelhante a essa amostra. Essa amostra define o tempo limite de SDID como 15 segundos.

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

