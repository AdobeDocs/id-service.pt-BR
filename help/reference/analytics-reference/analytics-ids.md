---
description: O serviço de identidade da Experience Cloud substitui os métodos de ID de visitante herdados do Analytics.
keywords: Serviço de ID
title: Definir Analytics e Experience Cloud IDs
exl-id: 7399ea16-d13e-452c-b8d9-8d0699566aa2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 99%

---

# Definir Analytics e Experience Cloud IDs{#setting-analytics-and-experience-cloud-ids}

O serviço de identidade da Experience Cloud substitui os métodos de ID de visitante herdados do Analytics.

Depois que o serviço de ID é implementado, esse código é executado antes do AppMeasurement. O serviço de ID recupera as IDs da Experience Cloud e do Analytics para que esses valores estejam prontos quando o AppMeasurement for carregado.

Quando o AppMeasurement é carregado, os valores das IDs da Experience Cloud e do Analytics são solicitados do serviço de ID e enviados para a coleta de dados com cada chamada de servidor. Como o serviço de ID determina a ID de visitante e a transfere para o AppMeasurement, o serviço de ID deve ser incluído e implementado em cada página antes do arquivo JavaScript do AppMeasurement.

## Mudanças no processo de ID do Analytics {#section-79bb86ae63f546419bb1a7ef5e710462}

A mudança principal ao migrar para o serviço de ID da [!DNL Experience Cloud] é que o cookie da ID é configurado usando o JavaScript em vez do cabeçalho HTTP retornado pelo servidor da Web da coleta de dados. Para entender essa alteração, as seções a seguir descrevem como os cookies são definidos usando esses dois métodos.

**Cabeçalho HTTP**

Uma resposta HTTP de um servidor da Web define cookies em um navegador. É assim que o `s_vi` cookie é definido. O `s_vi` cookie identifica os visitantes do Analytics. Depois que um cookie é configurado, ele é enviado com todas as solicitações HTTP subsequentes para esse servidor.

Quando uma solicitação é enviada para o servidor de coleta de dados da Adobe, o cabeçalho é verificado para procurar um cookie `s_vi`. Se este cookie estiver na solicitação, ele é usado para identificar o visitante. Se o cookie não está na solicitação, o servidor gera uma [!DNL Experience Cloud] ID exclusiva, a configura como um cookie no cabeçalho de resposta HTTP e a envia com a solicitação. O cookie é armazenado no navegador e enviado de volta ao servidor de coleta de dados durante visitas subsequentes ao site. Isso permite que o visitante seja identificado nas visitas.

No entanto, alguns navegadores, como o Apple Safari, não aceitam cookies de terceiros. Esses cookies são definidos no navegador a partir de domínios diferentes do site atual. Além disso, o Safari bloqueia cookies em domínios de terceiros se um visitante não tiver estado nesse domínio antes. Por exemplo, se você está em `mysite.com` e o servidor de coleta de dados for `mysite.omtrdc.net`, o cookie retornado no cabeçalho HTTP de `mysite.omtrdc.net` pode ser rejeitado pelo navegador.

Para evitar isso, vários clientes implementaram registros CNAME para os servidores responsáveis pela coleta de dados. Esta pode ser uma parte eficiente de uma estratégia de [implementação de cookies próprios](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html?lang=pt-BR). Se um registro CNAME estiver configurado para mapear um nome de host no domínio do cliente para o servidor de coleta de dados (por exemplo, mapear `metrics.mysite.com` para `mysite.omtrdc.net`), o cookie da [!DNL Experience Cloud] é armazenado, pois o domínio de coleta de dados agora corresponde ao domínio do site. Isso aumenta a probabilidade de o cookie do serviço de ID ser armazenado. No entanto, isso apresenta alguma sobrecarga, pois é necessário configurar registros CNAME e manter certificados SSL para os servidores de coleta de dados.

**JavaScript**

O JavaScript pode ler e gravar cookies definidos no domínio próprio (o domínio do site atual). O serviço da [!DNL Experience Cloud] ID usa esse método para definir o cookie `AMCV_###@AdobeOrg` que contém todas as IDs de visitante, para que o domínio do servidor de rastreamento não precise mais corresponder ao domínio do site para que o cookie da ID seja armazenado. Na maioria das circunstâncias, essa é a maneira preferida de definir o cookie do serviço de ID, pois elimina a sobrecarga dos registros CNAME e certificados SSL.

<!---However, there are a few situations where setting the cookie in the HTTP header is beneficial for cross-domain tracking, which is described in [Data Collection CNAMEs and Cross-Domain Tracking](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).-->

## IDs personalizadas do Analytics {#section-b6a7bd19e9ff432390010062450808f6}

Definir uma ID do cliente usando `s.visitorID` é um método para identificar usuários no Analytics. No entanto, as integrações em que os dados do Analytics são exportados ou importados usando o Serviço de ID não funcionam quando um visitante é identificado usando `s.visitorID`.

Isso inclui, mas não está limitado a, públicos-alvo compartilhados, Analytics for Target (A4T) e atributos do cliente. Para essas integrações, não há suporte para uma ID personalizada do Analytics.

## Ordem da ID de visitante do Analytics {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

Depois de implantar o serviço de ID de visitante, há cinco maneiras de identificar um visitante no Analytics (listadas na tabela a seguir em ordem de preferência):

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Pedido usado </th> 
   <th colname="col2" class="entry"> Parâmetro do query (método de coleta) </th> 
   <th colname="col3" class="entry"> Apresentar quando </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=pt-BR" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID está definido </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=pt-BR" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>O visitante tinha um s_vi cookie antes de você implantar o serviço de ID da <span class="keyword">Experience Cloud</span> ou você tem um <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> período de carência</a> configurado. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (cookie AMCV_ definido pelo serviço de ID de visitante da Experience Cloud) </p> </td> 
   <td colname="col3"> <p>O navegador do visitante aceita cookies próprios </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/analytics-ids.html?lang=pt-BR" format="http" scope="external"> fid (cookie de recuperação de falhas no H.25.3 ou posterior, ou AppMeasurement para JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Um navegador não aceita cookies de terceiros e o servidor de rastreamento do Analytics está configurado como um servidor de rastreamento de terceiros. </p> <p> <p>Observação: o <span class="codeph">fid</span> é um identificador herdado e não é usado se você implementou o serviço de ID do site. Nesse caso, o <span class="codeph"> fid</span> não é necessário porque o <a href="../../introduction/cookies.md" format="dita" scope="local">cookie próprio AMCV</a> o torna obsoleto. Foi mantido para comportar o código herdado e por motivos históricos. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/technotes/visitor-identification.html?lang=pt-BR" format="http" scope="external"> Endereço IP, Agente do usuário, Endereço IP de gateway</a> </p> </td> 
   <td colname="col3"> <p>O navegador do visitante não aceita cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

Em muitos casos, você verá duas ou três IDs diferentes em uma chamada, mas o Analytics usará a primeira ID apresentada na lista como a [!DNL Experience Cloud] oficial. Por exemplo, se você estiver enviando uma ID de visitante personalizada (incluída no parâmetro de consulta &quot;vid&quot;), essa ID será usada antes de outras IDs que possam estar presentes nessa mesma ocorrência.

>[!MORELIKETHIS]
>
>* [Ordem de operação das IDs do Analytics](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)
