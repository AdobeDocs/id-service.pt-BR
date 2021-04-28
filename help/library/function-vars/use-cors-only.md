---
description: Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço de identidade da Experience Cloud.
keywords: Serviço de ID
seo-description: Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço de identidade da Experience Cloud.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '163'
ht-degree: 100%

---

# useCORSOnly {#usecorsonly}

Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço de identidade da Experience Cloud.

**Sintaxe:** `useCORSOnly: true|false` (o padrão é `false`.)

**Visão geral**

Quando está definido como `false`, o navegador executa verificações de recursos com CORS ou JSONP. No entanto, o serviço de ID sempre tenta solicitar recursos com o CORS primeiro. Ele reverte para JSONP em navegadores antigos não compatíveis com o CORS. Se for necessário forçar o navegador para usar somente o CORS, defina `useCORSOnly:true` na chamada de função `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` se você tiver requisitos de segurança rigorosos. Você só deverá ativar esse modo se estiver confiante de que todos os visitantes usam navegadores compatíveis com o CORS. A experiência do usuário não é afetada por navegadores incompatíveis com o CORS. No entanto, os navegadores sem suporte para CORS não podem solicitar dados de recursos ou troca com a [!DNL Adobe Experience Cloud].

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
