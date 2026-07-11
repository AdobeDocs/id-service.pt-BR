---
description: Lançamentos, atualizações ou alterações de recursos do Serviço de ID do visitante.
keywords: Serviço de ID de visitante
title: Notas de versão de 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
TQID: https://experienceleague.adobe.com/AB8VuYn9X41P9REJ8C215GzBRtH66lb35i-q1PNbZfU
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 110
ht-degree: 59%

---

# Notas de versão do Serviço de ID de visitante da Adobe - 2021

Lançamentos, atualizações ou alterações de recursos do Serviço de ID do visitante.

## Visitor 5.3.0

As atualizações a seguir foram incluídas na versão 5.3.0 do Visitor:

* Algoritmo atualizado para gerar ECID local.
* Aceitação mais recente com os sinalizadores `Secure` e `SameSite` para cookies de privacidade.
* Patch de correção para um problema do navegador Firefox quando uma página é carregada em um iFrame secundário.

## Visitor 5.2.0

As atualizações a seguir foram incluídas na versão 5.2.0 do Visitor:

* Esta versão apresenta um evento `onReceiveEcid`, que é chamado quando uma ECID é recebida do Serviço de ID do visitante. Por exemplo:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```

