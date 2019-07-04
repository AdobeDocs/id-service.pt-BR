---
description: Essas instruções se destinam a clientes do Target que desejam usar o serviço da Experience Cloud ID e não usam o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.
keywords: Serviço de ID
seo-description: Essas instruções se destinam a clientes do Target que desejam usar o serviço da Experience Cloud ID e não usam o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.
seo-title: Implementar o serviço da Experience Cloud ID no Target
title: Implementar o serviço da Experience Cloud ID no Target
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Implementar o serviço da Experience Cloud ID no Target{#implement-the-experience-cloud-id-service-for-target}

Essas instruções se destinam a clientes do Target que desejam usar o serviço da Experience Cloud ID e não usam o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.

>[!IMPORTANT]
>
>* [Leia as exigências](../mcvid-reference/mcvid-requirements.md) antes de começar.
>* Configure e teste esse código em um ambiente de desenvolvimento antes de implantá-lo na produção.
>



## Etapa 1: obter o código do serviço de ID {#section-b32ba0548aa546a79dd38be59832a53e}

O [!DNL ID Service] exige a `VisitorAPI.js` biblioteca de códigos. Entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) para obter este código.

## Etapa 2: adicionar a função Visitor.getInstance ao código do serviço de ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: copiar a função Visitor.getInstance abaixo**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Parte 2: adicionar o código da função ao arquivo VisitorAPI.js**

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

Na `Visitor.getInstance` função, substitua `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` pela [!DNL Experience Cloud] ID da organização. Caso não saiba a ID da organização, é possível encontrá-la na página de [!DNL Experience Cloud]administração da. Consulte também [Administração - Serviços principais](https://marketing.adobe.com/resources/help/pt_BR/mcloud/admin_getting_started.html). A função editada pode ser parecida com o exemplo abaixo.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Não* altere a caixa dos caracteres na ID da organização. A ID diferencia maiúsculas e minúsculas e deve ser usada exatamente como foi fornecida.

## Etapa 4: adicionar o código da API do visitante à página {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implante o arquivo `VisitorAPI.js` para o site nas tags `<head>` antes da referência ao arquivo `mbox.js`. O serviço da [!DNL Experience Cloud] ID deve ser executado antes da geração da primeira chamada de rede do [!DNL Target]. Transfira esse código para a produção após os testes e a verificação.

## Etapa 5: testar e implantar o código do serviço de ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

É possível testar e implantar da seguinte maneira.

**Testar e verificar**

Para testar a implementação do serviço de ID:

* Verifique o cookie AMCV no domínio em que sua página está hospedada.
* Verifique se `mboxMCGVID` aparece em sua solicitação do [!DNL Target] e se contém a [!DNL Experience Cloud] ID (MID).

Consulte [Cookies e o serviço da Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md) para obter informações sobre o cookie AMCV e a MID.

**Implantação**

Implanta o código após o teste.
