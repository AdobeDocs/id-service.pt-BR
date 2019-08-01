---
description: A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao código de serviço de identidade da Experience Cloud que impede a definição de cookies no domínio de terceiros de um navegador.
keywords: Serviço de ID
seo-description: A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao código de serviço de identidade da Experience Cloud que impede a definição de cookies no domínio de terceiros de um navegador.
seo-title: Suporte à lei COPPA no serviço de identidade da Experience Cloud
title: Suporte à lei COPPA no serviço de identidade da Experience Cloud
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2

---


# COPPA Support in the Experience Cloud Identity Service {#coppa-support-in-the-experience-cloud-id-service}

A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao código de serviço de identidade da Experience Cloud que impede a definição de cookies no domínio de terceiros de um navegador.

>[!NOTE]
>
>Para a versão 3.0.0 ou posterior.

**Cookies e rastreamento**

Quando uma página carrega, o serviço da [!DNL Experience Cloud] ID chama um servidor de coleta de dados (DCS) da [!DNL Adobe]. A resposta do DCS inclui um cookie da Experience Cloud e um cookie demdex.net.

* O cookie da Experience Cloud é definido no domínio primário. Ele não pode ser usado para rastrear visitantes em diferentes domínios, a menos que os domínios trabalhem em conjunto para permitir o acesso.
* O cookie demdex.net é definido no domínio de terceiros. Ele contém um identificador exclusivo que pode ser usado para rastrear visitantes em diferentes domínios.

**Cookies e conformidade com a COPPA**

Os cookies de terceiros que rastreiam visitantes por diferentes domínios em sites direcionados para crianças (ou principalmente para elas) acionam as exigências da COPPA de consentimento dos pais. Para estar de acordo com a COPPA para as análises internas de sites, adicione a variável `disableThirdPartyCookies:true` à `Visitor.getInstance` função, conforme mostrado abaixo.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Quando definido como `true`, o `disableThirdPartyCookies` objeto impede o DCS de retornar o cookie demdex.net de terceiros. Se o visitante já apresentar esse cookie no navegador, o serviço de ID não o usará para criar uma nova [!DNL Experience Cloud] ID ou para retornar uma ID existente. Em vez disso, o serviço da [!DNL Experience Cloud] ID cria uma ID nova e aleatória no cookie primário. Após a ativação, é possível coletar dados com o serviço de ID e compartilhá-los em diferentes [!DNL Experience Cloud] soluções da, incluindo outras operações internas permitidas pela COPPA.

>[!MORE_LIKE_THIS]
>
>* [Centro de privacidade da Adobe](http://www.adobe.com/privacy.html)
>* [O que é a COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

