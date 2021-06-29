---
description: Um sinalizador booleano opcional que controla como o serviço de identidade da Experience Cloud carrega o iFrame de sincronização de ID.
keywords: Serviço de ID
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '77'
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
