---
description: Essa configuração permite substituir o intervalo de expiração padrão da ID de dados suplementares (SDID) ao passá-la de uma página para outra usando a função auxiliar appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter a SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não conseguir recuperar a SDID em menos de 30 segundos, ele solicitará uma nova SDID. Essa funcionalidade destina-se principalmente a clientes do A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo limite.
keywords: Serviço de ID
seo-description: Essa configuração permite substituir o intervalo de expiração padrão da ID de dados suplementares (SDID) ao passá-la de uma página para outra usando a função auxiliar appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter a SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não conseguir recuperar a SDID em menos de 30 segundos, ele solicitará uma nova SDID. Essa funcionalidade destina-se principalmente a clientes do A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo limite.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '357'
ht-degree: 100%

---

# sdidParamExpiry {#sdidparamexpiry}

Essa configuração permite substituir o intervalo de expiração padrão da ID de dados suplementares (SDID) ao passá-la de uma página para outra usando a função auxiliar appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter a SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não conseguir recuperar a SDID em menos de 30 segundos, ele solicitará uma nova SDID. Essa funcionalidade destina-se principalmente a clientes do A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo limite.

**Substituir o tempo limite da SDID**

Se for necessário alterar o tempo limite da SDID padrão, adicione `sdidParamExpiry` à `Visitor.getInstance` função com a seguinte sintaxe:

**Sintaxe:** ` sdidParamExpiry: *`tempo em segundos`*`

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
