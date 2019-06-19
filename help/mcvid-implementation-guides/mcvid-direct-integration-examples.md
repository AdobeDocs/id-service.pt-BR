---
description: Esses exemplos abordam dois casos de uso comuns relacionados à integração direta e à Experience Cloud ID (MID). A MID é uma ID exclusiva e contínua para os visitantes de seu site.
keywords: Serviço de ID
seo-description: Esses exemplos abordam dois casos de uso comuns relacionados à integração direta e à Experience Cloud ID (MID). A MID é uma ID exclusiva e contínua para os visitantes de seu site.
seo-title: Casos de uso da integração direta
title: Casos de uso da integração direta
uuid: 6 de 1 eb 8 b -4783-4545-8 a 64-ab 6 b 9 ef 93432
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# Casos de uso da integração direta {#direct-integration-use-cases}

Esses exemplos abordam dois casos de uso comuns relacionados à integração direta e à Experience Cloud ID (MID). A MID é uma ID exclusiva e contínua para os visitantes de seu site.

>[!TIP]
>
>* Analise e entenda a sintaxe [de código e variáveis](../mcvid-implementation-guides/mcvid-direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) antes de mergulhar nos casos de uso.
>* Para obter mais informações sobre a MID, consulte [Cookies e o serviço da Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md).
>



## Caso de uso 1: Eu tenho uma MID, mas quero passar minhas IDs de visitante e definir um estado de autenticação {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento do caso de uso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condições</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso considera que você: </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">Tem uma MID do visitante do site. Chamaremos essa ID de 1234. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">Reconheça esse visitante por sua ID exclusiva. Chamaremos essa ID de 9876. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">Deseja vincular a MID (1234) à sua ID exclusiva (9876). </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(Opcional)</i> Deseja definir um status de autenticação desse visitante. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Ações</b> </p> </td> 
   <td colname="col2"> <p>Nessas condições, faça uma chamada para o serviço de ID que inclui: </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">A MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">A ID do seu provedor de dados. Essa é uma ID exclusiva atribuída para sua empresa. Chamaremos essa ID de 4444. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">Sua ID para o visitante (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(Opcional)</i> Uma ID de status para definir o estado de autenticação desse visitante. </li> 
    </ul> <p>Se você listou outros parâmetros no <a href="../mcvid-implementation-guides/mcvid-direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> guia de integração direta</a> (por exemplo,<span class="codeph"> d_blob</span> ou <span class="codeph">dcs_region</span> etc.) não há problema em passá-los também. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solução e amostra de código</b> </p> </td> 
   <td colname="col2"> <p>Formate a chamada para o serviço de ID desta forma: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>Observe como a chamada de amostra contém a: </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID: <span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">MID ingressada em sua ID exclusiva do visitante: <span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">ID do estado de autenticação: <span class="codeph">...d_cid=4444%019876%011</span> (dica: é o último dígito). </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Caso de uso 2: Eu não tenho uma MID e precise gerar uma {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento do caso de uso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condições</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso considera que você: </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">Não tem uma MID para o visitante do site. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Precisa solicitar uma MID do serviço de ID. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Conhece sua <a href="../mcvid-reference/mcvid-requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">ID da organização</a>. Chamaremos isso de 5555. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Ações</b> </p> </td> 
   <td colname="col2"> <p>Nessa condições, faça uma chamada para o serviço de ID que inclui sua ID da organização. </p> <p>Se você listou outros parâmetros no <a href="../mcvid-implementation-guides/mcvid-direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> guia de integração direta</a> (por exemplo,<span class="codeph"> d_blob</span> ou <span class="codeph">dcs_region</span> etc.) não há problema em passá-los também. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solução e amostra de código</b> </p> </td> 
   <td colname="col2"> <p>Formate a chamada para o serviço de ID desta forma: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>Observe como a chamada de amostra contém sua ID da organização, <span class="codeph">d_orgid=5555</span>. Isso retornaria uma <span class="keyword">Experience Cloud</span> ID para esse visitante. </p> </td> 
  </tr> 
 </tbody> 
</table>
