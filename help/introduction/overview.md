---
description: A função do Serviço de identidade da Experience Platform na Adobe Experience Cloud.
seo-description: O Serviço de identidade da Experience Platform permite a estrutura de identificação comum dos principais serviços, soluções e atributos do cliente da Experience Cloud no serviço principal Pessoas.
seo-title: Visão geral do serviço de ID
title: Visão geral
uuid: null
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Visão geral

O Serviço de identidade da Experience Platform permite a estrutura de identificação comum dos principais serviços, soluções e atributos do cliente da Experience Cloud no serviço principal Pessoas. Isso funciona ao atribuir uma ID exclusiva e persistente para um visitante do site. Quando a organização implementa o serviço de ID, isso permite que você identifique o mesmo visitante do site e os dados em soluções diferentes da Experience Cloud.

![](assets/ecid.png)

Além disso, o serviço de ID pode substituir diferentes IDs específicas da solução (por exemplo, Analytics AID). E, por meio da [funcionalidade IDs do cliente e estados](/help/reference/authenticated-state.md) de autenticação, o serviço de ID permite que você passe suas IDs do cliente para a Experience Cloud. No entanto, lembre-se de que o serviço de ID funciona apenas com as soluções nas quais você já está inscrito. Ele não fornecerá acesso a outros produtos se você não tiver feito uma assinatura deles.

O serviço de ID é um componente integral de diversos recursos, aprimoramentos e serviços atuais e futuros da Experience Cloud. No momento, o serviço de ID oferece suporte ao [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), ao [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) e ao [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). É obrigatório se você deseja participar do Adobe Experience Cloud Device Co-op. Se você ainda não implementou o serviço de ID, agora é o momento de começar a pensar em uma estratégia de migração. Para obter mais informações sobre a importância e a função do serviço de ID, consulte [Por que o Serviço de identidade da plataforma de experiência deve estar em seu radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Resumo dos recursos

Resumindo, o serviço de ID:

* Cria uma chave ou ID comum que pode ser usada para vincular perfis e identidades.
* Identifica exclusivamente um dispositivo em várias soluções.
* Define um cookie primário no domínio do cliente para garantir o rastreamento no mesmo domínio. Consulte Experience Cloud.
* Recebe aliases e mapeamentos de ID de clientes e parceiros da Experience Cloud.
* Gerencia a sincronização de ID na Experience Cloud.
* Oferece suporte à sincronização de ID com terceiros diferentes no ecossistema de tecnologia de anúncios.

## Requisitos do serviço de ID

A solução e outras bibliotecas de código da Adobe devem atender a [específicos](/help/reference/requirements.md) para poder usar o serviço de ID.

* [Cookies e o Serviço de identidade da plataforma Experience Platform](cookies.md): O serviço de ID usa a ID da empresa, o cookie AMCV da Experience Cloud e um cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.
* [Como o serviço de identidade da plataforma Experience Platform solicita e define IDs](id-request.md): Uma visão geral do processo de resposta e solicitação de ID. Esses exemplos cobrem a atribuição de ID em sites individuais, em sites diferentes e para sites gerenciados por clientes diversos da Experience Cloud com suas próprias IDs da organização.
* [Noções básicas sobre sincronização de ID e taxas de correspondência](match-rates.md): Uma visão geral dos processos de sincronização de ID e taxas de correspondência no Serviço de identidade da plataforma Experience Platform, incluindo o Adobe Media Optimizer e o serviço de ID.