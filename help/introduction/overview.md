---
description: A função do serviço de identidade da Experience Cloud na Adobe Experience Cloud.
title: Visão geral do serviço da Experience Cloud ID
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: 953a4932e581a7a0019bec354201be4bc39f8b6b
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 97%

---

# Visão geral do serviço da Experience Cloud ID

O [!UICONTROL serviço de identidade da Experience Cloud] permite a estrutura de identificação comum para as soluções da Experience Cloud (como atributos e públicos-alvo do cliente) no serviço de identidade da Experience Platform.

>[!NOTE]
>
> Você pode ver referências ao serviço de ID como acrônimos ou nomes antigos, como ECID, Serviço da Experience Cloud ID (MID) e Serviço de ID de visitante. Elas se referem ao [!UICONTROL serviço de identidade da Experience Cloud]. Você também pode ver o [!UICONTROL serviço de identidade da Experience Platform]. Para esclarecer:

* [!UICONTROL Serviço de identidade da Experience Platform]: o serviço que vincula as identidades. É o serviço de vinculação de dispositivos para o gerenciamento de experiências baseado em pessoas.
* [!UICONTROL Serviço de ID da Experience Cloud ID] (ECID): ID exclusiva e contínua designada a um visitante do site. É uma entidade específica que pode ser usada pelo Platform Identity Service.

Quando sua organização implementa o serviço de ID, essa ID permite identificar o mesmo visitante do site e seus dados em diferentes soluções da Experience Cloud.

![](assets/ecid-new.png)

Além disso, o serviço de ID pode substituir diferentes IDs específicas da solução (por exemplo, Analytics AID). E, através da funcionalidade de [IDs de cliente e Estados de autenticação](/help/reference/authenticated-state.md), o serviço de ID permite que você passe suas próprias IDs de cliente para a Experience Cloud. No entanto, lembre-se de que o serviço de ID funciona apenas com as soluções nas quais você já está inscrito. Ele não fornecerá acesso a outros produtos se você não estiver inscrito neles.

O serviço de ID é um componente integral de diversos recursos, aprimoramentos e serviços atuais e futuros da Experience Cloud. No momento, o serviço de ID oferece suporte ao [Analytics](http://www.adobe.com/br/marketing-cloud/web-analytics.html), ao [Audience Manager](http://www.adobe.com/br/marketing-cloud/data-management-platform.html) e ao [Target](http://www.adobe.com/br/marketing-cloud/testing-targeting.html). Se você ainda não implementou o serviço de ID, agora é o momento de começar a pensar em uma estratégia de migração.

## Resumo dos recursos

Resumindo, o serviço de ID:

* Cria uma chave comum ou ID que pode ser usada para vincular perfis e identidades.
* Identifica com exclusividade um dispositivo em várias soluções.
* Define um cookie próprio no domínio do cliente para garantir o rastreamento no mesmo domínio. Consulte o documento sobre [cookies e serviço de identidade da Experience Cloud](./cookies.md) para obter mais informações.
* Recebe aliases e mapeamentos de ID de clientes e parceiros da Experience Cloud.
* Gerencia a sincronização de ID na Experience Cloud.
* Oferece suporte à sincronização de ID com terceiros diferentes no ecossistema de tecnologia de anúncios.

## Requisitos do serviço de ID

A solução e outras bibliotecas de código da Adobe devem atender a [determinados requisitos](/help/reference/requirements.md) antes de poder usar o serviço de ID.

* [Cookies e o serviço de identidade da Experience Cloud](cookies.md): o serviço de ID usa a ID da organização, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.
* [Como o serviço de identidade da Experience Cloud solicita e define IDs](id-request.md): uma visão geral do processo de solicitação e resposta de ID. Esses exemplos cobrem a atribuição de ID em sites individuais, em sites diferentes e para sites gerenciados por clientes diversos da Experience Cloud com suas próprias IDs da organização.
* [Entendendo a sincronização de ID e as taxas de correspondência](match-rates.md): uma visão geral dos processos de sincronização de ID e taxas de correspondência no serviço de identidade da Experience Cloud, incluindo o Adobe Media Optimizer e o serviço de ID.
