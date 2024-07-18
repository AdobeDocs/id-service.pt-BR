---
description: A função do serviço de identidade da Experience Cloud na Adobe Experience Cloud.
title: Visão geral do Serviço de identidade da Experience Cloud
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 100%

---

# Visão geral do Serviço de identidade da Experience Cloud

O Serviço de identidade da Experience Cloud ativa a estrutura de identificação comum para os serviços de aplicativos da Experience Cloud. Você pode usar o Serviço de identidade da Experience Cloud para definir a [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=pt-BR).

A ECID é um namespace de identidade compartilhada usado em aplicativos da Adobe Experience Platform e Experience Cloud para rastrear o comportamento do visitante e garantir que cada dispositivo tenha um identificador exclusivo que possa ser mantido em várias sessões.

>[!TIP]
>
>O Serviço de identidade da Experience Cloud, da Experience Platform e a ECID são três entidades **diferentes**.

O Serviço de identidade da Experience Cloud pode substituir diferentes IDs específicas do aplicativo e usar a funcionalidade [IDs de cliente e Estados de autenticação](/help/reference/authenticated-state.md) para permitir que você transmita suas próprias IDs de cliente para a Experience Cloud.

>[!NOTE]
>
>O Serviço de identidade da Experience Cloud só funciona com os serviços de aplicativos da Experience Cloud nos quais você está inscrito e não fornece acesso a outros serviços de aplicativos se você não estiver inscrito neles.

O Serviço de identidade da Experience Cloud é compatível com os seguintes aplicativos:

* [Adobe Analytics](https://business.adobe.com/br/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/br/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/br/products/target/adobe-target.html)

O serviço de ID é um componente integral de diversos recursos, aprimoramentos e serviços atuais e futuros da Experience Cloud. No momento, o serviço de ID oferece suporte ao [Analytics](http://www.adobe.com/br/marketing-cloud/web-analytics.html), ao [Audience Manager](http://www.adobe.com/br/marketing-cloud/data-management-platform.html) e ao [Target](http://www.adobe.com/br/marketing-cloud/testing-targeting.html). Se você ainda não implementou o serviço de ID, agora é o momento de começar a pensar em uma estratégia de migração.

## Resumo dos recursos

Em resumo, o Serviço de identidade da Experience Cloud ajuda a:

* Identificar exclusivamente um visitante em um dispositivo em vários aplicativos.
* Define um cookie primário no domínio do cliente para garantir o rastreamento no mesmo domínio. Consulte o documento sobre [cookies e serviço de identidade da Experience Cloud](./cookies.md) para obter mais informações.
* Recebe aliases e mapeamentos de ID de clientes e parceiros da Experience Cloud.
* Gerencia a sincronização de ID na Experience Cloud.
* Oferece suporte à sincronização de ID com terceiros diferentes no ecossistema de tecnologia de anúncios.

## Requisitos do Serviço de identidade da Experience Cloud

Sua solução e outras bibliotecas de código da Adobe devem atender a [certos requisitos](/help/reference/requirements.md) antes de você poder usar o Serviço de identidade.

* [Cookies e o Serviço de identidade da Experience Cloud](cookies.md): o Serviço de identidade da Experience Cloud usa a ID da sua organização, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o Serviço de identidade rastreie os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.
* [Como o serviço de identidade da Experience Cloud solicita e define IDs](id-request.md): uma visão geral do processo de solicitação e resposta de ID. Esses exemplos cobrem a atribuição de ID em sites individuais, em sites diferentes e para sites gerenciados por clientes diversos da Experience Cloud com suas próprias IDs da organização.
* [Entendendo a sincronização de ID e taxas de correspondência](match-rates.md): uma visão geral dos processos de sincronização de ID e taxas de correspondência no Serviço de identidade da Experience Cloud, incluindo o Adobe Media Optimizer e o Serviço de identidade.
