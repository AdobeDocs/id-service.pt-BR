---
description: Necessário para domínios de alto nível e com muitas partes, em que qualquer uma das duas últimas partes do URL é maior do que dois caracteres.
keywords: Serviço de ID
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 100%

---

# cookieDomain{#cookiedomain}

Necessário para domínios de nível superior e com muitas partes, em que qualquer uma das duas últimas partes do URL é maior do que dois caracteres.

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
