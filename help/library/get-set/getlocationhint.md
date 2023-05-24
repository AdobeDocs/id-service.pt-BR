---
description: Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização) é um identificador numérico para a localização geográfica de um data center de serviço de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.
keywords: Serviço de ID
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Retorna a ID de região do serviço de identidade da Experience Cloud. Uma ID de região (ou dica de localização) é um identificador numérico para a localização geográfica de um data center de serviço de ID específico. Você precisar da ID da região para fazer chamadas de API do lado do servidor para o Audience Manager.

**Sintaxe:** ` var *`nome da variável`* = visitor.getLocationHint()`

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
