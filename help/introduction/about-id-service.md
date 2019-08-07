---
description: A função do Serviço de identidade da Experience Platform na Adobe Experience Cloud.
keywords: Serviço de ID
seo-description: A função do Serviço de identidade da Experience Platform na Adobe Experience Cloud.
seo-title: Sobre o serviço de ID
title: Visão geral
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Sobre o serviço de ID{#aboutidservice}

A função do Serviço de identidade da Experience Cloud na Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## The Experience Cloud Identity Service: A Foundational Element of Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

O Serviço de identidade da Experience Cloud permite a estrutura de identificação comum dos principais serviços, soluções e atributos do cliente e públicos-alvo da Experience Cloud. Isso funciona ao atribuir uma ID exclusiva e persistente para um visitante do site. Quando a organização implementa o serviço de ID, isso permite que você identifique o mesmo visitante do site e os dados em soluções diferentes da Experience Cloud.

![](assets/ecid.png)

Além disso, o serviço de ID pode substituir diferentes IDs específicas da solução (por exemplo, Analytics AID). E, através da funcionalidade de [IDs de cliente e Estados de autenticação](../reference/authenticated-state.md), o serviço de ID permite que você passe suas próprias IDs de cliente para a [!DNL Experience Cloud]. No entanto, lembre-se de que o serviço de ID funciona apenas com as soluções nas quais você já está inscrito. Ele não fornecerá acesso a outros produtos se você não tiver feito uma assinatura deles.

O serviço de ID é um componente integral de diversos recursos, aprimoramentos e serviços atuais e [!DNL Experience Cloud] futuros da. No momento, o serviço de ID oferece suporte ao [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), ao [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) e ao [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). É obrigatório se você deseja participar do [!DNL Adobe Experience Cloud] Device Co-op. Se você ainda não implementou o serviço de ID, agora é o momento de começar a pensar em uma estratégia de migração. For more information about the importance and role of the ID service, see [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Resumo dos recursos {#section-96555473455c4bf8924c2d56ff4f3255}

Resumindo, o serviço de ID:

* Cria uma chave ou ID comum que pode ser usada para vincular perfis e identidades.
* Identifica exclusivamente um dispositivo em várias soluções.
* Define um cookie primário no domínio do cliente para garantir o rastreamento no mesmo domínio. Consulte [Experience Cloud](../introduction/cookies.md).
* Recebe aliases e mapeamentos de ID de [!DNL Experience Cloud] clientes e parceiros da
* Gerencia a sincronização de ID na [!DNL Experience Cloud].
* Oferece suporte à sincronização de ID com terceiros diferentes no ecossistema de tecnologia de anúncios.
