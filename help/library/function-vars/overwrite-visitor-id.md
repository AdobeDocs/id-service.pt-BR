---
description: Essa propriedade substitui as Experience Cloud e Analytics IDs dos visitantes durante a navegação de um domínio para outro. Para substituir uma ID, é necessário possuir e implementar o serviço de ID em cada domínio. Esse código não permite a substituição de IDs em domínios fora de seu controle.
keywords: Serviço de ID
seo-description: Essa propriedade substitui as Experience Cloud e Analytics IDs dos visitantes durante a navegação de um domínio para outro. Para substituir uma ID, é necessário possuir e implementar o serviço de ID em cada domínio. Esse código não permite a substituição de IDs em domínios fora de seu controle.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Essa propriedade substitui as Experience Cloud e Analytics IDs dos visitantes durante a navegação de um domínio para outro. Para substituir uma ID, é necessário possuir e implementar o serviço de ID em cada domínio. Esse código não permite a substituição de IDs em domínios fora de seu controle.

**Sintaxe:**`Visitor.overwriteCrossDomainMCIDAndAID: true|false` (o padrão é `false`)

**Amostra de código**

O código JavaScript pode ser semelhante ao seguinte exemplo.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Casos de uso**

Para rastrear visitantes do site, o serviço de ID grava uma [!DNL Experience Cloud] ID (ou MID) no cookie do navegador. A tabela a seguir lista e descreve os casos de uso comuns, nos quais você pode desejar substituir uma MID definida pelo serviço de ID em outro domínio.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso de uso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identificar visitantes em páginas de aterrissagem de domínio diferentes</b> </p> </td> 
   <td colname="col2"> <p>Considere que você é o proprietário dos Domínios A e B. Nesse caso, é possível definir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> quando: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Cada domínio tem uma página de aterrissagem própria. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">Um visitante já tem um cookie (e uma MID) definido a partir de uma visita anterior ao Domínio B. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">Você deseja identificar de modo consistente um visitante quando chega ao Domínio B vindo de A. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificar visitantes em páginas de aterrissagem e conversão</b> </p> </td> 
   <td colname="col2"> <p>Considere que você é o proprietário dos Domínios A e B. Nesse caso, é possível definir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> quando: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">O domínio A é a página de aterrissagem. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">O domínio B é uma página de conversão, agendamento ou outro fluxo de trabalho final à parte. </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Um visitante já tem um cookie (e um MID) definido a partir de uma visita anterior ao Domínio B, e você sabe que essas são MIDs menos desejáveis do lado do cliente em vez de MIDs do lado do servidor. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">Você deseja identificar de modo consistente um visitante quando chega ao Domínio B vindo de A. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificar visitantes de aplicativos móveis em navegadores da Web</b> </p> </td> 
   <td colname="col2"> <p>Esse caso de uso é um pouco diferente. Envolve a identificação de usuários enquanto mudam do aplicativo móvel para o site. Nesse caso, o visitante já tem uma MID definida localmente por um aplicativo móvel e uma MID diferente definida em um cookie no site. É possível definir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> para substituir a MID definida no cookie do navegador pela MID definida pelo aplicativo móvel. </p> </td> 
  </tr> 
 </tbody> 
</table>

