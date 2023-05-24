---
description: Lançamentos, atualizações ou mudanças futuras do serviço de identidade da Experience Cloud.
keywords: Serviço de ID
title: Notas de versão de 2021
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
source-git-commit: fcd3e8b65bb84e94eabac7ffec6a34f4cf75ec3d
workflow-type: tm+mt
source-wordcount: '103'
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

* Esta versão introduz um evento `onRecieveEcid`, que é chamado quando uma ECID é recebida do Serviço de identidade. Por exemplo:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
