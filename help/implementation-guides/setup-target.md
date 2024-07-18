---
description: Estas instruções são para clientes do Target que desejam usar o serviço de identidade da Experience Cloud e não uitilizam as tags da coleção de dados. No entanto, recomendamos fortemente o uso de tags ao implementar o serviço de ID. As tags simplificam o fluxo de trabalho de implementação e automaticamente garante o posicionamento e sequenciamento corretos do código.
keywords: Serviço de ID
title: Implementar o serviço de identidade da Experience Cloud para Target
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
source-git-commit: 792fb5d5192843f345577a99b6179fb6d95fedc0
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 100%

---

# Implementar o serviço de identidade da Experience Cloud para Target{#implement-the-experience-cloud-id-service-for-target}

Estas instruções são destinadas a clientes do Target que desejam usar o serviço de identidade da Experience Cloud e não utilizam as [tags da coleção de dados](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=pt-BR). No entanto, recomendamos fortemente o uso de tags ao implementar o serviço de ID. As tags simplificam o fluxo de trabalho de implementação e automaticamente garante o posicionamento e sequenciamento corretos do código.

>[!IMPORTANT]
>
>* [Leia as exigências](../reference/requirements.md) antes de começar.
>* Configure e teste esse código em um ambiente de desenvolvimento antes de implantá-lo na produção.

## Etapa 1: obter o código do serviço de ID {#section-b32ba0548aa546a79dd38be59832a53e}

O [!UICONTROL serviço de ID] exige a biblioteca de código `VisitorAPI.js`. Entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) para obter esse código.

## Etapa 2: adicionar a função Visitor.getInstance ao código do serviço de ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: Copie a função Visitor.getInstance abaixo**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Parte 2: Adicionar código de função ao arquivo VisitorAPI.js**

Insira a `Visitor.getInstance` função ao final do arquivo, após o bloqueio do código. O arquivo editado deve ficar parecido com o exemplo abaixo:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Etapa 3: adicionar a ID da organização da Experience Cloud ao Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Na `Visitor.getInstance` função, substitua `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` pela [!DNL Experience Cloud] ID da organização. Caso não saiba a ID da organização, é possível encontrá-la na página de [!DNL Experience Cloud] administração. Consulte também, [Administração - Serviços principais](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=pt-BR). A função editada pode ser parecida com o exemplo abaixo.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Não* altere a caixa dos caracteres na ID da organização. A ID diferencia maiúsculas e minúsculas e deve ser usada exatamente como foi fornecida.

## Etapa 4: adicionar o código da API de visitante à página {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implante o arquivo `VisitorAPI.js` para o site nas tags `<head>` antes da referência ao arquivo `mbox.js`. O serviço da [!DNL Experience Cloud] ID deve ser executado antes da geração da primeira chamada de rede do [!DNL Target]. Transfira esse código para a produção após os testes e a verificação.

## Etapa 5: testar e implantar o código do serviço de ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

É possível testar e implantar da seguinte maneira.

**Testar e verificar**

Para testar a implementação do serviço de ID:

* Verifique o cookie AMCV no domínio em que sua página está hospedada.
* Verifique se `mboxMCGVID` aparece em sua solicitação do [!DNL Target] e se contém a [!DNL Experience Cloud] ID (MID).

Consulte [Cookies e o serviço de identidade da Experience Cloud](../introduction/cookies.md) para obter informações sobre o cookie AMCV e a MID.

**Implantar**

Implante o código depois que ele passar no teste.
