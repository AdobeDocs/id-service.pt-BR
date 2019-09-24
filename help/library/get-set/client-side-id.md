---
description: Chame essa função do serviço de ID para determinar se o serviço de ID gerou uma ID de visitante da Experience Cloud (MID) do lado do cliente. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
keywords: Serviço de ID
seo-description: Chame essa função do serviço de ID para determinar se o serviço de ID gerou uma ID de visitante da Experience Cloud (MID) do lado do cliente. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Chame essa função do serviço de ID para determinar se o serviço de ID gerou uma ID de visitante da Experience Cloud (MID) do lado do cliente. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.

**Sintaxe**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

A tabela a seguir lista e descreve as respostas retornadas pela função.

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

