---
description: Um sinalizador booleano opcional que desativa a sincronização de ID.
keywords: ID Service
seo-description: Um sinalizador booleano opcional que desativa a sincronização de ID.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 100%

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

