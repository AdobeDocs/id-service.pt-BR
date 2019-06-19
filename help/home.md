---
description: 'O Serviço de identidade da Experience Platform fornece uma ID contínua e universal que identifica seus visitantes em todas as soluções na Experience Cloud. '
keywords: Serviço de ID
seo-description: O Adobe Experience Platform Identity Service (serviço de ID) fornece uma ID contínua e universal que identifica seus visitantes em todas as soluções na Experience Cloud. Permite substituir o código de geração de ID para serviços como o Analytics, Audience Manager, Target e outros recursos e soluções da Experience Cloud.
seo-title: Serviço de identidade da plataforma Experience Platform
title: Serviço de identidade da plataforma Experience Platform
uuid: b 68194 b 5-e 549-4 f 6 f-bfaf -7744926 aeaac
translation-type: tm+mt
source-git-commit: 746f8937c59d318dcf7245c7f8484884974601dc

---


# Adobe Experience Platform Identity Service {#experience-cloud-id-service}

O Adobe Experience Platform Identity Service (serviço de identidade) fornece uma ID contínua e universal que identifica seus visitantes em todas as soluções na Experience Cloud. Permite substituir o código de geração de ID para serviços como o Analytics, Audience Manager, Target e outros recursos e soluções da Experience Cloud.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Introdução</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> Visão geral </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Requisitos para o Serviço de identidade da plataforma Experience Platform </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Implementação padrão com DTM </a> </li> 
     </ul> </p> <p><b>Bibliotecas Javascript da Experience Cloud ID</b> </p> <p>O javascript para o Serviço de identidade da Experience Platform está localizado em: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external"> https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>Itens novos ou especiais</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Serviço de aceitação</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> Perguntas frequentes </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>Anúncios:</b> </p> 
     <p> <p>Importante: O suporte ao serviço de ID para o Internet Explorer 6, 7 e 8 está obsoleto e será descontinuado em uma versão futura. </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>Notas de versão</b> </p> <p><b>A versão de February 2 de</b> fevereiro de 1.0 9 inclui o serviço <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> de aceitação</a> usado para identificar se você pode colocar um cookie no dispositivo ou no navegador de um usuário ao visitar o site. </p> <p>A versão de 18 de janeiro de 2018 inclui a atualização 3.0.0 do JavaScript e atualiza os métodos da API. Consulte <a href="library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> Disableidsyncs</a> e <a href="library/function-vars/disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> disablethirdpartycookies</a>. </p> 
    <draft-comment> 
     <p>A versão de outubro de 2017 não inclui alterações ou atualizações de código para o serviço de ID. O código do serviço de ID permanece inalterado na v 2.5. </p> 
    </draft-comment> 
    <draft-comment> 
     <p> A versão de setembro de 2017 aprimora o código do serviço de ID para v 2.5. </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Consulte as <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">Notas de versão da Experience Cloud</a> para obter novos recursos e correções. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Consulte <a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">as notas de versão anteriores</a>. </li> 
     </ul> </p> <p> <b>Recursos da Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Centro de privacidade da Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Treinamento e tutoriais da Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> Página inicial da documentação do produto</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

