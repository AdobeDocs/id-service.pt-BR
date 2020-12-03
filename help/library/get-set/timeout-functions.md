---
description: Chame essas funções do serviço de ID para determinar o status do tempo limite do serviço de identidade da Experience Cloud, do Analytics ou de uma solicitação do Audience Manager. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
keywords: ID Service
seo-description: Chame essas funções do serviço de ID para determinar o status do tempo limite do serviço de identidade da Experience Cloud, do Analytics ou de uma solicitação do Audience Manager. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
seo-title: Métodos de callTimeOut
title: Métodos de callTimeOut
uuid: e5047498-11db-4945-b356-c92b7d447573
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 96%

---


# Métodos de callTimeOut{#calltimeout-methods}

Chame essas funções do serviço de ID para determinar o status do tempo limite do serviço de identidade da Experience Cloud, do Analytics ou de uma solicitação do Audience Manager. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.

## Funções de tempo limite {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solução ou serviço </th> 
   <th colname="col2" class="entry"> Sintaxe da função </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Serviço de identidade da Experience Cloud </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Respostas de função {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Resposta </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>O serviço de ID enviou uma solicitação e ela atingiu o tempo limite. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>O serviço de ID enviou uma solicitação e recebeu uma resposta do servidor. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>O serviço de ID não enviou uma solicitação. </p> </td> 
  </tr> 
 </tbody> 
</table>

