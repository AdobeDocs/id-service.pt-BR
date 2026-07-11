---
description: Essa função permite que você compartilhe a ECID de um visitante entre domínios quando os navegadores bloqueiam cookies de terceiros. Para usar essa função, é necessário implementar o Serviço de ID de visitante e ser o proprietário dos domínios de origem e destino. Disponível na versão 1.7.0 ou posterior de VisitorAPI.js.
keywords: Serviço de ID de visitante
title: appendVisitorIDsTo (rastreamento entre domínios)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
TQID: https://experienceleague.adobe.com/F4rWmYj6NidX861-qU8KI9RRbdwNdzP0x4CZUxPZfYw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 432
ht-degree: 50%

---

# appendVisitorIDsTo (rastreamento entre domínios){#appendvisitoridsto-cross-domain-tracking}

>[!TIP]
>
>O rastreamento entre domínios não funcionará conforme o esperado se a ECID for rejeitada inicialmente (ou anteriormente). Ele não verificará as IDs existentes que foram transmitidas via URL ou que já existiam no cookie, considerando que essas eram as IDs quando o consentimento foi definido como &quot;NÃO&quot;.

Essa função permite que você compartilhe a ECID de um visitante entre domínios quando os navegadores bloqueiam cookies de terceiros. Para usar essa função, é necessário implementar o Serviço de ID de visitante e ser o proprietário dos domínios de origem e destino. Disponível em `VisitorAPI.js` versão 1.7.0 ou superior.

Conteúdo:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Rastrear visitantes nos domínios quando os navegadores bloqueiam cookies de terceiros </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Anexar a amostra de código da ID de visitante </a> </li> 
 </a> </li> 
</ul>

## Rastrear visitantes nos domínios quando os navegadores bloqueiam cookies de terceiros {#section-7251d88befd440b4b79520e33c5aa44a}

O Serviço de ID do visitante grava cookies próprios e de terceiros no navegador quando uma pessoa visita seu site (consulte [Cookies e o Serviço de ID do visitante](../../introduction/cookies.md) ). O cookie primário contém a MID, um identificador exclusivo para esse visitante. O cookie de terceiros contém outra ID usada pelo Serviço de ID do visitante para gerar a MID. Quando um navegador bloqueia esse cookie de terceiros, o Serviço de ID de visitante não pode:

* Gerar novamente o identificador exclusivo do visitante do site quando eles navegarem para outro domínio.
* Rastrear visitantes em diferentes domínios pertencentes à sua organização.

Para ajudar a resolver esse problema, implemente `Visitor.appendVisitorIDsTo( *`URL`*)`. Essa propriedade permite que o Serviço de ID do visitante rastreie visitantes do site em vários domínios, mesmo quando os navegadores bloqueiam cookies de terceiros. Funciona assim:

* À medida que um visitante navega em outros domínios, o `Visitor.appendVisitorIDsTo( *`URL`*)` anexa a MID como um parâmetro de consulta no redirecionamento de URL do domínio original para o domínio de destino.
* O código do Serviço de ID de visitante no domínio de destino extrai a MID do URL em vez de enviar uma solicitação da ID de visitante para a Adobe. Essa solicitação inclui a ID do cookie de terceiros, que não está disponível nesse caso.
* O código do Serviço de ID de visitante na página de destino usa a MID passada para rastrear o visitante.

Consulte a amostra de código para obter detalhes.

## Anexar a amostra de código da ID de visitante {#section-62d55f7f986542b0b9238e483d50d7b0}

O código de exemplo a seguir pode ajudar você a começar a usar a função `appendVisitorIDsTo`:

>[!TIP]
>
>Esse código pode ser colocado no editor de código personalizado que faz parte da extensão do Adobe Analytics ou na parte superior do [AppMeasurement.js](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=pt-BR).

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- 
>[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with `Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the Visitor ID Service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, ECID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` 
-->

<!--
## SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html?lang=pt-BR" format="https" scope="external"> Android Visitor ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html?lang=pt-BR" format="https" scope="external"> iOS Visitor ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> 
-->

