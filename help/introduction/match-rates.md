---
description: Uma visão geral dos processos de sincronização de ID e taxas de correspondência no serviço da Experience Cloud ID, incluindo o Adobe Media Optimizer e o serviço de ID.
keywords: Serviço de ID
seo-description: Uma visão geral dos processos de sincronização de ID e taxas de correspondência no serviço da Experience Cloud ID, incluindo o Adobe Media Optimizer e o serviço de ID.
seo-title: Como entender a sincronização de ID e taxas de correspondência
title: Como entender a sincronização de ID e taxas de correspondência
uuid: 31 bd 655 f -2 b 9 e -4 f 8 d -9 a 1 f-e 81 a 6110 eda 8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Understanding ID synchronization and match rates{#understanding-id-synchronization-and-match-rates}

Uma visão geral dos processos de sincronização de ID e taxas de correspondência no serviço da Experience Cloud ID, incluindo o Adobe Media Optimizer e o serviço de ID.

## ID synchronization and match rates {#section-f652aae7234945e89d26dd833c5215fb}

A sincronização de ID relaciona IDs atribuídas pelo serviço de ID para IDs atribuídas aos visitantes do site pelos clientes. Por exemplo, considere que o serviço de ID atribuiu a ID de visitante 1234. Outra plataforma conhece o visitante pela ID 4321. O serviço de ID mapeia as IDs durante o processo de sincronização. Os resultados adicionam novos pontos de dados ao que os clientes conhecem sobre os visitantes do site. Além disso, se o serviço de ID não relacionar uma ID, ele cria uma nova e a usa para sincronizações futuras.

As taxas de correspondência avaliam e validam a eficácia do processo de sincronização de ID. As altas taxas de correspondência sugerem que um serviço específico será mais eficaz e fornecerá acesso a um público-alvo online maior do que um serviço com taxas de correspondência menores. A comparação entre taxas de correspondência é uma maneira quantificável de avaliar diferentes plataformas de anúncio integradas.

![](assets/idsync2.png)

**Garantia de altas taxas de correspondência**

To generate high match rates, it is important to set up the ID service properly (see the [standard implementation guide](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Uma implementação adequada ajuda a garantir altas taxas de correspondência, pois permite que o serviço de ID defina os cookies necessários para funcionar e sincronizar as IDs com parceiros de dados ativados. Entretanto, fatores como conexões lentas à Internet, coleta de dados de dispositivos móveis ou redes sem fio podem afetar o desempenho de coleta, sincronização e correspondência de IDs do serviço de ID. Essas variáveis do cliente estão além do controle do serviço de ID ou da [!DNL Adobe].

## ID synchronization process described {#section-a541a85cbbc74f5682824b1a2ee2a657}

O serviço de ID sincroniza as IDs em tempo real. Esse processo funciona no navegador em vez de uma transferência de dados de servidor para servidor. A tabela a seguir descreve as etapas no processo de sincronização de ID.

**Etapa 1: Carregar página**

When a visitor comes to your site and loads a page, the `Visitor.getInstance` function makes a [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) or JSON-P call to the ID service. O serviço de ID responde com um cookie que inclui a [!DNL Experience Cloud] ID (MID) do visitante. A MID é uma ID exclusiva atribuída a cada visitante do site. Consulte também a seção [Cookies e o serviço de Experience Cloud ID](../introduction/cookies.md).

**Etapa 2: carregar iFrame**

Enquanto o corpo da página é carregado, o serviço de ID carrega um iFrame chamado de *`Destination Publishing iFrame`*. [!DNL Destination Publishing iFrame] As cargas em um domínio separado da página principal. Esse design ajuda a garantir o desempenho da página e a melhorar a segurança, pois o iFrame:

* É carregado de modo assíncrono em relação à página pai. This means the parent page can load independently from the [!DNL Destination Publishing iFrame]. O carregamento do iFrame e dos pixels de sincronização de ID no iFrame não afeta a página pai ou a experiência do usuário.
* Carrega o mais rápido possível. Se for muito rápido, é possível carregar o iFrame depois do evento de carregamento de janela (não recomendado). Consulte [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) para obter mais detalhes.
* Impede que o código no iFrame acesse ou afete a página pai.

Consulte também a seção [Como o serviço da Experience Cloud ID solicita e define IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**Etapa 3: acionar sincronizações de ID**

A sincronização de ID é um URL acionado no iFrame de publicação de destino. Como mostrado no exemplo genérico, um URL de sincronização de ID contém o ponto de extremidade de sincronização de ID do parceiro e um URL de redirecionamento, ou seja, um redirecionamento para a [!DNL Adobe] que inclui a ID.

```
http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<
<varname>
  ADOBE_PARTNER_ID
</varname>>&dpuuid=<
<varname>
  PARTNER_UUID
</varname>>
```

Consulte também, [Sincronização de ID para transferências de dados de entrada](https://marketing.adobe.com/resources/help/en_US/aam/c_id_sync_in.html).

**Etapa 4: armazenamento de IDs**

IDs sincronizadas são armazenadas nos [servidores de borda e dados principais](https://marketing.adobe.com/resources/help/en_US/aam/c_compedge.html).

## Sync services manages ID synchronization {#section-cd5784d7ad404a24aa28ad4816a0119a}

The term *`Sync Services`* refers to internal [!DNL Experience Cloud] technologies responsible for ID synchronization. Esse serviço está ativado por padrão. Para desativá-lo, adicione uma [variável opcional](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) à função `Visitor.getInstance` do serviço de ID. Sync Services matches different [!DNL Experience Cloud] IDs such as:

* Third-party [!DNL Experience Cloud] cookie IDs to first-party [!DNL Experience Cloud] IDs.

* First-party [!DNL Experience Cloud] cookie IDs to [!DNL Adobe Media Optimizer] (AMO) IDs.

* IDs de cookies de terceiros da [!DNL Experience Cloud] para provedores de dados de terceiros e IDs da plataforma de direcionamento. Isso inclui serviços e plataformas, como provedores de dados, plataformas sob demanda e/ou de suprimento, redes de anúncios, trocas etc.
* First-party [!DNL Experience Cloud] cookie IDs to cross-device partner IDs.

## ID synchronization with Adobe Media Optimizer {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Media Optimizer] é uma exceção ao processo de sincronização de ID com base em quadros. Because [!DNL Media Optimizer] is a trusted domain, ID syncs take place from the parent page rather than in the [!DNL Destination Publishing iFrame]. During synchronization, the ID service calls [!DNL Media Optimizer] at `cm.eversttech.net`, which is a legacy domain name used by [!DNL Media Optimizer] prior to its acquisition by Adobe. O envio de dados para o [!DNL Media Optimizer] ajuda a melhorar as taxas de correspondência e é automático para clientes do serviço de ID que usam a versão 2.0 (ou posterior). Consulte também, [Cookies do Media Optimizer](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_media_optimizer.html).

>[!MORE_ LIKE_ THIS]
>
>* [Compreender as chamadas ao domínio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)

