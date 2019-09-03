---
description: Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço de identidade da Experience Cloud.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço de identidade da Experience Cloud.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# useCORSOnly{#usecorsonly}

Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço de identidade da Experience Cloud.

**Sintaxe:**`useCORSOnly: true|false` (o padrão é `false`.)

**Visão geral**

Quando está definido como `false`, o navegador executa verificações de recursos com CORS ou JSONP. Entretanto, o serviço de ID sempre tenta solicitar recursos com CORS primeiro. Em seguida, reverte para JSONP em navegadores antigos sem suporte ao CORS. Se for necessário forçar o navegador para usar somente o CORS, defina `useCORSOnly:true` na chamada de função `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` se você tiver requisitos de segurança rigorosos. Esse modo deve ser habilitado somente se você tiver certeza de que os visitantes usam navegadores com suporte para CORS. A experiência do usuário não é afetada por navegadores sem suporte para CORS. No entanto, os navegadores sem suporte para CORS não podem solicitar dados de recursos ou troca com a [!DNL Adobe Experience Cloud].

**Amostra de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

