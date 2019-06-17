---
description: Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar por uma resposta do serviço de ID.
keywords: Serviço de ID
seo-description: Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar por uma resposta do serviço de ID.
seo-title: loadTimeout
title: loadTimeout
uuid: f 627 e 044-bd 73-49 a 4-8 a 90-6 d 19 aa 566751
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# loadTimeout{#loadtimeout}

Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar por uma resposta do serviço de ID.

**Sintaxe:**` loadTimeout: *`intervalo em milissegundos`*`

O valor padrão é de 30.000 milissegundos (30 segundos). Recomendamos que você *não* altere o valor padrão.

>[!NOTE]
>
>As chamadas para o serviço de ID são assíncronas em relação a outros códigos não pertencentes à Adobe na página. Como resultado, o aumento ou a diminuição do intervalo de tempo limite não altera a taxa na qual a página processa o conteúdo. No entanto, longos intervalos de limite de tempo podem afetar o tempo de carregamento conforme a medição feita por ferramentas de monitoramento de rede comuns, mas o tempo de processamento não é afetado.

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

