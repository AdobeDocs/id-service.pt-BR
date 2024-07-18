---
description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
keywords: Serviço de ID
title: Notas de versão de 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 100%

---

# Notas de versão do Serviço de identidade da Experience Cloud - 2021

Lançamentos, atualizações ou mudanças futuras do Serviço de identidade da Experience Cloud.

## Visitor 5.3.0

As atualizações a seguir foram incluídas na versão 5.3.0 do Visitor:

* Algoritmo atualizado para gerar ECID local.
* Aceitação mais recente com os sinalizadores `Secure` e `SameSite` para cookies de privacidade.
* Patch de correção para um problema do navegador Firefox quando uma página é carregada em um iFrame secundário.

## Visitor 5.2.0

As atualizações a seguir foram incluídas na versão 5.2.0 do Visitor:

* Esta versão introduz um evento `onReceiveEcid`, que é chamado quando uma ECID é recebida do Serviço de identidade. Por exemplo:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```
