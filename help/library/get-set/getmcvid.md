---
description: getMarketingCloudVisitorID retorna a ID de visitante da Experience Cloud.
keywords: Serviço de ID
seo-description: getMarketingCloudVisitorID retorna a ID de visitante da Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID retorna a ID de visitante da Experience Cloud.

**Sintaxe:**` var *`nome da variável`* = visitor.getMarketingCloudVisitorID()`

Normalmente, esse método é usado com as soluções personalizadas que exigem a leitura da ID de visitante. Ela não é usada em uma implementação padrão. `getMarketingCloudVisitorID` também funciona com funções de retorno de chamada para ler as [!DNL Analytics] IDs do e trazê-las para o sistema ou aplicativo.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingClouidID)
```

>[!TIP]
>
>Caso você seja um [!DNL Analytics] cliente do, verifique também e envie a [!DNL Analytics] ID do para sua função. Por exemplo, os dois identificadores são desejados ao passar a ID do visitante em um elemento de formulário oculto para um aplicativo do lado do servidor que usa a API de inserção de dados. Nesse caso, é necessário coletar e retornar as IDs do visitante da [!DNL Experience Cloud] e do [!DNL Analytics]. Consulte [Obter uma ID de visitante do Analytics](../../library/get-set/getanalyticsvisitorid.md).

