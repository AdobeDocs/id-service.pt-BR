---
description: Um sinalizador booleano opcional que impede o serviço de identidade da Experience Cloud de retornar o cookie de terceiros demdex.net.
keywords: Serviço de ID
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 100%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Um sinalizador booleano opcional que impede o serviço de identidade da Experience Cloud de retornar o cookie de terceiros demdex.net.

>[!NOTE]
>
>Essa configuração era `idSyncDisable3rdPartySyncing` e foi renomeada para `disableThirdPartyCookies` na versão v3.0 de 18 de janeiro de 2018.

**Sintaxe:** `disableThirdPartyCookies: true|false` (o padrão é `false`.) Para `VisitorAPI.js` v3.0.0 ou superior.

Quando `disableThirdPartyCookies: true`, o serviço de ID não retorna o cookie demdex.net de terceiros (consulte [Cookies e o serviço de identidade da Experience Cloud](../../introduction/cookies.md)). Se o visitante do site já tiver esse cookie no navegador, o serviço de ID não o usará para criar uma nova Experience Cloud ID (MID) ou para retornar uma ID existente. Em vez disso, o serviço de ID cria uma MID nova e aleatória no cookie primário. Após a ativação, é possível coletar dados com o serviço de ID e compartilhá-los em diferentes soluções da Experience Cloud.

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
