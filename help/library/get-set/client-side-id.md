---
description: Chame essa função do serviço de ID para determinar se o serviço de ID gerou uma ID de visitante da Experience Cloud (MID) do lado do cliente. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
keywords: Serviço de ID
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Chame essa função do serviço de ID para determinar se o serviço de ID gerou uma ID de visitante da Experience Cloud (MID) do lado do cliente. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.

**Sintaxe**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

A tabela a seguir lista e descreve as respostas retornadas por essa função.

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Resposta </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>O serviço de ID não conseguiu ou não recebeu uma MID do servidor da <span class="keyword">Experience Cloud</span>. Uma MID foi criada localmente no navegador (lado do cliente). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>O serviço de ID recebeu uma MID do servidor da <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>O serviço de ID não efetuou uma chamada para o servidor da <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>
