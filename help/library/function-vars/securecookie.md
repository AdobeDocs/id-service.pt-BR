---
description: Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.
keywords: Serviço de ID
seo-description: Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995 d 19 f 6-9 c 9 d -4493-9 c 9 c -545 b 0 b 5696 b 0
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# secureCookie{#securecookie}

Um sinalizador Booleano opcional que adiciona um atributo “Seguro” ao cookie AMCV.

Esse atributo de configuração está disponível na `visitorAPI`, versão 3.3.0.

>[!NOTE]
>
>A `SecureCookie` configuração não funcionará em domínios não seguros e poderá resultar no recebimento dos valores MID para visitas que usam um protocolo não seguro. A configuração `secureCookie` deve ser definida como `true` somente quando você tiver certeza de que todas as páginas e subdomínios estão usando um protocolo seguro todas as vezes.

**Sintaxe:**`secureCookie: true | false` (padrão)

**Amostra de código**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

