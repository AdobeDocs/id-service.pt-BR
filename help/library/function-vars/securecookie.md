---
description: Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.
keywords: Serviço de ID
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '93'
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
