---
description: setCustomerIDs define um ou mais pares de valor chave que definem as IDs do cliente e os estados de autenticação.
keywords: ID Service
seo-description: setCustomerIDs define um ou mais pares de valor chave que definem as IDs do cliente e os estados de autenticação.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
translation-type: tm+mt
source-git-commit: 21fb12b817b7c8cd34e6022ca6c188229228d1df
workflow-type: tm+mt
source-wordcount: '71'
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

