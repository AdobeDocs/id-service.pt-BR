---
description: Métodos de implementação padrão ou não padrão do Serviço de identidade da Experience Cloud.
keywords: Serviço de ID
seo-description: Métodos de implementação padrão ou não padrão do Serviço de identidade da Experience Cloud.
seo-title: Métodos de implementação
title: Métodos de implementação
uuid: d41250e2-09f4-4a8b-8ade-54d43e9281c9
translation-type: tm+mt
source-git-commit: e75a448a2fa1c384c88f00648a6f868a886c6569

---


# Métodos de implementação

Você pode escolher um método de [!DNL Experience Cloud ID Service] implementação padrão usando [!DNL Experience Platform Launch], [!DNL Dynamic Tag Manager] (DTM) ou um método não padrão.

>[!IMPORTANT]
>
>Leia e entenda os [requisitos do serviço de ID](../reference/requirements.md) antes de começar a usar esses procedimentos.

## Implementação padrão {#section-ea1e5270f2184f85a2e85214a6ac60cb}

A Adobe recomenda usar [!DNL Experience Platform Launch](https://docs.adobe.com/content/help/en/launch/using/implement/solutions/idservice-save.html) para implementar o serviço de ID. Esse método garante a integração com outras [!DNL Experience Cloud] soluções, simplifica os fluxos de trabalho de implementação e garante automaticamente a inserção e o sequenciamento corretos do código.

## Implementações não padrão {#section-2c4f2db1f9704315a7cccab6d2e07113}

The procedures and code samples in this guide can help you set up the [!DNL Experience Cloud] ID service in a manual, or non-standard manner. Observe que essas implementações são frequentemente tecnicamente desafiadoras e complexas. Elas podem exigir recursos de engenharia ou consumir tempo de suporte contratado do consultor da Adobe.

>[!TIP]
>
>Como alternativa, você pode implementar o serviço de ID usando [!DNL Dynamic Tag Manager](https://docs.adobe.com/content/help/en/dtm/using/dtm-home.html). No entanto, novos clientes devem usar [!DNL Experience Platform Launch]. Para atualizar [!DNL Experience Platform Launch] de [!DNL Dynamic Tag Manager], consulte [Atualizar do DTM para o Launch](https://docs.adobe.com/content/help/en/launch/using/reference/upgrade/overview.html)).
