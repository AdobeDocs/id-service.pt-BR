---
description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso das soluções da Experience Cloud com o serviço de ID.
keywords: ID Service
seo-description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso das soluções da Experience Cloud com o serviço de ID.
seo-title: Perguntas frequentes de outras soluções da Experience Cloud
title: Perguntas frequentes de outras soluções da Experience Cloud
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 77%

---


# Perguntas frequentes de outras soluções da Experience Cloud{#faqs-for-other-experience-cloud-solutions}

Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso das soluções da Experience Cloud com o serviço de ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Posso usar o Gerenciamento dinâmico de tags para implantar o serviço de ID do visitante?**

Sim, essa é a opção de implantação preferencial e recomendada.

See [Standard Implementation with DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics e Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**O histórico de visitas de um usuário poderá ser exportado do [!DNL Adobe Analytics] para o [!DNL Audience Manager] depois que eu implementar o serviço de identidade da Experience Cloud?**

Existem duas opções aqui:

* Se um usuário tiver uma atividade de visitação após a implementação do Serviço de ID, o visitante e seu histórico serão incluídos na exportação de dados para o [!DNL Audience Manager].
* Se um usuário não tiver uma atividade de visitação após a implementação do Serviço de ID, o visitante e seu histórico não serão incluídos na exportação de dados para o Audience Manager. Como a nova atividade não está presente, não temos como associar a ID do Analytics à ID do Experience Cloud.

