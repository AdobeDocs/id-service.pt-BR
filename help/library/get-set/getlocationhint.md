---
description: Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização) é um identificador numérico para a localização geográfica de um data center de serviço de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.
keywords: Serviço de ID
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
TQID: https://experienceleague.adobe.com/Q58a-bmHINs-3mhlUarH8Ipo85tNhjTjMDSlZLFcHsw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 195
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização) é um identificador numérico para a localização geográfica de um data center de serviço de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.

**Sintaxe:** `var *`nome da variável`* = visitor.getLocationHint()`

Para obter uma lista de IDs de região e locais correspondentes, consulte [IDs de região, locais e nomes de host do DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=pt-BR).

**Amostra de código**

A função de dica de localização lê a ID de região do cookie AMCV. Se a ID da região já estiver definida no cookie AMCV, o retorno de chamada ocorrerá imediatamente. Se a ID da região não estiver definida, a função aguardará uma resposta do servidor antes de passar a ID da região para o retorno de chamada. O código pode ser semelhante ao seguinte exemplo.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

