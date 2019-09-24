---
description: Necessário para domínios de alto nível e com muitas partes, em que qualquer uma das duas últimas partes do URL é maior do que dois caracteres.
keywords: Serviço de ID
seo-description: Necessário para domínios de alto nível e com muitas partes, em que qualquer uma das duas últimas partes do URL é maior do que dois caracteres.
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07b-4d54-8aea-8e8b152f1423
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieDomain{#cookiedomain}

Necessário para domínios de alto nível e com muitas partes, em que qualquer uma das duas últimas partes do URL é maior do que dois caracteres.

**Sintaxe:** ` cookieDomain: " *`URL`*"` (O `www` prefixo não é necessário.)

**Caso de uso**

* Obrigatório: `www.example.com.uk`
* Não obrigatório: `www.example.co.uk`

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```

