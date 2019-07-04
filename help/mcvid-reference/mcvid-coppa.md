---
description: A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao seu código do serviço da Experience Cloud ID de modo a evitar a definição de cookies no domínio de terceiros de um navegador.
keywords: Serviço de ID
seo-description: A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao seu código do serviço da Experience Cloud ID de modo a evitar a definição de cookies no domínio de terceiros de um navegador.
seo-title: Suporte para COPPA no serviço de Experience Cloud ID
title: Suporte para COPPA no serviço de Experience Cloud ID
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Suporte para COPPA no serviço de Experience Cloud ID {#coppa-support-in-the-experience-cloud-id-service}

A lei americana de privacidade infantil Children’s Online Privacy Protection Act (COPPA) proíbe a coleta de informações pessoais de crianças menores de 13 anos sem o consentimento dos pais. Os clientes com preocupações relacionadas à COPPA podem adicionar uma variável opcional ao seu código do serviço da Experience Cloud ID de modo a evitar a definição de cookies no domínio de terceiros de um navegador.

>[!NOTE]
>
>Para a versão 1.5.3 ou posterior.

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
>* [Adobe Privacy Center](http://www.adobe.com/br/privacy.html)
>* [O que é a COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

