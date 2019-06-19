---
description: O Serviço de identidade da plataforma Experience Platform substitui os métodos herdados de ID de visitante do Analytics.
keywords: Serviço de ID
seo-description: O Serviço de identidade da plataforma Experience Platform substitui os métodos herdados de ID de visitante do Analytics.
seo-title: Definição de IDs do Analytics e da Experience Cloud
title: Definição de IDs do Analytics e da Experience Cloud
uuid: 421 cf 597-a 3 e 0-4 ca 3-8 ce 8-d 0 c 80 cbb 6 aca
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Definição de IDs do Analytics e da Experience Cloud{#setting-analytics-and-experience-cloud-ids}

O Serviço de identidade da plataforma Experience Platform substitui os métodos herdados de ID de visitante do Analytics.

Após o serviço de ID ser implementado, este código é executado antes do AppMeasurement. O serviço de ID recupera as IDs da Experience Cloud e do Analytics para que esses valores estejam prontos quando o AppMeasurement for carregado.

Quando o AppMeasurement é carregado, os valores das IDs da Experience Cloud e do Analytics são solicitados no serviço de ID e enviados para a coleta de dados com cada chamada de servidor. Como o serviço de ID determina a ID de visitante e a transfere para o AppMeasurement, o serviço de ID deve ser incluído e implementado em cada página antes do arquivo JavaScript do AppMeasurement.

## Mudanças no processo de ID do Analytics {#section-79bb86ae63f546419bb1a7ef5e710462}

A mudança principal ao migrar para o serviço de ID da [!DNL Experience Cloud] é que o cookie da ID é configurado usando o JavaScript em vez do cabeçalho HTTP retornado pelo servidor da Web da coleta de dados. Para entender essa mudança, as seções a seguir descrevem como os cookies são definidos usando estes dois métodos.

**Cabeçalho HTTP**

Uma resposta HTTP de um servidor da Web define os cookies de um navegador. Esse é o modo como o `s_vi` cookie é definido. O `s_vi` cookie identifica os visitantes do Analytics. Depois que um cookie é configurado, ele é enviado com todas as solicitações HTTP subsequentes para esse servidor.

Quando uma solicitação é enviada para o servidor de coleta de dados da Adobe, o cabeçalho é verificado para procurar um cookie `s_vi`. Se este cookie estiver na solicitação, ele é usado para identificar o visitante. Se o cookie não está na solicitação, o servidor gera uma [!DNL Experience Cloud] ID exclusiva, a configura como um cookie no cabeçalho de resposta HTTP e a envia com a solicitação. O cookie é armazenado no navegador e enviado para o servidor responsável pela coleta de dados durante as visitas subsequentes ao site. Isso permite que o visitante seja identificado quando fizer uma visita.

No entanto, alguns navegadores, como o Apple Safari, não aceitam cookies de terceiros. Esses cookies são definidos no navegador por domínios diferentes daqueles do site atual. Além disso, o Safari bloqueia cookies em domínios de terceiros se um visitante estiver naquele domínio pela primeira vez. Por exemplo, se você está em `mysite.com` e o servidor de coleta de dados for `mysite.omtrdc.net`, o cookie retornado no cabeçalho HTTP de `mysite.omtrdc.net` pode ser rejeitado pelo navegador.

Para evitar isso, vários clientes implementaram registros CNAME para os servidores responsáveis pela coleta de dados. Essa pode ser uma parte eficiente de uma estratégia de [implementação de cookies próprios](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/). Se um registro CNAME estiver configurado para mapear um nome de host no domínio do cliente para o servidor de coleta de dados (por exemplo, mapear `metrics.mysite.com` para `mysite.omtrdc.net`), o cookie da [!DNL Experience Cloud] é armazenado, pois o domínio de coleta de dados agora corresponde ao domínio do site. Isso aumenta a probabilidade dos cookies do serviço de ID serem armazenados. No entanto, isso apresenta alguma sobrecarga porque é necessário configurar os registros CNAME e manter os certificados SSL dos servidores responsáveis pela coleta de dados.

**JavaScript**

O JavaScript pode ler e gravar cookies definidos pelo domínio próprio (o domínio do site atual). O serviço da [!DNL Experience Cloud] ID usa esse método para definir o cookie `AMCV_###@AdobeOrg` que contém todas as IDs de visitante, para que o domínio do servidor de rastreamento não precise mais corresponder ao domínio do site para que o cookie da ID seja armazenado. Essa costuma ser a maneira preferida para definir o cookie do serviço de ID, pois elimina a sobrecarga dos registros CNAME e certificados SSL.

Entretanto, existem algumas situações em que definir o cookie no cabeçalho HTTP traz vantagens para o Rastreamento entre domínios, descrito em [Coletas de dados CNAME e rastreamento entre domínios](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).

## IDs personalizadas do Analytics {#section-b6a7bd19e9ff432390010062450808f6}

Definir uma ID do cliente usando `s.visitorID` é um método para identificar usuários no Analytics. No entanto, as integrações em que os dados do Analytics são exportados ou importados usando o Serviço de ID não funcionam quando um visitante é identificado usando `s.visitorID`.

Isso inclui, mas não está limitado a, públicos-alvo compartilhados, Analytics for Target (A4T) e atributos do cliente. Para essas integrações, não há suporte para uma ID personalizada do Analytics.

## Ordem da ID de visitante do Analytics {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

Depois de implantar o serviço de ID de visitante, há cinco maneiras de identificar um visitante no Analytics (listadas na tabela a seguir em ordem de preferência):

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ordem usada </th> 
   <th colname="col2" class="entry"> Parâmetro de consulta (método de coleta) </th> 
   <th colname="col3" class="entry"> Presente quando </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID está definido </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>O visitante tinha um cookie s_ vi antes de implantar o serviço <span class="keyword"> da Experience Cloud</span> ID ou um período <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> de cortesia</a> configurado. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (AMCV_ cookie definido pelo serviço de ID de visitante da Experience Cloud) </p> </td> 
   <td colname="col3"> <p>O navegador do visitante aceita cookies próprios </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie de recuperação de falhas no H.25.3 ou posterior, ou AppMeasurement para JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Um navegador não aceita cookies de terceiros e o servidor de rastreamento do Analytics está configurado como um servidor de rastreamento de terceiros. </p> <p> <p>Observação: o <span class="codeph">fid</span> é um identificador herdado e não é usado se você implementou o serviço de ID do site. Nesse caso, <span class="codeph"> o fid</span> não é necessário porque o cookie <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV o</a> torna obsoleto. Foi mantido para comportar o código herdado e por motivos históricos. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> Endereço IP, Agente do usuário, Endereço IP de gateway</a> </p> </td> 
   <td colname="col3"> <p>O navegador do visitante não aceita cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

Em muitos casos, você verá duas ou três IDs diferentes em uma chamada, mas o Analytics usará a primeira ID apresentada na lista como a [!DNL Experience Cloud] oficial. Por exemplo, se você estiver enviando uma ID de visitante personalizada (incluída no parâmetro de consulta &quot;vid&quot;), essa ID será usada antes de outras IDs que possam estar presentes nessa mesma ocorrência.

>[!MORE_ LIKE_ THIS]
>
>* [Ordem de operação das IDs do Analytics](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

