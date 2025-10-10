---
description: Essa variável permite que você substitua o intervalo padrão do cookie AMCV.
keywords: Serviço de ID
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# cookieLifetime{#cookielifetime}

Essa variável permite que você substitua o intervalo padrão do cookie AMCV.

Por padrão, os cookies do serviço da [!DNL Experience Cloud] ID expiram após 24 meses. Defina o intervalo em segundos.

**Sintaxe:** `cookieLifetime: *`duração em segundos`*`

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```
