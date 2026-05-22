---
description: Essa configuração permite substituir o intervalo de expiração padrão da ID de dados suplementares (SDID) ao passá-la de uma página para outra usando a função auxiliar appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter a SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não conseguir recuperar a SDID em menos de 30 segundos, ele solicitará uma nova SDID. Essa funcionalidade destina-se principalmente a clientes do A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo-limite.
keywords: Serviço de ID
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
TQID: https://experienceleague.adobe.com/PUHy-KpWKY0BQSMkKidwpLYES6FvME2EtKCbCpfMFrw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 260
ht-degree: 96%

---

# sdidParamExpiry{#sdidparamexpiry}

Essa configuração permite substituir o intervalo de expiração padrão da ID de dados suplementares (SDID) ao passá-la de uma página para outra usando a função auxiliar appendSupplementalDataIDTo. Por padrão, o código do serviço de ID na página de recebimento tem 30 segundos para obter a SDID do URL enviado pela página de referência. Se o código do serviço de ID na página de recebimento não conseguir recuperar a SDID em menos de 30 segundos, ele solicitará uma nova SDID. Essa funcionalidade destina-se principalmente a clientes do A4T que precisam passar a SDID de uma página para outra e desejam controlar esse intervalo de tempo-limite.

**Substituir o tempo-limite da SDID**

Se for necessário alterar o tempo-limite da SDID padrão, adicione `sdidParamExpiry` à `Visitor.getInstance` função com a seguinte sintaxe:

**Sintaxe:** `sdidParamExpiry: *`tempo em segundos`*`

**Amostra de código**

Quando configurado, o código do serviço de ID pode ser semelhante a este exemplo. Essa amostra define o tempo-limite de SDID como 15 segundos. Esta configuração funciona com o método auxiliar [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

