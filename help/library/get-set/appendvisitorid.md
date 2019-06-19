---
description: Essa função permite que você compartilhe a Experience Cloud ID de um visitante entre domínios quando os navegadores bloqueiam cookies de terceiros. Para usar essa função, é necessário implementar o serviço de ID, bem como ser o proprietário dos domínios de origem e destino. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
keywords: Serviço de ID
seo-description: Essa função permite que você compartilhe a Experience Cloud ID de um visitante entre domínios quando os navegadores bloqueiam cookies de terceiros. Para usar essa função, é necessário implementar o serviço de ID, bem como ser o proprietário dos domínios de origem e destino. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
seo-title: appendVisitorIDsTo (rastreamento entre domínios)
title: appendVisitorIDsTo (rastreamento entre domínios)
uuid: 06 b 453 ee -73 c 5-4625-82 d 9-82 7 ad 2 b 4 f 702
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# appendVisitorIDsTo (rastreamento entre domínios){#appendvisitoridsto-cross-domain-tracking}

Essa função permite que você compartilhe a Experience Cloud ID de um visitante entre domínios quando os navegadores bloqueiam cookies de terceiros. Para usar essa função, é necessário implementar o serviço de ID, bem como ser o proprietário dos domínios de origem e destino. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.

Conteúdo:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Acompanhar visitantes nos domínios quando os navegadores bloqueiam cookies de terceiros </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Anexar a amostra de código da ID de visitante </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) e suporte ao SDK </a> </li> 
</ul>

## Rastrear visitantes nos domínios quando os navegadores bloqueiam cookies de terceiros {#section-7251d88befd440b4b79520e33c5aa44a}

O serviço de ID grava um cookie primário e de terceiros para o navegador quando uma pessoa visita seu site (consulte [Cookies e o Serviço](../../introduction/cookies.md) de identidade da plataforma Experience Platform). O cookie primário contém a MID, uma ID exclusiva do visitante. O cookie de terceiros contém outra ID usada pelo serviço de ID para gerar a MID. Quando um navegador bloqueia esse cookie de terceiros, o serviço de ID não consegue:

* Gerar novamente a ID exclusiva desse visitante do site ao navegar para outro domínio.
* Acompanhar visitantes em domínios diferentes da sua empresa.

Para ajudar a solucionar esse problema, implemente ` Visitor.appendVisitorIDsTo( *`o url`*)`. Essa propriedade permite que o serviço de ID rastreie visitantes em diversos domínios, mesmo quando o navegador bloqueia cookies de terceiros. Funciona deste modo:

* Conforme um visitante navega para seus outros domínios, o ` Visitor.appendVisitorIDsTo( *`url`*)` anexa a MID como um parâmetro de consulta no URL redirecionado do domínio original para o de destino.
* O código do serviço de ID no domínio de destino extrai a MID do URL em vez de enviar uma solicitação da ID de visitante para a Adobe. Essa solicitação inclui a ID do cookie de terceiros, que não está disponível nesse caso.
* O código do serviço de ID na página de destino usa a MID passada para rastrear o visitante.

Consulte a amostra de código para obter mais detalhes.

## Anexar a amostra de código da ID de visitante {#section-62d55f7f986542b0b9238e483d50d7b0}

O exemplo a seguir pode ajudar você a começar com ` Visitor.appendVisitorIDsTo( *`url`*)`. Quando implementado adequadamente, o código JavaScript pode ser semelhante ao seguinte exemplo.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
//Redirect to the destination
```

## Dynamic Tag Management (DTM) e suporte ao SDK {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Compatível com </th> 
   <th colname="col2" class="entry"> Consulte </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Definir a função appendVisitorIDTo no DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/android/mc_methods.html" format="https" scope="external"> Métodos do serviço de ID do Android </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/ios/mc_methods.html" format="https" scope="external"> Métodos do serviço de ID do iOS </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
