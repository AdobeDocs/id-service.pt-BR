---
description: Estas instruções são para clientes do Target que desejam usar o Serviço de ID de visitante e não usam tags de. No entanto, recomendamos que você use tags para implementar o Serviço de ID de visitante. As tags simplificam o fluxo de trabalho de implementação e automaticamente garante o posicionamento e sequenciamento corretos do código.
keywords: Serviço de ID de visitante
title: Implementar o serviço de ID de visitante da Adobe para Target
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 430
ht-degree: 47%

---

# Implementar o serviço de ID de visitante da Adobe para Target{#implement-the-experience-cloud-id-service-for-target}

Estas instruções são para clientes do Target que desejam usar o Serviço de ID de visitante e não usam [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=pt-BR). No entanto, recomendamos que você use tags para implementar o Serviço de ID de visitante. As tags simplificam o fluxo de trabalho de implementação e automaticamente garante o posicionamento e sequenciamento corretos do código.

>[!IMPORTANT]
>
>* [Leia as exigências](../reference/requirements.md) antes de começar.
>* Configure e teste esse código em um ambiente de desenvolvimento antes de implantá-lo na produção.

## Etapa 1: obter o código do Serviço de ID de visitante {#section-b32ba0548aa546a79dd38be59832a53e}

O Serviço de ID de Visitante exige a biblioteca de código `VisitorAPI.js`. Entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) para obter esse código.

## Etapa 2: adicionar a função Visitor.getInstance ao código do Serviço de ID de visitante {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: Copie a função Visitor.getInstance abaixo**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 
```

**Parte 2: Adicionar código de função ao arquivo `VisitorAPI.js`**

Insira a `Visitor.getInstance` função ao final do arquivo, após o bloqueio do código. O arquivo editado deve ficar parecido com o exemplo abaixo:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE");
```

## Etapa 3: adicionar a ID da organização IMS a Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Na função `Visitor.getInstance`, substitua `INSERT-IMS-ORG-ID-HERE` pela ID da organização IMS. Caso não saiba a ID da organização IMS, é possível encontrá-la na página de administração do CX Enterprise. Consulte também, [Administração - Serviços principais](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=pt-BR). A função editada pode ser parecida com o exemplo abaixo.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Não* altere as letras maiúsculas e minúsculas dos caracteres na ID da organização IMS. A ID diferencia maiúsculas e minúsculas e deve ser usada exatamente como foi fornecida.

## Etapa 4: adicionar o código da API de visitante à página {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implante o arquivo `VisitorAPI.js` para o site nas tags `<head>` antes da referência ao arquivo `mbox.js`. O Serviço de ID de visitante deve ser executado antes da geração da primeira chamada de rede do Target. Transfira esse código para a produção após os testes e a verificação.

## Etapa 5: testar e implantar o código do Serviço de ID de visitante {#section-e81ee439bb8a4c2abea43d76f3112e9c}

É possível testar e implantar da seguinte maneira.

**Testar e verificar**

Para testar a implementação do Serviço de ID de visitante:

* Verifique o cookie AMCV no domínio em que sua página está hospedada.
* Verifique se `mboxMCGVID` aparece em sua solicitação do Target e se contém a ECID.

Consulte [Cookies e o Serviço de ID de visitante](../introduction/cookies.md) para obter informações sobre o cookie AMCV e a MID.

**Implantar**

Implante o código depois que ele passar no teste.

