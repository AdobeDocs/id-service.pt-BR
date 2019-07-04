---
description: Essa propriedade define a ID do contêiner de origem dos dados que você deseja usar para sincronizações de ID.
keywords: Serviço de ID
seo-description: Essa propriedade define a ID do contêiner de origem dos dados que você deseja usar para sincronizações de ID.
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e35dc48b-1aa1-41e3-91c1-ef1e9d2d8b90
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncContainerID{#idsynccontainerid}

Essa propriedade define a ID do contêiner de origem dos dados que você deseja usar para sincronizações de ID.

Conteúdo:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> Sintaxe e amostra de código </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local"> O que são contêineres e quando devo usá-los? </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> Definir IDs de contêineres ao usar DIL e VisitorAPI.js </a> </li> 
</ul>

## Sintaxe e amostra de código {#section-b0c50732b1c84bed8616e82e8e83d58c}

**Sintaxe:**` idSyncContainerID: *`valor da ID do contêiner`*`

**Amostra de código:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## O que são contêineres e quando devo usá-los? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**Contêineres**

Os contêineres são objetos criados pelo [!DNL Audience Manager]. Embora não sejam acessíveis externamente, esses contêineres listam todas as fontes de dados que:

* Estão disponíveis para você, mas não são usadas na sincronização de ID.
* São usadas na sincronização de ID.

Mesmo se você não for um [!DNL Audience Manager] cliente do, sua conta terá esses contêineres se estiver trocando IDs com diferentes fontes de dados em páginas diferentes do seu domínio. Isso ocorre porque o [!DNL Audience Manager] fornece a tecnologia e a funcionalidade de back-end que permite a sincronização de ID.

**Casos de uso**

Dependendo da situação, você pode ou não adicionar essa configuração ao seu código do serviço de ID.

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Condição </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Não é necessário</b> </p> </td> 
   <td colname="col2"> <p>Você não precisa usar essa configuração se: </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">Você usa o serviço de ID com qualquer solução da <span class="keyword">Experience Cloud</span> e não executa sincronizações de ID com outras fontes de dados. Nesse caso, sua conta tem um contêiner padrão com a ID 0 e nenhuma ação é necessária. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">Todas as suas fontes de dados estão em um único contêiner. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Necessário</b> </p> </td> 
   <td colname="col2"> <p>Você precisa usar essa configuração quando todas as condições a seguir se aplicarem: </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">Você não usa o <span class="keyword">Audience Manager </span>. </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">Você precisa sincronizar IDs com outras fontes de dados organizadas por contêineres. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">Você precisa sincronizar as IDs com fontes de dados em diferentes contêineres em páginas diferentes no seu domínio. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Definir IDs de contêiner ao usar DIL e VisitorAPI.js {#section-f283cb69c8de4348b5316cc4e02a3e9e}

Você implantou [!DNL DIL]*e* VisitorAPI.js na mesma página:

* O código do serviço de ID do visitante tem prioridade sobre o DIL para sincronizações de ID.
* Defina a `idSyncContainerID` configuração de somente no código do serviço de ID.

