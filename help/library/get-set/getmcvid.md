---
description: getMarketingCloudVisitorID retorna a ID de visitante da Experience Cloud.
keywords: Serviço de ID
seo-description: getMarketingCloudVisitorID retorna a ID de visitante da Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93 e 16220-b 5 b 3-4 d 81-9189-30031 bc 15129
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID retorna a ID de visitante da Experience Cloud.

**Sintaxe:**` var *`nome da variável`* = visitor.getMarketingCloudVisitorID()`

Normalmente, esse método é usado com as soluções personalizadas que exigem a leitura da ID de visitante. Ele não é usado em uma implementação padrão. `getMarketingCloudVisitorID` também funciona com funções de retorno de chamada para ler as IDs do [!DNL Analytics] e trazê-las para o sistema ou aplicativo.

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
>Se você for [!DNL Analytics] um cliente, verifique e envie [!DNL Analytics] a ID para a sua função. Por exemplo, os dois identificadores são desejados ao passar a ID do visitante em um elemento de formulário oculto para um aplicativo que usa a API de inserção de dados. Nesse caso, você deve coletar e retornar as IDs [!DNL Experience Cloud] de [!DNL Analytics] visitante. Consulte [Obter ID de visitante do Analytics](../../library/get-set/getanalyticsvisitorid.md).

