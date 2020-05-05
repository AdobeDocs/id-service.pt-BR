---
description: Uma visão geral dos processos de sincronização de ID e taxas de correspondência no serviço de identidade da Experience Cloud, incluindo o Adobe Media Optimizer e o serviço de ID.
keywords: ID Service
seo-description: Uma visão geral dos processos de sincronização de ID e taxas de correspondência no serviço de identidade da Experience Cloud, incluindo o Adobe Media Optimizer e o serviço de ID.
seo-title: Como entender a sincronização de ID e taxas de correspondência
title: Como entender a sincronização de ID e taxas de correspondência
uuid: 31bd655f-2b9e-4f8d-9a1f-e81a6110eda8
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Como entender a sincronização de ID e as taxas de correspondência{#understanding-id-synchronization-and-match-rates}

Uma visão geral dos processos de sincronização de ID e taxas de correspondência no serviço de identidade da Experience Cloud, incluindo o Adobe Media Optimizer e o serviço de ID.

## Sincronização de ID e taxas de correspondência {#section-f652aae7234945e89d26dd833c5215fb}

A sincronização de ID corresponde IDs atribuídas pelo serviço de ID às IDs atribuídas aos visitantes do site pelos clientes. Por exemplo, considere que o serviço de ID atribuiu uma ID de visitante 1234. Outra plataforma conhece esse visitante pela ID 4321. O serviço de ID mapeia essas IDs em conjunto durante o processo de sincronização. Os resultados adicionam novos pontos de dados ao que nossos clientes sabem sobre os visitantes do site. E, se o serviço de ID não corresponder a uma ID, ele criará uma nova ID e a usará para sincronização futura.

As taxas de correspondência avaliam e validam a eficácia do processo de sincronização de ID. As altas taxas de correspondência sugerem que um serviço específico será mais eficiente e fornecerá acesso a uma audiência on-line maior do que um serviço com taxas de correspondência baixas. A comparação das taxas de correspondência é uma maneira quantificável de avaliar diferentes plataformas de anúncio integradas.

![](assets/idsync2.png)

**Garantia de altas taxas de correspondência**

Para gerar altas taxas de correspondência, é importante configurar o serviço de ID adequadamente (consulte [o guia de implementação padrão](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Uma implementação adequada ajuda a garantir altas taxas de correspondência, pois permite que o serviço de ID defina os cookies necessários para funcionar e sincronizar IDs com parceiros de dados habilitados. No entanto, fatores como conexões lentas com a Internet, coleta de dados de dispositivos móveis ou redes sem fio podem afetar o modo como o serviço de ID coleta, sincroniza e corresponde IDs. Essas variáveis do lado do cliente estão além do controle do serviço de ID ou da [!DNL Adobe].

## Descrição do processo de sincronização de ID {#section-a541a85cbbc74f5682824b1a2ee2a657}

O serviço de ID sincroniza IDs em tempo real. Esse processo funciona no navegador em vez de uma transferência de dados de servidor para servidor. A tabela a seguir descreve as etapas no processo de sincronização de ID.

**Etapa 1: carregar a página**

Quando um visitante entra no site e carrega uma página, a função `Visitor.getInstance` faz uma chamada [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) ou JSON-P para o serviço de ID. O serviço de ID responde com um cookie que inclui a [!DNL Experience Cloud] ID (MID) do visitante. A MID é uma ID exclusiva atribuída a cada visitante do site. Consulte [Cookies e o serviço de identidade da Experience Cloud](../introduction/cookies.md).

**Etapa 2: carregar iFrame**

Enquanto o corpo da página é carregado, o serviço de ID carrega um iFrame chamado de *`Destination Publishing iFrame`*. The [!UICONTROL Destination Publishing iFrame] loads in a domain separate from the parent page. Esse design ajuda a garantir o desempenho da página e melhora a segurança, pois o iFrame:

* Carrega de forma assíncrona em relação à página pai. This means the parent page can load independently from the [!UICONTROL Destination Publishing iFrame]. O carregamento do iFrame e dos pixels de sincronização de ID no iFrame não afeta a página pai nem a experiência do usuário.
* Carrega o mais rápido possível. Se isso for muito rápido, é possível carregar o iFrame após o evento de carregamento da janela (não recomendado). See [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) for details.
* Impede que o código no iFrame tenha acesso à página pai ou afete a mesma.

See also, [How the Experience Cloud Identity Service Requests and Sets IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**Etapa 3: Sincronizações de ID de fogo**

A sincronização de ID é um URL acionado no iFrame de publicação de destino. Como mostrado no exemplo genérico, um URL de sincronização de ID contém o ponto de extremidade de sincronização de ID do parceiro e um URL de redirecionamento, ou seja, um redirecionamento para a [!DNL Adobe] que inclui a ID.

`http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<ADOBE_PARTNER_ID>&dpuuid=<PARTNER_UUID>`

Consulte também, [Sincronização de ID para transferências de dados de entrada](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/implementation-integration-guides/sending-audience-data/batch-data-transfer-process/id-sync-http.html).

**Etapa 4: armazenamento de IDs**

Synchronized IDs are stored on the [edge and core data servers](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/system-components/components-edge.html).

## Serviços de sincronização gerenciam a sincronização da ID {#section-cd5784d7ad404a24aa28ad4816a0119a}

O termo *`Sync Services`* se refere às [!DNL Experience Cloud] tecnologias internas responsáveis pela sincronização de ID. Esse serviço está ativado por padrão. Para desativá-lo, adicione uma [variável opcional](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) à função `Visitor.getInstance` do serviço de ID. Os Serviços de sincronização corresponde diferentes [!DNL Experience Cloud] IDs como:

* IDs de [!DNL Experience Cloud] cookies de terceiros da para [!DNL Experience Cloud] IDs primárias.

* IDs de [!DNL Experience Cloud] cookie primários da para IDs do [!DNL Adobe Media Optimizer] (AMO).

* IDs de cookies de terceiros da [!DNL Experience Cloud] para provedores de dados de terceiros e IDs da plataforma de direcionamento. Isso inclui serviços e plataformas, como provedores de dados, plataformas sob demanda e/ou de suprimento, redes de anúncios, trocas etc.
* IDs de [!DNL Experience Cloud] cookie primário da para IDs de parceiros de vários dispositivos.

## Sincronização de ID com a Adobe Advertising Cloud {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Advertising Cloud] (anteriormente chamado [!DNL Adobe Media Optimizer]) é uma exceção ao processo de sincronização de ID baseado em iFrame. Como o [!DNL Advertising Cloud] é um domínio confiável, as sincronizações de ID ocorrem de uma página principal em vez de um [!UICONTROL iFrame de publicação de destino]. Durante a sincronização, o serviço de ID chama o [!DNL Advertising Cloud] em `cm.eversttech.net`, que é um nome de domínio herdado usado pelo [!DNL Advertising Cloud] antes da aquisição pela Adobe. O envio de dados para o [!DNL Advertising Cloud] ajuda a melhorar as taxas de correspondência e é automático para clientes do serviço de ID que usam a versão 2.0 (ou posterior). Consulte também Cookies [da](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-advertising-cloud.html)Advertising Cloud.

>[!MORELIKETHIS]
>
>* [Compreender as chamadas ao domínio Demdex](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/reference/demdex-calls.html)

