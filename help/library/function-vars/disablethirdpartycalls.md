---
description: Um sinalizador booleano opcional que impede o serviço de ID de efetuar chamadas para outros domínios.
keywords: rastreamento entre domínios, serviço de ID
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 200
ht-degree: 100%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

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

