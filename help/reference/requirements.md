---
description: Consulte esta seção para verificar se você está usando as soluções, os serviços e as versões de código adequadas exigidas pelo Serviço de ID do visitante.
keywords: Serviço de ID de visitante
title: Requisitos para o serviço de ID de visitante da Adobe
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
TQID: https://experienceleague.adobe.com/yOoLEIKihVSpDLeZsplTZzg-toOENKlBzsQt2G2YcKk
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
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 39%

---

# Requisitos para o serviço de ID de visitante da Adobe {#requirements-for-the-experience-cloud-id-service}

Consulte esta seção para verificar se você está usando as soluções, os serviços e as versões de código adequadas exigidas pelo Serviço de ID do visitante.

## Requisitos garantem o sucesso e o suporte da implementação {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Uma implementação de sucesso e com suporte atende (ou excede) os requisitos de código, além de seguir as instruções à medida que aparecem na ajuda do Adobe. Uma implementação não suportada produzirá resultados inesperados e impedirá que o Atendimento ao cliente e nossas equipes de engenharia ajudem nos esforços para solucionar ou resolver seus problemas com o Serviço de ID do visitante.

### Implementações padrão

Consulte [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=pt-BR) na Coleta de dados da Adobe Experience Platform para sua implementação padrão.

### Implementações não padrão

Para implementações não padrão ou manuais, você deve configurar o Serviço de ID de visitante conforme descrito pelos procedimentos deste guia. Assim como nas diretrizes de implementação padrão acima, a inserção e o carregamento inadequados do código criarão uma implementação não compatível.

## Requisitos corporativos da CX: ID da organização IMS {#section-a02f537129a64ffbb690d5738d360c26}

Para usar o Serviço de ID de visitante, sua empresa deve estar habilitada para o CX Enterprise e ter uma ID da organização IMS. Verifique a lista a seguir caso não saiba ao certo o status da CX Enterprise da sua empresa e precise localizar a ID da organização IMS.

>[!IMPORTANT]
>
>A ID da organização IMS diferencia maiúsculas de minúsculas e deve ser usada exatamente como foi fornecida.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status corporativo da CX </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Habilitado</b> </p> </td> 
   <td colname="col2"> <p>Se sua empresa estiver habilitada para o CX Enterprise, mas você não tiver a ID da Organização IMS, consulte <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=pt-BR" format="https" scope="external"> IDs Organizacionais</a> (role para baixo até a seção <i>Localizar a ID da sua Organização</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Não tenho certeza</b> </p> </td> 
   <td colname="col2"> <p> Se não souber ao certo o status da empresa no CX, pergunte para quem gerencia a conta da Adobe se os membros da empresa podem fazer logon em <a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a> usando uma Adobe ID. Se sim, você está habilitado e um administrador poderá exibir sua ID da organização IMS. Para encontrar a ID da organização IMS, consulte a seção "Página de Administração" na <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=pt-BR" format="https" scope="external"> CX Enterprise Administration</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Não habilitada</b> </p> </td> 
   <td colname="col2"> <p> Se a empresa não estiver habilitada para o CX Enterprise, consulte <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=pt-BR" format="https" scope="external"> Principais serviços - Habilitando suas soluções</a> para começar. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Exigências do Analytics: coleta de dados regionais (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Todos os servidores de rastreamento foram convertidos para RDC, portanto, não há necessidade de alterar o servidor de rastreamento do Analytics. [Mais informações...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=pt-BR)

## Exigências de versão e código de bibliotecas {#section-ad7542a4317d430fa79fc6b095beb84d}

As seções a seguir listam as versões mínimas do código necessárias para usar o Serviço de ID do visitante.

>[!TIP]
>
>É recomendado usar as versões mais recentes do código em vez do mínimo exigido.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solução corporativa CX </th> 
   <th colname="col3" class="entry"> Biblioteca de código </th> 
   <th colname="col4" class="entry"> Requisitos da versão </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Serviço de ID do Visitante</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 ou posterior </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=pt-BR" format="https" scope="external">AppMeasurement para JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 ou posterior. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Observação: o <span class="keyword"> Analytics</span> s_code versão H.27 não é mais suportado com o lançamento do Serviço de ID de Visitante versão 1.6.0. Atualize seu código para a versão mais recente do AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Pulsação de vídeo </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=pt-BR" format="https" scope="external">Video Heartbeat 2.x para JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> Consulte <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=pt-BR" format="https" scope="external">Biblioteca de integração de dados</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/en/docs/target-dev/developer/client-side/at-js-implementation/at-js/overview" format="https" scope="external">código mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/en/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works" format="https" scope="external">Implementação de at.js</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos do SDK para Android e iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

No mínimo, o Serviço de ID de visitante exige as versões do SDK listadas abaixo.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>É recomendado usar as versões mais recentes do código em vez do mínimo exigido.

Seu código SDK deve ser habilitado para o Serviço de ID de visitante. Habilite e baixe o código do SDK mais recente para cada aplicativo da conta do [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Consulte também:

* [Configuração das opções do SDK do serviço de ID do visitante](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=pt-BR)
* [Métodos do SDK para Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=pt-BR)
* [Métodos SDK do iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=pt-BR)

>[!MORELIKETHIS]
>
>* [Biblioteca de código](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
