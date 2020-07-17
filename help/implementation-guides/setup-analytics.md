---
description: Estas instruções são para clientes do Analytics que desejam usar o serviço de identidade da Experience Cloud e não usam o Dynamic Tag Management (DTM). No entanto, recomendamos que você use o DTM ao implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação e garante automaticamente a inserção e o sequenciamento corretos do código.
keywords: ID Service
seo-description: Estas instruções são para clientes do Analytics que desejam usar o serviço de identidade da Experience Cloud e não usam o Dynamic Tag Management (DTM). No entanto, recomendamos que você use o DTM ao implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação e garante automaticamente a inserção e o sequenciamento corretos do código.
seo-title: Implementar o serviço de identidade da Experience Cloud para Analytics
title: Implementar o serviço de identidade da Experience Cloud para Analytics
uuid: 7fbd6fa0-1713-4232-8680-500ed62709d5
translation-type: ht
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: ht
source-wordcount: '1087'
ht-degree: 100%

---


# Implementar o serviço de identidade da Experience Cloud para Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Estas instruções são para clientes do Analytics que desejam usar o serviço de identidade da Experience Cloud e não usam o Dynamic Tag Management (DTM). No entanto, recomendamos que você use o DTM ao implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação e garante automaticamente a inserção e o sequenciamento corretos do código.

>[!IMPORTANT]
>
>* [Leia as exigências](../reference/requirements.md) antes de começar.
>* Configure e teste esse código em um ambiente de desenvolvimento antes de implantá-lo na produção.


Siga estas etapas para implementar o serviço de ID do Adobe Analytics:

1. [Baixar o código do serviço de ID](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Adicionar a função Visitor.getInstance ao código do serviço de ID](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Adicionar a ID da organização da Experience Cloud ao Visitor.getInstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Adicionar os servidores de rastreamento ao Visitor.getInstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Atualizar o arquivo AppMeasurement.js ou s_code.js](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Adicionar o código da API do visitante à página](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Opcional) Configurar um período de carência](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Testar e implantar o código de serviço de ID](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Etapa 1: baixar o código do serviço de ID {#section-ead9403a6b7e45b887f9ac959ef89f7f}

O [!UICONTROL serviço de ID] exige a biblioteca de código `VisitorAPI.js`. Para baixar a biblioteca de código:

1. Acesse **[!UICONTROL Administração]** > **[!UICONTROL Gerenciamento de código]**.
1. Em [!UICONTROL Gerenciamento de código], clique em **[!UICONTROL JavaScript (Novo)]** ou **[!UICONTROL JavaScript (Herdado)]**.

   As bibliotecas de código comprimidas serão baixadas.

1. Descomprima o arquivo de código e abra o `VisitorAPI.js` arquivo.

## Etapa 2: Adicionar a função Visitor.getInstance ao código do serviço de ID {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* As versões anteriores da API de serviço de ID colocavam essa função em um local diferente e exigiam uma sintaxe distinta. Se você estiver migrando de uma versão anterior à [versão 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), observe a nova disposição e sintaxe documentadas aqui.
>* O código em ALL CAPS é um espaço reservado para valores reais. Substitua esse texto pela ID da organização, URL do servidor de rastreamento ou outro valor nomeado.


**Parte 1: Copie a função Visitor.getInstance abaixo**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
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

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Etapa 3: adicionar a ID da organização da Experience Cloud ao Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Na `Visitor.getInstance` função, substitua `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` pela [!DNL Experience Cloud] ID da organização. Caso não saiba a ID da organização, é possível encontrá-la na página de [!DNL Experience Cloud] administração. Consulte também, [Administração - Serviços principais](https://docs.adobe.com/content/help/pt-BR/core-services/interface/manage-users-and-products/admin-getting-started.html). A função editada pode ser parecida com o exemplo abaixo.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Não* altere a caixa dos caracteres na ID da organização. A ID diferencia maiúsculas e minúsculas e deve ser usada exatamente como foi fornecida.

## Etapa 4: adicionar os servidores de rastreamento ao Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

Rastreamento dos servidores usados para a coleta de dados do[!DNL Analytics].

**Parte 1: encontrar os URLs do servidor de rastreamento**

Verifique os arquivos `s_code.js` ou `AppMeasurement.js` para encontrar os URLs do servidor de rastreamento. Os URLs devem ser especificados pelas variáveis:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: Definir variáveis do servidor de rastreamento**

Para determinar quais variáveis do servidor de rastreamento usar:

1. Responda às perguntas na matriz de decisão abaixo. Use as variáveis que correspondem às suas respostas.
1. Substitua os espaços reservados do servidor de rastreamento pelos URLs do servidor de rastreamento.
1. Remova o servidor de rastreamento não usado e as variáveis do [!DNL Experience Cloud] servidor da do código.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Quando usados, associe os [!DNL Experience Cloud] URLs do servidor da aos URLs do servidor de rastreamento correspondentes, desta forma:
>
>* [!DNL Experience Cloud] URL do servidor da = URL do servidor de rastreamento
>* [!DNL Experience Cloud] URL seguro do servidor da = URL seguro do servidor de rastreamento


Caso não tenha certeza de como encontrar o servidor de rastreamento, consulte [Perguntas frequentes](../faq-intro/faq.md) e [Preencher corretamente as variáveis trackingServer e trackingServerSecure](https://helpx.adobe.com/br/analytics/kb/determining-data-center.html#).

## Etapa 5: atualizar o arquivo AppMeasurement.js ou s_code.js {#section-b53113aea1bd4de896e0e4e9a7edee19}

Adicione esta função ao arquivo `AppMeasurement.js` ou `s_code.js`:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Coloque o código na mesma seção que contém configurações como `linkInternalFilters`, `charSet`, `trackDownloads`, etc.

***(Opcional, mas recomendado)* Criar um prop personalizado.**

Defina um prop personalizado em `AppMeasurement.js` ou `s_code.js` para medir a cobertura. Adicione este prop personalizado à `doPlugins` função dos arquivos `AppMeasurement.js` ou `s_code.js`:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Etapa 6: adicionar o código da API do visitante à página {#section-d46d6aa324c842f2931d901e38d6db1d}

Insira o `VisitorAPI.js` arquivo nas tags `<head>` de cada página. Ao anexar o `VisitorAPI.js` arquivo à página:

* Coloque-o no início da `<head>` seção para que apareça antes de outras tags de solução.
* É necessário executar antes do AppMeasurement e do código de outras soluções da [!DNL Experience Cloud].

Transfira esse código para a produção após os testes e a verificação.

## Etapa 7: (opcional) configurar um período de carência {#section-7bbb2f72c26e4abeb8881e18366797a3}

Se algum desses casos de uso se aplicar à sua situação, peça ao [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) para configurar um [período de carência](../reference/analytics-reference/grace-period.md) temporário. Os períodos de carência podem durar até 180 dias. Você pode renovar um período de carência, se necessário.

**Implementação parcial**

Se você possuir páginas que usam o serviço de ID e outras que não o usam, é necessário ter um período de carência para que todas sejam relatadas no mesmo conjunto de [!DNL Analytics]relatórios do. Isso é comum se você tiver um conjunto de relatórios global que faz relatórios entre domínios.

Descontinue o período de carência depois que o serviço de ID é implantado em todas as páginas da Web que relatam no mesmo conjunto de relatórios.

**Requisitos de cookie s_vi**

É necessário um período de carência se você precisar que os novos visitantes tenham um cookie s_vi após migrar para o serviço de ID. Isso é comum se sua implementação ler o cookie s_vi e armazená-lo em uma variável.

A descontinuação do período de carência após a implementação pode capturar a MID em vez de ler o cookie s_vi.

Consulte [Cookies e o serviço de identidade da Experience Cloud](../introduction/cookies.md).

É necessário ter um período de carência caso envie dados para um sistema interno de um feed de dados de sequência de cliques que processe os usos das colunas `visid_high` e `visid_low`.

Faça a descontinuação do período de carência se o processo de ingestão de dados conseguir usar as colunas `post_visid_high` e `post_visid_low`.

Consulte [Referência da coluna de dados de sequência de cliques](https://docs.adobe.com/content/help/pt-BR/analytics/export/analytics-data-feed/data-feed-overview.html).

**Ingestão de dados da sequência de cliques**

## Etapa 8: testar e implantar o código do serviço de ID {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

É possível testar e implantar da seguinte maneira.

**Testar e verificar**

Para testar a implementação do serviço de ID, verifique:

* [Cookie AMCV](../introduction/cookies.md) no domínio em que a página está hospedada.
* O valor da MID na [!DNL Analytics]solicitação de imagem com a [ferramenta Adobe Debugger](https://docs.adobe.com/content/help/pt-BR/analytics/implementation/validate/debugger.html).

Consulte [Testar e verificar o serviço de identidade da Experience Cloud](../implementation-guides/test-verify.md).

**Implantar código**

Implante o código depois que ele passar no teste.

Se você ativou um período de carência na [Etapa 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Garanta que a [!DNL Analytics] ID do e a MID estejam presentes na solicitação de imagem.
* Lembre-se de desabilitar o período de carência após atender os critérios para a descontinuação.
