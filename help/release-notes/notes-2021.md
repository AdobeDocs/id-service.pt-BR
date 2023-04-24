---
description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
keywords: Serviço de ID
title: Notas de versão de 2021
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 25%

---

# Notas de versão do Experience Cloud Identity Service - 2021

Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.

## Visitante 5.3.0

As atualizações a seguir foram incluídas na versão 5.3.0 do Visitante:

* Algoritmo atualizado para gerar ECID local.
* Aceitação mais recente com `Secure` e `SameSite` sinalizadores para cookie de privacidade.
* Correção de patch para um problema do navegador Firefox quando uma página é carregada em um iFrame secundário.

## Visitante 5.2.0

As atualizações a seguir foram incluídas na versão 5.2.0 do Visitante:

* Esta versão introduz um evento `onRecieveEcid`, que é chamada quando uma ECID é recebida do Serviço de identidade. Por exemplo:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
