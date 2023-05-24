---
description: Casos de uso de amostra e soluções para gerenciar o serviço de Opt-in.
title: Casos de uso de opt-in
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 100%

---

# Casos de uso de opt-in {#opt-in-use-cases}

Casos de uso de amostra e soluções para gerenciar o serviço de Opt-in.

## Dicas e solução de problemas {#section-5c566366410f4a8f89eca0d3f556d99f}

* A inicialização do JS do Visitante é síncrona e é executada no carregamento da página. Se você estiver interagindo com uma persistência de permissões ou CMP que tenha alta latência, talvez seja preferível usar as funções assíncronas descritas em [Configuração de aceitação](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* O Opt-in é uma implementação por domínio. Ele não lidará com implementações entre domínios.
* Para desativar chamadas de terceiros para uma biblioteca específica, será necessário configurar essa preferência em cada biblioteca separadamente.

## Cenários de opt-in {#section-1178053c065c430bba26f82ef383a71c}

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
   <td colname="col1"> <p>O Analytics pode coletar no estado de pré-consentimento, mas todas as outras bibliotecas só podem ser carregadas depois que o consentimento é recebido </p> </td> 
   <td colname="col2"> <p>Usar a aceitação para ativar a categoria do Analytics no estado de pré-consentimento </p> </td> 
   <td colname="col3"> <p>O Analytics usa seu próprio identificador e não a ECID para coletar em pré-consentimento. Depois que a ECID for aprovada, um novo identificador será usado, e o visitante receberá uma ECID que poderá ser usada para ativação e integrações. </p> <p>É esperada a fragmentação do visitante no estado pré/pós-consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>A medição própria pode coletar no estado pré-consentimento. Todos os outros tipos de uso de dados são impedidos até que o consentimento seja recebido. </p> </td> 
   <td colname="col2"> <p>Use a aceitação para ativar as bibliotecas do Analytics + ECID no estado de pré-consentimento. </p> <p>Adicionar a configuração "disablethirdpartycookies" à biblioteca da ECID para bloquear cookies de terceiros + sincronizações de ID no estado de pré-consentimento </p> </td> 
   <td colname="col3"> <p>A chamada Demdex da Adobe acionará a recuperação da ECID, mas nenhum cookie Demdex, cookie de terceiros ou sincronização de ID estará presente. </p> <p>Mantém o visitante no estado pré/pós-consentimento consistente para o Analytics. A coleção no estado de pré-consentimento será vinculada à coleção de dados após o consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Medição própria e direcionamento são aceitáveis em um estado pré-consentimento. Todos os outros tipos de uso de dados são impedidos até que o consentimento seja recebido. </p> </td> 
   <td colname="col2"> <p>Use a aceitação para ativar as bibliotecas do Analytics + ECID + Target no estado de pré-consentimento. </p> <p>Adicione a configuração <span class="codeph">isablethirdpartycookies</span> à biblioteca da ECID para bloquear cookies de terceiros + sincronizações de ID no estado pré-consentimento. Remova o sinalizador no estado de pós-consentimento. </p> </td> 
   <td colname="col3"> <p>A chamada Adobe Demdex acionará a recuperação da ECID, mas nenhum cookie Demdex, cookie de terceiros ou sincronização de ID estará presente. </p> <p>Mantém o visitante no estado pré/pós-consentimento consistente para soluções de próprias. A coleção no estado de pré-consentimento será vinculada à coleção de dados após o consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Nenhum cookie pode ser definido em um estado de pré-consentimento </p> </td> 
   <td colname="col2"> <p>Usar a aceitação para bloquear o carregamento de todas as bibliotecas até que o consentimento seja recebido </p> </td> 
   <td colname="col3"> <p>A implementação é a esperada e todas as bibliotecas, incluindo a ECID, serão carregadas na sequência correta no estado de pós-consentimento. </p> <p>Perda de dados para clientes que nunca consentiram em ser rastreados. </p> </td> 
  </tr> 
 </tbody> 
</table>
