---
description: getInstance retorna um objeto de ID de visitante para a ID de empresa da Experience Cloud especificada. Isso é necessário para inicializar o objeto de ID de visitante fornecido para o AppMeasurement por meio do s.visitor.
keywords: Serviço de ID
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '226'
ht-degree: 100%

---

# getInstance{#getinstance}

getInstance retorna um objeto de ID de visitante para a ID de empresa da Experience Cloud especificada. Isso é necessário para inicializar o objeto de ID de visitante fornecido para o AppMeasurement por meio do s.visitor.

**Sintaxe**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
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
>*Não* instancie a função Visitante com `var visitor = new Visitor`. Você deve usar a chamada de função adequada descrita aqui. Aplicável a biblioteca de códigos [!UICONTROL VisitorAPI.js] v3.0 ou posterior.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Se `getInstance` não encontrar uma instância existente, uma nova instância é criada e retornada. Isso é semelhante à [`s_gi()` função ](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=pt-BR) no [!DNL AppMeasurement].

**Uso comum**

A API do serviço da [!DNL Experience Cloud] ID mantém uma lista de todas as instâncias criadas para cada [!DNL Adobe Experience Cloud] ID de empresa da. Se o aplicativo com a API do serviço de ID não estiver passando uma referência para a instância, ele pode encontrar a instância chamando `getInstance` em vez de criar uma nova. Isso também oferece suporte a diversas instâncias e para diferentes empresas na mesma página da Web ou aplicativo.

Isso é útil para aplicativos que não possuem uma `init` fase definida, mas precisam verificar a API do serviço de ID em vários lugares. É possível chamar `getInstance` em todos esses lugares, e a primeira execução criará a instância. A instância existente será retornada por chamadas subsequentes.
