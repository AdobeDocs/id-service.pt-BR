---
description: Um sinalizador booleano opcional que impede o Serviço de identidade da Experience Platform de retornar o cookie demdex. net de terceiros.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que impede o Serviço de identidade da Experience Platform de retornar o cookie demdex. net de terceiros.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Um sinalizador booleano opcional que impede o Serviço de identidade da Experience Platform de retornar o cookie demdex. net de terceiros.

>[!NOTE]
>
>Essa configuração era `idSyncDisable3rdPartySyncing` e foi renomeada para `disableThirdPartyCookies` na versão v3.0 de 18 de janeiro de 2018.

**Sintaxe:**`disableThirdPartyCookies: true|false` (o padrão é `false`.) Para `VisitorAPI.js` v1.5.3 ou superior.

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Platform Identity Service](../../introduction/cookies.md) ). Se o visitante já apresentar esse cookie no navegador, o serviço de ID não o usará para criar uma nova Experience Cloud ID (MID) ou para retornar uma ID existente. Em vez disso, o serviço da ID cria uma nova MID aleatória no seu cookie primário. Depois de habilitado, é possível coletar dados com o serviço de ID e compartilhá-los com soluções diferentes da Experience Cloud.

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

