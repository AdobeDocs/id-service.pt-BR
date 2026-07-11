---
description: Define um intervalo de tempo-limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar uma resposta do Serviço de ID do visitante.
keywords: Serviço de ID de visitante
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
TQID: https://experienceleague.adobe.com/w0-c0ROMsYRLqlHQuBfSAdardHnMfaJ8oTLf1xwL9QQ
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 56%

---

# loadTimeout{#loadtimeout}

Define um intervalo de tempo-limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar uma resposta do Serviço de ID do visitante.

**Sintaxe:** `loadTimeout: *`intervalo em milissegundos`*`

O valor padrão é de 30.000 milissegundos (30 segundos). É altamente recomendável que você *não* altere o valor padrão.

>[!NOTE]
>
>As chamadas ao Serviço de ID do visitante são assíncronas em relação ao código que não é da Adobe na página. Como resultado, aumentar ou diminuir o intervalo de tempo-limite não altera a taxa na qual a página renderiza o conteúdo. No entanto, longos intervalos de tempo-limite podem afetar o tempo de carregamento da página, conforme medido pelas ferramentas de monitoramento de rede comuns, mas o tempo de renderização não é afetado.

**Amostra de código**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```

