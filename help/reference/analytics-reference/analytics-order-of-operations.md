---
description: Depois de implantar o serviço de ID do visitante, existem 5 maneiras de identificar o visitante no Analytics.
keywords: ID Service
seo-description: Depois de implantar o serviço de ID do visitante, existem 5 maneiras de identificar o visitante no Analytics.
seo-title: Ordem de operação das IDs do Analytics
title: Ordem de operação das IDs do Analytics
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '329'
ht-degree: 100%

---


# Ordem de operação das IDs do Analytics {#order-of-operations-for-analytics-ids}

Depois de implantar o serviço de ID do visitante, existem 5 maneiras de identificar o visitante no Analytics.

Em muitos casos, você verá duas ou três IDs diferentes em uma chamada, mas o Analytics usará a primeira ID apresentada na lista como a [!DNL Experience Cloud] oficial. Por exemplo, se estiver configurando uma ID de visitante personalizada (incluída no `vid` parâmetro de consulta), essa ID será usada antes das outras que podem estar presentes na mesma ocorrência. Consulte [Definir Analytics e Experience Cloud IDs](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) para obter mais informações.

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
   <td colname="col1"> <p> <b>1<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/pt-BR/analytics/implementation/vars/config-vars/visitorid.html" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>A <span class="codeph">s.visitorID</span> está definida. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/pt-BR/core-services/interface/ec-cookies/cookies-analytics.html" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>O visitante tinha um s_vi cookie antes de você implantar o serviço de ID da <span class="keyword">Experience Cloud</span> ou você tem um <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> período de carência</a> configurado. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>O navegador do visitante aceita cookies próprios. Isso é definido pelo cookie AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/pt-BR/id-service/using/reference/analytics-reference/analytics-ids.html" format="http" scope="external"> fid (cookie de recuperação de falhas no H.25.3 ou posterior, ou AppMeasurement para JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Um navegador não aceita cookies de terceiros e o servidor de rastreamento do Analytics está configurado como um servidor de rastreamento de terceiros. </p> <p> <p>Observação: o <span class="codeph">fid</span> é um identificador herdado e não é usado se você implementou o serviço de ID do site. Nesse caso, o <span class="codeph"> fid</span> não é necessário porque o <a href="../../introduction/cookies.md" format="dita" scope="local">cookie próprio AMCV</a> o torna obsoleto. Foi mantido para comportar o código herdado e por motivos históricos. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/pt-BR/analytics/technotes/visitor-identification.html" format="http" scope="external"> Endereço IP, Agente do usuário, Endereço IP de gateway</a> </p> </td> 
   <td colname="col3"> <p>O navegador do visitante não aceita cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

