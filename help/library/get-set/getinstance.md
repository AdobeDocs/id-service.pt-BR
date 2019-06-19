---
description: getInstance retorna um objeto da ID de visitante da ID da organização da Experience Cloud especificada. Isso é necessário para inicializar o objeto de ID de visitante fornecido para o AppMeasurement pelo s.visitor.
keywords: Serviço de ID
seo-description: getInstance retorna um objeto da ID de visitante da ID da organização da Experience Cloud especificada. Isso é necessário para inicializar o objeto de ID de visitante fornecido para o AppMeasurement pelo s.visitor.
seo-title: getInstance
title: getInstance
uuid: 259 b 88 a 6-e 3 d 0-4 aab-b 935-566099 bdab 98
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getInstance{#getinstance}

getInstance retorna um objeto da ID de visitante da ID da organização da Experience Cloud especificada. Isso é necessário para inicializar o objeto de ID de visitante fornecido para o AppMeasurement pelo s.visitor.

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
>*Não* instancie a função Visitante com `var visitor = new Visitor`. Você deve usar a chamada de função adequada descrita aqui. Aplicável à biblioteca de código v3.0 ou posterior de [!DNL VisitorAPI.js].

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

Se `getInstance` não encontrar uma instância existente, uma nova instância é criada e retornada. Isso é semelhante à [`s_gi()` função ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) em [!DNL AppMeasurement].

**Uso comum**

A API de serviço [!DNL Experience Cloud] de ID mantém uma lista de todas as instâncias criadas para cada [!DNL Adobe Experience Cloud] ID de empresa. Se o aplicativo com a API do serviço de ID não estiver passando uma referência para a instância, ele pode encontrar a instância chamando `getInstance` em vez de criar uma nova. Isso também oferece suporte a diversas instâncias e para diferentes empresas na mesma página da Web ou aplicativo.

Isso é útil para aplicativos que não possuem uma fase `init` definida, mas precisam verificar a API do serviço de ID em vários lugares. É possível chamar `getInstance` em todos esses lugares, e a primeira execução criará a instância. A instância existente será retornada por chamadas subsequentes.
