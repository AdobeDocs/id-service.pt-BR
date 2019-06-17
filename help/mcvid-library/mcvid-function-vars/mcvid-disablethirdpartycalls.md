---
description: Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.
keywords: rastreamento entre domínios; Serviço de ID
seo-description: Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e 92 ce 1 f 5-67 a 4-476 c -9 d 04-41 d 4 e 96 b 1592
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.

**Sintaxe:**` `Disablethirdpartycalls: true | false «(padrão é `false`.)

Quando `disableThirdPartyCalls: true`, o serviço de ID não fará chamadas para outros domínios.

**Propósito**

Essa variável foi criada para clientes que precisam:

* Impedir que o serviço de ID faça chamadas de páginas seguras e autenticadas.
* Visitantes do site tenham uma Experience Cloud ID (MID).
* As outras soluções da Experience Cloud funcionam adequadamente.

**Estratégia de implementação**

Como as outras soluções da Experience Cloud dependem da MID, o serviço de ID chama a Adobe para retornar e definir essa ID. Se for necessário impedir que o serviço de ID faça chamadas às seções autenticadas do site, permita que faça as chamadas necessárias das páginas que não exigem autenticação primeiro. Depois que o visitante do site tiver uma MID, é possível definir `disableThirdPartyCalls= true` no código do serviço de ID nas seções autenticadas do site. É necessário considerar que a maioria, senão todos, os clientes navegarão até uma página de autenticação antes de acessarem as partes protegidas do site.

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
