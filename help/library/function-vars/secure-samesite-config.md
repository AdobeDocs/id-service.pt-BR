---
description: Uma configuração no ECID que pode ser usada para dar suporte a cookies AMCV em páginas do Google AMP.
keywords: Serviço de ID
title: Configurações seguras e do SameSite
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '154'
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
