---
description: Retorna a ID da região do Serviço de identidade da Experience Platform. Uma ID de região (ou dica de localização), é um identificador numérico da localização geográfica de um data center de serviços de ID específico. Você precisar da ID da região para fazer chamadas de API do servidor para o Audience Manager.
keywords: Serviço de ID
seo-description: Retorna a ID da região do Serviço de identidade da Experience Platform. Uma ID de região (ou dica de localização), é um identificador numérico da localização geográfica de um data center de serviços de ID específico. Você precisar da ID da região para fazer chamadas de API do servidor para o Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc 312 b 7-d 270-4 a 5 c-a 2 bb -0 fbb 37 f 1 e 2 f 4
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getLocationHint{#getlocationhint}

Retorna a ID da região do Serviço de identidade da Experience Platform. Uma ID de região (ou dica de localização), é um identificador numérico da localização geográfica de um data center de serviços de ID específico. Você precisar da ID da região para fazer chamadas de API do servidor para o Audience Manager.

**Sintaxe:**` var *`nome da variável`* = visitor.getLocationHint()`

Para obter uma lista de IDs de região e os locais correspondentes, consulte [ID de região DCS, Locais e Nomes de host](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html).

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

