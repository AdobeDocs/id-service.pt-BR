---
description: Um sinalizador booleano opcional que impede o serviço de identidade da Experience Cloud de retornar o cookie de terceiros demdex.net.
keywords: ID Service
seo-description: Um sinalizador booleano opcional que impede o serviço de identidade da Experience Cloud de retornar o cookie de terceiros demdex.net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 60%

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Um sinalizador booleano opcional que impede o serviço de identidade da Experience Cloud de retornar o cookie de terceiros demdex.net.

>[!NOTE]
>
>Essa configuração era `idSyncDisable3rdPartySyncing` e foi renomeada para `disableThirdPartyCookies` na versão v3.0 de 18 de janeiro de 2018.

**Sintaxe:**`disableThirdPartyCookies: true|false` (o padrão é `false`.) Para `VisitorAPI.js` v3.0.0 ou superior.

Quando `disableThirdPartyCookies: true`, o serviço de ID não retorna o cookie demdex.net de terceiros (consulte [Cookies e o serviço de identidade da Experience Cloud](../../introduction/cookies.md)). Se um visitante do site já tiver esse cookie em seu navegador, o serviço de ID não o usará para criar uma nova Experience Cloud ID (MID) ou retornar uma ID existente. Em vez disso, o serviço de ID cria uma nova MID aleatória no cookie primário. Depois de ativados, você pode coletar dados com o serviço de ID e compartilhá-los em diferentes soluções de Experience Cloud.

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

