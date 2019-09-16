---
description: As funções idSyncByURL e idSyncByDataSource do serviço de ID permitem que você implemente manualmente uma sincronização de ID no iFrame de publicação de destino. Elas estão disponíveis no VisitorAPI.js versão 1.10 ou posterior.
keywords: Serviço de ID
seo-description: As funções idSyncByURL e idSyncByDataSource do serviço de ID permitem que você implemente manualmente uma sincronização de ID no iFrame de publicação de destino. Elas estão disponíveis no VisitorAPI.js versão 1.10 ou posterior.
seo-title: Sincronização de ID por URL ou fonte de dados
title: Sincronização de ID por URL ou fonte de dados
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: tm+mt
source-git-commit: b83b192655f59a728b488b4e2a9aa2efbcf093f0

---


# Sincronização de ID por URL ou fonte de dados{#id-synchronization-by-url-or-data-source}

As funções idSyncByURL e idSyncByDataSource do serviço de ID permitem que você implemente manualmente uma sincronização de ID no iFrame de publicação de destino. Elas estão disponíveis no VisitorAPI.js versão 1.10 ou posterior.

## Sintaxe, propriedades e macros {#section-90ac61617482463aaf4c57009b830332}

**Sintaxe**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Código </th> 
   <th colname="col2" class="entry"> Sincroniza as IDs do usuário </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>Entre os diferentes parceiros de dados e o <span class="keyword">Audience Manager</span> ao usar o URL de sincronização de ID personalizado. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Quando você já conhece o DPID e DPUUID e deseja enviá-los para o <span class="keyword">Audience Manager</span> no formato de URL de sincronização de ID padrão. </p> <p> 
     <draft-comment>
       Quando você já conhece a ID de usuário e deseja enviá-la para o Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**Propriedades**

A tabela a seguir lista e define as propriedades disponíveis para ambas as funções.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nome </th> 
   <th colname="col2" class="entry"> Tipo </th> 
   <th colname="col3" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> Sequência de caracteres </td> 
   <td colname="col3"> <p>A ID do provedor de dados atribuída pelo Audience Manager. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> Sequência de caracteres </td> 
   <td colname="col3"> <p>A ID exclusiva do provedor de dados para o usuário. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Número </td> 
   <td colname="col3"> <p> <i>(Opcional)</i> Define o tempo de expiração do cookie. Deve ser um inteiro. O padrão é de 20160 minutos (14 dias). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> Sequência de caracteres </td> 
   <td colname="col3"> <p>URL de Destino. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Macros**

Ambas as funções aceitam as seguintes macros:

* `%TIMESTAMP%`: gera um carimbo de data e hora (em milissegundos). Usado para eliminação de cache.
* `%DID%`: insere a ID do Audience Manager para o usuário.
* `%HTTP_PROTO%`: define o protocolo de comunicação (`http` ou `https`).

## Código e saída de exemplo {#section-0115615c37584a19a2ab11e917c4e7e9}

Ambas as funções retornam `Successfully queued` se bem-sucedidas. Do contrário, elas retornam uma sequência de mensagem de erro.

### visitor.idSyncByURL

**Código de exemplo**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Saída de exemplo**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**Código de exemplo**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dpuuid: '98765', // must be a string 
     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Saída de exemplo**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORE_LIKE_THIS]
>
>* [DIL idSync](https://docs.adobe.com/content/help/en/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)

