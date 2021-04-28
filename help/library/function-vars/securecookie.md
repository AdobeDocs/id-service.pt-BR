---
description: Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.
keywords: Serviço de ID
seo-description: Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '105'
ht-degree: 100%

---

# secureCookie {#securecookie}

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
