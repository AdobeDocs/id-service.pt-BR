---
description: Um sinalizador booleano opcional que desativa a sincronização de ID.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que desativa a sincronização de ID.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8 bea 1 de 8-53 c 8-4 a 15-bcf 5-f 0869763 a 32 e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableIdSyncs{#disableidsyncs}

Um sinalizador booleano opcional que desativa a sincronização de ID.

>[!NOTE]
>
>Esta configuração foi `idSyncDisableSyncs` e renomeada `disableIdSyncs` para a versão de January 8 de janeiro de 28 18 da versão v 3.0.

**Sintaxe:**`disableIdSyncs: true|false` (padrão é `false`.)

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

