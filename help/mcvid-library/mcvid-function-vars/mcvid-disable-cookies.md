---
description: Um sinalizador booleano opcional que impede o serviço da Experience Cloud ID de retornar o cookie de terceiros demdex.net.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que impede o serviço da Experience Cloud ID de retornar o cookie de terceiros demdex.net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Um sinalizador booleano opcional que impede o serviço da Experience Cloud ID de retornar o cookie de terceiros demdex.net.

>[!NOTE]
>
>Esta configuração foi `idSyncDisable3rdPartySyncing` e renomeada `disableThirdPartyCookies` para a versão de January 8 de janeiro de 28 18 da versão v 3.0.

**Sintaxe:**`disableThirdPartyCookies: true|false` (padrão é `false`.) Para `VisitorAPI.js` v 1.5.3 ou superior.

Quando `disableThirdPartyCookies: true`, o serviço de ID não retorna o cookie demdex. net de terceiros (consulte [Cookies e o serviço](../../mcvid-introduction/mcvid-cookies.md) da Experience Cloud ID). Se o visitante já apresentar esse cookie no navegador, o serviço de ID não o usará para criar uma nova Experience Cloud ID (MID) ou para retornar uma ID existente. Em vez disso, o serviço da ID cria uma nova MID aleatória no seu cookie primário. Depois de habilitado, é possível coletar dados com o serviço de ID e compartilhá-los com soluções diferentes da Experience Cloud.

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

