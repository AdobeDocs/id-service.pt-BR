---
description: setCustomerIDs define um ou mais pares de valor chave que definem as IDs do cliente e os estados de autenticação.
keywords: Serviço de ID
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 100%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs define um ou mais pares de valor chave que definem as IDs do cliente e os estados de autenticação.

**Sintaxe:** `visitor.setCustomerIDs()`

É possível definir IDs múltiplas ou únicas conforme exemplificado na amostra de código abaixo. Consulte [IDs do cliente e estados de autenticação](../../reference/authenticated-state.md) para obter mais informações e exemplos.

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

