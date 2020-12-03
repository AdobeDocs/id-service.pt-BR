---
description: Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.
keywords: cross domain tracking;ID Service
seo-description: Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 44%

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.

**Sintaxe:** ` `disableThirdPartyCalls: true|false`` (o padrão é `false`.)

Quando `disableThirdPartyCalls: true`, o serviço de ID não fará chamadas para outros domínios.

**Propósito**

Essa variável foi projetada para clientes que precisam:

* Para impedir que o serviço de ID faça chamadas de suas páginas seguras e autenticadas.
* Visitantes do site para ter uma Experience Cloud ID (MID).
* Suas outras soluções Experience Cloud para funcionar corretamente.

**Estratégia de implementação**

Como outras soluções de Experience Cloud dependem da MID, o serviço de ID chama a Adobe para retornar e definir essa ID. Se você precisar impedir que o serviço de ID faça chamadas de seções autenticadas do seu site, deixe que ele faça essas chamadas necessárias de páginas que não exigem autenticação primeiro. Depois que o visitante do site tiver uma MID, é possível definir `disableThirdPartyCalls= true` no código do serviço de ID nas seções autenticadas do site. A suposição aqui é que a maioria, se não todos, de seus clientes navegarão até uma página de autenticação antes de terem acesso às partes seguras do site.

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

