---
description: Especifica se o modelo de publicação de destino deve usar Akamai para as conexões HTTPS.
keywords: Serviço de ID
seo-description: Especifica se o modelo de publicação de destino deve usar Akamai para as conexões HTTPS.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501 ccc 37-c 3 ab -4454-bfcf -3 e 3 c 3 e 8 b 5 ca 3
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

Especifica se o modelo de publicação de destino deve usar Akamai para as conexões HTTPS.

A configuração `idSyncSSLUseAkamai` é ativada com base no parceiro.

**Sintaxe: ** `idSyncSSLUseAkamai: true`

**Amostra de código**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

