---
description: Um sinalizador booleano opcional que impede o Serviço de identidade da Experience Platform de retornar o cookie demdex. net de terceiros.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que impede o Serviço de identidade da Experience Platform de retornar o cookie demdex. net de terceiros.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Um sinalizador booleano opcional que impede o Serviço de identidade da Experience Platform de retornar o cookie demdex. net de terceiros.

>[!NOTE]
>
>Esta configuração foi `idSyncDisable3rdPartySyncing` e renomeada `disableThirdPartyCookies` para a versão de January 8 de janeiro de 28 18 da versão v 3.0.

**Sintaxe:**`disableThirdPartyCookies: true|false` (padrão é `false`.) Para `VisitorAPI.js` v 1.5.3 ou superior.

Quando `disableThirdPartyCookies: true`, o serviço de ID não retorna o cookie demdex. net de terceiros (consulte [Cookies e o Serviço](../../introduction/cookies.md) de identidade da plataforma Experience Platform). Se o visitante já apresentar esse cookie no navegador, o serviço de ID não o usará para criar uma nova Experience Cloud ID (MID) ou para retornar uma ID existente. Em vez disso, o serviço da ID cria uma nova MID aleatória no seu cookie primário. Depois de habilitado, é possível coletar dados com o serviço de ID e compartilhá-los com soluções diferentes da Experience Cloud.

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

