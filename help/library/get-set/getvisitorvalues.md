---
description: Esta é uma API assíncrona que retorna os identificadores para o Analytics, o serviço de ID, o cancelamento da coleta de dados, a localização geográfica e o conteúdo “blob” de metadados por padrão. Além disso, você pode controlar quais IDs deseja retornar com a enumeração opcional visitor.FIELDS.
keywords: Serviço de ID
seo-description: Esta é uma API assíncrona que retorna os identificadores para o Analytics, o serviço de ID, o cancelamento da coleta de dados, a localização geográfica e o conteúdo “blob” de metadados por padrão. Além disso, você pode controlar quais IDs deseja retornar com a enumeração opcional visitor.FIELDS.
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7 fb 831 b 3-cf 7 e -40 e 2-a 219-07 fec 28 ad 49 c
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

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

This function uses the following syntax (italics represents a placeholder for a variable): ` var *`values`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID type`*, visitor.FIELDS. *`ID type`*]);`

Nos parâmetros da função

* ` *`chamada de retorno`*` representa seu próprio código de retorno de chamada que recebe as IDs retornadas.
* *(Opcional)* ` visitor.FIELDS. *`O tipo de ID`*` é uma enumeração que permite especificar quais [valores de ID](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) você deseja retornar para essa função.

Consulte os casos de uso e as definições a seguir para obter mais informações.

## Caso de uso 1: solicitar o conjunto de dados padrão {#section-36a31683558742a5915db3a391e09f7b}

Esse código retorna o conjunto de dados padrão. Sua solicitação e a resposta podem ser semelhantes aos seguintes exemplos.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

Na resposta de exemplo padrão, alguns valores foram reduzidos para fins de demonstração.

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

Esse código usa uma matriz para retornar um conjunto específico de IDs usando o enum `visitor.FIELDS` . Nesse caso, queremos apenas a Experience Cloud ID (MCID) e a Analytics ID (MCAID) do visitante. Sua solicitação e a resposta podem ser semelhantes aos seguintes exemplos.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

A resposta da amostra personalizada retorna somente as IDs especificadas na solicitação.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Parâmetros de resposta definidos {#section-4c4c300167694c6fbff1d6c612f372b5}

A tabela a seguir lista e define os parâmetros de resposta. Esses são todos os valores no enum `visitor.FIELDS`. Observe que esse método retorna uma sequência de caracteres vazia se não existirem valores para uma variável específica.

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
   <td colname="col2"> <p>A ID de região para coleta de dados. É um identificador numérico da localização geográfica de um data center do serviço de ID específico. </p> <p>Consulte <a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external"> IDs de região DCS, Locais e Nomes de host </a> e <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getlocationhint </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>A <span class="keyword">Analytics</span> ID do visitante. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>A Experience Cloud ID do visitante. </p> <p>Consulte <a href="../../introduction/cookies.md" format="dita" scope="local"> Cookies e o Serviço de identidade da plataforma Experience Platform </a>. </p> </td> 
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
