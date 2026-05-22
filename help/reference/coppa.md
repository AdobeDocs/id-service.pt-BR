---
description: A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao seu código do serviço de identidade da Experience Cloud de modo a evitar a definição de cookies no domínio de terceiros de um navegador.
keywords: Serviço de ID
title: Suporte para COPPA no serviço de identidade da Experience Cloud
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 86%

---

# Suporte para COPPA no serviço de identidade da Experience Cloud {#coppa-support-in-the-experience-cloud-id-service}

A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao seu código do serviço de identidade da Experience Cloud de modo a evitar a definição de cookies no domínio de terceiros de um navegador.

>[!NOTE]
>
>Para a versão 3.0.0 ou posterior.

**Cookies e rastreamento**

Quando uma página carrega, o serviço da [!DNL Experience Cloud] ID chama um servidor de coleta de dados (DCS) da [!DNL Adobe]. A resposta do DCS inclui um cookie da Experience Cloud e um cookie demdex.net.

* O cookie da Experience Cloud é definido no domínio próprio. Ele não pode ser usado para rastrear visitantes em domínios diferentes, a menos que esses domínios trabalhem juntos para permitir o acesso.
* O cookie demdex.net é definido no domínio de terceiros. Ele contém um identificador exclusivo que pode ser usado para rastrear visitantes em diferentes domínios.

**Cookies e conformidade com a COPPA**

Cookies de terceiros que rastreiam visitantes em diferentes domínios em sites direcionados para crianças (ou principalmente para elas) acionam as exigências de consentimento dos pais da COPPA. Para estar de acordo com a COPPA para as análises internas de sites, adicione a variável `disableThirdPartyCookies:true` à `Visitor.getInstance` função, conforme mostrado abaixo.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Quando definido como `true`, o `disableThirdPartyCookies` objeto impede o DCS de retornar o cookie demdex.net de terceiros. Se o visitante do site já apresentar esse cookie no navegador, o serviço de ID não o usará para criar uma nova [!DNL Experience Cloud] ID ou para retornar uma ID existente. Em vez disso, o serviço da [!DNL Experience Cloud] ID cria uma ID nova e aleatória no cookie primário. Após a ativação, é possível coletar dados com o serviço de ID e compartilhá-los em diferentes [!DNL Experience Cloud] soluções da, incluindo outras operações internas permitidas pela COPPA.

>[!MORELIKETHIS]
>
>* [Centro de privacidade da Adobe](http://www.adobe.com/br/privacy.html)
>* [O que é a COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

