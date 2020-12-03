---
description: Casos de uso de amostra e soluções para gerenciar o serviço de Opt-in.
seo-description: Casos de uso de amostra e soluções para gerenciar o serviço de Opt-in.
seo-title: Casos de uso de opt-in
title: Casos de uso de opt-in
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 31%

---


# Casos de uso de opt-in {#opt-in-use-cases}

Casos de uso de amostra e soluções para gerenciar o serviço de Opt-in.

## Dicas e solução de problemas {#section-5c566366410f4a8f89eca0d3f556d99f}

* A inicialização do JS do Visitante é síncrona e é executada no carregamento da página. Se você estiver interagindo com um CMP ou com uma persistência de permissões que tenha uma latência alta, talvez seja preferível usar as funções assíncronas descritas em Configuração [](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)opcional.
* O Opt-in é uma implementação por domínio. Ele não lidará com implementações entre domínios.
* Para desativar chamadas de terceiros para uma biblioteca específica, será necessário configurar essa preferência em cada biblioteca separadamente.

## Cenários de opt-in  {#section-1178053c065c430bba26f82ef383a71c}

Esses casos de uso são exemplos para usar o serviço de Opt-in.

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Requisito </th> 
   <th colname="col2" class="entry"> Soluções </th> 
   <th colname="col3" class="entry"> Impacto </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>O Analytics não tem problemas em coletar no estado de pré-consentimento, mas todas as outras bibliotecas não podem ser carregadas até que o consentimento seja recebido </p> </td> 
   <td colname="col2"> <p>Usar o Opt-in para ativar a categoria do Analytics no estado de pré-consentimento </p> </td> 
   <td colname="col3"> <p>O Analytics usa seu próprio identificador e não a ECID para coletar em pré-consentimento. Uma vez aprovado o ECID, será utilizado um novo identificador e o visitante receberá um ECID que pode ser utilizado para ativações e integrações. </p> <p>É esperado fragmentar o visitante no estado de pré/pós-consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>A medição própria pode coletar no estado pré-consentimento. Todos os outros tipos de utilização de dados foram impedidos até que o consentimento seja recebido. </p> </td> 
   <td colname="col2"> <p>Use o Opt-in para ativar as bibliotecas do Analytics + ECID no estado de pré-consentimento. </p> <p>Adicione a configuração "disablethirdpartycookies" à biblioteca ECID para bloquear cookies de terceiros + sincronizações de ID no estado de pré-consentimento </p> </td> 
   <td colname="col3"> <p>A chamada de Adobe Demdex acionará a recuperação de ECID, mas nenhum cookie Demdex, outro cookie de terceiros ou sincronizações de ID estarão presentes. </p> <p>Mantém o visitante no estado pré/pós-consentimento consistente para o Analytics. A coleta no estado de pré-consentimento será vinculada à coleta de dados de pós-consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Medição própria e direcionamento são aceitáveis em um estado pré-consentimento. Todos os outros tipos de utilização de dados foram impedidos até que o consentimento seja recebido. </p> </td> 
   <td colname="col2"> <p>Use o Opt-in para ativar as bibliotecas Analytics + ECID + Públicos alvos no estado de pré-consentimento. </p> <p>Adicione a configuração <span class="codeph">isablethirdpartycookies</span> à biblioteca da ECID para bloquear cookies de terceiros + sincronizações de ID no estado pré-consentimento. Remova o sinalizador no estado de pós-consentimento. </p> </td> 
   <td colname="col3"> <p>A chamada Adobe Demdex acionará a recuperação de ECID, mas nenhum cookie Demdex, outro cookie de terceiros ou sincronizações de ID estarão presentes. </p> <p>Mantém o visitante no estado pré/pós-consentimento consistente para soluções de próprias. A coleta no estado de pré-consentimento será vinculada à coleta de dados de pós-consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Nenhum cookie pode ser definido em um estado de pré-consentimento </p> </td> 
   <td colname="col2"> <p>Use a opção de aceitação para bloquear o carregamento de todas as bibliotecas até que o consentimento seja recebido </p> </td> 
   <td colname="col3"> <p>A implementação é a esperada e todas as bibliotecas, incluindo o ECID, serão carregadas na sequência correta no estado pós-consentimento. </p> <p>Perda de dados para clientes que nunca dão autorização para serem rastreados. </p> </td> 
  </tr> 
 </tbody> 
</table>

