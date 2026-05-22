---
description: Um sinalizador booleano opcional que controla como o serviço de identidade da Experience Cloud carrega o iFrame de sincronização de ID.
keywords: Serviço de ID
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
TQID: https://experienceleague.adobe.com/fEqtHlUaNadgatKX-V-7FuZn-WTZOFg-YtBOD7yKg0k
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 77
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Um sinalizador booleano opcional que controla como o serviço de identidade da Experience Cloud carrega o iFrame de sincronização de ID.

**Sintaxe:** ` `idSyncAttachIframeOnWindowLoad= true false`` (o padrão é `false`.)

Quando `idSyncAttachIframeOnWindowLoad: true` o serviço de ID carrega o iFrame de sincronização de ID no carregamento da janela. Por padrão, o serviço de ID carrega o iFrame de sincronização de ID o mais rápido possível, em vez de carregar na janela.

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

