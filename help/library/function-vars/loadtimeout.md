---
description: Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Público alvo etc.) quanto tempo esperar por uma resposta do serviço de ID.
keywords: ID Service
seo-description: Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Público alvo etc.) quanto tempo esperar por uma resposta do serviço de ID.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 14%

---


# loadTimeout{#loadtimeout}

Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Público alvo etc.) quanto tempo esperar por uma resposta do serviço de ID.

**Sintaxe:**` loadTimeout: *`intervalo em milissegundos`*`

O valor padrão é 30.000 milissegundos (30 segundos). Recomendamos que você *não* altere o valor padrão.

>[!NOTE]
>
>As chamadas para o serviço de ID são assíncronas em relação ao código que não seja da Adobe na página. Como resultado, aumentar ou diminuir o intervalo de tempo limite não altera a taxa na qual a página renderiza o conteúdo. No entanto, longos intervalos de tempo limite podem afetar os tempos de carregamento da página, conforme medido pelas ferramentas comuns de monitoramento da rede, mas o tempo de renderização não é afetado.

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

