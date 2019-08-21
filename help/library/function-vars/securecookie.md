---
description: Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.
keywords: Serviço de ID
seo-description: Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

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

