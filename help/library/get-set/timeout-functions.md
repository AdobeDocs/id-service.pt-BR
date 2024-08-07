---
description: Chame essas funções do serviço de ID para determinar o status do tempo limite do serviço de identidade da Experience Cloud, do Analytics ou de uma solicitação do Audience Manager. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
keywords: Serviço de ID
title: Métodos de callTimeOut
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 98%

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
