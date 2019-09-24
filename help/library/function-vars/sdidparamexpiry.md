---
description: Essa configuração permite que você substitua o intervalo de expiração da ID de dados suplementares (SDID) padrão ao passá-la de uma página para outra usando a função auxiliar appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de destino tem 30 segundos para obter a SDID do URL enviada pela página de referência. Se o código do serviço de ID na página de destino não conseguir recuperar a SDID em menos de 30, é necessário solicitar uma nova SDID. Essa funcionalidade serve principalmente para clientes A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo limite.
keywords: Serviço de ID
seo-description: Essa configuração permite que você substitua o intervalo de expiração da ID de dados suplementares (SDID) padrão ao passá-la de uma página para outra usando a função auxiliar appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de destino tem 30 segundos para obter a SDID do URL enviada pela página de referência. Se o código do serviço de ID na página de destino não conseguir recuperar a SDID em menos de 30, é necessário solicitar uma nova SDID. Essa funcionalidade serve principalmente para clientes A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo limite.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# sdidParamExpiry{#sdidparamexpiry}

Essa configuração permite que você substitua o intervalo de expiração da ID de dados suplementares (SDID) padrão ao passá-la de uma página para outra usando a função auxiliar appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de destino tem 30 segundos para obter a SDID do URL enviada pela página de referência. Se o código do serviço de ID na página de destino não conseguir recuperar a SDID em menos de 30, é necessário solicitar uma nova SDID. Essa funcionalidade serve principalmente para clientes A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo limite.

**Substituir o tempo limite da SDID**

Se for necessário alterar o tempo limite da SDID padrão, adicione `sdidParamExpiry` à `Visitor.getInstance` função com a seguinte sintaxe:

**Sintaxe:**` sdidParamExpiry: *`tempo em segundos`*`

**Amostra de código**

Quando configurado, o código do serviço de ID pode ser semelhante a este exemplo. Essa amostra define o tempo limite de SDID como 15 segundos. Essa configuração funciona com o método auxiliar  [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

