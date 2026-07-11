---
description: getMarketingCloudVisitorID retorna a ECID.
keywords: Serviço de ID de visitante
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 52%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID retorna a ECID.

**Sintaxe:** `var *`nome da variável`* = visitor.getMarketingCloudVisitorID()`

Normalmente, esse método é usado com soluções personalizadas que exigem a leitura da ID de visitante. Ela não é usada em uma implementação padrão. O `getMarketingCloudVisitorID` também funciona com funções de retorno de chamada para ler as IDs do Analytics e trazê-las para o sistema ou aplicativo.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get the ECID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Se você for um cliente do Analytics, verifique também e envie a Analytics ID para sua função. Por exemplo, os dois identificadores são desejados ao passar a ID do visitante em um elemento de formulário oculto para um aplicativo do lado do servidor que usa a API de inserção de dados. Nesse caso, você deve coletar e retornar as IDs de visitante da ECID e do Analytics. Consulte [Obter uma ID de visitante do Analytics](../../library/get-set/getanalyticsvisitorid.md).

