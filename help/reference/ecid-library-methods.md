---
title: Métodos de biblioteca da ECID em um mundo da ITP Safari
description: Documentação da biblioteca da Adobe ECID (serviço de ID).
exl-id: ac1d1ee1-2b5f-457a-a694-60bb4c960ae7
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 100%

---

# Métodos de biblioteca da ECID em um mundo da ITP Safari

>[!NOTE]
>
>Foram feitas atualizações para refletir as últimas alterações na ITP, lançadas em 12 de novembro de 2020 como parte da versão do Big Sur OS.

À medida que o Safari reforça o rastreamento entre domínios por meio do ITP, a Adobe deve manter as práticas recomendadas para as bibliotecas que oferecem suporte aos clientes, além da privacidade e escolha do consumidor.

A partir de 10 de novembro de 2020, todos os cookies persistentes primários definidos pela API document.cookie, geralmente conhecidos como cookies &quot;do lado do cliente&quot;, e os cookies definidos por meio de implementações CNAME primárias em navegadores Safari e iOS móveis têm sua expiração limitada a sete dias. Os cookies de terceiros continuarão bloqueados conforme indicado nas versões anteriores da ITP. Para obter mais detalhes sobre a ITP 2.1 e o impacto das soluções da Adobe, leia [Safari ITP 2.1 Impact on Adobe Experience Cloud and Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Alterações, configurações e métodos relacionados à ITP

À medida que métodos adicionais são criados para rastreamento no Safari, eles são adicionados como referência nesta página.

>[!NOTE]
>
>*ECID* = *MID* = *MCID* em toda a documentação abaixo.

Veja abaixo os esforços relacionados ao uso da biblioteca ITP e ECID.

## Comportamento atual da biblioteca ECID com a ITP e o WebKit da Apple

O ITP 2.1 dificulta a capacidade de gravar cookies do lado do cliente, o que prejudica a capacidade de fornecer informações precisas de rastreamento do visitante para os clientes. Dessa forma, uma alteração está sendo introduzida nos servidores de rastreamento CNAME da Adobe para armazenar a Experience Cloud ID (ECID) do visitante em um cookie primário.

Essa alteração é útil apenas para clientes da ECID que utilizam um CNAME do Analytics no contexto próprio. Se você for um cliente do Analytics que não utiliza CNAME ou até mesmo se não for um cliente do Analytics, ainda é possível se qualificar para um registro CNAME. Entre em contato com o Atendimento ao cliente ou seu representante de conta para iniciar o processo de registro em um [CNAME](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html?lang=pt-BR).

Atualize para a biblioteca da ECID v. 4.3.0 + para aproveitar essa alteração.

A seguir, é mostrado como a biblioteca ECID se comporta com a ITP 2.1 e as alterações mais recentes feitas pela Apple como parte do lançamento do Big Sur.

**Projeto**

Depois que uma solicitação de ID é feita para demdex.net e uma ECID é recuperada, se um servidor de rastreamento for definido em sua biblioteca ECID, uma solicitação de ID será feita ao domínio do cliente. Esse ponto de extremidade lê o parâmetro de ECID da sequência de consulta e define um novo [cookie](/help/introduction/cookies.md) que abrange apenas a ECID e uma data de validade de dois anos. Sempre que esse ponto de extremidade é chamado dessa forma, o `s_ecid` cookie é regravado com uma data de validade de dois anos a partir da hora da chamada. A biblioteca da ECID precisa ser atualizada para v 4.3.0 para que o valor desse cookie possa ser recuperado.

>[!IMPORTANT]
>
>Como parte das atualizações do Big Sur, um `s_ecid` cookie definido via CNAME também é mantido com uma expiração de sete dias.

Esse novo `s_ecid` cookie segue o mesmo status de Opt-out do cookie AMCV. Se a ECID for lida a partir do `s_ecid` cookie, o demdex será sempre chamado imediatamente para recuperar o status de Opt-out mais recente para essa ID e armazenado no cookie AMCV.

Além disso, se o consumidor recusou o rastreamento do Analytics por meio deste [método](https://experienceleague.adobe.com/docs/analytics/implementation/js/opt-out.html?lang=pt-BR), esse `s_ecid` cookie será excluído.

O nome do servidor de rastreamento deve ser fornecido à biblioteca VisitorJS ao inicializar a biblioteca usando `trackingServer` ou `trackingServerSecure`. Isso deve corresponder à configuração `trackingServer` nas configurações do Analytics.

Se você optar por não aproveitar esse método, adicione a seguinte configuração à implementação da biblioteca da ECID: `discardtrackingServerECID`. Quando essa configuração é definida como true, a biblioteca de Visitante não lê a MID definida pelo servidor de rastreamento primário.

![](assets/itp-proposal-v1.png)

## Use o método appendVisitorIDsTo para rastreamento entre domínios (em vários domínios da sua própria empresa)

Essa função permite que você compartilhe a ECID de um visitante entre domínios quando os navegadores bloqueiam cookies de terceiros. Para usar essa função, é necessário implementar o serviço de ID, bem como ser o proprietário dos domínios de origem e destino. Disponível em VisitorAPI.js versão 1.7.0 ou posterior (mas não na versão 1.10.0).

**Projeto**

* Conforme um visitante navega até outros domínios, o Visitor.appendVisitorIDsTo(url) retorna um URL com a ECID em anexo como um parâmetro de consulta.

   Use esse URL para redirecionar do domínio original para o domínio de destino.

* O código do serviço de ID no domínio de destino extrai a ECID do URL em vez de enviar uma solicitação da ID de visitante para a Adobe.

   Essa solicitação inclui a ID do cookie de terceiros, que não está disponível nesse caso.

* O código do serviço de ID na página de destino usa a ECID passada para rastrear o visitante.

   >[!NOTE]
   >Se a página de destino já tiver uma ECID das visitas anteriores, a decisão de sobregravar o cookie existente é controlada por esta configuração overwriteCrossDomainMCIDAndAID. Para obter detalhes sobre essa configuração, consulte [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Para obter mais detalhes sobre este método, consulte a página de referência [appendVisitorIDsTo (Rastreamento entre domínios)](/help/library/get-set/appendvisitorid.md).
