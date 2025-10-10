---
description: Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar uma resposta do serviço de ID.
keywords: Serviço de ID
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 69%

---

# loadTimeout{#loadtimeout}

Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar uma resposta do serviço de ID.

**Sintaxe:** `loadTimeout: *`intervalo em milissegundos`*`

O valor padrão é de 30.000 milissegundos (30 segundos). É altamente recomendável que você *não* altere o valor padrão.

>[!NOTE]
>
>As chamadas para o serviço de ID são assíncronas em relação ao código que não seja da Adobe na página. Como resultado, aumentar ou diminuir o intervalo de tempo limite não altera a taxa na qual a página renderiza o conteúdo. No entanto, longos intervalos de tempo limite podem afetar o tempo de carregamento da página, conforme medido pelas ferramentas de monitoramento de rede comuns, mas o tempo de renderização não é afetado.

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```
