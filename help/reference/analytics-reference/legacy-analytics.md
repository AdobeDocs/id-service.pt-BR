---
description: Uma visão geral de como o serviço de identidade da Experience Cloud funciona com a Analytics ID herdada.
keywords: ID Service
seo-description: Uma visão geral de como o serviço de identidade da Experience Cloud funciona com a Analytics ID herdada.
seo-title: Solicitações do Analytics e da Experience Cloud ID
title: Solicitações do Analytics e da Experience Cloud ID
uuid: 28beed16-7ef9-4824-8e82-853930756eca
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Solicitações do Analytics e da Experience Cloud ID{#analytics-and-experience-cloud-id-requests}

Uma visão geral de como o serviço de identidade da Experience Cloud funciona com a Analytics ID herdada.

## Resumo {#section-64d8523ff7634cb987d0c6480f587dd3}

Historicamente, o serviço de identidade da Experience Cloud está integrado ao Adobe Analytics. Ele ainda é parte integral do Analytics, mas agora executa funções importantes para outras soluções e recursos na [!DNL Experience Cloud]. Devido a este legado histórico, verificar ou gravar uma Analytics ID é um pouco diferente do processo genérico descrito em [Como o serviço de identidade da Experience Cloud solicita e define IDs….](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a). Para obter mais informações sobre a ordem das operações para verificação de IDs, consulte [Definir Analytics e Experience Cloud IDs](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## O cookie AMCV não está definido no navegador {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Se o cookie [!DNL Experience Cloud] (AMCV) não estiver presente, uma chamada de serviço de ID [!DNL Adobe] gera uma resposta que varia dependendo da presença ou da ausência de uma ID do Analytics herdada. A ID [!DNL Analytics] herdada é armazenada no [cookie s_vi](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html). A tabela abaixo descreve como as IDs são gravadas no cookie AMCV com base no estado do cookie s_ vi.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status do cookie s_vi </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> O cookie s_vi não está definido</b> </p> </td> 
   <td colname="col2"> <p>O serviço de ID atribui aos visitantes uma <span class="keyword">Experience Cloud</span> ID (MID). A MID identifica os visitantes do <span class="keyword">Analytics</span> e de outras soluções da <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>O cookie s_vi está definido</b> </p> </td> 
   <td colname="col2"> <p>Quando um visitante do site com um cookie s_vi encontra o serviço de identidade da Experience Cloud pela primeira vez, esse serviço: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">Grava a ID do <span class="keyword">Analytics</span> armazenada no cookie s_vi para o cookie AMCV. Isso é gravado como a ID do <span class="keyword">Analytics</span> (AID). Essa ação <i>não</i> afeta a contagem de visitantes. O <span class="keyword">Analytics</span> continua identificando usuários com as IDs herdadas. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">Grava a MID no cookie AMCV. A MID identifica usuários em diferentes soluções. </li> 
    </ul> <p> <p>Observação: com um <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> período de carência</a>, a resposta do data center sempre inclui uma ID herdada armazenada no cookie s_vi. Durante o período de carência, a ID herdada é gravada no cookie AMCV como o valor de AID. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Os usuários identificados pelo cookie s_fid não terão o valor de FID herdado migrado para o cookie AMCV. Com um cookie s_fid, os usuários são migrados como se nenhum cookie s_fid estivesse presente (veja abaixo) e são exibidos como novos visitantes do seu site. Consulte Cookies [do](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html) Analytics para obter mais informações.

## O cookie AMCV está definido no navegador {#section-01c088fc565c4b24ba1722c7cc240310}

Se o cookie AMCV estiver presente, o usa a MID como o identificador do [!DNL Analytics] caso não exista um valor de ID do [!DNL Analytics] Analytics herdado no cookie.
