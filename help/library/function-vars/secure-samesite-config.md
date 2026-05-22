---
description: Uma configuração no ECID que pode ser usada para dar suporte a cookies AMCV em páginas do Google AMP.
keywords: Serviço de ID
title: Configurações seguras e do SameSite
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 156
ht-degree: 100%

---

# Configurações seguras e do SameSite

Essa configuração permite alterar as configurações dos cookies e dar suporte a [cookies AMCV](../../introduction/cookies.md) nas páginas do Google AMP.

O serviço de ID de visitante da Adobe define cookies ECID com a configuração padrão do navegador do `SameSite = Lax`, que será inacessível se a página for carregada em um iframe como uma página do Google AMP. Para acessar cookies ECID, use as configurações abaixo para atualizar a configuração do SameSite para `SameSite = None`.

>[!NOTE]
>
>Ao ser aplicada a configuração `SameSite = None`, os cookies devem ser definidos como `Secure`, para que os dados só possam ser transmitidos por meio de conexões HTTPS.

**Implementação**:

Se você estiver usando o Adobe Experience Platform Launch, atualize a extensão da Experience Cloud ID para a versão 5.1.0 e configure `secureCookie: true` e `sameSiteCookie: none`.

Se você não estiver usando o Experience Platform Launch, atualize para a biblioteca do Visitante 5.1.0 mais recente e siga as configurações abaixo ao inicializar a instância do Visitante:

**Amostra de código**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```

