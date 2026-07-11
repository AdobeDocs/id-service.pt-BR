---
description: getInstance retorna um objeto de ID de visitante para a ID da organização IMS especificada. Isso é necessário para inicializar o objeto de ID de visitante fornecido para o AppMeasurement por meio do s.visitor.
keywords: Serviço de ID de visitante
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 230
ht-degree: 55%

---

# getInstance{#getinstance}

getInstance retorna um objeto de ID de visitante para a ID da organização IMS especificada. Isso é necessário para inicializar o objeto de ID de visitante fornecido para o AppMeasurement por meio do s.visitor.

**Sintaxe**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*Não* instancie a função Visitante com `var visitor = new Visitor`. Você deve usar a chamada de função adequada descrita aqui. Aplicável à `VisitorAPI.js` biblioteca de código v3.0 ou posterior de.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Se `getInstance` não encontrar uma instância existente, uma nova instância é criada e retornada. Isso é semelhante à [`s_gi()` função](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=pt-BR) no AppMeasurement.

**Uso comum**

A API do Serviço de ID de visitante mantém uma lista de todas as instâncias criadas para cada ID de organização IMS. Se o aplicativo com a API do Serviço de ID de visitante não estiver passando uma referência para a instância, ele pode encontrar a instância chamando `getInstance` em vez de criar uma nova. Isso também oferece suporte a diversas instâncias e para diferentes empresas na mesma página da Web ou aplicativo.

Isso é útil para aplicativos que não têm uma fase `init` clara, mas precisam chamar a API do Serviço de ID do Visitante em vários lugares. É possível chamar `getInstance` em todos esses lugares, e a primeira execução criará a instância. A instância existente será retornada por chamadas subsequentes.

