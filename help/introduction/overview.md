---
description: A função do serviço de identidade da Experience Cloud na Adobe Experience Cloud.
seo-description: O serviço de identidade da Experience Cloud permite a estrutura de identificação comum para os serviços, as soluções e os atributos e públicos-alvo do cliente da Experience Cloud.
seo-title: Visão geral do serviço de ID
title: Visão geral
uuid: null
translation-type: tm+mt
source-git-commit: 6c314656c134a697540c289560c67ca3ab88bc63

---


# Visão geral

O Serviço de identidade da Experience Cloud permite a estrutura de identificação comum para os principais serviços, soluções e atributos e públicos-alvo do cliente da Experience Cloud no Serviço de identificação da plataforma. (Você pode ver referências a nomes ou acrônicos antigos, como Serviço da Experience Cloud ID, ECID, Serviço da Marketing Cloud ID, MID e Serviço de ID de visitante). O serviço de identidade funciona ao atribuir uma ID exclusiva e persistente para um visitante do site. Quando a organização implementa o serviço de ID, isso permite que você identifique o mesmo visitante do site e os dados em soluções diferentes da Experience Cloud.

![](assets/ecid.png)

Além disso, o serviço de ID pode substituir diferentes IDs específicas da solução (por exemplo, Analytics AID). E, através da funcionalidade de [IDs de cliente e Estados de autenticação](/help/reference/authenticated-state.md), o serviço de ID permite que você passe suas próprias IDs de cliente para a Experience Cloud. No entanto, lembre-se de que o serviço de ID funciona apenas com as soluções nas quais você já está inscrito. Ele não fornecerá acesso a outros produtos se você não tiver feito uma assinatura deles.

O serviço de ID é um componente integral de diversos recursos, aprimoramentos e serviços atuais e futuros da Experience Cloud. No momento, o serviço de ID oferece suporte ao [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), ao [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) e ao [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). É obrigatório se você deseja participar do Adobe Experience Cloud Device Co-op. Se você ainda não implementou o serviço de ID, agora é o momento de começar a pensar em uma estratégia de migração. Para obter mais informações sobre a importância e a função do serviço de identidade, consulte [Por que você deve prestar atenção no serviço de identidade da Experience Cloud](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Resumo dos recursos

Resumindo, o serviço de ID:

* Cria uma chave ou ID comum que pode ser usada para vincular perfis e identidades.
* Identifica exclusivamente um dispositivo em várias soluções.
* Define um cookie primário no domínio do cliente para garantir o rastreamento no mesmo domínio. Consulte Experience Cloud.
* Recebe aliases e mapeamentos de ID de clientes e parceiros da Experience Cloud.
* Gerencia a sincronização de ID na Experience Cloud.
* Oferece suporte à sincronização de ID com terceiros diferentes no ecossistema de tecnologia de anúncios.

## Requisitos do serviço de ID

A solução e outras bibliotecas de código da Adobe devem atender a [determinados requisitos](/help/reference/requirements.md) antes de poder usar o serviço de ID.

* [Cookies e o serviço de identidade da Experience Cloud](cookies.md): o serviço de ID usa a ID da organização, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.
* [Como o serviço de identidade da Experience Cloud solicita e define IDs](id-request.md): uma visão geral do processo de solicitação e resposta de ID. Esses exemplos cobrem a atribuição de ID em sites individuais, em sites diferentes e para sites gerenciados por clientes diversos da Experience Cloud com suas próprias IDs da organização.
* [Entendendo a sincronização de ID e as taxas de correspondência](match-rates.md): uma visão geral dos processos de sincronização de ID e taxas de correspondência no serviço de identidade da Experience Cloud, incluindo o Adobe Media Optimizer e o serviço de ID.