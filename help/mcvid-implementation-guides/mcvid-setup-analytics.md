---
description: Essas instruções servem para os clientes do Analytics que desejam usar o serviço da Experience Cloud ID e não usar o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.
keywords: Serviço de ID
seo-description: Essas instruções servem para os clientes do Analytics que desejam usar o serviço da Experience Cloud ID e não usar o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.
seo-title: Implementar o serviço da Experience Cloud ID para Analytics
title: Implementar o serviço da Experience Cloud ID para Analytics
uuid: 7 fbd 6 fa 0-1713-4232-868ed -500 ed 62709 d 5
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Implementar o serviço da Experience Cloud ID no Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Essas instruções servem para os clientes do Analytics que desejam usar o serviço da Experience Cloud ID e não usar o Dynamic Tag Management (DTM). Entretanto, recomendamos que você use o DTM para implementar o serviço de ID. O DTM simplifica o fluxo de trabalho de implementação, além de garantir automaticamente a inserção e o sequenciamento correto do código.

>[!IMPORTANT]
>
>* [Leia as exigências](../mcvid-reference/mcvid-requirements.md) antes de começar.
>* Configure e teste esse código em um ambiente de desenvolvimento antes de implantá-lo na produção.
>



Siga estas etapas para implementar o serviço de ID para o Adobe Analytics:

1. [Baixar o código do serviço de ID](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Adicionar a função Visitor. getinstance ao código de serviço de ID](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Adicionar a ID de empresa da Experience Cloud à Visitor. getinstance](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Adicionar seus servidores de rastreamento a Visitor. getinstance](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Atualizar o arquivo appmeasurement. js ou s_ code. js](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Adicionar o código da API do visitante à página](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Opcional) Configurar um período de carência](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Testar e implantar o código do serviço de ID](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Etapa 1: Baixar o código do serviço de ID {#section-ead9403a6b7e45b887f9ac959ef89f7f}

O [!DNL ID Service] código exige a biblioteca `VisitorAPI.js` de códigos. Para baixar a biblioteca de código:

1. Vá até **[!UICONTROL Administrador]** &gt; **[!UICONTROL Gerenciador de código]**.
1. Em [!DNL Code Manager], clique **[!UICONTROL em javascript (Novo)]** ou **[!UICONTROL javascript (Herdado)]**.

   As bibliotecas de código comprimidas serão baixadas.

1. Descomprima o arquivo de código e abra o arquivo `VisitorAPI.js`.

## Etapa 2: Adicionar a função Visitor. getinstance ao código de serviço de ID {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* as versões anteriores da API do serviço de ID colocavam essa função em um local diferente e exigiam uma sintaxe diferente. Caso esteja migrando de uma versão anterior para a [versão 1.4](../mcvid-release-notes/mcvid-notes-2015.md#section-f5c596f355b14da28f45c798df513572), observe a nova disposição e sintaxe documentadas aqui.
>* O código em MAIÚSCULA é um espaço reservado para valores. Substitua o texto pela ID da organização, pelo URL do servidor de rastreamento ou outro valor nomeado.
>



**Parte 1: copiar a função Visitor.getInstance abaixo**

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

**Parte 2: adicionar o código da função ao arquivo VisitorAPI.js**

Insira a função `Visitor.getInstance` ao final do arquivo, após o bloqueio do código. O arquivo editado deve ficar parecido com o exemplo abaixo:

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

## Etapa 3: Adicionar a ID de empresa da Experience Cloud à Visitor. getinstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Na `Visitor.getInstance` função, substitua `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` pela ID [!DNL Experience Cloud] da empresa. Caso não saiba a ID da organização, é possível encontrá-la na página de administração da [!DNL Experience Cloud]. Consulte também [Administração - Principais serviços](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). A função editada pode ser parecida com o exemplo abaixo.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Não* altere o caso dos caracteres na ID da empresa. A ID diferencia maiúsculas e minúsculas e deve ser usada exatamente como foi fornecida.

## Etapa 4: Adicionar seus servidores de rastreamento a Visitor. getinstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

Rastreamento dos servidores usados para a coleta de dados do [!DNL Analytics].

**Parte 1: encontrar os URLs do servidor de rastreamento**

Verifique os `s_code.js` urls do servidor `AppMeasurement.js` de rastreamento para encontrar os urls do servidor de rastreamento. Os URLs devem ser especificados pelas variáveis:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: definir as variáveis do servidor de rastreamento**

Para determinar quais variáveis do servidor de rastreamento usar:

1. Responda às perguntas da matriz de decisão abaixo. Use as variáveis que correspondem às suas respostas.
1. Substitua os marcadores de posição com os URLs do servidor de rastreamento.
1. Remova o servidor de rastreamento não usado e as variáveis do servidor da [!DNL Experience Cloud] do código.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Quando usada, corresponda os [!DNL Experience Cloud] urls do servidor aos urls do servidor de rastreamento correspondentes: &gt;
>* [!DNL Experience Cloud] URL do servidor = URL do servidor de rastreamento
>* [!DNL Experience Cloud] URL seguro do servidor = URL seguro do servidor de rastreamento
>



Caso não tenha certeza de como encontrar o servidor de rastreamento ver [as Perguntas frequentes](../mcvid-faq-intro/ecid-faq.md) e [preencher corretamente as variáveis trackingserver e trackingserversecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Etapa 5: Atualizar o arquivo appmeasurement. js ou s_ code. js {#section-b53113aea1bd4de896e0e4e9a7edee19}

Adicione esta função ao arquivo `AppMeasurement.js` ou `s_code.js` ao arquivo:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Coloque o código na mesma seção que contém configurações como `linkInternalFilters`, `charSet`etc `trackDownloads`.

***(Opcional, mas recomendado)*Criação de um prop personalizado**

Defina um prop personalizado ou `AppMeasurement.js``s_code.js` para medir a cobertura. Adicione este prop personalizado à `doPlugins` função de seus `AppMeasurement.js``s_code.js` arquivos:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Etapa 6: Adicionar o código da API do visitante à página {#section-d46d6aa324c842f2931d901e38d6db1d}

Coloque o `VisitorAPI.js` arquivo nas `<head>` tags em cada página. Ao anexar o arquivo `VisitorAPI.js` à página:

* Coloque-o no início da `<head>` seção a ele é exibido antes de outras tags de solução.
* É necessário executar antes do AppMeasurement e do código de outras soluções da [!DNL Experience Cloud].

Transfira esse código para a produção após os testes e a verificação.

## Etapa 7: (Opcional) Configurar um período de carência {#section-7bbb2f72c26e4abeb8881e18366797a3}

Se algum desses casos de uso se aplicar à sua situação, peça [ao Atendimento ao cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html) para configurar um período [de carência temporário](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md). Os períodos de carência podem durar até 180 dias. É possível renovar um período de carência, se necessário.

**Implementação parcial**

Se você possuir páginas que usam o serviço de ID e outras que não o usam, é necessário ter um período de carência para que todas sejam relatadas no mesmo conjunto de relatórios do [!DNL Analytics]. Isso é comum se você contar com um conjunto de relatórios globais que relatam entre domínios.

O período de carência será cancelado depois da implantação do serviço de ID em todas as suas páginas da Web que forem relatadas no mesmo conjunto de relatórios.

**Exigências do cookie s_vi**

É necessário ter um período de carência se os novos visitantes precisarem ter um cookie s_vi após migrarem para o serviço de ID. Isso é comum se a implementação ler o cookie s_vi e o armazenar em uma variável.

A descontinuação do período de carência após sua implementação pode capturar a MID em vez de ler o cookie s_vi.

Consulte [Cookies e o serviço de Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md).

É necessário ter um período de carência caso envie dados para um sistema interno de um feed de dados de sequência de cliques que processe os usos das colunas `visid_high` e `visid_low`.

Descontinuar o período de carência após seu processo de ingestão de dados pode usar as `post_visid_high``post_visid_low` colunas.

Consulte [Referência da coluna de dados da sequência de cliques](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

**Ingestão de dados da sequência de cliques**

## Etapa 8: Testar e implantar o código do serviço de ID {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Você pode testar e implantar como segue.

**Teste e verifique**

Para testar a implementação de serviço de ID, verifique:

* O [cookie AMCV](../mcvid-introduction/mcvid-cookies.md) no domínio em que sua página está hospedada.
* O valor da MID na solicitação de imagem do [!DNL Analytics] com a [ferramenta Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).

Consulte [Testar e verificar o serviço da Experience Cloud ID](../mcvid-implementation-guides/mcvid-test-verify.md).

**Implantar código**

Implanta o código após o teste.

Caso você habilite um período de carência na [Etapa 7](../mcvid-implementation-guides/mcvid-setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Garanta que a ID do [!DNL Analytics] e a MID estejam presentes na solicitação de imagem.
* Lembre-se de desabilitar o período de carência após atender os critérios para a descontinuação.
