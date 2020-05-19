---
description: Essas configurações permitem que diferentes instâncias do código do serviço de ID implementado em um iFrame e na página pai se comuniquem entre si. Foram projetadas para ajudar a resolver problemas com 2 casos de uso específicos onde pode-se ou não controlar a página ou o domínio principal e onde há código do serviço de ID sendo carregado no iFrame de um domínio sob seu controle. Eles estão disponíveis no código VisitorAPI.js versão 2.2 ou superior.
keywords: ID Service
seo-description: Essas configurações permitem que diferentes instâncias do código do serviço de ID implementado em um iFrame e na página pai se comuniquem entre si. Foram projetadas para ajudar a resolver problemas com 2 casos de uso específicos onde pode-se ou não controlar a página ou o domínio principal e onde há código do serviço de ID sendo carregado no iFrame de um domínio sob seu controle. Eles estão disponíveis no código VisitorAPI.js versão 2.2 ou superior.
seo-title: whitelistParentDomain e whitelistIframeDomains
title: whitelistParentDomain e whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '932'
ht-degree: 100%

---


# whitelistParentDomain e whitelistIframeDomains {#whitelistparentdomain-and-whitelistiframedomains}

Essas configurações permitem que diferentes instâncias do código do serviço de ID implementado em um iFrame e na página pai se comuniquem entre si. Foram projetadas para ajudar a resolver problemas com 2 casos de uso específicos onde pode-se ou não controlar a página ou o domínio principal e onde há código do serviço de ID sendo carregado no iFrame de um domínio sob seu controle. Eles estão disponíveis no código VisitorAPI.js versão 2.2 ou superior.

Conteúdo:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> Sintaxe </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> Amostra de código </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> Casos de uso </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> Segurança e proteção da configuração </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> Métodos de API do visitante suportados </a> </li> 
</ul>

## Sintaxe {#section-f645198bbaba4fba8961acb6e88d1470}

Ambos os elementos de configuração são necessários ao usar esse código.

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Sintaxe de configuração </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: " <span class="varname"> Nome do domínio da página principal </span>" </span> </p> </td> 
   <td colname="col2"> <p>Aceita um único nome de domínio passado como uma sequência de caracteres. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "Domínio do iFrame","Domínio do iFrame", "Domínio do iFrame" </span>] </span> </p> </td> 
   <td colname="col2"> <p>Aceita um ou mais nomes de domínio do iFrame passados como um array. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Amostra de código {#section-09d0049fe88a473baa69d404c50bf8ae}

O código do [!UICONTROL serviço de ID] configurado é semelhante ao deste exemplo.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## Casos de uso {#section-fc2eeb93546b406fae3b102dbcd11de7}

Essas configurações ajudam a resolver o problema de configuração de um cookie de serviço de ID e atribuição de uma ID de visitante quando os navegadores bloqueiam cookies de terceiros e se qualquer uma dessas condições se aplicar:

* Você controla ou não a página/domínio pai.
* O código do serviço de ID não está instalado na página pai, mas é implementado em um iFrame.

>[!TIP]
>
>Você também pode implementar essas configurações quando estiver disponibilizando vídeo em um iFrame com o [Video Heartbeat](https://docs.adobe.com/content/help/pt-BR/media-analytics/using/media-overview.html). O Video Heartbeat precisa de uma ID de serviço de ID (a MID) para funcionar corretamente.

**Caso de uso 1: O navegador bloqueia cookies de terceiros e o serviço de ID é implementado no iFrame e na página pai**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento de caso de uso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condições</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso inclui as seguintes condições: </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">A Empresa A implementa o serviço de ID em suas home pages. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">A Empresa A implementa o serviço de ID no iFrame na sua home page. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">A Empresa A é proprietária da página pai e do iFrame e implementou o serviço de ID em ambos os locais. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">Um cliente carrega a página pai em um navegador que bloqueia cookies de terceiros. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Resultados</b> </p> </td> 
   <td colname="col2"> <p>Dadas essas condições, o serviço de ID: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">Funciona corretamente na página principal. Ele solicita e define o cookie AMCV e atribui uma ID exclusiva ao visitante do site. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">Não funciona no iFrame. Isso ocorre porque o navegador vê o iFrame como um domínio de terceiros e impede que o serviço de ID defina o cookie AMCV. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solução</b> </p> </td> 
   <td colname="col2"> <p>Modifique a função <span class="codeph">Visitor.getInstance</span> do serviço de ID no iFrame com essas configurações de lista de permissões. Especifique os domínios pai e filho no código. Essas configurações permitem que o código do serviço de ID no iFrame verifique o código do serviço de ID na página pai de uma ID de visitante. </p> <p>Se o código do serviço de ID no iFrame não receber uma página pai de resposta, essas configurações geram uma ID de visitante local. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Caso de uso 2: Solicitação de uma ID de um iFrame incorporado em uma página pai que você não controla ou que não usa o serviço de ID**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento de caso de uso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condições</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso inclui as seguintes condições: </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">A Empresa A não usa o serviço de ID. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">A Empresa A carrega um iFrame na página. Este iFrame pertence à Empresa B e é carregado em um domínio diferente da Empresa A. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">O navegador bloqueia cookies de terceiros. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Resultados</b> </p> </td> 
   <td colname="col2"> <p>Dadas essas condições, o serviço de ID: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">Não funciona no iFrame. Isso ocorre porque o navegador vê o iFrame como um domínio de terceiros e impede que o serviço de ID defina o cookie AMCV. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">Não é possível obter uma ID de visitante da página principal porque a Empresa A não usa esse serviço. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solução</b> </p> </td> 
   <td colname="col2"> <p>Modifique a função <span class="codeph">Visitor.getInstance</span> do serviço de ID no iFrame com essas configurações de lista de permissões. Especifique os domínios pai e filho no código. Essas configurações permitem que o código do serviço de ID no iFrame verifique o código do serviço de ID na página pai de uma ID de visitante. </p> <p>Se o código do serviço de ID no iFrame não receber uma página pai de resposta, essas configurações geram uma ID de visitante local. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Segurança e proteção da configuração {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

É possível implementar essas configurações com segurança porque:

* O serviço de ID implementado no domínio pai e o domínio iFrame devem usar a mesma ID da organização. Essas configurações de lista branca não funcionarão quando as IDs da organização no pai ou no iFrame forem diferentes.
* Essas configurações só se comunicam com o domínio e os iFrames especificados no código.
* A comunicação entre o iFrame e a página pai segue um formato específico. Se o serviço de ID na página pai não receber uma solicitação no formato esperado, esse processo de compartilhamento falhará.

## Métodos de API do visitante suportados {#section-30c6a9f4dcdc4265a1149260b97cc057}

O serviço de ID oferece suporte a um conjunto limitado de métodos de API públicos ao implementar essas configurações de lista branca. Os métodos suportados variam de acordo com os cenários de caso de uso descritos acima.

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso de uso </th> 
   <th colname="col2" class="entry"> Métodos suportados </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Caso 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Caso 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

