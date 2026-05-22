---
description: Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço de identidade da Experience Cloud.
keywords: Serviço de ID
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
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 87%

---

# useCORSOnly{#usecorsonly}

Um sinalizador booleano opcional que controla como o navegador solicita recursos do serviço de identidade da Experience Cloud.

**Sintaxe:** `useCORSOnly: true|false` (o padrão é `false`.)

**Visão geral**

Quando está definido como `false`, o navegador executa verificações de recursos com CORS ou JSONP. No entanto, o serviço de ID sempre tenta solicitar recursos com o CORS primeiro. Ele reverte para JSONP em navegadores antigos não compatíveis com o CORS. Se for necessário forçar o navegador para usar somente o CORS, defina `useCORSOnly:true` na chamada de função `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` se você tiver requisitos de segurança rigorosos. Você só deve ativar esse modo se estiver confiante de que todos os visitantes usam navegadores compatíveis com o CORS. A experiência do usuário não é afetada por navegadores incompatíveis com o CORS. No entanto, os navegadores sem suporte para CORS não podem solicitar dados de recursos ou troca com a [!DNL Adobe Experience Cloud].

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

