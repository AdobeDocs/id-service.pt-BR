---
description: Um sinalizador booleano opcional que desativa a sincronização de ID.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que desativa a sincronização de ID.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableIdSyncs{#disableidsyncs}

Um sinalizador booleano opcional que desativa a sincronização de ID.

>[!NOTE]
>
>Essa configuração era `idSyncDisableSyncs` e foi renomeada para `disableIdSyncs` na versão v3.0 de 18 de janeiro de 2018.

**Sintaxe:**`disableIdSyncs: true|false` (o padrão é `false`.)

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

