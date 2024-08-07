---
description: O Serviço de identidade da Experience Cloud ativa a estrutura de identificação comum para aplicativos e serviços da Experience Cloud. Ele atribui uma ID exclusiva e contínua conhecida como Experience Cloud ID (ECID) a um visitante do site.
keywords: Serviço de ID; Serviço de identidade; Serviço de identidade da Experience Cloud
title: Serviço de identidade da Experience Cloud
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 100%

---

# Serviço de identidade da Adobe Experience Cloud {#experience-cloud-id-service}

O Serviço de identidade da Experience Cloud ativa a estrutura de identificação comum para aplicativos e serviços da Experience Cloud. Ele atribui uma ID exclusiva e contínua conhecida como Experience Cloud ID (ECID) a um visitante do site.

## Compreensão dos principais elementos da identidade

Para entender melhor como a Adobe ajuda a identificar de forma exclusiva os visitantes e resolve as informações de identidade, leia o detalhamento abaixo:

* **Serviço de identidade da Experience Cloud**: o Serviço de identidade da Experience Cloud **é responsável pela configuração da Experience Cloud ID (ECID)**. Para obter mais informações, leia a [Visão geral do serviço de identidade da Experience Cloud](./introduction/overview.md).
* **Experience Cloud ID (ECID)**: a ECID é um namespace de identidade compartilhada usado em aplicativos da Adobe Experience Platform e Adobe Experience Cloud para identificar pessoas e dispositivos. Para obter mais informações sobre a ECID, leia a [Visão geral da ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=pt-BR).
* **Serviço de identidade da Experience Platform**: o Serviço de identidade da Experience Platform fornece uma visão abrangente dos clientes e do comportamento deles ao unir as identidades de diferentes dispositivos e sistemas. Para obter mais informações, leia a [Visão geral do serviço de identidade da Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=pt-BR).

<!-- The Adobe Experience Cloud Identity Service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. It can replace ID generation code for Experience Cloud solutions and services. -->

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Introdução</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> Visão geral </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Requisitos do serviço de identidade da Experience Cloud </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=pt-BR" format="html" scope="external"> Implementação padrão com tags da Platform </a> </li> 
     </ul> </p> <p><b>Bibliotecas Javascript da Experience Cloud ID</b> </p> <p>O JavaScript para o serviço de identidade da Experience Cloud está localizado em: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>Itens novos ou especiais</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Serviço de opt-in</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> Perguntas frequentes </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>Notas de versão</b> </p> <p><b>A versão 4.4</b> de 17 de julho 2019 inclui suporte para o <a href="reference/hashing-support.md" format="dita" scope="local">algoritmo de hash SHA-256</a> que permite a transmissão de IDs do cliente ou endereços de email e de IDs com hash.</p><p><b>A Versão 4.0 de</b> 12 de fevereiro de 2019 inclui o <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">serviço de Opt-in</a> usado para identificar se você pode colocar um cookie no dispositivo ou no navegador de um usuário ao visitar o site. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Consulte as <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=pt-BR" format="https" scope="external">Notas de versão da Experience Cloud</a> para obter novos recursos e correções. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Consulte a seção <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=pt-BR" format="html" scope="external"> Notas de versão anteriores</a> para ver as seções mais antigas. </li> 
     </ul> </p> <p> <b>Recursos da Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/br/privacy.html" format="http" scope="external"> Centro de privacidade da Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=pt-BR" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/br/learning.html?promoid=KAUDK" scope="external" format="http"> Treinamento e tutoriais da Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/br/support/experience-cloud.html" scope="external" format="https"> Página inicial da documentação do produto</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
