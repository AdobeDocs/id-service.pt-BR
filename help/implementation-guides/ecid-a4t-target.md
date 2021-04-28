---
description: Essas instruções se aplicam aos clientes da A4T com implementações mistas do lado do servidor e do lado cliente para o Target, o Analytics e o serviço de ID. Os clientes que precisam executar o serviço de ID em um ambiente NodeJS ou Rhino também devem consultar essas informações. Essa instância do serviço de ID usa uma versão reduzida da biblioteca de códigos VisitorAPI.js, que você pode baixar e instalar no NPM (Gerenciador de pacotes de nós). Consulte esta seção para obter instruções de instalação e outros requisitos de configuração.
keywords: Serviço de ID
seo-description: Essas instruções se aplicam aos clientes da A4T com implementações mistas do lado do servidor e do lado cliente para o Target, o Analytics e o serviço de ID. Os clientes que precisam executar o serviço de ID em um ambiente NodeJS ou Rhino também devem consultar essas informações. Essa instância do serviço de ID usa uma versão reduzida da biblioteca de códigos VisitorAPI.js, que você pode baixar e instalar no NPM (Gerenciador de pacotes de nós). Consulte esta seção para obter instruções de instalação e outros requisitos de configuração.
seo-title: Uso do Serviço de ID com A4T e uma implementação do lado do servidor do Target
title: Uso do Serviço de ID com A4T e uma implementação do lado do servidor do Target
uuid: debbc5ca-7f8b-4331-923e-0e6339057de2
exl-id: 6f201378-29a1-44b7-b074-6004246fc999
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '915'
ht-degree: 100%

---

# Uso do Serviço de ID com A4T e uma implementação do lado do servidor do Target {#using-the-id-service-with-a-t-and-a-server-side-implementation-of-target}

Essas instruções se aplicam aos clientes da A4T com implementações mistas do lado do servidor e do lado cliente para o Target, o Analytics e o serviço de ID. Os clientes que precisam executar o serviço de ID em um ambiente NodeJS ou Rhino também devem consultar essas informações. Essa instância do serviço de ID usa uma versão reduzida da biblioteca de códigos VisitorAPI.js, que você pode baixar e instalar no NPM (Gerenciador de pacotes de nós). Consulte esta seção para obter instruções de instalação e outros requisitos de configuração.

## Introdução {#section-ab0521ff5bbd44c592c3eaab31c1de8b}

O A4T (e outros clientes) pode usar essa versão do serviço de ID quando for necessário:

* Renderize o conteúdo da página da Web em seus servidores e o transmita a um navegador para exibição final.
* Efetuar chamadas do [!DNL Target] do lado do servidor.
* Efetuar chamadas do lado do cliente (no navegador) para o [!DNL Analytics].
* Sincronizar IDs separadas do [!DNL Target] e do [!DNL Analytics] para determinar se um visitante visualizado por uma solução é a mesma pessoa visualizada por outra solução.

## Download do código e das interfaces fornecidas {#section-32d75561438b4c3dba8861be6557be8a}

Consulte o [repositório NPM do serviço de ID](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server) para baixar o pacote de códigos do lado do servidor e consultar as interfaces incluídas na versão atual.

## Fluxo de trabalho {#section-56b01017922046ed96536404239a272b}

O diagrama e as seções abaixo descrevem o que ocorre e o que é necessário configurar em cada etapa do processo de implementação do lado do servidor.

![](assets/serverside.png)

## Etapa 1: solicitar página {#section-c12e82633bc94e8b8a65747115d0dda8}

A atividade do lado do servidor começa quando um visitante faz uma solicitação HTTP para carregar uma página da Web. Durante essa etapa, o servidor recebe essa solicitação e verifica o [cookie AMCV](../introduction/cookies.md). O cookie AMCV contém a [!DNL Experience Cloud] ID (MID) do visitante.

## Etapa 2: gerar carga do serviço de ID {#section-c86531863db24bd9a5b761c1a2e0d964}

Em seguida, é necessário criar um *`payload request`* do lado do servidor para o serviço de ID. Uma solicitação de carga:

* Passa o cookie AMCV para o serviço de ID.
* Solicita dados exigidos pelo Target e Analytics em etapas subsequentes descritas abaixo.

>[!NOTE]
>
>Esse método solicita uma única mbox do [!DNL Target]. Se precisar solicitar várias mboxes em uma única chamada, consulte [generateBatchPayload](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server#generatebatchpayload).

A solicitação de carga deve ser semelhante ao seguinte exemplo de código. No exemplo de código, a função `visitor.setCustomerIDs` é opcional. Consulte [IDs do cliente e Estados de autenticação](../reference/authenticated-state.md) para obter mais informações.

```js
//Import the ID service server package 
var Visitor = require("@adobe-mcid/visitor-js-server"); 
 
//Pass in your Organization ID to instantiate Visitor 
var visitor = new Visitor("Insert Experience Cloud ID here"); 
 
// 
<i>(Optional)</i> Set a custom customer ID 
visitor.setCustomerIDs({ 
     userid:{ 
          id:"1234", 
          authState: Visitor.AuthState.UNKNOWN //AuthState is a static property of the Visitor class 
     } 
}); 
 
//Parse the visitor's HTTP request for the AMCV cookie 
var cookies = cookie.parse(req.headers.cookie || ""); 
var cookieName = visitor.getCookieName(); // Visitor API that returns the cookie name. 
var amcvCookie = cookies[cookieName]; 
 
//Generate the payload request pass your mbox name and the AMCV cookie if present 
var visitorPayload = visitor.generatePayload({ 
     mboxName: "bottom-banner-mbox", 
     amcvCookie: amcvCookie 
});
```

O serviço de ID retorna a carga em um objeto JSON semelhante ao seguinte exemplo. Os dados de carga são exigidos pelo [!DNL Target].

```js
{ 
    "marketingCloudVisitorId": "02111696918527575543455026275721941645", 
    "mboxParameters": { 
        "mboxAAMB": "abcd1234", 
        "mboxMCGLH": "9", 
        "mboxMCSDID": "56BE026543F7E211-1CC51BCAAE88F0D2", 
        "vst.userid.id": "1234567890", 
        "vst.userid.authState": 0 
    } 
}
```

Se o visitante não tiver um cookie AMCV, a carga omite os pares de valores chave abaixo:

* `marketingCloudvisitorId`
* `mboxAAMB`
* `mboxMCGLH`

## Etapa 3: adicionar carga à chamada do Target {#section-62451aa70d2f44ceb9fd0dc2d4f780f7}

Depois que o servidor receber dados de carga do serviço de ID, é necessário instanciar mais códigos para mesclá-los aos dados passados ao [!DNL Target]. O objeto JSON final passado para o [!DNL Target] deve ser semelhante a:

```js
{ 
"mbox" : "target-global-mbox", 
"marketingCloudVisitorId":"02111696918527575543455026275721941645", 
"requestLocation" : { 
     "pageURL" : "http://www.domain.com/test/demo.html", 
     "host" : "localhost:3000" 
     }, 
"mboxParameters" : { 
     "mboxAAMB" : "abcd1234", 
     "mboxMCGLH" : "9", 
     "mboxMCSDID": "56BE026543F7E211-1CC51BCAAE88F0D2", 
     "vst.userid.id": "1234567890", 
     "vst.userid.authState": 0, 
     } 
} 
```

## Etapa 4: obter o estado do servidor para o serviço de ID {#section-8ebfd177d42941c1893bfdde6e514280}

Os dados de estado do servidor contêm informações sobre o trabalho concluído no servidor. O código do serviço de ID do lado do cliente exige essas informações. Os clientes que implementaram o serviço de ID pelo [!DNL Dynamic Tag Manager] (DTM) podem configurar o DTM a fim de passar dados de estado do servidor pela ferramenta. Se você configurou o serviço de ID por um processo não padrão, é necessário retornar o estado do servidor com seu próprio código. O serviço de ID do lado do cliente e o código do [!DNL Analytics] passam dados de estado para a Adobe quando a página é carregada.

**Obter o estado do servidor pelo DTM**

Se você implementou o serviço de ID no DTM, é necessário adicionar código à página e especificar um par de valores de nome nas configurações do DTM.

**Código da Página**

Adicionar esse código à tag `<head>` da página HTML:

```js
//Get server state 
var serverState = visitor.getState(); 
 
Response.send(" 
... 
<head> 
     <script> 
          //Add 'serverState' as a stringified JSON global variable. 
          "var serverState = "+ JSON.stringify(serverState) +";  
     </script> 
     <script src = "DTM script (satellite JS)"> 
     </script> 
</head> 
...
```

**Configurações do DTM**

Adicione esses pares de valor de nome à seção **[!UICONTROL Geral > Configurações]** da instância do serviço de ID:

* **[!UICONTROL Nome:]** serverState
* **[!UICONTROL Valor:]** %serverState%

   >[!IMPORTANT]
   >
   >O nome do valor deve corresponder ao nome da variável definido para `serverState` no código da página.

As configurações definidas devem ter esta aparência:

![](assets/server_side_dtm.png)

Consulte também [Configurações do serviço de identidade da Experience Cloud para DTM](../implementation-guides/standard.md#concept-fb6cb6a0e6cc4f10b92371f8671f6b59).

**Obter o estado do servidor sem o DTM**

Se você tem uma implementação não padrão do serviço de ID, é necessário configurar esse código para funcionar no servidor enquanto monta a página solicitada:

```js
//Get server state 
var serverState = visitor.getState(); 
 
Response.send(" 
... 
<head> 
     <script src="VisitorAPI.js"></script> 
     <script> 
          var visitor = Visitor.getInstance(orgID, { 
          serverState: serverState  
          ... 
     </script> 
</head> 
...
```

## Etapa 5: servir uma página e retornar dados da Experience Cloud {#section-4b5631a0d75a41febd6f43f8c214c263}

Nesse ponto, o servidor da Web envia conteúdo da página para o navegador do visitante. A partir desse ponto, o navegador (e não o servidor) efetua as chamadas restantes do serviço de ID e do [!DNL Analytics]. Por exemplo, no navegador:

* O serviço de ID recebe dados de estado do servidor e passa a SDID para o AppMeasurement.
* O AppMeasurement envia dados sobre a ocorrência da página para o [!DNL Analytics], incluindo a SDID.
* O [!DNL Analytics] e o [!DNL Target] comparam SDIDs para esse visitante. Com uma SDID idêntica, o [!DNL Target] e o [!DNL Analytics] unem a chamada do lado do servidor e do lado do cliente. Nesse momento, ambas as soluções agora reconhecem o visitante como a mesma pessoa.

>[!MORELIKETHIS]
>
>* [Pacote de serviço de ID do lado do servidor do Gerenciador de pacote de nós](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server)

