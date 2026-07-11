---
description: O Serviço de ID de visitante da Adobe permite a estrutura de identificação comum para aplicativos e serviços corporativos CX. Ele atribui uma ID exclusiva e persistente conhecida como ECID a um visitante do site.
keywords: Serviço de ID de visitante; ECID
title: Serviço de ID de visitante da Adobe
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 433
ht-degree: 26%

---

# Serviço de ID de visitante da Adobe {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

O Serviço de ID do Visitante é **não** o [Serviço de Identidade da Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=pt-BR). O Serviço de ID de visitante é a biblioteca JavaScript do `VisitorAPI.js` descrita neste guia que define a ECID para o Adobe Analytics, o Audience Manager e o Target. Se você estiver procurando o serviço Adobe Experience Platform que resolve identidades em dispositivos e sistemas em um perfil de cliente unificado, consulte a [Visão geral do serviço de identidade da Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=pt-BR).

>[!ENDSHADEBOX]

O Serviço de ID de visitante da Adobe permite a estrutura de identificação comum para aplicativos e serviços corporativos CX. Ele atribui uma ID exclusiva e persistente conhecida como ECID a um visitante do site.

## Compreensão dos principais elementos da identidade

Para entender melhor como o Adobe ajuda a identificar de forma exclusiva os visitantes e resolve as informações de identidade, leia o detalhamento abaixo:

* **Serviço de ID do Visitante**: o Serviço de ID do Visitante **é responsável pela configuração da ECID**. Para obter mais informações, leia a [visão geral do Serviço de ID de Visitante](./introduction/overview.md).
* **ECID**: a ECID é um namespace de identidade compartilhada usado em aplicativos Adobe Experience Platform e Adobe CX Enterprise para identificar pessoas e dispositivos. Para obter mais informações sobre a ECID, leia a [Visão geral da ECID](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid).
* **Serviço de identidade da Experience Platform**: o Serviço de identidade da Experience Platform fornece uma visão abrangente dos clientes e do comportamento deles ao unir as identidades de diferentes dispositivos e sistemas. Para obter mais informações, leia a [Visão geral do serviço de identidade da Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=pt-BR).

## Introdução

* [Visão geral do Serviço de ID de Visitante](introduction/overview.md): saiba o que o Serviço de ID de Visitante faz e como ele se encaixa no CX Enterprise.
* [Requisitos do Serviço de ID de Visitante](reference/requirements.md): confirme se suas soluções e bibliotecas de código atendem aos pré-requisitos antes de implementar o Serviço de ID de Visitante.
* [Métodos de implementação](implementation-guides/implementation-methods.md): compare a implementação padrão usando [marcas](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=pt-BR) com métodos de integração direta não padrão.

## Conheça a documentação

**Implementação**

* [Guias de implementação](implementation-guides/implementation-guides.md)
* [Integração direta com o Serviço de ID do visitante](implementation-guides/direct-integration.md)
* [Visão geral do serviço de Opt-in](implementation-guides/opt-in-service/optin-overview.md)
* [Teste e verifique o Serviço de ID do visitante](implementation-guides/test-verify.md)

**Referência da API**

* [Visão geral da API do serviço de ID do visitante](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**Perguntas frequentes**

* [Perguntas frequentes do Serviço de ID de visitante](faq-intro/faq.md)
* [Perguntas frequentes de outras soluções da CX Enterprise](faq-intro/other-faq.md)

## Recursos adicionais

* [Versões da biblioteca JavaScript da ECID](https://github.com/Adobe-Marketing-Cloud/id-service/releases) no GitHub
* [Notas de versão do Serviço de ID de visitante](release-notes/notes-2022.md)
* [Centro de privacidade da Adobe](http://www.adobe.com/br/privacy.html)
* [Documentação do Adobe CX Enterprise](https://experienceleague.adobe.com/docs/home.html?lang=pt-BR)

