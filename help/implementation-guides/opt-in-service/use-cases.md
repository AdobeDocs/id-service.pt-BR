---
description: Casos de uso de amostra e soluções para gerenciar o serviço de Opt-in.
title: Casos de uso de opt-in
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
TQID: https://experienceleague.adobe.com/ssSKMn1pEhduempV4zjCqi4Pol1U0oEBU6l36SkUTH4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 460
ht-degree: 91%

---

# Casos de uso de opt-in {#opt-in-use-cases}

Casos de uso de amostra e soluções para gerenciar o serviço de Opt-in.

## Dicas e solução de problemas {#section-5c566366410f4a8f89eca0d3f556d99f}

* A inicialização do JS do Visitante é síncrona e é executada no carregamento da página. Se você estiver interagindo com uma persistência de permissões ou CMP que tenha alta latência, talvez seja preferível usar as funções assíncronas descritas em [Configuração de aceitação](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* O Opt-in é uma implementação por domínio. Ele não lidará com implementações entre domínios.
* Para desabilitar chamadas de terceiros para uma biblioteca específica, será necessário configurar essa preferência em cada biblioteca separadamente.

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
   <td colname="col1"> <p>O Analytics pode coletar no estado de pré-consentimento, mas todas as outras bibliotecas não podem ser carregadas até que o consentimento seja recebido </p> </td> 
   <td colname="col2"> <p>Usar a aceitação para habilitar a categoria do Analytics no estado de pré-consentimento </p> </td> 
   <td colname="col3"> <p>O Analytics usa seu próprio identificador e não a ECID para coletar em pré-consentimento. Depois que a ECID for aprovada, um novo identificador será usado, e o visitante receberá uma ECID que poderá ser usada para ativação e integrações. </p> <p>É esperada a fragmentação do visitante no estado pré/pós-consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>A medição própria pode coletar no estado pré-consentimento. Todos os outros tipos de uso de dados são impedidos até que o consentimento seja recebido. </p> </td> 
   <td colname="col2"> <p>Use a aceitação para habilitar as bibliotecas do Analytics + ECID no estado de pré-consentimento. </p> <p>Adicione a configuração "disablethirdpartycookies" à biblioteca da ECID para bloquear cookies de terceiros + sincronizações de ID no estado pré-consentimento </p> </td> 
   <td colname="col3"> <p>A chamada Demdex da Adobe acionará a recuperação da ECID, mas nenhum cookie Demdex, cookie de terceiros ou sincronização de ID estará presente. </p> <p>Mantém o visitante no estado pré/pós-consentimento consistente para o Analytics. A coleção no estado de pré-consentimento será vinculada à coleção de dados após o consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Medição própria e direcionamento são aceitáveis em um estado pré-consentimento. Todos os outros tipos de uso de dados são impedidos até que o consentimento seja recebido. </p> </td> 
   <td colname="col2"> <p>Use a aceitação para habilitar as bibliotecas do Analytics + ECID + Target no estado de pré-consentimento. </p> <p>Adicione a configuração <span class="codeph">isablethirdpartycookies</span> à biblioteca da ECID para bloquear cookies de terceiros + sincronizações de ID no estado pré-consentimento. Remova o sinalizador no estado de pós-consentimento. </p> </td> 
   <td colname="col3"> <p>A chamada Adobe Demdex acionará a recuperação da ECID, mas nenhum cookie Demdex, cookie de terceiros ou sincronização de ID estará presente. </p> <p>Mantém o visitante no estado pré/pós-consentimento consistente para soluções de próprias. A coleção no estado de pré-consentimento será vinculada à coleção de dados após o consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Nenhum cookie pode ser definido em um estado de pré-consentimento </p> </td> 
   <td colname="col2"> <p>Usar a aceitação para bloquear o carregamento de todas as bibliotecas até que o consentimento seja recebido </p> </td> 
   <td colname="col3"> <p>A implementação é a esperada e todas as bibliotecas, incluindo a ECID, serão carregadas na sequência correta no estado de pós-consentimento. </p> <p>Perda de dados para clientes que nunca consentiram em ser rastreados. </p> </td> 
  </tr> 
 </tbody> 
</table>

