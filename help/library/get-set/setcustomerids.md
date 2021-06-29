---
description: setCustomerIDs define um ou mais pares de valor chave que definem as IDs do cliente e os estados de autenticação.
keywords: Serviço de ID
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '58'
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
