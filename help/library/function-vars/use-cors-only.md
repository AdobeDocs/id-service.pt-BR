---
description: Um sinalizador booleano opcional que controla como o navegador solicita recursos do Serviço de ID do visitante.
keywords: Serviço de ID de visitante
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
TQID: https://experienceleague.adobe.com/QMYUbL2y8X5gSUcLmYnKZnp5mfEu7-uiogOx3rx2dkY
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 46%

---

# useCORSOnly{#usecorsonly}

Um sinalizador booleano opcional que controla como o navegador solicita recursos do Serviço de ID do visitante.

**Sintaxe:** `useCORSOnly: true|false` (o padrão é `false`.)

**Visão geral**

Quando está definido como `false`, o navegador executa verificações de recursos com CORS ou JSONP. No entanto, o Serviço de ID de visitante sempre tenta solicitar recursos com o CORS primeiro. Ele reverte para JSONP em navegadores antigos não compatíveis com o CORS. Se for necessário forçar o navegador para usar somente o CORS, defina `useCORSOnly:true` na chamada de função `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` se você tiver requisitos de segurança rigorosos. Você só deve ativar esse modo se estiver confiante de que todos os visitantes usam navegadores compatíveis com o CORS. A experiência do usuário não é afetada por navegadores incompatíveis com o CORS. No entanto, os navegadores sem suporte para CORS não podem solicitar dados de recursos ou troca com o Adobe CX Enterprise.

**Amostra de código**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

