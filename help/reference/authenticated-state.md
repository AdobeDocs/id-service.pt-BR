---
description: É possível associar outras IDs do cliente e um status de autenticação com cada visitante, juntamente com a ID de visitante da Experience Cloud.
keywords: Serviço de ID
seo-description: É possível associar outras IDs do cliente e um status de autenticação com cada visitante, juntamente com a ID de visitante da Experience Cloud.
seo-title: Estados de autenticação e IDs do cliente
title: Estados de autenticação e IDs do cliente
uuid: 643df363-224a-463e-a332-be59926b47e7
translation-type: ht
source-git-commit: 603540150edcdc76aacf407aeb6421c5b8386f56

---


# Estados de autenticação e IDs do cliente {#customer-ids-and-authentication-states}

É possível associar outras IDs do cliente e um status de autenticação com cada visitante, juntamente com a ID de visitante da Experience Cloud.

## Estados de autenticação {#section-68ad4065dfaa437d9070832d6e2bf85c}

O `setCustomerIDs` método aceita várias IDs do cliente para o mesmo visitante. Isso ajuda a identificar ou direcionar um usuário individual em diferentes dispositivos. Por exemplo, você pode fazer upload dessas IDs como [atributos do cliente](https://marketing.adobe.com/resources/help/pt_BR/mcloud/?f=attributes.html) para o [!DNL Experience Cloud] e acessar esses dados em diferentes soluções.

>[!IMPORTANT]
>
>`setCustomerIDs` (sincronização de ID do cliente) é exigida pelos atributos do cliente e pela funcionalidade dos serviços principais. Sincronização das IDs do cliente em um método de identificação opcional do [!DNL Analytics]. O [!DNL Target] requer `Visitor.AuthState.AUTHENTICATED` para que os Atributos do cliente funcionem. Consulte [Serviços principais - Como ativar as soluções](https://marketing.adobe.com/resources/help/pt_BR/mcloud/?f=core_services) para obter exemplos.

A partir do serviço de identidade da Experience Cloud v1.5+, `setCustomerIDs` inclui o objeto opcional `AuthState`. O `AuthState` identifica versões de acordo com seu status de autenticação (por exemplo, logon, logout). Você define o estado da autenticação com um valor de status listado na tabela. O status de autenticação é retornado como um número inteiro.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status de autenticação </th> 
   <th colname="col2" class="entry"> Número inteiro do status </th> 
   <th colname="col3" class="entry"> Status do usuário </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>Desconhecido ou nunca autenticado. </p> <p> Desconhecido se aplica por padrão quando o <span class="codeph">AuthState</span> não é usado com uma ID do visitante ou não é definido explicitamente em cada página de contexto do aplicativo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>Autenticado para uma instância, página ou aplicativo específico. </p> <p> <p>Atenção: para funcionar adequadamente, os Atributos do cliente do <span class="keyword">Target</span> exigem esse status. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">2</span> </p> </td> 
   <td colname="col3"> <p>Logout realizado. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Casos de uso para esados de autenticação {#section-fe9560cc490943b29dac2c4fb6efd72c}

É possível atribuir estados autenticação aos usuários, dependendo das ações que eles realizam nas suas propriedades da web e se estão autenticados ou não. Confira alguns exemplos na tabela abaixo:

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status de autenticação </th> 
   <th colname="col2" class="entry"> Caso de uso </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>Esse estado não pode ser usada para cenários como: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">Ler um email (essa ação geralmente significa que o leitor é o destinatário pretendido, mas o email também poderia ter sido encaminhado). </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">Clicar de um email para uma página de destino. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>O usuário está autenticado no momento com uma sessão ativa no seu site ou aplicativo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>O usuário foi autenticado, mas fez logout ativamente. O usuário quis se desconectar do estado autenticado. O usuário não deseja mais ser tratado como autenticado. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Definição das IDs do cliente e dos estados de autenticação {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

As IDs do cliente podem incluir combinações de IDs e estados de autenticação, conforme mostrado nos exemplos a seguir.

>[!IMPORTANT]
>
>* As IDs fazem distinção entre maiúsculas e minúsculas.
>* Use somente valores não codificados para as IDs.
>* Os estados de autenticação e as IDs de cliente não são armazenadas no cookie da ID do visitante. Eles devem ser definidos para cada página ou contexto de aplicativo.
>* Não inclua informações pessoais identificáveis (PII) nas IDs de cliente. Se você estiver usando PII para identificar um visitante (como um endereço de email), é recomendado armazenar uma versão com hash ou criptografada das informações. A biblioteca ECID fornece suporte para hash de identificadores de usuários. Consulte [Suporte a hash SHA 256 para setCustomerIDs](/help/reference/hashing-support.md).
>



```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Retorno das IDs do cliente e dos estados de autenticação {#section-71a610546188478fa9a3185a01d6e83b}

Use `getCustomerIDs` para retornar as IDs do cliente e os estados autenticados relacionados. Esse método retorna um estado autenticado do visitante como um número inteiro.

**Sintaxe**

`getCustomerIDs` retorna os dados com a seguinte sintaxe.

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**Exemplos**

Os dados de estados de autenticação e IDs do cliente retornados devem parecer com os exemplos a seguir.

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## Suporte do SDK {#section-861c6b3b1ba645dda133dccb22ec7bb0}

O serviço da [!DNL Experience Cloud] ID oferece suporte a diversas IDs e estados de autenticação do cliente em nosso código de SDK para Android e iOS. Consulte as seguintes bibliotecas de códigos:

* [Métodos do SDK para Android](https://marketing.adobe.com/resources/help/pt_BR/mobile/android/?f=c_marketing_cloud.html)
* [iOS SDK methods](https://marketing.adobe.com/resources/help/pt_BR/mobile/ios/?f=marketing_cloud.html)

## Aviso aos clientes do Analytics e do Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Caso esteja passando IDs declaradas para o [!DNL Audience Manager], o objeto `userid` precisa corresponder ao código de integração associado à fonte de dados. Para obter mais informações, consulte a seção [!UICONTROL Serviço de ID de visitante] na documentação [Configurar código regras de mesclagem](https://marketing.adobe.com/resources/help/pt_BR/aam/?f=merge-rules-configure-code.html).
