---
description: Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.
keywords: rastreamento entre domínios, serviço de ID
seo-description: Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '216'
ht-degree: 100%

---

# disableThirdPartyCalls {#disablethirdpartycalls}

Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.

**Sintaxe:** ` `disableThirdPartyCalls: true false`` (o padrão é `false`.)

Quando `disableThirdPartyCalls: true`, o serviço de ID não fará chamadas para outros domínios.

**Propósito**

Essa variável foi projetada para clientes que precisam:

* Para impedir que o serviço de ID faça chamadas de suas páginas seguras e autenticadas.
* Visitantes do site com uma Experience Cloud ID (MID).
* Suas outras soluções da Experience Cloud funcionam adequadamente.

**Estratégia de implementação**

Como as outras soluções da Experience Cloud dependem da MID, o serviço de ID chama a Adobe para retornar e definir essa ID. Se você precisar impedir que o serviço de ID faça chamadas das seções autenticadas do seu site, permita que ele faça as chamadas necessárias das páginas que não exigem autenticação primeiro. Depois que o visitante do site tiver uma MID, é possível definir `disableThirdPartyCalls= true` no código do serviço de ID nas seções autenticadas do site. A premissa é que a maioria dos clientes (se não todos) navegará para uma página de autenticação antes de ter acesso às partes seguras do site.

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
