---
description: Essa função foi projetada principalmente para clientes do A4T e tem como objetivo ajudar a solucionar problemas que podem surgir ao trabalhar com IDs em sites/telas ou aplicativos de uma única página.
keywords: Serviço de ID
seo-description: Essa função foi projetada principalmente para clientes do A4T e tem como objetivo ajudar a solucionar problemas que podem surgir ao trabalhar com IDs em sites/telas ou aplicativos de uma única página.
seo-title: resetState
title: resetState
uuid: ed 7 be 76 d-a 7 ee -4 e 51-b 26 c -456 ff 85 fd 096
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetState{#resetstate}

Essa função foi projetada principalmente para clientes do A4T e tem como objetivo ajudar a solucionar problemas que podem surgir ao trabalhar com IDs em sites/telas ou aplicativos de uma única página.

## Casos de uso {#section-840b88a5cdb042488b340cad5d7b22a5}

Como cliente A 4 T que usa o serviço de ID, você pode usar a `visitor.resetState()` função quando precisar:

* Passar uma ID de dados suplementares (SDID) ou qualquer outra ID de uma página ou tela para outra por um redirecionamento. Em geral, o serviço de ID não passará essa ID sem essa função.
* Use o código que atualiza somente seções específicas de uma página ou um aplicativo por chamadas do Ajax e você deseja rastrear essas ações. Por exemplo, considere que há uma página em que clicar em um objeto carrega ou altera apenas uma seção especial. Nesse caso, o serviço de ID não pode solicitar uma ID diferente exceto quando a página é recarregada. No entanto, com `visitor.resetState()`a opção, você pode solicitar uma nova ID nessas condições.

Consulte as amostras de código abaixo.

## Sintaxe {#section-9e63503e178f4be28ac850abf44d6d91}

**Sintaxe:**` visitor.resetState( *`state`*);`

## Amostras de código {#section-d75b211bb4ea473887eb284de2ad838b}

A implementação do serviço de ID afeta como você usaria essa função. Consulte a tabela abaixo para obter mais exemplos.

**Implementação do servidor**

Uma implementação do servidor é para clientes A 4 T com implementações mistas de servidor e cliente de [!DNL Target], [!DNL Analytics]e do serviço de ID. Se você configurou o serviço de ID com este método, tudo o que você precisa fazer é adicionar `visitor.resetState()` à página. As chamadas para o serviço de ID retornam uma nova ID e o estado do servidor automaticamente.

**Implementação não padrão** (com ID)

Se você configurou o serviço de ID com uma [implementação não padrão](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113), é necessário configurar um objeto de variável para manter a SDID (ou outras IDs) que você deseja passar com `visitor.resetState()`. Como mostrado abaixo, isso incluiria a[ ID da organização](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) e a ID que você deseja passar. O código pode ser semelhante ao seguinte exemplo.

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Implementação não padrão** (sem passar uma ID)

Nesse caso, `visitor.resetState()` pode ser usado para gerar uma nova ID. Isso pode ser útil em um aplicativo de página única quando um usuário navega para uma nova tela sem atualizar a página e você precisar de uma nova ID.

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**Gerenciador dinâmico de tags (DTM)**

No momento, não há um caminho de configuração do DTM para `visitor.resetState()`.
