---
description: Um sinalizador booleano opcional que controla como o Serviço de identidade da plataforma de experiência carrega o iframe de sincronização de ID.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que controla como o Serviço de identidade da plataforma de experiência carrega o iframe de sincronização de ID.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa 2 c 2 fa 4-2 cab -4 e 08-8 d 35-729 a 6 c 3 e 459 a
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Um sinalizador booleano opcional que controla como o Serviço de identidade da plataforma de experiência carrega o iframe de sincronização de ID.

**Sintaxe:**` `Idsyncattachiframeonwindowload = true | false «(padrão é `false`.)

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

