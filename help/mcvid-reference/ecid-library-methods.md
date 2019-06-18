---
title: Métodos de biblioteca ECID em um world do Safari ITP
seo-title: Métodos de biblioteca ECID em um world do Safari ITP
description: Documentação da biblioteca da Adobe ECID (serviço de ID).
seo-description: Documentação da biblioteca da Adobe ECID (serviço de ID).
translation-type: tm+mt
source-git-commit: 1dd8b109f7e9567b5f72747ecc653d35d0942413

---


# Métodos de biblioteca ECID em um world do Safari ITP

Conforme o Safari mantém o rastreamento entre domínios por meio do ITP, a Adobe deve manter as práticas recomendadas para bibliotecas compatíveis com os clientes, bem como a privacidade e a escolha do consumidor.

Em Fe1 de fevereiro de 21 19, a Apple anunciou a última atualização para ITP (Intelligent Tracking Prevention). Ao contrário das versões anteriores focadas em cookies de terceiros, essa versão apresenta novas medidas de prevenção de rastreamento para cookies primários. Todos os cookies persistentes primários definidos por meio da API document. cookie, geralmente conhecida como cookies de &quot;cliente&quot;, possuem a expiração de 7 dias. Os cookies de terceiros continuarão bloqueados, conforme declarado nas versões anteriores do ITP. Para obter mais detalhes sobre ITP 2.1 e o impacto das soluções da Adobe, leia [o Safari ITP 2.1 Impacto sobre os clientes da Adobe Experience Cloud e da Experience Platform](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Perguntas frequentes sobre o Adobe ECID para Safari ITP

**Por que o cookie AMCV é definido pela biblioteca da Experience Cloud ID (ECID) no domínio próprio dos clientes, afetado pelo ITP 2.1?**

O cookie AMCV atualmente depende da API document. cookie e é definida via &quot;client-side&quot;. O Safari favorece cookies definidos a partir do servidor de um cliente.

**Por que um cookie é definido por um servidor de rastreamento CNAME, uma opção melhor para rastrear no Safari?**

As regras do ITP concentram-se no fornecimento de controle aos desenvolvedores. As implementações por certificados CNAME não podem ser feitas somente por javascript. O programa de certificação CNAME da Adobe (rastreamento do lado do servidor) está em conformidade com ITP e faz parte da estratégia da Adobe por muitos anos. A biblioteca ECID consiste em métodos que se concentram na movimentação de funcionalidade de biblioteca ECID para uma implementação CNAME.

**Por que a Adobe está focada na biblioteca ECID quando outros métodos de rastreamento de visitantes do Analytics são usados com cnames hoje?**

A biblioteca ECID, o cookie AMCV e o ECID (MID MID) começaram como o método para integrar todas as soluções da Adobe sob uma ID. Essa ID continuará a ser a ID de nível de cookie prioritária no roteiro de produto da Adobe e é a ID de cookie padrão da Adobe Experience Platform.

**Os cnames ajudam os clientes a ativarem o rastreamento de vários domínios?**

As mesmas regras e avisos existentes anteriormente com cnames ainda existem. Em alguns casos, os cnames podem ajudar em um cenário multidomínio. Se você tiver um site de entrada principal em que os usuários possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento de vários domínios nos navegadores que não aceitam cookies de terceiros. No entanto, embora os cnames possam ajudar com vários domínios em alguns cenários, o motivo para a mudança do ECID para implementações CNAME é para identificação persistente do visitante, e não para o rastreamento de vários domínios. Para obter mais informações sobre CNAME e vários domínios, consulte [Coletas de dados cnames e Rastreamento entre domínios](/help/mcvid-reference/mcvid-analytics-reference/mcvid-cname.md).

Mais Perguntas frequentes serão adicionadas aqui, como outras alterações de ITP são lançadas. Para obter mais consultas, visite [Adobe Experience Manager](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## Alterações, métodos e configurações relacionadas ao ITP

Como métodos adicionais são criados para rastreamento no Safari, eles serão adicionados como referência a essa página.

>[!NOTE]*ECID* = *MID* = *MCID* em toda a documentação abaixo.

Veja abaixo os esforços relacionados ao uso da biblioteca ITP e ECID.

## Usar a biblioteca ECID e o rastreamento CNAME para estender a expiração da ID do visitante

O ITP 2.1 agrupa a capacidade de gravar cookies do cliente, que desfazem a capacidade de fornecer informações precisas do visitante para os clientes. Dessa forma, uma alteração está sendo introduzida nos servidores de rastreamento CNAME da Adobe para armazenar a Experience Cloud ID (ECID) do visitante em um cookie próprio.

Essa alteração é útil apenas para clientes ECID que usam um CNAME do Analytics no contexto primário. Se você for um cliente do Analytics que não usa um CNAME, ou até mesmo um cliente que não seja do Analytics, você ainda poderá se qualificar para um registro CNAME. Entre em contato com o Atendimento ao cliente ou seu representante de conta para iniciar o processo de registro de um [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

Atualize para a biblioteca ECID v. 4.3.0 + para aproveitar essa mudança.

**Projeto**

Quando uma solicitação de ID é feita em demdex. net e um ECID é recuperado, se um servidor de rastreamento estiver definido na biblioteca ECID, uma solicitação de ID será feita ao domínio do cliente. Esse terminal lê o param ecid da string de consulta e define um novo [cookie](/help/mcvid-introduction/mcvid-cookies.md) que abrange apenas o ECID e uma data de expiração dois anos no futuro. Sempre que esse terminal é chamado dessa forma, o `s_ecid` cookie é reescrito com uma data de expiração dois anos a partir do momento da chamada. A biblioteca ECID precisa ser atualizada para v 4.3.0 para que o valor desse cookie possa ser recuperado.

Esse novo `s_ecid` cookie segue o mesmo status de não participação do cookie AMCV. Se a ecid for lida do `s_ecid` cookie, o demdex será sempre chamado para recuperar o status de opção mais recente para a ID e armazenado no cookie AMCV.

Além disso, se o consumidor não tiver optado por sair do Analytics por meio desse [método](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html), este `s_ecid` cookie será excluído.

O nome do servidor de rastreamento deve ser fornecido à biblioteca visitorjs ao inicializar a biblioteca com trackingserver ou trackingserversecure. Isso deve corresponder à configuração trackingserver nas configurações do Analytics.

Se você optar por não aproveitar esse método, adicione a seguinte configuração à implementação da biblioteca ECID: Discardtrackingserverecid. Quando essa configuração é definida como true, a biblioteca de visitante não lê a MID definida pelo servidor de rastreamento próprio.

![](assets/itp-proposal-v1.png)

## Use o método appendvisitoridsto para rastreamento entre domínios (dentro dos vários domínios da empresa)

Essa função permite compartilhar o ECID de um visitante nos domínios quando os navegadores bloqueiam cookies de terceiros. Para usar essa função, é necessário implementar o serviço de ID, bem como ser o proprietário dos domínios de origem e destino. Disponível em visitorapi. js versão 1.7.0 ou superior (mas não na versão 1.10.0).

**Projeto**

* Conforme um visitante navega para seus outros domínios, o Visitor. appendvisitoridsto (url) retorna um URL com o ACID anexado como um parâmetro de consulta.

   Use esse URL para redirecionar do domínio original para o domínio de destino.

* O código de serviço de ID no domínio de destino extrai o ECID do URL em vez de enviar uma solicitação para a Adobe para a ID do visitante.

   Essa solicitação inclui a ID do cookie de terceiros, que não está disponível nesse caso.

* O código de serviço de ID na página de destino usa o ECID enviado para rastrear o visitante.

   >[!NOTE]
   >Se a página de destino já tiver um ECID de visitas anteriores, a decisão de sobrescrever o cookie existente será controlada por este overwritecrossdomainmcidandaid. Para obter detalhes sobre essa configuração, consulte [overwritecrossdomainmcidandaid](/help/mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md).
   >
   >Para obter mais detalhes sobre este método, consulte a [página](/help/mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md) de referência appendvisitoridsto (Rastreamento de domínio cruzado).
