---
description: A função do Serviço de ID de visitante no Adobe CX Enterprise.
title: Visão geral do serviço de ID de visitante da Adobe
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 18%

---

# Visão geral do serviço de ID de visitante da Adobe

O Adobe Visitor ID Service habilita a estrutura de identificação comum para os CX Enterprise Application Services. Você pode usar o Serviço de ID de visitante para definir a [ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=pt-BR).

A ECID é um namespace de identidade compartilhada usado em aplicativos Adobe Experience Platform e CX Enterprise para rastrear o comportamento do visitante e garantir que cada dispositivo tenha um identificador exclusivo que possa persistir em várias sessões.

>[!TIP]
>
>O Serviço de ID de visitante, o Serviço de identidade da Experience Platform e a ECID são três entidades **diferentes**.

O Serviço de ID de visitante pode substituir diferentes IDs específicas do aplicativo e usar a funcionalidade [IDs de cliente e Estados de autenticação](/help/reference/authenticated-state.md) para permitir que você passe suas próprias IDs de cliente para o CX Enterprise.

>[!NOTE]
>
>O Serviço de ID de visitante só funciona com os CX Enterprise Application Services aos quais você está inscrito e não fornecerá acesso a outros serviços de aplicativos se você não estiver inscrito neles.

O Serviço de ID de visitante é compatível com os seguintes aplicativos:

* [Adobe Analytics](https://business.adobe.com/br/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/br/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/br/products/target/adobe-target.html)

O Serviço de ID de visitante é um componente integral de vários recursos, aprimoramentos e serviços atuais e futuros do CX Enterprise. Atualmente, o Serviço de ID de Visitante oferece suporte ao [Analytics](http://www.adobe.com/br/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/br/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/br/marketing-cloud/testing-targeting.html). Se você não implementou o Serviço de ID de visitante, agora é o momento de começar a considerar uma estratégia de migração.

## Resumo dos recursos

Em resumo, o Serviço de ID de visitante ajuda a:

* Identificar exclusivamente um visitante em um dispositivo em vários aplicativos.
* Define um cookie primário no domínio do cliente para garantir o rastreamento no mesmo domínio. Consulte o documento sobre [cookies e o Serviço de ID de Visitante](./cookies.md) para obter mais informações.
* Recebe aliases e mapeamentos de ID de clientes e parceiros da CX Enterprise.
* Gerencia a sincronização de ID no CX Enterprise.
* Oferece suporte à sincronização de ID com terceiros diferentes no ecossistema de tecnologia de anúncios.

## Requisitos do Serviço de ID de visitante

Sua solução e outras bibliotecas de código da Adobe devem atender a [certos requisitos](/help/reference/requirements.md) antes de você poder usar o Serviço de ID de Visitante.

* [Cookies e o Serviço de ID do visitante](cookies.md): o Serviço de ID do visitante usa a ID da organização IMS, o cookie AMCV da CX Enterprise e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o Serviço de ID do visitante rastreie visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da CX Enterprise.
* [Como o Serviço de ID do Visitante solicita e define IDs](id-request.md): uma visão geral do processo de solicitação e resposta de ID. Esses exemplos cobrem a atribuição de ID em sites individuais, em sites diferentes e para sites gerenciados por clientes do CX Enterprise com suas próprias IDs da organização IMS.
* [Entendendo a sincronização de ID e as taxas de correspondência](match-rates.md): uma visão geral dos processos de sincronização de ID e taxas de correspondência no Serviço de ID do visitante, incluindo o Adobe Media Otimizer e o Serviço de ID do visitante.

