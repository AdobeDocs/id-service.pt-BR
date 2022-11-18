---
description: Métodos de implementação padrão versus não padrão do Serviço de identidade da Experience Cloud.
keywords: Serviço de ID
title: Métodos de implementação
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: ht
source-wordcount: '136'
ht-degree: 100%

---

# Métodos de implementação

Você pode escolher um método de implementação [!DNL Experience Cloud ID Service] padrão usando [!DNL Experience Platform Launch] ou um método não padrão.

>[!IMPORTANT]
>
>Leia e entenda os [requisitos do serviço de ID](../reference/requirements.md) antes de começar a usar esses procedimentos.

## Implementação padrão {#section-ea1e5270f2184f85a2e85214a6ac60cb}

A Adobe recomenda usar o [[!DNL Experience Platform tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=pt-BR) para implementar o serviço de ID. Esse método garante a integração com outras soluções da [!DNL Experience Cloud], simplifica os fluxos de trabalho de implementação e garante automaticamente a inserção e o sequenciamento corretos do código.

## Implementações não padrão {#section-2c4f2db1f9704315a7cccab6d2e07113}

Os procedimentos e exemplos de código neste guia podem ajudar você a configurar o serviço de [!DNL Experience Cloud] ID de forma manual e não padrão. Observe que essas implementações são muitas vezes complexas e desafiadoras do ponto de vista técnico. Elas podem exigir recursos de engenharia que são insuficientes da sua parte ou consumir o tempo de suporte contratado do seu consultor da Adobe.
