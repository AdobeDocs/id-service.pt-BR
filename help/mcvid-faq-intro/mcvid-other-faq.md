---
description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso das soluções da Experience Cloud com o serviço de ID.
keywords: Serviço de ID
seo-description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso das soluções da Experience Cloud com o serviço de ID.
seo-title: Perguntas frequentes para outras soluções da Experience Cloud
title: Perguntas frequentes para outras soluções da Experience Cloud
uuid: 7 d 848663-6 cbb -4 d 80-ab 06-7 b 6 d 2 dc 20 e 2 b
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Perguntas frequentes para outras soluções da Experience Cloud{#faqs-for-other-experience-cloud-solutions}

Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso das soluções da Experience Cloud com o serviço de ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Posso usar o Dynamic Tag Management para implantar o serviço de ID de visitante?**

Sim, essa é a opção de implantação preferencial e recomendada.

Consulte [Implementação padrão com DTM](../mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics e Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**O histórico de visitas de um usuário poderá ser exportado do[!DNL Adobe Analytics]para o[!DNL Audience Manager]depois que eu implementar o serviço da Experience Cloud ID?**

Existem duas opções aqui:

* Se um usuário tiver uma atividade de visitação após a implementação do Serviço de ID, o visitante e seu histórico serão incluídos na exportação de dados para o [!DNL Audience Manager].
* Se um usuário não tiver uma atividade de visitação após a implementação do Serviço de ID, o visitante e seu histórico não serão incluídos na exportação de dados para o Audience Manager. Como a nova atividade não está presente, não há como associar a Analytics ID com a Experience Cloud ID.

