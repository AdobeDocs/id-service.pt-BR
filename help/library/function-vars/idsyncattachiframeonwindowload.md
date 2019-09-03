---
description: Um sinalizador booleano opcional que controla como o serviço de identidade da Experience Cloud carrega o iFrame de sincronização de ID.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que controla como o serviço de identidade da Experience Cloud carrega o iFrame de sincronização de ID.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Um sinalizador booleano opcional que controla como o serviço de identidade da Experience Cloud carrega o iFrame de sincronização de ID.

**Sintaxe:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (o padrão é `false`.)

Quando `idSyncAttachIframeOnWindowLoad: true` o serviço de ID carrega o iFrame de sincronização de ID no carregamento da janela. Por padrão, o serviço de ID carrega o iFrame de sincronização de ID o mais rápido possível em vez de carregar na janela.

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

