---
description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso das soluções da Experience Cloud com o serviço de ID.
keywords: Serviço de ID
title: Perguntas frequentes de outras soluções da Experience Cloud
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '186'
ht-degree: 100%

---

# Perguntas frequentes de outras soluções da Experience Cloud {#faqs-for-other-experience-cloud-solutions}

Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso das soluções da Experience Cloud com o serviço de ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Posso usar o Dynamic Tag Management para implantar o serviço de ID de visitante?**

Sim, essa é a opção de implantação preferencial e recomendada.

Consulte [implementação padrão com o DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics e Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**O histórico de visitas de um usuário poderá ser exportado do [!DNL Adobe Analytics] para o [!DNL Audience Manager] depois que eu implementar o serviço de identidade da Experience Cloud?**

Existem duas opções aqui:

* Se um usuário tiver uma atividade de visitação após a implementação do Serviço de ID, o visitante e seu histórico serão incluídos na exportação de dados para o [!DNL Audience Manager].
* Se um usuário não tiver uma atividade de visitação após a implementação do Serviço de ID, o visitante e seu histórico não serão incluídos na exportação de dados para o Audience Manager. Como a nova atividade não está presente, não temos como associar a ID do Analytics à Experience Cloud ID.
