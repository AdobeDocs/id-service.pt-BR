---
title: Métodos de biblioteca da ECID em um mundo da ITP Safari
seo-title: Métodos de biblioteca da ECID em um mundo da ITP Safari
description: Documentação da biblioteca da Adobe ECID (serviço de ID).
seo-description: Documentação da biblioteca da Adobe ECID (serviço de ID).
translation-type: tm+mt
source-git-commit: 51abd7b0f38da4c3375c0d2fe48d8bf96bdfb387

---


# Métodos de biblioteca da ECID em um mundo da ITP Safari

À medida que o Safari reforça o rastreamento entre domínios por meio do ITP, a Adobe deve manter as práticas recomendadas para as bibliotecas que oferecem suporte aos clientes, além da privacidade e escolha do consumidor.

Em 21 de fevereiro de 2019, a Apple anunciou a última atualização para ITP (Intelligent Tracking Prevention). Ao contrário das versões anteriores focadas em cookies de terceiros, essa versão apresenta novas medidas de prevenção de rastreamento para cookies próprios. A validade de todos os cookies próprios persistentes definidos pela API document.cookie, geralmente conhecidos como cookies “do lado do cliente”, é limitada a 7 dias. Os cookies de terceiros continuarão bloqueados conforme indicado nas versões anteriores da ITP. For more details on ITP 2.1 and the impact of Adobe solutions, read [Safari ITP 2.1 Impact on Adobe Experience Cloud and Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Perguntas frequentes sobre a Adobe ECID para Safari ITP

**Por que o cookie AMCV, definido pela biblioteca da Experience Cloud ID (ECID) em um domínio próprio dos clientes, é afetado pela ITP 2.1?**

No momento, o cookie AMCV conta com a API document.cookie e é definido pelo “lado do cliente”. O Safari favorece cookies definidos pelo servidor de um cliente.

**Por que um cookie definido por um servidor de rastreamento CNAME é uma opção melhor para rastrear no Safari?**

As regras de ITP focalizam em devolver o controle aos desenvolvedores. As implementações por meio de certificados CNAME não podem ser feitas somente por JavaScript. O programa de certificação CNAME da Adobe (rastreamento do lado do servidor) está em conformidade com a ITP e faz parte da estratégia da Adobe há muitos anos. A biblioteca da ECID está lançando métodos que focalizam em levar a funcionalidade de biblioteca da ECID para uma implementação CNAME.

**Por que a Adobe focaliza na biblioteca da ECID quando outros métodos de rastreamento de visitantes do Analytics são usados com CNAMEs atualmente?**

A biblioteca da ECID, o cookie AMCV e a ECID (também conhecida como MID) começaram como o método de integração de todas as soluções da Adobe em uma única ID. Essa ID continuará a ser a ID de nível de cookie prioritária no roteiro de produtos da Adobe, além de ser a ID de cookie padrão da Adobe Experience Platform.

Mais Perguntas frequentes serão adicionadas aqui, à medida que outras alterações de ITP forem lançadas. For more inquiries, please visit [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## Alterações, métodos e configurações relacionadas à ITP

À medida que métodos adicionais são criados para rastreamento no Safari, eles são adicionados como referência nesta página.

>[!NOTE] *ECID* = *MID* = *MCID* em toda a documentação abaixo.

Veja abaixo os esforços relacionados ao uso da biblioteca ITP e ECID.

## Use a biblioteca da ECID e o rastreamento CNAME para aumentar a validade da ID do visitante.

O ITP 2.1 dificulta a capacidade de gravar cookies do lado do cliente, o que prejudica a capacidade de fornecer informações precisas de rastreamento do visitante para os clientes. Dessa forma, uma alteração está sendo introduzida nos servidores de rastreamento CNAME da Adobe, para armazenar a Experience Cloud ID (ECID) do visitante em um cookie próprio.

Essa alteração é útil apenas para clientes da ECID que utilizam um CNAME do Analytics no contexto próprio. Se você for um cliente do Analytics que não utiliza CNAME ou até mesmo se não for um cliente do Analytics, ainda é possível se qualificar para um registro CNAME. Contact Customer Care or your account representative to start the process of registering for a [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

Atualize para a biblioteca da ECID v. 4.3.0 + para aproveitar essa alteração.

**Projeto**

Depois que uma solicitação de ID é feita para demdex.net e uma ECID é recuperada, se um servidor de rastreamento for definido em sua biblioteca ECID, uma solicitação de ID será feita ao domínio do cliente. Esse ponto de extremidade lê o parâmetro de ECID da sequência de consulta e define um novo [cookie](/help/introduction/cookies.md) que abrange apenas a ECID e uma data de validade de dois anos. Sempre que esse ponto de extremidade é chamado dessa forma, o `s_ecid` cookie é regravado com uma data de validade de dois anos a partir da hora da chamada. A biblioteca da ECID precisa ser atualizada para v 4.3.0 para que o valor desse cookie possa ser recuperado.

Esse novo `s_ecid` cookie segue o mesmo status de Opt-out do cookie AMCV. Se a ECID for lida a partir do `s_ecid` cookie, o demdex será sempre chamado imediatamente para recuperar o status de Opt-out mais recente para essa ID e armazenado no cookie AMCV.

In addition, if your consumer has opted out of Analytics tracking via this [method](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html), this `s_ecid` cookie will be deleted.

O nome do servidor de rastreamento deve ser fornecido à biblioteca VisitorJS ao inicializar a biblioteca usando o trackingServer ou trackingServerSecure. Isso deve corresponder à configuração trackingServer nas configurações do Analytics.

Se você optar por não aproveitar esse método, adicione a seguinte configuração à implementação da biblioteca da ECID: discardtrackingServerECID. Quando essa configuração é definida como true, a biblioteca de Visitante não lê a MID definida pelo servidor de rastreamento próprio.

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
