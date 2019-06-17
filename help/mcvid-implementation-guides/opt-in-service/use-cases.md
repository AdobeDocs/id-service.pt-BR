---
description: Exemplos de casos de uso e soluções para gerenciar o serviço de aceitação.
seo-description: Exemplos de casos de uso e soluções para gerenciar o serviço de aceitação.
seo-title: Casos de uso de opt-in
title: Casos de uso de opt-in
uuid: d 75 a 44 d 5-b 713-43 d 1-b 5 b 6-95 d 1 d 0 d 213 a 7
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Casos de uso de opt-in {#opt-in-use-cases}

Exemplos de casos de uso e soluções para gerenciar o serviço de aceitação.

## Dicas e solução de problemas {#section-5c566366410f4a8f89eca0d3f556d99f}

* A inicialização do JS do Visitante é síncrona e é executada no carregamento da página. Se você estiver interagindo com uma persistência de permissões ou CMP que tenha alta latência, talvez seja preferível usar as funções assíncronas descritas em [Configuração de Opt-in](../../mcvid-implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* O Opt-in é uma implementação por domínio. Ele não lidará com implementações entre canais.
* Para desativar chamadas de terceiros para uma biblioteca específica, será necessário configurar a preferência em cada biblioteca separadamente.

## Cenários de opt-in {#section-1178053c065c430bba26f82ef383a71c}

Esses casos de uso são ideias de uso do serviço de aceitação.

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
   <td colname="col1"> <p>O Analytics pode coletar no estado pré-consentimento, mas todas as outras bibliotecas não poderão ser carregadas até que o consentimento seja recebido </p> </td> 
   <td colname="col2"> <p>Use o Opt-in para ativar a categoria do Analytics no estado pré-consentimento </p> </td> 
   <td colname="col3"> <p>O Analytics usa seu próprio identificador e não a ECID para coletar em pré-consentimento. Quando a ECID for aprovada, um novo identificador será usado e o visitante receberá uma ECID que pode ser usada para ativação e integração. </p> <p>A fragmentação do visitante no estado pré/pós-consentimento é esperada. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>A medição própria pode coletar no estado pré-consentimento. Todos os outros tipos de uso de dados estão impedidos até o recebimento do consentimento. </p> </td> 
   <td colname="col2"> <p>Use o Opt-in para ativar as bibliotecas do Analytics + ECID no estado pré-consentimento. </p> <p>Adicione a configuração “disablethirdpartycookies” à biblioteca da ECID para bloquear cookies de terceiros + sincronizações de ID no estado pré-consentimento </p> </td> 
   <td colname="col3"> <p>A chamada Demdex da Adobe disparará a recuperação da ECID, mas nenhum cookie Demdex, cookie de terceiros ou sincronização de ID estará presente. </p> <p>Mantém o visitante no estado pré/pós-consentimento consistente para o Analytics. A coleta no estado pré-consentimento estará vinculada à coleta de dados pós-consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Medição própria e direcionamento são aceitáveis em um estado pré-consentimento. Todos os outros tipos de uso de dados estão impedidos até o recebimento do consentimento. </p> </td> 
   <td colname="col2"> <p>Use o Opt-in para ativar as bibliotecas do Analytics + ECID + Target no estado pré-consentimento. </p> <p>Adicione a configuração <span class="codeph">isablethirdpartycookies</span> à biblioteca da ECID para bloquear cookies de terceiros + sincronizações de ID no estado pré-consentimento. Remova o sinalizador no estado pós-consentimento. </p> </td> 
   <td colname="col3"> <p>A chamada Demdex da Adobe disparará a recuperação da ECID, mas nenhum cookie Demdex, cookie de terceiros ou sincronização de ID estará presente. </p> <p>Mantém o visitante no estado pré/pós-consentimento consistente para soluções de próprias. A coleta no estado pré-consentimento estará vinculada à coleta de dados pós-consentimento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Nenhum cookie pode ser definido em um estado pré-consentimento </p> </td> 
   <td colname="col2"> <p>Use o Opt-in para impedir o carregamento de todas as bibliotecas até que o consentimento seja recebido </p> </td> 
   <td colname="col3"> <p>A implementação está conforme o esperado e todas as bibliotecas, incluindo a ECID, serão carregadas na sequência correta no estado pós-consentimento. </p> <p>Perda de dados para clientes que nunca forneceram consentimento para serem rastreados. </p> </td> 
  </tr> 
 </tbody> 
</table>

