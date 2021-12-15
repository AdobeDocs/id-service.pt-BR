---
description: Consulte esta seção para verificar se você está usando as soluções, os serviços e as versões de código adequadas exigidas pelo serviço de identidade da Experience Cloud.
keywords: Serviço de ID
title: Requisitos do serviço de identidade da Experience Cloud
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: e171c94ccfa1f4fe9b8d909d0204adb94f20cbb6
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 98%

---

# Requisitos do serviço de identidade da Experience Cloud {#requirements-for-the-experience-cloud-id-service}

Consulte esta seção para verificar se você está usando as soluções, os serviços e as versões de código adequadas exigidas pelo serviço de identidade da Experience Cloud.

## Requisitos garantem o sucesso e o suporte da implementação {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Uma implementação de sucesso e com suporte atende (ou excede) os requisitos de código, além de seguir as instruções à medida que aparecem na ajuda da [!DNL Adobe]. Uma implementação não suportada produzirá resultados inesperados e impedirá que o Atendimento ao cliente e nossas equipes de engenharia ajudem nos esforços para solucionar ou resolver seus problemas com o serviço de ID.

### Implementações padrão

Consulte [Tags de Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=pt-BR) para sua implementação padrão.

### Implementações não padrão

Para implementações não padrão ou manuais, você deve configurar o serviço de ID conforme descrito pelos procedimentos deste guia. Assim como nas diretrizes do DTM acima, a inserção e o carregamento inadequados do código criarão uma implementação sem suporte.

## Requisitos da Experience Cloud: ID da organização {#section-a02f537129a64ffbb690d5738d360c26}

Para usar o serviço de ID, a empresa deve estar habilitada para a [!DNL Experience Cloud] e ter uma ID da organização. Verifique a lista a seguir caso não saiba ao certo o status da [!DNL Experience Cloud] da sua empresa e precise localizar a ID da organização.

>[!IMPORTANT]
>
>A ID da organização diferencia maiúsculas de minúsculas, e deve ser usada exatamente como foi fornecida.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status da Experience Cloud </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Ativado</b> </p> </td> 
   <td colname="col2"> <p>Se sua empresa estiver habilitada para a <span class="keyword">Experience Cloud</span>, mas você não tiver a ID da organização, consulte as <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=pt-BR" format="https" scope="external">IDs organizacionais</a> (role para baixo até a seção <i>Localizar a ID da sua organização</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Não tenho certeza</b> </p> </td> 
   <td colname="col2"> <p> Se não souber ao certo o status da empresa na <span class="keyword">Experience Cloud</span>, pergunte para quem gerencia a conta da Adobe se os membros da empresa podem fazer logon em <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a> com uma Adobe ID. Se sim, você está habilitado e um administrador poderá exibir sua ID da organização. Para descobrir a ID da organização, consulte a seção “Página do administrador” na <a href="https://docs.adobe.com/help/pt-BR/core-services/interface/experience-cloud.html" format="https" scope="external">Administração da Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Não habilitada</b> </p> </td> 
   <td colname="col2"> <p> Se a empresa não estiver habilitada para a Experience Cloud, consulte <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=pt-BR" format="https" scope="external">Principais serviços - Habilitação das soluções</a> para começar. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Exigências do Analytics: coleta de dados regionais (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Todos os servidores de rastreamento foram convertidos para RDC, portanto, não há necessidade de alterar o servidor de rastreamento do Analytics. [Mais informações...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=pt-BR)

## Exigências de versão e código de bibliotecas {#section-ad7542a4317d430fa79fc6b095beb84d}

As seções a seguir listam as versões mínimas do código necessárias para usar o serviço da [!DNL Experience Cloud] ID.

>[!TIP]
>
>É recomendado usar as versões mais recentes do código em vez do mínimo exigido.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solução da Experience Cloud </th> 
   <th colname="col3" class="entry"> Biblioteca de código </th> 
   <th colname="col4" class="entry"> Requisitos da versão </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Serviço da</span> Experience Cloud ID</b> </p> </td> 
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
   <td colname="col4"> <p>H.27 </p> <p> <p>Observação:<span class="keyword"> o Analytics</span> s_code versão H.27 não é mais suportado com o lançamento do serviço de ID versão 1.6.0. Atualize o código para a versão mais recente do AppMeasurement. </p> </p> </td> 
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
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-technical.html?lang=pt-BR" format="https" scope="external">código mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js/how-atjs-works.html?lang=pt-BR" format="https" scope="external">Implementação de at.js</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos do SDK para Android e iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

No mínimo, o serviço de ID exige as versões do SDK listadas abaixo.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>É recomendado usar as versões mais recentes do código em vez do mínimo exigido.

O código do SDK deve ser habilitado para o serviço de ID. Habilite e baixe o código do SDK mais recente para cada aplicativo da conta do [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Consulte também:

* [Configuração das opções do SDK do serviço de ID do visitante](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=pt-BR)
* [Métodos do SDK para Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=pt-BR)
* [Métodos do SDK para iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=pt-BR)

>[!MORELIKETHIS]
>
>* [Biblioteca de código](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

