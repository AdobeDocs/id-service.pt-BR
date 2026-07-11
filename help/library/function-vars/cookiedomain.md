---
description: Necessário para domínios de alto nível e com muitas partes, em que qualquer uma das duas últimas partes do URL é maior do que dois caracteres.
keywords: Serviço de ID de visitante
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
TQID: https://experienceleague.adobe.com/V-Aej2Eh52NBXQfeUTHQHEs6Q72mzpI5HptURu6FTUM
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 63
ht-degree: 100%

---

# cookieDomain{#cookiedomain}

Necessário para domínios de nível superior e com muitas partes, em que qualquer uma das duas últimas partes do URL é maior do que dois caracteres.

**Sintaxe:** `cookieDomain: "*`URL`*"` (O `www` prefixo não é necessário.)

**Caso de uso**

* Obrigatório: `www.example.com.uk`
* Não obrigatório: `www.example.co.uk`

**Amostra de código**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```

