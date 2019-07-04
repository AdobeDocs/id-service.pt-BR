---
description: setCustomerIDs define um ou mais pares de valor chave que definem as IDs do cliente e os estados de autenticação.
keywords: Serviço de ID
seo-description: setCustomerIDs define um ou mais pares de valor chave que definem as IDs do cliente e os estados de autenticação.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs define um ou mais pares de valor chave que definem as IDs do cliente e os estados de autenticação.

**Sintaxe:** `visitor.setCustomerIDs()`

É possível definir IDs múltiplas ou únicas conforme exemplificado na amostra de código abaixo. Consulte [Estados de autenticação e IDs do cliente](../../mcvid-reference/mcvid-authenticated-state.md) para obter mais informações e exemplos.

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
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

