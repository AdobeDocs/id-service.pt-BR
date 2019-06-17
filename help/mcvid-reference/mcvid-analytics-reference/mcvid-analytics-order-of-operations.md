---
description: Depois de implantar o serviço de ID do visitante, existem 5 maneiras de identificar o visitante no Analytics.
keywords: Serviço de ID
seo-description: Depois de implantar o serviço de ID do visitante, existem 5 maneiras de identificar o visitante no Analytics.
seo-title: Ordem de operação para IDs do Analytics
title: Ordem de operação para IDs do Analytics
uuid: cb 1 d 136 e -093 f -43 b 0-a 7 e 1-96 f 1 e 61 fdad 0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Ordem de operação das IDs do Analytics{#order-of-operations-for-analytics-ids}

Depois de implantar o serviço de ID do visitante, existem 5 maneiras de identificar o visitante no Analytics.

Em muitos casos, você verá duas ou três IDs diferentes em uma chamada, mas o Analytics usará a primeira ID apresentada na lista como a [!DNL Experience Cloud] oficial. Por exemplo, se estiver configurando uma ID de visitante personalizada (incluída no parâmetro de consulta `vid`), essa ID será usada antes das outras que podem estar presentes na mesma ocorrência. Consulte [Configuração do Analytics e IDs da Experience Cloud](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) para obter mais informações.

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
   <td colname="col1"> <p> <b>1<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>A <span class="codeph">s.visitorID</span> está definida. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>O visitante tinha um cookie s_ vi antes de implantar o serviço <span class="keyword"> da Experience Cloud</span> ID ou um período <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local"> de cortesia</a> configurado. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../mcvid-introduction/mcvid-cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>O navegador do visitante aceita cookies próprios. Isso é definido pelo cookie AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie de recuperação de falhas no H.25.3 ou posterior, ou AppMeasurement para JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Um navegador não aceita cookies de terceiros e o servidor de rastreamento do Analytics está configurado como um servidor de rastreamento de terceiros. </p> <p> <p>Observação: o <span class="codeph">fid</span> é um identificador herdado e não é usado se você implementou o serviço de ID do site. Nesse caso, <span class="codeph"> o fid</span> não é necessário porque o cookie <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> AMCV o</a> torna obsoleto. Foi mantido para comportar o código herdado e por motivos históricos. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> Endereço IP, Agente do usuário, Endereço IP de gateway</a> </p> </td> 
   <td colname="col3"> <p>O navegador do visitante não aceita cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

