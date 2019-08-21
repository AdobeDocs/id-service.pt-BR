---
description: Essa variável permite que você substitua o intervalo padrão do cookie AMCV.
keywords: Serviço de ID
seo-description: Essa variável permite que você substitua o intervalo padrão do cookie AMCV.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3f-69ac259377a3
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieLifetime{#cookielifetime}

Essa variável permite que você substitua o intervalo padrão do cookie AMCV.

Por padrão, os cookies do serviço da [!DNL Experience Cloud] ID expiram após 24 meses. Defina o intervalo em segundos.

**Sintaxe:**` cookieLifetime: *`duração em segundos`*`

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

