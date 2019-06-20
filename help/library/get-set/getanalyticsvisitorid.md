---
description: Retorna a ID do Analytics herdada (se houver) que foi armazenada no cookie s_ vi antes da implementação do serviço da Experience Cloud ID. Ele retorna uma sequência vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.
keywords: Serviço de ID
seo-description: Retorna a ID do Analytics herdada (se houver) que foi armazenada no cookie s_ vi antes da implementação do serviço da Experience Cloud ID. Ele retorna uma sequência vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Retorna a ID do Analytics herdada (se houver) que foi armazenada no cookie s_ vi antes da implementação do serviço da Experience Cloud ID. Ele retorna uma sequência vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.

**Sintaxe** `var analyticsID = visitor.getAnalyticsVisitorID()`

Normalmente, essa função é usada com soluções personalizadas que exigem a leitura da ID do visitante. Ela não é usada em uma implementação padrão. `getAnalyticsVisitorID` também funciona com funções de retorno de chamada para ler as IDs do [!DNL Analytics] e trazê-las para o sistema ou aplicativo.

**Código de exemplo**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>If you&#39;re an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. Por exemplo, os dois identificadores são desejados ao passar a ID do visitante em um elemento de formulário oculto para um aplicativo que usa a API de inserção de dados. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**O parâmetro “aid” é um valor herdado**

O parâmetro `aid` aparece em uma sequência de consulta em dois conjuntos de condições diferentes.

**Caso 1**

O parâmetro `aid` é visto em uma sequência de consulta quando:

* The [!DNL Experience Cloud] ID service is deployed correctly.
* O usuário visita um site e tem uma ID do [!DNL Analytics] pré-existente armazenada no [cookie s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Caso 2**

You will see the `aid` parameter in a query string when your organization is using a [grace period](../../reference/analytics-reference/grace-period.md) before fully implementing the ID service. If the user visiting your site is new, and you&#39;re not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter.

>[!MORE_ LIKE_ THIS]
>
>* [Cookies do Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

