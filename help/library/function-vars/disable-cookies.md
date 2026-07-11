---
description: Um sinalizador booleano opcional que impede o Serviço de ID de visitante de retornar o cookie de terceiros demdex.net.
keywords: Serviço de ID de visitante
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 16%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Um sinalizador booleano opcional que impede o Serviço de ID de visitante de retornar o cookie de terceiros demdex.net.

>[!NOTE]
>
>Essa configuração era `idSyncDisable3rdPartySyncing` e foi renomeada para `disableThirdPartyCookies` na versão v3.0 de 18 de janeiro de 2018.

**Sintaxe:** `disableThirdPartyCookies: true|false` (o padrão é `false`.) Para `VisitorAPI.js` v3.0.0 ou posterior.

Quando `disableThirdPartyCookies: true`, o Serviço de ID do Visitante não retorna o cookie demdex.net de terceiros (consulte [Cookies e o Serviço de ID do Visitante](../../introduction/cookies.md) ). Se o visitante já apresentar esse cookie no navegador, o Serviço de ID do visitante não o usará para criar uma nova ECID ou para retornar uma ID existente. Em vez disso, o Serviço de ID do visitante cria uma MID nova e aleatória no cookie primário. Após a ativação, é possível coletar dados com o Serviço de ID do visitante e compartilhá-los em diferentes soluções da CX Enterprise.

**Amostra de código**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

