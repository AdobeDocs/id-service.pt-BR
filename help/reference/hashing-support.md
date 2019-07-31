---
description: O serviço da Experience Cloud ID (ECID) é compatível com o algoritmo de hash SHA -256 que permite transmitir IDs do cliente ou endereços de email e enviar IDs com hash. Este é um método opcional Javascript para enviar identificadores com hash à Experience Cloud. Você pode continuar a usar seus próprios métodos de hash antes de enviar IDs do cliente.
keywords: Serviço de ID
seo-description: O serviço da Experience Cloud ID (ECID) é compatível com o algoritmo de hash SHA -256 que permite transmitir IDs do cliente ou endereços de email e enviar IDs com hash. Este é um método opcional Javascript para enviar identificadores com hash à Experience Cloud. Você pode continuar a usar seus próprios métodos de hash antes de enviar IDs do cliente.
seo-title: SHA 256 Hashing Support for setcustomerids
title: SHA 256 Hashing Support for setcustomerids
translation-type: tm+mt
source-git-commit: 0311d57391a0a9d5ac5a0bba255ca71bdffd67c0

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

O serviço da Experience Cloud ID (ECID) é compatível com o algoritmo de hash SHA -256 que permite transmitir IDs do cliente ou endereços de email e enviar IDs com hash. Este é um método opcional Javascript para enviar identificadores com hash à Experience Cloud. Você pode continuar a usar seus próprios métodos de hash antes de enviar IDs do cliente.
Há duas maneiras de implementar o suporte de hash com setcustomerids, conforme descrito nas seções abaixo:

* Use o método setcustomerids na ECID
* Adicionar uma ação na Adobe Experience Platform Launch

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

Antes de hash, a biblioteca ECID realiza normalização de dados em customerids. Esse processo elimina os espaços em branco das customerids e converte todos os caracteres a minúsculas. Por exemplo, no caso de endereços de email: " ecid@adobe.com "torna-se" ecid@adobe.com "

Consulte abaixo um exemplo de código de como você define uma única ID do cliente (o endereço de email mencionado acima) com hash SHA -256.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

É possível associar outras IDs do cliente, status de autenticação e tipo de hash (SHA -256) a cada visitante juntamente com a ID de visitante da Experience Cloud. Se não fornecer nenhum tipo de hash, ele será considerado como nenhum hash.

O `setCustomerIDs` método aceita várias IDs do cliente para o mesmo visitante. Isso ajuda a identificar ou direcionar um usuário individual em diferentes dispositivos. Por exemplo, você pode fazer o upload dessas IDs como [atributos do cliente](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) para a Experience Cloud e acessar esses dados em soluções diferentes.

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Using the `setCustomerIDs` method results in a call to the Experience Cloud ID Service, to `dpm.demdex.net`, with the addition of the `d_cid_ic` query parameter, which contains the hashed customer ID. Uma chamada de amostra pode ser parecida com a abaixo. Quebras de linha foram adicionadas para maior clareza.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| Parâmetro | Descrição |
|------------|----------|
| `d_cid_ic` | Transmite o Código de integração, a ID de usuário exclusiva (DPUUID) e uma ID de estado autenticada para o serviço de ID. Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>Estado de autenticação</b> <br> Essa é uma ID opcional no parâmetro d_ cid_ ic. Expressa como um inteiro, identifica os usuários de acordo com o status de autenticação como mostrado abaixo: <br> <ul><li>0 (Desconhecido ou nunca autenticado)</li><li>1 (Atualmente autenticado para esta instância/contexto de página/aplicativo)</li><li>2 (Logout realizado)</li></ul> <br> Exemplos: <br> <ul><li>Desconhecido: ...d_cid=123%01456%01<b>0</b></li><li>Autenticado: ...d_cid=123%01456%01<b>1</b></li><li>Logout: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

O Launch Platform Launch é a próxima geração de recursos de gerenciamento de tags da Adobe. Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

<br> 

Depois de confirmar sua configuração, o Launch vincula os dados em um objeto, como abaixo:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Esta é uma amostra de código:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.