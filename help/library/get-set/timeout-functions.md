---
description: Chame essas funções do serviço de ID para determinar o status do tempo limite para uma solicitação de Serviço de identidade da Experience Platform, Analytics ou Audience Manager ID. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
keywords: Serviço de ID
seo-description: Chame essas funções do serviço de ID para determinar o status do tempo limite para uma solicitação de Serviço de identidade da Experience Platform, Analytics ou Audience Manager ID. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
seo-title: Métodos de callTimeOut
title: Métodos de callTimeOut
uuid: e 5047498-11 db -4945-b 356-c 92 b 7 d 447573
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Métodos de callTimeOut{#calltimeout-methods}

Chame essas funções do serviço de ID para determinar o status do tempo limite para uma solicitação de Serviço de identidade da Experience Platform, Analytics ou Audience Manager ID. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.

## Funções de tempo limite {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solução ou serviço </th> 
   <th colname="col2" class="entry"> Sintaxe de função </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Serviço de identidade da plataforma Experience Platform </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. mcidcalltimedout ()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. analyticsidcalltimedout ()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. aamidcalltimedout ()</span> </p> </td> 
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
