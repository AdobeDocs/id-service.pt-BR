---
description: Essa configuração permite substituir o intervalo de expiração padrão da ID de dados complementares (SDID) ao passar essa ID de uma página para outra usando a função de ajuda appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter o SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não puder recuperar o SDID em menos de 30 segundos, ele solicitará um novo SDID. Essa funcionalidade é principalmente para clientes A4T que precisam passar o SDID de uma página para outra e desejar controle sobre esse intervalo de tempo limite.
keywords: ID Service
seo-description: Essa configuração permite substituir o intervalo de expiração padrão da ID de dados complementares (SDID) ao passar essa ID de uma página para outra usando a função de ajuda appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter o SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não puder recuperar o SDID em menos de 30 segundos, ele solicitará um novo SDID. Essa funcionalidade é principalmente para clientes A4T que precisam passar o SDID de uma página para outra e desejar controle sobre esse intervalo de tempo limite.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 11%

---


# sdidParamExpiry{#sdidparamexpiry}

Essa configuração permite substituir o intervalo de expiração padrão da ID de dados complementares (SDID) ao passar essa ID de uma página para outra usando a função de ajuda appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter o SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não puder recuperar o SDID em menos de 30 segundos, ele solicitará um novo SDID. Essa funcionalidade é principalmente para clientes A4T que precisam passar o SDID de uma página para outra e desejar controle sobre esse intervalo de tempo limite.

**Substituir o tempo limite SDID**

Se for necessário alterar o tempo limite da SDID padrão, adicione `sdidParamExpiry` à `Visitor.getInstance` função com a seguinte sintaxe:

**Sintaxe:**` sdidParamExpiry: *`tempo em segundos`*`

**Amostra de código**

Quando configurado, seu código de serviço de ID pode ser semelhante a essa amostra. Essa amostra define o tempo limite de SDID como 15 segundos. Essa configuração funciona com o método auxiliar  [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

