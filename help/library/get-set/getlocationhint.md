---
description: Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização) é um identificador numérico para a localização geográfica de um data center de serviço de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.
keywords: ID Service
seo-description: Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização) é um identificador numérico para a localização geográfica de um data center de serviço de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '230'
ht-degree: 100%

---


# getLocationHint {#getlocationhint}

Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização) é um identificador numérico para a localização geográfica de um data center de serviço de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.

**Sintaxe:**` var *`nome da variável`* = visitor.getLocationHint()`

Para obter uma lista de IDs de região e locais correspondentes, consulte [IDs de região, locais e nomes de host do DCS](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

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

