---
description: Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar uma resposta do serviço de ID.
keywords: Serviço de ID
seo-description: Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar uma resposta do serviço de ID.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
exl-id: 485264f4-ee24-4042-8be3-259e70462110
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '169'
ht-degree: 100%

---

# loadTimeout {#loadtimeout}

Define um intervalo de tempo limite em milissegundos. Usado para informar outras soluções (por exemplo, Analytics, Audience Manager, Target etc.) por quanto tempo esperar uma resposta do serviço de ID.

**Sintaxe:** ` loadTimeout: *`intervalo em milissegundos`*`

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
