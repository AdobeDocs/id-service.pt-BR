---
description: Chame essa função do Serviço de ID de visitante para determinar se o Serviço de ID de visitante gerou uma ECID (MID) do lado do cliente. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
keywords: Serviço de ID de visitante
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 32%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Chame essa função do Serviço de ID de visitante para determinar se o Serviço de ID de visitante gerou uma ECID (MID) do lado do cliente. Disponível em `VisitorAPI.js` versão 1.7.0 ou superior.

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
   <td colname="col2"> <p>O Serviço de ID de visitante não conseguiu ou não recebeu uma MID do servidor CX Enterprise. Uma MID foi criada localmente no navegador (lado do cliente). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>O Serviço de ID de visitante recebeu uma MID do servidor CX Enterprise. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>O Serviço de ID de visitante não efetuou uma chamada para o CX Enterprise Server. </p> </td> 
  </tr> 
 </tbody> 
</table>

