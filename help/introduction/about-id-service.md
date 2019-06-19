---
description: A função do Serviço de identidade da Experience Platform na Adobe Experience Cloud.
keywords: Serviço de ID
seo-description: A função do Serviço de identidade da Experience Platform na Adobe Experience Cloud.
seo-title: Sobre o serviço de ID
title: Visão geral
uuid: c 52 d 6155-00 a 0-4 fc 5-9 d 8 e -5 ce 00 b 8 d 01 e 6
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Sobre o serviço de ID{#aboutidservice}

A função do Serviço de identidade da Experience Platform na Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## O Serviço de identidade da Experience Platform: Um elemento essencial dos principais serviços {#section-2de0eb1d65664e92a4d8bbb167b84bde}

O Serviço de identidade da Experience Platform permite a estrutura de identificação comum dos principais serviços, soluções e atributos do cliente da Experience Cloud no serviço principal Pessoas. Isso funciona ao atribuir uma ID exclusiva e persistente para um visitante do site. Quando a organização implementa o serviço de ID, isso permite que você identifique o mesmo visitante do site e os dados em soluções diferentes da Experience Cloud.

![](assets/ecid.png)

Além disso, o serviço de ID pode substituir diferentes IDs específicas da solução (por exemplo, Analytics AID). E, por meio da [funcionalidade IDs do cliente e estados](../reference/authenticated-state.md) de autenticação, o serviço de ID permite que você passe suas próprias IDs do cliente para o [!DNL Experience Cloud]. No entanto, lembre-se de que o serviço de ID funciona apenas com as soluções nas quais você já está inscrito. Ele não fornecerá acesso a outros produtos se você não tiver feito uma assinatura deles.

O serviço de ID é um componente integral de diversos recursos, aprimoramentos e serviços atuais e futuros da [!DNL Experience Cloud]. No momento, o serviço de ID oferece suporte ao [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), ao [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) e ao [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). É obrigatório se você deseja participar do [!DNL Adobe Experience Cloud] Device Co-op. Se você ainda não implementou o serviço de ID, agora é o momento de começar a pensar em uma estratégia de migração. Para obter mais informações sobre a importância e a função do serviço de ID, consulte [Por que o Serviço de identidade da plataforma de experiência deve estar em seu radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Resumo dos recursos {#section-96555473455c4bf8924c2d56ff4f3255}

Resumindo, o serviço de ID:

* Cria uma chave ou ID comum que pode ser usada para vincular perfis e identidades.
* Identifica exclusivamente um dispositivo em várias soluções.
* Define um cookie primário no domínio do cliente para garantir o rastreamento no mesmo domínio. Consulte [Experience Cloud](../introduction/cookies.md).
* Recebe aliases e mapeamentos de ID de clientes e parceiros da [!DNL Experience Cloud].
* Gerencia a sincronização de ID dentro [!DNL Experience Cloud]do.
* Oferece suporte à sincronização de ID com terceiros diferentes no ecossistema de tecnologia de anúncios.
