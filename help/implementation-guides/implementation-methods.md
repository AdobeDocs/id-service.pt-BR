---
description: Métodos de implementação padrão versus não padrão do Serviço de identidade da Experience Cloud.
keywords: Serviço de ID
title: Métodos de implementação
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
TQID: https://experienceleague.adobe.com/VcMKVPqOHJHqwX4CTYHeeQnqrEzwLLJ9xn2-e1vDr-k
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 141
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

