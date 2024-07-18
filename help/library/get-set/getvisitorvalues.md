---
description: Esta é uma API assíncrona que retorna os identificadores para o Analytics, o serviço de ID, o cancelamento da coleta de dados, a localização geográfica e o conteúdo “blob” de metadados por padrão. Além disso, você pode controlar quais IDs deseja retornar com a enumeração opcional visitor.FIELDS.
keywords: Serviço de ID
title: getVisitorValues
exl-id: bd023e8d-a804-4205-989f-e1e58080b63c
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 95%

---

# getVisitorValues{#getvisitorvalues}

Esta é uma API assíncrona que retorna os identificadores para o Analytics, o serviço de ID, o cancelamento da coleta de dados, a localização geográfica e o conteúdo “blob” de metadados por padrão. Além disso, você pode controlar quais IDs deseja retornar com a enumeração opcional visitor.FIELDS.

Conteúdo:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Sintaxe </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Caso de uso 1: solicitar o conjunto de dados padrão </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Caso de uso 2: solicitar um conjunto de dados personalizado </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Parâmetros de resposta definidos </a> </li> 
</ul>

## Sintaxe {#section-5aebe3907b2b46e997f45a1d1ed35c09}

Essa função usa a seguinte sintaxe (itálico representa um espaço reservado para uma variável): ` var *`valores`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`tipo de ID`*, visitor.FIELDS. *`tipo de ID`*]);`

Nos parâmetros da função:

* O ` *`retorno de chamada`*` representa seu próprio código de retorno de chamada que recebe as IDs retornadas.
* *(Opcional)* ` visitor.FIELDS. *`Tipo de ID`*` é um enum que permite especificar quais [valores de ID](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) você deseja que a função retorne.

Consulte os casos de uso e as definições a seguir para obter mais informações.

## Caso de uso 1: solicitar o conjunto de dados padrão {#section-36a31683558742a5915db3a391e09f7b}

Esse código retorna o conjunto de dados padrão. Sua solicitação e resposta podem ser semelhantes aos exemplos a seguir.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

Na resposta de amostra padrão, alguns valores foram encurtados para fins de demonstração.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## Caso de uso 2: solicitar um conjunto de dados personalizado {#section-467b2f4e513344c89b7332b05f6f59f3}

Esse código usa uma matriz para retornar um conjunto específico de IDs usando o `visitor.FIELDS` enum. Nesse caso, desejamos apenas a Experience Cloud ID (MCID) e a Analytics ID (MCAID) do visitante. Sua solicitação e resposta podem ser semelhantes aos exemplos a seguir.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

A resposta de amostra personalizada retorna somente as IDs especificadas na solicitação.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Parâmetros de resposta definidos {#section-4c4c300167694c6fbff1d6c612f372b5}

A tabela a seguir lista e define os parâmetros de resposta. Esses são todos os valores no `visitor.FIELDS` enum. Observe que esse método retornará uma string vazia se não houver valores para uma variável específica.

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Valor </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>Metadados criptografados do <span class="keyword">Audience Manager</span> conhecido como “a bolha”. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>A ID da região de coleta de dados. Este é um identificador numérico para a localização geográfica de um data center de serviço de ID específico. </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=pt-BR" format="https" scope="external"> IDs de região, locais e nomes de host do DCS </a> e <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local">getLocationHint</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>A <span class="keyword">Analytics</span> ID do visitante. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>A Experience Cloud ID do visitante. </p> <p>Consulte <a href="../../introduction/cookies.md" format="dita" scope="local">Cookies e o serviço de identidade da Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>Um sinalizador que indica se um visitante recusou a coleta de dados. </p> <p>Os valores incluem: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span>: um visitante recusou a coleta de dados. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false'</span>: um visitante não recusou a coleta de dados. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
