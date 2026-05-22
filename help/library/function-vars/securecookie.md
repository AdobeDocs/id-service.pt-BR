---
description: Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.
keywords: Serviço de ID
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
TQID: https://experienceleague.adobe.com/UBhpXY4BvJiEDp6Adje--6ng-4W12RCWun2CpMFD3kU
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 93
ht-degree: 100%

---

# secureCookie{#securecookie}

Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.

Esse atributo de configuração está disponível na `visitorAPI`, versão 3.3.0.

>[!NOTE]
>
>A `SecureCookie` configuração não funcionará em domínios inseguros e pode fazer você não receber os valores MID para as visitas que usam um protocolo inseguro. A `secureCookie` configuração deve ser definida como `true` somente quando você tiver certeza de que todas as páginas e subdomínios estão usando um protocolo seguro todas as vezes.

**Sintaxe:** `secureCookie: true | false` (padrão)

**Amostra de código**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

