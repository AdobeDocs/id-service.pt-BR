---
description: Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização), é um identificador numérico da localização geográfica de um data center de serviços de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.
keywords: Serviço de ID
seo-description: Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização), é um identificador numérico da localização geográfica de um data center de serviços de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# getLocationHint{#getlocationhint}

Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização), é um identificador numérico da localização geográfica de um data center de serviços de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.

**Sintaxe:**` var *`nome da variável`* = visitor.getLocationHint()`

Para obter uma lista de IDs de região e locais correspondentes, consulte [IDs de região, locais e nomes de host do DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html).

**Amostra de código**

A função de dica da localização lê a ID da região a partir do cookie AMCV. Se a ID da região já estiver definida no cookie AMCV, o retorno de chamada ocorre imediatamente. Se a ID de região não estiver definida, a função aguarda a resposta do servidor antes de passar a ID da região para o retorno de chamada. O código pode ser semelhante ao seguinte exemplo.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

