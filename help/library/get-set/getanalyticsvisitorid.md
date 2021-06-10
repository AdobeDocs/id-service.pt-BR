---
description: Retorna a Analytics ID herdada (se houver) que estava armazenada no cookie s_vi antes da implementação do serviço de identidade da Experience Cloud. Ele retorna uma sequência vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.
keywords: Serviço de ID
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 91%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Retorna a Analytics ID herdada (se houver) que estava armazenada no cookie s_vi antes da implementação do serviço de identidade da Experience Cloud. Ele retorna uma sequência vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.

**Sintaxe** `var analyticsID = visitor.getAnalyticsVisitorID()`

Normalmente, essa função é usada com soluções personalizadas que exigem a leitura da ID do visitante. Ela não é usada em uma implementação padrão. `getAnalyticsVisitorID` também funciona com funções de retorno de chamada para ler as [!DNL Analytics] IDs do e trazê-las para o sistema ou aplicativo.

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
>Caso você seja um [!DNL Analytics] cliente do, verifique também e envie a [!DNL Analytics] ID do para sua função. Por exemplo, os dois identificadores são desejados ao passar a ID do visitante em um elemento de formulário oculto para um aplicativo do lado do servidor que usa a API de inserção de dados. Nesse caso, é necessário coletar e retornar as IDs do visitante da [!DNL Experience Cloud] e do [!DNL Analytics]. Consulte [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**O parâmetro “aid” é um valor herdado**

O `aid` parâmetro aparece em uma sequência de consulta em dois conjuntos de condições diferentes.

**Caso 1**

O parâmetro `aid` é visto em uma sequência de consulta quando:

* O serviço da [!DNL Experience Cloud] ID é implantado corretamente.
* O usuário visita um site e tem uma ID do [!DNL Analytics] pré-existente armazenada no [cookie s_vi](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679).

**Caso 2**

Você verá o `aid` parâmetro em uma sequência de consulta quando a empresa estiver usando um [período de carência](../../reference/analytics-reference/grace-period.md) antes de implementar totalmente o serviço de ID. Se um novo usuário visitar seu site e você não usar um período de carência, ele receberá o parâmetro `mid`([!DNL Experience Cloud] ID).

>[!MORELIKETHIS]
>
>* [Cookies do Analytics](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html)

