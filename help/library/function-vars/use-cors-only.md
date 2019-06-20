---
description: Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço da Experience Cloud ID.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço da Experience Cloud ID.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607 dc 035-dffc -4 f 4 d-be 51-08 ef 6 c 0 a 8 fad
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# useCORSOnly{#usecorsonly}

Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço da Experience Cloud ID.

**Sintaxe:**`useCORSOnly: true|false` (padrão é `false`.)

**Visão geral**

Quando está definido como `false`, o navegador executa verificações de recursos com CORS ou JSONP. Entretanto, o serviço de ID sempre tenta solicitar recursos com CORS primeiro. Em seguida, reverte para JSONP em navegadores antigos sem suporte ao CORS. Se for necessário forçar o navegador para usar somente o CORS, defina `useCORSOnly:true` na chamada de função `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` se você tiver requisitos de segurança rígidos. Esse modo deve ser habilitado somente se você tiver certeza de que os visitantes usam navegadores com suporte para CORS. A experiência do usuário não é afetada por navegadores sem suporte para CORS. No entanto, os navegadores sem suporte para CORS não podem solicitar dados de recursos ou troca com a [!DNL Adobe Experience Cloud].

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

