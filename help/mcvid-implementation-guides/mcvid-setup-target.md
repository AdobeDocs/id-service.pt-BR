---
description: Essas instruções se destinam a clientes do Target que desejam usar o serviço da Experience Cloud ID e não usam o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.
keywords: Serviço de ID
seo-description: Essas instruções se destinam a clientes do Target que desejam usar o serviço da Experience Cloud ID e não usam o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.
seo-title: Implementar o serviço da Experience Cloud ID no Target
title: Implementar o serviço da Experience Cloud ID no Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Implementar o serviço da Experience Cloud ID no Target{#implement-the-experience-cloud-id-service-for-target}

Essas instruções se destinam a clientes do Target que desejam usar o serviço da Experience Cloud ID e não usam o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.

>[!IMPORTANT]
>
>* [Leia as exigências](../mcvid-reference/mcvid-requirements.md) antes de começar.
>* Configure e teste esse código em um ambiente de desenvolvimento antes de implantá-lo na produção.
>



## Etapa 1: Obter o código do serviço de ID {#section-b32ba0548aa546a79dd38be59832a53e}

O [!DNL ID Service] código exige a biblioteca `VisitorAPI.js` de códigos. Entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html) para receber o código.

## Etapa 2: Adicionar a função Visitor. getinstance ao código do serviço de ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: copiar a função Visitor.getInstance abaixo**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Parte 2: adicionar o código da função ao arquivo VisitorAPI.js**

Insira a função `Visitor.getInstance` ao final do arquivo, após o bloqueio do código. O arquivo editado deve ficar parecido com o exemplo abaixo:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Etapa 3: Adicionar a ID de empresa da Experience Cloud à Visitor. getinstance {#section-522b1877be9243c39b222859b821f0ce}

Na `Visitor.getInstance` função, substitua `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` pela ID [!DNL Experience Cloud] da empresa. Caso não saiba a ID da organização, é possível encontrá-la na página de administração da [!DNL Experience Cloud]. Consulte também [Administração - Principais serviços](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). A função editada pode ser parecida com o exemplo abaixo.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Não* altere o caso dos caracteres na ID da empresa. A ID diferencia maiúsculas e minúsculas e deve ser usada exatamente como foi fornecida.

## Etapa 4: Adicionar o código da API do visitante à página {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implante `VisitorAPI.js` o arquivo no site nas `<head>` tags antes da referência ao `mbox.js` arquivo. O serviço [!DNL Experience Cloud] de ID deve ser executado antes da geração da primeira [!DNL Target] chamada de rede. Transfira esse código para a produção após os testes e a verificação.

## Etapa 5: Testar e implantar o código do serviço de ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Você pode testar e implantar como segue.

**Teste e verifique**

Para testar a implementação do serviço de ID:

* Verifique o cookie AMCV no domínio em que sua página está hospedada.
* Verifique `mboxMCGVID` se ela aparece na [!DNL Target] solicitação e se ela contém [!DNL Experience Cloud] a ID (MID).

Consulte [Cookies e o serviço da Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md) para obter informações sobre o cookie AMCV e a MID.

**Implantação**

Implanta o código após o teste.
