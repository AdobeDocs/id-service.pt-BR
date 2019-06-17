---
description: Retorna a Analytics ID herdada (se houver) que estava armazenada no cookie s_vi antes da implementação do serviço da Experience Cloud ID. Ele retorna uma sequência vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.
keywords: Serviço de ID
seo-description: Retorna a Analytics ID herdada (se houver) que estava armazenada no cookie s_vi antes da implementação do serviço da Experience Cloud ID. Ele retorna uma sequência vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Retorna a Analytics ID herdada (se houver) que estava armazenada no cookie s_vi antes da implementação do serviço da Experience Cloud ID. Ele retorna uma sequência vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.

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
>Se você for [!DNL Analytics] um cliente, verifique e envie [!DNL Analytics] a ID para a sua função. Por exemplo, os dois identificadores são desejados ao passar a ID do visitante em um elemento de formulário oculto para um aplicativo que usa a API de inserção de dados. Nesse caso, você deve coletar e retornar as IDs [!DNL Experience Cloud] de [!DNL Analytics] visitante. Consulte [getmarketingcloudvisitorid](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md).

**O parâmetro “aid” é um valor herdado**

O parâmetro `aid` aparece em uma sequência de consulta em dois conjuntos de condições diferentes.

**Caso 1**

O parâmetro `aid` é visto em uma sequência de consulta quando:

* O serviço [!DNL Experience Cloud] de ID é implantado corretamente.
* O usuário visita um site e tem uma ID do [!DNL Analytics] pré-existente armazenada no [cookie s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Caso 2**

Você verá o `aid` parâmetro em uma sequência de consulta quando sua organização estiver usando um [período de carência](../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) antes de implementar totalmente o serviço de ID. Se o usuário visitar seu site é novo e você não estiver usando um período de carência, o visitante obterá o `mid` parâmetro ( [!DNL Experience Cloud] ID).

>[!MORE_ LIKE_ THIS]
>
>* [Cookies do Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

