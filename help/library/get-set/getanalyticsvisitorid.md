---
description: Retorna a Analytics ID herdada (se houver) que estava armazenada no cookie s_vi antes da implementação do Serviço de ID do visitante. Ele retorna uma string vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.
keywords: Serviço de ID de visitante
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
TQID: https://experienceleague.adobe.com/xJRR3qXoJpCnyFqKuEZqvEs0MpPCCA0brWOT6WbngX4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 46%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Retorna a Analytics ID herdada (se houver) que estava armazenada no cookie s_vi antes da implementação do Serviço de ID do visitante. Ele retorna uma string vazia se um visitante não possuir uma Analytics ID atribuída anteriormente.

**Sintaxe** `var analyticsID = visitor.getAnalyticsVisitorID()`

Normalmente, essa função é usada com soluções personalizadas que exigem a leitura da ID do visitante. Ela não é usada em uma implementação padrão. O `getAnalyticsVisitorID` também funciona com funções de retorno de chamada para ler as IDs do Analytics e trazê-las para o sistema ou aplicativo.

**Código de exemplo**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>Se você for um cliente do Analytics, verifique também e envie a Analytics ID para sua função. Por exemplo, os dois identificadores são desejados ao passar a ID do visitante em um elemento de formulário oculto para um aplicativo do lado do servidor que usa a API de inserção de dados. Nesse caso, você deve coletar e retornar as IDs de visitante da ECID e do Analytics. Consulte [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**O parâmetro “aid” é um valor herdado**

O `aid` parâmetro aparece em uma string de consulta em dois conjuntos de condições diferentes.

**Caso 1**

O parâmetro `aid` é visto em uma string de consulta quando:

* O Serviço de ID de visitante é implantado corretamente.
* O usuário visita um site e tem uma ID do Analytics pré-existente armazenada no [cookie s_vi](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=pt-BR#section-5d50a078de444d12b7d927d68ff3b679).

**Caso 2**

Você verá o parâmetro `aid` em uma sequência de consulta quando sua organização estiver usando um [período de carência](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/migration) antes de implementar totalmente o Serviço de ID de visitante. Se um novo usuário visitar seu site e você não usar um período de carência, ele receberá o parâmetro `mid` (ECID).

>[!MORELIKETHIS]
>
>* [Cookies do Analytics](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html?lang=pt-BR)

